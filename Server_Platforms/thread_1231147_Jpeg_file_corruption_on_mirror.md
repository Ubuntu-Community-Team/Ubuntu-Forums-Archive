---
title: "Jpeg file corruption on mirror"
date: 2009-08-04
forum: Server Platforms
---

### Post by msknight on 2009-08-04
Hi Folks,

Situation - Ubuntu server 8.04.2

Two 750 gig hard drives paired as a mirror /dev/md1

Today I've noticed that there is considerable damage to various Jpeg files in a folder and sub folders of it. Not all the Jpegs, but the majority.

The files appear to be there and are of the correct size. Permissions have been checked but not even the local machine is able to decode them.

Various Jpeg recovery programs have been tried but have failed.

*) The shear number of jpegs and the selective area and sub-folders that have been trashed leads me to believe an operating system issue rather than a virus.

*) Also supported by the fact that some odd files survived.

I've unmounted and run fsck but it says the filesystem is clean. File permissions have been double-checked and seem fine. No odd messages in /var/log/messages

We do get occasional power cuts and I can only think that a power cut took the files out and I've just been adding good files in there over time. The system is set to power itself back on once power returns and presumably auto-checks itself on so doing.

This is plausible, but how come the files are the correct size, etc. and the file system itself is intact? It also seems locallised. It is strange.

Fortunately, I think I have an off site backup that is old enough to still have these files on it, but I don't like mysteries like this where my data is involved; particularly as I'm a photographer and value my images.

Anyone have an opinion please?

---

### Post by grantemsley on 2009-08-04
RAID does not protect against data corruption...in fact, in some cases, it can make the problems worse.

Run the manufacturer's hard drive diagnostic (usually comes on a bootable CD) on both drives.  If they have errors, even if they are correctable, replace the drive(s).

Get a UPS...power failures can do very strange things to computers. You can have the power fail a hundred times and nothing go wrong...then that 101th time your filesystem craps out completely.

Are you sure it is just JPEG files being corrupted?  If it is, I would think it more likely to be software problems - maybe a program not saving the files correctly?

---

