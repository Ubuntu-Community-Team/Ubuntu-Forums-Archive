---
title: "SSH Remote desktop connections to multiple computers on the same remote network"
date: 2009-05-08
forum: Security
---

### Post by davidmigl on 2009-05-08
My home network has 2 computers behind a basic router/dsl modem. I want to be able to remotely administer both of them via SSH and be able to forward their desktops/X11 windows.

I currently have no experience with this. I understand that the basic plan would be to have an SSH server running on one PC and have the SSH port(s) forwarded through the router to that PC. Then I would ssh -X name@domain and be up and running.

However, this only allows for one possible computer to connect to. How would I be able to select which computer I connect to?

---

### Post by MysticalRiotCandy on 2009-05-08
Set up your port forwarding to each different computer, and have SSH have different ports instead of just 22.  Say I have 10 computers.  I would probably change the port to 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, and 32.  It means that if I do *$ ssh -XC user@123.123.123.123 -p 22* , it'll open up X Windows tunneled through SSH from computer 1.  And so on so forth.

---

### Post by aurelieng on 2009-05-08
If you are using a DSL connection or have a domain name, it's probably safer to use non standard ports (e.g. 2222, 2223, etc... ). You can also have all connections redirected to a single machine: connect first on this gateway, then on any other machine you want.

---

### Post by bodhi.zazen on 2009-05-08
If you are going to install openssh, look at securing it :

[AdvancedOpenSSH - Community Ubuntu Documentation]("https://help.ubuntu.com/community/AdvancedOpenSSH") 

From the windows side, use putty and Xming

[http://ftp.chiark.greenend.org.uk/~sgtatham/putty/](http://ftp.chiark.greenend.org.uk/~sgtatham/putty/)

[http://www.straightrunning.com/XmingNotes/](http://www.straightrunning.com/XmingNotes/)

The alternate is either tunneling VNC over ssh

[http://martybugs.net/smoothwall/puttyvnc.cgi](http://martybugs.net/smoothwall/puttyvnc.cgi)

FreeNX

or VPN (see OpenVPN).

---

