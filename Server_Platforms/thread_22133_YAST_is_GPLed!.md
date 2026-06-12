---
title: "YAST is GPLed!"
date: 2005-03-25
forum: Server Platforms
---

### Post by vvu on 2005-03-25
I vote Ubuntu/Kubuntu incorporate this into the codebase!  [http://news.com.com/2100-7344_3-5175682.html?tag=nefd_top](http://news.com.com/2100-7344_3-5175682.html?tag=nefd_top) =D>

Not from a developers perspective my user acceptance perspective - enable Administrator to do things even faster and uniformly.

---

### Post by GentleHatemonger on 2005-03-25
Not to be demeaning, but if you check the date on the article - March 18, 2004
compared to today - March 25, 2005, they're over a year apart.

---

### Post by vvu on 2005-03-25
True...my bad  8-[ , I just got excited for a tool like this in Ubuntu!  All the excitemenmt of my first Linux distro - coming from a MS Infrastructure background - this is really a needed tool for Administration of a system in Ubuntu - again Ubuntu rocks in terms of the reach of desktops, but I'd like for it to succeed in the Server space also.

---

### Post by Novack on 2005-03-26
Ubuntu is mainly a desktop distribution, so I don't think that adding server-side graphical configuration tools is a priority. At least we would first need to get all the client side GUI admin tools rolled out (which is what Gnome System Tools are all about).

Though in a part I agree with needing an easy YaST-like configuration tools for setting up some basic server functions. Like a PDC Samba server that authenticates through LDAP and a DHCP service that is connected to DNS service to form a dynamic DNS service. This is all very easy to do using YaST. 

But then again YaST has some major drawbacks, like effectively disabling the manual configuration (if you can't do it in YaST, it's difficult to do it manually). As I understand it (please correct if I'm wrong), starting up YaST after manual configuration can mess up things pretty bad. 

So basically it would need to written from scratch without trying to emulate YaST. We'd need a distro independent "Gnome Server Tools" -like solution in a similar way to what Gnome System Tools are doing for client side.

---

