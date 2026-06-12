---
title: "pptpd installed through ubuntu vps but ios device can not connect"
date: 2013-03-09
forum: Server Platforms
---

### Post by jokealot on 2013-03-09
Hi, I have just start to use VPS, and have installed ubuntu (11.0.4) on it. I have follow this:
[http://askubuntu.com/questions/199286/create-vpn-server-using-the-ubuntu-vps](http://askubuntu.com/questions/199286/create-vpn-server-using-the-ubuntu-vps)
to setup pptpd server, and after some effort it's up and running, but I am having trouble to connect my ipod touch (ios 6.1 jailbreak) to the VPN server I just set up, tough my laptop and Nexus 7 all works fine. Please advice. Thanks.

---

### Post by jokealot on 2013-03-10
I think it's because this line:
require-mppe-128
in the pptpd-options file.

If I keep this line, my laptop/N7 can connect, but ipod touch can not. While if I comment out this line, I can connect my ipod touch, but my windows laptop get the error message code 628. So question is what to do to make both work? Other options might be involved are set as:
refuse-pap
refuse-chap
refuse-mschap
require-mschap-v2

PS: I got windows connected [COLOR=#333333][FONT=Segoe UI]by select the data encryption type[/FONT][/COLOR] '[COLOR=#333333][FONT=Segoe UI]optional', but I am wondering is this safe?[/FONT][/COLOR]

---

