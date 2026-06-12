---
title: "Legacy Intel Xeon Server, Wont Boot/Install Ubuntu Server From USB."
date: 2016-08-03
forum: Server Platforms
---

### Post by upsidedowncandy on 2016-08-03
Tried fiddling with BIOS setting's, tried making the Bootable USB with different USB creator's, tried re-naming syslinux to isolinux on the USB and vice versa, tried multiple distro's. 

Once server goes through POST and tries to boot from USB... Constantly get the error message "A Disk Read Error Occurred" and another i have had but can't remember, think it was "Failed To Boot" or something.

[ATTACH=CONFIG]270548[/ATTACH]

Fairly sure it's this Motherboard

[http://download.intel.com/support/motherboards/server/se7501hg2/sb/se7501hg2_thol_rev22.pdf](http://download.intel.com/support/motherboards/server/se7501hg2/sb/se7501hg2_thol_rev22.pdf)

---

### Post by volkswagner on 2016-08-03
Does the stick boot in other computers?

Have you tried a different usb drive (some sticks just don't play nice)?

Is the CPU  64bit compatible?

---

### Post by upsidedowncandy on 2016-08-03
Ah just made a new USB with Ubuntu Server 16.04 on using YUMI... tested it on another computer and it booted in to the GUI installer with no problem's.

Tried it on the server and it got to the YUMI OS selection screen, selected Ubuntu Server and it didn't get to the GUI just say's "No Default Configuration Or UI Found, Boot:".

Fairly sure the supposed fix for that is to rename the syslinux/isolinux files and folder but I've tried that before with no success, may try that again unless you have any other idea's? 

All I know about the CPU's at the moment is that they are... Intel Xeon 3.06Ghz, 533Mhz FSB with 512k Level 2 Cache, Is a dual socket motherboard and both are single cores.

Thanks for the reply.

---

### Post by MAFoElffen on 2016-08-03
What is the make/model of the server or motherboard? Just saying that we might be able to get the spec's of it from that and get a closer ideas of what might be going on from that?

---

### Post by upsidedowncandy on 2016-08-03
Motherboard I believe is (going off the board part number - in pic in first post) Intel SE7501HG2, I linked to a "Tested Hardware and Operating System's" PDF in first post as well. The server i believe is a Custom "Whitebox" or something so I'm told.

Edit: It definitely is that motherboard.

---

### Post by gordintoronto on 2016-08-04
How much memory? Have you tried a tiny Linux, maybe even puppy, which would help you get the specs of the computer?

---

### Post by upsidedowncandy on 2016-08-05
Server has 4 x 1GB, haven't tried a tiny Linux no, can you post a link to the one you mentioned please or any other you might recommend?

---

### Post by MAFoElffen on 2016-08-05
This is a better manaul for your Intel Server Board:
[http://theor.jinr.ru/guide/archive/thproxy/prod_guide.pdf](http://theor.jinr.ru/guide/archive/thproxy/prod_guide.pdf)

I looked at some of the processors and the chipset of that board... and they do not support directly booting form a USB Drive. I confirmed that via page #75 of that manual. Removable in that menu means "floppy", or other legacy removables of the era. You could probably do that via a floppy or cd re-directing to your usb... but if you are going to use a CD anyways, then you might as well install the Minimal CD.

---

### Post by upsidedowncandy on 2016-08-10
Thanks for your reply and the answer to what is going on, looks like i'll be buying some blank cd-r's sometime then. 

Thanks again.

---

### Post by Vegan on 2016-08-10
looks like that old box too old for USB boot, so you will need a dvd burner and some blank dvds, linux is too big for cdrom now

---

### Post by mastablasta on 2016-08-11
if you have a floppy and floppy drive you can use plop boot manager on it to boot from USB.

---

### Post by MAFoElffen on 2016-08-12
LOL... Thanks for reinforcing and expanding on what I said. You left off just using a grub2 boot disk on floppy... and pointing to a bootable .iso file on a USB device. (map it as a drive).

There are many ways to do the same. But since it sounds like the CD drive it came with sounds like it still works (you said you might buy cd disks)... That would be an easiest solution. (Ever shopped for floppy disks lately?)

Keeping under your limit of 700 MB of your drive, that is why I suggested using the Minimal Install disk, which is well under your limit.

---

### Post by upsidedowncandy on 2016-12-08
@MAFoElffen haven't purchased a floppy once in my lifetime haha 

Have managed to get the latest Ubuntu installed using a PATA hard disk directly attached and all seems ok as far as I can tell, system is up and running just trying to learn the in's & out's now.

Look's like the only Hard Disk Drive it can see is the one the OS is running on and I have another single SCSI Hard Disk in the front drive bay.

As far as I know the SCSI Hard Drive should be ok as it was in a sealed ESD bag and had a test report attached to it which reported all ok.

Trying to make use of it and any help would be appreciated, have poked around in the megaRAID utility and googled but to no avail.

Don't know if this is of any help but the manual say's the motherboard has got an embedded "Adaptec AIC-7902 dual function SCSI controller" which provides Ultra320 (LVDS), (Ultra4) and Ultra wide (SE) SCSI interfaces as two independent PCI functions. 

And also... The Intel SE7501HG2 baseboard provides active terminators, termination voltage, resettable fuse and protection diode for both SCSI channels. If that's anything to do with it!.

Another edit: Also getting this in the megaRAID bios config... "Error when formatting the physical drive on Channel-1 ID 0x04.

Yet another edit: Turns out this system does have a PCI controller for the megaRAID SCSI hardware. I thought it was just an interface for the embedded controller and I'm still not sure about that but the PCI device is a "LSI Logic / Symbios Logic MegaRAID (rev 01) which apparently does have kernel/driver support and I can see it when I run lspci.

---

### Post by k-shavlov on 2016-12-14
Hi everyone. Had just the same issue with HP Proliant dl380 gen 5. I use UltraISO to burn the CD/DVD image on usb-flash. Windows Server 2008 and 2012 booted fine from usb and installed. Now i need to install Ubuntu Server 16.04. But while booting it says that the error occured and nothing on. Tried to make bootable flash with unetbootin. It works fine with any other PC but not with that HP server. Googled through the problem. They say i need to switch RAID-controller to AHCI mode. But i don't have such an option neither in motherboard bios nor in RAID-controller add-on rom. Can anyone give me a hand with this case? Thank you in advance.

UPD: just tried to make bootable usb with Ubuntu Server 12.04. It started the installation but failed copying files saying there's an error occured while trying to access cd-rom. It's actually usb-drive. Before it i tryed to boot from usb-cdrom and that didn't work too. That's sad. Don't even have any idea about what to do.

UPD: Ubuntu Server 10.04 on usb-drive also booted and started the installation but failed copying files saying there's a problem with cd-rom. Has anyone installed ubuntu on this server successfully?

---

### Post by upsidedowncandy on 2016-12-29
Managed to get my server set-up but in reply to K-Shavlov... Had a little look in the Manual for the Server you're trying to set up and did a control+f search for AHCI with no hit's? maybe your motherboard doesn't support it.

I say that because on a HP desktop I'm using it say's the following about AHCI.

Enhancing existing Vista or Windows 7 images from IDE mode or native AHCI mode
Vista and Windows 7 have a native AHCI driver. If Vista or Windows 7 was installed while in IDE mode, a registry change
will allow users to gracefully switch to AHCI mode using the Microsoft driver. See the Microsoft Knowledge Base Article
at [http://support.microsoft.com/kb/922976/en-us](http://support.microsoft.com/kb/922976/en-us) .
Corporate IT may be able to update an existing Vista or Window 7 image that was created in IDE mode to use the Intel
AHCI driver. The process requires inserting the Intel AHCI drivers into the image in a pre-installation environment using
the appropriate OS Tools.
Required software to insert the Intel AHCI driver:
&#8226; Windows Preinstallation Environment (WinPE) CD
&#8226; Windows OPK (OEM Preinstallation Kit) CD
&#8226; PKGMGR.EXE (Package Manager)
The OPK CD is not available for general download. It must be obtained through a Microsoft authorized distributor.
PKGMGR.EXE is a tool that installs, uninstalls, configures, and updates features and packages for Vista and Windows 7. 

Maybe it's gimped :/

Edit: Or maybe the setting is the "SATA Emulation Type" in either bios.

---

