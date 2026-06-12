---
title: "Vmware installed, Gutsy won't boot (safe graphics,then black screen)"
date: 2008-04-12
forum: Virtualisation
---

### Post by mgysgthath on 2008-04-12
I'm running Gutsy with an 8800 GTX (drivers installed with Envy script).  All was well, lastnight I installed Vmware 6.03.80004 and the process seemed to be fine.  I installed the same package on my Fedora Core 8 box and with a small hack that installed and is working fine.

My problem is after rebooting my Gutsy box, it boots up and complains about a problem with my display settings and says it's running in safe graphics mode (this only happened after Vmware install).  

So what I'd like to know is how to fix this or simply how to remove vmware from the recovery shell.  I tried apt-get remove vmware but i didn't install it with apt so I'm not sure if that will even work.  I'm pretty new to linux but I know a little.

---

### Post by dcstar on 2008-04-12
> **mgysgthath said:**
> I'm running Gutsy with an 8800 GTX (drivers installed with Envy script).  All was well, lastnight I installed Vmware 6.03.80004 and the process seemed to be fine.  I installed the same package on my Fedora Core 8 box and with a small hack that installed and is working fine.

My problem is after rebooting my Gutsy box, it boots up and complains about a problem with my display settings and says it's running in safe graphics mode (this only happened after Vmware install).  

So what I'd like to know is how to fix this or simply how to remove vmware from the recovery shell.  I tried apt-get remove vmware but i didn't install it with apt so I'm not sure if that will even work.  I'm pretty new to linux but I know a little.

```
sudo envy -t
```

---

### Post by bluewhale on 2008-04-12
I've got an 8800 GTX here at home as well. Per advice from this forum I ended up installing Envy then later removing it. All is well now. 

sure wish I knew how I fixed it   :roll:

---

### Post by mgysgthath on 2008-04-13
I'll try envy -t thanks for the advice, I'll let you know how it goes.

---

### Post by mgysgthath on 2008-04-13
envy -t got me back into x, i did the install function again and now i can get back booted, but only resolution option is 640x480.  at least now I can tinker, thanks.

---

### Post by mgysgthath on 2008-04-14
I was able to resolve the issue by using the GUI version of envy to uninstall, reboot, and reinstall the nvidia driver.

---

