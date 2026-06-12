---
title: "Mounting permanently a shared folder virtualboxed"
date: 2012-08-10
forum: Virtualisation
---

### Post by TRiCiDE on 2012-08-10
Win7 Host
Ubuntu 12.04 LTS Guest
Virualbox

Every time I reboot I have to enter this command.  Is there a simple way to mount it permanently every time it boots?

```
sudo mount.vboxsf Downloads /mnt/share
```

I know this is easy and you think I didn't look it up.  I did and I might not understand too much of the other tries I had, but, if you look at all my recent posts you can see I have been Mr. nub ubuntu project man.  

Thank you.

---

### Post by ads52 on 2012-08-12
Newer versions of virtualbox have an option for automounting the shared folder. I have attached a screenshot to show the option on my system. Then all you need is to make sure you are a member of the vboxsf group on the guest VM.

---

