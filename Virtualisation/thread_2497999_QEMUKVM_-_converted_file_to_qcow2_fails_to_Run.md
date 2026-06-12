---
title: "QEMU/KVM - converted file to qcow2 fails to Run"
date: 2024-05-25
forum: Virtualisation
---

### Post by Rick St. George on 2024-05-25
Note Build:
Mobo - MSI 990FXA-GD65 Military Hardened (not overclocked) set for UEFI Boot (confirmed)
CPU - AMD FX-8320 Vishera 8 Core
GPU - RX 580 8GB Ram in PCIe x16 slot
PSU - 450 Watt Enermax Gold
RAM - 2 X 8GB Corsair Vengence DDR3 1600 Mhz
OS - UbuntuStudio-64 v22.04 LTS


I received my new GPU, after hardware install ... did a Fresh Install of UbuntuStudio v22.04. Both Monitors now working.
Installed virt-manager via MUON Pkg Mgr, virt-manager will not Run. Have to open terminal and do;
```

sudo virt-manager

```

Previously converted from VirtualBox xxxx.vdi - VirtualBox no longer installed. Using the following format;

```

$ qemu-img convert VirtualDisk-TradeSoft.vdi -O qcow2 VirtualDisk-Tradesoft.qcow2

```

Selected the qcow2 file, from conversion, and Blue Screen shows when WinXP attempts to start with Stop: 0x000007B. Even Safe Mode won't work. Maybe it got corrupted and should try the conversion process again? So did so ... same thing! The qcow2 file is in under my Home dir.  I could start / build another one, but has to be Windows to install software for Trade Charting via MetaStock and a number of added modules. But, If I could import the Appliance .. its all there! 

Any ideas??? 
Thanks!

---

### Post by MAFoElffen on 2024-05-25
On having to use 'sudo'... Did you add yourself to groups kvm & libvirt? You shoudl not need to use sudo to start that. In fact your shouldn't...

That is the same commands I use to convirt vdi to qcow2.

Currently downloading a WinXP SP3 VDI image from [https://archive.org/details/xp51_20191108](https://archive.org/details/xp51_20191108) to test if I can bring it up. Will take an hour and a half... LOL

---

### Post by &amp;KyT$0P# on 2024-05-25
> **Rick St. George said:**
> Selected the qcow2 file, from conversion, and Blue Screen shows when WinXP attempts to start with Stop: 0x000007B. Even Safe Mode won't work. Maybe it got corrupted and should try the conversion process again? So did so ... same thing! 

Once saw a similar issue with migrating XP guest from VirtualBox to virt-manager.  The solution in that case was to boot the converted guest with [Hirens BootCD (version 15.2)]("https://www.hirensbootcd.org/old-versions/") and run one of the tools included in Hirens BootCD.  I don't remember more details, sorry.

---

### Post by MAFoElffen on 2024-05-26
The VDI I grabbed of Win XP Pro was a 32bit version. 64bit versions of XP were rare. Got the bluescreen on boot as it saw different (unknow about the previous) hardware than it was installed on originally. LOL

Status:
Replicated the problem. Working on a solution so I can post that. I have some out-of-the-box ideas. And it's raining right now, so I can't work on my truck (yet).

I have that ISO in my ISO Library. Will try it later, if other things don't work... LOL

---

### Post by MAFoElffen on 2024-05-26
I figured it out. It wasn't the vDisk conversion... LOL

I had set the controller to IDE. HDD, Floppy, and CDROM as IDE. BIOS as Legacy. Chipset as i440FX. Sound as AC97. Video to VGA. Old to replicate older hardware...

Windows stores what it was installed on hardware wise, including the motherboard, which said VirtualBox.

On startup, it would go into a boot loop, with a BlueScreen (BSOD) saying it had different hardware, then to a Boot Error screen asking if I want to SafeBoot, SafeBoot with networking etc... where non of the options would work...

Booted from an old Hiren's.BootDC.15.2.iso. > Mini XP > Started the HBCD Menu > Programs > Registry > Fix hard disk controller (fix-hdc.cmd). Shutdown.

After doing that, I changed the ISO in the CDROM device to the earliest Fedora Win virtio driver ISO in the CDROM settings. Reset the boot order to the HDD.

Booted. New found hardware wizard came up, Pointed it to find the drivers in the i386 Win7 folder. (most of those will work for XP.) Rinsed and repeated until it have all the virtio hardware drivers installed.

---

### Post by Rick St. George on 2024-05-27
> **MAFoElffen said:**
> 
I figured it out. It wasn't the vDisk conversion... LOL

Booted from an old Hiren's.BootDC.15.2.iso. > Mini XP > Started the HBCD Menu > Programs > Registry > Fix hard disk controller (fix-hdc.cmd). Shutdown.

After doing that, I changed the ISO in the CDROM device to the earliest Fedora Win virtio driver ISO in the CDROM settings. Reset the boot order to the HDD.

Booted. New found hardware wizard came up, Pointed it to find the drivers in the i386 Win7 folder. (most of those will work for XP.) Rinsed and repeated until it have all the virtio hardware drivers installed.

Need clarification please;

Got the Hirens Boot CD, Have Guest window OPEN (Guest not running) but how to Boot Hiren's CD inside the Guest not Running?
I can click the DETAILS would any info from here help? I clicked Add Hardware, added CDRom, but get 
"Error connecting to HBCD 15.2/autorun.inf, Permission denied", same with HBCDMenu.exe!  Don't see miniXP. There is an XP folder.

---

### Post by MAFoElffen on 2024-05-27
Note that the files ownership of ISO files should either be owned by you ($USER:$USER), or by kvm:libvirt.

After adding IDE CDROM 1 in the Settings > Add hardware... 

Select that CDROM drive in the left pane. Click browse in the right pane. But before that step... A popup will appear, with storage pools in the left pane, and files in the right pane.

I have a storage pool created (add via the <+> key), pointing to the directory of my ISO files, where I keep my ISO file library. Usually KVM Users put those ISO files in a folder inside the Downloads folder.

Select that ISO pool in the left pane. Select the ISO file in the right pane. Select Choose Volume. That popup dialog box will go away and populate the path & filename in the right dialog box. > Select Apply.

In Virt-Manager Settings > Boot Options > Select the checkbox for IDE CDROM 1 > While highlighted, click the Up Arrow to move it to the first in the boot order. > Select Apply. 

Select Screen > Run.

With the error you are getting and talking about an .exe files, either you are selecting the wrong thing in the wrong place, or you have the wrong ownership set, or the wrong permissions set for that ISO file.

Enough info?

---

### Post by Rick St. George on 2024-05-28
I'm trying to understand, not be difficult ...but why did the programmers remove CD/DVD drivers in Ubuntu 22.04 ?!?!?
Yesterday I installed the Drivers. Today ... again, CD / DVD Not Recognized. What the hell is going on???
And are you saying that Virtual Mgr. can read from an ISO file and BOOT? Knowing which file to Boot from in the ISO???

> **MAFoElffen said:**
> 
Note that the files ownership of ISO files should either be owned by you ($USER:$USER), or by kvm:libvirt.


ISO file I downloaded to Downloads / ISO shows Owner & Group can View & Modify
If I understand correctly, I'm using the ISO file, not the CDROM disk in the CD Drive.

> 
After adding IDE CDROM 1 in the Settings > Add hardware... 


There is no "Settings" in Virtual Mgr. I set CDROM as SATA because that's the way its is connected.
I Open the winxp which is shutoff, then click the blue "i" icon (show virtual hardware details)

> 
Select that CDROM drive in the left pane. Click browse in the right pane. But before that step... A popup will appear, with storage pools in the left pane, and files in the right pane.


There is no Pop-up, but I think I see the "pools" you are referencing. And why are we using CDROM to open an ISO file?
Clicked + key on bottom left, Name: Hirens-Boot-Vol   Type: dir: Filesystem Directory

> 
I have a storage pool created (add via the <+> key), pointing to the directory of my ISO files, where I keep my ISO file library. Usually KVM Users put those ISO files in a folder inside the Downloads folder.

Select that ISO pool in the left pane. Select the ISO file in the right pane. Select Choose Volume. That popup dialog box will go away and populate the path & filename in the right dialog box. > Select Apply.


Did so ... Going to my Downloads Folder where the ISO is, instead of the CD burned with the ISO contents, although not sure why?
Other than the fact the programmers don't want us accessing CD/DVD drives, as they left out the drivers from the OS!
The + key brings up "Create Storage Volume" / Name ****.qcow2  Format gcow2  (odd - this is an ISO file, not a qcow2 file)
So, I am confused about being confused.

> 
In Virt-Manager Settings > Boot Options > Select the checkbox for IDE CDROM 1 > While highlighted, click the Up Arrow to move it to the first in the boot order. > Select Apply. 
Select Screen > Run.


Did so, this is the Result ... 

"SeaBIOS (version 1.15.0-1)
Machine UUID 38ab9368 ****
iPXE 00:03.0 CA00  *****

Booting from DVD/CD ... 
Boot Failed: Could not read from CDROM (code 0005)
No bootable device."

Shutting down does not work, have to use Force Off (are you sure?) YES
Guest not Running --- Problem unresolved.

> 
With the error you are getting and talking about an .exe files, either you are selecting the wrong thing in the wrong place, or you have the wrong ownership set, or the wrong permissions set for that ISO file. Enough info?


Can you tell me where is the wrong place? Not a reflection on you, but I followed your instructions. This is a fresh install of Ubuntu v22.04.
After a month, why can't I get it working right? Why is it defeating me at every turn? By now .. this is not supposed to be hard!?!?

Are we expected, in the New Ubuntu 22.04 +, to VERIFY and/or Make Changes to set Permissions for every file on our computer, to ONLY install with SNAP (as using anything else breaks the OS), install drivers for simple hardware like CD / DVD drives that are a standard???
How do people operate this way? I've been an Operator since the 70's, I know most people don't have a clue! Now they are making it difficult even for me. Unbelievable ! ! ! BTW - the only hardware that changed was the GPU, and I installed the OS with UEFI, not BIOS.

---

### Post by Rick St. George on 2024-05-29
Recreated the scenario, following your explicit details. Thank You! Via add hardware made another CDRom but as IDE. 
Chose the Hiren's.BootCD.15.2.iso file, selected "Choose Volume" and Apply. Then chose CDRom 1 as 1st Boot.
Get the following msg.

"Error starting domain: Cannot access storage file 
'/home/stephen/Downloads/ISO/Hirens.BootCD.15.2/Hiren&apos;s.BootCD.15.2.iso':
No such file or directory"

And yet I'm looking right at it! For the life of me can't figure what I'm doing wrong!!

---

### Post by bobunderwood99 on 2024-05-29
Rename the iso file, removing the apostrophe and space.

---

### Post by Rick St. George on 2024-05-30
> **MAFoElffen said:**
> 

Booted from an old Hiren's.BootDC.15.2.iso. > Mini XP > Started the HBCD Menu > Programs > Registry > Fix hard disk controller (fix-hdc.cmd). Shutdown.


Accomplished ... Thank you!

> 
After doing that, I changed the ISO in the CDROM device to the earliest Fedora Win virtio driver ISO in the CDROM settings. Reset the boot order to the HDD.

Booted. New found hardware wizard came up, Pointed it to find the drivers in the i386 Win7 folder. (most of those will work for XP.) Rinsed and repeated until it have all the virtio hardware drivers installed.


What I got was, "Windows must be reactivated in 3 days, Do you want to reactivate now?"
Of course I click no, and WinXP ran, but probably will not work after the weekend, even though previously it was registered. Can't see the Guest Pkg. and wasn't able to install any of the drivers as it could not connect to the Net.

Any suggestions would be greatly appreciated.

---

### Post by bobunderwood99 on 2024-05-30
Search on "windows xp activation".

Looks like you can still use phone activation.

---

### Post by Rick St. George on 2024-05-31
Not too concerned about activation (trying to find my 2 XP CDs) I know it is embedded ... so how did it lose it? Nevertheless,
what I'm more concerned about is How to install the Guest Additions (maybe only needed in VirtualBox). and /or the Virtio drivers.
I have Windows running, and can access "virtio-win-0.1.1" and here are the choices;
* Balloon
* guest agent (but can't select OK as its greyed out)
* NetKVM
*qemupciserial
* viorng
* vioscsi
* vioserial
* viostor

But none seem to work for WinXP. Found new Hardware Wizard shows after Boot, and need to install;
* unknown
* pci
* vga
* NET
* Audio Device on HD audio bus

If I get the Network working, perhaps it can find the drivers. I can also update my Charts (takes only seconds) then I go offline.
Tryied the windows / inf folder also, but can't seem to locate drivers for the above. And if I find my Win CD, Ubuntu v22.04 will not even show my 2 CD/DVD drives! Had to install the drivers, and still won't show!

Any ideas? Thanks Bob for your concern and time. I'm afraid to ReInstall VirtualBox and invite all the previous problems, like knowing which kernel matching systems, black screen on boot, and UbuntuStudio 3rd install of v22.04 not working.

---

### Post by Rick St. George on 2024-05-31
HOORAY .. Got internet working by looking at Virtual Hardware Details (blue i), selecting NIC and choosing "virtio". 
Then looking at the GUI, New Hardware Wizard showed for Network and selected the folder NetKVM (see above).

Now if I can just get the USB to work! I see controller USB / Type: USB, Model: USB 2 (w/options USB3, Hypervisor default)
  Note: choosing Hypervisor shows ERROR: USB port 3 not present on USB bus 0

USB Redirector is Type: SpiceVMC (and can't be changed).

Need USB to connect thumb drive and Update Chart files from my Laptop.

---

### Post by bobunderwood99 on 2024-05-31
Insert USB drive before starting guest

In VirtMgr>Details click "Add Hardware"

Select "USB Host Device"

Select desired USB drive>click "Finish"

Power on the VM


Another way:

Copy your chart files from laptop to host.

Use python web server to copy files from host to guest (use command for python 3).

Shut the server down as soon as you're done!

[URL="https://medium.com/@onehackman/sharing-files-between-host-machine-and-vm-with-one-command-81fd6eb6c957"]https://medium.com/@onehackman/sharing-files-between-host-machine-and-vm-with-one-command-81fd6eb6c957
[/URL]

---

### Post by Rick St. George on 2024-06-02
> **bobunderwood99 said:**
> Insert USB drive before starting guest
In VirtMgr>Details click "Add Hardware"
Select "USB Host Device"
Select desired USB drive>click "Finish"
Power on the VM


This is what worked, got all files transferred and the Virtual machine online. 
Thanks a million Bob for sticking with me.

Much blessings to you and yours! Good Karma is coming your way!

Peace

---

### Post by bobunderwood99 on 2024-06-02
I'm happy it's working for you.

Namaste

---

