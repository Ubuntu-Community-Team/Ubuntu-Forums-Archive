---
title: "Unable to ssh to a maverick server on EC2"
date: 2011-01-19
forum: Ubuntu Cloud and Juju
---

### Post by dxxvi on 2011-01-19
Hi all,

I created an AMI with the AMI id here [http://aws.amazon.com/amis/4349?_encoding=UTF8&jiveRedirect=1]("http://aws.amazon.com/amis/4349?_encoding=UTF8&jiveRedirect=1") (the EBS root, us-east-1). I chose the default security group which I believe opens all ports for everybody on the Internet. Then I created a key pair and downloaded it to a Windows XP machine where I have cygwin/x installed. In the xterm of the Cygwin/X server, I run ```
chmod 400 ~/.ssh/key.pem
```Then I connected to that AMI with ```
ssh -i ~/.ssh/att.pem ubuntu@ec2-174-129-120-125.compute-1.amazonaws.com
```and ssh said ```
ssh: connect to host ec2-174-129-120-125.compute-1.amazonaws.com port 22: Connection timed out
```Did I do anything wrong?

---

### Post by kim0 on 2011-01-20
The default security group has nothing open, you need to open port 22 for ssh using the Amazon AWS console, or using ec2-authorize cli tool

---

