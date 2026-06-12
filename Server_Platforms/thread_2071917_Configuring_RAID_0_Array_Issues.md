---
title: "Configuring RAID 0 Array Issues"
date: 2012-10-16
forum: Server Platforms
---

### Post by souar on 2012-10-16
Hey, new to all this so sorry for such a simple question

I'm trying to build a simple file,print,web,mail server but run into issues configuring the RAID on the installation! 

I go to manually partition the drives and set each of the 1TB drives to have the maximum level of space set to 'physical volume for RAID' (not bothering with SWAP since I have 8gb's of RAM and doubt it would use all that a need more, would it?). So do this for both drives go to configure raid software, click 'Create MD device' select RAID 0 (I want maximum space and this seems the best way) but when I try and select the active devices for the array I move the box to the first RAID volume hit enter but it just takes me back to the 'Create MD device' screen? 

I'm not sure what Im doing wrong but any help would be fantastic!!

Thanks, Souar

---

### Post by darkod on 2012-10-16
First of all, making selections in a text menu is done with the Space bar, and the * sign will show to confirm it's selected.
Hitting Enter is the same as OK and closing the menu with no selection made.

Second, and more important, I think for softraid 0 you need a /boot partition outside the array, because the boot files can't be split and raid0 is splitting the data. Unless they made changes in the latest versions but I think not.

So, first you will need to make for example 500MB partition on both disks. You might as well mark it as raid partition too. Then create another big raid partition from the rest of the disks.

When configuring the raid devices, make one raid1 (mirror) from the small partitions, and then make that device ext4 with mount point /boot.
Then configure the other raid device as raid0 from the bigger partitions.

---

### Post by souar on 2012-10-16
Wellll that's mildly awkward ha! That makes a lot more sense, use the spacebar! Thank you.

Okay that all seems pretty simple and clear. Just one thing I want to make sure of, if I have one 'drive' running as RAID 1 for the boot as you said and the other as RAID 0 for storage will the server recognise both of them and allow me to use the storage array like a normal drive on windows? I ask this because when I had two drives installed on the desktop version I partition one for the system and then it would only recognise the other partition and other whole drive just like memory sticks and not actual installed drives and this is not what I want! 

Thanks

---

### Post by darkod on 2012-10-16
I'm not sure I understood you correctly, but I think the question was whether windows will be able to see the Samba shares on the raid0 array. Yes, it would.

Windows and other ubuntu machines are seeing just the shares themself. They don't care on which filesystem and actually on top of what that share is running.

Inside your big raid0 array (device) you will make folders, and in Samba create the shares. All machines inside your network will be able to see them.

Note that raid0 doesn't have any redundancy. If one disk dies, you lose all the data. So if this is very important data I wouldn't run raid0.

---

