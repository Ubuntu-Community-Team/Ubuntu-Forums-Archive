---
title: "Installing Ubuntu Touch: Terminal stuck at unlocking stage"
date: 2016-11-05
forum: Ubuntu Phone and Tablet
---

### Post by alpeace89 on 2016-11-05
Hi,

I am following the install instructions for Ubuntu Touch ([https://developer.ubuntu.com/en/phone/devices/installing-ubuntu-for-devices/](https://developer.ubuntu.com/en/phone/devices/installing-ubuntu-for-devices/)) but I am stuck at the unlocking stage.

I have got as far as 'Unlock the Android device'.

```
lsusb
```

gives me.

```

Bus 002 Device 024: ID 12d1:256a Huawei Technologies Co., Ltd. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 13d3:5710 IMC Networks UVC VGA Webcam
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Then...

```
adb reboot bootloader
```

Turns the phone screen black and it says ```
=>FASTBOOT mode ...
```

Then...

```
fastboot devices
```

gives me...

```
WT98360    fastboot


```


So I then go for the unlock...

```
sudo fastboot oem unlock
[sudo] password for alex: 
...

```

but it gets stuck at this stage. I have left it for over an hour and it still says the same. Any thoughts on this are appreciated

Cheers,

Alex
p.s. I am attempting to install it on a Huawei Y3.

---

### Post by alpeace89 on 2016-11-10
When I try this using a HTC Desire I get:

```
alex@alex-K54C:~$ sudo fastboot oem unlock
...
(bootloader) [ERR] Command error !!!
OKAY [  0.004s]
finished. total time: 0.005s

```

---

