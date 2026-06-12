---
title: "Backing up images from Virtual Machine Manager, question about permissions."
date: 2016-12-02
forum: Virtualisation
---

### Post by Frank_Snyder on 2016-12-02
[FONT=verdana]I have Ubuntu 16.04 and have recently setup a VM with 16.04 as well via Virtual Machine Manger. I'm using the GUI for the program. I want to backup the VM disk image externally so in case my machine ever fails I'll still be able to boot the iso in another instance.
[/FONT]
[FONT=verdana]I copied the disk image to another directory on my local machine to avoid damaging the original file in anything I was doing. To do so I used "cp -a /source/. /destination". I then used "chmod -R ugo+rw /imagefile/" to give full open permissions to the file. I did this to negate any possible permission issues in the process. I have the installation fully encrypted so I'm not terribly worried about it. I then hooked up a standard drive to a USB drive dock and proceeded to use "pv /source/ > /destination/" to copy it over to the drive.

[/FONT]
[FONT=verdana]So first I tried to import/open the image file in VMM directly from the drive on the dock. It gave me a few error prompts in the process that all were linked to permission issues and then ultimately failed importing. I ran "chmod -R ugo+rw /externaldrive/imagefile/" again to make sure permissions were completely open. I tried to mount it again with the same result. Next I used pv to copy the image file back from the external to the local machine. I then mounted the new copy residing on the local machine in the VMM and everything worked fine.

[/FONT]
[FONT=verdana]So either you can't mount from an external drive or there is something I'm not understanding about permissions here. Forgive me for my ignorance here, I'm still nothing near a linux guru. My main concern is losing this host system and going to try to mount the backup on another system only to never be able to use the VM image as permissions are tied to a then deceased and inaccessible account/machine.[/FONT]

---

### Post by TheFu on 2016-12-02
VMs need the XML file in addition to the "raw storage device(s)".  Did you get that?  **virsh dumpxml** is the command.  That XML specifies a specific location, network (like a bridge name), and perhaps CPU specific settings which might be different.

If the external drive isn't using a Linux file system ... well, there are likely going to be permissions issues.  xfat, vfat, fat32, NTFS will be issues.

I use VMM, but only to create new VMs and connect to a console during emergencies.  For networking and storage work on VMs, I do all that outside VMM to get full access to all the amazing tools.  VMM is a 60% tool, maybe less.

Curious as to which container type you are using for VMs?  qcow2, raw, something else?

There is little reason to make an image file 666.  It needs to be read-write for libvirt and/or root. Anything more is just a security issue.  Whole disk encryption only helps with the system is off, not when it is running.

---

### Post by Frank_Snyder on 2016-12-05
Yeah the external drive was the primary OS drive pulled from a Win7 machine. So I guess that would explain that. The file type is qcow2.

---

### Post by TheFu on 2016-12-05
So, if this is solved, please mark it such using the "thread tools". This helps folks trying to help you AND folks looking for an answer.  If not, a clear question is required, please.

---

