---
title: "Ubuntu hang after being logged"
date: 2012-01-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Chris180775 on 2012-01-24
Hi at all,
I have a problem with Ubuntu 12.04:
When I type my password and press enter at login screen, the computer seems to hang for 15-20 seconds, then the desktop normally load.
With dmesg command I see that there is a problem with my eth0:

```
[   10.711300] r8169 0000:02:00.0: eth0: link down
[   10.711491] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.859428] type=1400 audit(1327408135.657:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=798 comm="apparmor_parser"
[   10.860637] type=1400 audit(1327408135.661:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=802 comm="apparmor_parser"
[   10.861025] type=1400 audit(1327408135.661:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=802 comm="apparmor_parser"
[   10.861862] type=1400 audit(1327408135.661:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=803 comm="apparmor_parser"
[   10.862325] type=1400 audit(1327408135.661:11): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=803 comm="apparmor_parser"
[   10.957961] init: failsafe main process (720) killed by TERM signal
[   10.973167] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[   12.367303] r8169 0000:02:00.0: eth0: link up
[   12.367493] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   22.944133] eth0: no IPv6 routers present
```

I'm a newbie, anyone can help me?
Thanks in advance.

---

### Post by dino99 on 2012-01-24
dont worry about eth0, its a FIFO comment process, as later you get:

eth0: link becomes ready

about the login issue, either:
- purge lightdm via synaptic, then reinstall it
- sudo dpkg-reconfigure -phigh -a
( be patient, can take a while)

---

### Post by Chris180775 on 2012-01-24
> **dino99 said:**
> dont worry about eth0, its a FIFO comment process, as later you get:

eth0: link becomes ready

about the login issue, either:
- purge lightdm via synaptic, then reinstall it
- sudo dpkg-reconfigure -phigh -a
( be patient, can take a while)

Thanks, I'll give it a try! ;)

---

### Post by jerrylamos on 2012-01-24
[QUOTE=Chris180775;11636536]Hi at all,
I have a problem with Ubuntu 12.04:
When I type my password and press enter at login screen, the computer seems to hang for 15-20 seconds, then the desktop normally l/QUOTE]

I'm getting a prolonged "hang" on the new CD build install yesterday. I even thought it was busted and did a Ctrl-Alt-Del.  Then I found if I waited long enough it might come up.  Maybe.

Boot delay was even worse on the new install the day before (which would hardly run anyway).  

Today's update includes a lot of "xserver" so hang on to your hat....

Jerry

---

### Post by kansasnoob on 2012-01-24
> **jerrylamos said:**
> [QUOTE=Chris180775;11636536]Hi at all,
I have a problem with Ubuntu 12.04:
When I type my password and press enter at login screen, the computer seems to hang for 15-20 seconds, then the desktop normally l/QUOTE]

I'm getting a prolonged "hang" on the new CD build install yesterday. I even thought it was busted and did a Ctrl-Alt-Del.  Then I found if I waited long enough it might come up.  Maybe.

Boot delay was even worse on the new install the day before (which would hardly run anyway).  

Today's update includes a lot of "xserver" so hang on to your hat....

Jerry

Ditto all you said. Todays zsync showed both images only about 88% complete, so many changes are pouring in before iso-testing begins next week :D

I was just checking the forums to see if anyone else gets this update error on an existing PP:

```
Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages  Hash Sum mismatch
Some index files failed to download. They have been ignored, or old ones used instead.
```

Kind of busy ATM, some varmint is tunneling into my goat shed, so I'll just keep checking ;)

EDIT:

Wow, that's already fixed but I'm waiting for this to resolve:

```
The following packages have been kept back:
  libavformat53 libpostproc52 libswscale2

```

I take back everything I said about the name "Precise" being grandiose. It's obvious that Canonical is blowing bugs away at lightning speed :D

---

### Post by VMC on 2012-01-24
I have auto log on enabled, but I think I have the same issue except it only occurs when I install nvidia drivers. I have a normal < 22 seconds boot, but with nvidia installed it stops right after I would normally log in for about 30 extra seconds.

---

