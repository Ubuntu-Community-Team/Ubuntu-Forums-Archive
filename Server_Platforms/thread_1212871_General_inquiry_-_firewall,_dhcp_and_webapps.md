---
title: "General inquiry - firewall, dhcp and webapps"
date: 2009-07-14
forum: Server Platforms
---

### Post by herrfledermaus on 2009-07-14
Hi there,
 
at the moment, I'm using a Clarkconnect box to manage my home network. Since I'm studying Java, I would like to change to Ubuntu so I can install JRE, Tomcat, Mysql and such. CC cannot handle that, I think, or it is to difficult. But before I start migrating to Ubuntu next thursday, I would want to ask a few basic questions if I may... ;-)
 
1. My CC box has two network cards: one for external (provider) which is the link to the internet, and one which serves the LAN (needs to provide DHCP and such). In between is a firewall and a filter (dansguardian). Is this also possible with Ubuntu server?
 
2. My Ubuntu box will be placed in the basement, so is it possible to remotly administrate the whole box?
 
3. How difficult is it to install a java enabled environment, including tomcat, maybe jboss, mysql and such? I'm quite a noob ... Does it work with rpm's and such?
 
thanks for your help, ):P

---

### Post by lisati on 2009-07-14
1. Although I haven't used it myself, I believe dansguardian can be used with Ubuntu. Ubuntu has firewall capabilities as well, but my knowledge of tweaking the settings is limited.
2. Ubuntu comes with remote login facilities. I've read on these forums of how some users have used this with their "headless" servers (computers without screen or keyboard) and other Ubuntu boxes.
3. (Apologies, insufficient Java knowledge on my part)

---

### Post by slugmax on 2009-07-14
1. Firewall - Sure, start with [https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall). 

2. Remote admin- Lots of ways. On a server where you likely won't have X installed, use SSH and a console. Even if you only install a few GUI apps on the server, you can still forward them remotely via SSH tunneling (ssh -X), which will use the X-server on your client. VNC is available for a full remote desktop, this can also be tunneled over SSH.

3. Java - Short answer, yes. Ubuntu is based on Debian and uses deb, not rpm. Apt is used to install deb packages and track dependencies. To get an idea of what is available, try these commands:

```

apt-cache search sun-java
apt-cache search tomcat
apt-cache search jboss
apt-cache search eclipse

```

You can install a package with apt-get or aptitude (aptitude when run by itself gives you a nice curses-based package manager):

```

sudo aptitude install tomcat6

```

Take a look at the server guide on package management for more:

[https://help.ubuntu.com/9.04/serverguide/C/package-management.html](https://help.ubuntu.com/9.04/serverguide/C/package-management.html)

Doug

---

### Post by herrfledermaus on 2009-07-14
ok thanks for your answers both! I now know what the options are and you all made it much clearer!

thanks mates !

:guitar:

---

### Post by spynappels on 2009-07-15
When you insert the Server Install disc, somewhere in the install it will ask you which server modules to install, if you select Tomcat, MySQL etc, it will all be configured in the initial install of the server OS, save time messing with .deb packages.

---

### Post by herrfledermaus on 2009-09-07
well it seems to work: more or less, only the gateway and dhcp give problems after a reboot, but I know how to fix that.

thanks for all help!

---

