---
title: "Ubuntu 8.10 - Server installation on Laptop ?"
date: 2008-11-02
forum: Server Platforms
---

### Post by ndnd on 2008-11-02
Hello, 
I am a newbie in the world of linux. Please provide details if and when possible. I wish to get aquainted with Linux server and will be installing additional products. 

I have two questions

1) I would like to install Ubuntu 8.10 - Server edition on my laptop - 
Specs:
Lenovo T61p
I have 15 GB HD, 4 GB RAM, 
Core 2 Duo 2.6 Ghz 


- Is this doable (in other words a very simple installation - boot from the CD and go by the GUI based options or will it require tweaking etc. ?


If the answer to question 1 is a YES

2) I currently have Vista running on the laptop and therefore I will have to partition the HD (I have 15 GB available for linux parition). My question should I use Vista' partition manager or UBUNTU's CD (server version 8.10 downloaded) gives me a safe option to handle the NTFT Vista files ? 

Thanks in advance.

---

### Post by jona7han on 2008-11-02
I don't know if you've tried this already, but why don't you install Ubuntu in VMware or Virtual Box in Windows first so as to get a feel for it. That way your not having to mess around with partition tables and it'll work well with the spec of laptop you have.

---

### Post by cjwallace on 2008-11-02
Hi mate. 

Just my 2p worth. Like you i am very very new to linux but not to computers as have been working and networking Windows box's for more years than i can remember and have all manor of certs MCP , MCSA , and training for CCNA

Anyway i tried many many different flavors of Linux but i finally settled with Ubuntu. I love it and never thought i could love anything apart from Windows. Playing with the GUI helps loads and when i finally started to play with the server version it made so much more sense to me. The support on this site is also something that has made the jump to ubuntu so much easier. 

You laptop spec would be fine for what you are trying to do but i agree if you can run it under vmware to get a feel.

Really enjoying the Ubuntu experience.

Craig

---

### Post by cariboo on 2008-11-02
I would suggest that seeing as you are a new Linux user, that it might be better to install the desktop version, as the server installation is text based and there is no gui installed.

To install serrver components to your desktop go to System-->Administration-->Synaptic Package Manager-->Edit-->Mark Packages by Task. This will bring up a menu with different installation options.

LAMP is probably what you are looking for, it installs Apache2, Mysql and Php5

Jim

---

### Post by HermanAB on 2008-11-02
The only difference between the desktop and server version is the presence/absense of a graphical desktop.  So I'd suggest that you install the desktop Ubuntu and if you want to see what it is like without X, just change to run level 3 with 'sudo init 3'.

---

### Post by mike010 on 2008-11-03
There are a few more things the server has or can do that the desktop does not just like the server does not install a x-window but the desktop will and the gui can be installed on the server but it sounds like the desktop would be what you need.

here is what you need to install the desktop for the server
sudo apt-get install ubuntu-desktop

also for x-windows try this dont know if it still works
apt-get install x-window-system-core xserver-xorg gnome-desktop-environment for starters

---

### Post by ndnd on 2008-11-03
Hello all,
Thank you for your prompt responses. Based on  your suggestions and questions here is my update:

My background:
I do have limited experience with linux O.S had done Red Hat (Fedora) installation few years ago. Currently I use it more for getting my work done as a user but not as an admin. So I do have a feel for linux and I suspect Ubuntu may not be too different. 

Reason for a dual boot install: 
The reason for Server installation is because I will be installing a 'server based software for handling database'. This will be processor and RAM intensive hence using VMware with Vista will really slow things down for me. 

Now  HermanAB and cariboo907 mentioned installing Desktop version and then install the server parts (Is it easy to identify the server related parts or do we have to select specific package based on our requirement-that might be difficult for me to identify?). 

> Carbio:
To install serrver components to your desktop go to System-->Administration-->Synaptic Package Manager-->Edit-->Mark Packages by Task. This will bring up a menu with different installation options.

LAMP is probably what you are looking for, it installs Apache2, Mysql and Php5



So I believe the trade off for me is that 

1) Install Desktop version - switch off the X, identify and install server related components

OR

2) Install Server version with Command Line Interface :
Is it possible to select default options or do we need to know the exact commands and options ?  I believe if there are default settings available and in terms of hardware they are able to identify the correct drivers etc. it should okay for me. 


-- Your comments and thoughts on Option 1 and Option 2

---

### Post by mike010 on 2008-11-03
Why not just install the server with GUI as said in my last post
if you need the server 
command 

sudo apt-get install ubuntu-desktop

---

