---
title: "Black screen after GRUB menu, &quot;common&quot; fixes haven't helped"
date: 2020-11-15
forum: Server Platforms
---

### Post by apokkalyps on 2020-11-15
I have a Threadripper 2920x server with a GT 710 video card (and some SAS drives) running 18.04.  Mostly this is a headless box I SSH into, which works fine.  But I also have a monitor/keyboard on the rack, and very early on it developed an issue where it was not outputting video from the gt710 for troubleshooting.

I can see the SAS bios loading and it gets to the grub menu.  When I select Ubuntu the screen goes black.  It is booting, as I can still ssh in and access the machine, I'm just not getting hard video out.

I am not very fluent with GRUB editing or kernel flags but I have tried the following things
[LIST]
[*]adding 'quiet splash' to the 'linux' line
[*]adding 'nomodeset' to the linux line
[*]adding 'vga=791' to the linux line
[*]setting 'gfxmode 1024x768`
[*]running `sudo ubuntu-drivers autoinstall` through SSH, which installed a bunch of nvidia packages
[/LIST]

As I said I'm not very fluent with editing settings like the above, so (I cringe to say this but) it is possible I did any of them "wrong" somehow, if things like parameter order matter.  Mainly I put the kernel flags at the end of the linux line, I also tried them between 'ro' and the one extra param I have there for an SSD power saving mode workaround.  I also tried 'nomodeset' without the 'ro' setting (?).  I am willing to try any of them again.

```
$ lspci -k | grep -EA3 'VGA|3D|Display'
42:00.0 VGA compatible controller: NVIDIA Corporation GK208B [GeForce GT 710] (rev a1)
        Subsystem: ZOTAC International (MCO) Ltd. GK208B [GeForce GT 710]
        Kernel driver in use: nvidia
        Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
```

Any ideas?

---

### Post by oldfred on 2020-11-15
If you have not installed nVidia driver, then nomodeset is correct boot paramter to use. 
I normally remove quiet splash and now put in noplymouth. Then I see boot process and perhaps any errors or warnings that are also in log file.

sed -i '/GRUB_CMDLINE_LINUX_DEFAULT/ s/"quiet splash"/"noplymouth"/' /etc/default/grub

Your autoinstall of driver should have worked.
But you can only have one driver installed. New driver does not replace and old driver, so you have to first purge any previous nVidia drivers.
If first install, it now should boot. But you now do not want nomodeset as that prevents nVidia driver from loading.

---

### Post by apokkalyps on 2020-11-16
Thanks for the sanity checks.  What actually ended up fixing it was updating my kernel.  I noticed choosing older kernels in grub booted normally.
4.19.19 and older did not have an issue
4.19.29 was my most "current" kernel.  When chosen through the list of older kernels in "Advanced options for Ubuntu" in grub, it would, rather than blacking out the screen, show text but the video only would freeze (cursor not blinking) after "Loading initial ramdisk..." although booting would continue and I could ssh into a working system.  Choosing that same kernel through the default "Ubuntu" menu option (it being my newest kernel) and it would give me a black screen.
4.19.127 (the last 4.19) had exactly the same behavior.  Chosen through the default menu item when it was the newest installed would give me a black screen, chosen through the "Advanced options for Ubuntu" list, it would show a console that would hang at "Loading initial ramdisk..." while the system finished booting to an otherwise functional state behind the frozen video.
4.20+ Didn't have any wierd problems like this.

`lsb_release -a` says I'm on 18.04.5 and that point release goes out with kernel 5.4 so I went ahead and just upgraded to that, actually I fat-fingered ukuu and updated to 5.5.  But that seems to be working so I don't see a reason to go back to 5.4 or forward to 5.6 or .7 or .8

---

### Post by oldfred on 2020-11-16
This should show if nVidia driver integrated into your kernels:
#What is installed
dkms status

---

