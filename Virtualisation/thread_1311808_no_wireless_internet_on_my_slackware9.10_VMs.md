---
title: "no wireless internet on my slackware/9.10 VMs"
date: 2009-11-02
forum: Virtualisation
---

### Post by muteXe on 2009-11-02
Hi,
Running virtualbox 3.0.8. Since updating to this version both my ubuntu 9.10 and slackware 13 VMs no longer have internet access.  The host system is ubuntu 8.04, on a wireless internet connection.
  
I keep reading that I have to do some port forwarding. Is this true?  They both worked ok with my last version of virtualbox.

Cheers in advance,

mute

---

### Post by T.R. on 2009-11-19
I second this. Just installed Slackware in virtualbox and can't get it connected. It's only Slackware that can't connect - Damn Small Linux and XP (only for messing around with, I swear!) both connect fine, haven't tested OpenBSD (segfaults constantly during install, but that's another thing altogether).

I'm on Ubuntu 9.10.

---

### Post by T.R. on 2009-11-25
I got it: you need to enable IP forwarding in Slack. Run as root:
```
sysctl -w net.ipv4.ip_forward=1
sysctl -p /etc/sysctl.conf
```If you don't have /etc/sysctl.conf, you'll need to create it and put
```
net.ipv4.ip_forward = 1
```in it. HTH

---

### Post by muteXe on 2009-11-29
You star.  Sorry it's taken so long to reply.  I shall try this when i get home tonight!

Thanks again,

mute

---

### Post by muteXe on 2009-11-29
No luck i'm afraid.  Tried your commands, and adding the config file in /etc/ but still didnt get internet working. Also tried a restart too.
Thanks anyway mate,

mute

---

