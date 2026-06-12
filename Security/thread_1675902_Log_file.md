---
title: "Log file??"
date: 2011-01-26
forum: Security
---

### Post by themanfromdelmonte on 2011-01-26
Is this normal?

```
b-HP-G62-Notebook-PC polkit-agent-helper-1[2616]: pam_sm_authenticate: Called
Jan 24 13:08:03 bob-HP-G62-Notebook-PC polkit-agent-helper-1[2616]: pam_sm_authenticate: username = [bob]
Jan 24 13:08:03 bob-HP-G62-Notebook-PC polkit-agent-helper-1[2616]: pam_sm_authenticate: /home/bob is already mounted
Jan 24 13:08:03 bob-HP-G62-Notebook-PC polkitd(authority=local): Operator of unix-session:/org/freedesktop/ConsoleKit/Session2 successfully authenticated as unix-user:bob to gain TEMPORARY authorization for action org.debian.apt.upgrade-packages for system-bus-name::1.49 [/usr/bin/python2.6 /usr/bin/update-manager --no-focus-on-map] (owned by unix-user:bob)
Jan 24 13:17:01 bob-HP-G62-Notebook-PC CRON[11086]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 24 13:17:01 bob-HP-G62-Notebook-PC CRON[11086]: pam_unix(cron:session): session closed for user root
Jan 24 13:21:28 bob-HP-G62-Notebook-PC polkitd(authority=local): Unregistered Authentication Agent for session /org/freedesktop/ConsoleKit/Session2 (system bus name :1.30, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_GB.utf
Jan 24 13:51:28 bob-HP-G62-Notebook-PC gdm-session-worker[1475]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "bob"
Jan 24 13:51:37 bob-HP-G62-Notebook-PC gdm-session-worker[1475]: pam_unix(gdm:session): session opened for user bob by (uid=0)
Jan 24 13:51:37 bob-HP-G62-Notebook-PC gdm-session-worker[1475]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Jan 24 13:51:40 bob-HP-G62-Notebook-PC polkitd(authority=local): Registered Authentication Agent for session /org/freedesktop/ConsoleKit/Session2 (system bus name :1.30 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_GB.utf
Jan 24 13:51:45 bob-HP-G62-Notebook-PC dbus-daemon: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.39" (uid=1000 pid=1755 comm="nautilus) interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply=0 destination=":1.6" (uid=0 pid=1088 comm="/usr/sbin/console-kit-daemon))
Jan 24 13:57:54 bob-HP-G62-Notebook-PC polkitd(authority=local): Unregistered Authentication Agent for session /org/freedesktop/ConsoleKit/Session2 (system bus name :1.30, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_GB.utf
Jan 24 13:57:54 bob-HP-G62-Notebook-PC gdm-session-worker[1475]: pam_unix(gdm:session): session closed for user bob
Jan 25 08:46:33 bob-HP-G62-Notebook-PC gdm-session-worker[1493]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "bob"
Jan 25 08:46:41 bob-HP-G62-Notebook-PC gdm-session-worker[1493]: pam_unix(gdm:session): session opened for user bob by (uid=0)
Jan 25 08:46:41 bob-HP-G62-Notebook-PC gdm-session-worker[1493]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Jan 25 08:46:42 bob-HP-G62-Notebook-PC polkitd(authority=local): Registered Authentication Agent for session /org/freedesktop/ConsoleKit/Session2 (system bus name :1.30 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_GB.utf
Jan 25 08:46:43 bob-HP-G62-Notebook-PC dbus-daemon: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.36" (uid=1000 pid=1698 comm="nautilus) interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply=0 destination=":1.5" (uid=0 pid=1100 comm="/usr/sbin/console-kit-daemon))
Jan 25 09:17:01 bob-HP-G62-Notebook-PC CRON[1887]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 25 09:17:01 bob-HP-G62-Notebook-PC CRON[1887]: pam_unix(cron:session): session closed for user root
Jan 25 09:42:02 bob-HP-G62-Notebook-PC polkitd(authority=local): Unregistered Authentication Agent for session /org/freedesktop/ConsoleKit/Session2 (system bus name :1.30, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_GB.utf
Jan 25 09:42:02 bob-HP-G62-Notebook-PC gdm-session-worker[1493]: pam_unix(gdm:session): session closed for user bob
Jan 26 08:07:15 bob-HP-G62-Notebook-PC gdm-session-worker[1372]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "bob"
Jan 26 08:07:17 bob-HP-G62-Notebook-PC gdm-session-worker[1372]: pam_unix(gdm:auth): conversation failed
Jan 26 08:07:17 bob-HP-G62-Notebook-PC gdm-session-worker[1372]: pam_unix(gdm:auth): auth could not identify password for [bob]
Jan 26 08:07:18 bob-HP-G62-Notebook-PC gdm-session-worker[1589]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "carol"
Jan 26 08:07:27 bob-HP-G62-Notebook-PC gdm-session-worker[1589]: pam_unix(gdm:session): session opened for user carol by (uid=0)
Jan 26 08:07:27 bob-HP-G62-Notebook-PC gdm-session-worker[1589]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Jan 26 08:07:28 bob-HP-G62-Notebook-PC polkitd(authority=local): Registered Authentication Agent for session /org/freedesktop/ConsoleKit/Session2 (system bus name :1.31 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_GB.UTF-
Jan 26 08:07:29 bob-HP-G62-Notebook-PC dbus-daemon: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.38" (uid=1001 pid=1712 comm="nautilus) interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply=0 destination=":1.5" (uid=0 pid=1065 comm="/usr/sbin/console-kit-daemon))
Jan 26 08:17:01 bob-HP-G62-Notebook-PC CRON[2224]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 26 08:17:01 bob-HP-G62-Notebook-PC CRON[2224]: pam_unix(cron:session): session closed for user root
Jan 26 09:17:01 bob-HP-G62-Notebook-PC CRON[2811]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 26 09:17:01 bob-HP-G62-Notebook-PC CRON[2811]: pam_unix(cron:session): session closed for user root
Jan 26 10:17:01 bob-HP-G62-Notebook-PC CRON[2895]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 26 10:17:01 bob-HP-G62-Notebook-PC CRON[2895]: pam_unix(cron:session): session closed for user root
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3041]: Successful su for carol by root
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3041]: + ??? root:carol
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3041]: pam_unix(su:session): session opened for user carol by (uid=0)
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3041]: pam_unix(su:session): session closed for user carol
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3053]: Successful su for carol by root
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3053]: + ??? root:carol
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3053]: pam_unix(su:session): session opened for user carol by (uid=0)
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3053]: pam_unix(su:session): session closed for user carol
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3070]: Successful su for carol by root
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3070]: + ??? root:carol
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3070]: pam_unix(su:session): session opened for user carol by (uid=0)
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3070]: pam_unix(su:session): session closed for user carol
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3100]: Successful su for carol by root
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3100]: + ??? root:carol
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3100]: pam_unix(su:session): session opened for user carol by (uid=0)
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3100]: pam_unix(su:session): session closed for user carol
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3112]: Successful su for carol by root
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3112]: + ??? root:carol
```


```
and-alternatives: run with --install /usr/bin/nmblookup nmblookup /usr/bin/nmblookup.samba3 0 --slave /usr/share/man/man1/nmblookup.1.gz nmblookup.1.gz /usr/share/man/man1/nmblookup.samba3.1.gz
2011-01-17 14:24:11 update-alternatives: link group nmblookup updated to point to /usr/bin/nmblookup.samba3
2011-01-17 14:24:11 update-alternatives: run with --install /usr/bin/net net /usr/bin/net.samba3 10 --slave /usr/share/man/man8/net.8.gz net.8.gz /usr/share/man/man8/net.samba3.8.gz
2011-01-17 14:24:11 update-alternatives: link group net updated to point to /usr/bin/net.samba3
2011-01-17 14:24:11 update-alternatives: run with --install /usr/bin/testparm testparm /usr/bin/testparm.samba3 10 --slave /usr/share/man/man1/testparm.1.gz testparm.1.gz /usr/share/man/man1/testparm.samba3.1.gz
2011-01-17 14:24:11 update-alternatives: link group testparm updated to point to /usr/bin/testparm.samba3
2011-01-17 14:24:13 update-alternatives: run with --install /lib/plymouth/themes/default.plymouth default.plymouth /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth 100
2011-01-17 14:24:18 update-alternatives: run with --install /usr/bin/xulrunner xulrunner /usr/bin/xulrunner-1.9.2 50
2011-01-17 14:24:18 update-alternatives: link group xulrunner updated to point to /usr/bin/xulrunner-1.9.2
2011-01-17 14:24:57 update-alternatives: run with --install /usr/bin/x-www-browser x-www-browser /usr/bin/firefox 40
2011-01-17 14:24:58 update-alternatives: run with --install /usr/bin/gnome-www-browser gnome-www-browser /usr/bin/firefox 40
2011-01-24 13:08:37 update-alternatives: run with --install /usr/sbin/rmt rmt /usr/sbin/rmt-tar 50 --slave /usr/share/man/man8/rmt.8.gz rmt.8.gz /usr/share/man/man8/rmt-tar.8.gz
2011-01-24 13:08:44 update-alternatives: run with --install /usr/bin/pager pager /bin/more 50 --slave /usr/share/man/man1/pager.1.gz pager.1.gz /usr/share/man/man1/more.1.gz
2011-01-24 13:08:44 update-alternatives: run with --install /usr/bin/pager pager /usr/bin/pg 10 --slave /usr/share/man/man1/pager.1.gz pager.1.gz /usr/share/man/man1/pg.1.gz
2011-01-24 13:09:22 update-alternatives: run with --remove nmblookup /usr/bin/nmblookup.samba3
2011-01-24 13:09:22 update-alternatives: link group nmblookup fully removed
2011-01-24 13:09:22 update-alternatives: run with --remove net /usr/bin/net.samba3
2011-01-24 13:09:22 update-alternatives: link group net fully removed
2011-01-24 13:09:22 update-alternatives: run with --remove testparm /usr/bin/testparm.samba3
2011-01-24 13:09:22 update-alternatives: link group testparm fully removed
2011-01-24 13:09:46 update-alternatives: run with --install /usr/bin/nmblookup nmblookup /usr/bin/nmblookup.samba3 0 --slave /usr/share/man/man1/nmblookup.1.gz nmblookup.1.gz /usr/share/man/man1/nmblookup.samba3.1.gz
2011-01-24 13:09:46 update-alternatives: link group nmblookup updated to point to /usr/bin/nmblookup.samba3
2011-01-24 13:09:46 update-alternatives: run with --install /usr/bin/net net /usr/bin/net.samba3 10 --slave /usr/share/man/man8/net.8.gz net.8.gz /usr/share/man/man8/net.samba3.8.gz
2011-01-24 13:09:46 update-alternatives: link group net updated to point to /usr/bin/net.samba3
2011-01-24 13:09:46 update-alternatives: run with --install /usr/bin/testparm testparm /usr/bin/testparm.samba3 10 --slave /usr/share/man/man1/testparm.1.gz testparm.1.gz /usr/share/man/man1/testparm.samba3.1.gz
2011-01-24 13:09:46 update-alternatives: link group testparm updated to point to /usr/bin/testparm.samba3
2011-01-26 14:33:46 update-alternatives: run with --quiet --remove rlogin /usr/bin/ssh
2011-01-26 14:33:46 update-alternatives: run with --quiet --remove rcp /usr/bin/ssh
2011-01-26 14:34:04 update-alternatives: run with --quiet --install /usr/bin/ssh-askpass ssh-askpass /usr/lib/openssh/gnome-ssh-askpass 30 --slave /usr/share/man/man1/ssh-askpass.1.gz ssh-askpass.1.gz /usr/share/man/man1/gnome-ssh-askpass.1.gz
```

and

```
bob-HP-G62-Notebook-PC polkitd(authority=local): Unregistered Authentication Agent for session /org/freedesktop/ConsoleKit/Session2 (system bus name :1.30, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_GB.utf
Jan 24 13:51:28 bob-HP-G62-Notebook-PC gdm-session-worker[1475]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "bob"
Jan 24 13:51:37 bob-HP-G62-Notebook-PC gdm-session-worker[1475]: pam_unix(gdm:session): session opened for user bob by (uid=0)
Jan 24 13:51:37 bob-HP-G62-Notebook-PC gdm-session-worker[1475]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Jan 24 13:51:40 bob-HP-G62-Notebook-PC polkitd(authority=local): Registered Authentication Agent for session /org/freedesktop/ConsoleKit/Session2 (system bus name :1.30 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_GB.utf
Jan 24 13:51:45 bob-HP-G62-Notebook-PC dbus-daemon: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.39" (uid=1000 pid=1755 comm="nautilus) interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply=0 destination=":1.6" (uid=0 pid=1088 comm="/usr/sbin/console-kit-daemon))
Jan 24 13:57:54 bob-HP-G62-Notebook-PC polkitd(authority=local): Unregistered Authentication Agent for session /org/freedesktop/ConsoleKit/Session2 (system bus name :1.30, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_GB.utf
Jan 24 13:57:54 bob-HP-G62-Notebook-PC gdm-session-worker[1475]: pam_unix(gdm:session): session closed for user bob
```

---

### Post by artie_effim on 2011-01-26
hmmm .. smells like homework ... Bob and Carol (HA!) where's Alice?

---

### Post by uRock on 2011-01-26
Hello and welcome to the forums,

Which log file(s) are we looking at?

---

### Post by Rubi1200 on 2011-01-26
@ uRock:

looks like alternatives.log and auth.log

Question for themanfromdelmonte:

why is su being used (on Ubuntu it is normal to use sudo to gain root privileges) and what exactly do you want to know?

---

### Post by themanfromdelmonte on 2011-01-27
I have a lot of trouble with people hacking into my system, where i live. Wireless is out of the question. It wouldnt last 5 mins.

Well thats just it. I have never used th su command?

```
but-G62-Notebook-PC CRON[2224]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 26 08:17:01 bob-HP-G62-Notebook-PC CRON[2224]: pam_unix(cron:session): session closed for user root
Jan 26 09:17:01 bob-HP-G62-Notebook-PC CRON[2811]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 26 09:17:01 bob-HP-G62-Notebook-PC CRON[2811]: pam_unix(cron:session): session closed for user root
Jan 26 10:17:01 bob-HP-G62-Notebook-PC CRON[2895]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 26 10:17:01 bob-HP-G62-Notebook-PC CRON[2895]: pam_unix(cron:session): session closed for user root
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3041]: Successful su for carol by root
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3041]: + ??? root:carol
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3041]: pam_unix(su:session): session opened for user carol by (uid=0)
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3041]: pam_unix(su:session): session closed for user carol
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3053]: Successful su for carol by root
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3053]: + ??? root:carol
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3053]: pam_unix(su:session): session opened for user carol by (uid=0)
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3053]: pam_unix(su:session): session closed for user carol
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3070]: Successful su for carol by root
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3070]: + ??? root:carol
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3070]: pam_unix(su:session): session opened for user carol by (uid=0)
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3070]: pam_unix(su:session): session closed for user carol
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3100]: Successful su for carol by root
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3100]: + ??? root:carol
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3100]: pam_unix(su:session): session opened for user carol by (uid=0)
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3100]: pam_unix(su:session): session closed for user carol
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3112]: Successful su for carol by root
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3112]: + ??? root:carol
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3112]: pam_unix(su:session): session opened for user carol by (uid=0)
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3112]: pam_unix(su:session): session closed for user carol
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3129]: Successful su for carol by root
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3129]: + ??? root:carol
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3129]: pam_unix(su:session): session opened for user carol by (uid=0)
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3129]: pam_unix(su:session): session closed for user carol
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3144]: Successful su for carol by root
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3144]: + ??? root:carol
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3144]: pam_unix(su:session): session opened for user carol by (uid=0)
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3144]: pam_unix(su:session): session closed for user carol
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3161]: Successful su for carol by root
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3161]: + ??? root:carol
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3161]: pam_unix(su:session): session opened for user carol by (uid=0)
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3161]: pam_unix(su:session): session closed for user carol
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3176]: Successful su for carol by root
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3176]: + ??? root:carol
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3176]: pam_unix(su:session): session opened for user carol by (uid=0)
Jan 26 10:24:20 bob-HP-G62-Notebook-PC su[3176]: pam_unix(su:session): session closed for user carol
Jan 26 10:34:07 bob-HP-G62-Notebook-PC su[3405]: Successful su for carol by root
Jan 26 10:34:07 bob-HP-G62-Notebook-PC su[3405]: + ??? root:carol
Jan 26 10:34:07 bob-HP-G62-Notebook-PC su[3405]: pam_unix(su:session): session opened for user carol by (uid=0)
Jan 26 10:34:08 bob-HP-G62-Notebook-PC su[3405]: pam_unix(su:session): session closed for user carol
Jan 26 10:34:08 bob-HP-G62-Notebook-PC su[3421]: Successful su for carol by root
Jan 26 10:34:08 bob-HP-G62-Notebook-PC su[3421]: + ??? root:carol
Jan 26 10:34:08 bob-HP-G62-Notebook-PC su[3421]: pam_unix(su:session): session opened for user carol by (uid=0)
Jan 26 10:34:08 bob-HP-G62-Notebook-PC su[3421]: pam_unix(su:session): session closed for user carol
Jan 26 10:34:08 bob-HP-G62-Notebook-PC su[3435]: Successful su for carol by root
Jan 26 10:34:08 bob-HP-G62-Notebook-PC su[3435]: + ??? root:carol
Jan 26 10:34:08 bob-HP-G62-Notebook-PC su[3435]: pam_unix(su:session): session opened for user carol by (uid=0)
Jan 26 10:34:08 bob-HP-G62-Notebook-PC su[3435]: pam_unix(su:session): session closed for user carol
Jan 26 10:34:08 bob-HP-G62-Notebook-PC su[3454]: Successful su for carol by root
Jan 26 10:34:08 bob-HP-G62-Notebook-PC su[3454]: + ??? root:carol
Jan 26 10:34:08 bob-HP-G62-Notebook-PC su[3454]: pam_unix(su:session): session opened for user carol by (uid=0)
Jan 26 10:34:08 bob-HP-G62-Notebook-PC su[3454]: pam_unix(su:session): session closed for user carol
Jan 26 10:34:08 bob-HP-G62-Notebook-PC su[3472]: Successful su for carol by root
Jan 26 10:34:08 bob-HP-G62-Notebook-PC su[3472]: + ??? root:carol
Jan 26 10:34:08 bob-HP-G62-Notebook-PC su[3472]: pam_unix(su:session): session opened for user carol by (uid=0)
Jan 26 10:34:08 bob-HP-G62-Notebook-PC su[3472]: pam_unix(su:session): session closed for user carol
Jan 26 10:34:08 bob-HP-G62-Notebook-PC su[3486]: Successful su for carol by root
Jan 26 10:34:08 bob-HP-G62-Notebook-PC su[3486]: + ??? root:carol
Jan 26 10:34:08 bob-HP-G62-Notebook-PC su[3486]: pam_unix(su:session): session opened for user carol by (uid=0)
Jan 26 10:34:08 bob-HP-G62-Notebook-PC su[3486]: pam_unix(su:session): session closed for user carol
Jan 26 10:34:20 bob-HP-G62-Notebook-PC gnome-screensaver-dialog: gkr-pam: unlocked login keyring
Jan 26 11:17:01 bob-HP-G62-Notebook-PC CRON[3663]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 26 11:17:01 bob-HP-G62-Notebook-PC CRON[3663]: pam_unix(cron:session): session closed for user root
Jan 26 12:17:01 bob-HP-G62-Notebook-PC CRON[3675]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 26 12:17:01 bob-HP-G62-Notebook-PC CRON[3675]: pam_unix(cron:session): session closed for user root
Jan 26 12:19:40 bob-HP-G62-Notebook-PC gnome-screensaver-dialog: gkr-pam: unlocked login keyring
Jan 26 13:17:01 bob-HP-G62-Notebook-PC CRON[3700]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 26 13:17:01 bob-HP-G62-Notebook-PC CRON[3700]: pam_unix(cron:session): session closed for user root
Jan 26 14:02:00 bob-HP-G62-Notebook-PC gnome-screensaver-dialog: gkr-pam: unlocked login keyring
Jan 26 14:09:01 bob-HP-G62-Notebook-PC chsh[3842]: can't change shell for 'nobody'
Jan 26 14:10:18 bob-HP-G62-Notebook-PC sudo:    carol : user NOT in sudoers ; TTY=pts/0 ;

```
What is this freedeskop session i see so much off??

I know im properly para but I need to know.

Bob is the admin account and carol the user account.

I have no services up and running the only open port is 127.0.0.1 631  cups?

Also where can I view the text displayed on shut down?  Is it logged or can the page be paused??

---

### Post by uRock on 2011-01-27
Cracking WPA wireless is easier said than done. Cracking your password to mess with your system takes even more skill. Especially if you have your firewall enabled.

---

