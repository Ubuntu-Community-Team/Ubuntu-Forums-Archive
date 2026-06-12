---
title: "Win7 upgrade from WinXP with VirtualBox on Jaunty"
date: 2010-04-03
forum: Virtualisation
---

### Post by fritzman on 2010-04-03
Installing Windows 7 as an upgrade from Windows XP, following the recommended method from Microsoft involves downloading it into your Windows XP or Windows Vista, running the Windows 7 Upgrade advisor, and running the Win7-HP-Retail-en-us-x86.exe, which unpacks the setup1.box and setup2.box.  I could NOT get Windows 7 to successfully install on my VirtualBox installation of Windows XP Home Edition, running on Ubuntu 9.04 host.  After several failed attempts, and an hour or so of research, I decided I would need to try the install from a windows 7 iso.  A quick Google search found a site from which I could download an official windows7.iso.
The following is a fairly close representation of my steps to complete an upgrade from Windows XP to Windows 7 as a virtual machine, using Sun VirtualBox on my Ubuntu 9.04 machine as host;

First, download a windows 7 iso.  From the following link, you can choose which windows 7 iso to download.
[http://techpp.com/2009/11/11/download-windows-7-iso-official-direct-download-links/](http://techpp.com/2009/11/11/download-windows-7-iso-official-direct-download-links/)
Download it to some location on your computer, and remember the location.  I downloaded the 32bit version from this link.  I don't think the 64bit version will work, but I could be wrong.
[http://msft-dnl.digitalrivercontent.net/msvista/pub/X15-65732/X15-65732.iso](http://msft-dnl.digitalrivercontent.net/msvista/pub/X15-65732/X15-65732.iso)

Second, if you already have Windows XP installed on VirtualBox, skip to step _3_.  If not, launch Sun VirtualBox, and click on 'New.' Click on 'Next,' and then enter the name of your Windows XP.  I used winxp.  My machine opened up to 'Microsoft Windows' as the os, and 'Windows XP' as the version.  Click next, and follow the instructions on the various screens to build yourself Windows XP virtual machine.  Those familiar with using VirtualBox might know that you don't need to have a CD or DVD burned to install an os.  You can, instead, just point the CD/DVD device to the location where you saved your Windows XP iso, if you have it copied to your hard drive. Else, point it to your CD/DVD drive, if it doesn't already point to it.  Then, put your WindowsXP CD in your drive and close it. 

Third, after you have your Windows XP virtual machine built, don't worry about getting all the bugs and quirks worked out of it.  It doesn't need to work at all.  The Windows 7 installer will just look for a qualified upgradeable product, and then move on.  The functionality of it is irrelevant.  Turn off your Windows XP machine, and from the VirtualBox menu, click on 'New' again.  Step through the process to build a Windows 7 machine.  I cleverly called mine win7.  Before you click on 'Start,' open up your settings, and scroll to 'Storage.'  Right-click on IDE Controller and click on 'Add Hard Disk.'  Browse to the Windows XP hard disk you just created or already have, and add it as a second hard disk to your new Windows 7.  Also, browse to the location of your downloaded Windows 7 iso for your CD/DVD device.  For me, that is a great feature, because the Windows 7 iso I downloaded from MS is in UDF format.  I could not get K3B to burn in that format.  Windows will let you download a burning tool for your Windows 7 iso, but it requires Windows XP, Windows Vista, or Windows 7 to use it.  This could be a real dilemma for you.

Fourth, click on 'Start,' and proceed with the installation.  When you get to the screen asking where you want to install it, point to your new empty hard disk. (It should be drive 0.)  The installer will "see" your Windows XP drive, and when you get to the screen asking for your License Key string, enter it.  The installer should accept it, and proceed with the rest of the installation.

Of all the tripe I've seen from Microsoft over the years, in my opinion, Windows 7 smells the least.  Far too much is still hidden and kept mysterious to the user, but at least it works.  Mine hasn't choked on me even once, yet.

So, for the rare occasion that I actually NEED Windows, I have a new Windows 7 to use, and I didn't have to waste a partition on my hard drive for it.

I hope this helps anyone trying to upgrade your WinXP virtual machine.

owa):P

---

