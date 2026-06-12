---
title: "virtualbox 2.0.2 no usb support ? .... HELP"
date: 2008-10-12
forum: Virtualisation
---

### Post by smooth3006 on 2008-10-12
ok i have virtual box installed in ubuntu 8.04 and vista which is running on my virtual machine does not pick up my pda connected via a usb cable ? how can i resolve this ?

---

### Post by bazzam on 2008-10-12
> **smooth3006 said:**
> ok i have virtual box installed in ubuntu 8.04 and vista which is running on my virtual machine does not pick up my pda connected via a usb cable ? how can i resolve this ?

I haven't gotten round to doing this myself yet, but this is from the FAQs.

[http://www.virtualbox.org/wiki/User_FAQ](http://www.virtualbox.org/wiki/User_FAQ)

"USB on Ubuntu/Gutsy: Ubuntu removed support for /proc/bus/usb/*. We will address this issue in the future. Until this, edit the script `/etc/init.d/mountdevsubfs.sh and activate the four lines around line 40 (Magic to make /proc/bus/usb work). Then execute 
/etc/init.d/mountdevsubfs.sh start
From now on, there should be a directory /proc/bus/usb/ and the device entries below should be accessible by any user. "

Let me know if it works.

---

### Post by smooth3006 on 2008-10-12
> **bazzam said:**
> I haven't gotten round to doing this myself yet, but this is from the FAQs.

[http://www.virtualbox.org/wiki/User_FAQ](http://www.virtualbox.org/wiki/User_FAQ)

"USB on Ubuntu/Gutsy: Ubuntu removed support for /proc/bus/usb/*. We will address this issue in the future. Until this, edit the script `/etc/init.d/mountdevsubfs.sh and activate the four lines around line 40 (Magic to make /proc/bus/usb work). Then execute 
/etc/init.d/mountdevsubfs.sh start
From now on, there should be a directory /proc/bus/usb/ and the device entries below should be accessible by any user. "

Let me know if it works.

thanks but i went with vmware for linux now and its working. :KS

---

### Post by bazzam on 2008-10-12
Just out of interest which version of VMware are you using. I have an older version which still works quite well but don't know if its worth upgrading. Please let me know what you think of it.

---

### Post by smooth3006 on 2008-10-13
> **bazzam said:**
> Just out of interest which version of VMware are you using. I have an older version which still works quite well but don't know if its worth upgrading. Please let me know what you think of it.

6.5 workstation and i love it. i can even sync up my wm pda now.

---

