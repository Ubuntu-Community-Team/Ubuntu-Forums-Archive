---
title: "rm -rf * = OMFGWTF!"
date: 2007-04-03
forum: The Cafe
---

### Post by FoolsGold on 2007-04-03
A friendly tip of advice, or a reminder, either way:

If you want to delete the contents of a folder and all folders contained within using a terminal, **for goodness sakes** be careful of how you type things.

[FONT="Courier New"]rm -rf .uplink/*[/FONT]

is right.

[FONT="Courier New"]rm -rf .uplink/ * [/FONT]    (note the space)

is **bad**, particularly when run in your home folder. :mad: 

For the record, not much damage was done. Once I noticed my desktop icons suddenly disappear I realized what I had done and aborted the rm quickly. Fortunately all that was deleted was the Desktop folder and half of a temp folder I had set up. If I had let it go a few seconds longer, the hidden files would be next, which would be interesting.

So, what other catastrophic or near-catastropic stuff have you done in Linux?

:popcorn:

---

### Post by total wormage on 2007-04-03
yesterday i formatted my backup hard disk, being very sure i had all my files spread on an other hard disk, i moved and deleted all my stuff to my secondary backup hdd

rebooting after a failed attempt to install windows on the formatted disk my feisty told me my home folder was non-existing
as it was a messy install i would rather reinstall feisty then figure out what went wrong and try to fix it
but during the install  i began to sweat, realizing that my home folder was a symlink from one of my two 'backup' hdd's, i thought maybe i selected the wrong hdd to format, and since i deleted all my files i would be in a total loss

but i didn't :p
got my files now spread over three hdd's, this wont almost happen again
:lolflag:

silly story btw, confusing too, sorry. i also don't know _what_ went wrong... silly things

---

### Post by ice60 on 2007-04-03
you can do **rmdir -p .uplink** tab, tab, tab etc to remove that directory and its contents. i think that's why they made rmdir so you don't end up making that mistake, i'm not sure though :confused:

---

### Post by heimo on 2007-04-03
Some people prefer to make rm an alias to mv, which is set to move the files to some directory (probably emptied by a cron job periodically).

Worst things I've managed to do? Removed some of the base system packages, like coreutils (cat cp echo ls rm etc.), several times I've messed up package management database, formatted wrong partition, and many many years ago I once installed Debian system, managed to mistype root's password twice during install (creating root) and wasn't able to login after first boot (or maybe I just forgot the password). Oh, and the classic one (some friends of mine could identify me based on this), I was working on a Windows system with KVM (keyboard video mouse switch), where also a Debian server with dozens of users was running, and "logged in" with ctrl-alt-del without checking which computer was selected, instant reboot and lots of friends. ;)

---

### Post by insane_alien on 2007-04-03
while not exactly a catastrophic thing in linux, (it was more of a hardware thing) i accidentally destroyed my laptop at a component level by setting off a nice big electromagnet near it. appart from immediately vapourising anything even remotely resembling a chip it also warped the chassis. GO ME!

---

### Post by bashologist on 2007-04-03
Yep, I've done something like that before.

You seem to know, but I'll mention it since you didn't; It happens because filenames are seperated by spaces.

Like in the man page:
```
rm [OPTION]... FILE...
```
The three leading periods mean it can accepts more than one filename.

---

### Post by fuscia on 2007-04-03
can't you just right-click on your home folder and select 'delete'?

---

### Post by finferflu on 2007-04-03
What I have done, back in my Knoppix times was a rm -rf FOUND* in my ex-Windows folder, and they were actually system files, don't know exactly what, but I managed to wipe all my Windows install (the thread is still there, [check it out]("http://www.knoppix.net/forum/viewtopic.php?t=24624&highlight="), it's fun when it's only an old memory). Very very bad, since I used to share that machine with a friend of mine, and some of the files belonged to him. The positive thing though, was that it encouraged me not to install Windows anymore. I'm 100% Windows free since 21st June 2006 :D

---

### Post by karellen on 2007-04-03
I use "rm -i filename" or "rm -r dirname". never "rm -rf"

---

### Post by bastiegast on 2007-04-03
When I just started with linux I learned about how you could mount any partition at any point, so I thought it might be fun to mount some of those strange directories on another place (Yeah! Great Fun! /sarcasm) I edited fstab to mount I believe the /usr dir on another place. I rebooted and was surprised to be greeted with a error storm and a nice intimidating black maintenance shell.
Another time in my n00b days I tried to compile a new version of XFree86 from source and install it but that's another story...

---

### Post by DoctorMO on 2007-04-03
rm -fr * won't remove any hidden files only normal ones.

---

