---
title: "First time installing Ubuntu"
date: 2016-08-26
forum: Virtualisation
---

### Post by shaw-91 on 2016-08-26
Hello all,

I would like create virtual host running Ubuntu server 12.04.5 to ultimately create an apache Web Server. I have and Ubuntu12.04.5serveramd64.iso  file. I am using VMWare Workstation to create the virtual machine.
My host hardware specifications are:
HP 8300 Small Form Factor
Memory: 8GB
HDD: 500 GB
Processor Intel(R)Core(TM) i5-3570 CPU @ 3.4ghz

When I attempt to install at some point I am brought to a screen that ask for user name and password within and CLI interface. After I enter the data I see a "Welcome to Ubuntu" message and nothing else happens.
I am stumped here and would greatly appreciate if anyone can suggest the correct course of action to successfully install Ubuntu 12.04.5 in my virtual machine.

---

### Post by mastablasta on 2016-08-26
i suggest a newer image. 

check if the image you downloaded is good.

---

### Post by HermanAB on 2016-08-26
Since this is the first time, use the latest Desktop version of Ubuntu, not the server version.  

The server version is not unfriendly, it is just very choosy about who exactly its friends are and you can do exactly the same things with the desktop version, and more, so you can install Apache on it.

---

### Post by grahammechanical on 2016-08-26
> I am brought to a screen that ask for user name and password within and  CLI interface. After I enter the data I see a "Welcome to Ubuntu"  message and nothing else happens.

Nothing else is supposed to happen until the user runs a command. By entering your user name and password you logged into Ubuntu server. It has a command line user interface.

Regards

---

### Post by TheMTtakeover on 2016-08-27
Hello. As others have pointed out you as using Ubuntu Server edition which is CLI only. You can still what you want from the standard Ubuntu Desktop version which can be downloaded [here]("http://www.ubuntu.com/download/desktop"). If you install that version it will automatically start a GUI with the system.

---

### Post by shaw-91 on 2016-09-07
Thank you all for you comments and suggestion I did download the desktop version of Ubuntu 16.04.1. I am now in the process of securing my server by enabling SSH login and disabling the password authentication. Within the CLI I am attempting to run this command; sudo nano /etc/ssh/sshd_config ; in order to run the SSH daemon configuration. According to the tutorial I am using I am to find the line that specifies "PasswordAuthentication" and then too delete the preceding number and change its value to no. However when I enter that command I G[IMG]pictures/captureubuntu.png[/IMG]et this screen with no information. What would be my best course of action here
     

This is the link to the tutorial to the tutorial for your reference
  [https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-16-04)

---

### Post by HermanAB on 2016-09-07
Well, ssh works out of the box and password authentication is good enough for starters, provided that you make your passwords very long - more than 12 characters. So I suggest leaving well enough alone until you are more comfortable with the system.  Don't try to do all at once.

---

### Post by Bucky Ball on 2016-09-08
*Thread moved to **Virtualisation**.*

> **shaw-91 said:**
> However when I enter that command I G[IMG]pictures/captureubuntu.png[/IMG]et this screen with no information. What would be my best course of action here

Please attach pics by using 'Adv Reply' or 'Go Advanced' buttons then the paperclip icon in the taskbar there rather than inserting them into the body of the post. Thanks.

---

### Post by shaw-91 on 2016-09-08
Thank you Herman I will take that into consideration. 

In response to Bucky Ball the  screen I am brought to when running the "sudo nano /etc/ssh/sshd_config" command is below. Please diregard the amazon insert.

---

