---
title: "Nero Linux &quot;no device detected&quot; error"
date: 2008-08-13
forum: Ubuntu Studio
---

### Post by godmode117 on 2008-08-13
FIXED: it seems a made a noob mistake, on windows you opt the disc in when ever, but on linux you need to put in the blank disc first,mount it, then open a burning program


hi y'all, i need some help with nero linux. 

When i open up nero linux it gives me a "No device dectected" error.

---

### Post by raffytaffy on 2008-08-13
> **godmode117 said:**
> hi y'all, i need some help with nero linux. 

When i open up nero linux it gives me a "No device dectected" error.

Why not use a linux native burning device such as *gnome baker* or *k3b*

---

### Post by godmode117 on 2008-08-13
> **raffytaffy said:**
> Why not use a linux native burning device such as *gnome baker* or *k3b*

Because I like nero for all its features.

---

### Post by IndyGunFreak on 2008-08-14
> **godmode117 said:**
> Because I like nero for all its features.

What does Nero do that Gnomebaker and K3b do not?  I used Nero religiously as a windows user for several years, and I've found Gnomebaker to be its equal for my needs.

IGF

---

### Post by godmode117 on 2008-08-14
i guess ill try gnomebaker since no one wants to help..

---

### Post by IndyGunFreak on 2008-08-14
> **godmode117 said:**
> i guess ill try gnomebaker since no one wants to help..

Its not that nobody wants to help, its just that using Linux native apps, is going to almost guarantee compatibility, as opposed to opening Wine will run a windows app correctly.  I'd still like to know what features you consider missing from Gnomebaker or K3b.

---

### Post by godmode117 on 2008-08-14
its not that nero has more features (it may or may not) it just im used to using it. btw im not running it under wine, they released a linux version.

Edit: now im having problems with gnomebaker, [http://ubuntuforums.org/showthread.php?t=890004](http://ubuntuforums.org/showthread.php?t=890004)

---

### Post by CrazyG on 2008-08-26
> **IndyGUnFreak said:**
> What does Nero do that Gnomebaker and K3b do not?  I used Nero religiously as a windows user for several years, and I've found Gnomebaker to be its equal for my needs.

IGF

I have been trying to burn 8.04.1 LiveCds for the last 2 weeks, and have used the Nautilus burner, Gnomebaker, K3b and lastly Nero for Linux.  I do not run Windows at all, only Dapper.  Nero was the only program that did not produce "coasters" - the other 3 programs all gave me CDs that produced a number of error messages when trying to use them as LiveCds.  DVD drive is NEC 3520A.  Not trying to start a flamewar here, I just find this odd.

---

### Post by sleepingdragon on 2008-09-03
Whilst I try not to belittle the efforts of any development team, Nero Linux is an *error* in its own right. Poor interface, limited features, and nothing that K3B cannot provide for free.

Sorry, I'll never pay for that quality of software. It's that sort of thing that would drive a person to use free software/Linux... 

Oh, wait...

---

### Post by sunny_nwho on 2008-09-07
Hi mate! I followed what you said but still get the error..does any one still get the same

---

### Post by stinger30au on 2008-09-07
> **godmode117 said:**
> Because I like nero for all its features.


what features????

all the features are in the windows version, not the linux version.

write then a latter and tell them to wake up and release a decent version for linux.

in the mean time use K3B and do everything it does for free


Nero linux 3 is just that.  Version 3 of Nero for linux. Not version 6 or 7 or 8 for that fact.

It is total garbage:mad:

---

### Post by ad_267 on 2008-09-07
A bit off topic but isn't Brasero more up to date and better than GnomeBaker?

---

### Post by CrazyG on 2008-11-20
> **CrazyG said:**
> I have been trying to burn 8.04.1 LiveCds for the last 2 weeks, and have used the Nautilus burner, Gnomebaker, K3b and lastly Nero for Linux.  I do not run Windows at all, only Dapper.  Nero was the only program that did not produce "coasters" - the other 3 programs all gave me CDs that produced a number of error messages when trying to use them as LiveCds.  DVD drive is NEC 3520A.  Not trying to start a flamewar here, I just find this odd.

I had to replace NEC drive (defective) several weeks ago - my issues were probably due to this and not the software.

---

### Post by lmellor on 2008-11-21
> **stinger30au said:**
> what features????

all the features are in the windows version, not the linux version.

write then a latter and tell them to wake up and release a decent version for linux.

in the mean time use K3B and do everything it does for free


Nero linux 3 is just that.  Version 3 of Nero for linux. Not version 6 or 7 or 8 for that fact.

It is total garbage:mad:

Here was me thinking that this was a community led help forum, I guess I was wrong, if it's of any use I'm running intrepid ibex x64 with nerolinux 3, I have had the odd problem with it but generally a restart does the trick.

Can people stop bitching about what's better and what you 'should' be using and just shut the hell up if they're not going to be constructive please? I'm no moderator or anything, which is a good job as you'd be gone by now. If the guy wanted to use something else I'm pretty sure he'd have found something in the Add/Remove programs section by now, it's not rocket science. All you've achieved with your replies so far is to confuse the original questioner to some degree and leave dead end threads like this appear to have had enough responses for the rest of the world to ignore.

There, you've been told, now play nice.

:P

And for the record, nerolinux is my burning app of choice too, I dislike running all the KDE malarky on an otherwise full gnome setup and it does the job marvellously.

---

### Post by fdm on 2009-03-14
i have Nero Linux v3.5.1.0 installed and i love it because of disc errors i more often get with the open-source alternatives. plus it sports a handsome gui like nero 6, the only good version for windows. the "No Devices Detected" problem is you see when you use a crippled account. just load it up with "sudo nero" or change your drive permissions as found here:
[http://club.cdfreaks.com/f104/fedora-9-nero-linux-3-no-drive-254074/](http://club.cdfreaks.com/f104/fedora-9-nero-linux-3-no-drive-254074/)

i know this is an old topic, but here is the answer i needed and came to.

---

### Post by wxnker on 2009-10-01
Rather old topic I know, but this thread helped me solve the same issue recently, so I thought I would share the info.

In Mandriva I solved this by adding the user to the cdwriter & cdrom groups (instead of running NeroLinux as root). I suppose this should work in Ubuntu as well.

---

