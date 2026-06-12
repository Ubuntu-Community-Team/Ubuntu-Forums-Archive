---
title: "two network icons on menu bar"
date: 2014-09-05
forum: Ubuntu Development Version
---

### Post by ventrical on 2014-09-05
Anyone else have these ?

How to get rid of one of them ?

---

### Post by bapoumba on 2014-09-05
Would you have network-manager in Default apps for LX sessions > Autostart ?
Running lubuntu 14.10 up-to-date, not this issue here.

---

### Post by ventrical on 2014-09-06
I un-checked it but 2 icons still there.

---

### Post by bapoumba on 2014-09-06
I'm sorry, I was not clear. Network-manager should not be in the manually added list (not shown in your screenshot, manual entries are just above). Can you remove one editing the panel ?

---

### Post by ventrical on 2014-09-06
Add/Remove panel items but the network widgits don't show or I am doing somthing wrong.

---

### Post by ventrical on 2014-09-06
I removed /system tray/  and that got rid of both of them , then I added Manage Networks and now I only have one with icon and info hover. Works for now :)

---

### Post by bapoumba on 2014-09-07
System tray is giving me issues on 14.04.1 (runs fine when I add it but then does not show open applications icons after a logout or reboot), but not on 14.10. Go figure :)

---

### Post by Cavsfan on 2014-09-08
In Ubuntu Utopic Mate 14.10 I don't have 2 network icons but I have 2 dates. The left one I can click on and the calendar shows up. The right one (almost overlapping) serves no functionality that I can see.

[ATTACH=CONFIG]256266[/ATTACH]

I do not see a way to make it go away either. This just started happening a week or so ago.

---

### Post by Cavsfan on 2014-09-09
Nevermind today's updates fixed the double date and no time. It's all good now on Utopic Mate.

Did it also fix your double network icon issue?

Oh wait, I now have 2 volume icons :lol:

[ATTACH=CONFIG]256307[/ATTACH]

I can mute the left one and it makes no difference but the right one does. *giggity*

---

### Post by ventrical on 2014-09-10
I think one is for mic:)

---

### Post by Cavsfan on 2014-09-10
> **ventrical said:**
> I think one is for mic:)

I don't think so lol. They both said Output and a level. But that was before I rebooted. Now I have one volume output and 2 dates again just like before.
A progression and then a regression. :lol:

This is just on Utopic Mate, Utopic is fine.

PS: One nice thing I've noticed about Mate is that when you accidentally make a change to a text file then click Edit and then undo, the * disappears at the top and you don't have to save the file at that point.
I've never seen such coolness. :)

---

### Post by DogMatix on 2014-09-10
I've had issues with lxpanel 'system tray' applets during this testing cycle. Initially I was missing the network icon, this also affected 12.04 Lubuntu. This was fixed. The problem I have had recently is only applicable to booting with systemd, which is, the network icon shows wifi is not connected, when in fact it works fine.

---

### Post by Cavsfan on 2014-09-11
My issue is solved and I now have one each speaker volume control, network icon and the actual date and time. 
This is on Mate and I never have had any problems with regular Ubuntu Utopic 14.10.

Booted into both systemd and upstart and both are good. :)

It was a little aggravating yesterday as I had two dates at the top right and the time was wrong in my conky. :o
But I found a site that told how to make a script on Mate adding 4 additional US time servers to a cron script and apparently that works well.

---

### Post by ventrical on 2014-09-12
> **DogMatix said:**
> I've had issues with lxpanel 'system tray' applets during this testing cycle. Initially I was missing the network icon, this also affected 12.04 Lubuntu. This was fixed. The problem I have had recently is only applicable to booting with systemd, which is, the network icon shows wifi is not connected, when in fact it works fine.

I got this yesterday and still today:

```

Preparing to unpack .../lxmenu-data_0.1.3-1_all.deb ...
Unpacking lxmenu-data (0.1.3-1) over (0.1.2-2) ...
dpkg: error processing archive /var/cache/apt/archives/lxmenu-data_0.1.3-1_all.deb (--unpack):
 trying to overwrite '/usr/share/desktop-directories/lxde-science.directory', which is also in package lxlauncher 0.2.3-1
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Errors were encountered while processing:
 /var/cache/apt/archives/lxmenu-data_0.1.3-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
ventrical@ventrical-Asus-Overclock:~$ 

```

---

