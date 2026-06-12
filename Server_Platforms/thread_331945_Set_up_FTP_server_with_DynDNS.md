---
title: "Set up FTP server with DynDNS?"
date: 2007-01-05
forum: Server Platforms
---

### Post by Brian Boyko on 2007-01-05
Hi.  How would I go about setting up an FTP server so that I can log into my home computer from anywhere on the Internet, using DYNDNS to handle NAT issues?

Bonus points if you can also tell me how to SSH in.  Hell - even telnet'll do it.

---

### Post by K.Mandla on 2007-01-05
(Moved to Servers & Security. :) )

---

### Post by rth on 2007-01-05
Step 0: Configure IPTables
Step 1: Install SSHd

I do not know the specifics of DnyDNS, but I use No-IP and everything is peachy for me. I don't run an FTP at the moment, but I do have a web server and SSH...

I'm not sure what you mean by DynDNS handling NAT issues. NAT is Network Address Translation which is how computers on a LAN have internal IPs but share one external IP for use getting on the Internet. Do you plan on doing port forwarding and have a LAN? Is your machine on its own and will be the FTP and SSH server?

FTP gives you access to download files, it will not give you access to run commands. SSH will allow you to run command line commands remotely. You can tunnel things like VNC through SSH or X sessions as well...

---

### Post by kebes on 2007-01-05
> **Brian Boyko said:**
> Hi.  How would I go about setting up an FTP server so that I can log into my home computer from anywhere on the Internet, using DYNDNS to handle NAT issues?

Bonus points if you can also tell me how to SSH in.  Hell - even telnet'll do it.

Set up FTP server:
sudo aptitude install proftpd

Set up SSH server:
sudo aptitude install sshd


Then create a new account with DynDNS or NoIP or whoever (see step 5 in [this tutorial]("http://ubuntuforums.org/showthread.php?t=268985") for details about setting up NoIP, and check step 2.a for hints on dealing with router issues).


Once that's done you can SSH, SFTP or FTP into your home machine by going to the web address you chose with DynDNS (or NoIP, or whoever).


I know the above instructions are quick and vague, but I'm not sure how much background knowledge you have. If you need help with any step, please post.

---

### Post by wayne_za on 2007-01-07
I currently use proftp with No-ip works very well dont forget to specify the port to be forwarded in the proftptd.conf. You will need to configure this in your FTP program .

---

### Post by mattc908 on 2008-02-19
[http://insightahoy.com/forum/viewtopic.php?f=4&t=2](http://insightahoy.com/forum/viewtopic.php?f=4&t=2)

---

