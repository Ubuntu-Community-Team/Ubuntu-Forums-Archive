---
title: "Not connection Kali Linux"
date: 2018-01-08
forum: Ubuntu/Debian BASED
---

### Post by dangertoxic on 2018-01-08
I had internet connection the first time I install Kali Linux, but now, every time I opened I don't. When I ping I transmitted packets but I don't received and an error appears to me "Destination host unreachable" I tried to change the DNS and my IP but not of that is working I need help please:p

---

### Post by yancek on 2018-01-08
Is this an actual install of Kali or are you running it 'live' from a usb?  If it's a 'live' system, no settings changes are saved.  Networking is disabled by default in Kali.  Best source of information on Kali is thier site since it is not a standard Linux but very specialized.

[https://docs.kali.org/](https://docs.kali.org/)

---

### Post by dangertoxic on 2018-01-08
it's not an usb install, it's installed in my pc with VirtualMachine

---

### Post by yancek on 2018-01-08
Which virtual software are you using?  I've only used Virtualbox and with it, you need network set to bridged to access outside the virtual environment.  I think the default is NAT.

---

### Post by dangertoxic on 2018-01-09
I had already done that too. I have tried in wm ware and in VirtualBox but non of them work.
Also thanks for anwer;)

---

### Post by yancek on 2018-01-09
Are you able to go online with Kali, for example to get to google or yahoo?
Or, is the problem accessing anything on the host or a LAN?

---

### Post by dangertoxic on 2018-01-09
I enter in firefox and all the websites start loading but non of them fineshed. And like I said before, when I ping I can send packets but I can´t received

---

### Post by yancek on 2018-01-09
What do you successfully ping?  Some online site like Google, your router, another machine on the LAN?  Do you get a timeout error on firefox?
From where are you trying to ping to Kali?  Another machine on the LAN? the host machine?

You might be better off at the Kali site at the link I posted above.  They have very good documentation.  I've never used it myself so can't really help any more.

---

