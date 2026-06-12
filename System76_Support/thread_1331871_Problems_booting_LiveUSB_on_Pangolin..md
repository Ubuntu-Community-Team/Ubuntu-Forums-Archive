---
title: "Problems booting LiveUSB on Pangolin."
date: 2009-11-19
forum: System76 Support
---

### Post by jwbrase on 2009-11-19
I'm running a Pangolin, model number PAN-P5, order #8538 for specific details.

Back in October, I decided I wanted to resize the /home and / partitions, as detailed in [this]("http://ubuntuforums.org/showthread.php?t=1284446") thread. I eventually decided to follow the recommendation of using an Jaunty LiveUSB to resize (I'd been considering using a Parted Magic USB), based on the fact that an Ubuntu LiveUSB could also be useful in the event of various failures. However, I've been unable to get the USB to boot to a GUI. Once I select the "Try Ubuntu without any change to your computer" option, I get a splash screen, then "Loading... please wait", whereupon I am dropped into Busy Box with an initramfs prompt.

In researching the problem, I've found several mentions of similar problems such as [this]("http://ubuntuforums.org/showthread.php?t=765195") thread (I've read the first few and last few pages), generally indicating that the problem is somehow hardware related and giving various workarounds that generally seem to be fairly hardware-specific (one solution was for a machine with a floppy drive and simply involved inserting any old floppy, but that doesn't apply to the Pangolin). Also, many of the people experiencing similar problems were getting error messages between "Loading... please wait" and the drop into Busy Box, but I'm getting no such errors, and no explanation for why I'm being dumped into Busy Box instead of a GUI.

I see some mention that there may be a kernel bug that affects multiple distros involved, but since other people experiencing similar problems seem to see a broad range of specific symptoms and solutions, and the person that mentioned a kernel bug didn't mention his exact symptoms, I don't know if this bug is a possible cause of my problem.

Are there any known previous occurrences/solutions of this problem on the Pangolin?

---

### Post by jdb on 2009-11-19
> **jwbrase said:**
> I'm running a Pangolin, model number PAN-P5, order #8538 for specific details.

Back in October, I decided I wanted to resize the /home and / partitions, as detailed in [this]("http://ubuntuforums.org/showthread.php?t=1284446") thread. I eventually decided to follow the recommendation of using an Jaunty LiveUSB to resize (I'd been considering using a Parted Magic USB), based on the fact that an Ubuntu LiveUSB could also be useful in the event of various failures. However, I've been unable to get the USB to boot to a GUI. Once I select the "Try Ubuntu without any change to your computer" option, I get a splash screen, then "Loading... please wait", whereupon I am dropped into Busy Box with an initramfs prompt.

In researching the problem, I've found several mentions of similar problems such as [this]("http://ubuntuforums.org/showthread.php?t=765195") thread (I've read the first few and last few pages), generally indicating that the problem is somehow hardware related and giving various workarounds that generally seem to be fairly hardware-specific (one solution was for a machine with a floppy drive and simply involved inserting any old floppy, but that doesn't apply to the Pangolin). Also, many of the people experiencing similar problems were getting error messages between "Loading... please wait" and the drop into Busy Box, but I'm getting no such errors, and no explanation for why I'm being dumped into Busy Box instead of a GUI.

I see some mention that there may be a kernel bug that affects multiple distros involved, but since other people experiencing similar problems seem to see a broad range of specific symptoms and solutions, and the person that mentioned a kernel bug didn't mention his exact symptoms, I don't know if this bug is a possible cause of my problem.

Are there any known previous occurrences/solutions of this problem on the Pangolin?

You might try a liveCD instead of the liveUSB.

jdb

---

### Post by Eldera on 2009-11-20
Hello, jwbrase

Are you still out of your home country with no CD s available?

[quote=jwbrase]Are there any known previous occurrences/solutions of this problem on the Pangolin?[/quote]

Yes, I had this problem.

I am very inexperienced and learning Linux by trying things. The first bootable USB stick I made booted into that initramfs screen. Since I did not understand what to do, and did not urgently need the USB stick, I erased it. Because of some other things I was trying, I wiped my hard drive and did clean installs of my OS a couple of times. After a few months, I tried again and from freshly downloaded ISO files made USB sticks of Hardy, Jaunty, and Karmic that do boot into a Gui.

The only thing I can tell you from my experience is that the problem on the Pangolin is probably in the software or a corrupted ISO image rather than the hardware. I have made good and bad sticks on the same hardware.

I am running a S76 panp4n, core 2 duo T5800, 3GB RAM, HD 320GB 5400 RPM, nVidia GeForce 9300M GS with Jaunty 64 bit/Hardy 32 bit/Jaunty 64 bit in a tri boot set up. The successful Jaunty and Karmic sticks were made on the Jaunty partition with a kernel 2.6.28-16 generic. I don't remember what kernel I had when I made the good Hardy. I think I was running Intrepid when I made the bad stick.

I hope you can get your troubles worked out soon.

---

### Post by jwbrase on 2009-11-20
> **Eldera said:**
> Hello, jwbrase

Are you still out of your home country with no CD s available?

Yeah, I'll be here for a year, although now I probably should be able to get ahold of a CD blank (now that I have my student ID, it's valid as a rail pass and I can use any public transportation in the Berlin/Brandenburg area for free). But the mentions of similar problems that I've seen seem to indicate that this can happen with either a CD or a USB, so it might not work even with a CD. If I get the time to buy a stack of blanks in the next week or so, I'll try burning a LiveCD.

> 
Yes, I had this problem.

I am very inexperienced and learning Linux by trying things. The first bootable USB stick I made booted into that initramfs screen. Since I did not understand what to do, and did not urgently need the USB stick, I erased it. Because of some other things I was trying, I wiped my hard drive and did clean installs of my OS a couple of times. After a few months, I tried again and from freshly downloaded ISO files made USB sticks of Hardy, Jaunty, and Karmic that do boot into a Gui.

Is there any difference in how you wrote the sticks, perhaps? Persistent vs. non-persistent?

> 
The only thing I can tell you from my experience is that the problem on the Pangolin is probably in the software or a corrupted ISO image rather than the hardware. I have made good and bad sticks on the same hardware.

I am running a S76 panp4n, core 2 duo T5800, 3GB RAM, HD 320GB 5400 RPM, nVidia GeForce 9300M GS with Jaunty 64 bit/Hardy 32 bit/Jaunty 64 bit in a tri boot set up. The successful Jaunty and Karmic sticks were made on the Jaunty partition with a kernel 2.6.28-16 generic. I don't remember what kernel I had when I made the good Hardy. I think I was running Intrepid when I made the bad stick.

I hope you can get your troubles worked out soon.

Actually part of the reason that it's taking so long is that this is important but not urgent: I can probably survive a few more months without working it out, but it definitely does need to be worked out eventually.

---

### Post by Eldera on 2009-11-20
[quote=jwbrase]Is there any difference in how you wrote the sticks, perhaps? Persistent vs. non-persistent?[/quote]

I am not sure. I don't quite understand what the terms persistent vs. non-persistent mean when applied to writing USB sticks. 

In all cases I went to System>Administration>USB Startup Disk Creator (or whatever it was called in Intrepid.) Then I followed the prompts for using the tool.

For the Jaunty stick, I selected that when it is used, data would be saved to the stick. For the Karmic stick, I selected that data would be erased at the end of each session. They both booted equally well.

The only differences between writing the stick that wouldn't boot and the sticks that would, were that I had different versions of the OS on my computer and used different images. I thought perhaps there was an error in the Creator that was corrected in a later install of my OS, or there was an error in the ISO image from which I made the USB. (Perhaps the computer just hiccuped when I was making it.) I did not change any hardware or anything in the BIOS.

When I did the *bad* stick I had not yet learned how to use the md5sum check tool and did not check the iso image for errors. It could have been a corrupted image. I checked the ISO images from which I made the sticks that work and their md5sums were OK.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Off topic: I hope you are enjoying the University. My college days were some of the most exciting times of my life. Long, long ago, but good memories.

---

### Post by jwbrase on 2009-11-20
> **Eldera said:**
> I am not sure. I don't quite understand what the terms persistent vs. non-persistent mean when applied to writing USB sticks. 


You actually did a good job of explaining what persistent and non-persistent mean yourself, though you didn't know it:

> 
For the Jaunty stick, I selected that when it is used, data would be saved to the stick. For the Karmic stick, I selected that data would be erased at the end of each session. They both booted equally well.

---

### Post by jwbrase on 2009-11-21
On the other thread, somebody did mention the possibility of installing programs to /home instead of /. Does anybody know how that would be done (can Synaptic be configured to do that, for example?)

---

### Post by jwbrase on 2009-11-28
Well, I just got out today and bought myself a stack of CD-R's. Burned a live CD and am repartitioning (and posting) from it at the moment.

But, yeesh... Repartitioning a 320 gig drive takes *forever*. I'm estimating that I'm looking at eight to twelve hours to get it done (of which one or two have passed).

I'm a bit curious as to why the HD was partitioned as it was: 10 or 20 gigabytes would give about 70% to 140% more space in root, while only taking 4 to 8 percent out of home. That would have obviated the need to repartition in the first place. And I'm also wondering why sda's 5 and 6 are logical paritions. Assuming that different partition types take the same amount of time to work with (which may be a bad assumption, as I've not dealt with extended partitions before, so do correct me if I'm wrong), it's looking like about half of the time for this job will be consumed by manipulating sda2, whose existence doesn't really seem to me to be of much benefit (I thought extended and logical partitions were only necessary with more than 4 partitions on a drive...).

Other than the partitioning issue, though, I'm a very satisfied System76 customer.

---

### Post by jwbrase on 2009-11-28
Well. It's complete (Resizing the extended partition took a few seconds instead of the hours I had expected). I haven't yet rebooted the HD install, but from the looks of it all my data is intact. I'm a bit worried about the swap partition, though. Moving and resizing it took several tries, and even when I got it to work it said there were "4 warnings" (which I didn't really figure out how to check).

In any case, I don't think I've ever once used all of Ram on this thing, and I don't really use hibernate, so the swap file is probably moot.

---

### Post by jwbrase on 2009-11-28
I spoke to soon. The filesystem itself seems to be OK (the LiveCD can read it, as noted in my previous post), but grub has been borked. The machine does the POST, then I get a black screen with "GRUB" up in one corner, and nothing further happens. Will start a thread in General Help and link to it here.

EDIT: Link removed, problem solved


Well, Thanks everyone for all the help. I now have a working install with a bit more breathing room.

---

### Post by Eldera on 2009-11-28
I saw something in the Knowledge Base about Grub, but I'm not sure if it is what you need. This was something that was in there during Jaunty and before. I would try to check with thomasaaron before trying it with Karmic.

All I know is that they changed grub in Karmic. I have not tried to upgrade because I have not had the time to study the change.

[http://knowledge76.com/index.php/Restore_Grub](http://knowledge76.com/index.php/Restore_Grub)

---

### Post by Eldera on 2009-11-28
Great. You solved the problem while I was typing.

---

