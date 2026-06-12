---
title: "Setting up wireless in Virtualbox"
date: 2008-09-19
forum: Virtualisation
---

### Post by winrowc on 2008-09-19
Hi I tried following [these]("https://help.ubuntu.com/community/VirtualBox?highlight=(VirtualBox)|(usb") instructions to set up Wireless networking with the proprietary version of Virtual Box. I got an error after i tried to apply the script though, and after searching for parts of the error in Google, I got nothing.

```
net.ipv4.ip_forward = 1
VBoxTunctl: option requires an argument -- 'u'
Create: VBoxTunctl [-b] [-u owner] [-g group] [-t device-name] [-f tun-clone-device]
Delete: VBoxTunctl -d device-name [-f tun-clone-device]

The default tun clone device is /dev/net/tun - some systems use
/dev/misc/net/tun instead

-b will result in brief output (just the device name)
Cannot find device "tap0"
Cannot find device "tap0"
```

It says it cannot find device tap0 but I thought that was supposed to be a virtual device...

Heres what the script looks like:

```
sysctl net.ipv4.ip_forward=1
VBoxTunctl -b -u $colin
ip link set tap0 up
ip addr add 192.168.1.5/24 dev tap0
parprouted wlan0 tap0
```

colin is my username, and I have a bcm43xx wifi card.

---

### Post by dark_phantom on 2008-09-20
For starters, you have $colin as if that was a variable instead of just colin.  Second, what are you trying to accomplish?  Bridging? If so then, the manual states that  bridging is not supported in most wireless network devices.

---

