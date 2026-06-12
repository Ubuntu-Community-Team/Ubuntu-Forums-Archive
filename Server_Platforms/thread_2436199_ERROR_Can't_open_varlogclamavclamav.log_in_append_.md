---
title: "ERROR: Can't open /var/log/clamav/clamav.log in append mode (check permissions!)."
date: 2020-02-02
forum: Server Platforms
---

### Post by beepee on 2020-02-02
Hello,

Since a few days I have problems with my mailserver: It's a virtual Ubuntu 18.04.4 LTS running postfix, dovecot, amavis with clamav. On January 29 I did a software update (apt update & apt upgrade) and it seems that since that moment the clamd failed.

**Moment of failure:**

syslog: nothing!
maillog: nothing!

APT history:
```
Start-Date: 2020-01-29  16:33:36
Commandline: apt-get upgrade
Upgrade: cloud-init:amd64 (19.3-41-gc4735dd3-0ubuntu1~18.04.1, 19.4-33-gbb4131a2-0ubuntu1~18.04.1), libsasl2-modules-db:amd64 (2.1.27~101-g0780600+dfsg-3ubuntu2, 2.1.27~101-g0780600+dfsg-3ubuntu2.1), linux-libc-dev:amd64 (4.15.0-74.84, 4.15.0-76.86), libsasl2-2:amd64 (2.1.27~101-g0780600+dfsg-3ubuntu2, 2.1.27~101-g0780600+dfsg-3ubuntu2.1), libsasl2-modules:amd64 (2.1.27~101-g0780600+dfsg-3ubuntu2, 2.1.27~101-g0780600+dfsg-3ubuntu2.1)
End-Date: 2020-01-29  16:33:53

Start-Date: 2020-01-29  16:40:55
Commandline: apt-get -y install linux-generic linux-headers-generic linux-image-generic
Install: linux-headers-4.15.0-76-generic:amd64 (4.15.0-76.86, automatic), linux-modules-extra-4.15.0-76-generic:amd64 (4.15.0-76.86, automatic), linux-modules-4.15.0-76-generic:amd64 (4.15.0-76.86, automatic), linux-headers-4.15.0-76:amd64 (4.15.0-76.86, automatic), linux-image-4.15.0-76-generic:amd64 (4.15.0-76.86, automatic)
Upgrade: linux-headers-generic:amd64 (4.15.0.74.76, 4.15.0.76.78), linux-image-generic:amd64 (4.15.0.74.76, 4.15.0.76.78), linux-generic:amd64 (4.15.0.74.76, 4.15.0.76.78)
End-Date: 2020-01-29  16:43:24

Start-Date: 2020-01-29  16:47:01
Commandline: apt-get autoremove
Remove: linux-modules-4.15.0-72-generic:amd64 (4.15.0-72.81), linux-headers-4.15.0-72-generic:amd64 (4.15.0-72.81), linux-headers-4.15.0-72:amd64 (4.15.0-72.81), linux-image-4.15.0-72-generic:amd64 (4.15.0-72.81), linux-modules-extra-4.15.0-72-generic:amd64 (4.15.0-72.81)
End-Date: 2020-01-29  16:47:39

```
clamav log:
```
Wed Jan 29 16:00:28 2020 -> SelfCheck: Database status OK.
Wed Jan 29 16:43:57 2020 -> --- Stopped at Wed Jan 29 16:43:57 2020
Wed Jan 29 16:43:57 2020 -> Socket file removed.

```
freshclam log:
```
Wed Jan 29 16:28:12 2020 -> Received signal: wake up
Wed Jan 29 16:28:12 2020 -> ClamAV update process started at Wed Jan 29 16:28:12 2020
Wed Jan 29 16:28:17 2020 -> daily.cld database is up to date (version: 25710, sigs: 2166077, f-level: 63, builder: raynman)
Wed Jan 29 16:28:17 2020 -> main.cld database is up to date (version: 59, sigs: 4564902, f-level: 60, builder: sigmgr)
Wed Jan 29 16:28:17 2020 -> bytecode.cvd database is up to date (version: 331, sigs: 94, f-level: 63, builder: anvilleg)
Wed Jan 29 16:28:17 2020 -> --------------------------------------
Wed Jan 29 16:43:53 2020 -> Update process terminated

```

**Troubleshooting:**
_Step1:_ tried restarting clamav
syslog:
```
Feb  2 10:19:16 mailserver systemd[1]: Starting Clam AntiVirus userspace daemon...
Feb  2 10:19:16 mailserver mkdir[8081]: /bin/mkdir: cannot create directory â€˜/run/clamavâ€™: File exists
Feb  2 10:19:16 mailserver systemd[1]: Started Clam AntiVirus userspace daemon.
Feb  2 10:19:16 mailserver clamd[8086]: WARNING: Ignoring deprecated option ScanOnAccess at /etc/clamav/clamd.conf:62
Feb  2 10:19:16 mailserver clamd[8086]: WARNING: Ignoring deprecated option AllowSupplementaryGroups at /etc/clamav/clamd.conf:88
Feb  2 10:19:16 mailserver clamd[8086]: ERROR: Can't initialize the internal logger
Feb  2 10:19:16 mailserver clamd[8086]: ERROR: Can't open /var/log/clamav/clamav.log in append mode (check permissions!).
Feb  2 10:19:16 mailserver systemd[1]: clamav-daemon.service: Main process exited, code=exited, status=1/FAILURE
Feb  2 10:19:16 mailserver systemd[1]: clamav-daemon.service: Failed with result 'exit-code'.

```

what I have: terminal:
```
Welcome to Ubuntu 18.04.4 LTS (GNU/Linux 4.15.0-76-generic x86_64)

# lsb_release -a -a
No LSB modules are available.
Distributor ID:Ubuntu
Description:Ubuntu 18.04.4 LTS
Release:18.04
Codename:bionic
# service postfix status

 postfix.service - Postfix Mail Transport Agent
   Loaded: loaded (/lib/systemd/system/postfix.service; enabled; vendor preset: enabled)
   Active: active (exited) since Sun 2020-02-02 00:00:35 CET; 11h ago
  Process: 1410 ExecStart=/bin/true (code=exited, status=0/SUCCESS)
 Main PID: 1410 (code=exited, status=0/SUCCESS)

Feb 02 00:00:35 mailserver systemd[1]: Starting Postfix Mail Transport Agent...
Feb 02 00:00:35 mailserver systemd[1]: Started Postfix Mail Transport Agent.

# telnet localhost 10024
Trying ::1...
Connected to localhost.localdomain.
Escape character is '^]'.
220 [::1] ESMTP amavisd-new service ready
quit
221 2.0.0 [::1] amavisd-new closing transmission channel
Connection closed by foreign host.

```
[U]
Step2:[/U] Checking permissions:
```
# cd /var/log
# ls -al
total 275004
drwxrwxr-x  10 root      syslog               4096 Feb  2 05:00 .
drwxr-xr-x  14 root      root                 4096 Sep 25 23:52 ..
...
drw-rw-r--   2 clamav    adm                  4096 Feb  2 05:00 clamav
...
-rw-rw-r--   1 root      utmp                  384 Feb  1 22:21 wtmp.1
# cd clamav/
# ls -al
total 1912
drw-rw-r--  2 clamav adm       4096 Feb  2 05:00 .
drwxrwxr-x 10 root   syslog    4096 Feb  2 05:00 ..
-rw-r-----  1 clamav adm          0 Feb  2 05:00 clamav.log
-rw-r--r--  1 clamav adm     177303 Jan 29 16:43 clamav.log.1
...
-rw-r-----  1 clamav adm          0 Feb  2 05:00 freshclam.log
-rw-r--r--  1 clamav adm    1728206 Jan 29 16:43 freshclam.log.1
...
```

Tried all kinds of permissions and permutations, tried 666 and various ownerships but always:
```
# service clamav-daemon restart
# etc/init.d/clamav-daemon status
 clamav-daemon.service - Clam AntiVirus userspace daemon
   Loaded: loaded (/lib/systemd/system/clamav-daemon.service; enabled; vendor preset: enabled)
  Drop-In: /etc/systemd/system/clamav-daemon.service.d
           extend.conf
   Active: failed (Result: exit-code) since Sun 2020-02-02 11:06:36 CET; 10s ago
     Docs: man:clamd(8)
           man:clamd.conf(5)
           https://www.clamav.net/documents/
  Process: 9111 ExecStart=/usr/sbin/clamd --foreground=true (code=exited, status=1/FAILURE)
  Process: 9109 ExecStartPre=/bin/chown clamav /run/clamav (code=exited, status=0/SUCCESS)
  Process: 9107 ExecStartPre=/bin/mkdir /run/clamav (code=exited, status=1/FAILURE)
 Main PID: 9111 (code=exited, status=1/FAILURE)

Feb 02 11:06:36 mailserver systemd[1]: Starting Clam AntiVirus userspace daemon...
Feb 02 11:06:36 mailserver mkdir[9107]: /bin/mkdir: cannot create directory /run/clamav: File exists
Feb 02 11:06:36 mailserver systemd[1]: Started Clam AntiVirus userspace daemon.
Feb 02 11:06:36 mailserver clamd[9111]: WARNING: Ignoring deprecated option ScanOnAccess at /etc/clamav/clamd.conf:62
Feb 02 11:06:36 mailserver clamd[9111]: WARNING: Ignoring deprecated option AllowSupplementaryGroups at /etc/clamav/clamd.conf:88
Feb 02 11:06:36 mailserver clamd[9111]: ERROR: Can't initialize the internal logger
Feb 02 11:06:36 mailserver clamd[9111]: ERROR: Can't open /var/log/clamav/clamav.log in append mode (check permissions!).
Feb 02 11:06:36 mailserver systemd[1]: clamav-daemon.service: Main process exited, code=exited, status=1/FAILURE
Feb 02 11:06:36 mailserver systemd[1]: clamav-daemon.service: Failed with result 'exit-code'.

```

_Step3:_ tried to update again everything: apt update & apt upgrade & reboot: no luck
_Step4:_ tried to edit /etc/clamav/clamd.conf and /etc/clamav/freshclam.conf to comment out logfile lines:

```
# service clamav-daemon restart
# /etc/init.d/clamav-daemon status
 clamav-daemon.service - Clam AntiVirus userspace daemon
   Loaded: loaded (/lib/systemd/system/clamav-daemon.service; enabled; vendor preset: enabled)
  Drop-In: /etc/systemd/system/clamav-daemon.service.d
           extend.conf
   Active: active (running) since Sun 2020-02-02 11:08:18 CET; 2s ago
     Docs: man:clamd(8)
           man:clamd.conf(5)
           https://www.clamav.net/documents/
  Process: 9221 ExecStartPre=/bin/chown clamav /run/clamav (code=exited, status=0/SUCCESS)
  Process: 9219 ExecStartPre=/bin/mkdir /run/clamav (code=exited, status=1/FAILURE)
 Main PID: 9225 (clamd)
    Tasks: 1 (limit: 4915)
   CGroup: /system.slice/clamav-daemon.service
           9225 /usr/sbin/clamd --foreground=true

Feb 02 11:08:18 mailserver systemd[1]: Starting Clam AntiVirus userspace daemon...
Feb 02 11:08:18 mailserver mkdir[9219]: /bin/mkdir: cannot create directory /run/clamav: File exists
Feb 02 11:08:18 mailserver systemd[1]: Started Clam AntiVirus userspace daemon.
Feb 02 11:08:18 mailserver clamd[9225]: WARNING: Ignoring deprecated option ScanOnAccess at /etc/clamav/clamd.conf:62
Feb 02 11:08:18 mailserver clamd[9225]: WARNING: Ignoring deprecated option AllowSupplementaryGroups at /etc/clamav/clamd.conf:88

```

Step5: reinstalled clamav
```
# apt purge clamav clamav-deamon
# apt install clamav clamav-deamon

# service clamav-daemon restart
# /etc/init.d/clamav-daemon status
  clamav-daemon.service - Clam AntiVirus userspace daemon
   Loaded: loaded (/lib/systemd/system/clamav-daemon.service; enabled; vendor preset: enabled)
  Drop-In: /etc/systemd/system/clamav-daemon.service.d
           &#9492;&#9472;extend.conf
   Active: failed (Result: exit-code) since Sun 2020-02-02 11:52:09 CET; 1s ago
     Docs: man:clamd(8)
           man:clamd.conf(5)
           https://www.clamav.net/documents/
  Process: 12658 ExecStart=/usr/sbin/clamd --foreground=true (code=exited, status=1/FAILURE)
  Process: 12654 ExecStartPre=/bin/chown clamav /run/clamav (code=exited, status=0/SUCCESS)
  Process: 12653 ExecStartPre=/bin/mkdir /run/clamav (code=exited, status=1/FAILURE)
 Main PID: 12658 (code=exited, status=1/FAILURE)

Feb 02 11:52:09 mailserver systemd[1]: Starting Clam AntiVirus userspace daemon...
Feb 02 11:52:09 mailserver mkdir[12653]: /bin/mkdir: cannot create directory ‘/run/clamav’: File exists
Feb 02 11:52:09 mailserver systemd[1]: Started Clam AntiVirus userspace daemon.
Feb 02 11:52:09 mailserver clamd[12658]: ERROR: Can't initialize the internal logger
Feb 02 11:52:09 mailserver clamd[12658]: ERROR: Can't open /var/log/clamav/clamav.log in append mode (check permissions!).
Feb 02 11:52:09 mailserver systemd[1]: clamav-daemon.service: Main process exited, code=exited, status=1/FAILURE
Feb 02 11:52:09 mailserver systemd[1]: clamav-daemon.service: Failed with result 'exit-code'.

```

Conclusion: I'm running out of ideas and would appreciate your help.
Many thanks
BeePee

---

### Post by SeijiSensei on 2020-02-02
What is the ownership on the directory /var/log/clamav itself? Perhaps the clamav user doesn't have permissions there in order to write files in that directory.

---

### Post by beepee on 2020-02-03
The directory ownership is the same as the files: clamav:adm. I have also tested clamav:clamav but that didn&#8216;t help either. As permissions I tried 666 and 664.

---

### Post by SeijiSensei on 2020-02-04
Check the "User" directive in /etc/clamd.conf and make sure the daemon is running as user clamav.  On some RedHat systems, clamd runs as a different user ("clam") and encounters permission problems.

---

### Post by beepee on 2020-02-04
OK, I&#8216;m out of thecountry atm but I&#8217;ll check that asap when I get home. Thanks!

---

### Post by beepee on 2020-02-06
Hmm, the  the "User" directive in /etc/clamav/clamd.conf is > User clamav thus this shouldn't be the problem.

---

### Post by beepee on 2020-02-24
OK, after spending hours on this problem I had to set up a new virtual machine and new mail server. That took me under 3 hours and I moved everything over. I'd love to know what went wrong in the first place but setting up a new machine was the better solution at the end. Thanks for the help anyway. BeePee

---

