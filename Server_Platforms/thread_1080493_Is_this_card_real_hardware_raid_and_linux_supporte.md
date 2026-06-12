---
title: "Is this card real hardware raid and linux supported?"
date: 2009-02-25
forum: Server Platforms
---

### Post by alkisx on 2009-02-25
The card I am talking about is:

Supermicro AOC-LPZCR3

Is its raid real or fake?
On the site it sais it supports only suse and redhat. Will be detected by ubuntu? On their drivers list on the site I see their names started with aacraid*. I think this is supported.

Does anyone knows if this card will work on Ubuntu,debian or slackware?

After lots of failures already with the onboard fakeraid and 2 other cards, I must find something that works.

Thank you.

---

### Post by windependence on 2009-02-25
> **Compatible Operating Systems** 												 													
[LIST]
[*]Microsoft Windows XP / 2000 / 2003
[COLOR=#FF0000]For Windows 2003 Server, please install the driver from the CD instead of the default driver in Windows.[/COLOR]
[*]Linux SuSE 9.0 / 9.1 / 9.2, RedHat 3.0 / 4.0
[/LIST]


I am sure this is the real deal. It has a 600MHz Intel processor on board, battery backup, etc. 

The aacraid driver is an Adaptec driver that supports a fair number of cards. Linux != Windows. You don't have to load drivers for everything because they are included and sometimes built right in to the kernel. The OS will detect the card and load the driver as a kernel module in most cases. The driver is already present in the kernel so there is no need to load the driver manually. It should work fine for you, and even if you have to load the driver, you can convert the rpm file into a .deb package in most cases.

-Tim

---

