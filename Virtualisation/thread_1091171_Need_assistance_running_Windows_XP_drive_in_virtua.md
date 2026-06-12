---
title: "Need assistance running Windows XP drive in virtual machine."
date: 2009-03-09
forum: Virtualisation
---

### Post by T3kG33k on 2009-03-09
I have a friend that I built a new computer for and installed Ubuntu 8.10.  Its been running flawlessly but there is an issue.  He's a quicken user and needs to be able to access his data.  This data happens to be in .QDF format which gnucash won't read.  There's 10 years worth of data on the old XP drive which is still bootable.  My question is this.

Is there any way to boot a bootable separate hard drive as a virtual machine in Ubuntu?

---

### Post by Dedoimedo on 2009-03-09
Hello,

Yes. Although I would recommend against mounting physical partitions in virtual machines as you can easily screw things up and cause massive data loss.

Dedoimedo

---

### Post by T3kG33k on 2009-03-09
> **Dedoimedo said:**
> Hello,

Yes. Although I would recommend against mounting physical partitions in virtual machines as you can easily screw things up and cause massive data loss.

Dedoimedo

SO it is possible!  I haven't been able to find a way how to do it.  Throwing all caution aside. How can it be done?

---

### Post by T3kG33k on 2009-03-09
Nevermind.  My brain appears to be missing today.  I found the sticky :oops:

---

### Post by NimoTh on 2009-03-30
Have you really? I have been searching now for the past few days but all the howtos I find seem to be for a previous version of VMWare Server. Mine is VMware Server 2.0.0 build-122956 and the steps for creating a new Virtual Machine are not at all like in the howtos. Can someone please help me to run my existing Windows XP (with IDE drive) from the new VMWare Server 2? I didn't yet figure out how to tell vmware to use my existing installation instead of creating a new one.

Thank you very much.
Martin

---

### Post by lewtwo on 2009-04-01
This is not exactly the answer that you are loking for but I have used it several time particularly in the case where I have an old windows machine with data or application that I could not afford to loose.

Ghost the old machine (or clonezilla) to a removable drive (2nd IDE hard disk, USB, whatever).

create a Virual Drive large enough to hold the image files.

Use an existing VM machine with XP.
Mount the new virtual drive  and a share where the images files are stored. 
Copy the images files to the new Virtual drive.

Createa new target virtual machine with:
1) CD image with Gost restore (or clonezila)
2) New blank target OS/application drive
3) Drive containing the image files

Do an image restore on the virtual machine.

It is a lot of trouble but once done you can backup the VM drive (a couple of times) and have the ability to move the old data/application as needed to new hardware, os etc. We have a very old DOS based ERP system (pre 2K ... its data goes back more than 20 years) that we still access for historical purposes via this method (see note below).

If you are using VMware they  have a free program that you can use to convert a running Windows based system to a VDMK (any version) file. QIMAGE can convert a VDMK file to QCOW2 for KVM/Qemu.



Interesting note:
The origonal ERP system hardware was the size (and weight) of a small refrigerator. The whole thing now fits on a USB stick.

---

### Post by NimoTh on 2009-04-01
Thank you, lewtwo, for that alternative way. However, I am looking for a solution that still lets me hard boot into Windows XP. When I need to work on a project for a longer period of time, I'd like to use the 'real' thing, so I want to boot Windows directly. The virtual machine is just for the case when I need to make a quick bugfix in Visual Studio or get overly fed up again with Skype and MSN alternatives in Linux.

Your solution or converting the physical to a virtual Windows leaves me with two independent Windows, right? I think that'd be too much of a hassle as well as a waste of disk space.

Thanks anyway, though.

---

### Post by lewtwo on 2009-04-01
Ok ...

I am not sure about KVM (i think that is on the roadmap).

VM Workstation should be able to do it according to their manual. At one time we used VM Server 1.X with native partitions (Windows NTFS) but they would eventially get corrupted by the host OS and require a restore.

---

