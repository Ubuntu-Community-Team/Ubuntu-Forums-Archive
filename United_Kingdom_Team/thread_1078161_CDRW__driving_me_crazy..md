---
title: "CD/RW  driving me crazy."
date: 2009-02-23
forum: United Kingdom Team
---

### Post by Moko76 on 2009-02-23
Hi there! I'm hoping one of you clever folks can help me get to the bottom of this problem. I'm trying to use K3b to burn an audio cd on ubuntu 8.10. my cdrw is shown in the places dropdown list and shows up on the k3b burning bar too as "cyberdrv cw058d".
However when i try to burn the cd, it sets up all the files ready to burn and then..... nothing happens. No light on the drive, no whirring etc.

was looking art other threads for ideas and tried typing "wodim --devices"

and got this:

wodim: Warning: controller returns wrong size for CD capabilities page.
wodim: Overview of accessible drives (1 found) :
-------------------------------------------------------------------------
0 dev='/dev/scd0' rwrw-- : '' 'ATAPI CDROM.52X'


It's only recognising my other non-rw drive

also "wodim -scanbus" gets me this..

scsibus1:
wodim: Warning: controller returns wrong size for CD capabilities page.
1,0,0 100) ' ' 'ATAPI CDROM.52X ' '110K' Removable CD-ROM
1,1,0 101) *
1,2,0 102) *
1,3,0 103) *
1,4,0 104) *
1,5,0 105) *
1,6,0 106) *
1,7,0 107) *
shaun@shaun-desktop:~$ 


Also not recognising the drive.

any ideas what i should try next?

much thanks.

---

