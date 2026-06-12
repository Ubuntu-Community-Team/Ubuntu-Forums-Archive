---
title: "Cannot Install Ubuntu in VirtualBox VM"
date: 2020-05-27
forum: Virtualisation
---

### Post by aakritibarat on 2020-05-27
Hi everybody,

I am brand new to Ubuntu and tried installing both Ubuntu 20.04 LTS as well as 18.04 LTS. The installation method I follow is as in -- [https://www.dev2qa.com/how-to-install-ubuntu-on-virtualbox-mac/](https://www.dev2qa.com/how-to-install-ubuntu-on-virtualbox-mac/)

Same settings - 2048MB, VDI..

So I create the VM in Virtual box first, then upload the image (....amd64.iso) I dowloaded from Ubuntu website and it starts installing then stops with errors. I cancel, retry installing, it runs a little further then stops again with errors.

Please forgive me, I don't know anything and I am just starting to learn. My laptop is MAC OS Catalina 10.15.5

Thank you
Aakriti

---

### Post by ActionParsnip on 2020-05-28
Did you MD5 test the ISO you downloaded?

---

### Post by wildmanne39 on 2020-05-28
*Thread moved to **Virtualisation for a more appropriate fit**.*

---

### Post by kneutron on 2020-06-25
--You should also upgrade to the latest version of Virtualbox, which as of this writing is 6.1.10

---

### Post by TheFu on 2020-06-25
Often, seeing a youtube video showing the install on the same hostOS as you have will make things clear.  Have you looked yet? Video can really help a beginner.

Avoid EFi boot, create a vdi that is 15G or more, use virtio for storage and network devices. Set the video RAM to the max allowed (128 MB). Those are standard recommendations.  i don't know anything about OSX, so the virtio stuff may not be possible.

---

### Post by SeijiSensei on 2020-06-26
Have you used this version of VirtualBox before?  Looks as much like a VirtualBox problem as a Linux one.  Especially since, as you say, you've tried installing both 18.04 and 20.04 images.

I'd try reinstalling VirtualBox.

---

