---
title: "Ubuntu server version 24.04 version fails to boot on Raspberry Pi after poweroff"
date: 2024-11-10
forum: Server Platforms
---

### Post by ujjwalrathod007 on 2024-11-10
Hello,

I have installed Ubuntu from RaspberryPi imager and could not start it after the device is poweroff. I think that it is lost somewhere in the boot process.
Then I have to run some commands

fskc -y /dev/mmcxxx
exit

Then it runs fine after again booting the pi. I have one more RaspberryPi running 23.04 version that do not have this issue. I think this issue is of software itself and not anything else.

---

