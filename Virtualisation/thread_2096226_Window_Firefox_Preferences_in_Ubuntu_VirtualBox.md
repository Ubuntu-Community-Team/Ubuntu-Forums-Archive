---
title: "Window Firefox Preferences in Ubuntu VirtualBox"
date: 2012-12-19
forum: Virtualisation
---

### Post by Arjani on 2012-12-19
Hi All, 
The window inside Ubuntu for the settings of Firefox is not completely visible. I cannot scroll down completely or see the whole window. 
I need to change some Firefox network settings which I use inside Ubuntu inside Oracle VM VirtualBox. 
Hope there is someone who can help me out. 

Thank you in advance! 

Kind regards

---

### Post by Ms. Daisy on 2012-12-19
You need to install the Guest Additions in the virtual machine. That will allow for better mouse capture, resizing the VM, sharing files, and using cd drives, etc.  Download it from here:

[http://download.virtualbox.org/virtualbox/4.2.6/Oracle_VM_VirtualBox_Extension_Pack-4.2.6-82870.vbox-extpack](http://download.virtualbox.org/virtualbox/4.2.6/Oracle_VM_VirtualBox_Extension_Pack-4.2.6-82870.vbox-extpack)

Here is the virtualbox manual section regarding installing Guest Additions. Make sure you follow the appropriate installation directions for the _guest_ operating system:
[http://www.virtualbox.org/manual/ch04.html#idp11577648](http://www.virtualbox.org/manual/ch04.html#idp11577648)

---

### Post by Ms. Daisy on 2012-12-19
Additionally you mentioned that you wanted to fix something network related in the virtual machine's firefox.  Have a look at the virtual network portion of the manual. One of the benefits of a vm is that networking becomes very easy to reconfigure in a moment.

[http://www.virtualbox.org/manual/ch06.html](http://www.virtualbox.org/manual/ch06.html)

---

