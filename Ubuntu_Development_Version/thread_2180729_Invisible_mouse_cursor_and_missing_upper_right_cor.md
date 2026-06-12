---
title: "Invisible mouse cursor and missing upper right corner gear icon"
date: 2013-10-14
forum: Ubuntu Development Version
---

### Post by pnarciso on 2013-10-14
Sometimes when I boot ubuntu 13.10 my mouse cursor is invisible, this happened also in daily iso live cd.
Also the upper right corner gear icon likes to dissapear.
This issues are fixed by loging out and loging in.
Have someone experienced these behavior?

---

### Post by zika on 2013-10-14
[URL="http://ubuntuforums.org/showthread.php?t=2175433"]http://ubuntuforums.org/showthread.php?t=2175433
[/URL]Log-out/in does not help at my case or I did not try enough...

---

### Post by mc4man on 2013-10-14
> **pnarciso said:**
> Sometimes when I boot ubuntu 13.10 my mouse cursor is invisible, this happened also in daily iso live cd.
Also the upper right corner gear icon likes to dissapear.
This issues are fixed by loging out and loging in.
Have someone experienced these behavior?

As far as the invisible cursor I've had good luck by disabling the gnome-settings-daemon cursor plugin (been several days & haven't had it re-occur

```
gsettings set org.gnome.settings-daemon.plugins.cursor active false
```
Is there any value to that plugin?, none that I've seen yet

If in fact the plugin is the cause then possibly changing it's priority may also help, here don't care, just made inactive.

As far as no session indicator, no clue, it just doesn't show at times, also see the same for the datetime indicator
seems to happen a bit more often on a ssd boot, but not limited to (slowing down lightdm doesn't help here

---

### Post by zika on 2013-10-14
> **mc4man said:**
> As far as the invisible cursor I've had good luck by disabling the gnome-settings-daemon cursor plugin (been several days & haven't had it re-occur

```
gsettings set org.gnome.settings-daemon.plugins.cursor active false
```
Is there any value to that plugin?, none that I've seen yet

If in fact the plugin is the cause then possibly changing it's priority may also help, here don't care, just made inactive.

As far as no session indicator, no clue, it just doesn't show at times, also see the same for the datetime indicator
seems to happen a bit more often on a ssd boot, but not limited to (slowing down lightdm doesn't help here
It seems that it works... Thank You.
You've made me entry Unity and Fllback again after (quite) some time and now I have to iron many of glitches accumulated.. ;)

---

### Post by pnarciso on 2013-10-14
So Ubuntu 13.10 will be out a couple of days, and this annoying bugs still persist.

---

### Post by zika on 2013-10-14
It seems to be connected also to GnomeTweakTool:KeyboardAndMouseShowLocationPointer... Did not try yet, some work to do...

---

### Post by mc4man on 2013-10-15
A report on cursor visibility is here
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1238410](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1238410)

When the cursor remains hidden & there is  no session indicator then a log out works here though sometimes takes a few.
(-  ctrl+alt+delete probably still opens a log out even though it's now set in compiz to open system-monitor, a bug they shouldn't bother to fix if still open.
Though it seems[ if gnome-screensaver isn't installed]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1237564") then it & custom shortcuts don't work.

---

### Post by zika on 2013-10-21
> **mc4man said:**
> A report on cursor visibility is here
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1238410](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1238410)

When the cursor remains hidden & there is  no session indicator then a log out works here though sometimes takes a few.
(-  ctrl+alt+delete probably still opens a log out even though it's now set in compiz to open system-monitor, a bug they shouldn't bother to fix if still open.
Though it seems[ if gnome-screensaver isn't installed]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1237564") then it & custom shortcuts don't work.
This bug is not what bugged me: I've moved mouse but cursor did not appear...
After turning this switch off I did not have any troubles...
Update&#8321;: But it works now, even if not applied... It is OK now...

---

### Post by GSilvaPT on 2013-10-21
That didn't solve my problem. Still seeing the damn cursor blinking and sometimes it goes out dark and I only know where it is because of the menu animations... Anyone wants to try to help?

---

### Post by cariboo on 2013-10-21
@GSilvaPT, seeing as Saucy has been released, and this sub-forum is for discussion and problem solving of the current development version, I'd suggest you create a new thread in General Help.

---

