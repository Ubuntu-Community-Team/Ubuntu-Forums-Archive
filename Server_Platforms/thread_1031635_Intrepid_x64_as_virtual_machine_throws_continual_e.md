---
title: "Intrepid x64 as virtual machine throws continual errors"
date: 2009-01-05
forum: Server Platforms
---

### Post by sfgreenwood on 2009-01-05
Hi -

I have a copy of 8.10 AMD64 server running as a guest under Xen on Centos 5.2 x64 on a HP Proliant ML110 server. Its disk is a LVM partition on an unmounted volume group dedicated for virtual machines. The server boots and runs ok, but is continually sending the follow error to the console, to dmesg and consequently to messages and syslog:

```
[ 1345.236651] ata2.00: configured for MWDMA2
[ 1345.236690] ata2: EH complete
[ 1345.237043] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 1345.237577] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 1345.237578]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 1345.237579]          res 41/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x3 (HSM violation)
[ 1345.240016] ata2.00: status: { DRDY ERR }
[ 1345.240503] ata2: soft resetting link

```

It doesn't affect the operation of the vm but renders dmesg useless and takes up space. Stopping the errors would be fine. Does anyone have any ideas?

---

### Post by breamond on 2009-01-06
As I wanted to write that I have the same issue here. It comes to my mind, that this might not be the hdd which causes the problem.

After creating and configurating the DomainU with 'virt-manager' it sets the disk param to "disk = [ 'phy:something,hda,hda,w', ',cdrom:hdc,r' ]".

After removing the the second entry ",',cdrom:hdc,r'" in the config file from the DomainU the error is gone.

Edit: Alternative you could remove the cdrom from the virt-manager.

Maybe this helps you too. ;)

---

