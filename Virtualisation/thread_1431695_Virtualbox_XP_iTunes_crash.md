---
title: "Virtualbox XP iTunes crash"
date: 2010-03-16
forum: Virtualisation
---

### Post by jdc158 on 2010-03-16
iTunes crashes as soon as it fully loads. I get this error report.

[IMG]http://i848.photobucket.com/albums/ab50/jdc1588/Screenshot-2.png[/IMG]

I'm pretty sure this is because my XP is pirated. Is there a way around this? Or do I just need a legit copy of XP?

---

### Post by Jeff Anthony on 2010-03-17
way to kill any chance of getting help

---

### Post by Carroarmato0 on 2010-04-05
dear jdc158, first of all I do not incurrage the usage of pirated software.

Now that that's behind the back, no, it's not because of the pirated version of Windows XP, you are not alone in having the recent version of iTunes crashing every time in Virtual Box.

From what I have found, people are guessing it might have something to do with the VT-x/AMD-v CPU Virtualiztion option in VirtualBox, and obviously iTunes being a retarded peace of software, always trying to change any files it likes in order to ruin your life.

Suggestion is to downgrade iTunes to a known working version number. I'm currently in the process of finding out for myself which older version is working. (going to try 9.0.3, seeing as the current version is 9.3.15 which is having the problem)

---

### Post by gpaciga on 2010-04-28
Any progress on finding a working version? Or a workaround? Mine is doing this too (with a legit copy of Windows XP SP2, by the way). I downloaded 9.1.1 from the apple website.

---

### Post by MMSpeer on 2010-04-30
> **gpaciga said:**
> Any progress on finding a working version? Or a workaround? Mine is doing this too (with a legit copy of Windows XP SP2, by the way). I downloaded 9.1.1 from the apple website.

Had exactly the same problem. Tried several versions, version 9.0.2. seems to work fine. Not ideal, better than nothing. Hope finally we can use the most recent versions soon. Or better, a Linux version of Itunes.

---

### Post by jepong on 2010-05-01
i have the same problem and version 9.0.2 does the trick... i tried to install version 9.1 on a virtualbox for windows and it works. just wondering how.

---

### Post by Ginsu543 on 2010-05-03
I too had to go back to 9.0.2.25 to have it working again. Before my migration to Lucid, I had 9.0.3 working for a while, but it started crashing again. The only thing that has sucked is restoring all my music and videos to my 30GB iPhone after syncing it to a different version of iTunes. I love my iPhone, but, egads, I hate iTunes! Why can't Apple just make it so that I can drag/drop files onto my iPhone like a usb flash drive?

---

### Post by EnlistedSquire on 2010-06-08
I've been happy enough not upgrading my iTunes since they started crashing in VBox, but I've just read that upgrading to iOS4 will require iTunes 9.2.

Nowhere can I even find clarification as to whether this is a bug with VBox or iTunes - is anyone working on it?

I don't really want to have to install Windows just to upgrade my iPhone.

---

### Post by jepong on 2010-06-08
hope OS update is possible over the air soon

---

### Post by sammyjayuk on 2010-06-09
> **EnlistedSquire said:**
> Nowhere can I even find clarification as to whether this is a bug with VBox or iTunes ...

I've seen a report that iTunes 9.1+ will work in VirtualBox 3.1.x, but I haven't tried that yet.

What I have tried is VMware Player--the same VM, exported from VBox and imported into Player--after seeing someone say it works, and I don't seem to get the crash there, although I'm sure I've seen at least one person saying they *do* get the crash. So, conflicting reports.

All I know is that with VBox I can't even play an entire song without iTunes crashing whereas I can in Player.

VMware Player is useless for my purposes though. Not only does it feel a fair bit slower, it's unusable on an 800x480 display--it seems to have a fixed minimum window size that appears to be substantially bigger than 640x480 but less than 800x600, and it won't even go fullscreen, even after telling maximus to ignore it!

Anyway, my own experience (above) and everything I've read seems to suggest that the problem is VirtualBox's virtualisation on systems where it can't use VT-x/AMD-v--as in those that either lack CPU assisted virtualisation extensions or have them disabled and locked by the firmware (whether that's EFI or a BIOS).

My problem is that the little 1.33 GHz Atom N520 computer I'm using has an EFI firmware and lacks even BIOS emulation, and is being used in a way that's so far from what the device is actually sold for that there's zero hope of the retailer or the manufacturer ever being of any assistance whatsoever!

So I'm off to see whether a VBox 3.2.x VM will run under 3.1.x! Wish me luck...

Sam

---

### Post by rmp73 on 2010-06-22
How come this thread is marked as [Solved]?  The issue is that upgrading to iOS4 will require iTunes 9.2 and so those of us that want to upgrade have to either install Windows side by side on our machines (less than ideal) or ditch Linux, which isn't an option either - I'm loving Ubuntu 10.04.

---

### Post by EnlistedSquire on 2010-06-22
I've switched to VMware Player to resolve this. I'm actually very pleased I did. Performance is much better and although I've lost some advanced features like snapshots, one of the coolest things I can do is actually put a launcher for iTunes on my desktop/dock/panel/wherever and it will fire up the VM and then launch iTunes in Unity mode (think seamless mode in VBox).

---

### Post by h3n5y on 2010-06-23
> **rmp73 said:**
> How come this thread is marked as [Solved]?  The issue is that upgrading to iOS4 will require iTunes 9.2 and so those of us that want to upgrade have to either install Windows side by side on our machines (less than ideal) or ditch Linux, which isn't an option either - I'm loving Ubuntu 10.04.

Couldn't agree more with you, rmp. Just ran into the same issue that 9.2 crashes immediately on VBox 3.1.6 running XP SP3 on Lucid host, AMD CPU. If I turn on EFI (as mentioned elsewhere), XP doesn't boot at all, so no help there...



Of course we don't want to ditch Linux because some stupid Apple software doesn't work correctly. Nevertheless, I'd like to update to iOS4, too! 

Who can remove the [solved] tag here?

Cheers,
h.

---

### Post by TheBurner on 2010-06-23
Im experiencing the same problem with itunes 9.2 and as the others i need to upgrade in order to update my iphone os to ios4. Any progress on this?

---

### Post by revolverXD on 2010-06-23
try VMplayer itunes 9.2 works and there is no complications with your usb

---

### Post by jshombre on 2010-06-23
> **sammyjayuk said:**
> Anyway, my own experience (above) and everything I've read seems to suggest that the problem is VirtualBox's virtualisation on systems where it can't use VT-x/AMD-v--as in those that either lack CPU assisted virtualisation extensions or have them disabled and locked by the firmware (whether that's EFI or a BIOS).


I can confirm this, at least on my equipment. Without activating the processor's virtualisation extensions, iTunes 9.2 would just crash straight away when running in XP on Virtualbox 3.2.4. (I hadn't actually noticed that the extensions were turned off in the BIOS and had been blithely using VB regardless).

Having turned them on, iTunes works fine so far.

Joe.

---

### Post by arak on 2010-06-23
Same problem. I WANT TO USE LINUX/VIRTUALBOX/XP.   PLEASE, PLEASE, someone find a solution.

---

### Post by fromthehill on 2010-06-23
I'm running virtualbox and the same happens to me when running itunes 9.2 

I've tested it with virtual machines running windows xp, vista and windows 7. all having the same problem

an older version of itunes worked for me, but it doesn;t support OS4.0

I have an laptop with a core2duo T6400 which doesn't support virtualisation technology

---

### Post by TheBurner on 2010-06-23
Well this has been going on ever since 9.0.2 was updated so 4+ months at least . Hopefully someone can fix its rather annoying.

---

### Post by rduplain on 2010-06-24
> **jshombre said:**
> iTunes 9.2 would just crash straight away when running in XP on Virtualbox 3.2.4.

I had the same issue.  I enabled VT-x/AMD-V in VirtualBox and iTunes worked.  I don't have EFI enabled.

The issue: attempting to launch iTunes in a Windows XP guest would immediately crash with an error of 'The memory could not be "read"'.

Setup: iTunes 9.2.0.61 on Windows XP Pro SP3 via VirtualBox 3.2.4 r62467 on Ubuntu 10.04 Lucid on Asus UL30A.

-Ron

---

### Post by fromthehill on 2010-06-24
> **rduplain said:**
> I had the same issue.  I enabled VT-x/AMD-V in VirtualBox and iTunes worked.  I don't have EFI enabled.

so in a virtual machine itunes will only work when VT is enabled
while on a native windows desktop it doesn't matter if the system has VT or not.

the same problem occurs when running vista or windows 7
vmware also seems to have the same problem

I'd almost think apple did this on purpose

---

### Post by arak on 2010-06-24
> **TheBurner said:**
> Well this has been going on ever since 9.0.2 was updated so 4+ months at least . Hopefully someone can fix its rather annoying.
Please, please tell us how you enable "VT-x/AMD-V in VirtualBox."  What do you click? Where do you find the place to click.
 
I'M A NEWBEE

---

### Post by TheBurner on 2010-06-24
I believe it depends if your mobo supports it on my virtualbox it is clicked but greyed out. I have no option to enable virtualization in bios.

---

### Post by w8ryanb on 2010-06-25
Took me a while to make it work... until I found this forum. Itunes worked on my desktop AMD X2 but did not work in my wife's laptop (AMD as well). Turning virtualization on in the Bios made all the difference... now I can sink my Iphone4 ;)

---

### Post by fromthehill on 2010-06-25
why is this solved
it still doesn't work with the following processors

**_Desktop CPUS_**
**Core 2 Duo **	 
E4300/4400/4500/4600/4700 
E7200/7300/7400/7500 
E8190

**Core 2 Quad **
Q8200/8200S/8300/8400/8400S 	

**Pentium D/Pentium EE 	** 
805/820/830/840 	
915/925/935/945 

**Pentium for Desktop **	 
E2140/2160/2180/2200/2220
E5200/5300/5400

**_Mobile CPU products_**
**Core 2 Duo Mobile **	
P7350/7450 	
T5200/5250/5270/5300/5450/5470 	
T5550/5670/5750/5800/5850/5870/5900 	
T6400/6570 	

**Core 2 Quad Mobile **
Q9100 	

**Core Duo **	 
T2050/2250 
T2300E/2350/2450

**Core Solo** 
T1350

---

### Post by sryzr on 2010-06-26
I have enabled that, and it still doesnt work for me

---

### Post by VinoFuriaRoja on 2010-06-27
This may sound like a dumb question, but how do you enable virtualization in the bios?

---

### Post by dhawkins on 2010-06-27
I have found the same issues: I couldn't get iTunes 9.2 (running on a Windows XP guest; VirtualBox 3.2.6 host on Ubuntu Karmic) - It would come up with a Windows crash box as iTunes was starting up.

I enabled Virtualisation etc on my PCs BIOS (after updating the BIOS) and enabled the AMD-V setting in VirtualBox for my virtual windows machine. However when looking at the run-time Virtualbox status of the machine - it showed that the AMD-V feature was disabled. I checked the VirtualBox log (VBox.log) to find that it was saying this:

*No VT-x or AMD-V CPU extension found. Reason VERR_SVM_IN_USE*

So I found this: [http://www.virtualbox.org/ticket/5639](http://www.virtualbox.org/ticket/5639)

And as a result set the environment variable before running VirtualBox:

[I]export VBOX_HWVIRTEX_IGNORE_SVM_IN_USE=true
[/I]
Now iTunes doe not crash and the run-time Virtualbox status of the machine indicates that AMD-V is enabled.

Hope that helps

---

### Post by lex0429 on 2010-06-30
Upgrading BIOS on Sony VGN-TT190 to enable the option to turn on Intel virtualization technology and then enabling that worked for me. Thank you very much!!!

---

### Post by JEDIDIAH on 2010-07-01
It may just be time to ditch XP. It's 2 versions back so that probably means that it will be de-supported soon. I initially tried to run iTunes with Win2K when I was first starting with this VM stuff and had similar trouble.

It may be time to move to Vista or Win7 if you are not willing to stay on an older version of iTunes. I've got iTunes 9.2 running just fine in my 64-bit Win7 VM. I just used the defaults for creating a VM in VirtualBox. I didn't go out of my way to configure the VM with iTunes in mind.

---

### Post by CarbineReloaded on 2010-07-05
For what it's worth....

I have 2 computers running Ubuntu.... one with an AMD Turion 64x2 Processor and another with an Intel Centrino Duo Processor.

My primary box is the AMD - Updated iTunes and started having the crashing problem.  I do NOT have the options in my bios to enable Virtualization on this box.

I transfered my XP virt hard disk to my Intel based laptop and installed virtualbox.  It launched right away and iTunes works 100% on that laptop.  Prior to the transfer, I did enable Virtualization in the bios.  


Unfortunately the Intel based laptop is my travel laptop where the AMD box is more of my "home desktop replacment"  I'm not thrilled that I have to use the intel box to work on my ipod.... but it's better then nothing.

---

### Post by guren on 2010-07-18
> **rduplain said:**
> I had the same issue.  I enabled VT-x/AMD-V in VirtualBox and iTunes worked.  I don't have EFI enabled.


This solution worked for me as well.. Thanks! :D

---

### Post by irfanahmed on 2010-07-20
I was having the same problem. 
I have a Dell XPS 1530, Core 2 Duo, 4GB RAM, running Ubuntu 10.04 64.
I use VirtualBox 3.2.6 and have installed Windows 7 Professional.

I had enabled the VT-x/AMD-V setting in the VBox and hence assumed it to be enabled. However I had not enabled virtualization in the BIOS. Once I enabled Virtualization in the BIOS, iTunes 9.2 is now working fine.

I have successfully ugraded my iPhone OS to iOS4.0.1

---

### Post by vipseixas on 2010-07-28
My notebook processor does not have virtualization capabilities (it is an Intel without VT-X). The only solution for me was to convert the VirtualBox VDI disk to an VMWare VMDK disk and install the VMWare Player 3 (it's free). 

VMWare Player does not have an option to create a new VM using an existing disk, but you can add an existing disk just after you create it with an dummy disk (and of course remove the dummy disk).

It seems that the problem only occurs inside VB, now I can use iTunes again.

If anyone is interested in converting VirtualBox disks:

```

VBoxManage clonehd /path/to/disk/disk.vdi /path/to/disk/disk.vmdk --format VMDK --variant Split2G

```

---

### Post by ThomWilhelm on 2010-08-04
As the poster above mentioned, this seems to be a problem that affects non-virtualisation enabled processors on VirtualBox. I have an Intel T5550 processor on my laptop, had this exact same problem with both Windows XP and Windows Vista on VirtualBox.

Rather than copying the disk, I just installed a clean copy of Windows XP on WMware player 3, and I have now synced my iPhone 4 successfully and have no problems with itunes.

Bit of a time consuming workaround but at least I can now use itunes!

---

### Post by scot.mcpherson on 2010-08-08
Just reporting that with my Dell XPS 710, that enabling virtualization in the BIOS solved the problem. Virtual Box already had VT-x checked. Upgraded iTunes to the current version successfully and it runs just fine, including syncing, backing up and restoring my iPhone.

Still need a native Windows machine to complete the iPhone upgrades though. It updates just fine, but can't handle an iPhone in restore mode from an upgrade.

---

### Post by Ginsu543 on 2010-08-08
> **scot.mcpherson said:**
> 
Still need a native Windows machine to complete the iPhone upgrades though. It updates just fine, but can't handle an iPhone in restore mode from an upgrade.

I personally have been able to upgrade my iPhone 3GS from iOS 3.1.3 to iOS 4.0.1 using iTunes 9.2.1 inside my Windows XP guest on VirtualBox 3.2.8. The only glitch was that VirtualBox (and therefore Windows) kept losing the USB connection, so I had to nurse it through by clicking on Apple mobile device in the Devices --> USB Devices menu whenever it lost connection. But I have been able to successfully upgrade my iPhone twice, 3.1.3 --> 4.0 and 4.0 --> 4.0.1.

---

### Post by Carroarmato0 on 2010-08-11
> **Ginsu543 said:**
> The only glitch was that VirtualBox (and therefore Windows) kept losing the USB connection, so I had to nurse it through by clicking on Apple mobile device in the Devices --> USB Devices menu whenever it lost connection. But I have been able to successfully upgrade my iPhone twice, 3.1.3 --> 4.0 and 4.0 --> 4.0.1.

Actually, that's not a glitch as VirtualBox is doing what it's supposed to do.
If you take a careful look, you'll see that during the firmware update process, the Ipod/Iphone exposes different Usb driver signatures. To VirtualBox, it simply looks like you're plugin in different usb devices.

In order to avoid this future annoyance (which is Apple's doing in the first place), you simply need to make a new usb device filter in VirtualBox with just the common signatures used in Ipod/Iphone drivers (for example: Vendor: Apple,  something like that)

---

### Post by raistlin_kell on 2010-08-14
I'm using an old HP Compaq NC6220 laptop with 2.5g of Ram. Have upgraded Vbox to 3.2.8 r64453. Am running a (licensed) copy of XP with SP3 and MS Security Essentials with  not much else... except iTunes 9.02. 

The laptop doesn't have any visualization extensions in the BIOS. Its nearly 5 years old but does everything I want with Lucid... except drive iTunes 9.2.x for iOS4.

Q - is it possible to buy Snow Leopard installation (not upgrade) from Apple? I'd prefer running OSX in a Virtual Box rather than Windoze anything. I suspect if this was possible, iTunes wouldn't be a problem however haven't been able to find any sites willing/able to sell me a license of Snow Leopard.

Maybe I upgrade the old laptop with a iMac Laptop?

---

### Post by Ginsu543 on 2010-08-15
> **Carroarmato0 said:**
> Actually, that's not a glitch as VirtualBox is doing what it's supposed to do.
If you take a careful look, you'll see that during the firmware update process, the Ipod/Iphone exposes different Usb driver signatures. To VirtualBox, it simply looks like you're plugin in different usb devices.

In order to avoid this future annoyance (which is Apple's doing in the first place), you simply need to make a new usb device filter in VirtualBox with just the common signatures used in Ipod/Iphone drivers (for example: Vendor: Apple,  something like that)
Good to know. Thanks!

---

### Post by Ginsu543 on 2010-08-15
> **raistlin_kell said:**
> 
The laptop doesn't have any visualization extensions in the BIOS. Its nearly 5 years old but does everything I want with Lucid... except drive iTunes 9.2.x for iOS4.

You might want to check out VMware. I personally don't have any experience with VMware (VirtualBox does everything I need it tio do), but I've heard that VMware does not require virtualization extensions to run iTunes.

---

### Post by vipseixas on 2010-08-15
> **raistlin_kell said:**
> 
Q - is it possible to buy Snow Leopard installation (not upgrade) from Apple? I'd prefer running OSX in a Virtual Box rather than Windoze anything. I suspect if this was possible, iTunes wouldn't be a problem however haven't been able to find any sites willing/able to sell me a license of Snow Leopard.


Mac OS X is only allowed by its license to run over Apple hardware, so you cannot run it inside a VM that is not running at a real Mac. I read somewhere that the next version of VirtualBox will be able to run Mac OS X, but it will probably only do that on the Mac version.

Try VMWare Player, see my other post.

---

### Post by seshwan on 2010-08-15
wow I just spent 8 hours the past two days uninstalling, reinstalling, wiping the registry, trying old versions, new versions, different logins and was almost ready to reinstall windows from scratch only to come here and find I just needed to click a checkbox. Shoulda checked here earlier lol, thanks guys!

---

### Post by aa4bb on 2010-08-21
Followed the instructions about enabling Virtualization in the BIOS and making certain that VT-x/AMD-v was enabled in virtualbox. Voila! It solved the problem of iTunes 9.2 crashing in XP-guest/Ubuntu 10.04-host that has bugged me for months.

Thank you very much!

---

### Post by arepaking on 2010-08-31
The following worked for me:

a) Enable in the BIOS the Intel Virtualization
b) Enable in Virtualbox the VT-X/AMD-V feature.

Note: When you enable the Intel Virtualization in the BIOS you MUST Power Cycle your PC (Turn it OFF and back ON). I tried this without doing it and I still got the crash. Once I did the power cycle it worked for me!!!!

---

### Post by arepaking on 2010-09-02
Update:
I just upgraded my iTunes from 9.2 to 10 and the issue came back. I have the virtualization enabled in the BIOS and in VBox but started to crash once again.

Any thoughts on this?

Thanks,
AK

---

### Post by kevinwu on 2010-09-03
> **arepaking said:**
> Update:
I just upgraded my iTunes from 9.2 to 10 and the issue came back. I have the virtualization enabled in the BIOS and in VBox but started to crash once again.

Any thoughts on this?

Thanks,
AK

That's strange, I waited to upgrade because 9.2 kept crashing on me.  Upgrading to iTunes 10 finally worked for me and I'm able to upgrade to iOS 4.0.2

I had some nasty USB connect/disconnect issues during the firmware upgrade, but found a thread that helped remind me that the USB gets disconnected with the ipod touch goes into recovery mode.  You have to setup a looser USB filter and strip out the device ID so that it can get passed through to VirtualBox when the ipod reconnects.

---

### Post by erikkratz on 2010-09-05
After upgrading to iTunes 10, I'm no longer experiencing problems, even with a CPU that doesn't support VT-x.

---

### Post by Eben Fourie on 2010-09-13
similar issues for me. 

HP G61 - does not support processor virtualization.
karmic, running virtualbox 3.1.8 (xp sp3)
iPod Nano 5G

iTunes 9.1.1 crashes
tried iTunes 8.2.1, but Nano wanted iTunes 9 or later
iTunes 10.0.0.68 = success :-)

also tried various Ubuntu packages such as gtkPod - no success

would love something that works under Ubuntu, but for now vBox with iTunes 10 seems to do the trick...

---

### Post by arak on 2010-09-22
Am running the latest version of Virtualbox and Itunes 10.0.0.68 and it no longer crashes on my machine.  I have an older machine without virtualization in the BIOS

---

### Post by adamf663 on 2011-06-30
I've always run rockbox in my ipods, but had to use the standard apple firmware for the first time as my new ipod classic has the firmware locked and my car stereo will only talk to the apple firmware.

itunes is the worst P.O.S. I've experienced in 30 years.  Constant lockups, even on real hardware.  Idiotic activities like searching for 'gapless playback' for 20 hours whereas it should have been accomplished by a penny's worth of buffer memory on the player and 20 lines of code to play the last of the previous track from the buffer while the next track is being started.

My solution has been to use winamp.  At least I am able to get my player loaded that way.  However, it still works very poorly from both vmware and virtualbox.  I keep around an $80 p4-celeron just for this one app.  I expect the problem is with the apple usb driver and that problem is seen in winamp as well.  At least winamp doesn't lockup constantly.

---

