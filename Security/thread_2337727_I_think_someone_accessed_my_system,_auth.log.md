---
title: "I think someone accessed my system, auth.log"
date: 2016-09-21
forum: Security
---

### Post by jamz2 on 2016-09-21
Can someone please help me analyze these auth.log files? The usernames listed are not me. My username is Jamz. 

```
Sep 19 15:50:39 jamz-Lenovo-G570 systemd-logind[778]: Lid opened.
Sep 19 15:50:39 jamz-Lenovo-G570 systemd-logind[778]: Operation finished.
Sep 19 15:51:52 jamz-Lenovo-G570 dbus[738]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.596" (uid=0 pid=24784 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.592" (uid=0 pid=24773 comm="NetworkManager ")
Sep 19 16:01:40 jamz-Lenovo-G570 polkit-agent-helper-1[4508]: pam_unix(polkit-1:auth): authentication failure; logname= uid=1000 euid=0 tty= ruser=jamz rhost=  user=jamz
Sep 19 16:01:47 jamz-Lenovo-G570 polkitd(authority=local): Operator of unix-session:c2 successfully authenticated as unix-user:jamz to gain TEMPORARY authorization for action org.debian.apt.install-or-remove-packages for system-bus-name::1.458 [/usr/bin/python3 /usr/bin/update-manager --no-update --no-focus-on-map] (owned by unix-user:jamz)
Sep 19 16:09:01 jamz-Lenovo-G570 CRON[7657]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 16:09:01 jamz-Lenovo-G570 CRON[7657]: pam_unix(cron:session): session closed for user root
Sep 19 16:10:09 jamz-Lenovo-G570 groupadd[8027]: group added to /etc/group: name=usermetrics, GID=133
Sep 19 16:10:09 jamz-Lenovo-G570 groupadd[8027]: group added to /etc/gshadow: name=usermetrics
Sep 19 16:10:09 jamz-Lenovo-G570 groupadd[8027]: new group: name=usermetrics, GID=133
Sep 19 16:10:09 jamz-Lenovo-G570 useradd[8034]: new user: name=usermetrics, UID=123, GID=133, home=/var/lib/usermetrics, shell=/bin/false
Sep 19 16:10:10 jamz-Lenovo-G570 usermod[8039]: change user 'usermetrics' password
Sep 19 16:10:10 jamz-Lenovo-G570 chage[8045]: changed password expiry for usermetrics
Sep 19 16:15:54 jamz-Lenovo-G570 systemd-logind[778]: Watching system buttons on /dev/input/event2 (Lid Switch)
Sep 19 16:15:54 jamz-Lenovo-G570 systemd-logind[778]: Watching system buttons on /dev/input/event10 (Video Bus)
Sep 19 16:15:54 jamz-Lenovo-G570 systemd-logind[778]: Watching system buttons on /dev/input/event3 (Power Button)
Sep 19 16:15:54 jamz-Lenovo-G570 systemd-logind[778]: Watching system buttons on /dev/input/event0 (Power Button)
Sep 19 16:15:54 jamz-Lenovo-G570 systemd-logind[778]: Watching system buttons on /dev/input/event1 (Sleep Button)
Sep 19 16:16:05 jamz-Lenovo-G570 groupadd[9605]: group added to /etc/group: name=clickpkg, GID=134
Sep 19 16:16:05 jamz-Lenovo-G570 groupadd[9605]: group added to /etc/gshadow: name=clickpkg
Sep 19 16:16:05 jamz-Lenovo-G570 groupadd[9605]: new group: name=clickpkg, GID=134
Sep 19 16:16:05 jamz-Lenovo-G570 useradd[9609]: new user: name=clickpkg, UID=124, GID=134, home=/nonexistent, shell=/bin/false
Sep 19 16:16:06 jamz-Lenovo-G570 usermod[9615]: change user 'clickpkg' password
Sep 19 16:16:06 jamz-Lenovo-G570 chage[9620]: changed password expiry for clickpkg
Sep 19 16:17:02 jamz-Lenovo-G570 CRON[10631]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 16:17:02 jamz-Lenovo-G570 CRON[10631]: pam_unix(cron:session): session closed for user root
Sep 19 16:21:20 jamz-Lenovo-G570 pkexec: pam_unix(polkit-1:session): session opened for user root by (uid=1000)
Sep 19 16:21:20 jamz-Lenovo-G570 pkexec[29251]: jamz: Executing command [USER=root] [TTY=unknown] [CWD=/home/jamz] [COMMAND=/usr/lib/update-notifier/package-system-locked]
```




I can provide the logs from before or after if that would help. My computer has been acting weird, powering off, freezing. I am trying to investigate as much as I can, but my knowledge is limited.

---

### Post by TheFu on 2016-09-21
a) userids need to be all lowercase. 
b) best if hostnames are lowercase too.  Lots of scripts will not normalize hostnames and others will, which can lead to errors along the way.
c) if you were installing new packages at those timestamps, it is common for a new service to create a new userid and groupid to be used. It is a system security thing.
d) Use the '**last**' command to see who came in from where ... last.

By default, Ubuntu doesn't have any services open to the network, so unless someone installed services without your knowledge, forgetaboutit.

Nothing seems off to me.

If you care about Linux security, start learning. My signature has some good links for workable system security. There isn't a checkbox for "security." It is a continuing process.

Daily, versioned, backups and system monitoring are the best security tools that I know.  If you have installed ssh, be certain to secure that service on the network too - use fail2ban, never use passwords (only use keys), and block most of the internet from having any access to the ssh port - only allow subnets you KNOW need access to have access.

Hope this all helps.

---

