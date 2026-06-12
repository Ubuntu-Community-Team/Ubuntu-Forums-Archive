---
title: "Virus scan my windows partition from my Ubuntu partition???"
date: 2009-06-17
forum: Security
---

### Post by Dwiman89 on 2009-06-17
Hay, My windows partition is all infected with viruses/trogens or whatever,  and that AVG wont remove them. Is there a virus scanner for linux I can sue to scan that partition? and or a way to get rid of them from the Ubuntu side?

---

### Post by lisati on 2009-06-17
AVG free comes in a Linux-friendly version. There are also other Linux-friendly AV scanners, including Avast and clamav

---

### Post by Dwiman89 on 2009-06-17
I tried installing ClamAV but I cant figure out how to use it for scanning files, there is no GUI.

---

### Post by renkinjutsu on 2009-06-17
would those AV even scan windows binaries for windows viruses?
you can TRY using your AV through WINE ... also COMODO is a good open source windows AV you can try using

---

### Post by lovinglinux on 2009-06-17
Unlike AVG, [BitDefender](https://help.ubuntu.com/community/BitDefender) can cleanup the viruses, works fast, it is easy to update and has a nice gui.

---

### Post by Chronon on 2009-06-18
> **Dwiman89 said:**
> I tried installing ClamAV but I cant figure out how to use it for scanning files, there is no GUI.

I use KlamAV.  It's a KDE front-end for ClamAV.  I'm beginning to question whether or not it's worth it, though.  I rarely boot into Windows and I have to deal with false-positives from time to time.  It seems to trip over certain files left over from a build directory.

---

### Post by Awaneendra on 2009-06-18
> **Dwiman89 said:**
> Hay, My windows partition is all infected with viruses/trogens or whatever,  and that AVG wont remove them. Is there a virus scanner for linux I can sue to scan that partition? and or a way to get rid of them from the Ubuntu side?

Hello, I would suggest you to install the latest version of Avast AV. You can go for free home edition. After installing it on windows xp select boot time virus scan, boot time scan removes all the viruses.

Cheers,
Awaneendra

---

### Post by HermanAB on 2009-06-18
I prefer cleaning up Windows with a Windows bootable CD:
[http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)

---

### Post by Cheesemill on 2009-06-18
> **renkinjutsu said:**
> would those AV even scan windows binaries for windows viruses?

All AV programs for Linux **only** scan for Windows viruses.

---

### Post by munky99999 on 2009-06-18
> **renkinjutsu said:**
> would those AV even scan windows binaries for windows viruses?
you can TRY using your AV through WINE ... also COMODO is a good open source windows AV you can try using
They would scan for what otherwise?

Obviously they are meant for windoze viruses.

Now I have bitdefender on my main machine that hosts all the windows go through stuff... like samba sharing and such. Hard to beat that. Gui is sleek and nice.

Clamav does have a gtk gui in the repos. Though not that great. You are far better using commandline.

Easy enough to operate so as long as you know how to use the commandline and check out the manpage or --help.

As for scanning windows partition; mount it then simply scan it from commandline

clamscan -i -r /media/disk

or whatever.

-r makes it go recursive in that then it scans everything.
-i makes it so it doesnt spam you with not-found.

---

### Post by ankur1993 on 2013-01-31
how to scan virus through ubuntu in window partition?

---

### Post by howefield on 2013-01-31
Old thread closed.

Feel free to start a fresh one, although a search of the forum might yield you quicker results.

---

