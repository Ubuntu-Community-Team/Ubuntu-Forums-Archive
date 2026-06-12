---
title: "VirtualBox Ubuntu VM display settings"
date: 2010-05-25
forum: Virtualisation
---

### Post by sdaniels6363 on 2010-05-25
Hello, I have a Macbook, and have successfully installed Ubuntu 10.04 in VirtualBox.  I am having an issue with screen resolution, I tried to edit the xorg.conf file, however it's not in my VM's file system.  I would like to get the resolution to 1280x800, so that I may use the VM in fullscreen mode.  How may I go about doing this?  Any help is greatly appreciated, thanks in advance.

---

### Post by boonenoob on 2010-05-26
to change your display to something besides 800 by 600, you have to install vbox guest additions. go to the "devices" tab on the window(or on mac, use the top bar with "file, edit, etc") and click "install guest Additions..." this will put a virtual cd on your virtualization. go to the "places" tab in ubunto and click on VBOX ADDITIONS. click "open autorun prompt", and install it. after this is finished, restart your virtual box and you will be able to have more resolution options. hope this helps.

---

### Post by sdaniels6363 on 2010-05-26
That worked! Thank you very much.

---

### Post by boonenoob on 2010-05-26
no problem! glad I could help! :D

---

