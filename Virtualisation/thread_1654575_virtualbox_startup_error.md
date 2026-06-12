---
title: "virtualbox startup error"
date: 2010-12-28
forum: Virtualisation
---

### Post by sdowney717 on 2010-12-28
decided to run it again using MM, but getting errors
In the past I had been using vmware.

tried their help fix but no go
scott@scott-desktop:~$ sudo /etc/init.d/vboxdrv setup
scott@scott-desktop:~$

---

### Post by karthick87 on 2010-12-28
Try,```

VBoxManage startvm "name"
```

---

### Post by pricetech on 2010-12-28
The last time I ran into this I had to edit my grub.conf to boot the previous kernel.  Seems vbox stayed behind in that area.

---

### Post by sdowney717 on 2010-12-28
well, I was trying to run the v4 beta.
could not get it to work, so I used synaptic and installed the one in the repo and it is working.

[http://www.webupd8.org/2010/12/how-to-install-virtualbox-40-beta-in.html](http://www.webupd8.org/2010/12/how-to-install-virtualbox-40-beta-in.html)

still wondering now about kvm modules, does it interfere with virtualbox?

---

