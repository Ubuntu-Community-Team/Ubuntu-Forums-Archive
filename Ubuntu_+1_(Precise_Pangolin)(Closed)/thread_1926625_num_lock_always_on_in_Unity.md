---
title: "num lock always on in Unity"
date: 2012-02-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Quackers on 2012-02-16
I can't turn it off :( It's a pain holding down the Fn button to type everything normally
I tried the num lk key and Fn + num lk and still no good. I've rebooted and cold booted and still the same.
It's ok when using Windows so definitely seems to be an Ubuntu thing.
Anyone else seeing similar?

---

### Post by dino99 on 2012-02-16
seeing your post i've checked my keyboard to switch numlock, but like yours i cant set it off. Tried to find something logged about that but nothing found :(
Wonder which update have pushed that issue. Latest "onboard" update should not have broken the real keyboard settings.

---

### Post by Quackers on 2012-02-16
Thanks for confirmation dino99. No clue what's caused it. I'll keep holding down the FN key to type, for the moment.

---

### Post by dino99 on 2012-02-16
I've googled around to review the numlock settings but it seems we are playing out of the bleeding edge here :(
On my desktop system i always need it activated, so its not a big issue, but need to find a workaround and report against  (exept the latest lightdm & onboard updates, i only see the recent devscripts to blame)

Launchpad old fix:  [https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/841541](https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/841541)

---

### Post by dino99 on 2012-02-16
bug reported: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/933405](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/933405)

---

### Post by Quackers on 2012-02-16
I've me too'd it. 
Thanks dino99, you saved me the effort of a bug report :-)

---

### Post by dino99 on 2012-02-16
A workaround is to change the key "remember-numlock-state"
in org.gnome.settings-daemon.peripherals.keyboard in dconf-editor to false.

---

### Post by ppd on 2012-02-16
I took the freedom to update the bug with my findings and also to specify the affected package.

So another "workaround" would be to downgrade gnome-settings-daemon, but I would recommend sticking to my other proposal of disabling the above mentioned key in dconf.

---

### Post by cecilpierce on 2012-02-16
Thanks dino99, that did it  :)

---

### Post by Harry33 on 2012-02-16
There is a new gnome-settings-daemo (3.3.5-0ubuntu2)n in repos now.
Just update and the issue is fixed.

---

### Post by TDK800 on 2012-02-16
num lock always on in Unity

---

### Post by dino99 on 2012-02-16
Should be fixed now if your system is updated. Is it an issue only with Unity ? (i dont use it at all)
and the workaround have been posted earlier on this thread in case you still need it.

[http://ubuntuforums.org/showthread.php?t=1926326](http://ubuntuforums.org/showthread.php?t=1926326)

---

### Post by cariboo on 2012-02-16
Merged two similar threads.

---

### Post by Quackers on 2012-02-16
I just ran the new updates and rebooted. My num lk light stayed on!!! Fortunately it turns off when I press the num lk key. That's good :-)
Thanks all.

---

