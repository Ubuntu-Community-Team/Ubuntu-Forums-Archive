---
title: "UFW stats unactive at startup in Ubuntu 16.04"
date: 2016-10-24
forum: Security
---

### Post by napalm2016 on 2016-10-24
Hello, dear friends.
I have use Ubuntu 16.04 LTS.
I want to ufw start active state at startup.
Now situation is:
- **ufw enable** [I]Firewall is active and enabled on system startup
- [/I]**systemctl status ufw.service**[I]
ufw.service - Uncomplicated firewall
   Loaded: loaded (/lib/systemd/system/ufw.service; enabled; vendor preset: enabled)
   Active: active (exited) since  2016-10-24 10:17:32; 1h 32min ago
 Main PID: 266 (code=exited, status=0/SUCCESS)
   CGroup: /system.slice/ufw.service
&#1086;&#1082;&#1090; 24 10:17:32 laptop systemd[1]: Started Uncomplicated firewall.
Warning: Journal has been rotated since unit was started. Log output is incomplete or unavailable.
- [/I]**systemctl**[I]
- ufw.service loaded active exited    Uncomplicated firewall
[/I]- **reboot**
- **ufw status** [I]Status: inactive (after reboot)


[/I]Can`t understand why after reboot ufw status - [I]inactive?
[/I]Plz help me with this issue.
Thanks.

---

### Post by Jimiteru on 2017-03-05
I'm encountering exactly same issue on Ubuntu 16.04 LTS server I installed recently in VPS.
I've been surfing web for a while about this, but couldn't get a convincing answer for this situation.

My situations:

cat /etc/os-release
 
NAME="Ubuntu"
VERSION="16.04.2 LTS (Xenial Xerus)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 16.04.2 LTS"
VERSION_ID="16.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
VERSION_CODENAME=xenial
UBUNTU_CODENAME=xenial

sudo ufw version

ufw 0.35
Copyright 2008-2015 Canonical Ltd.

sudo systemctl is-active ufw
-> active
sudo systemctl enabled ufw
-> enabled
sudo ufw enable
-> active
sudo ufw status
-> active
sudo reboot
# and ssh login again after reboot
sudo ufw status
-> inactive

# /etc/ufw/ufw.conf
#


# Set to yes to start on boot. If setting this remotely, be sure to add a rule
# to allow your remote connection before starting ufw. Eg: 'ufw allow 22/tcp'
ENABLED=yes

No good explanations about this on the web including [https://bugs.launchpad.net/ufw/](https://bugs.launchpad.net/ufw/)

---

### Post by KenUBF on 2017-04-09
I did some searching and I found this thread. [https://unix.stackexchange.com/questions/182959/how-can-i-enable-ufw-automatically-on-boot/345505](https://unix.stackexchange.com/questions/182959/how-can-i-enable-ufw-automatically-on-boot/345505)

See if their solutions work for you. I hope it helps.

---

### Post by IceAlinutza on 2018-03-13
I think you have not set the logging parameter and when rebooting the system does not know what to load: low, medium or high.
Try:
```
sudo ufw enable
sudo ufw logging high
```
and reboot. To view the status try:
```
sudo ufw status verbose
```
[https://serverfault.com/questions/516838/where-are-the-logs-for-ufw-located-on-ubuntu-server](https://serverfault.com/questions/516838/where-are-the-logs-for-ufw-located-on-ubuntu-server)

---

