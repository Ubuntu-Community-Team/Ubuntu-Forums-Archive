---
title: "My experience with the 12.04 upgrade process."
date: 2012-04-30
forum: Testimonials &amp; Experiences
---

### Post by mintplant on 2012-04-30
So the notification for the 12.04 stable release pops up today, after arriving back from the airport and the land of intermittent internet connections. *Oh hey,* I think, *that's finally out. Why not upgrade now?* And I do.

All goes well, until I notice it's been installing the same package for the past ten minutes. Turns out two installers require manual input in the hidden terminal panel to restart a few services... Okay, that's fine. Would confuse the heck out of a normal user, but it's not a problem for me. Carrying on.

Then, much further along in the upgrade process, the same thing happens. Except the terminal shows naught but apt-get output this time, with *libsqlite0* as the last package pending installation. And it remains that way. For two hours. Finally, I get impatient, and close the upgrade window, then restart it.

...Only to receive an error about dpkg still being locked...

...Followed shortly by a total system crash...

...And a kernel panic on reboot.

Well, that was fun. Time to download the latest ISO, scrape out my data (I was on a trip... backups are a bit stale), do a fresh re-install, get the bootloader set up *again*, and try to remember what-all custom packages I had set up.

And I can't help but think... SQLite? Really? *That's* what (seemingly) ruins my day?

Yep. Gotta love 12.04.

---

### Post by garvinrick4 on 2012-04-30
Put in Install CD and boot off of it and use Try UBuntu:
Get internet connection (just make sure firefox is getting on internet)
Open a terminal:
```
sudo fdisk -l
``` (lower Case L)
pick out your Ubuntu Linux install:
I will use sda5 for this[COLOR=Red] you use your own:[/COLOR]

```
sudo mount /dev/sda5 /mnt
```
```
sudo mount -o bind /dev /mnt/dev; sudo mount -o bind /dev/pts /mnt/dev/pts; sudo mount -o bind /proc /mnt/proc; sudo mount -o bind /sys /mnt/sys

```
```
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
```
```
sudo chroot /mnt
```
```
dpkg --configure -a
```
```
apt-get update; apt-get upgrade
```
```
dpkg --configure -a
```
```
exit
```
```

sudo umount /mnt/dev/pts; sudo umount /mnt/dev; sudo umount /mnt/proc; sudo umount /mnt/sys; sudo umount /mnt

```
Now just reboot into Ubuntu install, hope it fixed you up.

---

### Post by mintplant on 2012-05-01
Tried that. Nearly every command, except mount, threw (tons of) errors. Already backing up my stuff; at this point I'm just going to do a fresh install. Far less hassle.

---

### Post by Version Dependency on 2012-05-01
> **mintplant said:**
> ...at this point I'm just going to do a fresh install. Far less hassle.

If you have backups, this is usually the way to go.  If it takes more than a hour or two to fix, I typically just nuke the entire site from orbit and start over.

---

### Post by Tamlynmac on 2012-05-01
> mintplant

Since first installing Ubuntu (7.04) I've found the online upgrade process to be unreliable. I tried it once and it failed miserably. I only do manual installs and always recommend that to new users. With all the variables involved (PPA's, etc.) it's not surprising that failure is an option.

This issue has been addressed many times in this section. I think the consensus has been that the process should be avoided. A search of the T&E will reveal quite a few threads/posts regarding the online upgrade process and feedback.

In my experience, a clean install is the preferable choice. Thus, I totally agree with this statement.
> Already backing up my stuff; at this point I'm just going to do a fresh install. Far less hassle.

Good Luck

---

### Post by garvinrick4 on 2012-05-01
If a user makes a seperate /home partition from their / partition(file system) at install then never have to worry about upgrade method your personals are on different partition. Just make a 10 gig or so / and a big as /home as desired and your swap if desired. When doing fresh install choose the / partition and not to format the /home partition and you are just fine. You can then have all the installs you want using the same /home (always choose not to format or will lose your /home files.) Also when you dist-upgrade does not effect /home.
Always keep backups on any O.S. to be safe. 
Getting the right partition scheme is not a do or die situation but sure is nice when you have a good partition scheme. Learn how to use package "gparted" to make your partitions before you install and use the "other than" at install and install in partitions you made. 
Also learn about Primary,Extended and Logical partitions the 3 available on your basic drive. Just google these items and read about.

#Do not expect a brand new user to start this way but should be a goal in your Ubuntu 
skill sets. 

#This was a short quide for new comers to Ubuntu not specific for any one user.

---

### Post by 3rdalbum on 2012-05-01
> **garvinrick4 said:**
> If a user makes a seperate /home partition from their / partition(file system) at install then never have to worry about upgrade method your personals are on different partition. Just make a 10 gig or so / and a big as /home as desired and your swap if desired. When doing fresh install choose the / partition and not to format the /home partition and you are just fine.

You've been on Ubuntu Forums since August 2009. Since April 2009, Ubuntu has been able to do a clean install in a partition and preserve the existing /home even if it is NOT in a different partition.

So, basically, you've never used Ubuntu in an era when this wasn't possible :-)

Please update your records; you don't need a seperate /home anymore, even for fresh installs. Unless installing a totally different distro that doesn't use the Ubiquity installer.

---

### Post by garvinrick4 on 2012-05-02
> Ubuntu has been able to do a clean install in a partition and preserve  the existing /home even if it is NOT in a different partition.I did not know you could format a partition and not lose the data existing in that partition. I have used multiple partitions and always installed / in a seperate partition than /home so all partitions use the same /home. 
I have always chosen to not format the /home so as not to lose the data. Is there
a selection in Ubiquity to preserve the existing /home in same partition as one formatting
to install new / if not having /home in seperate partition? Or does /home in same partition ignore the formatting procedure?

---

### Post by FormatSeize on 2012-05-03
> **3rdalbum said:**
> You've been on Ubuntu Forums since August 2009. Since April 2009, Ubuntu has been able to do a clean install in a partition and preserve the existing /home even if it is NOT in a different partition.

So, basically, you've never used Ubuntu in an era when this wasn't possible :-)
I haven't either (as is obvious by my Join Date). But I'm curious as to how  this is possible as well. I've (both on accident and on purpose) blown away more /home partitions that should be allowed by law. Maybe this is far off topic, but I don't recall a fresh install that kept any of the stuff that I didn't back up to some sort of external memory. 

Not saying that you are wrong (I'm sure you are right), but what have I been missing? And how is this possible?

---

### Post by BlastXng on 2012-05-03
Some edits for I encountered some of the same things.. 
> **mintplant said:**
> So the notification for the 12.04 stable release pops up today, 

Yep. Gotta love 12.04.

At this point.. I am hosed. I too have experienced the same items you have.. Except mine actually made it the entire way through the upgrade process.. It wanted me to reboot.. So I did what it asked.. 

Now, I get the wonderful new depressing gray screen with the Ubuntu logo and then system locks.. Can't even get into terminal.. Sigh... 

- Tried nomodeset..
Nope
- Tried Recovery
Oh it crashed so hard that it rattled my teeth.. this happened when it was try to enable networking.. Really? You've got to be kidding.
- Trying now one of the other 200 suggestions.. 
At this point, I cannot and WILL NOT upgrade my wifes laptop.. I love the woman I married and I don't need the hassle...... 

I don't want to have to go through a complete re-install.. It took me the better part of three days to get 11.10 running smooth as silk with Ubunut/Kubuntu installed...

---

### Post by BlastXng on 2012-05-04
> **garvinrick4 said:**
> Put in Install CD and boot off of it and use Try UBuntu:
Get internet connection (just make sure firefox is getting on internet)
Open a terminal:
```
sudo fdisk -l
``` (lower Case L)
pick out your Ubuntu Linux install:
I will use sda5 for this[COLOR=Red] you use your own:[/COLOR]

```
sudo mount /dev/sda5 /mnt
```
```
sudo mount -o bind /dev /mnt/dev; sudo mount -o bind /dev/pts /mnt/dev/pts; sudo mount -o bind /proc /mnt/proc; sudo mount -o bind /sys /mnt/sys

```
```
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
```
```
sudo chroot /mnt
```
```
dpkg --configure -a
```
```
apt-get update; apt-get upgrade
```
```
dpkg --configure -a
```
```
exit
```
```

sudo umount /mnt/dev/pts; sudo umount /mnt/dev; sudo umount /mnt/proc; sudo umount /mnt/sys; sudo umount /mnt

```
Now just reboot into Ubuntu install, hope it fixed you up.

Uhmm.. this doesn't apparently work for some reason?

ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
cp: not writing through dangling symlink `/mnt/etc/resolv.conf'

---

### Post by BlastXng on 2012-05-04
garvinrick4....

I tried your list of items and I got some errors along the way or odd spit back.. In any case the update and upgrade ran and I got a new kernal it would appear.. 

however, I'm still hosed...;

now I get the gray screen and a message telling me that it's trying to mount the crypto.. well when I try to perform a manual recovery my system locks up hard.. real hard.. 

This is getting pretty bad..

---

