---
title: "vmware files can be deleted in Konsole but not Dolphin"
date: 2021-10-01
forum: Virtualisation
---

### Post by eightsix on 2021-10-01
I'm running Kubuntu 21 as a vmware guest in Windows 10. Host folders are mounted via fstab:

```
[FONT=monospace][COLOR=#000000]vmhgfs-fuse /home/eightsix/vmwareShares fuse defaults,allow_other,uid=1000,gid=1000 0 0[/COLOR]
[/FONT]
```

In Konsole, I can do anything I want to files, including deleting them. Dolphin will let me open folders and files, but it won't let me delete, rename, or move anything.

I don't have this problem with my external USB drive. 

How might this be fixed?

Thanks!

---

### Post by ActionParsnip on 2021-10-01
What command do you use in the terminal to delete the files (you can use the "history" command if you want to find an example)

---

### Post by eightsix on 2021-10-01
I use **rm** for files and **rm -rf** for directories.
But I can't even rename in Dolphin.

---

### Post by QIII on 2021-10-01
Moved to Virtualisation.

---

### Post by ActionParsnip on 2021-10-02
Do you prefix with sudo?

---

### Post by eightsix on 2021-10-02
No, no sudo. Just little ol' me.

---

