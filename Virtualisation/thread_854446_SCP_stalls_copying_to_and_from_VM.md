---
title: "SCP stalls copying to and from VM"
date: 2008-07-09
forum: Virtualisation
---

### Post by zaarch on 2008-07-09
Using KVM+Libvert+QEMU to make VM's. Guest OS : Ubuntu 8.04 JeOS HOST: Ubuntu 8.04 Sever Ed.

Copying data ~ approximately 8GB via SCP to guest.

SCP transfer stall after 5 or 6 files and I am unable to ping guest after this. Need to reboot the guest after every stall!

Any ideas, what may cause such stall/network crash ?

---

### Post by pytheas22 on 2008-07-09
scp is flaky and is not really designed for transferring a lot of separate files at once.  I'd recommend either packing all the files together into a tarball and transferring them that way as one big file, or using rsync instead of scp.  This isn't exactly an answer to your question, but hopefully it will solve your problem.

---

### Post by zaarch on 2008-07-09
intresting...rsync you say!

so i am guessing this is regular problem with scp..

i have in the past used scp to move about ...4 gb worth data..individual files being 150-200 MB.

but this 8GB is composed of smaller files....i would they range from 10-30 MB..smaller than before....

but for some reason scp crashes my nic ?

could it be a nic / driver issues as opposed to rsync ?

---

### Post by pytheas22 on 2008-07-09
> could it be a nic / driver issues as opposed to rsync ?

Certainly, it could be.  But if you're only having trouble when using scp and other kinds of traffic don't break anything, then there's a good chance that scp itself is at fault.  rsync and scp are similar in that they both work via ssh, but the big difference is that scp spawns a new process for every file that it transfers.  rsync can also be run with arguments to compress files before sending them (maybe scp can too but I don't know of this option), which reduces the load on the network and makes things faster and more reliable in general.

So the bottom line is, the problem doesn't necessarily lie with scp, but I suspect that it does and that using rsync instead might make a difference.

Otherwise, try looking at the logs of the guest machine to see if you can trace its crashes down to something else.

---

