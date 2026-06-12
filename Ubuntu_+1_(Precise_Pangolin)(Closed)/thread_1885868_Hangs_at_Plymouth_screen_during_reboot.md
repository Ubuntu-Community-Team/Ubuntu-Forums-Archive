---
title: "Hangs at Plymouth screen during reboot"
date: 2011-11-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Quackers on 2011-11-24
I haven't updated Precise for a few days.
I just ran all the current updates (200+ MB) which included the 3.2.0-1 kernel and when selecting reboot the system hangs at the Plymouth screen during shutdown.
It becomes necessary to power off the machine.
I have browsed the recent threads but have not seen this listed. Anybody else finding this? Any remedy?
Thanks

---

### Post by cariboo on 2011-11-24
I had the same problem this morning, but I assumed it was for something completely different. After a bit of investigation, it turns out on my system at least, the nvidia driver didn't get compiled when the new kernel was installed. Re-installing nvidia-current, solved the problem.

My assumption was, that  I had installed a couple of dash lenses from a ppa, and that was what was causing the problem.

---

### Post by Quackers on 2011-11-24
Thanks cariboo907, I can try the nvidia thing.
Actually, thinking about it, it did boot a bit too quickly for a new kernel on the first try. You may well be right :-)

---

### Post by Quackers on 2011-11-24
That's odd!
I got to the login screen then did ctrl+Alt+F1 and logged in there. I purged nvidia-current-updates and nvidia-settings-updates and rebooted.
Same hang at Plymouth during shutdown.
I powered off and back on again. Logged in and although Additional Drivers shows no nvidia drivers in use and symaptic shows only nvidia-common installed, I have the gnome-shell desktop showing.
Is that possible without proprietary drivers?

---

### Post by Harry33 on 2011-11-24
> **Quackers said:**
> That's odd!
I got to the login screen then did ctrl+Alt+F1 and logged in there. I purged nvidia-current-updates and nvidia-settings-updates and rebooted.
Same hang at Plymouth during shutdown.
I powered off and back on again. Logged in and although Additional Drivers shows no nvidia drivers in use and symaptic shows only nvidia-common installed, I have the gnome-shell desktop showing.
Is that possible without proprietary drivers?

You mean can nouveau show G-S desktop?
Yes it can.

See this article here:
[http://www.phoronix.com/scan.php?page=news_item&px=MTAxMTI](http://www.phoronix.com/scan.php?page=news_item&px=MTAxMTI)

---

### Post by Harry33 on 2011-11-24
> **Quackers said:**
> I haven't updated Precise for a few days.
I just ran all the current updates (200+ MB) which included the 3.2.0-1 kernel and when selecting reboot the system hangs at the Plymouth screen during shutdown.
It becomes necessary to power off the machine.
I have browsed the recent threads but have not seen this listed. Anybody else finding this? Any remedy?
Thanks

I have experienced this with my AMD setup (ATI open source x driver).
See this post here:
[http://ubuntuforums.org/showpost.php?p=11473369&postcount=5](http://ubuntuforums.org/showpost.php?p=11473369&postcount=5)

---

### Post by ventrical on 2011-11-24
I don't have that problem with this adapter card:

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AQ [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AQ [Radeon 9600] (Secondary)


but I will check my two systems running nvidia adapters.

---

### Post by effenberg0x0 on 2011-11-24
I can add that using nvidia-proprietary installer, upgrading from 290.03 or 290.06 to 290.10 using the bin default installation procedure, the kernel module is installed / loaded normally. New libs and the soft links mess are also updated correctly. Immediate use of the driver works, and so does the first reboot after install. I couldn't find any warning/error related to nvidia on logs from after the update date. 

What has *never* worked for me using the proprietary installer is dkms. I do loose the kernel module at every kernel upgrade. Manually running the installer bin with the -K option builds and loads the module for the available kernels.

---

### Post by Harry33 on 2011-11-24
> **effenberg0x0 said:**
> I can add that using nvidia-proprietary installer, upgrading from 290.03 or 290.06 to 290.10 using the bin default installation procedure, the kernel module is installed / loaded normally. New libs and the soft links mess are also updated correctly. Immediate use of the driver works, and so does the first reboot after install. I couldn't find any warning/error related to nvidia on logs from after the update date. 

What has *never* worked for me using the proprietary installer is dkms. I do loose the kernel module at every kernel upgrade. Manually running the installer bin with the -K option builds and loads the module for the available kernels.

Well that has never happened to me. Kernel upgrade always works and nvidia module gets automatically installed.
I have always used Ubuntu patched kernels, though, never vanilla ones.
Maybe this is the reason for that.

---

### Post by ronacc on 2011-11-24
I think what he means is when he hand installs the driver from nvidia not through dkms that on subsequent kernel updates dkms does not update the hand installed driver , it never does for me either .

---

### Post by effenberg0x0 on 2011-11-24
> **ronacc said:**
> I think what he means is when he hand installs the driver from nvidia not through dkms that on subsequent kernel updates dkms does not update the hand installed driver , it never does for me either .

Exactly... On may main machine I only use Ubuntu kernels, don't config them, etc. AFAIK, when updating kernel via normal method (apt-get update, dpkg -i <kernel debs), dkms should rebuild the Nvidia module automagically. I never investigated why it doesn't work here though.. maybe it's something simple.

---

### Post by Bowmore on 2011-11-24
I'm not convinced of that this is a driver issue, at least not an ndivia driver issue solely.

I've tried running both *nvidia-current* and *nouveau* which work great but at shutdown or reboot the system hard locks. No magic keys work, e.g Alt+SysRq+B, no registers can be printed, etc, so the power button is the only way out.

At the moment I'm running the older 3.1.0-2 that works, as it's pretty tricky to trace such hard lock errors.

---

### Post by ventrical on 2011-11-24
No prob here using this card:

01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)

with this driver:

---

### Post by Bowmore on 2011-11-24
Mine is:
02:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 330M] (rev a2)

---

### Post by ronacc on 2011-11-24
> **effenberg0x0 said:**
> Exactly... On may main machine I only use Ubuntu kernels, don't config them, etc. AFAIK, when updating kernel via normal method (apt-get update, dpkg -i <kernel debs), dkms should rebuild the Nvidia module automagically. I never investigated why it doesn't work here though.. maybe it's something simple.

I think the reason that it doesn't update is that dkms looks in /usr/src for the nvidia driver to install, and when you hand install those files aren't written.

---

### Post by Quackers on 2011-11-24
Thanks for your links Harry33. I didn't know about gnome-shell being available with nouveau :-)
I'm about to re-install nvidia-current-updates and we'll see if things are sorted.

---

### Post by dino99 on 2011-11-24
no issue with nvidia-current (not -updates) here on i386 & 290.10 (edgers)

---

### Post by Quackers on 2011-11-24
I installed nvidia-current instead but things are still the same :-(
I booted with the last 3.1 kernel and the issue doean't apear there so it's likely to be something in the 3.2 kernel, it seems. Maybe it doesn't like my hardware :-)

---

### Post by ronacc on 2011-11-24
what driver # ? the 290.10 directfrom nvidia works ok on my 64 bit install.

---

### Post by Quackers on 2011-11-24
285.09 at the moment, ronacc.
But the fact remains that this problem doesn't occur with the 3.1 kernel and the nvidia-current-updates driver or the nvidia-current.

---

### Post by ronacc on 2011-11-24
285.09 is nvidia-curent from the repos and that on does have a problem with the 3.2.01 kernel

---

### Post by Quackers on 2011-11-24
Thanks for the info ronacc.
The problem first appeared when I had the nvidia-current-updates driver installed. Sadly I can't remember what version that was :-(

---

### Post by ronacc on 2011-11-24
look in /usr/src and you will see what dkms has available .

---

### Post by Harry33 on 2011-11-24
> **Quackers said:**
> 285.09 at the moment, ronacc.
But the fact remains that this problem doesn't occur with the 3.1 kernel and the nvidia-current-updates driver or the nvidia-current.

Yes I am pretty sure it is a kernel issue.
One mobo/graphics card in my one setup (amd) does not shut down nor reboot with 3.2 kernel.
Two other setups (intel and nvidia) work very well with 3.1 and 3.2 kernels, though.
So, certain hardware have difficulties with 3.2.

---

### Post by Bowmore on 2011-11-25
The new  3.2.0-2 kernel has resolved the shutdown/reboot issue for me :)
However, **vboxhost** still is an issue to be resolved by the VB team.

---

### Post by effenberg0x0 on 2011-11-25
> **Bowmore said:**
> The new  3.2.0-2 kernel has resolved the shutdown/reboot issue for me :)
However, **vboxhost** still is an issue to be resolved by the VB team.

I'm using VirtualBox (not OSE) with Kernel 3.2.0-2. All I did was sudo apt-get install --reinstall virtualbox-dkms.

---

### Post by Bowmore on 2011-11-25
Thanks effenberg0x0, that made my day :P
Hopefully this will work out of the box soon.

---

### Post by effenberg0x0 on 2011-11-25
> **Bowmore said:**
> Thanks effenberg0x0, that made my day :P
Hopefully this will work out of the box soon.

Cool, remember to vote for me on any upcoming elections (for any position) :)
Seriously though, glad it worked. VirtualBox and VMware Player are virtually essential for my work..and I got used to testing PP inside VMs too. At every Kernel update, I got used to the same-old procedure: The thing will boot to console. Run nvidia-x.y.z.run -K (build kernel module), reinstall VirtualBox dkms, start lightdm, run VMware, see it complaining of no Kernel module and asking to build it, pray for it to succeed (the latest being the most complicated), if not start trying to manually fix build errors... It's far from out-of-the-box, but doable quite quickly.

---

### Post by Quackers on 2011-11-28
The 3.2.0-2 kernel seems to have cured this problem for me :-)
I'll mark as solved.

---

### Post by Harry33 on 2011-11-28
> **Quackers said:**
> The 3.2.0-2 kernel seems to have cured this problem for me :-)
I'll mark as solved.

Same here, fixed.
Now there is a new build of this rc3 3.2 kernel:
[https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-2.5](https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-2.5)

---

