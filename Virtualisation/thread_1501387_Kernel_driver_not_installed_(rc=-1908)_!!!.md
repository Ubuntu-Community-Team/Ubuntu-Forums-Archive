---
title: "Kernel driver not installed (rc=-1908) ???!!!"
date: 2010-06-04
forum: Virtualisation
---

### Post by KingOfDeath on 2010-06-04
VVirtualBox Was Working Fine With Me Until Today Morning...
I Opened The Virtual Os.
And Here Wat It Told Me



```
  p, li { white-space: pre-wrap; }  Kernel driver not installed (rc=-1908)

Please install the virtualbox-ose-dkms package and execute 'modprobe vboxdrv' as root.

```

So Yahh I Have Dkms Alreead Intalled Lol

Then I Did This

```
yanal@ubuntu:~$ /etc/init.d/vboxdrv setup
bash: /etc/init.d/vboxdrv: No file  or folder of this type
```

How Can I Solve This ?

---

### Post by KingOfDeath on 2010-06-05
Any Answers ?

---

### Post by KingOfDeath on 2010-06-05
Never Mind I Fixed It I Wrote This In terminal:
```
sudo /etc/init.d/virtualbox-ose start 
```

---

