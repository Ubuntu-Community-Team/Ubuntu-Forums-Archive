---
title: "Server RAID grub reinstall"
date: 2014-05-18
forum: Server Platforms
---

### Post by varun_sharma2 on 2014-05-18
Hi,

I've been facing a similar issue with Boot-repair, it continuously loops through the following message

"Filesystem repair requires to unmount partitions. Please close all your programs. Then close this window."

I have checked the logs and I am not sure any of the changes I am specifying are actually being made - so the error message is completely debilitating to the process. There is also an additional error message with regards to one of the device partitions being encrypted (not the one I am trying to boot into so I am tempted to ignore)

Basically I have a RAID10 setup to which I have copied over a previous installation of 12.04 (which had openstack + other personalisations made) I have been attempting to move this over to RAID10 for some time now but keep failing to do so because of GRUB.

I have the boot repair log from pastebin below:

[http://paste.ubuntu.com/7485917/](http://paste.ubuntu.com/7485917/)

Any assistance on this would be really appreciated as I am getting quite close to giving up on trying to recover my prior installation (the one which was on the encrypted device partition) sde5 and doing a fresh RAID10 install on with 14.04.

Cheers.

---

### Post by oldfred on 2014-05-18
Moved to your own thread.
Error may be related to RAID, but I do not know RAID.
And you have to mount the RAID giving you passphrase to unencrypt for it to find your installs /boot folder.

Did you have Boot-Repair reinstall grub to the RAID. You do not install to MBR of a drive.

---

### Post by varun_sharma2 on 2014-05-26
Hi,

Just to update on this, thanks for the advice, I did indeed get grub to start after installing it specifically on the RAID partition using Boot-Repair. But despite trying multiple things including Raid-Update I have been unable to get rid of the following error message on boot which interrupts the booting sequence.
error: file /grub2/i386-pc/raid.mod not found

---

### Post by oldfred on 2014-05-26
I do not use RAID.

But interestingly my 12.04 has raid.mod in /boot/grub. In 14.04 they moved the .mod files ito the i386-pc sub-directory and I only have raid5rec.mod & raid6rec.mod??

---

