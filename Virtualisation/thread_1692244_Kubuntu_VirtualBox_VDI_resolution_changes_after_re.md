---
title: "Kubuntu VirtualBox VDI resolution changes after reboot!"
date: 2011-02-21
forum: Virtualisation
---

### Post by Rytron on 2011-02-21
Hi.

I have installed Kubuntu 10.10 in VirtualBox. Guest additions was installed and after a reboot I got the full resolution for my monitor (1360x768).

However I noticed that future VDI reboots cause the resolution to change to 1152x846 (image 1). How can I make it stay permanently at 1360x768 (image 2)?

Thanks.

---

### Post by Rytron on 2011-02-21
Just found the solution:

I got it [here]("http://askubuntu.com/questions/3205/higher-screen-resolution-in-virtualbox")

```
sudo apt-get install virtualbox-ose-guest-utils virtualbox-ose-guest-x11 virtualbox-ose-guest-dkms
```

---

