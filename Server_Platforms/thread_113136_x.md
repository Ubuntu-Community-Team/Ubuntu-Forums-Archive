---
title: "x"
date: 2006-01-05
forum: Server Platforms
---

### Post by kragh on 2006-01-05
I installed server. How do I start x?

---

### Post by Zelut on 2006-01-05
x is not included in the 'server' version... thats kinda the point :)

---

### Post by amohanty on 2006-01-05
Install xorg:
> sudo apt-get install xserver-xorg

Then:
> startx

**NOTE** I am not sure if this will default to gnome. To install the entire set of desktop apps do the following:
> sudo apt-get install ubuntu-desktop
and reboot.

HTH
AM

---

### Post by kragh on 2006-01-05
Well can I set up DHCP, mail server and apache with the ubuntu workstation?

---

### Post by kragh on 2006-01-05
Thanks
[QUOTE=amohanty]Install xorg:


Then:


**NOTE** I am not sure if this will default to gnome. To install the entire set of desktop apps do the following:

and reboot.

HTH
AM[/QUOTE]

---

### Post by Soleil-Raid on 2006-01-05
[QUOTE=kragh]Well can I set up DHCP, mail server and apache with the ubuntu workstation?[/QUOTE]

Yes.

sudo apt-get install apache2 dhcp3-server postfix
(I personally prefer Exim4 over postfix, but that's just cos it's what I know, and the Ubuntu default seems to be postfix)
For IMAP and/or Pop3, I'd reccomend the Courier series.

courier-imap
courier-imap-ssl
courier-pop
courier-pop-ssl

Steer well clear of anything that uses mbox unless you enjoy having your mail strewn all over your home directory.

---

### Post by kragh on 2006-01-05
I am a recent refugee from windoesnot and have no UNIX experience. I want to get things up and running without spending too much time learning command line syntax.
[QUOTE=kuyaedz]x is not included in the 'server' version... thats kinda the point :)[/QUOTE]

---

### Post by amohanty on 2006-01-06
I guess then since you are used to the point and click culture, you better install the desktop version. There's no difference, its just assumed that most servers will be headless and thus the GUI part is not needed. To start with that try:

> sudo apt-get install ubuntu-desktop

reboot and you can then login via the GUI.

as an aside if you are expecting to configure and run server apps like web/mail  server you will have to learn how to deal with the cli, and my suggestion would be to take a  deep breath and jump right in. The community will always be there if you mess it up. Everybody I know learnt it that way and apparently it is the best way, simply because it forces you to understand what you are doing and thus preventing you from making really bad mistakes like setup and open proxy.

HTH
AM

---

### Post by kragh on 2006-01-08
Does anyone kno how to quickly set up a DHCP server hosting a website with mail-server for the domain?
The Ubuntu server will be the DHCP server for WinXP machines and function as the gateway/firewall/mail and web host.

---

### Post by kragh on 2006-01-08
[QUOTE=Soleil-Raid]Yes.

sudo apt-get install apache2 dhcp3-server postfix
(I personally prefer Exim4 over postfix, but that's just cos it's what I know, and the Ubuntu default seems to be postfix)
For IMAP and/or Pop3, I'd reccomend the Courier series.

courier-imap
courier-imap-ssl
courier-pop
courier-pop-ssl

Steer well clear of anything that uses mbox unless you enjoy having your mail strewn all over your home directory.[/QUOTE]

Thanks. That went through smoothly. I have two nics in the machine and want to connect one of them to the cable/internet and the other to the switch with XP clients on the LAN. The idea is to replace the SBS with the linux machine. I will use the dynamic ip software to update my dynamic ip assigned routable address with the  the dns servers so I can host a website and receive mail. Can this be done with Ubntu server?

---

### Post by Soleil-Raid on 2006-01-09
[QUOTE=kragh]Thanks. That went through smoothly. I have two nics in the machine and want to connect one of them to the cable/internet and the other to the switch with XP clients on the LAN. The idea is to replace the SBS with the linux machine. I will use the dynamic ip software to update my dynamic ip assigned routable address with the  the dns servers so I can host a website and receive mail. Can this be done with Ubntu server?[/QUOTE]

Definatly. Did this myself many moons ago. :)

---

### Post by SlowJet on 2006-01-09
[QUOTE=kragh]Thanks. That went through smoothly. I have two nics in the machine and want to connect one of them to the cable/internet and the other to the switch with XP clients on the LAN. The idea is to replace the SBS with the linux machine. I will use the dynamic ip software to update my dynamic ip assigned routable address with the  the dns servers so I can host a website and receive mail. Can this be done with Ubntu server?[/QUOTE]


Yeah, but that server is not rally that safe without some extras installed, is it?
And the Windows LAN is still not isolated that good either?

I have the same setup with a windows machine that I want to make a Linux and aviod $ of software lincenses.

But I'm not running e-mail or web server and I'm still more paraniod than you seem to be about security.

I would have another router sever between the e-mail / webb servers and the lan.

On the second one I would have squid proxy for the lan web browsing, samba sever, and maybe ftp server.
I would also get some type of AV on that one also.
And then finally, for me, not knowing iptables that good, I would try to use zerba or gugga router software to block all the unneeded protocols for the lan.
But I'm not sure how o do that.

I think the e-mail and web in the middle like that is a DMZ (but they should be hanging off a nic and hub so that when they get hosed the gateway is still avilable.(They need different environment so they can be hardened with approiate tools, e-mail, web, database, cvs, ftp - what ever function is need for a site.)

I know it is a lot of hardware but the internet, the DMZ and the LAN need strog seperation and different security tighing processes.


If it were easy someone would have a script for all. :)

I'm only talking to myself coz it's a frustrating not knowing how to configure a text file yet I could put all these computer together, and install the software in a day.
And if I were to ask any 10 people I would get 10 different answers.  :)

SJ

---

### Post by kragh on 2006-01-09
[QUOTE=Soleil-Raid]Definatly. Did this myself many moons ago. :)[/QUOTE]
Well if you will give me some clue.::confused: 
BTW the first step as I see it is to install the dynamic ip updater from noip.com. Have you been able to do that?

---

