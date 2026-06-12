---
title: "Hotspot testing platform"
date: 2008-10-10
forum: Server Platforms
---

### Post by kritro on 2008-10-10
Hello
I'm in a project to set up a wlan hotspot system based on freeRadius, coova-chilli and some web portal like drupal.

Now I have an Ubuntu server that I want to set up a test envirement. I'm thinking using two ethernet interfaces, one with internet connection and one that the client can use to access internet, througt the server after authentication. 

I have no Access Point at the moment so I will use a wired connection as described over first if possible.

Do I need to use some router software in ubuntu to make the server act as a router?

I wondered if someone could tell me if this is possible and what software I need to make it happen.

I just need a push in the right direction so I can start working with it.

Thanks
kritro

---

### Post by abean on 2009-11-18
I know this is an old post but I thought I'd answer anyway...

You can definately set up a hotspot with what you have, and use the access point.


Since I assume your new to all this stuff, try easyhotspot, [http://easyhotspot.sourceforge.net/](http://easyhotspot.sourceforge.net/)

This lets you install a distro of kubuntu and works out of the box. Let me know if you find this useful :).

They do have some problems like the currency is jp rather than dollars etc.. but that is all changeable.

Only thing is make sure you don't have any router capability interfering, for example dont enable DHCP on your access point if your using easyhotspot to assign IP addresses :).

---

