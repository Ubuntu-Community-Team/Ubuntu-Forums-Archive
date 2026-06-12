---
title: "Ratel will not let me into the boot menu nor bios settings"
date: 2011-03-04
forum: System76 Support
---

### Post by StephenDavison on 2011-03-04
I've run into my first issue with a new Ratel Ultra.  Sometimes the startup menu (bios settings, update flash, boot menu) doesn't even appear when I turn it on, and never from reset/reboot.  Furthermore, even when the initial menu appear, any key press or press and hold just boots from the hard disk instead of taking action indicated by the function key pressed.

I was able to access the boot menu to boot from a USB thumb drive earlier this evening, but now it behaves as described above.  Anybody else run into this on a Ratel Ultra?

Edited to add:
Tried many more times.  Sometimes I can get into the BIOS settings, but never into the boot menu: it just goes to the grub menu (yes, I turned off the hidden menu timeout).

---

### Post by AlexMason on 2011-03-04
Can you boot from live cd? If so, this might be useful for you: [http://www.pendrivelinux.com/boot-from-usb-without-bios-support-via-plop-cd/](http://www.pendrivelinux.com/boot-from-usb-without-bios-support-via-plop-cd/)

Also have you tried to spam the key that boots into the menu? if not spam whatever key it is from the time you hit the power button till the time it does its thing... if that dont work choose a different key and spam that.

---

### Post by isantop on 2011-03-04
I talked with this customer over the phone, and we think it's a BIOS issue. We're going to have a look at it.

---

### Post by StephenDavison on 2011-03-04
Alex, good point: since it will let me into the BIOS settings (but not the boot menu), I'll try changing the boot device order and see if that will let me update to the BIOS from a USB drive.

Thanks isantop; I am getting good support from S76.

---

### Post by AlexMason on 2011-03-05
Not a problem, just glad i can help.

I had to use PLoP boot manager before on a old system that was not capable from booting a usb.

---

### Post by jr223 on 2011-03-05
> **StephenDavison said:**
> I've run into my first issue with a new Ratel Ultra.  Sometimes the startup menu (bios settings, update flash, boot menu) doesn't even appear when I turn it on, and never from reset/reboot.  Anybody else run into this on a Ratel Ultra?

Edited to add:
Tried many more times.  Sometimes I can get into the BIOS settings, but never into the boot menu: it just goes to the grub menu (yes, I turned off the hidden menu timeout).

Hi I have the same issue as well but with a different twist.
My Ratel Ultra will not let me in to the Bios 3 times out of about 5.
Even when I hold the F2 function key (bios) on boot, to the point I get a long post beep.
There is another issue I;m now faced with which I will post in a seperate message.

---

### Post by StephenDavison on 2011-03-05
jr223, thanks for the post.  Are you able to get the BIOS boot menu from F10?  Also, are you using HDMI or DVI?  Switching to DVI helped to fix the intermittent boot splash logo and menu.  I'm getting into the BIOS setting more reliably now.  For whatever it's worth, I updated the BIOS according to [https://bugs.launchpad.net/system76/+bug/621845](https://bugs.launchpad.net/system76/+bug/621845), but that doesn't seem to have helped.

---

### Post by jr223 on 2011-03-09
Yes I found a trick that seems to work.
I have put a CD/DVD in the drive before boot up.
Then I boot and hit F2/F10.
Then it seems to work.
I still think there is a bug.
3 out 0f 5 times when I see the boot up screen and hit F2 the bios does not come up.

It could be that I need to hold down the F2 key but I get keyboard POST when I tried this one time.
Also I noticed that if I hit F2 a couple of times I don't always get into the BIOS.

As an comparion I do the same thing on my spare PC and hit F2 when the message appears. Every time the bios settings come up no problem.

Thanks

---

