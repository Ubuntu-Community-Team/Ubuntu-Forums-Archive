---
title: "Firestarter - problem with active connections"
date: 2005-07-11
forum: Server Platforms
---

### Post by peter07 on 2005-07-11
I've just installed firestarter. I'm using DSL network connection ( called 'neostrada'). Everything had worked fine untill I set Firestarter to load automatically when I log.
It is working, but I can't see active connections ( for example when I use firefox). Active connections box is always empty

Why?? How can I repair it ??

---

### Post by acascianelli on 2005-07-11
Open firestarter and goto... 

Preferences -> Firewall -> Network Settings

...Check to see if one of the other devices in those drop down menus work.  I have a feeling that Neostrada created another network device for it to use.

---

### Post by peter07 on 2005-07-12
In my PC I have two network devices:

1)ordinary modem - which I don't use
2) ADSL modem - this is my primary device ( neostrada )

I've checked Preferences -> Firewall -> Network Settings and there are:

1) Dialup device  -  ppp0
2) Ethernet device  -  eth0
3) Ipv6 Tunnel  -  sit0

When I was run wizzard I could read tip:
> 
"Tip: If you use a modem device name is likely ppp0. If you have a cable modem or a DSL connection, chose eth0. Choose ppp0 if you know your cable or DSL operator uses the PPPoE protocol"

Then I searched the web and I asked my fiends what should I choose. I have choosen ppp0, becouse I think neostrada is running on PPPoE protocol ( but I can't find some english manual for you - only polish sites). And when i started my connection - modem was working. I set startup persistence (Preferences -> Firewall). I chose start/restart firewall on dial-out and on DHCP renewal. I had also list of active connections. I could see everything. Then I set firestarter to start with whole system ( using firestarter manual ). Firestarter is still working, but active connections box is always empty.


EDIT

I've just made some new tests. I turned off my internet connection and then I turned off firestarter. Then I restarted firestarter and I reconnect to the Internet. Then I noticed that active connections box was working. I could see active programs. 

Could somebody tell my why firestarter doesn't work when it starts with system start? My internet connections starts with the system also. I can't manualy starts firewall.

I've send email to Firestarter team - but with no respond.

---

### Post by peter07 on 2005-07-14
I've searched everywhere. I've checked mailing list, forums but I can't find any solutions.

Many other users have the same problem:

[http://sourceforge.net/mailarchive/message.php?msg_id=11061491](http://sourceforge.net/mailarchive/message.php?msg_id=11061491)

[http://sourceforge.net/mailarchive/message.php?msg_id=11924533](http://sourceforge.net/mailarchive/message.php?msg_id=11924533)


How turn this avtive connections option on  ??

---

