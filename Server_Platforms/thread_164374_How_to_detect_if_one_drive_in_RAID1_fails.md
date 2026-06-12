---
title: "How to detect if one drive in RAID1 fails"
date: 2006-04-22
forum: Server Platforms
---

### Post by puffyelms on 2006-04-22
Disclaimer: I've worked with unix and pcs for many years, but i'm new to server maintainance and configuration in linux.

I've set up my ubuntu server with 2 drives (raid1).  Everything is working fine and i tested to see if both would boot without the other.

My questions is, How do I know if one drives fails?  I'd imagine the server would crash(?), but is there a way I can set up an email alert on next reboot?

I'm trying to avoid running with a broken drive and not knowing it.

Thanks...

---

### Post by Jimbob0i0 on 2006-04-24
[http://www.die.net/doc/linux/man/man8/mdadm.8.html](http://www.die.net/doc/linux/man/man8/mdadm.8.html)

mdadm is the tool you want to use. 
The man page for it is above.
Either configure a cron job to start it every so often in monitor mode for checks every X minutes or better still write an init script to run it at start up.

---

### Post by colo on 2006-04-24
Just monitor the pseudo-files /proc/mdstat - on my system, it looks like this right now:

```
colo@zealot ~ $ cat /proc/mdstat 
Personalities : [raid0] [raid1] 
md1 : active raid1 sdb1[1] sda1[0]
      72192 blocks [2/2] [UU]
      
md3 : active raid1 sdb3[1] sda3[0]
      4008128 blocks [2/2] [UU]
      
md5 : active raid0 sdb5[1] sda5[0]
      6216960 blocks 64k chunks
      
md6 : active raid0 sdb6[1] sda6[0]
      4016000 blocks 64k chunks
      
md7 : active raid0 sdb7[1] sda7[0]
      4016000 blocks 64k chunks
      
md8 : active raid0 sdb8[1] sda8[0]
      288237952 blocks 64k chunks
      
unused devices: <none>
```

Additionally, a warning will be printed to your kernels debug ringbuffer, which you can check via "dmesg". I don't know the exact wording of it right now, since it's been a while one of my arrays has failed.

---

