---
title: "PanP7 USB 2.0 Performance Lags / A little help, please?"
date: 2010-08-09
forum: System76 Support
---

### Post by IAmWhatWasDavidBowman on 2010-08-09
[COLOR="Blue"]**[SIZE="2"]This issue has been resolved for me by using kernel version 3.0+![/SIZE]**[/COLOR]



Greetings all! I've owned my PanP7 for a couple weeks now, and I'm absolutely in love with it. Honestly, I'm really glad that I went for the custom built laptop instead of trying (and failing) to get a Windows Tax refund from some other manufacturer.

I'm wondering if any other System76 users are experiencing this problem. I feel like I can't be the only System76 user to have experienced this problem, but I'm not blaming the company by any means.

On the PanP7, I'm running the 64-bit version of Lucid, and one thing that I've run into is that USB 2.0 performance can be quite laggy when transferring large files to an external drive (this has been documented many, many times across various linux distros since at least 2007, so I'll skip the reference links here - search linux USB 2.0 slow and you'll get thousands of hits). Transfers begin quickly, but then bottom out after a few hundred megabytes  - eventually lagging somewhere in the area of 1 Mbps (regardless of file system type, and I've tested between FAT32, NTFS, and ext2 with the same results). For me, this happens between different USB thumb drives and an external hard drive, none of which experience this problem on my desktop nor under Windows. eSata works very quickly on the PanP7 for the external hard drive under Lucid.

Now before I asked for assistance here, I did do some research into this matter. Some forum posts suggested adding an **"evelator=[X]"** to the end of the kernel string in grub (see: [http://ubuntuforums.org/showthread.php?p=8124833#post8124833]("http://ubuntuforums.org/showthread.php?p=8124833#post8124833")). Some people reported success with this method, others not so much.

Others suggested (and I'm more convinced of this) that the underlying cause is the ehci_hcd module, and this can be fixed by unloading it and then reloading with

```
sudo modprobe -r ehci_hcd
sudo modprobe ehci_hcd
```

My questions to the System76 community would be then:
[LIST]
[*]Has anyone else experienced this problem?
[*]What do you do to correct it?
[/LIST]

Trying the above command to unload the module, the command line returns: "FATAL: Module ehci_hcd is builtin" since in the newest Ubuntu kernels this module is not separate any longer!

From what I've read, I do think this is related to Intel chipsets. I already attempted to disable Legacy USB support in the BIOS and it rendered the same results.

So yeah. I'm pretty stumped. Any and all help would be appreciated! I can post any error logs or whatnot that would be helpful. Please just let me know how to get that info.

[Update] I may try to compile a new kernel with the Anticipatory I/O Scheduling instead of CFQ, like the above linked post spoke about. Does anyone have any input or advice on this for the PanP7? I'm currently backing up my system partition with Clonezilla and I might try this. The only thing that makes me pause is that the above post is an old post and I'm not sure if it would even do me any good.

Does anyone know of how I might test the "elevator=" method above? I do not have a /boot/grub/menu.lst.

[Update 2] I did more reading and found out about the changes to GRUB2. So I held down the shift key and got to the grub menu, manually added the evelator=as to enable Anticipatory I/O Scheduling and then booted to Lucid. ...And the change did nothing.

So I'm guessing that either this did not work, or this is not the cause of the problem.

I'm STILL STUCK! ARRRRRRG!!

Thank you in advance!

---

### Post by thomasaaron on 2010-08-10
Actually, that might be the first time anyone has ever mentioned that on our forums. I hadn't even heard of it.

We can try to work in some tests around here, but my advice would be to participate in the bugs that have already been filed on it, as the problem is going to end up having to be formally solved by upstream developers.

---

### Post by IAmWhatWasDavidBowman on 2010-08-10
Thomas,

Thanks for the reply. Nobody, huh? Ha ha! That is my usual luck. I flubbed my original installation of Lucidtrying to resize the sysem drive so that I could create a separate /home partition (the install that shipped from you guys). So I reinstalled Lucid following the directions on your Knowledge Base, and all seems well - just not the USB. I didn't have the laptop long enough to know if this problem was there before that happened.

Does System76 use the stock Ubuntu kernel? I'm assuming you do. Is there anything you can think of that may have changed between the factory install and my reinstallation?

I'm absolutely not placing any blame on your company. I'm just trying to take all factors into account if I'm the only one that this has happened to.

Oh, and I have already started participating in the bug reports. They're so many related to this though, and many if them have been ongoing for years.

I'm going to download some live cd's of other distros and see how those do.

---

### Post by thomasaaron on 2010-08-10
Yes, we basically use a stock installation, plus our System76 Driver.

We definitely don't do anything that would effect USB speed. So, it's got to be something with the driver module loaded by Ubuntu.

I'll do a little poking around online and see if I can come up with any ideas.

---

### Post by IAmWhatWasDavidBowman on 2010-08-10
Thank you again. I'll also report back if I have any updates.

---

### Post by IAmWhatWasDavidBowman on 2010-08-11
Okay, so after some halfway-extensive testing, I've got the following bits of info to add to this:

[LIST]
[*] The 32-bit version of Lucid doesn't demonstate this problem, either through a live cd environment or installed to the internal hard drive. Speed stays consistent, but does not seem to exceed 12 Mbps.
[*] Puppy Linux 4.3.1 doesn't seem to demonstrate this problem, though because of the lack of a progress bar for the copy operation, I can't give exact speeds. I would guess that it is operating at 12 Mbps like the 32-bit version of Lucid as it seemed to take about the same amount of time to transfer a large file.
[*]Fedora 13 64-bit (live cd) demonstrates this problem
[*]A live cd for 64-bit Lucid  bit also demonstrates this problem
[*]Linux Mint 9 64-bit live cd also had this problem
[*]Lucid Puppy 5.0.1 live cd did not have this problem, though I think this is a 32-bit distro, and was as fast as the live Windows cd
[*]A live Windows cd does not demonstrate this problem.
[/LIST]

I'm going to try to fill out all of the bug reports with more thorough information regarding this problem. I agree with you that it looks like something that will have to be fixed with upstream developers.

---

### Post by IAmWhatWasDavidBowman on 2010-08-12
Thomas,

I've been working with submitting but reports to Launchpad, and I will soon try to send them to the main kernel developers too.

I tried the latest mainline kernel, and it still gave me the same problem.

I've tried and seen this problem reproduced using a Kingston DataTraveler (4GB) USB thumbdrive, the (admittedly bad class) microSD card in my Motorola Droid, and my external hard drive. I then tested them against a Window PC, and I did not seem to see the same problems. I thought of buying another thumbdrive, but really I have no use for another at the moment.

I've PM'd several members of this forum that said they own a PanP7. Some have said they've seen similar issues, and some not.

I'm trying to determine what the root of the issue is. I'm almost 100% sure it's not hardware. It sounds like it's software, but I'm not sure what I would have setup differently then the other owners that are not having this problem.

So I was wondering something: could someone at System76 see if they experience anything like this on a PanP7 in the office, and if not, is there a way to get an image made of that partition (like Clonezilla maybe) and make that available to me so that I can apply it on my own machine to see if there's a difference?

Thank you!

---

### Post by thomasaaron on 2010-08-12
IAmWhatWasDavidBowman,

Good news: We'll absolutely do that for you.

Bad news: Our PanP7 is out of the shop until Monday or Tuesday. Please bump this thread then, and we'll get it done.

Thanks for helping with this one.

---

### Post by IAmWhatWasDavidBowman on 2010-08-12
Thomas,

That *is* good news. Thank you for that. I really love this machine so far, but I'm one of those dreaded *perfectionists*, so I want everything running 100%.

No need to thank me, I'm just trying to give back a little to the community. This is why I switched to linux full time in the first place.

I'll be sure to bump the thread early next week.

As always, your help is appreciated,

Dave

---

### Post by jmlapeyre on 2010-08-15
Hi all, I do confirm what IAmWhatWasDavidBowman observed.

I have a PanP wich runs (still) karmic 64bits and IAmWhatWasDavidBowman contacted me to see if I could experience the same issue. I have to admit that I really never looked at this as all my big file transfers are performed using eSata (on a server in my basement)...

So I just took a little bit of time to run a few tests with my current config and a  couple of thumb-drives. Took a folder with a few files of very different  sizes (biggest being 2.1G) and yes, the transfer seems very slow (seems  to stall for some time roughly every 120ish MB - not 128 ). Very same behavior for all drives (I used a SanDisk and a Kingston just to be sure it was not a bad flash drive)...

:sad:

---

### Post by IAmWhatWasDavidBowman on 2010-08-17
Thomas,

I'm bumping the thread as you requested. I'd really appreciate your help.

Thank you again,
Dave

---

