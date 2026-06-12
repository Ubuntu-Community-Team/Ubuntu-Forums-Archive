---
title: "USB sticks, file systems, and my annoyances aired."
date: 2018-10-04
forum: Ubuntu, Linux and OS Chat
---

### Post by jerome1232 on 2018-10-04
Maybe I'm the only one but to this day it annoys me that there really isn't in my opinion a "good" choice when it comes to formating usb sticks.

If I use fat, I lose large file support and fancy new filesystem things. Oh and the ability to really fsck the drive. *To be fair I"m fairly sure fsck is pretty good with fat drives, I just got annoyed with mine when "disks", the default ubuntu disk tool, failed to remove the dirty bit on a fat drive and I said "YOU KNOW WHAT FINE, I"ll FREAKING REFORMAT YOU SINCE I JUST WANT TO PUT A FEW FILES ON YOU ANYWAYS". And So I did, to NTFS, then I was sure to press eject icon for fear of triggering that dirty bit again.

If I use NTFS, I end up with with a pretty good slew of fancy filesystem things, but it's not open source/linux native and I can't *really* fsck the drive, I know some stuff can work, but hey I just had a gui tool fail to remove the dirty bit from a fat drive, I doubt my NTFS experience will be any more smooth.

If I use EXT3, 4 or any other linux filesystem I know of, I run into permissions problems which doesn't really make sense with USB sticks.

I wish we had a native, permissionless (maybe some form of permission system is fine, but user ownership just doesn't work for portable media), file system specifically for portable media like usb keys.

Maybe there's something out there I don't know about, bot boy does this tiny thing annoy me.

---

### Post by i7Fd-2sCB1 on 2018-10-04
Would this help [https://ubuntuforums.org/showthread.php?t=2005281](https://ubuntuforums.org/showthread.php?t=2005281) ????

---

### Post by linuxyogi on 2018-10-04
I use Ext2 file system to make it compatible with OpenBSD and Linux. Never faced any problem.

---

### Post by poorguy on 2018-10-04
My USB drives I believe come formatted as ***"fat32"*** and I've never had any problems using ***"fat32"***.

I do have to say I have noticed certain brands of USB drives don't work well with Linux and have been problematic.


I use these and have no complaints. 
***[http://www.lexar.com/portfolio_page/jumpdrive-twistturn-usb-flash-drive/](http://www.lexar.com/portfolio_page/jumpdrive-twistturn-usb-flash-drive/)***

---

### Post by sudodus on 2018-10-04
Maybe the following links can help,

[How do I copy a file larger than 4GB to a USB flash drive?](https://askubuntu.com/questions/952673/how-do-i-copy-a-file-larger-than-4gb-to-a-usb-flash-drive/952706#952706)

[Can't format my usb drive. I have already tried with mkdosfs and gparted](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035)

[Installation/FromUSBStick - Postrequisites - restore the USB stick](https://help.ubuntu.com/community/Installation/FromUSBStick#Postrequisites_-_restore_the_USB_stick)

---

### Post by ajgreeny on 2018-10-04
In your first post you say "And So I did, to NTFS, then I was sure to press eject icon for fear of triggering that dirty bit again."

Can we assume from that, that you have not ALWAYS in the past made sure you have unmounted a USB stick before removing it?

If you have occasionally pulled out a USB stick without ejecting or unmounting it you could be causing this problem of which you speak, as I've had a few USB sticks for upwards of 10 years, all fat32, and in none of them have I ever had a problem due to a "dirty bit", whatever you mean by that.

Some of the utilities that are used to create USB boot disks, eg an installation USB for Ubuntu, made using mkusb, will make the USB unusable for normal purposes without it first being reformatted, or returned to default status, again easiest using mkusb.

Maybe you've been unlucky; maybe you have been just unplugging USBs without unmounting; certainly I do not have the problems you have seen.

---

### Post by jerome1232 on 2018-10-04
Firstly thanks for the support links, I purposefully posted in this section because I'm not specifically looking for support. Just chatting about an annoyance.

> **ajgreeny said:**
> In your first post you say "And So I did, to NTFS, then I was sure to press eject icon for fear of triggering that dirty bit again."

Can we assume from that, that you have not ALWAYS in the past made sure you have unmounted a USB stick before removing it?



Yes you can assume that I have done that, My sister-in-law was done using the stick and pulled it out and handed it to me so I can use it. Because that's what tons of users do. It's extremely typical user behavior that doesn't seem to be accounted for. If I do at in Ubuntu, I end up with a confused user wondering why their usb key is read only now with no immediately apparent way to change it. 

I do remember fat devices having their dirty bit automatically reset for some reason in the past when being mounted, maybe not though. 


I recall that there's a way to mount filesystems so that their writes aren't cached, If my recollection is correct wouldn't it just make sense to make that a default for things that are known to be removable media? No one wants the OS to pretend it's done writing data to a usb key they are anxiously waiting to rip out.


I find it hard to believe anyone has used a linux filesystem on a usb key, copied things to a usb key, went to the next computer, tried to copy more things only to realize now they have to bounce into a command line to modify permissions because the user on this system has a different uuid. That is confusing for your typical user, It just seems like a native linux filesystem that is permissionless would be a useful thing specifically for portable media.

---

### Post by rainintheface on 2018-10-04
Strangely, I have found that if I have a USB stick that is misbehaving it helps to stick it in a Windows machine and reformat it to Fat 32 and usually it works fine after that, even with Linux. Windows format tools just seem to work reliably.

---

### Post by ajgreeny on 2018-10-04
> **jerome1232 said:**
> Firstly thanks for the support links, I purposefully posted in this section because I'm not specifically looking for support. Just chatting about an annoyance.



Yes you can assume that I have done that, My sister-in-law was done using the stick and pulled it out and handed it to me so I can use it. Because that's what tons of users do. It's extremely typical user behavior that doesn't seem to be accounted for. If I do at in Ubuntu, I end up with a confused user wondering why their usb key is read only now with no immediately apparent way to change it. 

This, I am pretty certain is why you have been seeing the problem of dirty USB sticks not working as they should.

**It is essential that you unmount all USB disks before unplugging** or filesystem corruption is almost certain to happen at some point, maybe not every time, but it will happen sometime or other so learn not to do it.

---

### Post by jerome1232 on 2018-10-04
You know what, I decided to mess around with it, here I am with my thumb drive formatted NTFS, I'm writing files to it, letting them finish. Then ripping it out sans eject button on sticking it back in like a maniac and it's working just fine.

Once the written file was no longer there (I assume it never got written and it was still cached) which is something I can expect to happen. But not once did it mount read only like I got with the fat32. Maybe I did just get the unlucky pull. Maybe she was in the middle of still writing stuff to it when she pulled it lol who knows. The behavior I'm seeing right now is what I'd expect.

---

### Post by jerome1232 on 2018-10-04
Annnnnnd it's working normally with fat32 too, with ripping it out sans eject button, I have to conclude she was actually mid write when it was pulled out or something haha.

---

### Post by ajgreeny on 2018-10-06
OK, but be warned, if you pull out USB sticks before unmounting, **YOU WILL LOSE DATA**; sooner or later it **WILL** happen!

Is it worth the risk for a couple of clicks?
Incidentally this is the same in Windows or Mac systems, not just Linux.

In your post #7 you say
> Yes you can assume that I have done that, My sister-in-law was done using the stick and pulled it out and handed it to me so I can use it. Because that's what tons of users do. **It's extremely typical user behavior that doesn't seem to be accounted for.** If I do at in Ubuntu, I end up with a confused user wondering why their usb key is read only now with no immediately apparent way to change it. 
It may be typical behaviour for you and others but that does not make it correct, as this is simply a property of USB drives; the only way to avoid loss or corruption of data is to ensure they are unmounted or ejected, either will do, before unplugging.

---

### Post by jerome1232 on 2018-10-10
> **ajgreeny said:**
> OK, but be warned, if you pull out USB sticks before unmounting, **YOU WILL LOSE DATA**; sooner or later it **WILL** happen!

Is it worth the risk for a couple of clicks?
Incidentally this is the same in Windows or Mac systems, not just Linux.

In your post #7 you say

It may be typical behaviour for you and others but that does not make it correct, as this is simply a property of USB drives; the only way to avoid loss or corruption of data is to ensure they are unmounted or ejected, either will do, before unplugging.

Well, no. No it's not actually. These days Windows by default disables write caching for usb devices. Which is a sane default. I highly doubt the performance benefit of write caching is significant in any of the ways that people typically use usb drives. You know why it does that? Because no amount of preaching "safely remove" will get people to actually do it. So it's best to just make it not an issue, to avoid people's precious data evaporating into thin air and damaged file systems.

You keep zeroing in on "it's not smart to just rip out usb devices" when what I'm saying is "It shouldn't be an issue, write caching should be off for removable media because users be stupid, and there's little benefit to having it on anyways". I hope that clarifies what I am trying to say.

---

