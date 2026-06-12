---
title: "Ubuntu VM issue"
date: 2021-08-18
forum: Virtualisation
---

### Post by peter-1984 on 2021-08-18
Hi,
Currently Ubuntu is one Virtualbox guest machine. I do not know why its screen is rather small. Before this, everything is fine on it. Where to adjust its resolution?

---

### Post by guiverc on 2021-08-18
You've not provided any release details, but I'll provide

[https://help.ubuntu.com/stable/ubuntu-help/look-resolution.html.en](https://help.ubuntu.com/stable/ubuntu-help/look-resolution.html.en)

Note: being a VM, the resolutions are limited to whatever the HOST settings allow; ie. if you can't get what you want, settings on your HOST OS & VM configuration may require change, and the VM to then be restarted.

(*I've also assumed Ubuntu Desktop, and not Ubuntu Server or other Ubuntu product*)

---

### Post by monkeybrain20122 on 2021-08-18
To installl/update the guest additions.

[https://itsfoss.com/virtualbox-guest-additions-ubuntu/](https://itsfoss.com/virtualbox-guest-additions-ubuntu/)

---

### Post by QIII on 2021-08-19
Moved to Virtualization.

Your thread was originally placed in a chat area, not a technical support area.

---

### Post by peter-1984 on 2021-08-19
Hi,
Thanks to all. What to further select to adjust OS resolution?

---

### Post by MAFoElffen on 2021-08-19
Like was mentioned, but not explained, if you install the Virtual Box Additions to the Guest... among other integration abilities, it will add hooks to better graphics options, which one of those helps with the guest being able to recognize that the resolution can be changed. That is step #1...

At the moment, without that, the guest only see's a limited box that it lives in, including just a basic VGA monitor.

Note that the version of the Guest Additions neds to be the same version asthe VirtualBox that you have installed. Find that in "About."

---

### Post by peter-1984 on 2021-08-19
Hi,
I have issue below to mount the Virtualbox addition to Ubuntu.


> Unable to insert the virtual optical disk C:\Program Files\Oracle\VirtualBox\VBoxGuestAdditions.iso into the machine Ubun18.04(Python) Hd5.












Could not mount the media/drive 'C:\Program Files\Oracle\VirtualBox\VBoxGuestAdditions.iso' (VERR_PDM_MEDIA_LOCKED).




Result Code: E_FAIL (0x80004005)
Component: ConsoleWrap
Interface: IConsole {872da645-4a9b-1727-bee2-5585105b9eed}
Callee: IMachine {85632c68-b5bb-4316-a900-5eb28d3413df}






---

### Post by MAFoElffen on 2021-08-20
You didn't follow the instructions from post #3...

If you follow the link to the tutorial, it shows you exactly which menu item in the VirtualBox Guest Manager to select, which installs it automatically... not mounted from the Guest...

---

### Post by peter-1984 on 2021-08-22
Hi,
How about the error attached below?[https://ubuntuforums.org/attachment.php?attachmentid=289031&stc=1](https://ubuntuforums.org/attachment.php?attachmentid=289031&stc=1)

Currently the Ubuntu version is 18.04.

---

### Post by ajgreeny on 2021-08-22
Try installing ***build-essentials, linux-headers and dkms*** packages in your VM which I think will help you overcome this problem.

---

### Post by peter-1984 on 2021-08-22
Hi,
Can you help to issue like




due to this command?


sudo apt install build-essential dkms linux-headers-generic

---

### Post by deadflowr on 2021-08-23
How long has that been running?
The lock issue is shown to be caused by the dpkg program already being in use by the unattended-upgrade program.
But that usually only lasts until the unattended-upgrades are finished installing any packages marked  to be upgraded.

---

### Post by peter-1984 on 2021-08-23
Can you help to issue below?

---

### Post by coffeecat on 2021-08-23
@peter-1984, I've removed the large image from each of your last two posts, leaving the clickable thumbnails. Other staff members have done the same with two previous posts. Please do not add the large images - thumbnails suffice.

---

