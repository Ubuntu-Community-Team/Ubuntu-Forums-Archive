---
title: "What else have we stole from OSX Today?"
date: 2005-10-01
forum: The Cafe
---

### Post by jdong on 2005-10-01
Check out [http://people.redhat.com/dcbw/NetworkManager/](http://people.redhat.com/dcbw/NetworkManager/) -- this is in Breezy Universe (GET HYPED).

It's a HAL/DBUS wireless configuration applet that handles everything from associating to an access point to DHCP of wired and wireless connections. This is perfect for that laptop that frequents hotspots. No more pulling up terminals and iwconfigging/dhclienting. (yes, those are verbs now. geez).


Note that this is an all-in-one replacement for the Debian ifup/ifdown/interfaces(5) system. It includes a preconfigured bind9 DNS server along with special DBUS DHCP  support.


If you're an OSX user, you'll see that this is virtually a clone of OSX's tool.


Weaknesses? (1) DHCP-only, no static IP support. (whether or not it's planned is unclear. If you think about it, static IP's don't make sense in the context of this applet.) (2) No WPA support. The RedHat guys are working on getting wpa_supplicant to work with this. WEP is fully supported, and open vs shared is auto-detected and remembered. (Yea, true, WEP barely fits with the purpose of this applet!)

---

### Post by kiddo on 2005-10-01
Hi there, I'm curious to know what difference there is between that one and my current "netapplet" 1.0.x ? The backend I guess, since from a UI standpoint they look the same:
[[IMG]http://img212.imageshack.us/img212/8841/kitsune200510019ia.th.jpg[/IMG]]("http://img212.imageshack.us/my.php?image=kitsune200510019ia.jpg")

---

### Post by bob_c_b on 2005-10-01
[QUOTE=jdong]If you're an OSX user, you'll see that this is virtually a clone of OSX's tool. Weaknesses? (1) DHCP-only, no static IP support. (whether or not it's planned is unclear. If you think about it, static IP's don't make sense in the context of this applet.) (2) No WPA support. The RedHat guys are working on getting wpa_supplicant to work with this. WEP is fully supported, and open vs shared is auto-detected and remembered. (Yea, true, WEP barely fits with the purpose of this applet!)[/QUOTE]

I saw this demonstarted at Ohio Linuxfest today, people were really hyped up for this program, looks promising.

---

### Post by AgenT on 2005-10-01
Why is that stealing? Is Honda always stealing from Ford because they use rims in cars? Is Ford stealing from the people that made chariots because they use wheels? Are the chariot makers stealing from the cavemen because they too use the wheel?

I think I will tell my local baker that he is stealing from every other baker who is also stealing from every other baker because they all more or less bake the same thing: bread. Those pirates! YAAR!

:rolleyes:

---

### Post by jdong on 2005-10-02
[QUOTE=kiddo]Hi there, I'm curious to know what difference there is between that one and my current "netapplet" 1.0.x ? The backend I guess, since from a UI standpoint they look the same:
[[IMG]http://img212.imageshack.us/img212/8841/kitsune200510019ia.th.jpg[/IMG]]("http://img212.imageshack.us/my.php?image=kitsune200510019ia.jpg")[/QUOTE]

Mostly it's a completeness-of-solution deal. Both are FDO compliant, but NetworkManager is the more promising of the two.


From netapplet's developers:
> 
Netapplet is a hack at best that more or less simply calls “ifup” and “ifdown” on interfaces. It’s 3700 lines of code. We never intended it to be a GNOME solution or even a cross-distribution one. That wasn’t because of any perceived value-add in it, it was because it was a stop-gap measure to fix the problem of switching between wired and wireless networks in SUSE, given tight restraints on development time. Judging from the response netapplet has received in retrospect from SUSE and NLD users, it was a pretty serious problem. Robert and I readily admit that NetworkManager is a more complete solution, and if you look at the list archives over the past 3 months Robert has arguably been the most active developer on NM.

---

### Post by AgenT on 2005-10-02
[quote=kiddo]Linux. Il y a moins bien, mais c'est plus cher.[/quote] 
Faux!

Linux. Il y a **plus** bien, **et** c'est **moins** cher.

;)

---

### Post by emperor on 2005-10-02
[quote=jdong]Check out [http://people.redhat.com/dcbw/NetworkManager/]("http://people.redhat.com/dcbw/NetworkManager/") -- this is in Breezy Universe (GET HYPED).

It's a HAL/DBUS wireless configuration applet that handles everything from associating to an access point to DHCP of wired and wireless connections. This is perfect for that laptop that frequents hotspots. No more pulling up terminals and iwconfigging/dhclienting. (yes, those are verbs now. geez).
[/quote]

I prefer "wifi-radar" which is easier to configure!

---

### Post by BoyOfDestiny on 2005-10-02
[QUOTE=AgenT]Why is that stealing? Is Honda always stealing from Ford because they use rims in cars? Is Ford stealing from the people that made chariots because they use wheels? Are the chariot makers stealing from the cavemen because they too use the wheel?

I think I will tell my local baker that he is stealing from every other baker who is also stealing from every other baker because they all more or less bake the same thing: bread. Those pirates! YAAR!

:rolleyes:[/QUOTE]

Amen. One can say the same about architecture, medicine, hundreds of inventions etc. 
If they didn't take the sourcecode, it's not stealing, it's just imitation, which has the potential to surpass the original. 
It just adds to the monstrous potential of linux.

---

### Post by Kvark on 2005-10-02
As AgenT and BoyOfDestiny already pointed out. And many others prolly will point out too. You really shouldn't use the word "stole" here. OSX still has their network thingy so apperantly nobody has deprived them of it. A more accurate title would have been "What else have we **learned** from OSX Today?".

---

### Post by darkmatter on 2005-10-02
[QUOTE=Kvark]A more accurate title would have been "What else have we **learned** from OSX Today?".[/QUOTE]

Considering they've learned so much from us...

---

### Post by phen on 2005-10-02
it is "moins cher"!

or i dont get the joke?! :)

because the french  language doesn't have a word for cheap. so you need to say less expensive :)

pat.. pat.. on my shoulder, i am a good pupil

---

### Post by AgenT on 2005-10-02
[quote=phen]it is "moins cher"!

or i dont get the joke?! :)[/quote]                                         Désolé! C'est mois cher, bien sûr.
 
[quote=phen]it is "moins cher"!
because the french  language doesn't have a word for cheap. so you need to say less expensive :)[/quote] 
Il y a un mot en français qui est comparable à le mot «cheap»: bon marché.

---

### Post by jdong on 2005-10-02
I personally do think this is stolen (i.e. cloned) from OSX. There are definitely an infinite number of ways of implementing such a manager, and for the UI and behavior to be virtually identical is certainly suspicious ;)


I'm not saying this is a bad thing though. Linux certainly needs applets like this, but if Apple gets ticked, I dont think these authors have any way of denying the resemblance.

---

### Post by Lovechild on 2005-10-02
NM has undergone quite a few UI changes over time, the first releases were very different from the current UI. I've followed it since the beginning, and while I did not know that OS X offered a silimar feature, I sorta suspected that it wasn't entirely new feature as this is really basic functionality that any OS would want, and there are a limited number of ways we can present it.

---

### Post by jdong on 2005-10-02
[img]http://uqconnect.net/images/wireless/osx-quickconnect.png[/img]

You guys be the judge :)

---

### Post by Kvark on 2005-10-02
[QUOTE=jdong][img]http://uqconnect.net/images/wireless/osx-quickconnect.png[/img]
You guys be the judge :)[/QUOTE]
If you have a bunch of network options then it is pretty logical to put them together in a menu. I don't understand how you can see this a theft. It is even more stealing to have for example a right click menu, a menu with shortcuts to the programs, various menues in the top of windows and so on. Other OSes had that before Ubuntu. Should we throw Ubuntu in jail?

---

### Post by jdong on 2005-10-02
It's not like GNOME to organize widgets like that. There are no other GNOME applets that work quite the same. Either way, in the end it's a good thing for Ubuntu :).

---

