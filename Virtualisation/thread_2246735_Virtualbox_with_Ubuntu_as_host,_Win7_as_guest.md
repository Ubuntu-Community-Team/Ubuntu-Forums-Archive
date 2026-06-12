---
title: "Virtualbox with Ubuntu as host, Win7 as guest"
date: 2014-10-02
forum: Virtualisation
---

### Post by jlh68 on 2014-10-02
I am considering installing VB on my Ubuntu 14.04LTS computer.  I need some instructions on the procedure to accomplish this, The settings, size of vitural drives, and any other information that would help get this operational.

Which is the better, dual boot Ubuntu and Win7 or to Use Ubuntu (as host) and Win7 (as guest) using VituralBox?

---

### Post by SeijiSensei on 2014-10-03
I'm running Win7 in a VirtualBox on a Kubuntu 14.04 system.  The machine has 6 GB of memory; I allocate three to Windows when it is running.  I created an 80 GB virtual drive for the system.  Most data files I would be using from Windows are located on a network server, so I only need space for the operating system and programs.  

I strongly recommend following the [installation procedure]("https://www.virtualbox.org/wiki/Linux_Downloads") outlined for "Debian-based" systems at the VirtualBox site.  You'll get the most recent updates to VB this way, and maintenance will be automatic just like with regular Ubuntu packages.

It's possible to install Win7 on an Ubuntu host with just 2 GB of memory, but performance will be horrid.  I've used 0.5 GB for Ubuntu and 1.5 GB for Windows, but I wouldn't recommend it.  Even expanding your memory from two to three GB would make a big difference if you want to run a VM.

I spend nearly all my time in Kubuntu and only boot Windows once a month or less.  Given my usage of Windows, virtualization makes far more sense for me than a dual-boot arrangement.  If you spend a lot of time in Windows, and have limited memory, dual-booting is probably a better choice.  The other option is running Windows natively and using VirtualBox to boot an Ubuntu machine.  My daughter's gaming computer is set up this way, though she spends a lot of time in Kubuntu when doing tasks like browsing, email, etc., that aren't demanding of the hardware like games are.

---

### Post by sandyd on 2014-10-03
Moved to *VIrtualisation*

---

### Post by rbmorse on 2014-10-03
Agree with SeijiSensi.  I run a Windows 7 VM on my Ubuntu host on a daily basis.  No issues at all.  

My personal recommendation is that the host machine should have at least 8GB of RAM with 4 or 6 GB assigned to the Windows VM.  It'll work with less, maybe acceptably well depending on the specific tasks, but Windows 7 installed to hardware runs best with at least 4 GB of RAM available and it's not reasonable to expect Windows in a VM to be any different.

---

### Post by Jordan_Cameron on 2014-10-03
Agree with the rest of the posters: running Windows in a VM instead of dual booting, although it does depend on how much you want to use Windows, and what for.

As SeijiSensi said, follow the debian instructions, and make sure you install the addons pack (for usb 2.0 support) and maybe the guest additions, to allow easier clipboard copying between the host and the guest.

Cheers, 
J.

---

### Post by jlh68 on 2014-10-03
Thank to all for the advice.  I have two choices for a computer to run VB on.  one is this netbook (4GB RAM installed and max) the other is my desktop which has *GB RAM installed.  I would be using Win7 not very often.  I mainly need Windows OS for two tasks that have not been ported to Linux.  One is updating maps on my TomTom GPS (max 4 times per year), and to update/program my Logiteck Harmony 650 remote control for my Audio/Video system (including TV).  Just for information I get the Harmony softwar to work on my Ubuntu system with the following exception Ubuntu will not communcate with the Harmony unit or vice versa.  It is hooked to USB port but uses some other king of communication.   The TomTom just won't interface with Ubuntu even though TomTom is a Linux based OS.

I am leaning towards installing on the desktop as I don't think I need to have it mobile.

To install Win7 as guest on VB, will I need the product key from the bottom of the computer?  And will Win7 install on any computer?  I have a third party CD which is a "Fully Install Or Repair Windows".  That reminds me that I will have to get it on a USB flah drive and I don't know if I just need to copy the CD to the flash drive or make an ISO file and copy it.  Any help there?

---

