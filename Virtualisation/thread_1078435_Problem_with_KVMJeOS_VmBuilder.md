---
title: "Problem with KVM/JeOS VmBuilder"
date: 2009-02-23
forum: Virtualisation
---

### Post by sevor on 2009-02-23
Im using VmBuilder to create vms.  I can create about 3 vms perfectly, however around the 4th vm I get this error:

```
Could not find any free loop deviceBad address
```


If i reboot the system I can create more vms but will run into the same problem after I creating a couple. 

Is there any solution to this?  It seems like there is something not letting go of a resource or ip address or something.  can I run a command to do some kind of clean up after each vm??

thanks for the help

---

### Post by dendrobates on 2009-03-03
> **sevor said:**
> Im using VmBuilder to create vms.  I can create about 3 vms perfectly, however around the 4th vm I get this error:

```
Could not find any free loop deviceBad address
```


If i reboot the system I can create more vms but will run into the same problem after I creating a couple. 

Is there any solution to this?  It seems like there is something not letting go of a resource or ip address or something.  can I run a command to do some kind of clean up after each vm??

thanks for the help

Can you post the vmbuilder command?  Also could you add the --debug switch to the vmbuilder command and post the output?

---

