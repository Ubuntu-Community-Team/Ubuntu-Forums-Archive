---
title: "How do I access shared folders via Guest Additions in Sun Virtual Box from Ubuntu?"
date: 2009-06-02
forum: Virtualisation
---

### Post by Rytron on 2009-06-02
Hi.
I have installed Ubuntu 8.10 in Sun Virtual Box. I did this to create a .vdi file that is handy to have. I have installed guest additions but I don't see how to access my shared folders. I have selected my desktop and documents folders as two shared folders on my host OS.

Do I need to use one of these commands?
VBoxClient
VBoxClient-all
VBoxContro

---

### Post by namaku0 on 2009-06-02
On VirtualBox main window, open Help by pressing F1
(or Help > Contents...), go to chapter 4.6.

There is also a guide about installing Guest Additions
at chapter 4.3.

> 
mount -t vboxsf [-o OPTIONS] sharename mountpoint


---

### Post by Rytron on 2009-06-02
Hi.
I have dkms installed on both the Ubuntu host and Ubuntu guest operating systems. I think that is the correct method? I have Guest Additions installed on the Ubuntu guest OS.
I want to share my Documents folder of the host Ubuntu OS with the guest Ubuntu OS. I'd like it to be mounted on the Desktop of the guest Ubuntu OS.

How should this code be modified to do the above?

```
mount -t vboxsf [-o OPTIONS] sharename mountpoint 
```

---

### Post by namaku0 on 2009-06-03
When you configure a folder to share in VirtualBox,
you give it a name. Now lets assume the name is
"hostdesktop". Open Terminal in guest OS, try the
following line:

mount -t vboxsf  hostdesktop /home/guestusername/Desktop

---

### Post by Rytron on 2009-06-03
> **namaku0 said:**
> When you configure a folder to share in VirtualBox,
you give it a name. Now lets assume the name is
"hostdesktop". Open Terminal in guest OS, try the
following line:

mount -t vboxsf  hostdesktop /home/guestusername/Desktop

Perfect. Works a charm. Is there a possibility of a GUI interface? I guess I could just use 
```
sudo nautilus
```
to access the Shared folder via a GUI interface.
One strange this was that when I created a folder and a document on my guest OS, the same folder and file appeared on my host OS!

---

