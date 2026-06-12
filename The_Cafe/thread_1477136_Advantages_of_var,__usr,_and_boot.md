---
title: "Advantages of /var,  /usr, and /boot?"
date: 2010-05-08
forum: The Cafe
---

### Post by Sef on 2010-05-08
What are the advantages of /var  /usr, and /boot?   I have seen partitioning like that before, but I really do not understand what advantages that they give user or business.

---

### Post by jbrown96 on 2010-05-08
/bin and /usr are the places where executables exist on the system. If you put them on their own partitions, then everything else could be mounted noexec, which is good for security. 

Almost all server stuff gets stored in /var (apache pages, MySQL DBs, logging, etc.). Typically that info is fairly static, or in the case of logging, not tremendously important. Therefore, ext2 is a good option because it is so fast -- no journaling overhead. If you run a server, then this directory tends to be very large, and may require dedicated storage. 

A separate /boot is mainly used for unsupported / file systems. Grub1 has no support (without patches) for booting from ext4 devices, so if you want / to be ext4, then /boot needs to be a supported file system like ext2/ext3. Except when doing updates, then /boot never changes, so mounting ro offers security advantages.

Another advantage of having separate file systems is that in the event of a crash some file systems may be corrupted. typically, data loss does not occur, but fscks may be required. If not all systems have to be checked -- because of chance or ro mount options, then recovery time may be improved. 
The downside is that you need to know your storage constraints very well at install time. You can get around this by LVMing all your storage and carving up storage that way. It does give flexibility, but it's a lot of work. 

On a desktop system, there's no advantage to creating so many partitions.

---

### Post by Sporkman on 2010-05-08
> **jbrown96 said:**
> Another advantage of having separate file systems is that in the event of a crash some file systems may be corrupted. typically, data loss does not occur, but fscks may be required. If not all systems have to be checked -- because of chance or ro mount options, then recovery time may be improved.

I believe that separate partitions also improves apparmor-type security by disallowing hard links across partition boundaries.

---

### Post by koenn on 2010-05-08
what jbrown said. 

In addition to that, the filesystem hierarchy is in fact organised so that you can mount some things read-only, or no-exec, while other directories (-> mount points -> partitions) are writeable. Eg keeping your software read-only can help protect against rootkits etc, and that works because other dirs eg logs, tmp, ... are still writeable.


The other use case is when you mount stuff off nfs servers (eg /usr ) -> programs that may be needed during startup before nfs mounts are possible, will be in /bin and /sbin

disk qouta, iirc, depend on partitions, as does the "x% of disk space reserved for root", i.e. the x% can vary per partition, so if you have special plans for /var, you'd give it its own partition ...

---

### Post by Xbehave on 2010-05-08
/usr is pretty static so i can mount it ro (this a tiny bit is good for security, but also prevents anything messing up my system by mistake)
/var is fairly dynamic but i can mount it noexec and limiting it's size makes sure i empty my caches every so often
/boot is not used after booting so i don't mount it (see /usr) and it is also nice when dual booting to have the kernels in one safe palce.

---

### Post by oldfred on 2010-05-08
If you have a old computer with BIOS limits you might need a /boot at the beginning of the drive.  Otherwise it seems to add complications in managing boot.

[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_boot_partition](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_boot_partition)

---

### Post by jbrown96 on 2010-05-08
> **Xbehave said:**
> /usr is pretty static so i can mount it ro (this a tiny bit is good for security, but also prevents anything messing up my system by mistake)
/var is fairly dynamic but i can mount it noexec and limiting it's size makes sure i empty my caches every so often
/boot is not used after booting so i don't mount it (see /usr) and it is also nice when dual booting to have the kernels in one safe palce.

Saying /usr is static is not really true. There are really no security patches that you can apply if /usr is ro.

---

### Post by koenn on 2010-05-09
> **jbrown96 said:**
> Saying /usr is static is not really true. There are really no security patches that you can apply if /usr is ro.

depends how you organize things

you can have /usr read-only during normal operations - nothing should be modifying anything in there then.

you can remount it read/write during your maintenance periods, and apply updates then.

---

### Post by NightwishFan on 2010-05-09
Also if your mail server gets spammed, so can mount it separate so it will not bring down the whole system.

---

