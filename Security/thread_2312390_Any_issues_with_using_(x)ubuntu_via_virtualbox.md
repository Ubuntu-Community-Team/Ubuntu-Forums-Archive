---
title: "Any issues with using (x)ubuntu via virtualbox"
date: 2016-02-04
forum: Security
---

### Post by xadder on 2016-02-04
Hi!

I need a new laptop soon, and wonder whether to install Xubuntu via virtualbox, instead of doing my usual wipe-out of Windows and full ubuntu install.  I assume I will need some virus protection (AGV?), but with minimal use of Windows do I need to worry much more about this way of using Ubuntu?

(I am not a security fanatic; my laptop has mainly open-source code and no secrets.)

The first reason I am considering this is to have access to the occasional use of MS-only software (e.g. Olympus camera software); I have no intention of installing MS Office and suchlike. The second is that I read that Windows takes care of the wireless connections even for an Ubuntu session, which might help sometimes. (As background, my current Thinkpad X220i with Xubuntu started having issues with wirelss (and suspend) around the time of 14.xx  upgrades, or was it 13.xx. Before that all  things worked perfectly.)

Thanks!

---

### Post by TheFu on 2016-02-05
There are always security/privacy issues with any hostOS. Only you can decide whether running Windows as the hostOS makes sense or not. Basically, the hostOS is a man-in-the-middle, so consider that aspect. Have you read the new privacy policy for Win10 and carefully read what data they collect and share without explicitly asking?

AV is only 50% effective. If you can 5 AV programs, that would be 85% effective, tops.

If you don't have anything to hide, please post your email userid and password here. That will help everyone understand how much they really care about privacy.

Would it be possible to run Windows inside a VM under Linux? If you mainly run Linux all day, that is what I'd do.  Of course, if you are a Windows gamer, you really need to dual-boot.

Lastly, you could swap everything I said about Windows and put Linux in that place. Everything is still true, except the AV part.  There are viruses for Linux, we just don't see them very often and most of the time, the only reason to run AV on Linux is to be nice to Windows and Mac people on the same network.

Are there any issues using ubuntu via virtualbox?  Sure, there are always issues. Depending on your needs, the graphics performance might not be what you want. You'll want to tune the hostOS and virtualbox settings to get the most performance possible. Lots of how-tos exist for that. Definitely avoid any Linux DE that wants 3D GPU (like Unity). XFCE or LXDE or any pure WM will work fine.

---

### Post by xadder on 2016-02-05
OK, thanks. I can consider Windows within Linux; I assume new laptops come with a CD to install but I'm not sure. (I generally just do a full install of Linux, and throw away any MS discs.) Maybe I'll just give up on the virtualization idea and then just worry about one OS at a time.

---

### Post by pfeiffep on 2016-02-05
> **xadder said:**
> OK, thanks. I can consider Windows within Linux; I assume new laptops come with a CD to install but I'm not sure. (I generally just do a full install of Linux, and throw away any MS discs.) Maybe I'll just give up on the virtualization idea and then just worry about one OS at a time.Many folks posting here use multiple OSes. Virtual installs are certainly on method with the advantage that one doesn't have to reboot to access the other OS. 
I prefer to dual boot - on my HP desktop machine I've installed Ubuntu on a separate hard drive and use bios to choose when to boot Windows. 
If you have all the uses required for your computer covered by Linux then installing Windows is probably unnecessary. 
Many folks have specific needs that are more easily addressed by Windows apps so they have 2 OSes.

---

### Post by TheFu on 2016-02-05
I don't like to dual boot. Find that it trashes the boot controls about 2x a year (thanks to MSFT patches ignoring that grub exists).  I use virtualization constantly, daily, right now.  Earlier today, that post was written from a Win7 machine running x2go-client connected via ssh to a KVM VM running Ubuntu Server + openbox for the window-manager.  Now I'm out of the house with a 13inch 1080p Chromebook (love the hardware, hate ChromeOS) running ubuntu + openbox inside a chroot environment. Inside that ubuntu, I'm using x2go-client to connect to the same kvm-desktop running in a private cloud.  Having a desktop that is available from anywhere in the world is nice. I've used x2go from 5 different continents and it basically works the same provided at least ISDN bandwidth is available.  If there isn't any networking, a lite-netbook-type machine is what I choose.

So, as you can see, I use multiple OSes, multiple VM technologies, and lots of different sorts of hardware daily - all with ubuntu at the core.
Sometimes I need Windows.
Most of the time, I **need** Linux and Ubuntu is my choice (without any DE). Openbox is a relatively lite window-manager. I wouldn't suggest someone new to Linux deal directly with openbox - a DE makes life easier until you get frustrated with and lack of control and the bloat every DE brings. Perhaps 20 yrs from now, you'll be like me and run a minimal Linux too?

I stopped using virtualbox over 2 yrs ago (maybe 3). virt-manager on KVM with either x2go or spice easily meet my needs for most remote desktop access. No high-FPS gaming of course.  If you must use Windows as the hostOS, then virtualbox is the least of the _evil_ choices available. IMHO.  Virtualbox has a pretty GUI that makes it seem like a full-featured hypervisor and for most people it is absolutely fine. If you can run Linux as the hostOS, there are many other choices worth consideration.

This doesn't have to be a hard choice. Comes down to what the Windows license allows - can it be virtualized legally or not?  I won't run Win10, so don't know how those license are, but some XP, Vista and Win7 licenses were tied to the hardware and would not load onto any different hardware (or into a virtual machine).  If you get Windows with a PC, there aren't usually any Windows-OS disks provided. I haven't seen that since 2004-ish.  Saving the $0.40/PC in creating the Windows install DVD really saves those PC vendors a bunch!  In theory, you should be able to create recovery media yourself. That's the theory. Be certain that you do, even if you never intend to run Windows - when you sell the machine to the next person, they might appreciate running Windows - or you can make an image backup of the factory HDD using something liike partimage, clonezilla, or dd. There must be 50 other tools that do it too (including pretty Windows-only tools). Having a bit-for-bit backup of Windows is a good idea.

Ask if you have more questions.

---

### Post by pfeiffep on 2016-02-06
> **TheFu said:**
> I don't like to dual boot. Find that it trashes the boot controls about 2x a year (thanks to MSFT patches ignoring that grub exists). 
<snip>+1 

I'm fortunate in that on the machine I primarily dual boot I don't use grub to access Windows 7. I'm able to select the Windows boot drive with an escape key press during bios startup.

---

