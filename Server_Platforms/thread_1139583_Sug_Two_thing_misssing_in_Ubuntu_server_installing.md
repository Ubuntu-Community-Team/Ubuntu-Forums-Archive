---
title: "Sug: Two thing misssing in Ubuntu server installing"
date: 2009-04-27
forum: Server Platforms
---

### Post by irc4arab on 2009-04-27
I installed Ubuntu Server 9.04 in my server ,,,,, 

Installation steps are good and easy.

There many options like: LAMP, Tomcat, Samba, Printer server, OpenSSH, Mail Server, etc.


#1 but there are no "FTP Server" in the Options.
#2 There are no option to set static ip during the installation.


hope see these options in the next versions :KS

---

### Post by windependence on 2009-04-27
You should be using ssh instead of FTP whenever possible. 

There actually is an option to configure a static IP in the installation. You must have missed it.

-Tim

---

### Post by kamaji792 on 2009-04-27
> #1 but there are no "FTP Server" in the Options.
> #2 There are no option to set static ip during the installation.

The following link has information on how to set up an FTP server and setting a static IP address.  Not installed 9.04 myself but when I install 8.04 I usually set the network up post install anyway.

[https://help.ubuntu.com/9.04/serverguide/C/index.html]("https://help.ubuntu.com/9.04/serverguide/C/index.html")

All the best

---

### Post by Cheesemill on 2009-04-27
To set up a static IP on install, hit ESC when the installer prompts for a hostname and then select the 'Manual network configuration' option that appears.

Cheesemill

---

