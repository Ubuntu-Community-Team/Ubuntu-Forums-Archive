---
title: "Frustration... kernel upgrades are still annoying"
date: 2008-06-01
forum: The Cafe
---

### Post by QCompson on 2008-06-01
I've been a linux user mostly full-time at home for the last 5,6 years.  By far I prefer a linux distro to windows 2000/XP/Vista.  Ubuntu has been the most user-friendly linux distro I have used.  However, after 5+ years I *still* cringe when I see there is a kernel upgrade pending, and this happens all too often.

My cringing is for good reason.  Just today I upgraded to  2.6.24-17-generic and after a reboot, surprise! I couldn't get into X because the nvidia drivers were messed up.  Again.  So, like usual, I had to go through a command line process of uninstalling linux-restricted-modules, nvidia-settings, and nvidia-glx, and then reinstalling them again.

I am used to this after all these years of using linux (admittedly, it used to be even more complicated).  But what do new users think?  As annoying as Windows is, I have never had it not load graphically after a reboot (or at least to safemode).  There is nothing worse than fearing new updates; it is unfortunate from a usability as well as a security perspective.

I realize this can probably be blamed on the proprietary nature of the nvidia drivers.  But is there any significant progress being made to break free of these chains?  I have heard that open-source 3d video drivers are being developed for *years* now.

Sorry to rant, but I am just tired of feeling that tinge of anxiety when I see the update icon.

---

### Post by Barrucadu on 2008-06-01
Ouch, bad luck. I'm lucky enough to survive kernel upgrades unscathed.

---

### Post by Phenax on 2008-06-01
Hello,

I've been all over the Linux world. From LFS to Gentoo to Sourcemage, and now currently my main desktop is running Ubuntu Hardy.

Oddly enough, I have an Nvidia 7950GT (nvidia-glx-new) and kernel upgrades on Ubuntu Hardy have never been detrimental to my system. I've upgraded it numerous times. On my parent's computer (The mobo just fried recently :'() I have Xubuntu and a GeForce 6600GT (nvidia-glx-new) and a kernel upgrade has never thwarted it.

(Nostalgic) Back on LFS, Gentoo, or Sourcemage I'd have to compile my own kernel. You had to go through a configuration process of choosing features that are relevant to your hardware; choosing options such as latency. After you do it for one kernel, you could copy over the configuration file and do a "make oldconfig" which would apply the same options and prompt you for any new ones. Usually on these operating systems I'd hold the kernel upgrades until I had a lot of free time.

There are 2d open source drivers (nv) that have worked for 2d non-hardware accelerated applications for quite a while. [Nouveau]("http://nouveau.freedesktop.org/wiki/") are working on drivers that will work with hardware accelerated 3d-graphics. Right now if you are lucky Nouveau might be able to run Glxgears - it's highly experimental and will likely not rival the quality of Nvidia drivers - but in years to come it may be a serious choice for people who value open-source software and still want proper 3d acceleration.

---

### Post by jrusso2 on 2008-06-01
If you install using the restricted drivers manager that shouldn't happen. But if you use other methods it most likely will.

That being said things don't always work as planned. YMMV

---

### Post by BlueSkyNIS on 2008-06-01
> **Barrucadu said:**
> I'm lucky enough to survive kernel upgrades unscathed.

Me too, no problems here using restricted nvidia drivers :popcorn:

Cheers

---

### Post by QCompson on 2008-06-01
> **jrusso2 said:**
> If you install using the restricted drivers manager that shouldn't happen.
Please explain.  I'm pretty sure I used the most n00b-friendly way of installing the nvidia drivers possible this time, i.e. using the GUI dialogue that Ubuntu prompted.  I didn't install them myself, nor with Envy.

Another issue that I just discovered.  Now Virtualbox doesn't work after the upgrade.  Arggh.  :(

---

### Post by KillerSponge on 2008-06-01
I always install the nVidia drivers with Envy, and kernel updates always worked out fine for me, never had any trouble.

---

### Post by SunnyRabbiera on 2008-06-01
well at least linux updates are not as rampant as windows ones where you have to restart everything just for one app...

---

### Post by qazwsx on 2008-06-01
That is the the number one reason why I hate proprietary  drivers.

I had to patch nvidia kernel stuff to get 3D working in 2.6.25 kernel. :mad: :(

---

### Post by Methuselah on 2008-06-01
This is precisely the reason why proprietary drivers are bad.
Obviously, it's not an option for the linux devs to stop developing the kernel because some drivers might break. 
Drivers for which source is available are updated with the kernel so there's no issue with them.

---

### Post by madjr on 2008-06-02
> **qazwsx said:**
> That is the the number one reason why I hate proprietary  drivers.

I had to patch nvidia kernel stuff to get 3D working in 2.6.25 kernel. :mad: :(

Nvidia fixed this
[http://news.softpedia.com/news/NVidia-173-14-05-Display-Driver-Brings-Support-for-X-Org-1-5-86771.shtml](http://news.softpedia.com/news/NVidia-173-14-05-Display-Driver-Brings-Support-for-X-Org-1-5-86771.shtml)

---

### Post by madjr on 2008-06-02
> **QCompson said:**
> I've been a linux user mostly full-time at home for the last 5,6 years.  By far I prefer a linux distro to windows 2000/XP/Vista.  Ubuntu has been the most user-friendly linux distro I have used.  However, after 5+ years I *still* cringe when I see there is a kernel upgrade pending, and this happens all too often.

My cringing is for good reason.  Just today I upgraded to  2.6.24-17-generic and after a reboot, surprise! I couldn't get into X because the nvidia drivers were messed up.  Again.  So, like usual, I had to go through a command line process of uninstalling linux-restricted-modules, nvidia-settings, and nvidia-glx, and then reinstalling them again.

I am used to this after all these years of using linux (admittedly, it used to be even more complicated).  But what do new users think?  As annoying as Windows is, I have never had it not load graphically after a reboot (or at least to safemode).  There is nothing worse than fearing new updates; it is unfortunate from a usability as well as a security perspective.

I realize this can probably be blamed on the proprietary nature of the nvidia drivers.  But is there any significant progress being made to break free of these chains?  I have heard that open-source 3d video drivers are being developed for *years* now.

Sorry to rant, but I am just tired of feeling that tinge of anxiety when I see the update icon.

this is why i prefer linuxmint for friends and family

so they don't brake their system with kernel updates and call me at 2am.

---

### Post by mcduck on 2008-06-02
As long as you have the linux-generic package installed (to make sure that you get _all_ required packages during the kernel update, if you use other than gereic kerenl then get the correct metapackage for that kernel instead) and you have installed the drivers from Ubuntu's repositories nothing should break during updates.

The most common reason I've seen for graphics drivers breaking during kernel updates was that those people had installed a different kernel but didnä't have that kernels metapackage installe, so during the update they got the new kernel image but no restricted modules..

---

### Post by Xbehave on 2008-06-02
slow down, from what ive read the kernel update, nvidia thing only happens if your right on top of your updates, let your kernel updates slip by a day and you should be fine.

---

### Post by QCompson on 2008-06-02
> **mcduck said:**
> As long as you have the linux-generic package installed (to make sure that you get _all_ required packages during the kernel update, if you use other than gereic kerenl then get the correct metapackage for that kernel instead) and you have installed the drivers from Ubuntu's repositories nothing should break during updates.

The most common reason I've seen for graphics drivers breaking during kernel updates was that those people had installed a different kernel but didnä't have that kernels metapackage installe, so during the update they got the new kernel image but no restricted modules..

Thanks for the tip!  I will try installing linux-generic.  This is actually the first time a kernel update has bitten me in a while, but it was frustrating because it brought back many bad memories.

---

### Post by Mr. Picklesworth on 2008-06-02
What would help here is some kind of GUI tool for building software from source that tracks dependencies and integrates with Apt (PackageKit?). It could offer to rebuild software when dependencies change and provide a dummy package that runs make install and make uninstall when added or removed. Could be quite a nice touch ;)

---

