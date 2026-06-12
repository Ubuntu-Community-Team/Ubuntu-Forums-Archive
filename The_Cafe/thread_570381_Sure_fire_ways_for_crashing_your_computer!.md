---
title: "Sure fire ways for crashing your computer!"
date: 2007-10-08
forum: The Cafe
---

### Post by dickohead on 2007-10-08
Having used Linux for about 5 years now, I've slowly built up a collection of my most hated quirks and oddities with many different distributions, applications and other doo-hickeys. But recently I have been watching most of them slide right off my list.

But one of them has been around longer than any others, and it's by far the most annoying and destructive!!!

Whenever I have Samba shares mounted on my machine, if I suspend or hibernate my machine (or accidentally unplug a network cable), upon resuming the session I can guarantee that my desktop will cease to function. No music will play (from the samba server), my home directory won't load up in nautilus (because of the samba shares mounted inside) and worst of all; doing ye olde CTRL+ALT+BACKSPACE doesn't help either, as there is something wrong with the Samba client (or so it would seem). Even restarting the networking service seems to have no effect.

So I am forced to reboot my computer - and being a Linux lover, I loathe doing this for ANY reason other than a kernel update.

So...

Who else has a pet hate with certain applications and what not that they'd love to have fixed?

Or better yet.. can anyone fix mine or anyone elses?

:D

---

### Post by HermanAB on 2007-10-08
User error.  Don't do that.
:)

---

### Post by dickohead on 2007-10-08
hahahaha, well there's always that!!! Nothing like PEBKAC to kill a computer!

---

### Post by aquavitae on 2007-10-08
By restarting the network service do you mean restart /etc/init.d/networking or /etc/init.d/samba?  Or how about killing samba?

If you want to crash, install loads of beta software, then run them all at the same time.  Nothing quite like it!  What would be interesting is a thread "How to make windows crash".  But maybe that would be too long...

---

### Post by ironfistchamp on 2007-10-08
ForkBomb cha cha cha, ForkBomb cha cha cha.
 
Great fun to execute on your mates websever. Watch his face turn red :p
 
On one of my computers (using Feisty) just running the machine for more than an hour is enough to lock it completely!

---

### Post by aquavitae on 2007-10-08
dickohead: just been googling and it looks like you might be able to even upgrade the kernel without rebooting but editing /dev/kmem.  I don't have the time right now to look into it, but I thought you might be interested.

---

### Post by aquavitae on 2007-10-08
Don't try this!!```
sudo rm -rf /proc
```

---

### Post by Tom Mann on 2007-10-08
Oops too late :(

I think PEBKAC should become the following:

Problem
Resides
In-between
Chair and
Keyboard.

There's always the one of that Non-Techie Computer Chap too... :KS

---

### Post by derekr44 on 2007-10-08
Question: Sure fire ways for crashing your computer
Answer: Install Windows

---

### Post by -grubby on 2007-10-08
open 3 videos in firefox

---

### Post by smartboyathome on 2007-10-08
> **ironfistchamp said:**
> ForkBomb cha cha cha, ForkBomb cha cha cha.
 
Great fun to execute on your mates websever. Watch his face turn red :p
 
On one of my computers (using Feisty) just running the machine for more than an hour is enough to lock it completely!

I got tricked into using that once by a friend of mine who had been using Linux for years. I will never forgive him for it. :lolflag:

---

### Post by tech9 on 2007-10-08
> **dickohead said:**
> Having used Linux for about 5 years now, I've slowly built up a collection of my most hated quirks and oddities with many different distributions, applications and other doo-hickeys. But recently I have been watching most of them slide right off my list.

But one of them has been around longer than any others, and it's by far the most annoying and destructive!!!

Whenever I have Samba shares mounted on my machine, if I suspend or hibernate my machine (or accidentally unplug a network cable), upon resuming the session I can guarantee that my desktop will cease to function. No music will play (from the samba server), my home directory won't load up in nautilus (because of the samba shares mounted inside) and worst of all; doing ye olde CTRL+ALT+BACKSPACE doesn't help either, as there is something wrong with the Samba client (or so it would seem). Even restarting the networking service seems to have no effect.

So I am forced to reboot my computer - and being a Linux lover, I loathe doing this for ANY reason other than a kernel update.

So...

Who else has a pet hate with certain applications and what not that they'd love to have fixed?

Or better yet.. can anyone fix mine or anyone elses?

:D

may I ask why you need to unplug your network connection?

---

### Post by zekica on 2007-10-08
I'm not sure, but using something like:
```
#!/bin/bash
for i in `mount | grep "type nfs " | cut -d " " -f 1`; do
umount $i
done
for i in `mount | grep "type smbfs " | cut -d " " -f 1`; do
umount $i
done

```
and saving it into:
/etc/acpi/suspend.d/20-umount-network-shares.sh

I thing this would help...? You can use:
**umount -fl $i** instead of **umount $i** it it doesn't work as it should.

---

### Post by Officer Dibble on 2007-10-08
> **tech9 said:**
> may I ask why you need to unplug your network connection?

He said "accidentally". :)

---

