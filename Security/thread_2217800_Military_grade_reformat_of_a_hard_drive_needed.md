---
title: "Military grade reformat of a hard drive needed?"
date: 2014-04-18
forum: Security
---

### Post by Heeter on 2014-04-18
Hi all,

I am selling an old laptop with an 80gig HD in it. I would like to reformat this drive to the point that nothing can be undeletable/recoverable from it after it is done. Will be installing Ubuntu after the reformatting is done.

What can I use to securely reformat this HD? I can take it out and reformat it using my other Ubuntu laptop if needed.

Thanks

Heeter

---

### Post by sefs on 2014-04-18
> **Heeter said:**
> Hi all,

I am selling an old laptop with an 80gig HD in it. I would like to reformat this drive to the point that nothing can be undeletable/recoverable from it after it is done. Will be installing Ubuntu after the reformatting is done.

What can I use to securely reformat this HD? I can take it out and reformat it using my other Ubuntu laptop if needed.

Thanks

Heeter

boot with a live cd on system and pop open a termainal

sudo fdisk -l  to see devices and make sure to note correct device you want to wipe

assuming the device you want to wipe is /dev/sda for instance then the command below is good enough. It wipes random info to the drive.


sudo dd if=/dev/urandom of=/dev/sda bs=1M

OR 

sudo dd if=/dev/zero of=/dev/sda bs=1M  <--- this will just write zeros, which is equally as good.  I use this.


NB: take caution in running above command as you will lose all data permanatly on the targeted drive.

---

### Post by Heeter on 2014-04-18
Awesome, Thank You, sefs


Heeter

---

### Post by sudodus on 2014-04-18
There is a faster method, that uses hdparm. See this link [best way to wipe a drive]("http://ubuntuforums.org/showthread.php?t=2124829")

---

### Post by david98 on 2014-04-19
+ 1 for hdprarm a very useful and easy to use  and will totally destroy any data with no way to recover it with any data recovery software.

---

### Post by Danger_Monkey on 2014-04-21
I've used both shred and hdparm.  Both are very good at destroying all data, so always make absolutely sure you want it gone.  You have the option of writing zeros over the sectors.  In my testing, I was not able to get back any data from this:

```

shred -n 4 -vz /dev/sda

```

---

### Post by QIII on 2014-04-21
DBAN has a selection to meet MILSPEC DoD 5220.22-M, if you are interested.

Don't use it on an SSD, though.  It'll render it inoperable.

---

