---
title: "Ubuntu server installation error: debootstrap program exited with an error return val"
date: 2014-03-20
forum: Server Platforms
---

### Post by vedioboy on 2014-03-20
So here's exactly what happened. I was doing the setup and everything was going good. I am using a usb by the way. I used [Universal USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") to make it bootable with linux. I got to the partition manager and set the partition to use full disk guided, etc... Then it started installing the base system and it hanged at 2% for about 5min then it gave me this error: debootstrap program exited with an error (return value 1)

Anybody have any idea what this could be? Is it a harddrive problem or install usb problem?

---

### Post by sudodus on 2014-03-20
Which version are you installing, 12.04 LTS, 13.10 or Trusty Tahr?

I'm not sure that Ubuntu Server 12.04 LTS installs OK from USB even if it does work properly from CD or DVD. I know that Ubuntu Server and Ubuntu mini.iso version 13.10 work well from USB.

I suggest that you use another tool to create the USB install drive, for example Unetbootin or mkusb. See this link for more details

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by vedioboy on 2014-03-20
Thanks for the suggestion, I'll do that as soon as I get home. I'll post again here if I run into the problem again.

---

