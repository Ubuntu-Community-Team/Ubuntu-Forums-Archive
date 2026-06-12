---
title: "VMware Workstation 12 Pro grinds to halt on all VMs"
date: 2016-02-14
forum: Virtualisation
---

### Post by louisallen on 2016-02-14
After using VMware workstation 12 pro for about 10mins on a fresh Ubuntu 15.10 host, the guest VM (Windows 10 x64) will start locking up until it pretty much grinds to a halt and even opening a folder will take up to 5mins.

Host hardware:
OS: Ubuntu 15.10 x64
CPU: Intel i5 4200m
RAM: 8GB
HDD: 120GB SSD
GFX: Nvidia GTX 760M

Things I have tried:

[LIST]
[*]Rebooting the guest, it is immediately just as slow.
[*]Removing guest antivirus.
[*]Booting up another guest VM (Ubuntu 13.04 and Windows 7) runs just as slow. **It affects ALL guests.**
[*]Changing guest CPU allocation from 2 to 1 changes nothing.
[*]Changing memory allocation from 2GB to 4GB.
[*]Removing all unnecessary hardware such as sound card, floppy drive, 3d acceleration etc does not have an effect.
[*]I have VMware tools installed within all guests.
[*]Host CPU virtualization is enabled.
[*]A number of settings within workstation have been tested.
[/LIST]

What's interesting is if I reboot the host, and start up VMware Workstation 12 again, the guest VM is fast again - for about 10mins.

It appears to be something with Ubuntu as the host as I have ported these machines over to a Windows host and they do not have these issues?

---

### Post by MAFoElffen on 2016-02-15
Not saying I know what is going on with you and your's-- I don't have VMWare Workstation installed here. But I do have a server with vSphere.

Having vSphere, I do visit the VMWare forums occasionally. I remember from the VMWare forum that this also happened with VMWare Workstation 11 when it was first released. 

As I remember ... there were improvements that they released, that had to have some tuning done to them to work some things out with first... that caused the same performance problems. I think what they did was to revert their VM's back to capatability to the previous version, thus, not taking advantage to those new versions enhancements. The VM's immediately were fine again. They did that until they worked out what was going on was worked out.

Did you try that with one of your VM's?

---

### Post by louisallen on 2016-02-16
Will try this tonight, although I'm sure one of the other VM's (win 7) is running on the older hw version 10/11. 

Thanks

---

### Post by louisallen on 2016-02-16
Tried dropping the hardware version down to 11 and it appears to have worked. The VM has been running now for 2 hours without issue.

Thanks for the tip.

---

### Post by MAFoElffen on 2016-02-16
Glad I could help. It doesn't usually take then long after the release to work out those problems... so at least now you how a workable solution to keep you going until them.

Please go to the top of page, to the link in the upper right: "Thread Tools" > "Mark as Solved" .. so that others with the same issues can find a solution faster.

---

