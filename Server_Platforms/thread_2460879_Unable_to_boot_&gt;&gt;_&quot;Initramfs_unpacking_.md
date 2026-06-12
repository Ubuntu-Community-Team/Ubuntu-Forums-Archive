---
title: "Unable to boot &gt;&gt; &quot;Initramfs unpacking failed: junk within compressed archive&quot;"
date: 2021-04-20
forum: Server Platforms
---

### Post by jim.cat on 2021-04-20
I rebooted after some updates, it had not been rebooted for  several months so I thought it was due. Now however does not boot, and  outputs this:

[IMG]https://dl3.pushbulletusercontent.com/JxyXoEGYvPdJC1ngEBBCjidOq2vHn2Ek/20210420_135526.jpg[/IMG]

The most notable errors are:
"Initramfs unpacking failed: junk within compressed archive"
"Kernel Panic - Not syncing:  No working init found"

This is ubuntu server arm64, on a raspberry pi 4, booting from an SD card that upon basic checks seems to be completely healthy.

Also, intitially I was not able to connect it to a screen, so since it was not coming online I gave it a few manual powercycles; I am not  sure wether the error showing now was the error that initialy made it  not to boot up, or wether this kernel panic may have been caused by  several powercycles without proper shutdown. 

Any ideas about what this can be or how to debug it further? Or -most interestingly- how to sort it out?

---

### Post by LHammonds on 2021-04-21
> **jim.cat said:**
> I rebooted after some updates, it had not been rebooted for  several months so I thought it was due.You should not have to guess if you need to reboot after an update.  Check for the existence of this file in order to know if you need to reboot for certain updates to complete (such as kernel updates)

```
ls -l /var/run/reboot*
```

If you do not see a couple of files, then there is no need to reboot due to pending updates.  I have my servers automatically reboot if they see those files during the maintenance window.

My wild guess is that you applied several updates that included newer kernels but were running such an old kernel that it got purged.  But since this a boot problem, you will probably need to boot a LiveCD and then use the commandline to mount root and boot to /mnt and then chroot them and instruct grub to rebuild.

LHammonds

---

### Post by jim.cat on 2021-04-21
It needed a reeboot, it had been needed for quite a while. But even if old kernels have been purged, should new ones not work straightaway? I don't see why not rebooting for monts should lead to an unbootable system.

Thanks for your help. Would you be able to direct me on how to "chroot and instruct grub to rebuild" when the architecture is different the system is arm64 (Raspberry Pi 4) and I would be doing this in a amd64 computer. I do not seem to find any guiedance on how to do this in ubuntu, and what I have tried to do with other guides has so far not worked.

---

### Post by LHammonds on 2021-04-22
> **jim.cat said:**
> It needed a reeboot, it had been needed for quite a while. But even if old kernels have been purged, should new ones not work straightaway? I don't see why not rebooting for monts should lead to an unbootable system.

Thanks for your help. Would you be able to direct me on how to "chroot and instruct grub to rebuild" when the architecture is different the system is arm64 (Raspberry Pi 4) and I would be doing this in a amd64 computer. I do not seem to find any guiedance on how to do this in ubuntu, and what I have tried to do with other guides has so far not worked.
It has been a LONG time since I have had boot problems (knocks on wood)...somewhere around Ubuntu Server 10.04 if I recall correctly so the process might be different now.

Did a quick search and several guides seem to mention boot-repair including the [Ubuntu documentation](https://help.ubuntu.com/community/Boot-Repair).  But [this guide](https://linuxhint.com/ubuntu_boot_repair_tutorial/) seems to go into more detail on usage.

I have never performed a boot repair on anything other than a standard Ubuntu server install.  I would imagine it would be very similar unless the device cannot make use of a LiveCD with a GUI.   If no GUI, then you'll have to resort to command-line...which is what I did for Ubuntu Server 10.04.  But the critical point to make here is that you use the same "installation software" that you used to install the OS in the 1st place.  So if you have Ubuntu Server 18.04 for ARM installed, make darn sure the LiveCD you are booting up is "Ubuntu Server 18.04 for ARM" and not 18.04 for amd64 or 20.04 or ARM, etc.

As for how to do the mount and chroot, [here is an article](https://steemit.com/utopian-io/@roj/how-to-install-or-repair-grub-2-with-ubuntu-live-cd-flash) that covers how they did it.  I seem to recall only mounting /boot and root but then again, it was a LONG time ago and my memory ain't that great.  But the process was very similar to how I recall doing it from the command prompt.

LHammonds

---

