---
title: "Which laptop should I buy for dual booting Ubuntu and Windows ?"
date: 2020-04-14
forum: The Cafe
---

### Post by forkiramskla on 2020-04-14
I require to dual boot Ubuntu LTS 18.04 along with Windows 10. Which laptop would you recommend to do so? I would need a good community to troubleshoot with, documentation, step-by-step guides to dual boot Ubuntu on that particular laptop. My minimum storage and RAM requirements are respectively 512 GB, 16 GB. The laptop should have good I/O. The laptop would be used for video editing and playing GTA V and Rainbow Six Siege along with Rocket League, along with a bit of machine learning (thus CUDA support and tensor flow). I would need 8+ hours of battery life when web browsing, watching video/movies, coding. The laptop should also not have any major issues (like overheating for instance) and should last me for a couple of years. The processor needs to be Intel and discrete GPU NVIDIA.

---

### Post by oldfred on 2020-04-14
Similar question and suggestions.
[https://ubuntuforums.org/showthread.php?t=2440682](https://ubuntuforums.org/showthread.php?t=2440682)

But what you want is not a laptop, but a higher end desktop.
Or you have to comprise on just about everything if you really have to have portability.

---

### Post by forkiramskla on 2020-04-14
But what laptop which has portability meets as close to my needs? Which one has very less or no driver issues etc and works almost out of box, and has very detailed installation guides (dual boot)? Please specify model and brand [**[COLOR=#C61919]oldfred[/COLOR]**]("https://ubuntuforums.org/member.php?u=852711")

---

### Post by Hwæt on 2020-04-15
So oldfred's advice is good as gold here. Linux's Achilles heel is laptops. Wireless support has and always will be flaky.

But if you wanted to try it, your best bet is to try to see if you can find a laptop designed with Linux in mind. System76 sells some, Dell sells some. These are probably the best bet since you can use the OS that comes with them, and just install Windows 10 on a separate partition.

The operating system furnished by System76 is Ubuntu-based. A wise idea if these don't fit your particular need, might be to look at the specs of the System76 and XPS Developer Edition laptops that have Ubuntu preloaded. Assuming either vendor isn't popping in their own proprietary drivers, this hardware might be your best bet.

But it also might not be. I will say that Nvidia fairs significantly better than AMD as far as graphics in Linux go, though you furlough Wayland support and GPU passthrough with Nvidia (if that's important to you).

EDIT- Be sure the laptop has an ethernet port. In the past, I've had distributions entirely FAIL to support my wireless chip for YEARS.

---

### Post by forkiramskla on 2020-04-15
[COLOR=#242729][FONT=Arial]I need to dual boot Ubuntu LTS 18.04 along with Windows 10. Which laptop would you recommend to do so? I would need a good community to troubleshoot with, documentation, step-by-step guides to dual boot Ubuntu on that particular laptop. My minimum storage and RAM requirements are respectively 512 GB, 16 GB. The laptop should have good I/O. The laptop would be used for video editing and playing GTA V and Rainbow Six Siege along with Rocket League, along with a bit of machine learning (thus CUDA support and tensor flow). I would need 8+ hours of battery life when web browsing, watching video/movies, coding. The laptop should also not have any major issues (like overheating for instance) and should last me for a couple of years. The processor needs to be Intel and discrete GPU NVIDIA. Please recommend laptop model for me.

[/FONT][/COLOR]

---

### Post by CelticWarrior on 2020-04-15
Welcome.

The battery life requirement seems excessive considering the other CPU/GPU requirements.
Furthermore any laptop works fine with Ubuntu, those who don't are the rare exception. So I suggest you do your own homework, find a model that you like then google that model plus Ubuntu.

---

### Post by slickymaster on 2020-04-15
Threads merged.

Please do not create duplicate threads, it dilutes the community&#8217;s efforts to provide support and causes confusion.

---

### Post by forkiramskla on 2020-04-15
Which Dell laptop model is sold with linux? Maybe I will buy the windows variant and install myself

---

### Post by sdsurfer on 2020-04-15
Hmm, I have two System76 Gazelles and have had zero issues with wireless. Both have Nvidia GPU's. I just recently set up a Dell 5480 with 18.04 and it is also working well, no challenges encountered.

This question really is "how long is a ball of string?" I don't think it's a specific brand and model that is important. If you want to dual boot, I'd say disk space is a huge factor. What I like to do is put the two OS's on different drives, but if partitioned you should be able to pull it off with a single drive.

As for "sold with Linux," a recent experience I had with a Dell Precision Tower desktop will demonstrate. This was when 18.04 was well established and 19+ was in development. Out of the box, the "pre installed" OS was . . . . 16-something! First thing I had to do was upgrade.

The point being, with the exception of Windows which comes with a license, it doesn't matter what a Dell is shipped with, you will probably need to upgrade and at the very least update.

---

### Post by kurt18947 on 2020-04-15
I'm no expert on this stuff, my laptop use is pretty light duty. Not model specific but it sounds like you want more of a 'desktop replacement' with a docking station, not a machine designed for portability. ThinkPads and the higher end Dells have pretty good reputations for Linux compatibility. The last I knew Dells that came with Ubuntu preinstalled were sold as higher end developer machines. The higher end System76 machines seem to meet your requirements. For instance:

[URL="https://system76.com/laptops/oryx"]https://system76.com/laptops/oryx
[/URL]
The benefit of buying from someone who sells machines with linux pre-installed is if you call for support you're not going to hear "Sorry we don't support Linux".

---

### Post by oldfred on 2020-04-15
I would use a vendor that at least supports UEFI update from Linux.
Almost all vendors first level call support will say they do not support Linux, but if they allow updates at least the vendor recognizes some users will use Linux. Dell was one of the earliest vendors to allow UEFI updates.
[https://github.com/rhboot/fwupdate/blob/master/README.md](https://github.com/rhboot/fwupdate/blob/master/README.md)
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist) & 
[https://fwupd.org/vendorlist](https://fwupd.org/vendorlist)

---

### Post by Shibblet on 2020-04-15
Personally, for the things you have requested, I would look at Gaming Laptops...
But, considering the things you want to do with it, it looks more like you'd want to run Windows, and possibly a VM with Ubuntu.

I am a big fan of Asus: Check out the [Zephyrus Laptop]("https://www.asus.com/us/Laptops/ROG-Zephyrus-S17/")

And here is a link to the entire [Gaming Series.]("https://www.asus.com/us/Laptops/Gaming-Series-Products/")

---

