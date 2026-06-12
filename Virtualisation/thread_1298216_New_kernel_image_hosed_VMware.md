---
title: "New kernel image hosed VMware  *?*"
date: 2009-10-22
forum: Virtualisation
---

### Post by tixetsal on 2009-10-22
Did anyone else have their VMware instance get hosed by the kernel update today, or am I barking up the wrong tree?  I am @ work right now, and have another issue with a high-availability server that is acting up (unrelated issue) that I have to attend to, so I have not been able to dig into the problem yet.  I am actually booted into Windows right now b/c the VM won't come up, and I need to use some win s/w to diagnose the problem.  I just wanted to bounce this off of you guys, to see if anyone else had this issue...

TIA, everyone!

---

### Post by fjgaude on 2009-10-22
I believe the kernel has to re-compiled using a patch... here's some insight into the issue:

[http://www.insecure.ws/2009/09/11/vmware-specific-specific-5-5-x-and-kernel-2-6-31/comment-page-1](http://www.insecure.ws/2009/09/11/vmware-specific-specific-5-5-x-and-kernel-2-6-31/comment-page-1)

Good luck... I await until someone comes up with something I can handle.

---

### Post by tixetsal on 2009-10-22
> **fjgaude said:**
> I believe the kernel has to re-compiled using a patch... here's some insight into the issue:

[http://www.insecure.ws/2009/09/11/vmware-specific-specific-5-5-x-and-kernel-2-6-31/comment-page-1](http://www.insecure.ws/2009/09/11/vmware-specific-specific-5-5-x-and-kernel-2-6-31/comment-page-1)

Good luck... I await until someone comes up with something I can handle.

meh!

This will have to wait until I have a bit of free time...

Thank you much for the tip.

---

### Post by steveneddy on 2009-10-22
You will need to recompile the kernel module for your current kernel version.

Every time you install a new kernel version, a new module must be compiled for VM Ware to operate properly.

I think - as root:

```
vmware-config.pl
```

I now run vbox so this is from memory many moons ago.

---

### Post by klicki on 2009-10-23
> **tixetsal said:**
> Did anyone else have their VMware instance get hosed by the kernel update today, or am I barking up the wrong tree?  I am @ work right now, and have another issue with a high-availability server that is acting up (unrelated issue) that I have to attend to, so I have not been able to dig into the problem yet.  I am actually booted into Windows right now b/c the VM won't come up, and I need to use some win s/w to diagnose the problem.  I just wanted to bounce this off of you guys, to see if anyone else had this issue...

TIA, everyone!
:( Yep, same issue. :(
When I try to re-install vmware-tools, the script tells me, that it doesn't know about gcc-4.3.3. :mad: This is happenning time and again. I start to question my overall solution.
](*,)

---

### Post by sdowney717 on 2009-10-23
on karmic i solved by doing this

[http://blog.mymediasystem.net/uncate...-koala-x86_64/](http://blog.mymediasystem.net/uncate...-koala-x86_64/)

[http://ubuntuforums.org/showthread.php?t=1297939](http://ubuntuforums.org/showthread.php?t=1297939)

---

### Post by tixetsal on 2009-10-23
Steveneddy,

Thank you for your response!  Your solution solved my problem.  Yesterday, initially, I thought that maybe my iptables had become mucked-up.  I checked them and everything looked OK, so I figured it had to be the new kernel.  I don't know why I didn't think of running the Perl config script again, but I am glad that you did.  8)

Thanks to all for your excellent suggestions, and I hope that this thread will help others that are struggling with the same issue.  This is a good community to be a part of.

---

