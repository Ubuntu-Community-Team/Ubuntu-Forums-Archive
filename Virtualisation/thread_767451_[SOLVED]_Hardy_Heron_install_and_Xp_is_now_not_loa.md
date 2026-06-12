---
title: "[SOLVED] Hardy Heron install and Xp is now not loading in Virtual Box"
date: 2008-04-25
forum: Virtualisation
---

### Post by Rytron on 2008-04-25
Hi,
I had Xp working fine in Virtual Box under Ubuntu 7.10.
Now since I upgraded to Ubuntu 8.04 Hardy Heron I get this error message when I try to load Xp in Virtual Box.

```

PIIX3 cannot attach drive to the Secondary Master.
VBox status code: -102 (VERR_FILE_NOT_FOUND).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}
```

What do I need to do in order to fix this?
Thank you.

---

### Post by quantums on 2008-04-25
It appears to be because of having a second disk defined? I tried it with a virtual XP that had no second disk ever defined, which worked fine. Both of my VMs that I had just today setup with a second disk, passing back and forth, refuse to boot with same error. I noticed today that VB did not like it when I defined the disk for one VM and didn't exit the GUI before moving it the other, I don't know if this is related to that.

---

### Post by quantums on 2008-04-26
I have found a couple ways around the problem, one way was clone the vdi image and make a new VM with the cloned image, this then worked without the error. I also on the other VM that was giving me the error, just deleted the VM and make another one using the same drive image and that worked as well. Some thing must have changed with one of the config files, but this got me going. Woot, Woot as my youngest would say...

---

### Post by Rytron on 2008-04-27
Hi,
I eventually got it working.
In the settings there was a cd mounted that was linking to an windows iso that was moved.
I deselected the iso and now everything works perfect.
Cheers.

---

### Post by notepad on 2008-05-24
i had the same error message and i found that my cd rom was enabled and defined as the secondary SLAVE rather than the secondary MASTER.
i changed it from slave to master and that sorted it out.

---

### Post by Shachiel on 2008-06-16
Thanks a lot quantums, attaching the disk to a new virtual machine worked perfectly. Does anyone have an idea of why did this happen? I didn't update virtualbox or anything...

---

