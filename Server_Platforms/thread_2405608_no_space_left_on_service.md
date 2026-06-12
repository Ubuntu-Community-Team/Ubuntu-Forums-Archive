---
title: "no space left on service"
date: 2018-11-08
forum: Server Platforms
---

### Post by mn1247 on 2018-11-08
I'm running Ubuntu Server 18.04 (on a XenServer VM).  I'm getting an  error while trying to edit an apache config file using nano.  The error  is "no space left on service".  Not sure what's going on nor how to  fix.  I've attached the output from "df -i".  Any suggestions?  Thanks -  Eric[ATTACH=CONFIG]281590[/ATTACH]

---

### Post by TheFu on 2018-11-08
Need **df -Th** too.

df -i just shows inode use, not the same, but related.

The error message is one I've never heard or seen before.  Could the translation be off? Normally, it would be "no space left on device"

---

### Post by mn1247 on 2018-11-09
Thanks for the reply.  Yes, my typo... it's "No space left on device"  I  ran "df -Th" as you suggested (attached).  I have 50G allocated to the  VM, but I'm not seeing that much in the totals.  The server runs a LAMP  stack and zoneminder - maybe something goofy with that?

BTW, "du -sh" shows only 4.7G.  Am I not understanding something?

Eric[ATTACH=CONFIG]281593[/ATTACH]

---

### Post by TheFu on 2018-11-09
You are out of storage on /.  Need to fix that from outside the VM first, then inside the VM, you can expand the partition, then expand the LV.  
If you post the TEXT output from **sudo lsblk**, there might be an easier way. Cannot tell from what is provided.  Also, the TEXT output from **sudo fdisk -l** would be helpful.  I doubt you actually have 50G allocated to the VM based on what is being shown.

Also, please copy/paste using text, not images. Be kind to people who pay by the byte to volunteer here.

---

### Post by darkod on 2018-11-09
Since you are using LVM you should also post the output of:
```
sudo vgdisplay
sudo lvdisplay
```

And yes, please copy/paste the text output in CODE tags, that helps a lot.

---

