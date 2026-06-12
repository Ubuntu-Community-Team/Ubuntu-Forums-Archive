---
title: "Booting into Xen kernel loses tape drive"
date: 2008-01-25
forum: Virtualisation
---

### Post by berto- on 2008-01-25
Hi everyone,

I have a 6.06.1 LTS system with a Quantum DLT-V4 SATA tape drive.  The drive works flawlessly using the stock Ubuntu kernel, the latest one being 2.6.15-28-amd64-generic.

I compiled a Xen 3.0.4 kernel, which uses kernel version 2.6.16.33.  When I reboot into this kernel, the tape drive is no longer detected.

Are there any extra kernel modules in the Ubuntu kernel not found in the stock kernel for this tape drive that I should be adding to my Xen kernel?  Or are there any modules that I need to include aside from the st and sg modules?

This is what dmesg states under the Ubuntu kernel:

```

[   74.885415] st: Version 20050830, fixed bufsize 32768, s/g segs 256
[   74.885529] st 3:0:0:0: Attached scsi tape st0<4>st0: try direct i/o: yes (al
ignment 512 B), max page reachable by HBA 1048575
[   74.919265] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   74.919285] st 3:0:0:0: Attached scsi generic sg1 type 1

```

The list of modules shows the st module loaded:

```
$ lsmod | grep st
st                     44584  0
scsi_mod              160632  7 sbp2,sr_mod,sg,st,arcmsr,sd_mod,libata

```

And finally, the device 

```

$ ls -l /dev/st0
crw-rw---- 1 root tape 9, 0 2008-01-15 23:49 /dev/st0

```

Any help is greatly appreciated!

Thanks!
-Roberto.

---

