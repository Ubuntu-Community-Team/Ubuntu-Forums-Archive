---
title: "Bluetooth issue"
date: 2017-11-14
forum: Ubuntu Development Version
---

### Post by erkiha on 2017-11-14
After upgrading to bionic, bluetooth seems to crash. It finds my keyboard at first but disconnects in couple of seconds:

Nov 14 09:28:36 siil kernel: [ 2315.711841] hid-generic 0005:046D:B342.0008: input,hidraw7: BLUETOOTH HID v42.00 Keyboard [Keyboard K380] on f0:d5:bf:10:84:b5
Nov 14 09:29:02 siil kernel: [ 2342.396312] Bluetooth: Failed to disable LE scan: status 0x0c

has anybody seen similar things, any suggestions?

br, erki

---

### Post by erkiha on 2017-11-19
Found a workaround described here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1721271](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1721271)

adding

options iwlwifi bt_coex_active=0 swcrypto=1 11n_disable=8
or
options iwlwifi bt_coex_active=0

to /etc/modprobe-d/iwlwifi.conf

makes bluetooth work again.

Another solution is to downgrade to 4.12 kernel.

---

### Post by JoelParke on 2017-11-23
I too investigated this issue.
I found that the first solution: 
[COLOR=#000000]options iwlwifi bt_coex_active=0 swcrypto=1 11n_disable=8
gave poor wifi connection speed on my System76 laptop with excellent Bluetooth headset performance.

SO then I tried:
[/COLOR]options iwlwifi bt_coex_active=0
which worked well - much better wifi connection speed with excellent Bluetooth performance.

I then upgraded to the 4.14.1 kernel in the hope that the wifi-bluetooth issue would have been resolved.  But no such luck.
And I still needed:
options iwlwifi bt_coex_active=0
But on the Wifi 5Ghz network, I have excellent wifi speed AND excellent bluetooth performance. (and am not certain that the kernel change was necessary).
I was too lazy to downgrade the kernel, since I have a fine solution I left things with the new kernel.  

In case anyone else finds the need to shift to the most recent kernel, here is the script:

(Note MAKE sure this is the correct architecture for your system) - and all the other versions of the kernel are listed in the mainline directory. 

#!/bin/bash
cd /tmp
wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.14.1/linux-headers-4.14.1-041401_4.14.1-041401.201711210430_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.14.1/linux-headers-4.14.1-041401_4.14.1-041401.201711210430_all.deb)
wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.14.1/linux-headers-4.14.1-041401-generic_4.14.1-041401.201711210430_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.14.1/linux-headers-4.14.1-041401-generic_4.14.1-041401.201711210430_amd64.deb)
wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.14.1/linux-image-4.14.1-041401-generic_4.14.1-041401.201711210430_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.14.1/linux-image-4.14.1-041401-generic_4.14.1-041401.201711210430_amd64.deb)
echo Everything is downloaded. Time to install.
sudo dpkg -i linux-headers-4.14.1-*.deb linux-image-4.14.1-*.deb
echo Type sudo reboot to restart your system with the new kernel.

---

### Post by erkiha on 2017-11-23
This is currently work in progress in upstream, following kernel bug describes it better:
[https://bugzilla.kernel.org/show_bug.cgi?id=197147](https://bugzilla.kernel.org/show_bug.cgi?id=197147)

---

### Post by Chanath on 2017-11-23
> **JoelParke said:**
> [COLOR=#000000]
gave poor wifi connection speed on my System76 laptop with excellent Bluetooth headset performance.
[/COLOR]


If the laptop is System76, then the distro in it is Pop! OS, which is based on Ubuntu 17.04 Zesty. So, did you upgraded it to Bionic?

---

