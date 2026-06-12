---
title: "Best Linux Server Distro?"
date: 2010-08-21
forum: Server Platforms
---

### Post by TheCraneMan on 2010-08-21
I have an old Compaq that I'm not using anymore, it's got 256MB of RAM and a 250GB Hard Drive. I want to set it up as a small FTP server for my household, nothing big but easy file sharing from anywhere. What is the best Linux Distribution for this? I really need one that's NOT resource consuming, any help would be greatly appreciated! Thanks in advance! -Canute

---

### Post by earthpigg on 2010-08-22
ubuntu server will be fine.

but given your needs: it really doesn't make much of a difference, to be honest. 

CentOS, Ubuntu LTS, Debian Stable... flip a coin or roll a dice. :P

Software you choose to install and how you configure it will be the important factor, here.

---

### Post by Lars Noodén on 2010-08-23
As @earthpigg wrote, there is little difference. Just install the least amount of stuff you possibly can.  Then add what you need as you need it.  

Skip FTP (leave it out) unless you are planning to offer read-only downloads via Anonymous FTP. OpenSSH Server will be in the default installation and that comes with SFTP built in.  From a user perspective it is the same, but the important difference from a sysadmin perspective is that it is both simpler to set up and is secure.

Your desktop already has several SFTP clients.

---

### Post by TheCraneMan on 2010-08-23
Thank you both! Alright I know this is extremely dumb but I installed Ubuntu Server Edition not realizing servers had not GUI :) so do any of you know any good tutorials? And thanks for the tip about SSH vs. FTP, helped a lot! :)

---

### Post by earthpigg on 2010-08-23
> **TheCraneMan said:**
> Thank you both! Alright I know this is extremely dumb but I installed Ubuntu Server Edition not realizing servers had not GUI :)

they don't have a gui by tradition, not by necessity. 

you can add openbox or the windows 98-looking JWM, if you wish.

or even full-blown ubuntu-desktop, though i wouldn't advise it on that hardware.

my server is a dual core 2ghz, so it has ubuntu-desktop installed -> so it can serve the dual purpose of being a desktop machine.

---

### Post by drdos2006 on 2010-08-23
Here is a HOWTO which I found comprehensive and invaluable.
> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood


regards

---

