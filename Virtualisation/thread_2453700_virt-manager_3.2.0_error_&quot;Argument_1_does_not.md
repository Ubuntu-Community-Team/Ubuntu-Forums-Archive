---
title: "virt-manager 3.2.0 error &quot;Argument 1 does not allow None as a value&quot;"
date: 2020-11-15
forum: Virtualisation
---

### Post by franknfurter2 on 2020-11-15
Hello,

yesterday I managed to get virt-manger 3.2.0 to start on my ubuntu 18.04 LTS. Before I had to install some modules but it starts at the end without error. I also was not even able to start it, the installation worked as well.

But today, when I was digging deeper in, I get the following error, when I hit the VIrtIO Disk 1 item in the details page of a machine:

[HR][/HR]
Error reloading device page: Argument 1 does not allow None as a value

Traceback (most recent call last):
  File "./virtManager/details/details.py", line 1724, in _refresh_page
    self._refresh_disk_page(dev)
  File "./virtManager/details/details.py", line 2017, in _refresh_disk_page
    self._addstorage.set_dev(disk)
  File "./virtManager/device/addstorage.py", line 325, in set_dev
    self.widget("disk-removable").set_active(removable)
TypeError: Argument 1 does not allow None as a value

[HR][/HR]
I did not get this error with version 2.2.1 but get it again with version 3.1.0

Any advice?

Regards

Frank

---

### Post by ajgreeny on 2020-11-15
Where did these versions 3.2.0, and also 3.1.0 come from, and how did you install them?

---

### Post by franknfurter2 on 2020-11-16
I took the link provided at [https://virt-manager.org/download/](https://virt-manager.org/download/) . It guided me to [https://releases.pagure.org/virt-manager/](https://releases.pagure.org/virt-manager/). Problem now is, that I cannot uninstall 3.1.0 and install 2.2.1. I do not know how to uninstall and when I try to install 2.2.1 it fails. So I have to install intltool. With intltool installed I can install but not run. There are more errors then. I get stuck a bit.
I did the installing in terminal in the folder, where I extracted the version. I run "sudo ./setup.py install" as described in the documentation. You know, I know what RTFM means :P Or for testing purposes just "./virt-manager"

---

### Post by ajgreeny on 2020-11-16
Unfortunately I can not see how to uninstall either. Instructions are often included in the readme file, but not in this case, and I can't find anything in any of the other files in the source, so can not really help you.

A careful read through of the python script used to install might give you more clues but I'm afraid that apart from the comment that it usually installs virt-manager to /user/local I can find very little else.  Have a look in that folder and see if it's sitting there.

---

### Post by franknfurter2 on 2020-11-20
I opened a bug in the GitHub repository of virt-manager for this two days ago. No reaction until now.

---

