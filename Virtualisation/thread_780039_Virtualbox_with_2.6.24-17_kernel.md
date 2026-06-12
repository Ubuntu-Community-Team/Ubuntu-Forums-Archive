---
title: "Virtualbox with 2.6.24-17 kernel"
date: 2008-05-03
forum: Virtualisation
---

### Post by Anthony M on 2008-05-03
Is there a virtualbox module for the -17 kernel yet? All I can find in Synaptic is for the -16 kernel. I received the update to go to the -17 kernel and now virtualbox will not work.

Thanks!

---

### Post by FredB on 2008-05-03
You may have proposed repository enabled.

I have no 2.6.24-17 on my computer, and my apt database is up to date.

---

### Post by Super R on 2008-05-04
Hello,

I have the same problem. I accidentally left the proposed repository on after searching for something else, and when the kernel update came through, I didn't realize that it was only proposed. Is there a way to get 2.6.24-16 back or get an update for virtualbox that works with 2.6.24-17?

Thanks for your time,
Super R

---

### Post by eznet on 2008-05-06
You should still have the '.16' kernel available in GRUB.  Just select it to boot from for now - if you don't want to select it at every boot, just edit your menu.lst (ALT+F2 'gksudo gedit /boot/grub/menu.lst') and select .16 as the default to make it boot by default.

Is that an option for you?

I accidentally pulled the '.17' update as well and have just been booting this way until the module is released.

-Matt

---

### Post by Super R on 2008-05-06
Thanks eznet! That worked:) Do you know if we will still get the update when it comes in?

---

### Post by eznet on 2008-05-07
Yes, when it hits the official repositories it should pull as usual.  In short, this was our fault for having the proposed repositories enabled.  Likely, when the proposed is approved and moved to the main repos, the associated modules will be made available as well.

Best of luck,

-Matt

---

### Post by Anthony M on 2008-05-07
According to this:
[https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose-modules/+bug/226753](https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose-modules/+bug/226753)

The package is waiting for approval but should be in the repository shortly!

---

### Post by KipBond on 2008-05-26
kernel 2.6.24-17 is now in hardy-updates, so I got it this morning.  virtualbox-ose-modules only has the 2.6.24-16 version, so it no longer works.  I'm guessing it will be updated soon... until then, I just changed /boot/grub/menu.lst to boot the old kernel.

---

### Post by KipBond on 2008-05-28
I just checked, and virtualbox-ose-modules-2.6.24-17 is now in hardy-updates.  :)

[UPDATE]
I had to boot using the 2.6.24-17 kernel, then re-install the virtualbox modules for it to work.

---

### Post by seetho on 2008-05-28
I did not have "Proposed updates" checked, but I still was offered 2.6.24-17 yesterday.  :confused:

---

### Post by Glucklich on 2008-05-28
> **KipBond said:**
> I just checked, and virtualbox-ose-modules-2.6.24-17 is now in hardy-updates.  :)

[UPDATE]
I had to boot using the 2.6.24-17 kernel, then re-install the virtualbox modules for it to work.

This didn't worked for me. I didn't find the 2.6.24-17, it just keeps showing the 2.6.24-16 ones.
Can you say in more detail how did you find the virtualbox-ose-modules-2.6.24-17 ?

---

### Post by Glucklich on 2008-05-28
Did it. I had the Portuguese Server option. Just turned it to the Main Server. Thanks for the tip. Didn't even needed reboot.

---

