---
title: "Real Time!"
date: 2016-04-06
forum: Ubuntu/Debian BASED
---

### Post by Chris_Stoni on 2016-04-06
Alrighty! I see Ubuntu has ALL of the RT tools available in the repos except for tuna, but that is ok.......since python bits still need to be worked out.

THIS IS NOT A GUIDE, BUT MAY HAVE SOME GUIDEY TYPE BITS!

I have been working on a Hardware Realtime kernel build for Ubuntu that can be shared. Standard GNU warning...not responsible if it messes up your stuff.
Still has full support for all modules that the *Ubuntu 14.04 and 15.10 supports, BUT to use the official Nvidia Drivers it needs a patch and when installed a special call needs to be made so it will ignore the fact it is Preempt RT.

For the kernel can visit this page:
[http://linuxgems.tk/](http://linuxgems.tk/) (still under heavy construction - so for now will include direct download links)
Download here (64bit[buntu64], 32bit[buntu32], configs and source all here):
[https://www.dropbox.com/sh/mk3uad3495h5n0w/AABZvNwyBTcrrATx_3Cb_PA8a?dl=0](https://www.dropbox.com/sh/mk3uad3495h5n0w/AABZvNwyBTcrrATx_3Cb_PA8a?dl=0)

goto the folder(via command line) you downloaded all 4 parts in for your architecture (make sure they are the only .deb packages you have in that folder or move them to their own folder) and "sudo dpkg -i *.deb" and restart. If you use NVIDIA make sure you have gone back to the nouveu drivers before installing the kernel.

To Install the NVIDIA Driver:
Goto this link to get patched nvidia driver(lemme know if you need one patched - leave your video card for me to find the driver easier):
[https://www.dropbox.com/sh/xlwxsm9pkldlbmo/AACDeeJ3iXdv2uJuRi998Q7va?dl=0](https://www.dropbox.com/sh/xlwxsm9pkldlbmo/AACDeeJ3iXdv2uJuRi998Q7va?dl=0)

1) Hold shift to access GRUB when starting your pc and start in recovery mode for the kernel.
2) Disable all Nouveu drivers via modprode and restart again in recovery mode.
3) cd into the nvidia driver folder you extracted and type "sudo IGNORE_PREEMPT_RT_PRESENCE=1 ./nvidia-installer"

Installs and works on both 14.04 and 15.10, 32bit and 64bit machines. Code will be put on GitHub soon.
On a side note. To reduce jitter and get latency to reduce slightly (depending on system and hard drive), disable DMA on the Hard Drive.
"sudo hdparm -d0 /dev/sda" where sda is your hard drive
Also, set concurrency. CONCURRENCY_LEVEL=number_of_cores+1
These 2 little things may not seem like much, but can make a drastic difference where jitter is an issue.

For those of you that want to update their own nvidia driver here are the few steps.
1) extract your nvidia driver. "./nvidia-linux-***********.sh -x"
2) go to the folder NVIDIA-Linux-************/kernel/ and find nv-linux.h (this is the file that needs editing)
3) add #define CONFIG_PREEMPT_RT_FULL 1
4) Find
CONFIG_PREEMPT_RT 
and change it to
#if defined(CONFIG_PREEMPT_RT_FULL)
5) The statement should look something like this when it is done:

#if defined(CONFIG_PREEMPT_RT_FULL)
typedef raw_spinlock_t            nv_spinlock_t;
#define NV_SPIN_LOCK_INIT(lock)   raw_spin_lock_init(lock)
#define NV_SPIN_LOCK_IRQ(lock)    raw_spin_lock_irq(lock)
#define NV_SPIN_UNLOCK_IRQ(lock)  raw_spin_unlock_irq(lock)
#define NV_SPIN_LOCK_IRQSAVE(lock,flags) raw_spin_lock_irqsave(lock,flags)
#define NV_SPIN_UNLOCK_IRQRESTORE(lock,flags) raw_spin_unlock_irqrestore(lock,flags)
#define NV_SPIN_LOCK(lock)        raw_spin_lock(lock)
#define NV_SPIN_UNLOCK(lock)      raw_spin_unlock(lock)
#define NV_SPIN_UNLOCK_WAIT(lock) raw_spin_unlock_wait(lock)
#endif



ENJOY!! A special Thank You to my brother from another mother, Randy. You are awesome!

---

