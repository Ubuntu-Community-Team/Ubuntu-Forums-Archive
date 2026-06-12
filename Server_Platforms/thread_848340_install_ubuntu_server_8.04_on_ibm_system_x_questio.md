---
title: "install ubuntu server 8.04 on ibm system x question"
date: 2008-07-03
forum: Server Platforms
---

### Post by fouadk on 2008-07-03
hi everyone...

we have currently bought an ibm system x3500 server and we intend to install ubuntu server on it...

the server have RAID disks....

would installing ubuntu on that sever be a piece of cake(put in the CD and follow the instructions) or i have to do some stuff first in order to make RAID work properly ???


please help....

thanks in advance

---

### Post by FreakTech on 2008-07-03
I am assuming you have a hardware RAID.  If this is the case you should have no problem as Ubuntu should recognize your RAID array as one disk.

---

### Post by fouadk on 2008-07-03
thanks for your reply....

i really have no big experience in types of RAID....

what i can tell you is that there exist about 6 300GB disks that can easily be installed and removed....this is hardware RAID ???? what other types of RAID does exist ????

---

### Post by pdwerryhouse on 2008-07-03
As long as you chose a raid option when you ordered the server then it will be hardware raid. Just having 6 disks in itself isn't an indication of raid (ie, they could easily be run as six independent scsi disks).

I don't think you'll have any issues. We're running old releases Redhat and SuSE Enterprise on lots of IBM hardware and don't have any problems with the hardware raid.

When you boot the server up, the BIOS will ask you to press ctrl-M (I think) to configure the raid, and it will then throw you into a little configuration application. Set it up there, and then exit and install the OS.

---

### Post by fouadk on 2008-07-05
thanks again for your reply...

the whole process was a piece of cake...

when i first ran the server it said that BIOS was not installed so i booted from one of the CD that were shipped with the server and installed the BIOS and then ran a tool on that CD that dealt with RAID so i chose RAID0 (that is what i need) and then rebooted and installed ubuntu 8.04 server....it is a piece of cake process and ubuntu runs smoothly on that server....

---

