---
title: "virtualbox and usb wireless mouse problem"
date: 2009-04-21
forum: System76 Support
---

### Post by lshell on 2009-04-21
I just purchased a System76 Pangolin. I have installed virtualbox on it. I am having trouble capturing and un-capturing my usb wireless mouse in the guest (Windows XP) window. It is very erratic at best. Once I am able to capture the mouse, I have trouble un-capturing it. Any idea as to what is causing this problem? Thanks.

---

### Post by 3Miro on 2009-04-21
There might be something related to the Virtual Box OSE lack of USB support. Which version did you install? The one in the repos or from the Virtual Box web-page.

Also, what exactly does it do?

---

### Post by lshell on 2009-04-22
I installed the Closed-source version (non-OSE). To capture the mouse pointer in the guest window, I select from the window menu

Devices->USB Devices->Microsoft [0007]

The right-control button should perform an un-capture of the mouse, but it doesn't. I must shutdown Windows XP running in the guest window to un-capture the mouse.

---

### Post by lshell on 2009-04-22
I found my problem. I had not installed the Guest Additions. Everything seems to be working find now. Thanks for your help 3Miro.

---

