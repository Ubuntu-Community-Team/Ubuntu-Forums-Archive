---
title: "Log-in screen constantly refreshing, unable to log-in"
date: 2012-03-30
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by PaulW2U on 2012-03-30
I'm seeing a really horrible problem for the second time this week. On both occasions it's happened after updating the kernel.

After I've finished updating I reboot and select the new kernel version from the grub menu to get back into Unity. When the log-in screen is displayed it keeps getting refreshed and it is impossible to log-in. I can't switch to a tty as the log-in screen refresh takes control of my PC. All I can do is turn the PC off with the power switch. When this happened a few days ago I reinstalled and the problem disappeared until tonight's kernel update.

As this problem hasn't appeared on my Kubuntu installation I thought lightdm may be the problem as Kubuntu still uses kdm by default. gdm was already installed so I rebooted into text mode and did the necessary reconfiguration for gdm to be used as opposed to lightdm. The problem has disappeared, for now anyway.

My system specification is as per my signature and I'm using the open-source ATI driver.

I don't see anyone else having these specific problems although one or two other posts suggest something vaguely similar or related. I'm not too sure where to start looking for a bug report. Any ideas on where the problem might lie?


**Edit**: Bug report found - [https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/969589](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/969589)

---

### Post by grandtoubab on 2012-03-31
Hello
It affects me also, I boot in recovery mode then
[HTML]sudo dpkg -- remove ubuntu-desktop[/HTML]
[HTML]sudo dpkg --remove lightdm[/HTML]

then after a new reboot I am able to login using gdm

---

### Post by PaulW2U on 2012-03-31
A better way is

```
sudo dpkg-reconfigure gdm
```

and select gdm as opposed to lightdm. This leaves ubuntu-desktop in place.

---

