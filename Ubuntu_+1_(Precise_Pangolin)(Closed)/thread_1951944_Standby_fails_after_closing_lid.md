---
title: "Standby fails after closing lid"
date: 2012-04-03
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by bovender on 2012-04-03
Here's a weird problem that occurs with the Precise Beta on my Thinkpad laptop:

When I close the lid, the machine does not go into standby, but instead crashes: Hardware LED indicators (power, battery, wi-fi etc.) are still on, black screen, no discernible harddrive activity, but the computer is obviously still running. Pressing Ctrl-Alt-Del to kill the X server does not help, and I also cannot switch to console.

Interestingly, standby after Alt-F4 as well as standby after time-out (60 mins) works fine.

Anybody else with this problem?

---

### Post by 2F4U on 2012-04-03
What are your hardware specs? Did you look into /var/log/pm-suspend.log?

---

### Post by OGpmpdog on 2012-04-03
> **lazy_leukocyte said:**
> Here's a weird problem that occurs with the Precise Beta on my Thinkpad laptop:

When I close the lid, the machine does not go into standby, but instead crashes: Hardware LED indicators (power, battery, wi-fi etc.) are still on, black screen, no discernible harddrive activity, but the computer is obviously still running. Pressing Ctrl-Alt-Del to kill the X server does not help, and I also cannot switch to console.

Interestingly, standby after Alt-F4 as well as standby after time-out (60 mins) works fine.

Anybody else with this problem?

Hi, I also have a T61. Suspend hasnt worked since Alpha 2.  However, after this morning's updates, I closed the lid, and Suspend works now!!

My problem is Gnome...Since Beta 2, I've been unable to use Cinnamon or Gnome (neither Gnome3shell nor Classic)...I just get a blank screen, and have to CTRL ALT DEL to restart. 

I thought it would be a bummer to only be able to use Unity...To my surprise, Precise Unity is far more usable than Natty Unity.  Cant believe I just typed that :lolflag:

---

### Post by bovender on 2012-04-04
The crash after closing the lid is reproducible...

```
/var/log/pm-suspend.log
``` does not get any new entries when I close the lid.

I'm using the proprietary NVidia drivers, maybe something is wrong with them in the Precise Beta 2...

In addition the hw specs in my sig, the output of ```
sudo lshw
``` is in the attached file (snipped a few redundant lines to comply with the forum's size limit).

---

