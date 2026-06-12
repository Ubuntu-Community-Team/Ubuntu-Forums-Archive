---
title: "apparmor breaks VPN Surfshark and possibly Nord"
date: 2023-12-16
forum: Ubuntu Development Version
---

### Post by #&amp;thj^% on 2023-12-16
New update to apparmor brok my VPN Bug: [https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/2046624](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/2046624)
after reboot from upgrades:
```
 surfshark
[5927:1216/133159.791330:FATAL:credentials.cc(127)] Check failed: . : Permission denied (13)
Trace/breakpoint trap

```
It will run with the --no-sandbox, but that's not ideal
```
surfshark --no-sandbox
[6392:1216/133222.506292:ERROR:object_proxy.cc(590)] Failed to call method: org.freedesktop.portal.Settings.Read: object_path= /org/freedesktop/portal/desktop: org.freedesktop.DBus.Error.UnknownMethod: No such interface “org.freedesktop.portal.Settings” on object at path /org/freedesktop/portal/desktop


```
I purged apparmor for proof, see report.
If any current NordVPN users on Noble please reply, and let me know if your affected as well.

---

### Post by #&amp;thj^% on 2023-12-17
It now seems programs using userns (often used for sandboxing) now _must have_ an AppArmor profile.
It fixed my issue in the bug report: [https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/2046624](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/2046624)

---

### Post by MAFoElffen on 2023-12-17
LOL. 

Dang. I was going to ask you what happened if you just created a profile for that... 

I am happy you found the solution for that! (I know you were pulling your hair out over it yesterday.)

---

### Post by #&amp;thj^% on 2023-12-17
> **MAFoElffen said:**
> LOL. 

Dang. I was going to ask you what happened if you just created a profile for that... 



They are going to add a profile for it later. But for me it's Golden now.
> **MAFoElffen said:**
> 
 (I know you were pulling your hair out over it yesterday.)
I do have a tendency to be overly tenacious at time's. ;)
EDIT: just a heads up for any visitors, this may come in handy for someone:
```
 sudo cat /proc/sys/kernel/apparmor_restrict_unprivileged_userns
[sudo] password for me: 
1

```
If the returned value is 0 then restrictions on unprivileged user namespace are disabled, if a value of 1 is reported the restriction is enabled.

An excellent read is here: [https://gitlab.com/apparmor/apparmor/-/wikis/unprivileged_userns_restriction](https://gitlab.com/apparmor/apparmor/-/wikis/unprivileged_userns_restriction)

---

### Post by #&amp;thj^% on 2024-02-16
Keeping this thread updated..:P
I'm using both a snap version and .deb version of surfshark now ATM
new apparmor came in with the profiles needed for this single application:
```
apt policy apparmor grub-efi-amd64
apparmor:
  Installed: 4.0.0~alpha4-0ubuntu1
  Candidate: 4.0.0~alpha4-0ubuntu1
  Version table:
 *** 4.0.0~alpha4-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu noble/main amd64 Packages
        100 /var/lib/dpkg/status
grub-efi-amd64:
  Installed: (none)
  Candidate: 2.12-1ubuntu1
  Version table:
     2.12-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu noble/main amd64 Packages
        500 https://ppa.launchpadcontent.net/ubuntu-uefi-team/build/ubuntu noble/main amd64 Packages

```
Now surfshark is a happy application:
```
sudo aa-status |grep surfshark
   snap-update-ns.surfshark
   snap.surfshark.surfshark
   snap.surfshark.surfsharkd
   snap.surfshark.surfsharkd2
   surfshark
   /snap/surfshark/10/app/surfshark (3431) snap.surfshark.surfshark
   /snap/surfshark/10/app/surfshark (3724) snap.surfshark.surfshark
   /snap/surfshark/10/app/surfshark (3725) snap.surfshark.surfshark
   /snap/surfshark/10/app/chrome_crashpad_handler (3813) snap.surfshark.surfshark
   /snap/surfshark/10/app/surfshark (3845) snap.surfshark.surfshark
   /snap/surfshark/10/app/surfshark (3876) snap.surfshark.surfshark
   /usr/bin/bash (2187) snap.surfshark.surfsharkd
   /snap/surfshark/10/usr/bin/gjs-console (2309) snap.surfshark.surfsharkd
   /snap/surfshark/10/bin/ip (2359) snap.surfshark.surfsharkd
   /usr/bin/bash (2188) snap.surfshark.surfsharkd2
   /snap/surfshark/10/usr/bin/gjs-console (2310) snap.surfshark.surfsharkd2

```
I will continue adding a very limited amount of snaps to my once snap free system.
```
apt policy surfshark  && 
snap list surfshark
surfshark:
  Installed: 2.2.0-2835
  Candidate: 2.2.0-2835
  Version table:
 *** 2.2.0-2835 500
        500 https://ocean.surfshark.com/debian stretch/main amd64 Packages
        100 /var/lib/dpkg/status
Name       Version  Rev  Tracking     Publisher      Notes
surfshark  2.2.0    10   latest/beta  surfshark1vpn  -

```

---

