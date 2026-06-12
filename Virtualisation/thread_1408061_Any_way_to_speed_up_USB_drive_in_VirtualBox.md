---
title: "Any way to speed up USB drive in VirtualBox?"
date: 2010-02-15
forum: Virtualisation
---

### Post by sync00 on 2010-02-15
Copying data to a USB drive in VirtualBox is taking about 20 times longer than doing it in the host. I tripled the amount of memory allocated to the vm and it didn't make any difference.

---

### Post by HermanAB on 2010-02-16
Howdy,

Mount the USB schtick on the host then access it over SSH from the guest.

---

### Post by sync00 on 2010-02-16
It is a hard drive. Does that make any difference?

---

### Post by Morbius1 on 2010-02-16
You didn't say what OS was the host and what OS was the guest.

If it's a Linux host / Windows guest then you could try this:

_LINUX HOST_
Using the VBox application create a Shared Folder to **/media**:
    Folder Path:  /media
    Folder Name:  hostmedia ( or whatever you choose )

_WinXP GUEST_
Open Explorer ( the file manager) or My Computer

Select **Tools**
Select **Map Network Drive**
Drive: Select an available Drive Letter
Folder: Select Browse. You will notice that there is a listing titled VirtualBox Shared Folders. Within that will be the shared folder "hostmedia" you created above.
check **Reconnect at login**

Every time you boot into the WinXP guest your shared folder created from /media will show up as a drive letter. Within that will be any usb device mounted on the linux host . Now you're not using the VBox USB process, you're using the VBox internal networking process.

There's also a side benefit. You'll always know who is in charge of the mounted / unmounted device - it's always the host.

---

### Post by sync00 on 2010-02-16
I'm using Windows host and Linux guest.

I'm copying from an ntfs partition on one drive to an ext3 partition on another drive. I can only share the ntfs partition. I tried that and it was slow. Then I tried adding the drives as usb devices in VB and it was still slow.

---

