Terraform Documentation

Using terraform, create an AWS instance (ubuntu) in multiple regions (free tier) (us-east - 1 and eu-central -p 1)
    - should be on, minimum, 2 availability zones

    -should be reusable

     -can be built on multiple environment (dev 		and prod)

     - should have a script that creates an		                               	Ansible,  Docker container

      -Your script must be modularised

      - Create a VPC for the various environment

       		  What Is Terraform

Terraform is an IAC tool, used primarily by DevOps teams to automate various infrastructure tasks. The provisioning of cloud resources, for instance, is one of the main use cases of Terraform. It's a cloud-agnostic, open-source provisioning tool written in the Go language and created by HashiCorp.

		Prerequisites Tools
* Have An Account With AWS
* Install Terraform On Your Local Machine
* Install VScode On Your Local Machine (Mac OS, windows and Linus os)

         		Procedure
Folders and file arrangement is the first steps , I created terraform module folder and put ec2-ansible-docker folder there.
  
Then I create  a module folder and a VPC folder thee.

Now this is  the arrangement of my folder and file with the sequence of VPC configuration, ec2 instance spining,subnet 1, subnet 2, internet gateway, route tables and availability zones.

A module folder is created], where all he infrastructure tools are modularised and variable tf where the infrastructure tools configurations are referenced.

	File Arrangement And Configuration

* Terraform modules
* Ec2-ansible-docker
* 
                       Main.tf
- Create vac
- Create internet gateway and attach it to vic
- Use data source to get all availability zones in the region
- Create public subnet az1  (availability zone 1)
- Creatte public subnet az2 (availability zone 2)
- Create route table and add public route
- Associate public subnet az1 to public route table
	associate public subnet az2 to public route table

			Ec2.tf
- creating instance 
- User_data = <<-EOF. Is the bash script code used to install docker and pull ansible on the ec2 instance
- 

			Sg.tf  
- In the code the resource which bis aws_security_group was called and inbound rules such as network protocol to tcp and the description of respective network HTTP,HTPPS,SSH,Cidr_block,ports


			Variable.tf

- The variable.tf  region, project_name, vpc_cidr, public_subnet_az1_cidr,public_subnet_az2_cidr, ami, type,key_pair were all referenced here.
Note. Ami information can only be accessed by login on to my AWS GUI Interface, put ec2 in the search bar, press launch instance, go to ubuntu and you will see the ami value.

Us-east-1 was referenced in region-1.tfvars
Eu-central-1 was referenced in region-2.tfvars

			Output

- Output region
- Output project name
- Output vpc id
- Output internet gateway
- Output public ip

To run your terraform code on vscode, go to terraform folder,right click on it and open in integrated terminal

Run terraform init

Run terraform apply.
