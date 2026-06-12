---
title: "Intel AC-3160 Firmware Update fixes Bluetooth"
date: 2014-03-30
forum: System76 Support
---

### Post by Greg_Whitmore on 2014-03-30
Hello, I'm a new owner of a Galago Ultrapro.  From day 1 (less than a week ago), the bluetooth would crash when attempting to pair devices.  Fixing it required the latest firmware from Intel for the AC-3160.

The firmware update is located at [http://wireless.kernel.org/en/users/Drivers/iwlwifi](http://wireless.kernel.org/en/users/Drivers/iwlwifi)

Scroll down to find the latest for the 3160

1. Using Archive Manager, extract **iwlwifi-3160-7.ucode**

2. sudo mv /lib/firmware/iwlwifi-3160-7.ucode /lib/firmware/iwlwifi-3160-7.ucode.old

3. sudo cp ~/iwlwifi-3160-7.ucode /lib/firmware/

4. Reboot and enjoy.

Notes: wifi seems to grab connections faster as well as bluetooth now functioning.  Tested with Galaxy Note 3, LG Headphones and PS4 controller.

Hopefully this will help others.

---

### Post by Nicolas_Ehrhardt on 2014-04-02
Hi,

I am using the ubuntu default bluetooth UI, which I think is also the Gnome one.
I experienced trouble lately after upgrading to the last kernel: the link seemed to be bad quality, and after unpairing, I could not repair, no matter what I tried (resets, messing with config files, you know...)

But this solved my issue!

I hope there is a way to pass that message to the System76 team so that they include the patch to their driver upgrade software.

Thank you so much for sharing!

---

