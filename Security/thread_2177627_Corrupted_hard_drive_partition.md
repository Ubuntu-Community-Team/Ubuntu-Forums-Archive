---
title: "Corrupted hard drive partition?"
date: 2013-09-29
forum: Security
---

### Post by pooch2 on 2013-09-29
Hello everybody,
      I'm a relativly new ubuntu user, so I'm not super familiar with the operating system yet. Recently my internet speeds plunged to (on average) 176 b per second. This started happening after an unmountable, unejectable device showed up. I know the problem is my laptop because my roommate's computer can access the internet just fine. Any advice?

---

### Post by Dreamer Fithp Apprentice on 2013-09-29
1. You haven't given any reason you suspect a virus. Unless there is something to make you think that is the case, it is quite unlikely.

2. 176 mb/sec really isn't all that slow.

3. What is the "unmountable, unejectable device"? Does it have a name? How exactly did it "show up"?

What is the nature of your hardware? Exactly what OS are you running? Ubuntu? Xbuntu? Lubuntu? Precise? Raring? What?

You need to give details if anyone is to have any chance of helping you.

---

### Post by pooch2 on 2013-09-30
Alright sorry about that:
1.) My internet speed is 176 BYTES/sec (0.176 kB/sec)
2.) The drive/device is called h0@2
3.) I am running ubuntu 12.04 precise pangolin
4.) One day I turned my computer on, logged in, and opened my home folder and the drive wasd there, and my internet was super slow
5.) When I attempt to eject and/or mount the device it spits out an error message saying:
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
6.) I don't know for sure its actually a virus
7.) I can upload things on to the net just fine, its seems to be just my download speed that is lacking.

---

### Post by Nil_Pointer on 2013-10-01
Can't think of reason for problems with internet connection.

However, for this:

> **pooch2 said:**
> Alright sorry about that:
2.) The drive/device is called h0@2
5.) When I attempt to eject and/or mount the device it spits out an error message saying:
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

It looks like you have a corrupted hard drive partition on sda5. You can open Disk Utility and locate this partition on sda hard drive. Also you can check S.M.A.R.T. data for your hard disk in Disk Utility for bad blocks.

---

### Post by Dreamer Fithp Apprentice on 2013-10-06
-1 to me. Mea culpa for thinking mb when you clearly wrote b. Guess I was seeing what I expected to see.

+1 to Nil_Pointer. I concur. That sounds like a corrupt filesystem. You don't say anything about your hardware. If you are at all unsure which drive is sda it would be a real good idea to find out before you do anything drastic. If you only have one drive with 5 or more partitions, obviously that's the one. I believe sda will usually refer to the first drive the bios looks at to find some kind of bootloader, after looking at removable optical media and floppies and NOT counting usb external hard drives, even if you are booting from them. Note that this is not the same as saying the drive you boot from. You could, for instance, have two internal hds, one of which is bootable and the other of which is plain data but the bios might still LOOK to see IF the data drive is bootable BEFORE looking at the other. Take this with a grain, nay, make that a gram, of salt. I may have some of the details wrong and even if I'm absolutely right (which, OF COURSE, is normally the case,lol) there probably is some variation between bioss (biosae? biosi? Anyway between 1 bios and another). If you have an internal hard drive that is likely sda. But if you have more than one internal and you aren't sure which is which you'll need to take steps to become sure. Even if you have only one internal I'd still be real careful if you have ANY other media on the machine that can be written to to make SURE you know which is which before you do anything. For all I know maybe your bios is calling an external hd sda for instance, although I think it slightly unlikely. Depending on how you boot, figuring this out may be as simple as unplugging all the writable drives and plugging them back in one at a time. Be aware that the "sdX" nomenclature can  change as you plug in different configurations. For instance, if you had a 1 Tb seagate internal called sda and a 200 gb internal called sdb and you reversed the cables connecting them to their controller (usually on the motherboard nowadays)you'd probably find that which one was called sda would also be reversed. Or you may be able to tell using gparted, if you know how your devices are partitioned. OK, you get the idea. But if you aren't clear on which drive is sda, I'd seek clarification before doing anything.

As for what to do about it, maybe Disk Utility can fix it for you. I don't know. I don't have it installed and I've forgotten what it is like in detail. You may find fsck can fix it for you. If so, there is some chance of some data loss. If there is anything extraordinarily important on there that isn't backed up I'd be spending a while researching recovery software before I did anything with it. But if you're properly backed up, you can fsck it and it will probably fix it. You might lose a file or two. Or you can reformat it.

Exactly WHAT called the device h0@2? A file browser? And where did it call it that? In the side pane like a bookmark? In some folder, like /dev/ or /media/? Can you  click on it and take a properties? In either case I don't know what to make of it, though it will probably mean something to somebody here. You might try googling "h0@2". Try code search if regular gives you too much irrelevant stuff that doesn't contain an @. Google is a jackass about odd characters, even in the exact phrase field or surrounded by "s. It doesn't sound like an alternate name for sda5 to me.

I also can't think of a simple fix for the slow download speed. It could be physical damage to your hardware. But before I assumed that, I'd try reinstalling if nobody comes up with a better idea. Have you changed anything about how you hook up the net? Through a wireless router and internal wireless maybe?  Or do you have to plug something in to some port on the computer? Did you recently enable encryption on the connection or change the security level of the encryption? Really heavy encryption would slow it down, although I'd be surprised if it slowed it down THAT much unless it was a real antique like a Sinclaire or a TRS-80.

---

