---
title: "Please Help vmware server and guest OS problem"
date: 2008-01-22
forum: Virtualisation
---

### Post by Maluco on 2008-01-22
i have vmware server and windows XP OS guest. If my OS guest folder is under /home/myusername/WinXP are have no problem, but if I copy my WinXP folder to my second internal hardrive ( /media/My500 ) my guest OS do not start. I can see very quickly a red X on the network card and CDrom icons on the bottom of my VMware Server Console.
Thank you in advance for any help.

Luiz

---

### Post by Nano Geek on 2008-01-22
The problem is that VMWare is looking in a specific folder for the VM file.
I believe that you can change where it looks under preferences.

---

### Post by Maluco on 2008-01-22
I tried that too but didn't work.
I am lost .

---

### Post by hyper_ch on 2008-01-22
just symlink it... then all path should be fine again....

---

### Post by Maluco on 2008-01-22
Tks Hyper_ch

I tried it but didn't work.

---

### Post by Maluco on 2008-02-17
Please help.
why my guest OS only run if are on my system disk ? if I move to external disk, stop work.  I see a red X on the NIC card icon and on virtual disk icon.

Thanks in advance for any help.

---

### Post by bodhi.zazen on 2008-02-17
Sounds like a permissions problem (with the red X thing).

---

### Post by Maluco on 2008-02-19
I know but I don't know how and where to fix it.

Thanks anyway.

---

### Post by bodhi.zazen on 2008-02-19
OK, here are some links on permissions :

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

	[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

You can list the permissions with :

```
ls -l
```

---

