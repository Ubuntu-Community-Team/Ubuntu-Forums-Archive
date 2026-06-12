---
title: "Copied-Over Virtual Machine Refers to Wrong SCSI drive"
date: 2008-04-06
forum: Virtualisation
---

### Post by dbsoundman on 2008-04-06
I have a copy of a windows virtual machine installation I made on my previous Ubuntu 7.04 installation using VMware Server. I installed VMware Server on my new 7.04 install now, which is on a different drive than the first one, and copied the old installation over to the correct directory. However, when I try to start it up in VMware Server, I get told that the hard drive is missing essentially. This is not an error in the virtual machine itself by the way, it's actually a popup message from VMware. I'm thinking that the old VM refers to my other SCSI drive instead of the one it's on now, because it also says in the information on this machine that there is 0 MB of hard drive and it doesn't exist. I tried switching it from SCSI 0:0 to SCSI 1:0 or SCSI 0:1, but no luck. I'm not really sure how to fix this, or how to figure out what the SCSI ID# is for my current drive. What can I do to fix this?

Thanks,
Dan

---

