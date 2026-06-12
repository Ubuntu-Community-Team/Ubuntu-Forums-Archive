---
title: "block usb access"
date: 2010-12-23
forum: Security
---

### Post by pmohankumar on 2010-12-23
iam mohan,
iam working in IT company as trainee system administrator.
recently we migrated from windows to ubuntu.
we are using ubuntu 9.10 version OS
My doubt is: i want to block the usb drive (pen drive) access for security.
how to block usb access in ubuntu 9.10?

kindly reply

---

### Post by WthIteh on 2010-12-23
> **pmohankumar said:**
> iam mohan,
iam working in IT company as trainee system administrator.
recently we migrated from windows to ubuntu.
we are using ubuntu 9.10 version OS
My doubt is: i want to block the usb drive (pen drive) access for security.
how to block usb access in ubuntu 9.10?

kindly reply
You could see your usb storage driver here
```
ll /lib/modules/`uname -r`/kernel/drivers/usb/storage/usb-storage.ko
```
If you want to disable it, simply remove it.
**NOTE:** It is better to move it elsewhere (instead of removing it) so you could restore it easily.

---

### Post by karthick87 on 2010-12-23
[http://www.cyberciti.biz/faq/linux-disable-modprobe-loading-of-usb-storage-driver/](http://www.cyberciti.biz/faq/linux-disable-modprobe-loading-of-usb-storage-driver/)

---

### Post by SeijiSensei on 2010-12-23
Fill the USB ports with epoxy.  If you're serious about this, and don't expect to permit USB connections in the future, then making the ports physically inaccessible is the best approach.

---

### Post by pmohankumar on 2010-12-23
ll /lib/modules/`uname -r`/kernel/drivers/usb/storage/usb-storage.ko

where i can find above command.

anybody could tell the path to find this command.

---

### Post by AlphaNeil on 2010-12-24
ll is an alias for "ls -l". So you can use ls -l instead of ll.

---

### Post by cariboo on 2010-12-24
Just copy and paste the path in a terminal eg:

```
ls -l  /lib/modules/`uname -r`/kernel/drivers/usb/storage/usb-storage.ko
```

Will result in :

```
-rw-r--r-- 1 root root 124376 2010-12-21 20:14 /lib/modules/2.6.37-11-generic/kernel/drivers/usb/storage/usb-storage.ko
```

I'm running Natty, so your kernel version will be different.

---

### Post by t4thfavor on 2010-12-24
Can't you set permissions on the USB bus? I thought everything was a "file" in the good ol world of Unix's?

---

### Post by pmohankumar on 2010-12-24
ll /lib/modules/`uname -r`/kernel/drivers/usb/storage/usb-storage.ko

above code worked and usb loading is blocked.
i just cut and copied the file (usb-storage.ko) from storage to desktop, after rebooting, usb have been blocked.

thanks for all who are all reply to my doubt.

i was attracted by ubuntuforum due to its quick reply.

iam a learner.

i will keep in touch with ubuntuforum.

again meet in another doubt.

---

### Post by Dayofswords on 2010-12-24
dont forget to set a password on the bios and change it so they can boot from a CD or USB stick

---

### Post by HermanAB on 2010-12-24
Howdy,

You got all the wrong solutions above but TIMTOWTDI. 
:)

The right way, is to disable USB memory devices using Policykit.  There is a wizard for it somewhere, so it is just a click of the mouse to set it.

---

### Post by t4thfavor on 2010-12-24
You could also add that module to the blacklist, that way if you need to load it for administrative purposes, you still can, it just won't load on demand anymore.

---

### Post by tanapon on 2012-06-25
To Block :
sudo chmod 700 /media

To Unblock :
sudo chmod 755 /media

---

### Post by nothingspecial on 2012-06-25
[IMG]http://img845.imageshack.us/img845/6976/necro2.png[/IMG]

---

