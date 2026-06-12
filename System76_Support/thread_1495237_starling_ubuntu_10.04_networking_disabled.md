---
title: "starling ubuntu 10.04 networking disabled"
date: 2010-05-27
forum: System76 Support
---

### Post by superfrogman94 on 2010-05-27
so i lost wireless again for some reason so i tried to use wired to fix it but cannot connect to wired either! :(
 
so i did lshw and found the ethernet is disbled as well as the wireless, how can i enable the ethernet so i can connect to wired to fix wireless? :confused:

---

### Post by thomasaaron on 2010-05-28
Right-click your Network Manager icon and select "Enable Networking."

---

### Post by superfrogman94 on 2010-05-29
Thank you tom! i was also able to install build-essential,install driver,reboot, flip switch, reboot, and now im back in buisiness! :-D

---

### Post by Pykler on 2010-07-01
> **thomasaaron said:**
> Right-click your Network Manager icon and select "Enable Networking."

Yes, it was that easy

---

### Post by ThePeracha on 2010-08-19
I have the netbook edition 10.04, and I can't find the network manager.

---

### Post by isantop on 2010-08-20
It should be on your top panel to the left of the clock somewhere. I believe by default it is the icon furthest to the left before you leave the notification area.

---

### Post by Linux is dümmer als ich on 2010-08-20
i have an awful problem: Network manager is no more in the panel.
I can't find it anywhere because i don't know where to search ist. 
There is no search result displayed whatever i tried.
 
Two serious questions to the ubuntu developers: obviously the network manager is urgently needed to connect to a network. Why is it possible to delete this file from the control panel and there is no way to get it back? It's just ridiculous when ubuntu 10.04 linux is trying to start an "online search"  to find the network manager :lolflag:
 
Do you know any serious reason why there is no automatic repair function for the essentials  in ubuntu 10.04?

---

### Post by isantop on 2010-08-20
Please try the following.

open a terminal (Applications > Accessories > Terminal). Type the following line, followed by enter:
```
mv .gnome .gnome-bak && mv .gnome2 .gnome2-bak && mv .gconf .gconf-bak && mv .gconfd .gconfd-bak && mv .metacity .metacity-bak
```

I know, it looks long and hairy. This will create backups of your configuration, in case something goes wrong. We can use these to restore, so you will at least be able to get back to where you are now.

Next, run the following from that terminal:
```
rm -rv .gnome .gnome2 .gconf .gconfd .metacity
```
This will erase the current configuration, meaning that next time you log in, it will rebuild them from the defaults.

Then log out and log back in again.

---

### Post by Linux is dümmer als ich on 2010-08-20
@ [isantop]("http://ubuntuforums.org/member.php?u=394913")

thx - i'll try and report the results (hope from my ubuntu linux setup ):P)

---

### Post by Linux is dümmer als ich on 2010-08-20
@ [isantop]("http://ubuntuforums.org/member.php?u=394913")  u re my hero :D it works perfect 
THX ! [IMG]http://www.hifi-forum.de/images/smilies/beerchug.gif[/IMG]

---

### Post by Maarek Stele on 2010-08-22
My connection keeps on being disabled after the systems is turned off.  The only way to re-enable it is to go into networking and delete the connections in the list.  I would then reboot again or reconnect the USB network card and the connection would return.

Anyway to keep these settings so that it won't happen again?

---

### Post by isantop on 2010-08-23
Can I ask why you're not using the internal Network Card? The USB one could be causing problems.

---

