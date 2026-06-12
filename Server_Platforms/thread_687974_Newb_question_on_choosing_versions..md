---
title: "Newb question on choosing versions."
date: 2008-02-04
forum: Server Platforms
---

### Post by bdemers on 2008-02-04
Just picked up an old Dell 2450 dual processor w/ PERC3/Si intending to use it for a lo-bandwidth webserver.  I'm thinking that I should use a kernel ver of 2.4.x so that the raid card is supported, as it is not in the newer 2.6. 
Then, of course, to finish off the LAMP configuration, I will need to watch the versions of Apache, MySQL and PHP., the 3 apps needed to run Joomla 
I should be able to follow backwards from Joomla, picking up the version numbers for A, M, and P.  That then should give me the kernel version.  Seems that if I can relate the Ubuntu version, to the kernel, then the Ubuntu CD should have the proper versions of the other components, at least to get me started.

Finally, here's the questions:   
Where do I find the kernel version for each Ubuntu version, and then, the biggy, how do I find downloads for  the older versions of Ubuntu?  I will need the server version so that the multiprocessor is supported. Thanks

---

### Post by cdenley on 2008-02-05
The oldest version of ubuntu still supported is dapper, and runs linux 2.6.15.28. Are you sure the raid card isn't supported anymore?
[http://linux.dell.com/storage.shtml#aacraid](http://linux.dell.com/storage.shtml#aacraid)

> aacraid is included in kernels 2.6.x already

```

cdenley@ubuntu:~$ modprobe -l|grep aacraid
/lib/modules/2.6.22-14-generic/kernel/drivers/scsi/aacraid/aacraid.ko

```

---

### Post by bdemers on 2008-02-05
I've read that link, wasn't sure that it was current, though.  I read in another posting that support for the raid option was removed in the latest kernel.  Until I actually try it, all I can do is go by what I've read.  The posting is in this forum by the way.  I'll try the latest LTS when I get the computer, and then I'll report back.

I do see what you've given me, so I'm a little confused, to say the least.

---

