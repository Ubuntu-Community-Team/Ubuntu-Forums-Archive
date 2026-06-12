---
title: "Hello and thank you for having me"
date: 2013-05-14
forum: Security
---

### Post by AnonNoob on 2013-05-14
Looks like I'll be a regular here - I moved to Linux 2 months ago and I love it.

Unfortunately thi is however - another I got hcked post - now I'm a nooob but look at these logs for me please - a guest taking root privaledge - is this normal?

If not where did I go wro

```
groupadd[3742]: group added to /etc/group: name=guest-8qc2Eo, GID=125
May 14 10:37:30 deadman-CH groupadd[3742]: group added to /etc/gshadow: name=guest-8qc2Eo
May 14 10:37:30 deadman-CH groupadd[3742]: new group: name=guest-8qc2Eo, GID=125
May 14 10:37:30 deadman-CH useradd[3746]: new user: name=guest-8qc2Eo, UID=115, GID=125, home=/, shell=/bin/bash
May 14 10:37:31 deadman-CH usermod[3751]: change user 'guest-8qc2Eo' password
May 14 10:37:31 deadman-CH chage[3756]: changed password expiry for guest-8qc2Eo
May 14 10:37:31 deadman-CH chfn[3759]: changed user 'guest-8qc2Eo' information
May 14 10:37:31 deadman-CH usermod[3767]: change user 'guest-8qc2Eo' home from '/' to '/tmp/guest-8qc2Eo'
May 14 10:37:31 deadman-CH su[3772]: Successful su for guest-8qc2Eo by root
May 14 10:37:31 deadman-CH su[3772]: + ??? root:guest-8qc2Eo
May 14 10:37:31 deadman-CH su[3772]: pam_unix(su:session): session opened for user guest-8qc2Eo by (uid=0)
May 14 10:37:31 deadman-CH su[3772]: pam_unix(su:session): session closed for user guest-8qc2Eo
May 14 10:37:32 deadman-CH lightdm: pam_unix(lightdm-autologin:session): session opened for user guest-8qc2Eo by (uid=0)
May 14 10:37:32 deadman-CH lightdm: pam_ck_connector(lightdm-autologin:session): nox11 mode, ignoring PAM_TTY :1
May 14 10:37:35 deadman-CH polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session4 (system bus name :1.103 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
May 14 10:37:39 deadman-CH dbus[878]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.109" (uid=115 pid=4004 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.14" (uid=0 pid=1333 comm="/usr/sbin/console-kit-daemon --no-daemon ")
May 14 10:38:49 deadman-CH lightdm: pam_unix(lightdm:session): session opened for user lightdm by (uid=0)
May 14 10:38:49 deadman-CH lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :2
May 14 10:38:50 deadman-CH lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "deadman"
May 14 10:38:50 deadman-CH dbus[878]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.122" (uid=104 pid=4335 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.14" (uid=0 pid=1333 comm="/usr/sbin/console-kit-daemon --no-daemon ")
May 14 10:38:54 deadman-CH lightdm: pam_unix(lightdm:session): session closed for user lightdm
May 14 10:40:02 deadman-CH su[4599]: Successful su for deadman by root
May 14 10:40:02 deadman-CH su[4599]: + ??? root:deadman
May 14 10:40:02 deadman-CH su[4599]: pam_unix(su:session): session opened for user deadman by (uid=0)
May 14 10:40:03 deadman-CH su[4599]: pam_unix(su:session): session closed for user deadman
May 14 10:40:03 deadman-CH su[4615]: Successful su for deadman by root
May 14 10:40:03 deadman-CH su[4615]: + ??? root:deadman
May 14 10:40:03 deadman-CH su[4615]: pam_unix(su:session): session opened for user deadman by (uid=0)
May 14 10:40:03 deadman-CH su[4615]: pam_unix(su:session): session closed for user deadman
May 14 10:40:03 deadman-CH su[4632]: Successful su for deadman by root
May 14 10:40:03 deadman-CH su[4632]: + ??? root:deadman
May 14 10:40:03 deadman-CH su[4632]: pam_unix(su:session): session opened for user deadman by (uid=0)
May 14 10:40:03 deadman-CH su[4632]: pam_unix(su:session): session closed for user deadman
May 14 10:40:03 deadman-CH su[4651]: Successful su for guest-8qc2Eo by root
May 14 10:40:03 deadman-CH su[4651]: + ??? root:guest-8qc2Eo
May 14 10:40:03 deadman-CH su[4651]: pam_unix(su:session): session opened for user guest-8qc2Eo by (uid=0)
May 14 10:40:03 deadman-CH su[4651]: pam_unix(su:session): session closed for user guest-8qc2Eo
May 14 10:40:03 deadman-CH su[4665]: Successful su for guest-8qc2Eo by root
May 14 10:40:03 deadman-CH su[4665]: + ??? root:guest-8qc2Eo
May 14 10:40:03 deadman-CH su[4665]: pam_unix(su:session): session opened for user guest-8qc2Eo by (uid=0)
May 14 10:40:03 deadman-CH su[4665]: pam_unix(su:session): session closed for user guest-8qc2Eo
May 14 10:40:03 deadman-CH su[4680]: Successful su for guest-8qc2Eo by root
May 14 10:40:03 deadman-CH su[4680]: + ??? root:guest-8qc2Eo
May 14 10:40:03 deadman-CH su[4680]: pam_unix(su:session): session opened for user guest-8qc2Eo by (uid=0)
May 14 10:40:03 deadman-CH su[4680]: pam_unix(su:session): session closed for user guest-8qc2Eo
May 14 10:40:03 deadman-CH su[4708]: Successful su for deadman by root
May 14 10:40:03 deadman-CH su[4708]: + ??? root:deadman

heres a few hours later...

deadman-CH lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "deadman"
May 14 12:12:11 deadman-CH lightdm: pam_unix(lightdm:session): session closed for user lightdm
May 14 12:12:11 deadman-CH lightdm: pam_unix(lightdm:session): session opened for user deadman by (uid=0)
May 14 12:12:11 deadman-CH lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
May 14 12:12:13 deadman-CH polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session31 (system bus name :1.268 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
May 14 12:12:18 deadman-CH dbus[878]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.278" (uid=1000 pid=15897 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.14" (uid=0 pid=1333 comm="/usr/sbin/console-kit-daemon --no-daemon ")
May 14 12:17:01 deadman-CH CRON[16374]: pam_unix(cron:session): session opened for user root by (uid=0)
May 14 12:17:01 deadman-CH CRON[16374]: pam_unix(cron:session): session closed for user root
May 14 12:31:15 deadman-CH polkit-agent-helper-1[16816]: pam_ecryptfs: pam_sm_authenticate: /home/deadman is already mounted
May 14 12:31:15 deadman-CH polkitd(authority=local): Operator of unix-session:/org/freedesktop/ConsoleKit/Session31 successfully authenticated as unix-user:deadman to gain TEMPORARY authorization for action org.debian.apt.install-or-remove-packages for system-bus-name::1.310 [/usr/bin/python /usr/bin/ubuntuone-installer] (owned by unix-user:deadman)
May 14 12:49:31 deadman-CH polkit-agent-helper-1[17832]: pam_ecryptfs: pam_sm_authenticate: /home/deadman is already mounted
May 14 12:49:31 deadman-CH polkitd(authority=local): Operator of unix-session:/org/freedesktop/ConsoleKit/Session31 successfully authenticated as unix-user:deadman to gain TEMPORARY authorization for action gufw.daemon.start for unix-process:17822:1680992 [python /usr/lib/python2.7/dist-packages/gufw/gufw.py] (owned by unix-user:deadman)
May 14 13:17:01 deadman-CH CRON[19741]: pam_unix(cron:session): session opened for user root by (uid=0)
May 14 13:17:01 deadman-CH CRON[19741]: pam_unix(cron:session): session closed for user root
May 14 14:17:01 deadman-CH CRON[20705]: pam_unix(cron:session): session opened for user root by (uid=0)
May 14 14:17:01 deadman-CH CRON[20705]: pam_unix(cron:session): session closed for user root
May 14 15:17:01 deadman-CH CRON[21053]: pam_unix(cron:session): session opened for user root by (uid=0)
May 14 15:17:01 deadman-CH CRON[21053]: pam_unix(cron:session): session closed for user root
May 14 16:14:42 deadman-CH polkit-agent-helper-1[21529]: pam_ecryptfs: pam_sm_authenticate: /home/deadman is already mounted
May 14 16:14:42 deadman-CH polkitd(authority=local): Operator of unix-session:/org/freedesktop/ConsoleKit/Session31 successfully authenticated as unix-user:deadman to gain TEMPORARY authorization for action gufw.daemon.start for unix-process:20847:2405929 [python /usr/lib/python2.7/dist-packages/gufw/gufw.py] (owned by unix-user:deadman)
May 14 16:17:01 deadman-CH CRON[22472]: pam_unix(cron:session): session opened for user root by (uid=0)
May 14 16:17:01 deadman-CH CRON[22472]: pam_unix(cron:session): session closed for user root
May 14 16:31:39 deadman-CH gnome-keyring-daemon[15641]: unsupported key algorithm in certificate: 1.2.840.10045.2.1
May 14 16:32:58  gnome-keyring-daemon[15641]: last message repeated 9 times
May 14 17:17:02 deadman-CH CRON[22725]: pam_unix(cron:session): session opened for user root by (uid=0)
May 14 17:17:02 deadman-CH CRON[22725]: pam_unix(cron:session): session closed for user root

```


Any help with patching these security holes much appreciated - I'm running 3 firewalls here lol and still this   :(

---

### Post by matt_symes on 2013-05-14
Thread moved to **Security Discussions**

---

### Post by matt_symes on 2013-05-14
Hi

> **AnonNoob said:**
> Unfortunately thi is however - another I got hcked post - now I'm a nooob but look at these logs for me please - a guest taking root privaledge - is this normal?

Looks fine from here. Just seems to be opening and closing the session as you switch between users. This requires elevated privileges.

Here's aprt of mine.

```

May 14 18:52:54 matthew-S206 groupadd[22869]: group added to /etc/group: name=guest-E5hhh1, GID=131
May 14 18:52:54 matthew-S206 groupadd[22869]: group added to /etc/gshadow: name=guest-E5hhh1
May 14 18:52:54 matthew-S206 groupadd[22869]: new group: name=guest-E5hhh1, GID=131
May 14 18:52:54 matthew-S206 useradd[22873]: new user: name=guest-E5hhh1, UID=121, GID=131, home=/, shell=/bin/bash
May 14 18:52:54 matthew-S206 usermod[22884]: change user 'guest-E5hhh1' password
May 14 18:52:54 matthew-S206 chage[22889]: changed password expiry for guest-E5hhh1
May 14 18:52:54 matthew-S206 chfn[22892]: changed user 'guest-E5hhh1' information
May 14 18:52:55 matthew-S206 usermod[22900]: change user 'guest-E5hhh1' home from '/' to '/tmp/guest-E5hhh1'
May 14 18:52:55 matthew-S206 su[22908]: Successful su for guest-E5hhh1 by root
May 14 18:52:55 matthew-S206 su[22908]: + ??? root:guest-E5hhh1
May 14 18:52:55 matthew-S206 su[22908]: pam_unix(su:session): session opened for user guest-E5hhh1 by (uid=0)
May 14 18:52:55 matthew-S206 systemd-logind[1011]: Removed session c6.
May 14 18:52:55 matthew-S206 systemd-logind[1011]: New session c7 of user guest-E5hhh1.
May 14 18:52:55 matthew-S206 su[22908]: pam_unix(su:session): session closed for user guest-E5hhh1
May 14 18:52:56 matthew-S206 lightdm: pam_unix(lightdm-autologin:session): session opened for user guest-E5hhh1 by (uid=0)
May 14 18:52:56 matthew-S206 systemd-logind[1011]: Removed session c7.
May 14 18:52:56 matthew-S206 systemd-logind[1011]: New session c8 of user guest-E5hhh1.
May 14 18:52:56 matthew-S206 systemd-logind[1011]: Linked /tmp/.X11-unix/X1 to /run/user/121/X11-display.
May 14 18:52:56 matthew-S206 lightdm: pam_ck_connector(lightdm-autologin:session): nox11 mode, ignoring PAM_TTY :1
May 14 18:52:57 matthew-S206 gnome-keyring-daemon[23053]: couldn't set environment variable in session: The name org.gnome.SessionManager was not provided by any .service files
May 14 18:53:25  gnome-keyring-daemon[23053]: last message repeated 2 times
May 14 18:53:25 matthew-S206 lightdm: pam_unix(lightdm-autologin:session): session closed for user guest-E5hhh1
May 14 18:53:26 matthew-S206 userdel[23460]: delete user 'guest-E5hhh1'
May 14 18:53:26 matthew-S206 userdel[23460]: removed group 'guest-E5hhh1' owned by 'guest-E5hhh1'
```

> Any help with patching these security holes much appreciated - I'm running 3 firewalls here lol and still this 

Linux has NetFilter as it's firewall and uses IP tables rules that can be set up using different GUI i.e. gufw, firestarter.

How are you running 3 firewalls ?

Kind regards

---

