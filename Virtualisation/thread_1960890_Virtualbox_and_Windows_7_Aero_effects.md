---
title: "Virtualbox and Windows 7 Aero effects"
date: 2012-04-18
forum: Virtualisation
---

### Post by OliverHaslam on 2012-04-18
Hi,

I'm trying to make VIrtualbox work with Windows 7's Aero Peek effects, but am having little luck.

I believe the issue is with the graphics driver not supporting it, or not being signed by Microsoft. Is there a known way around this, or a better driver I can use? I've had a Google but so far I'm finding plenty of issues with no fixes.

Cheers!

---

### Post by ronaldbrijo on 2012-04-18
Hi,

I have the same issue. Virtualbox's maximum video size is 256mb, so unfortunately some options of aero  dont work.

---

### Post by OliverHaslam on 2012-04-18
> **ronaldbrijo said:**
> Hi,

I have the same issue. Virtualbox's maximum video size is 256mb, so unfortunately some options of aero  dont work.

Oh, right, so it isn't actually the driver then?

Does Windows need 256MB of graphics RAM in order to use Aero?

---

### Post by Cheesemill on 2012-04-18
You can run Aero under VirtualBox, but its not that straightforward.

First make sure you have given the machine 128MB or more of video RAM and enabled 2D and 3D effects.

Then you have to install the VirtualBox Guest Additions inside Windows 7.

To get 3D support though this has to be done in safe mode as it replaces some Windows system files, so hit F8 when you boot the VM. Then select Devices > Install Guest Additions from the VM menu, this will mount the required ISO. Fire up the CD from Windows Explorer and the installation will start.

When you select the 3D support checkbox a dialog will pop up, make sure you click No at this point or only the 2D drivers will be installed. Click on install, let the machine reboot, and hey-presto you can enable Aero.

---

### Post by Habitual on 2012-04-18
Required:
[http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html#extpack](http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html#extpack)

---

### Post by OliverHaslam on 2012-04-19
Thanks guys. I've got it running but it's crashing/locking/restarting at random. I suspect it is the lack of RAM on the graphics card. Pretty sure it's 64MB, so I'm not sure how Virtualbox thinks it is giving it 128MB. If only we could force it to use system RAM.

---

### Post by anejo on 2012-04-19
Given that your machine could display Aero features IF it was installed as localhost, then besides what has already been said:

Make sure that you set at least 128MB--can go to 256MB--on the Video tab of the Display properties
Make sure that you install the Guest Additions--with 3D selected--in Windows 'Safe Mode'
And it will work!

---

### Post by dzponce11 on 2012-04-19
try 1024 mbs.

---

### Post by anejo on 2012-04-24
> **OliverHaslam said:**
> I'm trying to make VIrtualbox work with Windows 7's Aero Peek effects, but am having little luck

Be nice to hear some feedback...

---

### Post by Amorget on 2012-04-27
Thanks for the guide, I never really thought to turn on Aero effects (never really cared) but came across this thread and was able to get it enabled no problems.

---

### Post by ronaldbrijo on 2012-04-29
Hi,

Thank you for the advice, but i still am not able to activate Aero?

I have followed all the steps,  Maximum video memory i can allocate is 256mb.

---

### Post by OliverHaslam on 2012-05-03
> **ronaldbrijo said:**
> Hi,

Thank you for the advice, but i still am not able to activate Aero?

I have followed all the steps,  Maximum video memory i can allocate is 256mb.

Tried changing the theme? I found that it did not automatically select the Aero theme.

---

### Post by dirtyblanket on 2012-10-13
> **Cheesemill said:**
> You can run Aero under VirtualBox, but its not that straightforward.

First make sure you have given the machine 128MB or more of video RAM and enabled 2D and 3D effects.

Then you have to install the VirtualBox Guest Additions inside Windows 7.

To get 3D support though this has to be done in safe mode as it replaces some Windows system files, so hit F8 when you boot the VM. Then select Devices > Install Guest Additions from the VM menu, this will mount the required ISO. Fire up the CD from Windows Explorer and the installation will start.

When you select the 3D support checkbox a dialog will pop up, make sure you click No at this point or only the 2D drivers will be installed. Click on install, let the machine reboot, and hey-presto you can enable Aero.

thank you-- this really does work. the 3d support is quite buggy for me though, so i ended up deciding to stick with vanilla windows until 3d support is more stable on virtualbox.

---

### Post by lekevinio on 2013-06-18
Thanks for helping with the Aero effect. That works perfectly.
But when I have it installed using the safemode method the resolution is stuck very low.
I tried running Virtualbox with my Nvidia gpu but no luck.
I do have both 2d and 3d checked in the settings. This is one of the reasons I like Vmware just a bit more than Virtualbox. But if it can be fixed that would be great. I'll download and try a windows X guest.

---

