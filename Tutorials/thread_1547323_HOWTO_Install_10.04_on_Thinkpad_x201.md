---
title: "HOWTO: Install 10.04 on Thinkpad x201"
date: 2010-08-06
forum: Tutorials
---

### Post by ssully on 2010-08-06
**Keywords**
[INDENT]thinkpad, x201, 10.04, lucid, blank screen, black screen, install, suspend, change brightness[/INDENT]

**Summary**
[INDENT]As of August 2010, installing 10.04 on a ThinkPad x201 is non-trivial.  The fixes have been worked out in many different forums, but I thought there might be value added in consolidating the process in one place.  I'll try to present every step simply, since more experienced users probably don't need this HOWTO in the first place.  If I miss any steps, or explain anything wrong, please let me know.[/INDENT]

**Sources**
[INDENT]Much more detailed discussions of installation issues and fixes may be found elsewhere.[/INDENT]
[INDENT][INDENT][generic] [http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)[/INDENT][/INDENT]
[INDENT][INDENT][x201] [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554569](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554569)[/INDENT][/INDENT]


[SIZE="4"]1. Initial Installation[/SIZE]
Note: tested with 10.04 on amd64, not alternate installer or i386.
[INDENT]Boot from usb startup disk (or whatever).[/INDENT]
[INDENT]When screen displays small keyboard/ubuntu icon, press escape to avoid it loading the gui with default graphics settings (which will lead to a black screen).[/INDENT]
[INDENT]Select language.[/INDENT]
[INDENT]Press F6, escape from popup menu, and edit Boot Options to include "xforcevesa i915.modeset=0" as follows:[/INDENT]
[INDENT][INDENT]```
Boot Options  noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- xforcevesa i915.modeset=0
```[/INDENT][/INDENT]
[INDENT]Press enter and you will load into the graphical installer environment.[/INDENT]	
[INDENT]Install away.[/INDENT]


[SIZE="4"]2. First Boot After Installing 10.04[/SIZE]
[INDENT]You'll still get a black screen if you try to boot straight away.
[/INDENT]	
[INDENT]Instead, hold down shift after the initial post screen to access the grub menu.[/INDENT]
[INDENT][INDENT]I find this tricky on my x201: if you hold shift too early you'll get a stuck key error---too late and you'll have missed your chance.[/INDENT][/INDENT]
[INDENT][INDENT]If you accidentally load into a blank screen, you can use the [magic sysrq key]("http://en.wikipedia.org/wiki/Magic_SysRq_key") to directly tell the kernel to somewhat safely reboot:[/INDENT][/INDENT]
[INDENT][INDENT][INDENT]Hold down alt while pressing, in sequence, Fn+PrtSc, s, u, b[/INDENT][/INDENT][/INDENT]
[INDENT]Once in the grub menu, highlight the kernel (right now I think it's 2.6.32-21-generic) and press "e" to edit boot options[/INDENT]
[INDENT]In boot options, replace "quiet splash" with "xforcevesa i915.modeset=0":[/INDENT]
[INDENT][INDENT]```
 ... crashkernel=g38M-2G:64M,2G-:128M quiet splash
```[/INDENT][/INDENT]
[INDENT][INDENT]becomes[/INDENT][/INDENT]
[INDENT][INDENT]```
... crashkernel=g38M-2G:64M,2G-:128M xforcevesa i915.modeset=0
```[/INDENT][/INDENT]
[INDENT]Press Ctrl+x to boot with these options enabled.
[/INDENT]


[SIZE="4"]3. Deciding What to Do Next[/SIZE]
[INDENT]At this point 10.04 should have loaded in low graphics mode, and everything should be working reasonably.  You have two options:[/INDENT]
	[INDENT][INDENT][Easy] Stick with reduced graphics (startup and suspend should work after running update, but as of August 2010, you will not be able to change screen brightness).[/INDENT][/INDENT]
[INDENT][INDENT][Harder] Roll your own patched kernel to get full graphics support (startup, suspend, and screen brightness should all work).[/INDENT][/INDENT]


[SIZE="4"]4.a [Easy] Stick with Reduced Graphics.[/SIZE]
	[INDENT]Go ahead and do a full update[/INDENT]
[INDENT][INDENT]```

sudo aptitude update
sudo aptitude safe-upgrade

```[/INDENT][/INDENT]
	[INDENT]Edit /etc/default/grub (e.g. sudo vi /etc/default/grub) to make low graphics persistent:[/INDENT]
[INDENT][INDENT]```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```[/INDENT][/INDENT]
[INDENT][INDENT]becomes[/INDENT][/INDENT]
[INDENT][INDENT]```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash xforcevesa i915.modeset=0"
```[/INDENT][/INDENT]
[INDENT]Then run the grub updater script.[/INDENT]
[INDENT][INDENT]```
sudo update-grub
```[/INDENT][/INDENT]
[INDENT]Go ahead and restart.  You should now be able to boot and suspend without issue.[/INDENT]


[SIZE="4"]4.b [Harder] Roll Patched Kernel[/SIZE]
[INDENT]A walkthrough for compiling the kernel is beyond this HOWTO, but many detailed guides are available[/INDENT]
		[INDENT][INDENT][https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)[/INDENT][/INDENT]
		[INDENT][INDENT][http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)[/INDENT][/INDENT]
		[INDENT][INDENT][http://ubuntuforums.org/showthread.php?t=24853](http://ubuntuforums.org/showthread.php?t=24853)[/INDENT][/INDENT]
[INDENT]The patch is attached.[/INDENT]
		[INDENT][INDENT]Originally posted [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554569](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554569) (comments #40 and #47)[/INDENT][/INDENT] 
	[INDENT]You may not even need to compile yourself if you can find a patched binary for your architecture[/INDENT]
		[INDENT][INDENT]e.g. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554569](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554569) (comments #45 and #46)[/INDENT][/INDENT]
		[INDENT][INDENT]e.g. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554569](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554569) (comments #63 and #64)[/INDENT][/INDENT]
	[INDENT]On first boot after installing patched kernel, you may need to reconfigure Xorg.[/INDENT]
	[INDENT]With the patched kernel, startup, suspend, and brightness should work as expected.[/INDENT]

---

### Post by luisito on 2010-09-15
I installed Ubuntu Lucid on my new X201 today (9/15/2010) using the GUI and the straight forward options. I had no problem whatsoever. The only things that were not set up correctly out of the box were:
1. Screen rotation. It does rotate using the option on System/Preference/Monitor, but the wacom pointer does not reflect it. I fixed it using one of those scripts that can be found in several posts on these forums.
2. Multitouch. I haven't really looked at this yet.

---

### Post by TruViet911 on 2010-09-15
i got mine to work on lenovo x300 without any problems.

---

### Post by belfi117 on 2010-12-02
@ ssully:
I have done all the steps you mentioned, except the patch file (thinkpadx201.diff.tar). Should I install it as well? If yes, then how?
Installing the mentioned 64bit kernel and headers, still I got problems with brightness control and also suspend/wake up.

Can you please help me to get around this problem? Rebooting my laptop many times a day is really annoying.
Many thanks in advance.
Belfi

---

### Post by ssully on 2010-12-19
> **belfi117 said:**
> @ ssully:
I have done all the steps you mentioned, except the patch file (thinkpadx201.diff.tar). Should I install it as well? If yes, then how?
Installing the mentioned 64bit kernel and headers, still I got problems with brightness control and also suspend/wake up.

The patch is used in rolling a custom kernel; some links to detailed HOWTO articles on compiling the kernel from source are provided in the original post. (You would apply the diff file to the source code before compiling.)

At this point, though, your best bet is to skip 10.04 and just install 10.10 instead.  All the relevant bugs appear to have been fixed.

---

### Post by belfi117 on 2010-12-29
Yes, upgrading to 10.10, removing xorg.conf and undoing changes (i915.modeset=0) to grub file worked for me. 
Now the problem is that sometimes after resume x-server restarts! I mean after resume I see a login page, after logging in none of the windows (which I left open before sleep) are open anymore and ubuntu login sound is being played. And I don't know how to reproduce this restart problem.

---

### Post by mike-g2 on 2011-03-16
Hi belfill117, I'm having the same reboot or X restart issue as you.  Did you figure out a solution or work around?

---

### Post by DanPerecky on 2013-05-12
> **ssully said:**
> The patch is used in rolling a custom kernel; some links to detailed HOWTO articles on compiling the kernel from source are provided in the original post. (You would apply the diff file to the source code before compiling.)

At this point, though, your best bet is to skip 10.04 and just install 10.10 instead.  All the relevant bugs appear to have been fixed.  Yes, 10.10 worked great for my X60s Thinkpad. Thanks for the tip. Saved me a LOT of work. Trying 12.04 just hung. Used both in a bootable USB to 'try UBUNTU'.</p><p>used this great video link as a help:</p>[http://www.youtube.com/watch?v=o_02Ca5LJpg](http://www.youtube.com/watch?v=o_02Ca5LJpg). Downloaded the 10.10 vrs from *linux.softpedia.com*. Note: Used vrs 11.x in UNetBootin, as vrs 10.10 was not listed. It worked fine.

---

