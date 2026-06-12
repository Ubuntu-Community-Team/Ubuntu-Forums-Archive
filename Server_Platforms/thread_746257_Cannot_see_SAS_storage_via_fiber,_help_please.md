---
title: "Cannot see SAS storage via fiber, help please"
date: 2008-04-05
forum: Server Platforms
---

### Post by Logist on 2008-04-05
Hello

i have googled, searched, read thru this and other forums, joined IRC channels you name it i did it all.. i now hope this thread will provide some answers...

Heres the setup:
IBM HS21 blade center, with attached SAS storage DS3400 via optical switches from qlogic(2 of them for redundancy)
Ubuntu server 7.10 64 bit

Anyhow heres what i want and i need to tell you now that im totaly new to linux/ubuntu...

ok so i take 1 blade, format it, put ubuntu 7.10 64 bit server on it.. its just gonna run ubuntu as a host and the freeVMware SERVER(btw is this even good for production or should i go with ESX?)
so the blade has 70 gig RAID 1 disks.. more than enugh for ubuntu. However no room for the VM's

now ALL i want wich is simply done in windows cant seem to get it to work in linux is the following:
how to i make ubuntu SEE the LUN hardrive(which i specified on DS3400, via management station, where you can define raid, partitions, size etc... did all) now supposedly the LUN i specified should somehow pop up as an unformated free space under linux. i cant seem to get to that point.. the CD that comes with the storage has some drivers on it but theyre for RHEL... and the instructions wich can be found on the web suggest that RDAC, or MPP driver should be installed on host from the cd wich i dont think will run with ubuntu? 

ubuntu sees the Qlogic HBA cards. cant seem to figure out or find a way how to set up the SAN in ubuntu.. what drivers do i need what commands do i need to put in to find, make and format the parititon on the external DS3400 storage so i can put the files of Vm's on it. And all that of course needs to be done via optic fiber controllers, cause of the speed(4gigs) i could have done it so that i would make the share in windows 2003(where btw the DS3400 works perfectly) and then use it from ubuntu as a mapped drive thru a share,  but thats REAAAALLLY not what i wanna do. need a direct access to the LUN drive in ubuntu and  i cant find a solotion to my problem for like 2 days  now and itd driving me insane! so ANY help would be appriciated... 

Thanks and sry for the long post

Logist

---

### Post by Logist on 2008-04-05
bump, thanks

---

