---
title: "Ventrilo Issue - Hotkey not working"
date: 2008-12-28
forum: Wine
---

### Post by europa on 2008-12-28
I finally took the time to switch to ubuntu amd64 but now i'm having issues with ventrilo.

I installed from memory at first, then followed the many guides i've found here and on google but i'm still having the same problem.

Ventrilo isn't detecting my hotkey. It doesn't matter if I have the ventrilo window selected or not. I can here everybody just fine, but when i press my hotkey, my mic doesn't light up and my mic does not transmit. 

I have taken the file needed from a windows installation and updated my system.ini file.


One thing I noticed was that when I try to switch to the GSM codec, I get an error and it changes back to speex.

Here is a screenshot:

[[IMG]http://img241.imageshack.us/img241/8928/ventah2.th.png[/IMG]](http://img241.imageshack.us/my.php?image=ventah2.png)

Any ideas? I had this working fine before.

---

### Post by europa on 2008-12-29
solved:
[http://ubuntuforums.org/showpost.php?p=6093739&postcount=3](http://ubuntuforums.org/showpost.php?p=6093739&postcount=3)

sudo killall pulseaudio

---

