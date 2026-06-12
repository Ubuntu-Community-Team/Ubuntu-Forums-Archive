---
title: "driver for SAS controller to install ubuntu 10.04 in IBM system x3550 M3"
date: 2012-05-14
forum: Server Platforms
---

### Post by manishrajbhandari on 2012-05-14
While installing Ubuntu10.04 in IBM system x3550 M3 hard disk is not detected. I think we need to install SAS controller driver inorder to detect hard drive. Do anyone have the driver. Help me.

---

### Post by mörgæs on 2012-05-14
Hi, welcome to the fora.

Why are you installing 10.04 and not 12.04?

---

### Post by madverb on 2012-05-14
Have you checked the IBM website for a driver?

---

### Post by manishrajbhandari on 2012-05-14
I am using  ubuntu 10.04 because there are some application which is designed and fully supports only in ubuntu 10.04

---

### Post by manishrajbhandari on 2012-05-14
Yes I have checked IBM site for the driver but there iare no drivers for ubuntu.

---

### Post by mörgæs on 2012-05-15
> **manishrajbhandari said:**
> I am using  ubuntu 10.04 because there are some application which is designed and fully supports only in ubuntu 10.04

But does the basic 12.04 install (only the vanilla OS, no extra applications) work well?

---

### Post by SeijiSensei on 2012-05-15
I've installed Ubuntu 10.04 server on a Dell box with a SAS controller; the driver was included in the image in installed by default.

If you're having problems installing Ubuntu, I suggest giving CentOS 6 a try.  It might contain the driver you need.  You don't need to install the image; just boot off a [LiveCD]("http://www.gtlib.gatech.edu/pub/centos/6.2/isos/i386/") and see if the device is detected.

---

