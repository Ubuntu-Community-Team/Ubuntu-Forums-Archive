---
title: "Server memory maintenance advice"
date: 2009-07-21
forum: Server Platforms
---

### Post by onetrx on 2009-07-21
Hi all,

I'm relatively new to Linux and have enjoyed my first project of install Ubuntu Server 9.04 onto a Compact Flash card in an [eBox 4863S]("http://www.compactpc.com.tw/ebox-4852.htm"). The server is running LAMP for experimenting, SSH, Cacti, and Samba to share an attached 1TB USB drive.

Because it's all installed on CF, I wanted to avoid unnecessary read/write cycles so I haven't created a swap space. The /var directory and subdirectories are pretty much all mounted as tmpfs, and a script is used to copy the log files temporarily to CF on reboot.

I have been keeping my eye on memory usage and noticed a steady but unpredictable decline in available memory (see graph). I'd like to be able to troubleshoot this so that I can identify why this is occurring and how to keep it under control.

Could you give me any advice on what steps you might take to investigate and rectify this? Thanks

[CENTER][IMG]http://i27.tinypic.com/1zexxs9.jpg[/IMG][/CENTER]

---

### Post by shredkingj on 2009-07-21
If you have /var mounted as tmpfs, then all the logs will be written to memory.  Memory is a finite resource, and the behavior you are seeing is predictable, imo.  I think a way to help you lower the rate logs are written to memory is by adjusting the verbosity of your logging in /etc/syslog.conf.

Edit:

Just wanted to add the Apache and Samba can be quite verbose in their logging.  Check their logging configuration as well.

---

### Post by grantemsley on 2009-07-21
If it is the logs, you might want to setup logrotate to delete old logs faster than usual.

Also, are you sure that's not including buffers?

"free -m" will show you.

My machine right now:
             total       used       free
Mem:          3995       3880        115
-/+ buffers/cache:        806       3189
Swap:         3906        502       3403

Which tells me that yes, it's using all my RAM - but most of it is for caching, which just means it doesn't have any other purpose for that RAM yet.  When it needs more ram, it will cache less.

---

### Post by onetrx on 2009-07-21
Okay, I think this goes to show my lack of knowledge in how memory is managed. Looks to me like it is using most of the memory for cache after all, so I guess I won't be too worried about it.

```

             total       used       free     shared    buffers     cached
Mem:           939        686        252          0         51        512
-/+ buffers/cache:        121        817
Swap:            0          0          0

```


Logs are being rotated and kept for 2 weeks, so I don't think that should be chewing up too much memory. And for the record, here's my fstab... all tmpfs filesystems are loaded into RAM, right?


```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# Compact Flash card filesystems
# /boot /dev/sda1
UUID=8c1c5941-bff9-430c-9e4b-58c879162f1d /boot           ext2    relatime        0       2
# / on /dev/sda5
UUID=ba7b8878-1385-4ea9-a57a-c83d2ac57530 /               reiserfs notail,noatime  0       1

# Reduce writing to Compact Flash card
# Script to copy logs to CF card on reboot
tmpfs           /tmp            tmpfs   defaults,noatime,mode=0777      0       0
tmpfs           /var/tmp        tmpfs   defaults,noatime,mode=0777      0       0
tmpfs           /var/log        tmpfs   defaults,noatime,mode=0777      0       0

# External USB 1TB storage drive
UUID=6153c674-164d-450d-8263-653f558a061d       /media/archive  ext3    defaults        0       0
UUID=810f5751-8cb3-4b46-8375-e893dca51b98       /media/sysbak   ext3    defaults        0       0

# Device attached to front USB port (eg. for future squid caching)
/dev/sdc1       /media/frontusb vfat    defaults,users,noatime,nodiratime       0       0

```

Thanks for your advice and comments.

---

### Post by dragos2 on 2009-07-22
You can increase the vm.swappiness from 60 to 80 or higher, this way you will force
the kernel to write inactive memory pages to disk.

echo "vm.swappiness = 90" >> /etc/sysctl.conf

This will decrease a little the performance and will use the CF more but you
will have more on-demand memory available.

---

### Post by grantemsley on 2009-07-22
It took me quite awhile to figure out how linux reports memory usage too.  So I expect that not too many people know about it.

It makes sense to use all the available RAM though - otherwise it's just sitting there wasted.

Your free -m looks fine, so I wouldn't worry about it.

---

