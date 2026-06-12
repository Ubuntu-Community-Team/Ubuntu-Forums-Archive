---
title: "Setting up small development team server"
date: 2007-09-29
forum: Server Platforms
---

### Post by codetiger on 2007-09-29
Hi everyone. I am new to this forum and to Ubuntu as well. I am trying to setup a ubuntu server for our studio. We are actually a small team of developer working on game development for mobile platform. 

My requirements:
1) Domain controller
2) File sharing + printer sharing with all Win XP Clients
3) Internet sharing

Progress:
I have now installed the latest Ubuntu server on my server and installed Samba on it. I also additionally installed GUI desktop. I intalled the printer and tested on the server. I have added one more network adaptor and connecting one to LAN switch and another to internet modem. 

Help needed:
1) I need to share internet with this server to all other systems. I also need to filter some sites which is secondary task.
2) I need to setup Domain controller like in Win 2003. I tried doing a lot of things using samba. but every time I try it shows as a workgroup in other windows systems. I dont know where is the mistake. In Smb.conf I gave "workgroup=servername", how do I configure a domain controller and create users for each employee so that they can login using this username on their system. With this username I also need to set rights during folder sharing.

---

### Post by rennen01 on 2007-09-29
Did you install Server Version 6.06, 6.10,  or 7.04?

If 7.04, here is something for you to look at:
[http://www.howtoforge.net/perfect_setup_ubuntu704](http://www.howtoforge.net/perfect_setup_ubuntu704)

If 6.06, here is something for you to look at:
[http://www.howtoforge.net/perfect_setup_ubuntu_6.06](http://www.howtoforge.net/perfect_setup_ubuntu_6.06)

Also here is some Samba documentation:
[http://www.howtoforge.net/samba_domaincontroller_setup_ubuntu_6.10](http://www.howtoforge.net/samba_domaincontroller_setup_ubuntu_6.10)

---

### Post by codetiger on 2007-10-01
How do I share internet with ubuntu server?

---

### Post by s.s.swapnil on 2007-10-01
I'm not sure about Ubuntu .... Buthe there is Killer Proxy in Linux ... i.e. SQUID proxy server ... This allows you 2 controll Internet access to the clients ....

---

### Post by markymarknz on 2007-10-01
Try using EBox it does everything you want and you use a web interface.
Aparently the new version coming out in a few weeks 7.10 "Gutsy" will have this integrated in some way.

Mark

---

### Post by codetiger on 2007-10-01
Thanks, for all you help. I have installed firestarter firewall and configured my ubuntu server to share internet.

Now Is there any way to block a list of websites to the clients?

---

