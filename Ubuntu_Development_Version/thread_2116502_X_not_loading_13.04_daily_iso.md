---
title: "X not loading 13.04 daily iso"
date: 2013-02-16
forum: Ubuntu Development Version
---

### Post by cafejunkie on 2013-02-16
Hello everyone.

I tried out 13.04 in a VM and then a quick wubi install and was very impressed so I wanted to do an actual install. When I boot from the USB I can see the splash screen but then the screen just goes black.

At that point I am able to get to a tty. When I look at the Xorg log it says

"screen(s) found but none have a usable configuration"

My GPU is an Nvidia GT520, works fine on 12.10 and below. I tried booting with nomodeset and that just caused the system to completely freeze after the boot splash (black screen, can't switch to tty, etc have to hard power off).

Had anyone else ran into this and found a way to solve it?

Thanks.

---

### Post by cariboo on 2013-02-16
When booting from a usb device, at the initial screen (the one with the little man and keyboard), press any key, select your language, and then at the menu, press F6 and select nomodeset, you should now be able to boot to the desktop, the resolution will be off, but you should be able to install Raring.

---

### Post by cafejunkie on 2013-02-16
> **cariboo907 said:**
> When booting from a usb device, at the initial screen (the one with the little man and keyboard), press any key, select your language, and then at the menu, press F6 and select nomodeset, you should now be able to boot to the desktop, the resolution will be off, but you should be able to install Raring.

Thanks for the reply.
I tried that and the system booted to a black screen still except I was unable to even switch to a tty, it was just frozen.

---

### Post by cafejunkie on 2013-02-16
Hmm, I just re created the usb and tried with nomodeset and it worked that time. Thanks!

---

