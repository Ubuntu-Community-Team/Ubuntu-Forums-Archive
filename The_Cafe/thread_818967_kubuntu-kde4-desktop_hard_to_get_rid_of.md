---
title: "kubuntu-kde4-desktop hard to get rid of"
date: 2008-06-04
forum: The Cafe
---

### Post by swoll1980 on 2008-06-04
Just a warning; I installed the kubuntu-kde4-desktop to discover I hated it.
Removing it is a freaking nightmare. You would think sudo apt-get remove kubuntu-kde4-desktop would remove it as it installed it, but that's not the case. I still had tons of kde crap on my computer, and even logged into the gnome environment I was still getting constant knotifcation crash warnings every 5 seconds. I had to go on a kde search and destroy mission which took about an hour, then I kept getting an error about icedtea not being installed or removed so I did a dpkg --configure -a then a dpkg-reconfigure -a which took another hour, but didn't work I have a thread posted in installation on this which I'm sure I'll get help with. To make a long story short if your going to try kde4 I wouldn't do it this way, because if you don't like it your in for a long night. :-#

---

### Post by hanzomon4 on 2008-06-04
Kubuntu-kde4-desktop is just a meta package that depends on everything eles. All you had to do was "apt-get remove auto-remove" or something like that...

Did bush really say that, lol... I'm drunk

---

### Post by Mauldrick on 2009-03-27
I am having the same problem. What is the best way to get rid of this stuff?

---

### Post by chucky chuckaluck on 2009-03-27
the same thing happens when you try to get rid of gnome. both are huge complex packages that take the right approach to dumping. it's not as simple as *sudo apt-get remove 9wm*.

---

### Post by JECHO on 2009-03-27
here is a nice simple way to get rid of it completely: [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by mehaga on 2009-03-27
Luckily, I'll never have to get rid of all that 'crap'. I have 4.2 installed and I love it. Many times better then anything else linux ever had.

---

### Post by swoll1980 on 2009-03-27
necromancy

---

### Post by kevin11951 on 2009-03-28
> **swoll1980 said:**
> necromancy

> The art of revealing future events by means of a pretended
 communication with the dead; the black art; hence, magic in
 general; conjuration; enchantment.
:confused:

---

### Post by DoubleClicker on 2009-03-28
> **swoll1980 said:**
> Just a warning; I installed the kubuntu-kde4-desktop to discover I hated it.
Removing it is a freaking nightmare. You would think sudo apt-get remove kubuntu-kde4-desktop would remove it as it installed it, but that's not the case. I still had tons of kde crap on my computer, and even logged into the gnome environment I was still getting constant knotifcation crash warnings every 5 seconds. I had to go on a kde search and destroy mission which took about an hour, then I kept getting an error about icedtea not being installed or removed so I did a dpkg --configure -a then a dpkg-reconfigure -a which took another hour, but didn't work I have a thread posted in installation on this which I'm sure I'll get help with. To make a long story short if your going to try kde4 I wouldn't do it this way, because if you don't like it your in for a long night. :-#

```
 apt-get remove libqt4-core 
``` will do the job since all the KDE environment in dependent on it.

---

### Post by jwxie on 2009-03-28
I wonder how long did it take this guy to track down all the package there

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by oobuntoo on 2009-03-28
> **swoll1980 said:**
> Just a warning; I installed the kubuntu-kde4-desktop to discover I hated it...

Don't hate it, embrace it :lolflag:

---

### Post by Sand &amp; Mercury on 2009-03-28
If you'd installed using aptitude instead of apt-get you'd be able to remove it with aptitude remove kubuntu-desktop. The only way to get rid of an apt-get install of it is to remove packages one by one, unfortunately.

---

