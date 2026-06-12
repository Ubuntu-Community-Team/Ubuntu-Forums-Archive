---
title: "gnome-characters snap package"
date: 2018-03-03
forum: Ubuntu Development Version
---

### Post by corradoventu on 2018-03-03
On my Ubuntu installed from ISO: Ubuntu 18.04 LTS "Bionic Beaver" - Alpha amd64 (20180301)
I fund 2 different apps for gnome-characters, one from snap and one from bionic/main, both installed automatically.
The app from bionic/main has colored characters while the one from snap has black and white.
Should I report the problem? How to report a bug for a snap package?
```
corrado@corrado-p6-bb-01mar:~$ snap find gnome-characters
Name              Version  Developer  Notes  Summary
gnome-characters  3.26.2   canonical  -      A character map application
corrado@corrado-p6-bb-01mar:~$ 

corrado@corrado-p6-bb-01mar:~$ apt policy gnome-characters
gnome-characters:
  Installed: 3.26.2-4
  Candidate: 3.26.2-4
  Version table:
 *** 3.26.2-4 500
        500 http://archive.ubuntu.com/ubuntu bionic/main amd64 Packages
        100 /var/lib/dpkg/status
corrado@corrado-p6-bb-01mar:~$ 

corrado@corrado-p6-bb-01mar:~$ inxi -SCx
System:    Host: corrado-p6-bb-01mar Kernel: 4.15.0-11-generic x86_64 bits: 64 gcc: 7.3.0
           Desktop: Gnome 3.26.2 (Gtk 3.22.28-1ubuntu3)
           Distro: Ubuntu Bionic Beaver (development branch)
CPU:       Dual core Intel Core i3-7100 (-MT-MCP-) arch: Skylake rev.9 cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 15648
           clock speeds: max: 3900 MHz 1: 800 MHz 2: 800 MHz 3: 800 MHz 4: 800 MHz
corrado@corrado-p6-bb-01mar:~$ 

```

---

### Post by mc4man on 2018-03-03
> **corradoventu said:**
> On my Ubuntu installed from ISO: Ubuntu 18.04 LTS "Bionic Beaver" - Alpha amd64 (20180301)
I fund 2 different apps for gnome-characters, one from snap and one from bionic/main, both installed automatically.
The app from bionic/main has colored characters while the one from snap has black and white.
Should I report the problem? How to report a bug for a snap package?


In general you'd go snap info snapname, if there is contact info that's how you'd report issues.
In this case Canonical produced the snap so .. I dunno
In any event unless they're blind figure they already know there is no color, check out the snap in ubuntu-software, the screenshot is in black & white for the category in question.

---

### Post by corradoventu on 2018-03-03
the screenshot in ubuntu-software is black & white for both apps (see the 2 top screenshot in my attachment)
the 2 screenshot at bottom of my screenshot are the ones displayed starting the apps, the bottom left in color from the 'standard' app, the bottom right black & white from the snap app.
if a snap app should be an 'evolution' of the standard one I'm expecting a better one, not a worse.

---

### Post by mc4man on 2018-03-03
> **corradoventu said:**
> the screenshot in ubuntu-software is black & white for both apps (see the 2 top screenshot in my attachment)
the 2 screenshot at bottom of my screenshot are the ones displayed starting the apps, the bottom left in color from the 'standard' app, the bottom right black & white from the snap app.
if a snap app should be an 'evolution' of the standard one I'm expecting a better one, not a worse.
Well of course the ubuntu-software screenshot would be in b&w, it's of punctuation.
As far a "a better one", cheaper is rarely better..

---

### Post by mc4man on 2018-03-04
This is probably as good a place as any for questions/issues, ect. when the contact info is useless..
[https://forum.snapcraft.io/c/snap](https://forum.snapcraft.io/c/snap)

---

### Post by jbicha on 2018-03-04
> **corradoventu said:**
> I fund 2 different apps for gnome-characters, one from snap and one from bionic/main, both installed automatically.


Yes, it's pretty easy to have duplicate apps for these apps where Ubuntu is switching to the snap by default. I think this will be handled for those who use the official upgrade tools once 18.04 is released. (If you're already using 18.04, you'll probably need to do manual cleanup or consider reinstalling later.)

> **corradoventu said:**
> 
The app from bionic/main has colored characters while the one from snap has black and white.


Good catch. I reported this as [LP: #1753146]("https://launchpad.net/bugs/1753146")

> **corradoventu said:**
> 
Should I report the problem? How to report a bug for a snap package?


Yes, please do report bugs for snaps. Here's a [chart]("https://forum.snapcraft.io/t/snaps-officially-supported-by-canonical/1719") to help you know where to report bugs for Canonical-maintained snaps.

It looks like you just report the bug against the Ubuntu package name in Launchpad but add the 'snap' tag for most of these.

Alternatively, you can use the Snapcraft forum to report some issues. For instance, it looks like Snaps can't be used as GNOME Shell search providers yet. Since that will require more coordination, [that issue]("https://forum.snapcraft.io/t/gnome-shell-search-providers/4322") was reported there.

---

### Post by corradoventu on 2018-03-05
@jbicha: i don't reported the bug against the Ubuntu package name in Launchpad (which is?), but now just signed for your bug.
thanks

---

### Post by jbicha on 2018-03-14
The black and white emoji issue has been fixed now. You can manually run
```

snap refresh

```

to ensure you get the update. Otherwise, I believe it will happen automatically in a few hours.

---

### Post by corradoventu on 2018-03-14
thanks a lot, i've already noted on the bug: [https://bugs.launchpad.net/ubuntu/+source/gnome-characters/+bug/1753146](https://bugs.launchpad.net/ubuntu/+source/gnome-characters/+bug/1753146)

---

