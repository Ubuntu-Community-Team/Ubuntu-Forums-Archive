---
title: "Update to server edition"
date: 2010-12-26
forum: Server Platforms
---

### Post by ranjix on 2010-12-26
I have Ubuntu Desktop edition. I want to update to Server Edition(Need to do that for assignment) with all features of server edition. Should I download Server edition again or there is another alternative???

---

### Post by nevius on 2010-12-26
> **ranjix said:**
> I have Ubuntu Desktop edition. I want to update to Server Edition(Need to do that for assignment) with all features of server edition. Should I download Server edition again or there is another alternative???

What type of a server do you need to set up? You can just install the required packages (apache, mysql, php, etc). The server edition and desktop edition use the same repositories. A better solution might be to install the server edition in virtualbox.

---

### Post by aceofspades686 on 2010-12-26
What specifically are you needing from the server edition? You may be able to just install those components on the desktop version.

Another alternative is to install it as a Virtual Machine.  VirtualBox is available in the Ubuntu repositories (or was last I knew, someone please correct me if this has changed) and it should be sufficient for most school assignments.  All you would need to do is install VirtualBox, download the Ubuntu Server ISO, then create a new Virtual Machine.  Mount the ISO image of Ubuntu Server edition when it asks you about the cd drive during creation, then when you start it, it behaves (more or less) like its installing to a new computer.

EDIT: Nevius beat me to it :P

---

### Post by ranjix on 2010-12-26
I need to install server edition. Never tried sever edition so don't know what type of server I need to set up. According to my assignment, I need to set up server for a Bank. I'm also trying to install XAMPP server. I downloaded the package from site but its in .tar.gz format. Don't know how to install it. 

Main problem with VirtualBox is I cant load full screen of OS in virtualbox. Yeah!! Its available in software center.

What is best alternative for virtualbox and it must load virtual OS in full screen mode. VMware??

---

### Post by aceofspades686 on 2010-12-27
Out of curiosity, why does it have to load in fullscreen mode? There is an entry in the machine menu on Virtual Box that allows you to switch to fullscreen if its needed, but whether it is fullscreen or not doesn't impact what the server can do.

As far as XAMPP is concerned, I've only ever installed that on windows machines, so I can't help you out too much there, but there's documentation available at [http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

---

### Post by ranjix on 2010-12-27
Its difficult to work with without full screen mode. VirtualBox full screen doesn't really support full screen mode. Only the virtual box window will be in full screen not the OS.

---

### Post by HugoSerrano on 2010-12-27
You know that in a server edition, with default installation, you only have the cli, no gui! 

But you can install VirtualBox, configure the network in bridge mode, install openssh-server, and then you can ssh to the server and maximize the console window! (dunno if this is what you want... hehe)

You can do everything in your Desktop Edition. The difference is that you got services running in your desktop that will be wasting resources in a server environment.

If you want to know how a server is look like, press CTRL+ALT+F2. (CTRL+ALT+F7 get you back to X).

Regards!

---

### Post by lisati on 2010-12-27
As others have suggested, your options can be influenced by what kind of server you're aiming for. Web server? Email server? File server? Something else? Some combination? Since it's for a bank, probably not a game server but something to handle transactions real time?

---

### Post by ranjix on 2010-12-27
Probably sth like that. If server edition have cli by default, I would not like to get more into server edition. Better option would be a Virtual Machine. I need a virtual machine which supports full screen mode. I've only tried VirtualBox and it doesn't. How is VMware??

---

### Post by aceofspades686 on 2010-12-27
I'm about 99.9% certain that VirtualBox does support full-screen, did you go to the machine menu on the actual machine window?  Also, you may need to install the VBox Additions to get "true" full screen.

That said, I use VMWare Workstation all the time, haven't used the free product (VMWare Server) in ages, but I'm fairly sure that it does have full screen as well.  You would also need to install VMWare tools in order to get a "true" full screen.

Another option you of course have is to set up a dual boot, but that's a bit heavy handed I believe.  What I personally like to do is set up a VM, get the network/ssh connection working, then just SSH into it with xterm and sshfs if I need to have file access.

---

### Post by ranjix on 2011-01-02
Maybe it didn't load actual full screen because I didn't install guest edition. Will try that later but can someone tell me how is VMware and is it a good alternative for Virtual Box?

---

