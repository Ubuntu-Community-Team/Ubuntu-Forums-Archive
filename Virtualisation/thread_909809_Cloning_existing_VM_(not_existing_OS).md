---
title: "Cloning existing VM (not existing OS)?"
date: 2008-09-03
forum: Virtualisation
---

### Post by dark_phantom on 2008-09-03
I don't know what I'm doing wrong, I thought it would be a simple task.  Here's what I want to do, but am running into the blue screen every time.

I have a VM in VirtualBox that I created from scratch a while ago, no problems ever since I created it.  I want to clone it to work on different things at once.  I created a clone via the following command.

VBoxManage clonevdi <existing_vdi_file> <new_vdi_file>

It successfully created a clone with a new UUID for the new vdi file, then I create a new VM from the wizard with the exact same settings as the original VM.  Then I go and run the new VM and it will always display the blue screen.

Any ideas what I'm doing wrong?

---

### Post by HermanAB on 2008-09-04
Here is the manual method:
Stop the VM
Copy the whole VM directory
Restart the VM
Start the new VM

Cheers,

Herman

---

### Post by dark_phantom on 2008-09-04
The VM is stopped, but why would I just copy the directory.  That would not work since it would have the same UUID, this is what the manual recommends as well (not to just copy it).  Also, there are two directories, one for the vdi and one for the configuration.  Your steps don't make sense, but thanks for replying.  Anyone else has some suggestions?

---

### Post by Shazaam on 2008-09-04
Did you read this?...
"Note that newer Linux distributions identify the boot hard disk from the ID of the drive. The ID VirtualBox reports for a drive is determined from the UUID of the virtual disk image. So if you clone a disk image and try to boot the copied image the guest might not be able to determine its own boot disk as the UUID changed. In this case you have to adapt the disk ID in your boot loader script (for example /boot/grub/menu.lst). The disk ID looks like scsi-SATA_VBOX_HARDDISK_VB5cfdb1e2-c251e503. The ID for the copied image can be determined with 

hdparm -i /dev/sda"

---

### Post by dark_phantom on 2008-09-04
Yes, I read that but did not know if it applied to my case or not.  Also, I have a fake raid setup so not sure how that would play out.

I guess I'm at a lost here as to how to approach this.

---

### Post by dark_phantom on 2008-09-05
Anyone?

---

### Post by dark_phantom on 2008-09-10
Update

In my older PC I still had VirtualBox 1.5.6 and I did the exact same thing that I did on version 1.6.6 without problems.  So, I wonder if it was disabled (or there's a different way to do it), or the amd64 version is different.

I don't know, but I'm a bit perplex why I could do it with an older version.  Still haven't tried with version 2, I guess I could try and find out.

Edit: How can I update the original post to show on the forum title?  I edited the first post, but did not reflect on the forum.

---

