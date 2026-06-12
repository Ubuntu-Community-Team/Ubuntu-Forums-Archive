---
title: "VirtualBox and Vista Guest Bluescreen / BSOD"
date: 2009-07-10
forum: Virtualisation
---

### Post by {CGL}ToWeR on 2009-07-10
Hello

Ive been using Jaunty 9.04 and managed to install Virtualbox 3.0.0 and whilst I can create a new VM with the Vista Install DVD and that boots and works fine, I cannot complete the migration of a Vista VMware vmdk file.

The VM's symptons are:
1) Boots to vista login
2) can crash there or post login
3) crash is bluescreen with some error message and it dumps some tinfo to a file, then resets itself, and repeats / loops the problem on next boot.

The crashes seem to change in messages, several of them are:
rdr_file_system rdbss.sys
Fs_rec.sys
pagefault in non page area tcpip.sys
msfs.sys

Other important info:
 - This was an exported vmware appliance, although the fact that i get to login screen means I think the VMDK file is ok
 - The Vista VM boots in safe mode fine
 - vmware tools is still installed, I cant remove it from programs/features in safe mode, but I disabled them in msconfig

Has anyone experienced the above?

Can anyone point me to a vmware to virtualbox migrate guide?

cheers

---

### Post by Perryg on 2009-07-11
Try version 3.0.2 which was released yesterday and see if helps.  There were several OVF and VMDK areas repaired (indicated in the change log).

You may get it to work by disabling the VMWare additions as you say you have done, but I have never gotten it to work with them installed.  Also pay close attention to the virtual network adapter.  Windows is touchy about this especially Vista.  Try setting it to the IntelPro/1000 T server.

---

### Post by {CGL}ToWeR on 2009-07-12
Tried enabling network iface with IntelPro/1000 T server, then disabling altogether. Also disabled audio and usb. Still same effect.  Will try new version asap and report result later.

thanks

---

### Post by {CGL}ToWeR on 2009-07-14
Nope Virtualbox 3.0.2 has same symptons.  I cant see anywhere in changelog about vmdk changes?

OK given most blue screens are about 'fs' or 'file system' Id say the problem is that this is a SCSI virtual disk and I need to convert to IDE if I want to run the vmdk directly in vbox.

Some hints given here:
[http://forums.virtualbox.org/viewtopic.php?f=2&t=10154](http://forums.virtualbox.org/viewtopic.php?f=2&t=10154)

Which makes sense except the vmware infrastructure client gui for the ESXi wont allow me to add IDE hard disks, just SCSI ones.  So try something else...

Convert VMDK to VDI for virtualbox perhaps?
right, so running QEMU 0.10.0 ...

> qemu-img convert -f vmdk ./ovm1.vmdk -O raw ovm1.bin 
qemu-img: error while reading

No dice.  

Any other help anyone?

---

### Post by {CGL}ToWeR on 2009-07-14
Fine, Ill solve it myself :p

Step 1: Convert the exported vmdk to pre-allocated disk

On my ubuntu system that meant using vmware-tools
> vmware-vdiskmanager -r ovm1.vmdk -t 2 ovm2.vmdk

Disk type '2' is a vmware 'pre-allocated disk' rather than a 'growable disk'
Also on my system it outputted a *-flat.vmdk file for some reason, so Ill use this.


Step 2: Convert to VMDK to Raw

This is where qemu finally played nice...
> qemu-img convert ovm2-flat.vmdk -O raw ovm1.bin 


Step 3: Convert Raw to VirtualBox VDI

> VBoxManage convertfromraw ovm1.bin ovm1.vdi


Step 4: Install the new .vdi hardisk in your VM. 
Here, whilst powered off, go to Settings->Hard Disks->Attachments and add the new .vdi file.
-  Ensure under 'Slot' it says IDE Primary Master, 
-  Uncheck 'Enable Additional Controller'
- IDE COntroller Type is PIIX4 like they say everywhere else on the web

and basically no SATA / SCSI / AHCI / buslogic slilogic stuff is set/on.

-Click OK and run the VM

My vista then booted fine, took a short while but the HDD icon was flashing a healthy green whilst booting which wasnt happening before.  

All bluescreens have completely gone now.  If you're still getting these after converting vmdk to vdi, and set the hard disk to IDE I would really like to know!

---

### Post by Viet Le Quang on 2009-08-15
Dear {CGL}ToWeR,
 
Thank you for sharing the information.
 
These steps worked fine for me. It helped resolve my problem of BSOD appearing after converting a Windows 2003 Server container from VMware to VirtualBox on Ubuntu 9.04.
 
The flat file as well as the .bin file were taking up the full allocated disk space therefore I deleted them as I went, while the final .vdi file was only taking the real space used so was a lot smaller in size. The conversion took about 10 minutes for each step on a 20GB container, running on a Dell PowerEdge 2950 with 2 dual core CPUs. 
 
In my case the conversion was done as root so "chgrp" and "chown" were also applied to the final .vdi otherwise VirtualBox could not open it from the GUI interface.

---

### Post by gOLdenHaWK3D on 2009-08-16
Have you kept both as 32-bit/64-bit, both host and guest operating systems should be of the same "bits" :confused:

---

### Post by {CGL}ToWeR on 2009-08-16
> **gOLdenHaWK3D said:**
> Have you kept both as 32-bit/64-bit, both host and guest operating systems should be of the same "bits" :confused:

To have a 64 bit guest, your host needs to be 64 bit.  Your CPU needs to support hardware virtualisation. Your BIOS needs to have an option or by default enable your cpu to do this.  See this thread

[http://ubuntuforums.org/showthread.php?t=730912](http://ubuntuforums.org/showthread.php?t=730912)

---

### Post by Perryg on 2009-08-16
> **{CGL}ToWeR said:**
> To have a 64 bit guest, your host needs to be 64 bit.  Your CPU needs to support hardware virtualisation. Your BIOS needs to have an option or by default enable your cpu to do this.  See this thread

[http://ubuntuforums.org/showthread.php?t=730912](http://ubuntuforums.org/showthread.php?t=730912)

Actually you can run a 64 bit guest on a 32 bit host but the machine must support hardware virtualization.  Also remember that there is some overhead doing this and the extra speed that you would achieve may not be as much as you would think.

---

### Post by UnOriginal on 2009-10-12
@  [FONT=&quot]{CGL}ToWeR: That totally works. Thanks dude.
[/FONT]

---

