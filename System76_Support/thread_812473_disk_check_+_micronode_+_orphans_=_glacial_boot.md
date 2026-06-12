---
title: "disk check + micronode + orphans = glacial boot"
date: 2008-05-29
forum: System76 Support
---

### Post by gruntlips_ on 2008-05-29
OK, I am stumped on this one, here goes. I just bought a new serval and have barely done anything with it except transfer my files onto sd3.  When I boot about half the time it boots correctly/quickly (under 20 secs).  The other half of the time it either hangs completely or takes 60+ minutes to boot. I remove the quiet from the boot/grub/menu.lst to see what's up and it seems to get caught up doing some kind of disk check on sd3.  The disk check stalls out at various points whereupon it gives back the following error repeatedly:

microcode SW error detected, Can't stop Rx DMA...

and at the beginning of the disk check it says:

Clearing orphaned inode 9502846 (uid=1000, gid=1000, mode=0100600 size=8200)

I understand that ubuntu would like to disk check itself periodically but is there something wrong with my HD (200 GB, 7200) based on these errors or the length of time it takes to check?  At this point it won't skip the disk check at all and it is just toodling around fsck-ing sd3 indefinitely.

Thanks.

- Chris

---

### Post by thomasaaron on 2008-05-30
Sounds like this...
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.24/+bug/226134](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.24/+bug/226134)

Please give us a little more info on your computer:
1. Does it have the 3945 card in it 
```
lspci | grep 3945
```

2. Are you running (K/X)Ubuntu? 

3. 32-bit or 64-bit?

4. Did you install linux-backports-modules onto it?

---

### Post by gruntlips_ on 2008-05-30
Thanks, but that post is all greek to me.  In answer to your other questions:

My serval does not have a 3945 card, or at least the grep command returns nothing. 
I am running Ubuntu 8.04 (not K or X).
It is 64 bit.
I did not install the linux-backports-modules. I don't know what those are.

Thanks.

- Chris

---

### Post by thomasaaron on 2008-05-30
Thanks.

I'll do some more searching on this. Try toggling the wireless switch on the front left edge of your computer to the right. Does the problem persist?

What if you toggle it to the left?

---

### Post by thomasaaron on 2008-05-30
Here is another thread with the same problem. The issue wasn't resolved. But it stopped happening, apparently.

[http://ubuntuforums.org/showthread.php?t=789766&highlight=slow+boot](http://ubuntuforums.org/showthread.php?t=789766&highlight=slow+boot)

It may also be a good idea to try and run fsck on your disk partitions from a live CD. I've seen on the forums where this fixes this problem for some people.

To do this:
1. Boot from a live CD.
2. Go to System > Adminstration > Partition Editor and see what your partition designations are. They will probably be /dev/sda1, /dev/sda3 and /dev/sda5
3. Run fsck for each partition:
fsck /dev/sda1
fsck /dev/sda3
etc...

---

### Post by gruntlips_ on 2008-05-30
Just to clarify, the problem only happens during boot.  I don't notice anything weird after that. I will try it the switch thing during boot a few times and report back.  Thanks again.

- Chris

---

### Post by gruntlips_ on 2008-05-30
Yeah I perused the other thread before I posted and saw that it had stopped but that there was no ready solution.  I will run fsck from a boot disk and post what happened.

- Chris

---

