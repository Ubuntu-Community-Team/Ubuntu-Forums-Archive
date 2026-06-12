---
title: "Camera and microphone"
date: 2012-01-07
forum: System76 Support
---

### Post by daniel.cotter on 2012-01-07
Hello,

System 76 laptop with integrated camera and microphone, running Ubuntu 11.10.  Started with 10.10 and have upgraded twice.  I don't know if either of them ever worked, though I am assuming they did when it was purchased new almost one year ago.

I want to use Skype, but neither device is working, and I have no software to check them.  Can anyone tell me how to troubleshoot this to find out if they work or not, and how to "turn them on"?  I can't find any installed software that uses a microphone or the camera.

```
dmesg returns:
process `skype' is using obsolete setsockopt SO_BSDCOMPAT

lsusb returns:
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 413c:3200 Dell Computer Corp. Mouse
Bus 002 Device 004: ID 147e:1000 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 002 Device 005: ID 5986:0343 Acer, Inc 

```Can't tell version information for Skype, but it is the newest, downloaded and installed today
Thanks for whatever help you can offer.
Daniel

---

### Post by oldos2er on 2012-01-07
Thread moved to System76 Support.

---

### Post by daniel.cotter on 2012-01-07
Not that anyone was clamoring to post answers, but I did get the devices working.  The microphone was simply an input volume setting, and I turned the camera on by telling Skype to start video automatically.

So false alarm, but thanks for reading.
Daniel

---

