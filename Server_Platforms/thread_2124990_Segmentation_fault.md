---
title: "Segmentation fault?"
date: 2013-03-12
forum: Server Platforms
---

### Post by d4m1r on 2013-03-12
Hey guys, today I tried to update a ubuntu server I have running at home for testing purposes. It is an older (non-pae) machine running 32bit 12.04 LTS but it failed to update with the errors below. Now it won't even boot to Ubuntu so I will likely have to reinstall it. What went wrong? Did it try to install a PAE kernal even though it is not supported? Before starting the update, it did correctly say several *PAE packages were being ignored...

[IMG]http://i.imgur.com/xa6vRAW.png[/IMG]

---

### Post by tgalati4 on 2013-03-12
Your screen shot is showing that grub found pae kernel images.  Post the output of:

```
ls -la /boot
```

I think your suspicion is correct, the update loaded a pae kernel, and if your processor can't handle it, then nothing will work.

You should be able to boot into a previous kernel.  Do you have them listed in grub when you boot up?

---

### Post by d4m1r on 2013-03-12
I can't even access it because it is a remote machine I don't have access to if it won't boot...So it is literally easier for me to reinstall Ubuntu.

Now, how can I prevent this happening again? As in, make SURE it is ignoring the *PAE packages when updating

---

### Post by d4m1r on 2013-03-13
Anybody? This doesn't even have to be server related....Basically, you have a non-pae 12.04 LTS system you want to update. How do you get it to COMPLETELY ignore ALL *pae packages?

---

### Post by tgalati4 on 2013-03-14
I don't think there is a way to do it, without pinning your current kernel version.  That means that your kernel won't get security updates that you expect.  I was under the impression that Ubuntu dropped support for non-PAE architecture, so loading non-PAE kernels is a "roll-your-own" activity.  That also means unsupported.  Several smart and kind folks have built non-PAE kernels and instructions on how to load them, but I wouldn't expect many updates going foreward.  

If you really need updates, then you will have to create a build environment for your non-PAE machine, download the source code for the latest 12.04 kernel and build it with the appropriate non-PAE switches enabled during kernel configuration.  If you do this every 6 months, you are looking at a few hours of compile time twice a year.  I would look for a PAE machine myself--there are lots of cheap Dell PowerEdge servers available.  You will have to weigh the agony units of each method.

The upside is you will get experience with compiling kernels--a useful skill that ranks up there with changing main engine bearings and rewiring a house.  Something that you don't perform often, but it takes time, patience, and will cause eyes to glaze over when you try to describe it.

---

### Post by d4m1r on 2013-03-14
Thanks for the reply. So how would I pin a kernel (as in get apt-get to ignore ALL kernel updates)? Any potential issues with that in terms of software compatibility/stability?

Apart from the security risks involved with running an older kernel...

---

### Post by schragge on 2013-03-14
[apt_preferences(5)]("http://manpages.ubuntu.com/manpages/precise/en/man5/apt_preferences.5.html")
[http://wiki.debian.org/AptPreferences](http://wiki.debian.org/AptPreferences)
[uhelp]community/PinningHowto[/uhelp]
[Debian Reference, Ch. 2. Debian package management]("http://www.debian.org/doc/manuals/debian-reference/ch02.en.html#_tweaking_candidate_version")

---

### Post by steeldriver on 2013-03-14
isn't all the 'Input/output error' and 'Read-only filesystem' stuff strange? is there something else going on here that's preventing the proper update (disk failure?) or are those consequences of the possible kernel mismatch?

---

### Post by schragge on 2013-03-14
@**steeldriver** Good call. Somehow I've forgotten that this thread's name is *Segmentation fault*. I think any consequences of the kernel mismatch would be seen only on reboot. Until then the old kernel is still in charge of the system.

---

### Post by d4m1r on 2013-03-14
So wait. Let's say I was doing the update and it DID pickup the PAE kernels....Would I not see a problem until I reboot the system? Aka, the installation of PAE kernels would complete successfully on non PAE machines because the old kernel was still the one in use? Of course you'd see the problem when you reboot the machine though because it would use the latest kernel....

---

### Post by tgalati4 on 2013-03-14
Yes, you are generally correct, you are running the old kernel until reboot, however, updating grub and the kernel packages will cause the creation of a new initrd (inital ram disk) and that requires running the new code.  The error in the original post happened when grub tried to configure itself to add a new kernel entry into the grub boot list.  The I/O error looks like a hard disk error, and it could be, but the fact that you are convinced that your machine cannot handle PAE and you have PAE kernel images is going to be problematic.

---

### Post by d4m1r on 2013-03-14
So basically, since my system does not support PAE, it should have never reached that step? This means we can ignore the Disk I/O errors as those are a side issue.

It seems to have downloaded/installed a non supported kernel and tried to add it to grub...That shouldn't have happened.

---

### Post by schragge on 2013-03-15
To me, PAE is a side issue, and the segmentation fault is the root problem. *update-initramfs* doesn't run any code from the new kernel. It's a shell script that invokes another shell script, *mkinitramfs*, that simply creates an initrd image with new kernel and modules as a gzip-compressed cpio archive. You can invoke update-initramfs manually and see it for yourself. I'd suggest adding *set -x* at the top of */usr/sbin/mkinitramfs*, and re-running *update-grub* to see at which line in the script the segmentation fault occurs.

The message [COLOR=green]Generating grub.cfg ...[/COLOR] after which the first segmentation fault occurs, actually comes from */usr/sbin/grub-mkconfig* that gets invoked by *update-grub*. It's also a shell script, so adding *set -x* there is possible, too. If *grub-mkconfig* doesn't work properly, no wonder grub picks the wrong kernel.

But first, look if there's */boot/grub/grub.cfg.new*. The last thing *grub-mkconfig* does is *mv grub.cfg.new grub.cfg*, so if it fails, the .new still will be there.

---

