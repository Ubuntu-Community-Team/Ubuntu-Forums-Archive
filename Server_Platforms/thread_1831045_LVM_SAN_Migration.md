---
title: "LVM SAN Migration"
date: 2011-08-22
forum: Server Platforms
---

### Post by pafoo on 2011-08-22
Hello! Question for all you veterans out there. Currently we have a LVM  setup with 8 PV's in 1 VG and 8 LV's each pointing to a specified PV. As  a background info 1 of the PV's is on a Tier 2 SAN (slow archive  drives) that needs to be on teir 1. So my idea is to have the SAN team  create another advertisment. Make that a PV, vgextend to include it,  some how add that to the appropriate LV, then pv move from tier 2 pv to  tier 1 pv. Then some how remove that PV from the LVM. 

I am really lost on how I should go about this, any idea's would greatly be appreciated!!!

Added

> 

Assuming the newly added Tier 1 SAN LUN is large enough to hold the old Tier 2 LV, it's a simple matter to move the LV.

Basically,

'pvcreate <the-new-pv>'
'vgextend <vgname> <the-new-pv>
'pvmove -i15 -v <the-old-tier2-pv> <the-new-pv>
'vgreduce <vgname> <the-old-tier2-pv>
'pvremove <the-old-tier2-pv>'

Where <the-new-pv> is a block device like /dev/sda (full volume),  /dev/sda1 (partition) or /dev/mapper/mpath1 (if you're using  dm-multipath); likewise for the <the-old-tier2-pv>.   <vgname>, of course, is the VG.

On the 'pvmove', the -i15 and -v will give you periodic status as the data is moved.

Before you start, look at the man pages for the different commands.

And 'pvdisplay --maps' and 'lvdisplay --maps' will tell you how everything is laid out before and after your move.  

Good luck.

This was a reply from Tommylovell

---

