---
title: "Problems after upgrade (GNOME, shutdown, install...)"
date: 2013-04-03
forum: Ubuntu Development Version
---

### Post by Kotrfa on 2013-04-03
Hi,

I upgraded my Ubuntu 12.10 to 13.04 and I'm getting terrible time. 

After upgrade (I used terminal version sudo -do-release-upgrade) which worked fine, computer asked for reboot - I did so and the ubuntu didn't started (just blinking cursor and nothing happened) and I couldn't even change the tty by using ctrl+alt+Fx. After hard reset it started well. Then I wanted to install gnome-shell 3.8 using "official way" (gnome3 repository) and it also went ok. But ater reset, lightdm didn't started and "gnome-shell --version" gave me 3.6.1 (and it should be 3.8). I uninstalled everything connected to gnome and try "fresh" install of gnome-shell. Everything worked again (installation), but my theme is broken and I guess there will be maybe more broken things. I tried to install gnome-theme-extra, gnome-themes-extra/standard/ubuntu... But it is still same.

Gnome-tweak-tool says Current theme: Adwaita (default), but it looks like high contrast. Here is screen of my [IMG]http://imageshack.us/scaled/landing/694/screenshotfrom201304031.png[/IMG]

Next problem is, when I try to reboot PC or just using shutdown through upper-right corner, computer doesn't shutdown. It just hangs at "System is going to shutdown for MAINTENANCE  I need tu use "sudo shutdown -h now".

Thanks

---

### Post by dino99 on 2013-04-03
you seems ready for a fresh install

---

### Post by Stinger on 2013-04-03
@ kotrfa
Thanks for posting, you just helped me nail my gdm bug.
It's a dependency problem when upgrading via the Gnome3 ppa leaving 29 packages not upgraded in my case, and gnome-shell at version 3.6.3.1 and gdm at 3.8.0

My bug report:  [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/1162466](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/1162466)

---

### Post by Stinger on 2013-04-03
@ kotrfa
After adding the Gnome3 ppa, you need to ```
sudo apt-get dist-upgrade
``` solved my problem :D
Just learned it from Jeremy.

---

### Post by dino99 on 2013-04-03
> **Stinger said:**
> @ kotrfa
After adding the Gnome3 ppa, you need to ```
sudo apt-get dist-upgrade
``` solved my problem :D
Just learned it from Jeremy.

no need to replicate your false discovery (see your other thread)

---

### Post by Stinger on 2013-04-03
@ dino99
And no need what so ever for you to be rude
What's your problem ?

---

### Post by Kotrfa on 2013-04-03
@Stinger:

It doesn't help:
```
 ~ $ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

@dino99:
My problem is just the missing theme. The reboot/shutdown problem occurs very randomly and I can live with that (and I hope it will get better, when the official release will be shipped). But the appearance is horrible. And I that is problem of Gnome3.8, so why do I need to reinstall whole system?

---

### Post by Stinger on 2013-04-03
@ Kotrfa
Beats me, but you said earlier that gnome-shell --version gave you 3.6.1 and thats not the version from the Gnome3 ppa, it's  GNOME Shell 3.8.0.1 that's why I thought your problem might be related :-k

---

### Post by cariboo on 2013-04-03
It may be a little to late now, but did you make sure the upgrade process had finished properly? Just because it said it was done, and wanted you to reboot, there may still have been unmet dependencies. I haven't bothered to upgrade for years, as it takes less time to do a fresh install, and restore from backups, but when I did upgrade testing, I found that running:

```
sudo apt-get -f install
```

made sure that there weren't any unmet dependencies, or packages that hadn't been fully installed.

At the point you are now, you may still want to run the command I posted, then if you'd really rather fix the problem, instead of doing a fresh installation, you may want to delete the ~/.config directory and reboot, this will remove all your customizations, but will also allow you to start from scratch as far as configuration files are concerned.

---

### Post by Kotrfa on 2013-04-04
@cariboo907
It's clean, nothing is missing

The look is OK now, I reinstalled gnome3. The shutdown problem I will solve later, when I will found any logs etc. Thanks for help.

---

