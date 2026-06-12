---
title: "Boot process stuck at 'Loading initial ramdisk'"
date: 2018-07-04
forum: Ubuntu/Debian BASED
---

### Post by uraisag on 2018-07-04
I've installed Elementary OS 0.4.1 Loki (64 bit) on a Lenovo with Intel Corporation Sky Lake Integrated Graphics. The install process went fine and it generally works great with kernel Linux 4.13.0-32-generic. With any newer kernel there's a graphics issue that causes the screen to simply be black, not allowing the decryption password prompt to ever appear (graphically). That, however, is not my problem - since, as I said, kernel 32 generally works well. But there is something that has happened twice now. The first time it happened I wasn't able to find a solution and ended up reinstalling the OS. But I would really, really prefer not to do that again. So any help would be appreciated.

For some reason, which I've haven't determined yet, the system will very randomly freeze, and when I perform a hard reset (holding down the power button), once it boots again it simply shows the glowing elementary logo. I've gone into grub and edited the boot parameters to remove [FONT=courier new]quiet splash[/FONT] and add [FONT=courier new]nomodeset[/FONT] but the only thing that gets printed is [FONT=courier new]Loading Linux 4.13.0-32-generic[/FONT] and [FONT=courier new]Loading initial ramdisk[/FONT], at which point it hangs. I've even also added [FONT=courier new]debug[/FONT] and [FONT=courier new]ignore_loglevel[/FONT] to the boot parameters but no other information gets printed to the screen during boot. Further, it doesn't seem like it's just a specific kernel issue because even when I attempt to boot with the other kernels I have installed it hangs at the same place.

I've also tried to use [FONT=courier new]boot-repair [/FONT]but the problem persists. For brevity, here's the log created by it:

[https://pastebin.com/raw/3wW2YTv0](https://pastebin.com/raw/3wW2YTv0)

I've looked through the logs of my system and they don't reveal much.. but it does seem that this was logged just before the system froze the last time:

[FONT=courier new][drm:intel_pipe_update_end [i915]] *ERROR* Atomic update failure on pipe A[/FONT]

Also, it seems like this isn't simply an issue with the kernel, as when I try to select different kernels that are installed via the grub menu they all get stuck at the same point noted above.

Further, I've made [FONT=courier new]timeshift[/FONT] backups and restoring to such backups achieves nothing. The boot still hangs at the same point. 

Note that I can successfully boot into recovery mode, which is how I'm writing this message now. But of course, I would prefer to be able to boot and for the system to operate normally.

Has anyone encountered this as well (& solved it)? Thanks!

P.S. I've also posted this on the elementary os stack exchange, which you can see here: [https://elementaryos.stackexchange.com/questions/15856/boot-process-stuck-at-loading-initial-ramdisk](https://elementaryos.stackexchange.com/questions/15856/boot-process-stuck-at-loading-initial-ramdisk)

---

