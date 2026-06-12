---
title: "Possible to migrate live LVM LV's?"
date: 2009-10-20
forum: Server Platforms
---

### Post by kameleon25 on 2009-10-20
I have a xen server that utilizes LVM and I want to move the LV's to an iscsi storage server while the VM's are still live. Is there a possible way to do this? I have read somewhere before that there is a command that allows moving a LV from one VG to another, but I cannot find that for the life of me again! I appreciate any and all guidance in this endeavor.

---

### Post by kameleon25 on 2009-10-20
If I remember correctly, it was something along the lines of:

setup ISCSI and mount the new remote drives on the xen server, 
move the LV's I want moved from the current VG to the new VG
change needed settings in xen to make sure the VM's read the correct VG
done...


If only it were that simple... something tells me it isn't.

---

### Post by kameleon25 on 2009-10-21
Ok, I have done some more digging and it appears as though I should be able to mount the current drives on the new server via ISCSI. Then run vgmerge to merge my two volume groups into one. Then I can use pvmove to migrate the lv's off the original server drive. Once I have the lv's all on the new server I could use vgreduce and pvremove to get the original drive out of the volume group.

The only issue I am having is getting the individual LV's to mount via ISCSI. Or do I mount the entire drive? I am semi-new to this whole ISCSI deal so any assistance is appreciated.

---

