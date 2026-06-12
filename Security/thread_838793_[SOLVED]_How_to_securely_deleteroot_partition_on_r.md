---
title: "[SOLVED] How to securely deleteroot partition on remote machines?"
date: 2008-06-23
forum: Security
---

### Post by syncrondi on 2008-06-23
I have a remote system I'll be ending use on and I was wondering how I could overwrite or delete securely the root partition while mounted since I can't pop in a live cd.

I really need to securely delete the mysql databases, but I would feel good to just trash the whole disk.

I understand that dd could be used to overwrite the data with zeros, but will this work on a mounted partition?

Any ideas would be helpful. Thanks.

---

### Post by p_quarles on 2008-06-24
Most types of network access to that hard drive will rely on it running software that tells it to serve files over the network. Attempting to securely delete on such a drive would be ridiculously unreliable, as it's likely to cut off access before deleting all the important stuff. 

The only thing I can think of here would be kinda crazy: it might be possible to netboot a live environment and then run the machine without mounting its hard drive. This would, I believe, require a customized live environment that would load the network services required to perform these operations remotely. 

Needless to say, this could get quite complicated. My advice, in order of preference:
1) Get someone to rip that HDD out and mail it to you
2) Run "shred" on everything important (i.e., the MySQL DBs).

---

### Post by /etc/init.d/ on 2008-06-24
Wiping just the partition where the databases are would almost certainly not be a reliable erase.  You would at minimum also need to wipe the swap partition(s).  To have confidence, you should wipe the entire drive.

Take the drive out and put it as a secondary in another system.

Or, if the machine has a floppy (or a USB port and a USB floppy drive), use a DOS boot disk and [HDDErase]("http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml").

Running "shred" on just the databases would not be reliable.

---

### Post by hyper_ch on 2008-06-24
as p_quarles said you would probably need to run an independant initrd. I have written a few days ago how to create one that can be logged into through ssh from a remote connection (and unlock encrypted root drives).

You'd need to modify that so that "shred" or "dd" will be included...

Steps would be

(1) create an own boot partition
(2) create an own initrd with "shred" or "dd"
(3) login through ssh and unmount the root partition
(4) run "dd" or "shred" over it... dd can be applied to the whole partition... not sure about shred.

---

### Post by syncrondi on 2008-06-24
> **p_quarles said:**
> Most types of network access to that hard drive will rely on it running software that tells it to serve files over the network. Attempting to securely delete on such a drive would be ridiculously unreliable, as it's likely to cut off access before deleting all the important stuff. 

Yep. I tried this in a virtual and it looks like dd cuts everything out before finishing the job and then segfaults. I would say that it was mostly successful because I tried to mount the partition and was unable to do so. In short, good answer, but I think **hyper_ch**'s idea is best for the remote situation. 

> **hyper_ch said:**
> as p_quarles said you would probably need to run an independant initrd. I have written a few days ago how to create one that can be logged into through ssh from a remote connection (and unlock encrypted root drives).

Can you point me to one of your writeups? Thanks!

---

### Post by hyper_ch on 2008-06-25
search --> advanced search --> search for threads by user ;)

---

### Post by syncrondi on 2008-06-25
> **hyper_ch said:**
> search --> advanced search --> search for threads by user ;)

Thanks ;)

---

### Post by hyper_ch on 2008-06-26
so you were able to make that work=

---

