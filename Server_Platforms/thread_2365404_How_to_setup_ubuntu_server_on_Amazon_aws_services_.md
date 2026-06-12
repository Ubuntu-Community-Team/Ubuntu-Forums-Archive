---
title: "How to setup ubuntu server on Amazon aws services in free tier?"
date: 2017-07-06
forum: Server Platforms
---

### Post by dkm171 on 2017-07-06
How to setup ubuntu server with php, mysql, phpmyadmin, ioncube and gd library etc... on Amazon aws services in free tier ? 

after setup the ubuntu instance, how to host multiple websites on single ubuntu instance ?

please reply or already answered to this subject on this forum please give me link, i will check !

---

### Post by Michael_McKenney on 2017-07-06
I have been watching the IT Pro.TV videos on AWS certification.  I have a yearly membership to IT Pro.TV.   I have been researching on AWS web site what OS are supported at each level.   Only certain OS are available on the free tier.  Ubuntu 14.04 LTS is on the free list only.   

[https://aws.amazon.com/marketplace/b/2649367011?page=1&filters=pricing_plan_attributes%2Carchitectures%2Cinstance_types&pricing_plan_attributes=FREE&architectures=64-bit&instance_types=t1.micro&searchTerms=&category=2649367011](https://aws.amazon.com/marketplace/b/2649367011?page=1&filters=pricing_plan_attributes%2Carchitectures%2Cinstance_types&pricing_plan_attributes=FREE&architectures=64-bit&instance_types=t1.micro&searchTerms=&category=2649367011)

---

### Post by dkm171 on 2017-07-06
thanks Michael

ubuntu 16.04lts server not for free, 

and

how to operate putty on ubuntu instance and how to install php, phpmyadmin, mysql and others, such as gdlibrary, ioncube.

I have zero knowledge about amazon aws free tiers services and i know cpanel hosting i can handle everything in cpanel.

> **Michael_McKenney said:**
> I have been watching the IT Pro.TV videos on AWS certification.  I have a yearly membership to IT Pro.TV.   I have been researching on AWS web site what OS are supported at each level.   Only certain OS are available on the free tier.  Ubuntu 14.04 LTS is on the free list only.   

[https://aws.amazon.com/marketplace/b/2649367011?page=1&filters=pricing_plan_attributes%2Carchitectures%2Cinstance_types&pricing_plan_attributes=FREE&architectures=64-bit&instance_types=t1.micro&searchTerms=&category=2649367011](https://aws.amazon.com/marketplace/b/2649367011?page=1&filters=pricing_plan_attributes%2Carchitectures%2Cinstance_types&pricing_plan_attributes=FREE&architectures=64-bit&instance_types=t1.micro&searchTerms=&category=2649367011)

---

### Post by Habitual on 2017-07-06
ssh into your AWS host and and issue
```
sudo su -
```

Once you are root. issue
```
tasksel
``` and press enter.
Make Certain "LAMP server" is selected  (toggle select is spacbar)
and press tab and that highlights the <Ok> option. Press Enter again.

LAMP is installed.

---

### Post by 1clue on 2017-07-06
It seems you're not very experienced with Ubuntu in general.

Putty is a windows-based ssh client. You don't run it on Ubuntu.

Setting up php, phpmyadmin, mysql and such on aws is the same as setting it up on your own hardware. I recommend that you create a local VM and install the images and software you want locally so you can learn the ropes before getting into cloud services.

I'd suggest starting with a LAMP server: Start with the ubuntu-server installer, and there should be a LAMP option in the installer. LAMP is Linux, Apache, Mysql and PHP. It's a basic web server.

Alternatively you could find the selection to install a minimal VM and then install the LAMP part afterward, this will probably make the smallest image.

---

### Post by 1clue on 2017-07-06
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by dkm171 on 2017-07-06
Hello Habitual 

I am a beginner with aws services and Ubuntu server, i dont know run commands, so please tell me clearly or first step...

 
> **Habitual said:**
> ssh into your AWS host and and issue
```
sudo su -
```

Once you are root. issue
```
tasksel
``` and press enter.
Make Certain "LAMP server" is selected  (toggle select is spacbar)
and press tab and that highlights the <Ok> option. Press Enter again.

LAMP is installed.

---

### Post by dkm171 on 2017-07-06
my computer have windows 8.1 so i connect to ubuntu with putty ?

I choosed the aws free tier services (ubuntu 16.04LTS instance) to my wordpress website(s)

how to ?

> **1clue said:**
> It seems you're not very experienced with Ubuntu in general.

Putty is a windows-based ssh client. You don't run it on Ubuntu.

Setting up php, phpmyadmin, mysql and such on aws is the same as setting it up on your own hardware. I recommend that you create a local VM and install the images and software you want locally so you can learn the ropes before getting into cloud services.

I'd suggest starting with a LAMP server: Start with the ubuntu-server installer, and there should be a LAMP option in the installer. LAMP is Linux, Apache, Mysql and PHP. It's a basic web server.

Alternatively you could find the selection to install a minimal VM and then install the LAMP part afterward, this will probably make the smallest image.

---

### Post by 1clue on 2017-07-06
Speaking as someone who uses a lot of VMs for personal and professional use, some of which are cloud-based, I want to give a little bit of  free advice. Please don't view this as obstructionism, and don't think I'm insulting you.

Observation:  You are asking about how to connect to a remote Ubuntu box from your  Windows computer, and about using Putty on Ubuntu. This makes me believe that you're so new at Linux that you  probably haven't installed any variant of Linux anywhere yet, or at least haven't been  confident that you had a successful install. There is no real problem  with being new to Linux, everyone on this forum was once new to Linux or is right now new to Linux. While there is no problem with being new to Linux, there is a huge problem with being new to Linux  and provisioning a Linux server on the cloud. You're jumping into the Linux pool at the deep end, and you need to know what the water feels like first.

My advice is this:  DO NOT install on any cloud service until you have become comfortable  using Ubuntu as a web server which is hosted on your local network. I  recommend you install it on a VM on some local system, and then  configure it, secure it and expose the services you need to your local  network.

Putting a system on the cloud exposes you to a world  containing people who Do Not Like You. They'll break into your system  and use it for their own ends. You might have this system for years and  not know you've been owned all this time if you don't take some  precautions. The precautions I'm talking about involve a lot of  education about Linux, web servers, databases and networking in general.  It involves an awareness of vulnerabilities and the patch release  cycle, and what all that means to your system.

With admittedly  very little information to go on, my instinct tells me that you've not  done much with networked servers running any operating system. Again, not a huge problem but the solution involves getting experience in a safe, controlled manner.

If you start a thread about how to install Ubuntu and start asking  questions about how to use it, I'll gladly point out some resources.  Pardon me if I don't help you get something on AWS.

---

### Post by Habitual on 2017-07-06
> **dkm171 said:**
> Hello Habitual 

I am a beginner with aws services and Ubuntu server, i dont know run commands, so please tell me clearly or first step...
Those were the first steps.

If you have no Linux Experience. You could do this in Virtualbox to get better acquainted with how Linux works?

Or the AWS way, it's shiny and it's GOOD stuff.

[Accessing Amazon EC2]("http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/concepts.html#access-ec2")

Physical access via remote terminal is accomplished with the .pem key AWS gave you in your AWS Console.
Putty accomplishes this for Windows users.
[Connecting to Your Linux Instance from Windows Using PuTTY]("http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/putty.html")
and  [Troubleshooting Connecting to Your Instance]("http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/TroubleshootingInstancesConnecting.html").

Have a Great Day.

---

### Post by QIII on 2017-07-06
I am going to echo 1clue's sage advice:  I strongly recommend you *do not* move forward with this if you are unfamiliar with servers, especially since this one will be exposed to the web.  Server maintenance and security are daunting tasks that take a lot of time, effort, and continuing threat research.

I recommend again that you *stop, take a breath, and refrain from rushing forward*.  Install your server locally in a VM on your home machine and expose it only in your home network.  Learn how your home network works, how to maintain it and how to secure it.  Learn how servers work, how to maintain them and how to secure them.  In that much safer environment, learn how to create a website on the server, maintain it, and secure it.

It is critical that you know what you are doing BEFORE you put something into the alligator pond -- otherwise the web will eat your lunch.

---

### Post by dkm171 on 2017-07-07
thanks to all (Habitual, 1clue, QIII)

Hi, I agree with you. I have zero knowledge about ubuntu linux server.  I am learner about how to use Ubuntu Desktop 
(But i have knowledge with cpanel hosting) and (i know wamp & xampp how it works on windows).

I will start with home VM with your suggestions. 

thanks to Habitual, How it works VirtualBox, i don't know... 

How many desktops i need for practice to host websites in my home network ?

---

### Post by CharlesA on 2017-07-07
> **Habitual said:**
> Those were the first steps.

If you have no Linux Experience. You could do this in Virtualbox to get better acquainted with how Linux works?

Vouching for this. This is how I got started.

> **QIII said:**
> I am going to echo 1clue's sage advice:  I strongly recommend you *do not* move forward with this if you are unfamiliar with servers, especially since this one will be exposed to the web.  Server maintenance and security are daunting tasks that take a lot of time, effort, and continuing threat research.

I recommend again that you *stop, take a breath, and refrain from rushing forward*.  Install your server locally in a VM on your home machine and expose it only in your home network.  Learn how your home network works, how to maintain it and how to secure it.  Learn how servers work, how to maintain them and how to secure them.  In that much safer environment, learn how to create a website on the server, maintain it, and secure it.

It is critical that you know what you are doing BEFORE you put something into the alligator pond -- otherwise the web will eat your lunch.

Good advice here too.

> **dkm171 said:**
> thanks to all (Habitual, 1clue, QIII)

Hi, I agree with you. I have zero knowledge about ubuntu linux server.  I am learner about how to use Ubuntu Desktop 
(But i have knowledge with cpanel hosting) and (i know wamp & xampp how it works on windows).

I will start with home VM with your suggestions. 

thanks to Habitual, How it works VirtualBox, i don't know... 

How many desktops i need for practice to host websites in my home network ?



[COLOR=#000000]**Habitual**[/COLOR]

With VirtualBox, you can run as many machines as your hardware supports.. I usually run one or two on my desktop if I'm messing around with things.

You can download VirtualBox here: [https://www.virtualbox.org/](https://www.virtualbox.org/)

This should get you started as well: [https://askubuntu.com/questions/142549/how-to-install-ubuntu-on-virtualbox](https://askubuntu.com/questions/142549/how-to-install-ubuntu-on-virtualbox)

Also: Snapshots are your friend, but they do not replace backups, only allow you to go back to a place in time... like right after you installed Ubuntu, but before you set up Apache.

---

### Post by Habitual on 2017-07-07
> **dkm171 said:**
> How many desktops i need for practice to host websites in my home network ?
If you are trying to learn servers, then no desktops.
As a general rule, Servers don't have desktops.

I suggest install from mini.iso and select to install and enable 
[COLOR="#FF0000"]
OpenSSH server
LAMP server[/COLOR]

[https://www.virtualbox.org/manual/ch01.html#hostossupport](https://www.virtualbox.org/manual/ch01.html#hostossupport)
[http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html)

Here is the summary:
Install [Virtualbox]("https://www.virtualbox.org/wiki/Downloads") for Windows.
32 or 64 bits for your ***host***. 
"host" is an important distinction from ***guest*** when discussing Virtualbox *appliances*.
No one but Virtualbox and the pedantic ever use the designated nomenclature. Nice to meet you!

Install Virtualbox5.
New Appliance. 
10G disk space allocation.
4096 Meg (4G) of Memory assigned. (could get by with less, maybe 3072 Meg or 3Gig)
Install Ubuntu from mini.iso (Virtualbox can boot ISOs on the host hard drive, permissions:owner:group permitting)
Where you get to "Software Selection" of the install, verify selection of
```

OpenSSH server
and 
LAMP server
```

Then I'd check back here for more instruction.

[https://codex.wordpress.org/Installing_WordPress#Famous_5-Minute_Install](https://codex.wordpress.org/Installing_WordPress#Famous_5-Minute_Install)
[https://codex.wordpress.org/Moving_WordPress](https://codex.wordpress.org/Moving_WordPress) 
NOTE: "move" in this context can be affected without any DNS changes, or using 127.0.0.1 site.com in /etc/hosts and some database edits
on the "copied" site.

All of this can be done without any negative impact on the original Wordpress site.

See also
[https://help.ubuntu.com/lts/serverguide/wordpress.html](https://help.ubuntu.com/lts/serverguide/wordpress.html)
[https://www.digitalocean.com/community/search?q=wordpress](https://www.digitalocean.com/community/search?q=wordpress)

---

### Post by 1clue on 2017-07-07
I always have to hunt for it but there's an option for a minimal VM on server or mini, I would start with that. A normal ubuntu server install has drivers for real hardware, which does nothing except take up disk space. If you start with the minimal VM then it only has drivers provided by VM software (kvm, virtualbox, vmware etc) and these drivers are faster anyway. So it's to your benefit to use this as your base install.

Otherwise what Habitual said is great.

---

### Post by 1clue on 2017-07-07
For my use at work I maintain a base VM with an Ubuntu on it. It gets updates and has the software installed that I want on every VM, which amounts to the minimal VM, the vim editor and some proprietary code we use at work. When I want a new VM I clone that one and start from there.

---

### Post by Michael_McKenney on 2017-07-07
I run a corporate data center.  I was curious about AWS as a solution for the data center.   So I called Rackspace.  AWS is designed to run on all their services.   It is not you placing your Ubuntu server with its databases on AWS.  It is designed for you to leverage their services for failover, scalability, and deployment.   Lets say your company is growing fast.   You think you need 100 servers brought online.   You go into AWS and dial up 100 servers with the databases services connected.   Minutes later you have 100 servers.   Then you realize your scaling up only needed 20 servers deployed.  You go back in and dial down to 20.   You get billed based on usage only.   How many vCPUs, RAM, storage, bandwidth.   It is not a hosting site for you to spin up your servers on for hosting.   It is designed for rapid ecommerce deployment.   Rackspace said for our company just use their hosting site not AWS.

---

### Post by 1clue on 2017-07-07
@Michael_McKenney,

Interesting. I never even evaluated them frankly, I thought it was just another hosting site. Not sure I would have a use for that type of arrangement, my company likes to have more control over details than that strategy seems to afford.

IMO it doesn't significantly change the discussion here. People need to understand security issues and maintenance issues just the same as with a regular hosting company.

---

