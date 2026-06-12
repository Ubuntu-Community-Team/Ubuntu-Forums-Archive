---
title: "Noob asking questions about VirtualBox"
date: 2011-01-07
forum: Virtualisation
---

### Post by 3602 on 2011-01-07
Alright. First, I don't understand *anything *regarding virtualization. I read about it in Encyclopaedia Brittanica.
So as I understand it, let's say:
1. VirtualBox would allow me to run (install) Windows 7 "in" Ubuntu. Is that correct?
2. Would that Windows 7 automatically detect my computer's hardware?
3. How do I exit virtualization when I'm done?
My intention of wanting virtualization is to play some games in Windows 7 (due to my overkill specs that can't be exploited in Ubuntu, thank you nVidia). Now if games don't run in virtual Windows 7 then I'll just forget about all this (installing Windows after Ubuntu is complicated).
Thank you very much.

---

### Post by snowpine on 2011-01-07
1. Yes, correct. Windows in Virtualbox will run like any other application. 
2. No. Windows 7 will see the virtual hardware of the virtual machine it's running in, not the physical hardware of your machine. [See here for more info]("http://en.wikipedia.org/wiki/VirtualBox#Hardware_emulation"). 
3. You shut down Windows and the VirtualBox window closes, or you simply close the virtual machine window as you would close the window of any other application (same as powering off the Windows computer).
4. I would recommend dual booting Windows/Ubuntu if you want to use Windows for graphics-intensive games. You will probably not get good graphics performance in Virtualbox.
5. We have a whole [sub-forum on virtualization]("http://ubuntuforums.org/forumdisplay.php?f=308") with some very helpful "sticky" threads. The [Wikipedia page ]("http://en.wikipedia.org/wiki/VirtualBox")is also informative.
6. Installing Windows after Ubuntu [is easy]("https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu"). :)

---

### Post by 3602 on 2011-01-07
> **snowpine said:**
> 1. Yes, correct. Windows in Virtualbox will run like any other application. 
2. No. Windows 7 will see the virtual hardware of the virtual machine it's running in, not the physical hardware of your machine. [See here for more info]("http://en.wikipedia.org/wiki/VirtualBox#Hardware_emulation"). 
3. You shut down Windows and the VirtualBox window closes, or you simply close the virtual machine window as you would close the window of any other application (same as powering off the Windows computer).
4. I would recommend dual booting Windows/Ubuntu if you want to use Windows for graphics-intensive games. You will probably not get good graphics performance in Virtualbox.
5. We have a whole [sub-forum on virtualization]("http://ubuntuforums.org/forumdisplay.php?f=308") with some very helpful "sticky" threads. The [Wikipedia page ]("http://en.wikipedia.org/wiki/VirtualBox")is also informative.
6. Installing Windows after Ubuntu [is easy]("https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu"). :)
Thanks, man. I don't think anything I'll be playing would be considered graphic-intensive. Surely I will use System Requirements Lab to check first, but all this hardware is backed by a weak i3. So I don't put much hope in it.
Also, see [this here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")? Complicated. What flows through my bloods when I read that is fear. Pure fear.

---

### Post by snowpine on 2011-01-07
> **3602 said:**
> Also, see [this here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")? Complicated. What flows through my bloods when I read that is fear. Pure fear.

I understand ;) and in that case VirtualBox is the "no fear" approach because it gives you a totally isolated "sandbox" environment for your Windows 7 "guest" OS. Good luck! :)

---

### Post by JKyleOKC on 2011-01-07
> **3602 said:**
> Also, see [this here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")? Complicated. What flows through my bloods when I read that is fear. Pure fear.When you create a virtual machine with VirtualBox or any other virtualization program, it acts like a totally separate piece of hardware. That's what the virtualization program does; when you launch the VM the first time, it's just like starting up a real machine that has no system on it. You have to install whatever you want. From that point on it's almost completely separate even though everything actually runs through your real hardware, so the complications that your link points to don't happen.

However as another poster said, you may be better served by setting up a dual-boot system with each operating system getting approximately half of your disk space. Since the VM's processor **is** virtual, it's going to be slower than your real processor, and the same will be true of the VM display and the memory. It won't be so noticeable on disk access, but will still be a bit slower. All of this may combine to produce noticeable lag in the game's response. My experience is that VMs work nicely on systems with at least 3 GB of RAM and at least dual-core processors, but are significantly slow on systems with single-core processors and less RAM (although I do run one on a single-core system with just 256 MB of RAM; it's usable, but painfully slow).

Setting up a system for dual booting isn't particularly complicated, if you start with an absolutely empty drive and install Windows first. When that is done you can install Ubuntu, and at the partitioning step tell it to share the drive; it'll automatically handle the splitting for you. If you install Ubuntu first, then you run into the problems described in your link!

---

### Post by vidtek on 2011-01-07
Like the others said, forget virtualisation and games, they don't go together.

Dual booting is easy, my advice is to get 3 physical drives, 2 smallish, maybe 250gb and one biggie for your data.

1) Install Windows from scratch on one with just that drive connected electrically.

2)Install big drive and move the My Documents setting into that drive, right mouse click on the desktop folder then -> move

3)Make sure that when you install your games, they install into the big drive, there is usually a choice, c:\program files\etc etc etc. change it to e:\games or whatever letter your big drive is.

4)Make sure everything runs!

5)Hook up drive 3 and install Linux into that one.  This is the nasty bit where things can go horribly wrong!

Unfortunately Linux likes to see all the hardware at installation time, there can be many fiascos when you add things on afterward in a piecemeal fashion.

Take your time over this next step, on switch-on now, many motherboards just show a splash screen so you can't see the boot messages.  There is always an option to turn this off in your motherboard bios.

This is how to do this:
Immediately after switch-on press the key which activates bios editing, it's usually the del or f8 or f2 keys, check your manual or the first boot screen (small text at the bottom of the screen for a couple of seconds) for which key does this.  

If you don't have a splash-screen ignore the preceding paragraph.

You can identify which drive is which by the switch-on (or POST Power-on self test) screen.  I always try to get different manufacturers drives which makes it a lot easier to identify drives at this early boot stage. 

You can stop the post in mid-stride by pressing the pause/break key.  I then just take a quick snapshot of the screen with my phone camera so I can refer to it later.  Press the enter key to resume the post.

Once you are confident you know which physical drive is the small Linux one you can proceed.

There is a lot of confusion over identifying drives because the bios, Windows and Linux call the same thing by 3 different names.

The bios calls them hdd0 hdd1 hdd2
Windows calls them disc0 disc1 disc2
Linux calls them (for serial ATA drives)sda1 sdb1 sdc1
Linux also calls partitions of physical drives sda2, sda3, sdb2, sdb3 etc.

6) Install Linux to the 3rd drive.  During install Linux will detect the other drives.  ALWAYS choose custom partitioning if you have a dual or multi-boot system

7) Linux installs are very poor at this critical point.  Check and check again where it is going to install the boot loader.  Make sure you install the boot loader into drive 3 linux MBR 

 [noparse]8)[/noparse] Check again it's going into drive 3 the linux drive.

9) Test your new system, make sure your Linux system can see the large drive for your documents

10) Boot into Windows when you want to play your games and do other silly Windows stuff.

Best of luck, Tony

---

