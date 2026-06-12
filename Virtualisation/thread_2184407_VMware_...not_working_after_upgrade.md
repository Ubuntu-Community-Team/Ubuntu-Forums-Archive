---
title: "VMware ...not working after upgrade???"
date: 2013-10-28
forum: Virtualisation
---

### Post by rainman3 on 2013-10-28
I installed the upgrade 13.10 and now my VMWare won't work.



"VMWare Kernel Module Updater.

Before you can run VMWare, several modules must be compiled and loaded into the running kernel.

Kernel Headers 3.8.0-31 generic

Kernel headers for version 3.8.0-31 generic were not found."



My VMWare was working perfectly *before* I updated... what's going on???

 Help please... I need my VMWare.


 R.

---

### Post by houstonbofh on 2013-10-29
How did you install VMware?  It may need to be reinstalled as there were some kernel revisions that may be too much for what you have on there.

---

### Post by rainman3 on 2013-10-30
I installed VMware workstation 10.1 ..... as I always do, CD to downloads, chmod etc, etc.. then installed it, except I got the above message from Ubuntu...

R.

---

### Post by warp99 on 2013-10-31
> **rainman3 said:**
> Kernel headers for version 3.8.0-31 generic were not found.

You need to install the kernel headers for 3.8.0-31 generic so VMware can compile modules against them.

```
sudo apt-get install linux-headers-3.8.0-31-generic
```

---

### Post by warp99 on 2013-11-01
For the future just install the meta-package so the latest version of headers will always be on your system.

```
sudo apt-get install linux-headers-generic 
```

---

### Post by re1d on 2013-11-03
**I get the same message about compiling modules after clean install of 13.10 and fresh install of VMware 9** - except it lists no specific files. When I click "install" in the dialogue box about the modules, nothing seems to happen. If I try to start VMware again, same dialogue, same non-result. No error message.

Installation said VMware 9 was successfully installed, although the only way I could figure to install it was using the command line the whole way - never saw the GUI installer.

I've used the code in the last post to check linux-headers-generic, and got the response that they were already updated to the latest version.

Anything else to to try? 

Thanks!

---

### Post by Paresh on 2013-11-05
I think the recompile GUI for VMware is broken.

I've used this command with success:
```
sudo vmware-modconfig --console --install-all
```

---

### Post by re1d on 2013-11-05
> **Paresh said:**
> I think the recompile GUI for VMware is broken.

I've used this command with success:
```
sudo vmware-modconfig --console --install-all
```

I used it, and got a lot of activity, but in the end it failed to compile - at least some modules didn't compile, it says "Unable to install all modules. See log for details." I'd paste the log text but you'd kill me, as it's pages. When I try to start VMware, I still get the dialogue box about the modules, and it still does nothing when I click "Install".

I'm wondering if something is wrong with Ubuntu? I just installed 13.10, clean on a new SSD, last week. But several times I've gotten error messages on startup about system errors, offering to send a msg to Ubuntu. Then the system goes on to run OK, so I haven't worried about it. 

Is there a diagnostic I could run that would correct any system errors? Or would I be better off at this point, since the install is new and not highly personalized, to just install the whole shootin' match over again?

Thanks for any wisdom! Appreciate it very much.

---

### Post by suhongdoan on 2013-11-26
Hi all,

There is an update for workstation 9 (9.0.3 build-1410761) that works with Ubuntu 13.10. I posted on other thread for this update info already, but I think it would help here also.
shd

---

### Post by re1d on 2013-11-27
> **suhongdoan said:**
> Hi all,

There is an update for workstation 9 (9.0.3 build-1410761) that works with Ubuntu 13.10. I posted on other thread for this update info already, but I think it would help here also.
shd

Thanks, will try it - maybe that's the problem. I haven't got VMware working yet - luckily, don't need it immediately. Appreciate it!

Reid

---

