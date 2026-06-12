---
title: "AWS cloud server"
date: 2011-03-17
forum: Server Platforms
---

### Post by jdb91 on 2011-03-17
Hi All,

I tried AWS with one of it's pre built (SuSE) distros to get a feel for how it all works and I must say it's all very nice and reasonable value for money.  So, any way, I was into SuSE many years ago and after that, switched to Ubuntu after it started to get annoying.  So I did the same on the server,  I "terminated it" and started a new one with Ubuntu 1010 server running.

The problem I'm having at the moment is that I can't connect to it without the SSH key, on SuSE all I did was create a user called "remote" with a password and homedir, which I could login with, then su to root on the box.  All good.  This principle doesn't seem to work with the Ubuntu server that's now running as it requests a key how ever I try to connect.

Any suggestions please?

---

### Post by BkkBonanza on 2011-03-17
As far as I know you have to use a key. The EC2 control panel makes it easy to create a key and have it assigned to the server at boot which is what I've always done. Using keys is easier than passwords and more secure.

On the EC2 control panel, create the key and it has a button to click and save it (the public half) on your local machine. Copy it to your ~/.ssh directory with a name like MyAWS.pem. Then create a file named **config** in the same .ssh directory and in that file put:

Host *.compute-1.amazonaws.com
StrictHostKeyChecking no
UserKnownHostsFile .ssh/MyAWSHosts
IdentityFile .ssh/MyAWS.pem
User ubuntu

Now when you ssh to the server it will all happen transparently, quickly and easily with no prompts.

Above assumes the user name is "ubuntu". I use the Alestic.com AMI images and that's how they are configured. Using a config file like this automates the details of the identity and makes it so you don't always get ip address warnings as they change every new instance anyway.

When you start an instance you tell it which key to start up with as you could have several (though I only have one).

The reason I have the file MyAWSHosts is to prevent your regular hosts key file from getting filled up with transient host keys from AWS (which for me change IP often and so keep getting stored over and over).

I know that when you're used to using passwords switching to keys seems unwieldy but it is a hurdle quickly overcome and a real step forward overall. I never use passwords for any of my servers now. Keys are way more secure.

---

### Post by jdb91 on 2011-03-17
> **BkkBonanza said:**
> As far as I know you have to use a key. The EC2 control panel makes it easy to create a key and have it assigned to the server at boot which is what I've always done. Using keys is easier than passwords and more secure.

On the EC2 control panel, create the key and it has a button to click and save it (the public half) on your local machine. Copy it to your ~/.ssh directory with a name like MyAWS.pem. Then create a file named **config** in the same .ssh directory and in that file put:

Host *.compute-1.amazonaws.com
StrictHostKeyChecking no
UserKnownHostsFile .ssh/MyAWSHosts
IdentityFile .ssh/MyAWS.pem
User ubuntu

Now when you ssh to the server it will all happen transparently, quickly and easily with no prompts.

Above assumes the user name is "ubuntu". I use the Alestic.com AMI images and that's how they are configured. Using a config file like this automates the details of the identity and makes it so you don't always get ip address warnings as they change every new instance anyway.

When you start an instance you tell it which key to start up with as you could have several (though I only have one).

The reason I have the file MyAWSHosts is to prevent your regular hosts key file from getting filled up with transient host keys from AWS (which for me change IP often and so keep getting stored over and over).

I know that when you're used to using passwords switching to keys seems unwieldy but it is a hurdle quickly overcome and a real step forward overall. I never use passwords for any of my servers now. Keys are way more secure.

It was working fine on AWS servers, that's the odd thing.  All I did was create a user witha a pw and would log in as that user with a pw.

I'm all up for using a key at home and do so with root and user "ubuntu" but not all ssh clients support keys so it's not always an option.  Plus (as far as I can see)  you can only download the key from the AWS site once and not again.

Odd one.  Strange that it worked fine with that horrid default SuSE install.

---

### Post by BkkBonanza on 2011-03-17
It would something configured by whoever creates the AMI. Maybe the folks who made the SuSE build decided against forcing keys. 

With a prebuilt AMI you don't have a choice to re-configure it since it boots as built. But if you create your own EBS (elastic block store) based AMI then you can adjust any settings like that in the AMI image so that it boots how you prefer. When I say boots I just mean it comes up and already has sshd_config settings that you choose.

It is fairly easy to convert a prebuilt AMI to your own custom one but a bit much to explain here. There are some tutorials around though.

I haven't really used the Canonical Ubuntu builds more than once to test. I use the Alestic ones. I'm not sure which is better but I had problems with the Canonical ones only working with their own cmd line tools and I prefer the [TimKay perl script]("http://timkay.com/aws/") for cmd line control which works nicely with the Alestic AMIs.

Using this tool I can start/stop instances in scripts from the cmd line. And even have it poll the instance and login in one simple command. Also real handy for moving files up onto S3 too.

---

### Post by jdb91 on 2011-03-17
> **BkkBonanza said:**
> It would something configured by whoever creates the AMI. Maybe the folks who made the SuSE build decided against forcing keys. 

With a prebuilt AMI you don't have a choice to re-configure it since it boots as built. But if you create your own EBS (elastic block store) based AMI then you can adjust any settings like that in the AMI image so that it boots how you prefer. When I say boots I just mean it comes up and already has sshd_config settings that you choose.

It is fairly easy to convert a prebuilt AMI to your own custom one but a bit much to explain here. There are some tutorials around though.

Ah, thanks for explaining the difference between the EBS and AMI, I had no idea.  It's just a bit of a hasstle, I totally understand the advantages of ssh-keys, I was an MPLS Core 2nd line Tech at BT and it was starting to be rolled out on the core routers there when I left.  

It's just annoying if I'm trying to use ssh on my phone to run a tiny job or whatever.

---

### Post by BkkBonanza on 2011-03-17
There's actually two kinds of AMI (amazon machine images):

EBS - which are like "dynamic" volumes you can mount and edit easily like a hard drive image.

Instance Store - which are like CD-ROM images you can boot but not change unless you totally rebuild them again.

EBS are more flexible and useful. Most newer instances use this but they didn't exist in the early days. But EBS images cost you money when they are sitting around not being run.

Instance Store images are basically free when not being used. Well, not if you make your own but the pre-made ones are.

You can start with an either one and "re-bundle" them into your own custom EBS image. Which is how you get a nice customized ready to use AMI. 

The easy way to make your own EBS one is to start with a premade one, customize it (without terminating it), and then stop the instance, "snapshot" it and create your own AMI with it. Then you can start as many machines with that AMI as you like, all starting from first boot as you customized.

If you do this you can customize the sshd_config and key values/passwords etc. then snapshot your own AMI to use as you prefer.

---

