---
title: "Where do you mount your storage disks?"
date: 2009-06-21
forum: The Cafe
---

### Post by Creap on 2009-06-21
Where in the filesystem hierarchy do you store your "warez" or whatever you have on your hard drives? I have previously mounted all storage disks in /media, but the Filesystem Hierarchy Standard states about **/media** that: > This directory contains subdirectories which are used as mount points for removeable media such as floppy disks, cdroms and zip disks.

Then what about **/mnt**?
> This directory is provided so that the system administrator may temporarily mount a filesystem as needed. The content of this directory is a local issue and should not affect the manner in which any program is run.
Not a proper place either, obviously. FHS can be read here: [http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

I've seen people using their own root dir, like **/storage**, but I don't particularly like that. I am considering mounting the disks in **/home/user/** somewhere but somehow it doesn't feel right.

Where do you put your stuff?

---

### Post by itreius on 2009-06-21
/media/partition name/

---

### Post by Marshal0505 on 2009-06-21
> **itreius said:**
> /media/partition name/

same

---

### Post by .Maleficus. on 2009-06-21
/mnt/partition name/

---

### Post by RandomJoe on 2009-06-21
On my desktop machine, the extra drives mount to directories in my home directory.  The big RAID array in my server is mounted to /raid.

No particular reason...

---

### Post by Phreaker on 2009-06-21
Usually when I dual boot I mount in
/windows

---

### Post by dragos240 on 2009-06-21
If it's autodetected.... /media

If I mount it, I put it in /mnt

---

### Post by .Maleficus. on 2009-06-21
> **dragos240 said:**
> If it's autodetected.... /media

If I mount it, I put it in /mnt
I suppose this is a more accurate description for me too.

---

### Post by pelle.k on 2009-06-21
**/media**, since that gives a nice shortcut in nautilus (and the desktop if that is how you have it configured).
But, if the partition i mount should be less "visible", i mount it under **/mnt** naturally. Like say a backup partition or such.

It wouldnt matter as much in kde though, as it doesn't prioritize the visibility of partitions based on mount point location as much as gnome, but for the sake of consistency, i do the same there.

---

### Post by sim-value on 2009-06-21
/home/((user))/download

---

### Post by The Real Dave on 2009-06-21
Autodetected drives usually just stay in in /media, with the exception of those that are mounted automatically to /mnt. If I'm a particular job with a disk, like dd-ing an OS install or just copying alot of files for a certain purpose, the drive get its own /drive-name dir. Also do that if I'm handling alot of mounted partitions. Helps me keep track of whats which

---

### Post by lovinglinux on 2009-06-21
> **sim-value said:**
> /home/((user))/download

+1

---

### Post by Dimitriid on 2009-06-21
I don't have windows or external drives I use. The closest thing is when I mount isos for games I will install with wine, in which I use gmount-iso to mount them on /media/cdrom0

It did gave me an error yesterday, Nautilus started complaining about hal disagreeing with unmounting, umount couldn't umount it so I had to reboot.

---

### Post by Eisenwinter on 2009-06-21
My storage disk only stores music, so /Music

---

### Post by SuperSonic4 on 2009-06-21
/media/<LABEL> for data

/mnt/Backup for backing up

However, I'm bored so I might change /media/<label> to /mnt and edit fstab

---

### Post by venator260 on 2009-06-21
/hangar

When I used windows, I named my extra disk Hangar 18, but that doesn't work as a directory name, so /hangar has to do.

---

### Post by Bodsda on 2009-06-21
> **dragos240 said:**
> If it's autodetected.... /media

If I mount it, I put it in /mnt

Thats what I do as well.

---

### Post by billgoldberg on 2009-06-21
For the rare occasion I have to manually mount something, it goes to /media.

---

### Post by Bachstelze on 2009-06-21
> **Bodsda said:**
> Thats what I do as well.

Same here.

---

### Post by swoll1980 on 2009-06-21
In the closet, where no one can see. Couldn't help myself.

---

### Post by Eisenwinter on 2009-06-21
> **swoll1980 said:**
> In the closet, where no one can see. Couldn't help myself.
:lolflag:

I love you, swoll, seriously. LOL

:P

---

### Post by SuperSonic4 on 2009-06-21
> **venator260 said:**
> /hangar

When I used windows, I named my extra disk Hangar 18, but that doesn't work as a directory name, so /hangar has to do.

```
sudo mkdir /Hangar\ 18
``` ;)

Not to mention it's an epic song :KS

---

### Post by H2SO_four on 2009-06-21
> **.Maleficus. said:**
> I suppose this is a more accurate description for me too.

same

---

### Post by hessiess on 2009-06-21
Vairious places, often mount network drives/web servers in the home dir for conviniance. Removeable drives are automounted to /media and my partitions are mounted as / and /home/a/ALL (main user data, one big SVN working copy)

---

### Post by PurposeOfReason on 2009-06-21
It depends, for my computer it is just /storage. But for my server, it describes the drive (which I somehow remember what is on what) so names like /WD750.

---

### Post by hellion0 on 2009-06-21
~/(mount name) - laptops

/media/(mount name) - desktops

/Volumes/(mount name) - if mounting on one of my Macs

(In the case of Windows partitions): /win(version)

---

### Post by Skip Da Shu on 2010-06-30
> **Creap said:**
> Where in the filesystem hierarchy do you store your "warez" or whatever you have on your hard drives? I have previously mounted all storage disks in /media, but the Filesystem Hierarchy Standard states about **/media** that: 

Then what about **/mnt**?

Not a proper place either, obviously. FHS can be read here: [http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

I've seen people using their own root dir, like **/storage**, but I don't particularly like that. I am considering mounting the disks in **/home/user/** somewhere but somehow it doesn't feel right.

Where do you put your stuff?

Well only a year after this post... I'm catching up, usually I'm 2 years out ;-)

Just read a good chunk of the FSSTND doc as was perplexed by the same seemingly exclusive statements about /media and /mnt.  So I went searching for the 'proper' place and found this thread.

I've always mounted extra physical, internal HDDs under /mnt.  Such as on this machine /mnt/data and mnt/data2.  

So I'm wondering by eliminating /media and /mnt are they indirectly saying they should be mounted to root (/data and /data2)?

I think they'll stay under /mnt until I find something a bit more definitive.

---

### Post by NightwishFan on 2010-06-30
I always mount everything permanant to /mnt, and anything temp to /media. Though I am sure there is no difference in any case it is more organized to me. I am quite sure there is no issue making an directory under / as OpenSUSE mounts Windows drives to /windows/c. I have .iso images I need to mount that are not warez, such as my bigbuckbunny dvd.

---

