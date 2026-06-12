---
title: "Freezes during boot after removing HDD"
date: 2018-10-14
forum: Server Platforms
---

### Post by LVCNSOL on 2018-10-14
Hi all,

I removed one of my secondary HDDs from my server but now the server freezes during boot. It displays a failed message along the lines of 'cannot start nfs daemon'. I have been trying to disable Nfs and remove all exports but no success. Does anyone have an idea why it would do this? Would it be best for me to just remove nfs? Nothing is using nfs anymore.

Thanks

---

### Post by TheFu on 2018-10-14
Check the /etc/fstab for stale references to the old disk.  Comment any that aren't used out.
The device to UUID mapping can be seen with the **blkid** command.

If the install uses encryption or LVM, another level of redirection will need to be figured out.

---

### Post by LVCNSOL on 2018-10-15
Thank you. Originally I did comment out the device I removed as well as an Nfs entry that was there as well. The problem still persists. 
Will have a look at the mapping later on. 

I'm not using LVM or encryption on my setup.

---

### Post by TheFu on 2018-10-15
NFS is "exported" by the /etc/exports file on the NFS server.  If you don't want **any** NFS storage shared, you can comment out all the lines in that file, and restart the nfs-server daemon.

---

### Post by darkod on 2018-10-15
Please post the output of:
```
cat /etc/exports
```

---

