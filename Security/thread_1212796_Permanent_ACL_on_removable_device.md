---
title: "Permanent ACL on removable device?"
date: 2009-07-14
forum: Security
---

### Post by wiresquire on 2009-07-14
Hi

I have a usb tv-tuner device that also can do fm radio.
When inserted, the tv device is correctly set up with an ACL (with me in it!) on /dev/video1. And it works!

It also sets up /dev/radio0 for the radio, but no ACL is set up, and only root can access it. I can set the ACL manually using setfacl (sudo setfacl -m u:wiresquire:rw /dev/radio0) and everything works, but when the device is removed, the ACL is lost. When I reinsert it, I'm back at square one. I could also 'cheat' and add myself to a group, but I'd rather have it consistent.

So, I would like to set up an ACL for /dev/radio0 when the device is inserted that is permanent. 

I've searched and seen some mention about udev etc, but that's when I start to get rather lost.

Can anyone help with some simple instructions/steps on how to do this?

TIA
ws

---

### Post by bodhi.zazen on 2009-07-14
You will probably need to make an entry in fstab for the removable device and manually mount it.

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

In the options column (4th column) add the options (as well as any others you wish):

```
user,acl
```

---

### Post by wiresquire on 2009-07-14
Thanks for the reply, but it's a removable usb tv tuner, not a stick, disk etc. AFAICT, it has no filesystem, and so fstab is not relevant?

ws

---

### Post by shaggy999 on 2009-07-16
Yeah, fstab is not relavent. But I think what you need to do is come up with a custom udev rule. Do a search for it. Hope this helps.

Just found this bit on the udev site:

> 
udev allows you to use additional assignments in rules to control ownership and permission attributes on each device.

The GROUP assignment allows you to define which Unix group should own the device node. Here is an example rule which defines that the video group will own the framebuffer devices:

    KERNEL=="fb[0-9]*", NAME="fb/%n", SYMLINK+="%k", GROUP="video"

The OWNER key, perhaps less useful, allows you to define which Unix user should have ownership permissions on the device node. Assuming the slightly odd situation where you would want john to own your floppy devices, you could use:

    KERNEL=="fd[0-9]*", OWNER="john"

udev defaults to creating nodes with Unix permissions of 0660 (read/write to owner and group). If you need to, you can override these defaults on certain devices using rules including the MODE assignment. As an example, the following rule defines that the inotify node shall be readable and writable to everyone:

    KERNEL=="inotify", NAME="misc/%k", SYMLINK+="%k", MODE="0666"


---

