---
title: "Odd things about Ringtail and usb"
date: 2013-03-21
forum: Ubuntu Development Version
---

### Post by Dark_Horizon on 2013-03-21
Well I've been giving it a trial on DVD not installing so far, mainly because in the past this has not gone all that well for me. As to the Live trial, I was pleasantly surprised as I installed in memory restricted extras and gave the dash search and preview a walk round the block and was quite happy with it.
I then thought it would be a good Idea to try it from a Pen drive, I had a spare 4GB one so I thought it should be straight forward, no such luck. I just can't get it to boot from USB it copies but won't boot I tried copying using startup disk in 11.04 and 12.04. I thought it would be usefull to test it further but installing a number of packages and saving the settings on the USB.

I did note that there was no right click on the desktop and everything went through the dash.

Is this a known USB problem with Ringtail, I had a look round and found others with the same problem.

---

### Post by dino99 on 2013-03-21
a very minimum is at least 8 GB, but 10 / 12 is recommended to get enough room for virtual ram and uncompressing the downloaded packages before upgrading

---

### Post by grahammechanical on 2013-03-21
> [COLOR=#000000]I just can't get it to boot from USB it copies but won't boot[/COLOR]

That does not tell us much. It does not help to narrow down the possible cause.

I cannot boot from USB or DVD. But then I do need to replace the CMOS battery. So, I am running on the BIOS defaults and I have not set a boot priority in the BIOS. Then again from November to March every Raring ISO image that I tried would start to load and then dump me at a Busybox prompt unless I modified the boot parameters in some way.

Having said that I do have an ISO image of Raring Edubuntu on USB and provided I have the boot priority set correctly, it works fine. So, I would not agree that Raring has a particular problem running from a USB. Some people have problems running a live session from DVD and USB when using already released versions of Ubuntu.

---

### Post by cariboo on 2013-03-21
I've used the startup-disk creator utility successfully the last two times I created a usb drive to install Ubuntu Gnome. I've also used dd:

```
sudo dd if=raring-desktop-i386.iso of=dev/sdc bs=1M
```

change the /dev/sdc to what ever your usb device is labelled as.

---

### Post by Dark_Horizon on 2013-03-21
Right just in case you didn't understand; I was making a (try or install) USB pen drive of 13.04, today&#8217;s daily build to test it out on various laptops and PC's. However, it failed to work as did the previous daily build. I have now tried (start-up disk creator) putting 12.10 on exactly the same drive  and it works fine, boots my laptop and pc no problem.
 

 Its not a question of boot sequence which is set to boot from USB first or what it's labelled, as far as I can see. Since the 12.10 works well from the 4gb pen drive. What I want to know is why is it failing with 13.04 and is there perhaps another way of getting it to image to the (4gb Pen drive) for testing purposes only.

 

 There seems to be some confusion here as to what I was doing and why, I'm not installing it I'm making the equivalent of a more functional live CD but with the USB pen drive I am able to store settings and some programs for test and demonstration purposes.

---

### Post by Dark_Horizon on 2013-03-29
Now an update; it had to be a problem with the image of ringtale, I have made a usb image for 13.04 on two machines now using startup disk creator  and they are working fine and both on the same USB pen drive. However, to what I was doing in the first place, making a more functional try or install image of 13.04. Rather than trialing out the bare desktop with no flash support Mp3 etc., I've installed screenlets , Cairo dock and Restricted extras on the trial so that I can test out the various functions. The odd thing is that if I use it for any time it stops recognising the Firefox browser. I thought that I should try it on a larger drive  since I was restricted in home folder size to 2GB on the 4GB pen drive, so I've tried it on a 16GB USB Sandisk Flash drive, which was slow to make the image and really slow to boot from it. I did however, get the same problem with firefox once I had used the trial and installed software into it, Installing the software to the trial image was massively slow a go and make tea slow with a couple of rounds of toast.

Has anyone else tried this, not the tea and toast thing obviously, but making the more functional image by installing software to the trial on USB pen or flash drive then installing third party software on it. This is a (trial or install) image run from USB Pen or flash drive I should add.

---

### Post by kevpan815 on 2013-03-30
I've had trouble with USB Start Up Disk Creator in BOTH 12.10 & 13.04 Nightly. That's why I use 12.04.2 on my 2010 Dell Net Book (since I can't get it to run on my 2013 Dell Laptop, KERNEL is to old) to create each Nightly Build of Ubuntu.

---

### Post by kevpan815 on 2013-03-30
By the way, when creating the USB, you need to create a Persistence File if you are using the Desktop Images. Even if its AMD64, you still need the File. FYI.

---

### Post by pfeiffep on 2013-03-30
I have been successful ***INSTALLING*** daily 13.04 to 8 Gb usb stick and to a usb hdd. Both boot just fine ... I know this isn't exactly the save as booting a live instance, which I also have been successful making a live dvd persistent by using another usb stick.

---

