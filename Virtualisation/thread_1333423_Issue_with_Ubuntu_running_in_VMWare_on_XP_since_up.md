---
title: "Issue with Ubuntu running in VMWare on XP since updates"
date: 2009-11-21
forum: Virtualisation
---

### Post by lister_infiji on 2009-11-21
So I have VMWare Workstation on XP and am running Ubuntu (Kubuntu for GUI) as a guest OS. I had not used this in 3 or 4 months, and loaded it up recently. I completed all updates through Kubuntu, and since doing so ran into several issues. I have now resolved all these for myself but for one.
 
I decided I needed to increase my partition size, and did so by following a VMWare/Ubuntu tutorial which involved using gparted from the LiveCD.
 
Since making this change I receive some failures on boot, and also receive the error:
 
[4.644651] powernow-k8: BIOS error - no PSB or ACPI _PSS objects.
 
I have read that this usually relates to the 64bit install of Ubuntu, but I will be honest that i don't remember which version I installed as it was so long ago, but may very well have been 64bit.
 
I also had a couple of other failures on boot. I looked up how to enable boot logging, and tried to set this up from the shell prompt I am presented when booting into the installation, but the file I need to edit is read only.
 
I then booted from the LiveCD, mounted the drive, and edited here, which indicated it had saved successfully. However, when rebooting into the installation, no log had been created and the changes I had made via the LiveCD to enable boot logging had been lost.
 
For my part, I'm just wanting to get back into Kubuntu so I can make some decisions about where to go with my PC. I have had some use of 7 over the past year, and have been considering switching to it. However, the latest Kubuntu (when I could access it) looked pretty slick, and I'm considering it as a serious competitor for my new host OS.
 
Any help would be appreciated. Both on the issue I've mentioned, and also how to successfully activate boot logging so I can look at what the boot failures were.

---

### Post by dcstar on 2009-11-21
> **lister_infiji said:**
> 
.........
Any help would be appreciated. Both on the issue I've mentioned, and also how to successfully activate boot logging so I can look at what the boot failures were.

Just look in the syslog file.

BTW, "errors" regarding power management issues in a VM are not errors, VMs cannot control the underlying physical hardware and messages like this should be disregarded.

---

### Post by lister_infiji on 2009-11-22
Well I do consider them errors when they prevent me from reaching an X session by default, and instead bring me to the shell prompt.  That in itself tells me something is not working correctly.  I viewed the syslog as you suggested and performed a search.
 
Faiures were in regards to Bluetooth (don't care) and in regards to last boot failing, which I consider irrelevent.
 
So my primary concern is the previously mentioned boot failure which prevents me getting into X (Kubuntu) on initial boot.

---

### Post by dcstar on 2009-11-24
> **lister_infiji said:**
> Well I do consider them errors when they prevent me from reaching an X session by default, and instead bring me to the shell prompt.  That in itself tells me something is not working correctly.  I viewed the syslog as you suggested and performed a search.
 
Faiures were in regards to Bluetooth (don't care) and in regards to last boot failing, which I consider irrelevent.
 
So my primary concern is the previously mentioned boot failure which prevents me getting into X (Kubuntu) on initial boot.

That message you are seeing is an irrelevant message because it just happens to be the last message on the text screen, it has nothing to do with the problems in your system. VMs cannot control the CPU on the host and that is basically all that is saying.

You need to confirm **exactly** what you did to "resize" the system.

---

### Post by lister_infiji on 2009-11-24
I followed the following guide:
 
[http://hubpages.com/hub/How-to-Increase-VMware-Hard-Disk-Space](http://hubpages.com/hub/How-to-Increase-VMware-Hard-Disk-Space)

---

### Post by dcstar on 2009-11-24
> **lister_infiji said:**
> I followed the following guide:
 
[http://hubpages.com/hub/How-to-Increase-VMware-Hard-Disk-Space](http://hubpages.com/hub/How-to-Increase-VMware-Hard-Disk-Space)

What a convoluted way to do something like this!

Anyway, from what I can determine there is a fair chance the UUID of the original system's partitions may be changed by this process.

If that has occured then you have to manually change the /etc/fstab file to reflect the changes so the system will boot correctly.

Other than that, the whole procedure may have fatally damaged your VM.

---

### Post by lister_infiji on 2009-11-24
I had already edited my fstab in regards UUID before I came to this forum without resolution..  If I have to reinstall then I will, because I want to see Kubuntu working fully..  But if you have any advice how I SHOULD increase disk space in future, then please advise.

---

