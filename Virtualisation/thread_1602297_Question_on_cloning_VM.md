---
title: "Question on cloning VM"
date: 2010-10-21
forum: Virtualisation
---

### Post by satimis on 2010-10-21
Hi folks,

host - Ubuntu 1010 desktop 64-bit
VM - Ubuntu 1010 private enterprise cloud 64-bit
VBox - Version 3.2.10 r65523

I just finished installing the captioned OS creating a new VM, say aaa.vdi.  Its size is 200G.  I need to clone a VM but with smaller size of 100G.  I couldn't figure out how to do it.  Can I run following command to do it?

```

$ VBoxManage clonehd ~/.VirtualBox/HardDisks/aaa.vdi ~/.VirtualBox/HardDisks/bbb.vdi --format VDI --size 100000MB

```

Please advise.  TIA

B.R.
satimis

---

### Post by JustinR on 2010-10-22
> **satimis said:**
> Hi folks,

host - Ubuntu 1010 desktop 64-bit
VM - Ubuntu 1010 private enterprise cloud 64-bit
VBox - Version 3.2.10 r65523

I just finished installing the captioned OS creating a new VM, say aaa.vdi.  Its size is 200G.  I need to clone a VM but with smaller size of 100G.  I couldn't figure out how to do it.  Can I run following command to do it?

```

$ VBoxManage clonehd ~/.VirtualBox/HardDisks/aaa.vdi ~/.VirtualBox/HardDisks/bbb.vdi --format VDI --size 100000MB

```

Please advise.  TIA

B.R.
satimis

What kind of disk is it? Dynamic or Fixed size?

---

### Post by satimis on 2010-10-22
> **JustinR said:**
> What kind of disk is it? Dynamic or Fixed size?

Dynamic.  Thanks

B.R.
satimis

---

### Post by JustinR on 2010-10-22
> **satimis said:**
> Dynamic.  Thanks

B.R.
satimis

Hi,

Sorry - didn't need to ask that question - thought your were resizing the disk.

But yes - that command should work just fine - I believe that's the recommended way in the VirtualBox Manual.

---

### Post by satimis on 2010-10-22
> **JustinR said:**
> 
But yes - that command should work just fine - I believe that's the recommended way in the VirtualBox Manual.
Hi JustinR,

Thanks.

A further question.  How to change the size of the new .vdi created after finish?  Tks

B.R.
satimis

---

### Post by JustinR on 2010-10-22
> **satimis said:**
> Hi JustinR,

Thanks.

A further question.  How to change the size of the new .vdi created after finish?  Tks

B.R.
satimis

Hello,

If it's the Dynamic VDI - VirtualBox (not even VBoxManage) includes a easy way to resize those types of VDIs.

The solution would be to create a smaller .VDI (Fixed or Dynamic) and copy the disk contents from the other one to the smaller one.

1. Create the new, smaller hard disk file in the Virtual Media Manager in VirtualBox.

2. Create (or use) a VM and attach both hard disk VDI's (the old and new). 

3. Download something like [Clonezilla]("http://clonezilla.org/") or [Easeus Disk Copy]("http://www.easeus.com/disk-copy/") (I prefer Easeus Disk Copy - it's easier to use).

4. Attach the .ISO file into the CD-ROM drive in VirtualBox and boot it up.

5. Clone the older .VDI to the new, smaller, VDI.

Then your done!
Good Luck.

---

### Post by satimis on 2010-10-24
> **JustinR said:**
> 
1. Create the new, smaller hard disk file in the Virtual Media Manager in VirtualBox.


Hi,

OK.  I can do it on Oracle VM VirtualBox (GUI)

> 
2. Create (or use) a VM and attach both hard disk VDI's (the old and new). 


Sorry I don't follow.  Where to create this VM?  How can I attach 2 hard disk VDIs to it, the old HD VDI and new HD VDI created on 1) above.

> 
3. Download something like [Clonezilla]("http://clonezilla.org/") or [Easeus Disk Copy]("http://www.easeus.com/disk-copy/") (I prefer Easeus Disk Copy - it's easier to use).


What will be the use of this package?  TIA


B.R.
satimis

---

### Post by JustinR on 2010-10-24
> **satimis said:**
> Hi,

OK.  I can do it on Oracle VM VirtualBox (GUI)



Sorry I don't follow.  Where to create this VM?  How can I attach 2 hard disk VDIs to it, the old HD VDI and new HD VDI created on 1) above.



What will be the use of this package?  TIA


B.R.
satimis

Hi,

I'll explain what we have to do - because we can't resize the VDI using any tools - we have to do it manually by cloning the VDI to another (smaller or bigger) VDI.

The Clonezilla / Easeus Disk Copy software is a .iso file that we will attach to the VM which will guide you through cloning your VDI to another smaller/bigger VDI.

1. Create a new VM , the OS is just 'Linux'/'Other' with at least 256MB of RAM. When it asks your to create a hard drive, create the hard drive with the size you want the new hard drive to be (i.e. The size you originally wanted your other VDI to be).

2. When your finished with that, click the VM and press the 'Settings' button. Scroll over to storage, in the CD-ROM bay attach the Clonezilla or Easeus Disk Copy iso. Then click on the SATA controller and press the '+' sign with the disk under it to attach a second VDI. Click on the first hard drive and attach your original VDI (the one you want resized), click the second hard drive and attach the VDI you just created (the one thats the size you want). After thats done, press OK.

3. Start your VM and follow the instruction to clone your original VDI to the new (smaller or bigger) VDI.

After that's finished then your done! You've resized your VDI.
If you need any help, just ask!

---

