---
title: "[SOLVED] Xubuntu on 4gb USB pendrive running out of space"
date: 2008-12-14
forum: The Cafe
---

### Post by alt3rn1ty on 2008-12-14
Hi all, I have been messing with various installations on a 4gb USB flashdrive. Decided to go with Xubuntu.

I have a problem with space running out during updates, on the filesystem.
There is plenty of space free on the pendrive as a whole (its just one partition fat32), but as I slowly and selectively install updates the filesystem seems to be restricted in its size and runs out without using any of the available free space.

Previously I have gone through the routine of installing then went straight to update manager, as the update progressed eventually it came up with an error out of space and the USB pendrive became un-bootable, so now after re-installing and doing updates I am selectively updating and monitoring free space, if I look at places/usb flashdrive, it has 581mb free (which has not decreased during the updates), but looking at places/filesystem it has only 57mb free (which has been decreasing during updates).

So I can only conclude there is some kind of restriction on the filesystem size.

Does anyone know how to either increase the size allocated to filesystem, or delete old files replaced by updates (for example initrd.img.old, and vmlinuz.old - plus all others which even as admin root user I cannot delete) ?

PS, I also store windows rar/zip files on the stick - Xubuntu has not taken up 3.5 gig if anyone was wondering :)

---

### Post by handy on 2008-12-14
Fat32 has a 4Gb maximum size.

You could go to your package cache & delete it or all but the most recent versions of packages, in case you need to downgrade for any reason.  It's always worth keeping a previous kernel I think.

Your logs could be trimmed or deleted as well.

---

### Post by alt3rn1ty on 2008-12-14
Yep understand the 4gb limit on fat32 which isnt a problem on a 4gb usb stick.

Where do I find the package cache?, I just want to update and then minimize residue from previous versions and/or increase the filesystem to utilize the whole 4gb (my windows rar/zip files can be easily reduced/deleted - but at the moment any free space this would give will not be utilized because of the filesystem size restriction)

Ok I think this needs to be clearer... forget the zip/rar files they can be deleted again.

1 partition, bootable, fat32, 4 gig

Xubuntu installation initially took around 800mb, leaving just under 3.2 gig

After updates just short of 2 gig used leaving 2 gig free

I cant update any further because filesystem only has 57mb free, and will not use the 2gig thats left on the same 1 partition.

Edit: And the method used to install was as per this advice......
[http://www.pendrivelinux.com/2008/11/05/usb-xubuntu-810-persistent-install-windows/#more-654](http://www.pendrivelinux.com/2008/11/05/usb-xubuntu-810-persistent-install-windows/#more-654)

---

### Post by alt3rn1ty on 2008-12-14
Solved it, when you setup the USB stick you have to set the size of the persistence file to include the rest of the space on the USB/partition, I think I must have skipped this bit somehow... oh well alls well that ends well. I reformatted the usb stick and did an install from live cd this time instead of via the windows method, after apt-get install usb-creator, using that you get a slider to designate how much space for the persistence file. So much easier.

Also found I have to sudo su to give myself the extra permissions to rm items - Yep I know I will be careful, and make sure I dont need the files first with a bit of research.

Still cant find the package cache but I suppose will find it eventually.

---

### Post by howefield on 2008-12-14
> **alt3rn1ty said:**
> Still cant find the package cache but I suppose will find it eventually.

var/cache/apt/archives

---

### Post by alt3rn1ty on 2008-12-14
Thanx Howefield, much appreciated.

For anyone else following this.... unless you have a bigger usb memory stick dont follow my solution, and more importantly take the update manager out of the startups.

If like me you want an OS on USB along with files you can access from windows, stay with the original install, (or probably better still use puppy instead of xubuntu). If you extend the size of the persistence file to the full size of the USB stick then windows can access it, but no longer has space to save things to because the persistence file has taken it all (even if within linux it is mostly empty).

:) So yep that means I just had to reformat the thing and set it all up again... why do I get the feeling some of you are hanging back thinking 'see, knew he would get there in the end' and smiling... :P

---

### Post by handy on 2008-12-14
> **howefield said:**
> var/cache/apt/archives

Thanks, I've been off Ubuntu for long enough to forget where it keeps its cache, I knew someone would pipe up with the path. :-)

---

