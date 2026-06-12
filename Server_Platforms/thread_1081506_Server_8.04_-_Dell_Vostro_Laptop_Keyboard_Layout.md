---
title: "Server 8.04 - Dell Vostro Laptop Keyboard Layout"
date: 2009-02-26
forum: Server Platforms
---

### Post by smc18 on 2009-02-26
Hi, I have setup a lab server installation in VMware on my Dell Vostro 1500 Laptop.

It seems all of my alphanumeric keys are working correctly, however the arrows keys, Page up, Page down keys etc are not working properly.

So using vi or accessing my command history is a bit challenging.


I've tried to change specify my keyboard layout using:

```
sudo dpkg-reconfigure console-setup
```

However, a Dell Vostro keyboard layout is not available, the other Dell layouts do not work properly either. (Besides the alphanumeric keys)

If I plug in a USB keyboard, the keys work fine on the USB keyboard of course.

I would like to just use my laptop keyboard, rather than using a USB keyboard.

Has anyone found a way to resolve this?  Any help is appreciated.

---

### Post by smc18 on 2009-02-27
.

---

### Post by smc18 on 2009-03-01
.

---

### Post by dwouters on 2009-05-16
I don't know if you have resolved this issue yet but I think your issue may be in the VM and not Ubuntu Server. You may want to check the keyboard layout the VM is using.

---

