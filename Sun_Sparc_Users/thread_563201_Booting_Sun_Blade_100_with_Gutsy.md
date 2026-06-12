---
title: "Booting Sun Blade 100 with Gutsy"
date: 2007-09-29
forum: Sun Sparc Users
---

### Post by Christophe Jacquet on 2007-09-29
I tried to boot a Sun Blade 100 with the latest Gutsy beta, which failed.

Some time after the message "loading initial ramdisk" appeared on screen, the process stopped with OBP displaying the message "memory address not aligned", and the "ok" prompt returned.

My SunBlade 100 has 512 MB RAM (one module, that I tried to take out and put back).

Any idea will be appreciated. Thanks in advance.

---

### Post by Christophe Jacquet on 2007-09-30
I solved the problems thanks to indications found on Debian mailing-lists.

The problems arises only when you start booting Solaris, then hit Stop-a, and boot the cdrom with "boot cdrom" (which is the case if Solaris is already installed on the machine). It does not arise after a proper poweroff.

The solution is then to set the cdrom as the default boot device, for instance with "setenv boot-device cdrom disk net", then power off the machine, and start it over.

---

### Post by cac on 2007-10-01
> **Christophe Jacquet said:**
> The solution is then to set the cdrom as the default boot device, for instance with "setenv boot-device cdrom disk net", then power off the machine, and start it over.

So you have successfully booted your SB100 using gutsy?  I can not get gutsy to boot at all: either by using gutsy cd to perform an installation or by installing feisty, dist-upgrade, followed by a reboot.  Both scenarios result in the system stopping at "Booting Linux...".  I suspect some kind of framebuffer problem, as it appears to have loaded the kernel just fine.  However I can't reach it though the network so I'm guessing it did not complete the boot and just didn't output anything.  I have auto-boot? set to false to prevent the problem you highlighted above.  I want to fiddle with the video=atyfb kernel arg but I can't seem to find what the silo label is for the default kernel.

I currently running 6.06 on a small gaggle of SB100; 6.10 had some problem I don't recall right now and 7.04 has the xorg mmap problems.  During my experimentation, I installed 7.04 and upgraded to 7.10.  After that finished I restarted gdm and was presented with the greeter!  But before I logged in I thought I had better restart the machine to ensure all of the other os components were correctly running.  This was a big mistake.

---

### Post by netztier on 2007-10-02
> **cac said:**
>  I want to fiddle with the video=atyfb kernel arg but I can't seem to find what the silo label is for the default kernel.

Hm... I'll have to check tonight, but I'm pretty sure that "linux" is the default - and right, **video=atyfb:1024x768@60** (or whatever suits your monitor's capabilities) was what I was about to suggest as boot option for the kernel.

I'll update this post as soon as I'll have one of my SPARC boxes within reach..

*Edit*: here's the current silo.conf from my Ultra 60 with SCSI drives - yours may vary, since the small Blades use IDE for their disks. Kernel parameters can go into the *append=* line; the label seems to be **Linux** (probably case-sensitive):

```
marc@grill:/etc$ more silo.conf
# root=/dev/sda2
root=/dev/disk/by-uuid/c5ea121a-6843-4a0d-917b-1d248fddb33b
partition=1
default=Linux
read-only
timeout=100
append="quiet splash"

image=/vmlinuz
        label=Linux
        initrd=/initrd.img

image=/vmlinuz.old
        label=LinuxOLD
        initrd=/initrd.img.old
```


best regards

Marc

---

### Post by cac on 2007-10-03
> **netztier said:**
> Hm... I'll have to check tonight, but I'm pretty sure that "linux" is the default - and right, **video=atyfb:1024x768@60** (or whatever suits your monitor's capabilities) was what I was about to suggest as boot option for the kernel.

The silo label is case sensitive and is **L**inux, so got past that hurdle.  As a side note, I think the gutsy beta live cd label is **l**inux; I started out by upgrading to gutsy from feisty so that might have something to do with it.

But on to the more interesting problem.  The video arg did not chang anything -- still halts at the "Booting Linux..." message.  I tried several values like *atyfb:off*, *atyfb:on*, *atyfb:1024x768@75* (which is what x likes); no joy.  I'm sure it is something as trivial as getting the right arg and value but unfortunately my experimentation time has expired so I've reverted back to my working 6.06 system image.  Hopefully if my workload lightens up I'll be able try it again.

Thanks for the help!
-Chris

---

### Post by Christophe Jacquet on 2007-10-04
> **cac said:**
> So you have successfully booted your SB100 using gutsy?

Yes, it works. There were two graphic cards in it, the integrated one and a PCI one. I took off the PCI one, and used a "video=atyfb:1024x768@60" paramter just because without it the video signals were out of range for my small LCD monitor.

---

