---
title: "Virtual box cannot clone, cannot resize"
date: 2014-01-22
forum: Virtualisation
---

### Post by saias on 2014-01-22
Hi all,

I copied some files into a shared (ubuntu/windows) folder which apparently excided my fixed hdd on the virtual box. After that i received the following error 
Result Code: NS_ERROR_FAILURE (0x80004005).

After searching online the proposed solution was to clone the vdi, then resize the hd and create a new one. I tried cloning which gave me a 

VBoxManage: error: Details: code VBOX_E_FILE_ERROR (0x80bb0004), component Medium, interface IMedium

assuming this is a size error i tried to resize but apparently i cannot since i am using fixed space... this is the error i am getting

VBoxManage: error: Resize hard disk operation for this format is not implemented yet!

i really dont know what to do next... 

any help is really appreciated!

---

### Post by oldos2er on 2014-01-23
Moved to Virtualisation.

---

### Post by TheFu on 2014-01-24
I didn't search for that error to confirm anything, but 

Step 1: if you just need to make a larger virtual HDD, do it inside the VBox GUI as a 2nd drive. 

Step 2: Then boot with any liveCD (add the ISO under the vbox storage) - gparted.iso would be a good choice

Step 3: then clone the contents of everything in the 1st vHDD into the 2nd. Doesn't really matter how you do it - dd, ddrescue, partimage, some cloning tool - I don't care.  If you do it at the device level (/dev/sda --> /dev/sdb) then the old partition table, partitions and swap, and all the UUIDs, etc will be cloned too. This is good. 

Step 4: Use gparted to increase the size of the new vHDD partition. Or do any other partition level work ... perhaps deleting the swap and recreating it at the far right-hand side of the vHDD?  If you delete the swap, you'll need to fix that in the /etc/fstab after booting, since a new UUID will have been created.

Step 5: Shutdown and remove the old vHDD from the VM settings, so only the newer one is left to the VM.

Step6:  Boot into the new vHDD - see more space.

Step 7: Be happy.

---

