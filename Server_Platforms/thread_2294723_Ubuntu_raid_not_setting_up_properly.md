---
title: "Ubuntu raid not setting up properly?"
date: 2015-09-12
forum: Server Platforms
---

### Post by static7 on 2015-09-12
I have set up a raid 1 on two 500GB HDDs using [this tutorial]("http://ubuntuforums.org/showthread.php?t=1687994")

When I enter "mdadm -Es | grep md0 >> /etc/mdadm/mdadm.conf" I get "-bash: /etc/mdadm/mdadm.conf: Permission denied"

However I did update the ramdisk and add the raid to fstab.

I can see the raid in fdisk as md0 and lsblk shows md0 as raid1. Also I can see and add files to it from my window 10 machine. But when I check the raid with "dmraid -s -s" it returns "no raid disks".

So somewhere in the "Append array" piece of the tutorial things went wrong. Because fdisk sees the raid and lsblk shows the raid am I ok? I don't want to reboot one day and find that my raid is no longer seen.

Thanks

---

### Post by steeldriver on 2015-09-12
The command's author probably assumes that you are running it in an interactive root shell (e.g. 'sudo -i')

If you are trying to run it by prepending the command with sudo, only the first command (mdadm -Es) is receiving elevated privileges so the redirect ( >> /etc/mdadm/mdadm.conf ) is failing due to lack of permission.

I'm not sure that dmraid is aware of soft-RAID arrays - so long as mdadm can see it, I'd not worry too much about that

---

### Post by static7 on 2015-09-12
Thanks for the reply.
I have tried this using root before and get suck here...

root@Tardis:~# mdadm -Es | grep md0 >> /etc/mdadm/mdadm.conf
mdadm: Unknown keyword mdadm

What am I missing here? Why is Ubuntu not liking mdadm?

Good to know that dmraid might not be the best tool to use here. Makes me feel better.

---

### Post by steeldriver on 2015-09-12
Sorry I've never encountered an "unknown keyword" error from the shell - I don't know why that would be

You could always do something like

```

sudo mdadm -Es | grep md0 | sudo tee -a /etc/mdadm/mdadm.conf

```

FWIW I'm not sure the 'grep' is helpful here: if you have a single array you can omit it. At least check that 'sudo mdadm -Es | grep md0' actually produces something - for example, I get

```

$ sudo mdadm -Es
ARRAY **/dev/md/0** metadata=1.2 UUID=0b6edd0e:662df5af:68f6ddff:ebddfdd9 name=htpc-01:0

```

which obviously doesn't match **md0**

---

### Post by darkod on 2015-09-13
The -E stands for --examine which is used on the partitions/devices which are part of the array. You don't need that when adding new array to mdadm.conf. You need -D which stands for --detail. That shows details of an array, not its components.

Also, if you have only one array and if it's md0, forget about the grep:
```
mdadm -Ds >> /etc/mdadm/mdadm.conf
```

Another option is to check the md0 UUID with sudo blkid and put it manually in mdadm.conf. Not everything has to be done automatically... :) You can make the mdadm.conf entry yourself. In fact, manual ARRAY definitions in mdadm.conf are often better because the system can also sometimes use different md number than you did originally. To me it has happened md2 to be "renamed" to md127 without any reason, and everything kept on working. After I put it manually to md2 it never changed again.

---

