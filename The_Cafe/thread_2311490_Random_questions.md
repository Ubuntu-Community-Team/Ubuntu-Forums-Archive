---
title: "Random questions"
date: 2016-01-27
forum: The Cafe
---

### Post by KayeNg on 2016-01-27
Hi guys.

1.  If I unplug the hard disk from the motherboard, then boot into an Ubuntu live USB, and plug in said hard disk to the motherboard while live USB is running (i.e. while live USB is in use), what would happen?

2.  Is it or is it NOT possible to upgrade from currently installed long term support DIRECTLY to the _latest_ long term support? Or do I have to, for example, update to 15.04, then 15.10, then to the latest (thru the terminal)? I've read a few articles and I still don't know.

3.  Only 1 GB of RAM installed in motherboard, how much swap space is best?

4.  Hard disk is plugged into the motherboard.  Turn on the computer, no beeping sound, and it cannot get past the POST screen and cannot get into BIOS by pressing F2.  
 However if hard disk is unplugged, beep sound is present, pressing F2 can get me into BIOS.  So apparently hard disk is the problem.  My question is, is the hard drive still usable? 
 Because how can you even test it or install an OS in it if you can't even get past the POST screen.  You can only get past POST or access BIOS if hard disk is unplugged from motherboard.  (this is        why I ask question number 1)

---

### Post by pfeiffep on 2016-01-27
From this description
> 4.  Hard disk is plugged into the motherboard.  Turn on the computer, no  beeping sound, and it cannot get past the POST screen and cannot get  into BIOS by pressing F2.  
 However if hard disk is unplugged, beep sound is present, pressing F2  can get me into BIOS.  So apparently hard disk is the problem.  My  question is, is the hard drive still usable? 
 Because how can you even test it or install an OS in it if you can't  even get past the POST screen.  You can only get past POST or access  BIOS if hard disk is unplugged from motherboard.  (this is        why I  ask question number 1)I suspect that there is a problem with the hard drive or the cable connecting the hd to mb. If you have another cable try that first. If you have another hd try that second.

---

### Post by grahammechanical on 2016-01-27
> 2.  Is it or is it NOT possible to upgrade from currently installed long term support DIRECTLY to the _latest_  long term support? Or do I have to, for example, update to 15.04, then  15.10, then to the latest (thru the terminal)? I've read a few articles  and I still don't know.

It all depends on the setting we have in System Settings>Software & Updates>Updates tab. If "Notify me of a new Ubuntu version" is set "For any new version" we will be notified of the next new version. If we are on 15.10 the next notification would be 16.04.

If the setting is "For long term support versions" & we are on 15.10 then we will be notified when 16.04 is released as it is LTS. If we are on 14.04 LTS then we will be notified when 16.04 is released.

At this period of Ubuntu development users on 14.04 should stay on 14.04 until 16.04 is released and then they can do a direct upgrade to 16.04. Users of 15.04 should upgrade immediately to 15.10 because 15.04 is about to reach end of life. 

User of 14.04 who for some reason want to upgrade to 15.10 should do a fresh install.

> 3.  Only 1 GB of RAM installed in motherboard, how much swap space is best?

Will we be using hibernation? If so, then the general rule is a little more than twice the amount of RAM. Uses with several GB of RAM might rarely need swap. So, if they are not going to hibernate then the general rule does not apply and swap space less than the amount of RAM might be sufficient.

Regards.

---

### Post by grahammechanical on 2016-01-27
> Because  how can you even test it or install an OS in it if you can't even get  past the POST screen.  You can only get past POST or access BIOS if hard  disk is unplugged from motherboard.  (this is        why I ask question  number 1)

Leave the hard disk connected. Boot into a live session and use the Disks utility. Does it see the hard disk? The disk utility can access the S.M.A.R.T data of the hard disk. That might give some information about the condition of the drive.

I do not see how a failing hard drive could stop the motherboard running POST or prevent access to the BIOS set up utility. POST is run first before the hard drive is accessed. These things happen very quick. so, we have to be quick to hit the key to enter the BIOS. I hit it repeatedly but slowly from the moment I see the motherboard splash screen until the BIOS utility loads.

Regards.

---

### Post by pfeiffep on 2016-01-27
@grahammechanical
> I do not see how a failing hard drive could stop the motherboard running  POST or prevent access to the BIOS set up utility. POST is run first  before the hard drive is accessed. These things happen very quick. so,  we have to be quick to hit the key to enter the BIOS. I hit it  repeatedly but slowly from the moment I see the motherboard splash  screen until the BIOS utility loads.I certainly agree mostly with this, but I have seen, while building PCs commercially, a shorted cable or otherwise defective component stop a MB from entering post.

---

### Post by KayeNg on 2016-01-27
Thank guys.
grahammechanical, I'm currently on 14.04.  How exactly do I upgrade _directly_ to 16.04 long term support when it final comes out? Just wait for the notification? Or do I type something in terminal? And would it be faster if I just did a fresh install of 16.04 LTS?

> [COLOR=#000000]Leave the hard disk connected. Boot into a live session and use the Disks utility. Does it see the hard disk? The disk utility can access the S.M.A.R.T data of the hard disk. That might give some information about the condition of the drive.[/COLOR]
That's what I'm trying to say.  I haven't tried it yet with live USB, but I CANNOT boot into an install dvd **_if_** the hard disk is plugged in the motherboard.  I have to unplug hard disk so that I can get past POST and actually boot the dvd.  I suspect the same with booting live USB.  I'll try later.  I'll also try a different hard disk if I can find one.

Thanks guys.

---

### Post by KayeNg on 2016-01-28
Confirmed. Cannot boot into live USB if hard disk is connected to motherboard. I disconnected hard disk and was able to boot live USB. I'll try connecting a different hard disk.

---

### Post by KayeNg on 2016-01-28
Also grahammechanical, I'm not sure what hibernate means. I only know sleep mode in windows system.

---

### Post by grahammechanical on 2016-01-28
We are going off topic. But that is normal for this forum. Which is the only forum I know.

There is suspend which is usually suspend to RAM. It is where the state of the OS is preserved in memory (RAM) and then most but not all of the components are powered off to save battery power.

Then there is hibernation which is suspend to disk. It is where the state of the OS is preserved on the hard disk allowing all of the components to be powered off. In Linux hibernation uses the swap partition which must be as large as the amount of RAM. In Windows a swap file is used which I expect is variable in size.

In new versions of Windows hibernation is used to give the effect of a very quick start up of Windows. If we, in Ubuntu, try to access an hibernated Windows partition then we will get an error message.

For Microsoft sleep mode = suspend to RAM (Linux suspend). And hibernation = suspend to disk (Linux hibernate).

[http://windows.microsoft.com/en-gb/windows7/sleep-and-hibernation-frequently-asked-questions](http://windows.microsoft.com/en-gb/windows7/sleep-and-hibernation-frequently-asked-questions)

As for upgrading from Ubuntu 14.04 to 16.04, just wait until the end of April and then when you update the OS you will be notified of the new version available and can upgrade to it with one click. For a few days we may even get a nag message about upgrading.

 My advice would be to first deactivate any proprietary video driver and use the open source video driver for the upgrade. And yes, we can use a command but in Ubuntu we do not need to.

Regards.

---

### Post by stalkingwolf on 2016-01-30
> 1. If I unplug the hard disk from the motherboard, then boot into an Ubuntu live USB, and plug in said hard disk to the motherboard while live USB is running (i.e. while live USB is in use), what would happen?


in my experience if you plug a HDD into a running system  one of two things possibly both will happen.   you will fry the motherboard or a part of it, you will fry the hard drive, or both to one degree or another.

---

