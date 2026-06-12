---
title: "How to disable Usb port in ubuntu 9.10"
date: 2010-03-09
forum: Security
---

### Post by IMadhavan on 2010-03-09
Hi
I need disable usb port access in ubuntu9.10.
Anyone can help me how to disable usb port in ubuntu9.10

---

### Post by cariboo on 2010-03-09
Do you want to physically disable the ports , or just restrict access?

---

### Post by IMadhavan on 2010-06-02
Hi
 I want just restrict access only.
Please say for Ubuntu 10.04 also

---

### Post by cariboo on 2010-06-02
You could remove the user from the plugdev group:

```
gpasswd -d <user> plugdev
```

---

### Post by IMadhavan on 2010-06-03
Hi

Thanks For your valuable reply. And one more i want to share with you.If its possible to install Ldap server with Ldap users and Groups in ubuntu any of the version from 8.04 to 10.04.
I have tried lot of things for this But I couldn't. I believe you can with some documents. I have already tried Ubuntu server Guide and many Of them. Kindly reply with Some suggestion. 


Thanks in advance

---

### Post by AlexanderDGreat on 2010-10-24
Doesn't work for me, using Lucid Lynx 32bit. Try shutting down and leave USB attached to cpu, when you login to Desktop, it's there!

---

### Post by SeijiSensei on 2010-10-24
Try adding "blacklist usb_storage" in /etc/modprobe.d/blacklist.conf and rebooting.  That should disable the use of USB drives.  If you want to disable the ports entirely, you'd probably need to blacklist additional kernel modules.  Run "lsmod | grep usb" to see a list of the installed modules with "usb" in their names.  In my case I have the HID input device modules for mice/keyboards, USB sound drivers, and drivers for my USB wifi adapter.

---

### Post by cariboo on 2010-10-24
> **AlexanderDGreat said:**
> Doesn't work for me, using Lucid Lynx 32bit. Try shutting down and leave USB attached to cpu, when you login to Desktop, it's there!

How are you testing this, are you logging on a a limited privilege user? What are the permission of the usb drive mount point?

---

### Post by AlexanderDGreat on 2010-10-24
@cariboo907 - Hi, I just logged-in as the sudoer of the computer. Removed users from plugdev group, and when I boot to the ordinary user, USB is mounted.

But I've found a solution already : [http://www.cyberciti.biz/faq/linux-disable-modprobe-loading-of-usb-storage-driver/]("http://www.cyberciti.biz/faq/linux-disable-modprobe-loading-of-usb-storage-driver/")

However, even this tutorial missed something, so I have to add a little more code, in rc.local, please look at comment 15.

I wonder, am I doing something wrong? Is my Ubuntu install corrupted? Is this a bug?

PS blacklist usb_storage also doesn't work for me.

---

### Post by cariboo on 2010-10-24
If the usb device is still connected, then you may have to adjust the permissions, in oder to keep other users out. For instance if the drive is formatted as ext4 and your main user is the owner, set the file permissions to 700, so that only root and the owner have access.

If the drive isn't plugged in can your limited permissions user plug  it in and access it?

---

### Post by AlexanderDGreat on 2010-10-25
> If the drive isn't plugged in can your limited permissions user plug it in and access it? - Not anymore by following the tutorial at cyberciti, and also removing usb-storage.ko.

---

### Post by karthick87 on 2010-10-26
> **SeijiSensei said:**
> Try adding "blacklist usb_storage" in /etc/modprobe.d/blacklist.conf and rebooting.  That should disable the use of USB drives.  If you want to disable the ports entirely, you'd probably need to blacklist additional kernel modules.  Run "lsmod | grep usb" to see a list of the installed modules with "usb" in their names.  In my case I have the HID input device modules for mice/keyboards, USB sound drivers, and drivers for my USB wifi adapter.

It works fine in ubuntu 10.04 :)

---

### Post by AlexanderDGreat on 2010-10-27
> It works fine in ubuntu 10.04  have you tried leaving the USB on the port and rebooting your computer?

---

### Post by karthick87 on 2010-10-27
> **AlexanderDGreat said:**
> have you tried leaving the USB on the port and rebooting your computer?

Just now i have checked,still the usb port is enabled..How come possible..?Actually wats happening here..?

---

### Post by AlexanderDGreat on 2010-11-01
OK, here's what you should do.

```
sudo mv /lib/modules/(uname -r)/kernel/drivers/usb/storage/usb-storage.ko /home/sudoer/
```

What this does is to remove the module from the kernel so when you plug a USB, in layman's terms, the kernel won't have any resources to actually detect it.

If you want to put it back on, just ```
sudo mv /home/sudoer/usb-storage.ko /lib/modules/(uname -r)/kernel/drivers/usb/storage/
```

Finally, to stop it from mounting at boot time. Just add this before the exit 0 to your /etc/rc.local script. This script is the final script Ubuntu launches before giving you your desktop:

modprobe -r usb_storage

Let me know if this works for you. It surely does for me in LUCID LYNX. Yeah baby! :)

---

### Post by karthick87 on 2010-11-01
> **AlexanderDGreat said:**
> OK, here's what you should do.

```
sudo mv /lib/modules/(uname -r)/kernel/drivers/usb/storage/usb-storage.ko /home/sudoer/
```What this does is to remove the module from the kernel so when you plug a USB, in layman's terms, the kernel won't have any resources to actually detect it.

If you want to put it back on, just ```
sudo mv /home/sudoer/usb-storage.ko /lib/modules/(uname -r)/kernel/drivers/usb/storage/
```Finally, to stop it from mounting at boot time. Just add this before the exit 0 to your /etc/rc.local script. This script is the final script Ubuntu launches before giving you your desktop:

modprobe -r usb_storage

Let me know if this works for you. It surely does for me in LUCID LYNX. Yeah baby! :)


Yes this is working :)

---

### Post by suresh_vandiyur on 2011-03-21
> **karthick87 said:**
> Yes this is working :)
Hi,

All running this sudo mv /lib/modules/(uname -r)/kernel/drivers/usb/storage/usb-storage.ko /home/sudoer/ i got this error
bash: syntax error near unexpected token `('


please help me

Thank you,

Regards,
Suresh

---

### Post by tredegar on 2011-03-21
Try:
```
sudo mv /lib/modules/[COLOR="Red"]$[/COLOR](uname -r)/kernel/drivers/usb/storage/usb-storage.ko  /home/sudoer/
```

---

