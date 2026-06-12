---
title: "How to mount iso for Virtualbox: PC freeze after run attempt of mounted iso at sr0"
date: 2018-01-21
forum: Virtualisation
---

### Post by smith73 on 2018-01-21
I'm installing Windows 8 on Virtualbox in Ubuntu Mate 16.04.3 and I treid 4 supported apps: gmountiso, gisomount, acetoneiso, furiusisomount, none of them worked. Trying to run windows Installation  from a physical dvd in Virtualbox also didn't work. After clicking a media for installation in Virtualbox there's only 1 option displayed in Virtualbox - DVDRAM (sr0) and after clicking it the PC freezes and needs a restart.  Earlier I installed same .iso in same Ubuntu distro with CDemu, it worked ok and during installation displayed 2 DVD drive options instead of only sr0. [https://launchpad.net/~cdemu/+archive/ubuntu/ppa](https://launchpad.net/~cdemu/+archive/ubuntu/ppa) but this ppa for CDemu is unsupported.  How to properly mount an .iso to run in Virtualbox? Should CDemu from unsupported ppa be used?    Thank you very much

---

### Post by yancek on 2018-01-21
You're trying to install windows in Virtual Box so I would suggest that you check the VirtualBox site which has detailed documentation.  Or a windows forum as the host system is not really significant for installing on a virtual machine.

---

### Post by lammert-nijhof on 2018-01-21
Do not worry about mounting the DVD, that will be done on insertion automatically. 

I assume you tried:

[LIST=1]
[*]Define the Virtual Machine
[*]Insert the DVD in the drive
[*]Change the Storage Section of the VM by selecting the DVD
[*]Afterwards click the DVD Icon in the extreme right hand of that window.
[*]Select the Host HW drive in the drop down menu instead of an ISO file.
[*]Start the Virtual Machine
[/LIST]

Maybe you have to dismount the DVD after insertion (by right clicking it in the host file manager), since it will be needed exclusively by the VM.
Or
Convert the DVD to an ISO file and use the ISO file to install the system. Use e.g. Brasero to copy the DVD to an ISO file.

---

### Post by deadflowr on 2018-01-22
*Thread moved to **Virtualization** *

---

### Post by smith73 on 2018-01-22
> **lammert-nijhof said:**
> Do not worry about mounting the DVD, that will be done on insertion automatically. 

I assume you tried:

[LIST=1]
[*]Define the Virtual Machine 
[*]Insert the DVD in the drive 
[*]Change the Storage Section of the VM by selecting the DVD 
[*]Afterwards click the DVD Icon in the extreme right hand of that window. 
[*]Select the Host HW drive in the drop down menu instead of an ISO file. 
[*]Start the Virtual Machine 
[/LIST]



1, 2 - yes. Ok.

The point is that I successfully used CDemu earlier for .iso mounting to Virtualbox in Ubuntu, but CDemu comes from unsupported ppa and people recommend it on the forum from unsupported ppa, and it is not present in apt-cache and can't be utilized for autoremove and has no uninstall function. 
When mounted via CDemu Virtualbox displays 2> options (sr1>, probably) for selecting the boot media, and with all 4 abovementioned iso mounting software Virtualbox always displayed only 1 option for boot media (sr0).

---

### Post by Habitual on 2018-01-22
For the Properties of the Windows **Guest**

Now go to Storage from the left sidebar and click Empty under IDE Controller. Click the CD icon next to CD/DVD Drive selection box and click Choose a virtual CD/DVD disk file. Now navigate to the Windows 8 ISO file that you downloaded and select it. When done, click OK.

Once Virtaulbox can "see" the .ISO, all you have to do is reboot and it should install from there.
See also [https://www.addictivetips.com/windows-tips/how-to-install-windows-8-on-virtualbox/](https://www.addictivetips.com/windows-tips/how-to-install-windows-8-on-virtualbox/)

CDmenu = IDK

---

### Post by smith73 on 2018-01-22
> **Habitual said:**
> For the Properties of the Windows **Guest**  Now go to Storage from the left sidebar and click Empty under IDE Controller. Click the CD icon next to CD/DVD Drive selection box and click Choose a virtual CD/DVD disk file. Now navigate to the Windows 8 ISO file that you downloaded and select it. When done, click OK.    I tried this one and it didn't work, PC became suspended and I needed to reboot it. I've also tried booting WIndows Guest in Virtual box from a physical CD and the result was the same.

---

### Post by smith73 on 2018-01-24
So I tried to mount the win81.iso at Virtualbox Storage section at 1536 MB and 1792 MB of RAM (on total 4 GB RAM) and all of them produced same result: PC becomes suspended and needs a reboot from "power" button. Last time the win81.iso installed in Virtualbox and worked well at 1536 MB RAM (when mounted from CDemu at virtual CD drive), it didin't need 3 GB, as stated in the link. 

When mounting from furiusisomount (probably, as I don't have access to it now), I tried mounting with both "Fuser" and "Loop" options available, and all of them produced the same result which necessitated in total PC reboot. Thus I may suppose that even mounting from command line (mount /path/to/file.iso  /mnt/cdrom -oloop) would produce the same result. I can't see how one can mount an .iso to Virtalbox from gmountiso, gisomount, acetoneiso, furiusisomount applications. None of them creates what is being "seen" by Virtualbox as sr1 or sr2 - what seems to be "true" virtual drive - in the dialog window where Virtualbox asks to choose a boot media. When mounted via these 4 apps in the dialog window Virtualbox asks to choose a boot media and there is only 1 option - HL-etc-DVDRAM sr0, which after running suspends the system. Only CDemu created the sr1 and sr2 virtual drive options to choose and successfully boot from. But CDemu is not in the repositories and can't be removed by autoremove function.

(I'm running Ubuntu-Mate 16.04.3)

---

### Post by smith73 on 2018-01-27
> **Habitual said:**
> For the Properties of the Windows **Guest**  See also [https://www.addictivetips.com/windows-tips/how-to-install-windows-8-on-virtualbox/](https://www.addictivetips.com/windows-tips/how-to-install-windows-8-on-virtualbox/)  CDmenu = IDK  The following issues differ in my installed Virtualbox (installed via Appgrid): 1) Under Guest Settings -> Storage there is no "IDE controler" option to select a cd/dvd drive until I click on the icon Create new device -> IDE Controller, and select .iso to boot from. 2) Under Guest Settings -> System -> Motherboard there's no option of "Enable absolute pointing device" under "Extended features". Instead there is a separate section for "Pointing device" with   3 options: 2 for tablet USBs, 1 - "PS2/Mouse".  So I reinstalled Virtualbox,  selected "PS2/Mouse" and while booting either from CDemu, or from .iso mounted at Storage -> IDE Controller, Virtualbox suspends everything after that for total PC restart.  Virtualbox not working!

---

