---
title: "Have formatted my entire hardrive Still Rootkits"
date: 2011-03-23
forum: Security
---

### Post by JRIDE on 2011-03-23
I have wiped my HD multiple times installed Ubuntu with a USB and CD yet still I have a rootkit. I just switched from windows to Ubuntu and am not dumb to PC's but am in way over my head with this one. It seems to be creating a fake operating environment and is using .bash to prevent me from getting logs
Here is RKhunter C&P

You must be the root user to run this program.
thestalked@stalked:~$ sudo rkhunter --check
[ Rootkit Hunter version 1.3.6 ]

Checking system commands...

  Performing 'strings' command checks
    Checking 'strings' command                               [ OK ]

  Performing 'shared libraries' checks
    Checking for preloading variables                        [ None found ]
    Checking for preloaded libraries                         [ None found ]
    Checking LD_LIBRARY_PATH variable                        [ Not found ]

  Performing file properties checks
    Checking for prerequisites                               [ OK ]
    /bin/bash                                                [ OK ]
    /bin/cat                                                 [ OK ]
    /bin/chmod                                               [ OK ]
    /bin/chown                                               [ OK ]
    /bin/cp                                                  [ OK ]
    /bin/date                                                [ OK ]
    /bin/df                                                  [ OK ]
    /bin/dmesg                                               [ OK ]
    /bin/echo                                                [ OK ]
    /bin/ed                                                  [ OK ]
    /bin/egrep                                               [ OK ]
    /bin/fgrep                                               [ OK ]
    /bin/fuser                                               [ OK ]
    /bin/grep                                                [ OK ]
    /bin/ip                                                  [ OK ]
    /bin/kill                                                [ OK ]
    /bin/less                                                [ OK ]
    /bin/login                                               [ OK ]
    /bin/ls                                                  [ OK ]
    /bin/lsmod                                               [ OK ]
    /bin/mktemp                                              [ OK ]
    /bin/more                                                [ OK ]
    /bin/mount                                               [ OK ]
    /bin/mv                                                  [ OK ]
    /bin/netstat                                             [ OK ]
    /bin/ps                                                  [ OK ]
    /bin/pwd                                                 [ OK ]
    /bin/readlink                                            [ OK ]
    /bin/sed                                                 [ OK ]
    /bin/sh                                                  [ OK ]
    /bin/su                                                  [ OK ]
    /bin/touch                                               [ OK ]
    /bin/uname                                               [ OK ]
    /bin/which                                               [ OK ]
    /bin/dash                                                [ OK ]
    /usr/bin/awk                                             [ OK ]
    /usr/bin/basename                                        [ OK ]
    /usr/bin/chattr                                          [ OK ]
    /usr/bin/cut                                             [ OK ]
    /usr/bin/diff                                            [ OK ]
    /usr/bin/dirname                                         [ OK ]
    /usr/bin/dpkg                                            [ OK ]
    /usr/bin/dpkg-query                                      [ OK ]
    /usr/bin/du                                              [ OK ]
    /usr/bin/env                                             [ OK ]
    /usr/bin/file                                            [ OK ]
    /usr/bin/find                                            [ OK ]
    /usr/bin/GET                                             [ OK ]
    /usr/bin/groups                                          [ OK ]
    /usr/bin/head                                            [ OK ]
    /usr/bin/id                                              [ OK ]
    /usr/bin/killall                                         [ OK ]
    /usr/bin/last                                            [ OK ]
    /usr/bin/lastlog                                         [ OK ]
    /usr/bin/ldd                                             [ OK ]
    /usr/bin/less                                            [ OK ]
    /usr/bin/locate                                          [ OK ]
    /usr/bin/logger                                          [ OK ]
    /usr/bin/lsattr                                          [ OK ]
    /usr/bin/lsof                                            [ OK ]
    /usr/bin/mail                                            [ OK ]
    /usr/bin/md5sum                                          [ OK ]
    /usr/bin/mlocate                                         [ OK ]
    /usr/bin/newgrp                                          [ OK ]
    /usr/bin/passwd                                          [ OK ]
    /usr/bin/perl                                            [ OK ]
    /usr/bin/pgrep                                           [ OK ]
    /usr/bin/pstree                                          [ OK ]
    /usr/bin/rkhunter                                        [ OK ]
    /usr/bin/runcon                                          [ OK ]
    /usr/bin/sha1sum                                         [ OK ]
    /usr/bin/sha224sum                                       [ OK ]
    /usr/bin/sha256sum                                       [ OK ]
    /usr/bin/sha384sum                                       [ OK ]
    /usr/bin/sha512sum                                       [ OK ]
    /usr/bin/size                                            [ OK ]
    /usr/bin/sort                                            [ OK ]
    /usr/bin/stat                                            [ OK ]
    /usr/bin/strace                                          [ OK ]
    /usr/bin/strings                                         [ OK ]
    /usr/bin/sudo                                            [ OK ]
    /usr/bin/tail                                            [ OK ]
    /usr/bin/test                                            [ OK ]
    /usr/bin/top                                             [ OK ]
    /usr/bin/touch                                           [ OK ]
    /usr/bin/tr                                              [ OK ]
    /usr/bin/uniq                                            [ OK ]
    /usr/bin/users                                           [ OK ]
    /usr/bin/vmstat                                          [ OK ]
    /usr/bin/w                                               [ OK ]
    /usr/bin/watch                                           [ OK ]
    /usr/bin/wc                                              [ OK ]
    /usr/bin/wget                                            [ OK ]
    /usr/bin/whatis                                          [ OK ]
    /usr/bin/whereis                                         [ OK ]
    /usr/bin/which                                           [ OK ]
    /usr/bin/who                                             [ OK ]
    /usr/bin/whoami                                          [ OK ]
    /usr/bin/mawk                                            [ OK ]
    /usr/bin/lwp-request                                     [ OK ]
    /usr/bin/bsd-mailx                                       [ OK ]
    /usr/bin/w.procps                                        [ OK ]
    /sbin/depmod                                             [ OK ]
    /sbin/ifconfig                                           [ OK ]
    /sbin/ifdown                                             [ OK ]
    /sbin/ifup                                               [ OK ]
    /sbin/init                                               [ OK ]
    /sbin/insmod                                             [ OK ]
    /sbin/ip                                                 [ OK ]
    /sbin/lsmod                                              [ OK ]
    /sbin/modinfo                                            [ OK ]
    /sbin/modprobe                                           [ OK ]
    /sbin/rmmod                                              [ OK ]
    /sbin/runlevel                                           [ OK ]
    /sbin/sulogin                                            [ OK ]
    /sbin/sysctl                                             [ OK ]
    /usr/sbin/adduser                                        [ OK ]
    /usr/sbin/chroot                                         [ OK ]
    /usr/sbin/cron                                           [ OK ]
    /usr/sbin/groupadd                                       [ OK ]
    /usr/sbin/groupdel                                       [ OK ]
    /usr/sbin/groupmod                                       [ OK ]
    /usr/sbin/grpck                                          [ OK ]
    /usr/sbin/nologin                                        [ OK ]
    /usr/sbin/pwck                                           [ OK ]
    /usr/sbin/rsyslogd                                       [ OK ]
    /usr/sbin/tcpd                                           [ OK ]
    /usr/sbin/useradd                                        [ OK ]
    /usr/sbin/userdel                                        [ OK ]
    /usr/sbin/usermod                                        [ OK ]
    /usr/sbin/vipw                                           [ OK ]
    /usr/sbin/unhide-linux26                                 [ OK ]

[Press <ENTER> to continue]


Checking for rootkits...

  Performing check of known rootkit files and directories
    55808 Trojan - Variant A                                 [ Not found ]
    ADM Worm                                                 [ Not found ]
    AjaKit Rootkit                                           [ Not found ]
    Adore Rootkit                                            [ Not found ]
    aPa Kit                                                  [ Not found ]
    Apache Worm                                              [ Not found ]
    Ambient (ark) Rootkit                                    [ Not found ]
    Balaur Rootkit                                           [ Not found ]
    BeastKit Rootkit                                         [ Not found ]
    beX2 Rootkit                                             [ Not found ]
    BOBKit Rootkit                                           [ Not found ]
    cb Rootkit                                               [ Not found ]
    CiNIK Worm (Slapper.B variant)                           [ Not found ]
    Danny-Boy's Abuse Kit                                    [ Not found ]
    Devil RootKit                                            [ Not found ]
    Dica-Kit Rootkit                                         [ Not found ]
    Dreams Rootkit                                           [ Not found ]
    Duarawkz Rootkit                                         [ Not found ]
    Enye LKM                                                 [ Not found ]
    Flea Linux Rootkit                                       [ Not found ]
    FreeBSD Rootkit                                          [ Not found ]
    Fu Rootkit                                               [ Not found ]
    ****`it Rootkit                                          [ Not found ]
    GasKit Rootkit                                           [ Not found ]
    Heroin LKM                                               [ Not found ]
    HjC Kit                                                  [ Not found ]
    ignoKit Rootkit                                          [ Not found ]
    iLLogiC Rootkit                                          [ Not found ]
    IntoXonia-NG Rootkit                                     [ Not found ]
    Irix Rootkit                                             [ Not found ]
    Kitko Rootkit                                            [ Not found ]
    Knark Rootkit                                            [ Not found ]
    ld-linuxv.so Rootkit                                     [ Not found ]
    Li0n Worm                                                [ Not found ]
    Lockit / LJK2 Rootkit                                    [ Not found ]
    Mood-NT Rootkit                                          [ Not found ]
    MRK Rootkit                                              [ Not found ]
    Ni0 Rootkit                                              [ Not found ]
    Ohhara Rootkit                                           [ Not found ]
    Optic Kit (Tux) Worm                                     [ Not found ]
    Oz Rootkit                                               [ Not found ]
    Phalanx Rootkit                                          [ Not found ]
    Phalanx2 Rootkit                                         [ Not found ]
    Phalanx2 Rootkit (extended tests)                        [ Not found ]
    Portacelo Rootkit                                        [ Not found ]
    R3dstorm Toolkit                                         [ Not found ]
    RH-Sharpe's Rootkit                                      [ Not found ]
    RSHA's Rootkit                                           [ Not found ]
    Scalper Worm                                             [ Not found ]
    Sebek LKM                                                [ Not found ]
    Shutdown Rootkit                                         [ Not found ]
    SHV4 Rootkit                                             [ Not found ]
    SHV5 Rootkit                                             [ Not found ]
    Sin Rootkit                                              [ Not found ]
    Slapper Worm                                             [ Not found ]
    Sneakin Rootkit                                          [ Not found ]
    'Spanish' Rootkit                                        [ Not found ]
    Suckit Rootkit                                           [ Not found ]
    SunOS Rootkit                                            [ Not found ]
    SunOS / NSDAP Rootkit                                    [ Not found ]
    Superkit Rootkit                                         [ Not found ]
    TBD (Telnet BackDoor)                                    [ Not found ]
    TeLeKiT Rootkit                                          [ Not found ]
    T0rn Rootkit                                             [ Not found ]
    trNkit Rootkit                                           [ Not found ]
    Trojanit Kit                                             [ Not found ]
    Tuxtendo Rootkit                                         [ Not found ]
    URK Rootkit                                              [ Not found ]
    Vampire Rootkit                                          [ Not found ]
    VcKit Rootkit                                            [ Not found ]
    Volc Rootkit                                             [ Not found ]
    Xzibit Rootkit                                           [ Not found ]
    X-Org SunOS Rootkit                                      [ Not found ]
    zaRwT.KiT Rootkit                                        [ Not found ]
    ZK Rootkit                                               [ Not found ]

  Performing additional rootkit checks
    Suckit Rookit additional checks                          [ OK ]
    Checking for possible rootkit files and directories      [ None found ]
    Checking for possible rootkit strings                    [ None found ]

  Performing malware checks
    Checking running processes for suspicious files          [ None found ]
    Checking for login backdoors                             [ None found ]
    Checking for suspicious directories                      [ None found ]
    Checking for sniffer log files                           [ None found ]

  Performing Linux specific checks
    Checking loaded kernel modules                           [ OK ]
    Checking kernel module names                             [ OK ]

[Press <ENTER> to continue]


Checking the network...

  Performing check for backdoor ports
    Checking for TCP port 1524                               [ Not found ]
    Checking for TCP port 1984                               [ Not found ]
    Checking for UDP port 2001                               [ Not found ]
    Checking for TCP port 2006                               [ Not found ]
    Checking for TCP port 2128                               [ Not found ]
    Checking for TCP port 6666                               [ Not found ]
    Checking for TCP port 6667                               [ Not found ]
    Checking for TCP port 6668                               [ Not found ]
    Checking for TCP port 6669                               [ Not found ]
    Checking for TCP port 7000                               [ Not found ]
    Checking for TCP port 13000                              [ Not found ]
    Checking for TCP port 14856                              [ Not found ]
    Checking for TCP port 25000                              [ Not found ]
    Checking for TCP port 29812                              [ Not found ]
    Checking for TCP port 31337                              [ Not found ]
    Checking for TCP port 33369                              [ Not found ]
    Checking for TCP port 47107                              [ Not found ]
    Checking for TCP port 47018                              [ Not found ]
    Checking for TCP port 60922                              [ Not found ]
    Checking for TCP port 62883                              [ Not found ]
    Checking for TCP port 65535                              [ Not found ]

  Performing checks on the network interfaces
    Checking for promiscuous interfaces                      [ None found ]

[Press <ENTER> to continue]


Checking the local host...

  Performing system boot checks
    Checking for local host name                             [ Found ]
    Checking for system startup files                        [ Found ]
    Checking system startup files for malware                [ None found ]

  Performing group and account checks
    Checking for passwd file                                 [ Found ]
    Checking for root equivalent (UID 0) accounts            [ None found ]
    Checking for passwordless accounts                       [ None found ]
    Checking for passwd file changes                         [ None found ]
    Checking for group file changes                          [ None found ]
    Checking root account shell history files                [ None found ]

  Performing system configuration file checks
    Checking for SSH configuration file                      [ Not found ]
    Checking for running syslog daemon                       [ Found ]
    Checking for syslog configuration file                   [ Found ]
    Checking if syslog remote logging is allowed             [ Not allowed ]

  Performing filesystem checks
    Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]

[Press <ENTER> to continue]



System checks summary
=====================

File properties checks...
    Files checked: 132
    Suspect files: 0

Rootkit checks...
    Rootkits checked : 242
    Possible rootkits: 0

Applications checks...
    All checks skipped

The system checks took: 56 seconds

All results have been written to the log file (/var/log/rkhunter.log)

One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log)

thestalked@stalked:~$ /var/log/rkhunter.log
bash: /var/log/rkhunter.log: Permission denied
thestalked@stalked:~$ sudo /var/log/rkhunter.log
sudo: /var/log/rkhunter.log: command not found
thestalked@stalked:~$ 


if anyone can help it would be much appreciated. I will post any logs necessary.

---

### Post by brian_p on 2011-03-23
> **JRIDE said:**
> 
thestalked@stalked:~$ /var/log/rkhunter.log
bash: /var/log/rkhunter.log: Permission denied
thestalked@stalked:~$ sudo /var/log/rkhunter.log
sudo: /var/log/rkhunter.log: command not found
thestalked@stalked:~$ 

```
thestalked@stalked:~$ /var/log/rkhunter.log
```

This is not an executable file. To read it you could do

```
thestalked@stalked:~$ less /var/log/rkhunter.log
```

---

### Post by rookcifer on 2011-03-23
What makes you think you have a rootkit?

---

### Post by JRIDE on 2011-03-23
What logs would you need me to show you I do? And this doesn't mean anything?
 Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]

---

### Post by JRIDE on 2011-03-23
When I was first compromised I was presented with a message from freedomdesktop.org and now that URL keeps showing up in my logs. 



Mar 23 04:58:04 stalked gdm-session-worker[1478]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "thestalked"
Mar 23 04:58:10 stalked gdm-session-worker[1478]: pam_unix(gdm:session): session opened for user thestalked by (uid=0)
Mar 23 04:58:10 stalked gdm-session-worker[1478]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Mar 23 04:58:12 stalked polkitd(authority=local): Registered Authentication Agent for session /org/freedesktop/ConsoleKit/Session2 (system bus name :1.28 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.utf8)
Mar 23 04:58:16 stalked dbus-daemon: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.36" (uid=1000 pid=1673 comm="nautilus) interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply=0 destination=":1.6" (uid=0 pid=1189 comm="/usr/sbin/console-kit-daemon))
Mar 23 05:05:45 stalked dbus-daemon: [system] Rejected send message, 1 matched rules; type="method_call", sender=":1.52" (uid=1000 pid=2042 comm="/usr/bin/python) interface="org.freedesktop.DBus.Introspectable" member="Introspect" error name="(unset)" requested_reply=0 destination=":1.55" (uid=0 pid=2064 comm="/usr/bin/python))
Mar 23 05:06:04 stalked polkitd(authority=local): Operator of unix-session:/org/freedesktop/ConsoleKit/Session2 successfully authenticated as unix-user:thestalked to gain TEMPORARY authorization for action org.debian.apt.change-repository for system-bus-name::1.52 [/usr/bin/python /usr/bin/software-center] (owned by unix-user:thestalked)
Mar 23 05:06:14 stalked dbus-daemon: [system] Rejected send message, 1 matched rules; type="method_call", sender=":1.52" (uid=1000 pid=2042 comm="/usr/bin/python) interface="org.freedesktop.DBus.Introspectable" member="Introspect" error name="(unset)" requested_reply=0 destination=":1.55" (uid=0 pid=2064 comm="/usr/bin/python))
Mar 23 05:17:01 stalked CRON[2227]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar 23 05:17:01 stalked CRON[2227]: pam_unix(cron:session): session closed for user root
Mar 23 05:20:37 stalked polkit-agent-helper-1[2319]: pam_unix(polkit-1:auth): authentication failure; logname= uid=1000 euid=0 tty= ruser=thestalked rhost=  user=thestalked
Mar 23 05:20:46 stalked polkitd(authority=local): Operator of unix-session:/org/freedesktop/ConsoleKit/Session2 successfully authenticated as unix-user:thestalked to gain TEMPORARY authorization for action org.debian.apt.install-or-remove-packages for system-bus-name::1.52 [/usr/bin/python /usr/bin/software-center] (owned by unix-user:thestalked)
Mar 23 05:21:09 stalked groupadd[2578]: group added to /etc/group: name=Debian-exim, GID=123
Mar 23 05:21:09 stalked groupadd[2578]: group added to /etc/gshadow: name=Debian-exim
Mar 23 05:21:09 stalked groupadd[2578]: new group: name=Debian-exim, GID=123
Mar 23 05:21:09 stalked useradd[2584]: new user: name=Debian-exim, UID=114, GID=123, home=/var/spool/exim4, shell=/bin/false
Mar 23 05:21:09 stalked chage[2589]: changed password expiry for Debian-exim
Mar 23 05:24:19 stalked sudo: thestalked : TTY=pts/0 ; PWD=/home/thestalked ; USER=root ; COMMAND=/usr/bin/rkhunter --check
Mar 23 06:01:27 stalked gnome-keyring-daemon[1576]: couldn't initialize slot with master password: The password or PIN is incorrect
Mar 23 06:01:27 stalked gnome-screensaver-dialog: gkr-pam: unlocked login keyring
Mar 23 06:03:12 stalked sudo: thestalked : TTY=pts/0 ; PWD=/home/thestalked ; USER=root ; COMMAND=/usr/bin/less /var/log/rkhunter.log
Mar 23 06:05:11 stalked polkitd(authority=local): Unregistered Authentication Agent for session /org/freedesktop/ConsoleKit/Session2 (system bus name :1.28, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.utf8)
Mar 23 06:05:12 stalked gdm-session-worker[1478]: pam_unix(gdm:session): session closed for user thestalked
Mar 23 06:06:29 stalked gdm-session-worker[1494]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "thestalked"
Mar 23 06:06:35 stalked gdm-session-worker[1494]: pam_unix(gdm:session): session opened for user thestalked by (uid=0)
Mar 23 06:06:35 stalked gdm-session-worker[1494]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Mar 23 06:06:37 stalked polkitd(authority=local): Registered Authentication Agent for session [COLOR=Red]/org/freedesktop/ConsoleKit/Session[/COLOR]2 (system bus name :1.30 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.utf8)
Mar 23 06:06:41 stalked dbus-daemon: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.38" (uid=1000 pid=1687 comm="nautilus) interface="[COLOR=Red]org.freedesktop[/COLOR].DBus.Properties" member="GetAll" error name="(unset)" requested_reply=0 destination=":1.6" (uid=0 pid=938 comm="/usr/sbin/console-kit-daemon))
Mar 23 06:12:02 stalked unix_chkpwd[1913]: password check failed for user (thestalked)
Mar 23 06:12:02 stalked gnome-screensaver-dialog: pam_unix(gnome-screensaver:auth): authentication failure; logname= uid=1000 euid=1000 tty=:0.0 ruser= rhost=  user=thestalked
Mar 23 06:12:15 stalked gnome-screensaver-dialog: gkr-pam: unlocked login keyring
Mar 23 06:12:29 stalked polkitd(authority=local): Operator of unix-session:/org/freedesktop/ConsoleKit/Session2 successfully authenticated as unix-user:thestalked to gain TEMPORARY authorization for action com.ubuntu.devicedriver.install for unix-process:1848:10743 [/usr/bin/python /usr/bin/jockey-gtk --check] (owned by unix-user:thestalked)
Mar 23 06:15:59 stalked dbus-daemon: [system] Rejected send message, 1 matched rules; type="method_call", sender=":1.54" (uid=1000 pid=19206 comm="/usr/bin/python) interface="org.freedesktop.DBus.Introspectable" member="Introspect" error name="(unset)" requested_reply=0 destination=":1.57" (uid=0 pid=19228 comm="/usr/bin/python))
Mar 23 06:16:41 stalked polkit-agent-helper-1[19235]: pam_unix(polkit-1:auth): authentication failure; logname= uid=1000 euid=0 tty= ruser=thestalked rhost=  user=thestalked
Mar 23 06:16:49 stalked polkitd(authority=local): Operator of unix-session:/org/freedesktop/ConsoleKit/Session2 successfully authenticated as unix-user:thestalked to gain TEMPORARY authorization for action org.debian.apt.install-or-remove-packages for system-bus-name::1.54 [/usr/bin/python /usr/bin/software-center] (owned by unix-user:thestalked)
Mar 23 06:17:01 stalked CRON[19243]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar 23 06:17:01 stalked CRON[19243]: pam_unix(cron:session): session closed for user root
Mar 23 06:19:01 stalked groupadd[20547]: group added to /etc/group: name=haldaemon, GID=124
Mar 23 06:19:01 stalked groupadd[20547]: group added to /etc/gshadow: name=haldaemon
Mar 23 06:19:01 stalked groupadd[20547]: new group: name=haldaemon, GID=124
Mar 23 06:19:01 stalked useradd[20551]: new user: name=haldaemon, UID=115, GID=124, home=/var/run/hald, shell=/bin/false
Mar 23 06:19:01 stalked usermod[20556]: change user 'haldaemon' password
Mar 23 06:19:02 stalked chage[20561]: changed password expiry for haldaemon
Mar 23 06:19:02 stalked chfn[20564]: changed user 'haldaemon' information
Mar 23 06:24:32 stalked polkit-agent-helper-1[21123]: pam_unix(polkit-1:auth): authentication failure; logname= uid=1000 euid=0 tty= ruser=thestalked rhost=  user=thestalked
Mar 23 06:24:41 stalked polkitd(authority=local): Operator of unix-session:/org/freedesktop/ConsoleKit/Session2 successfully authenticated as unix-user:thestalked to gain TEMPORARY authorization for action org.freedesktop.systemtoolsbackends.set for system-bus-name::1.59 [users-admin] (owned by unix-user:thestalked)
Mar 23 06:25:01 stalked CRON[21136]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar 23 06:25:01 stalked CRON[21136]: pam_unix(cron:session): session closed for user root


Now I am trying to usse an App I downloaded Firestarter and it is asking for PW when I type my root PW in says it is denied. And is it normal to have Screen caps when you just wiped your HD and a fresh install?  


Mar 23 07:11:41 stalked AptDaemon: INFO: CommitPackages() was called: dbus.Array([dbus.String(u'firestarter')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s'))
Mar 23 07:11:53 stalked AptDaemon.Trans: INFO: Queuing transaction /org/debian/apt/transaction/e20b9fe4607d4a9292d34bf3582a00f8
Mar 23 07:11:53 stalked AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/e20b9fe4607d4a9292d34bf3582a00f8
Mar 23 07:11:54 stalked AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/e20b9fe4607d4a9292d34bf3582a00f8
Mar 23 07:11:54 stalked AptDaemon.Worker: INFO: Committing packages: dbus.Array([dbus.String(u'firestarter')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
Mar 23 07:12:12 stalked AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/e20b9fe4607d4a9292d34bf3582a00f8
Mar 23 07:16:00 stalked kernel: [ 4210.581460] show_signal_msg: 3 callbacks suppressed
Mar 23 07:16:00 stalked kernel: [ 4210.581465] gnome-screensav[25811]: segfault at 4 ip 007d05a0 sp bfea42dc error 4 in libGL.so.1.2[763000+b4000]
Mar 23 07:17:01 stalked CRON[25846]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

---

### Post by rookcifer on 2011-03-23
> **JRIDE said:**
> When I was first compromised I was presented with a message from freedomdesktop.org and now that URL keeps showing up in my logs. 

That's not a URL.  It has to do with the X server and is completely normal.

> Now I am trying to usse an App I downloaded Firestarter and it is asking for PW when I type my root PW in says it is denied. And is it normal to have Screen caps when you just wiped your HD and a fresh install? 


Get rid of Firestarter.  It is no longer maintained.

I still don't see why you think you have been "hacked."

---

### Post by JRIDE on 2011-03-23
I know I was hacked. Mostly because the IP's mostly 255.2555etc that were pinging me and sending and sniffing my roomates apple connection one of them was nice enough to change his Identity to tell me I should WIKI WireShark....which I had up and do not know how to use. Can we get past if I was hacked or not and get to what YOU would like me to show to prove this? Please? And Firestarter was working fine like yesterday.

---

### Post by Grenage on 2011-03-23
It really sounds like you have nothing to be worried about, there appears to be no evidence of a compromised system.  If you 'were' compromised with a rootkit, about the only way to be sure is a total system wipe, which you have done.

---

### Post by rookcifer on 2011-03-23
> **JRIDE said:**
> I know I was hacked. Mostly because the IP's mostly 255.2555etc 

255.255.255.255 is not a hacker.  It is a [broadcast address.]("http://en.wikipedia.org/wiki/Broadcast_address")

I think you are being paranoid.  The chances of suddenly getting a rootkit after just installing Ubuntu is really about 0.  Again, rootkit scanners are not reliable.  Do a search on the forum -- there are tons of threads where people think they were "hacked" because rkhunter gives false positives.  This is why I detest rkhunter.  Too many Windows converts come to Linux thinking that security = a virus scanner.  That's not the way it works here.  Virus/rootkit scanners are worthless.

---

### Post by JRIDE on 2011-03-23
I understand you probably get it all the time that people think they were hacked and they were not. I was. I was told via IRC I was going to be.Then my Windows OS was slowly melted. Then My Admin and sudo privileges were systematically taken from me. 

Now let us move past if I was and tell me what I need to show you if I am or not before I start getting redirected away from this site or my IRC stops working. Never mind it has no more IRC.

---

### Post by Grenage on 2011-03-23
Assuming you don't have a load of services such as SSH/VNC open and without a password, people cannot magically install rootkits on your PC.  While Computer hackers on TV can compromise systems in 5 seconds, it doesn't work that way in real life.  I can't speak to the windows install, but they are normally also quite secure.

Bottom line here, if you really, *really* think you have a rootkit, I recommend a complete drive blank.

You could possibly have some defective hardware.

---

### Post by rookcifer on 2011-03-23
> **JRIDE said:**
> I understand you probably get it all the time that people think they were hacked and they were not. I was. I was told via IRC I was going to be.Then my Windows OS was slowly melted. Then My Admin and sudo privileges were systematically taken from me. 

Now let us move past if I was and tell me what I need to show you if I am or not before I start getting redirected away from this site or my IRC stops working. Never mind it has no more IRC.

Saying you were hacked requires proof.  And, no, proof is not what some yahoo on IRC told you.  I don't doubt your Windows box got cracked, but Windows is not Linux.  

The fact that you have formatted and reinstalled Ubuntu numerous times and still think you are hacked is what is telling me that you were not compromised but are simply being paranoid.  If the **entire** drive has been formatted there is no way a hacker can maintain access between installs.  And since Ubuntu comes with no listening ports, the hacker would have to be superman to "instantly" hack you again.  Something like this would require physical access.

Just for kicks and grins, open a terminal and run the following:

```
sudo netstat -ptvnl
```

Also, are you behind a router?

---

### Post by dogscoff on 2011-03-23
OK, if you really feel the need to spend more time setting your mind at ease, try this:

- Pull the network cable out of your PC / disable the wireless/ disconnect your mobile phone. Your PC is now completely cut off from the internet, and even the world's most awesomest hacker cannot possibly get into it, unless he also happens to be one of the X-Men.

- Wipe your hard drive(s) again. Make sure you wipe ALL partitions, and disconnect all external drives, USB sticks, memory cards etc. No rootkit/ virus can survive that, so your PC is now 100% guaranteed completely rootkit/ hacker / virus free. Until you reconnect it to a possible infection vector, there is no way for you to get infected.

- Reinstall Ubuntu using trusted media. A fresh CD downloaded and burnt at your friend's house might be a good idea.

- Run all your rootkit tests again. If they come up positive, either THEY ARE WRONG or YOU ARE MISREADING THEM! Your system cannot be compromised at this point, it just isn't possible. 

- Reconnect to the internet and immediately run all security updates. Run your tests again and see if they have changed since the last time.

- Report back here. We all promise not to say "I told you so".

Note that I think the above is all a complete waste of time. I don't think you are infected.

---

### Post by JRIDE on 2011-03-23
thestalked@stalked:~$ sudo netstat -ptvnl
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      969/cupsd       
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      1785/exim4      
tcp6       0      0 ::1:631                 :::*                    LISTEN      969/cupsd       
tcp6       0      0 ::1:25                  :::*                    LISTEN      1785/exim4      

I have no idea what this means.

You have all done a good job of convincing me I am just being paranoid. If not I did a lot of reformatting and going to parents house to get USB then CD. Seriously I did that.  I guess I am just being paranoid. Just wanted some 100% stamp of approval  there really isn't one. However, after seeing a script change your registry right in front of your eyes and not being able to do anything about it was crazy. I feel quite exposed. I don't have to do all you suggested because it has been done....I feel kinda silly now. 

I will just go back and start setting my OS according to the sticky.

---

### Post by BkkBonanza on 2011-03-23
OP: You should learn at least even the most basic Linux commands before coming here and making grandiose claims about being hacked. It's very obvious to anyone reading here that you have no idea what you're talking about. You are simply seeing some stuff you don't understand and claiming these things mean you have been hacked. But hey, sure, don't listen to anyone here, just keep re-installing your system over and over.

---

### Post by Thund3rstruck on 2011-03-23
In order for a rootkit to be useful it has to establish a remote connection to a host to upload the stealer (iStealer, etc) and keylogging logs; usually though FTP so all you have to do is run netstat checks periodically to identify unknown remote connections. Your output shows that you have a mail client and a printer client listening, which is expected. 

You're mostly interested in outbound connections to any *.no-ip.org or *.dyndns.org address. The vast majority of trojans use these dynamic dns services to transmit the keylogger logs. 

Keep in mind that certain network protocols are very chatty, for example WINS/NetBIOS is constantly sending out broadcasts to the network hardware to let it know that its alive. You aren't worried at all about broadcast traffic. You should be very worried about VNC, Telnet, FTP, etc, etc if you see this kind of traffic.

---

### Post by dogscoff on 2011-03-23
> Just wanted some 100% stamp of approval there really isn't one. 

You hit the nail on the head there. It is very very difficult to prove a negative, because there is always some (increasingly unlikely) "what if" scenario that evades every possible test or check. Sometimes you just have to accept that 99.9% certain is certain enough. 

It is nasty being targeted like that though. I hope your attacker didn't wipe / take any important data. It sounds like some kind of personal grudge though, so either (a) it's someone you know IRL, so they would be stupid to do something criminal like that or (b) it's Joe Random that you met on IRC, and you can probably lose them as easily as resetting your router to get a new IP address.

---

### Post by Soul-Sing on 2011-03-23
offtopic: should "we" really support rkhunter/chkrootkit related questions?
- there are known for "false positives"
- the outcome is difficult to interpret or al least ambiguous
- the results often cause panic

then we give our members some advise, because they don't trust their systems anymore
we tell them to run: sudo netstat -ptvnl
with this outcome: tcp 0 0 127.0.0.1:631 0.0.0.0:* LISTEN 969/cupsd
tcp 0 0 127.0.0.1:25 0.0.0.0:* LISTEN 1785/exim4 

again some panic, what is exim4!!!  exim4 comes with rkhunter........(really)

---

### Post by JRIDE on 2011-03-23
It was (b) I was trying to get some programming help and someone told me to DL some files (as soon as I did it I knew I screwed up) I didn't have sensitive info and changed e-mail PWs but yeah all of my old stuff was DLd then wiped.

---

### Post by Grenage on 2011-03-23
> **leoquant said:**
> offtopic: should "we" really support rkhunter/chkrootkit related questions?
- there are known for "false positives"
- the outcome is difficult to interpret or al least ambiguous
- the results often cause panic

then we give our members some advise, because they don't trust their systems anymore
we tell them to run: sudo netstat -ptvnl
with this outcome: tcp 0 0 127.0.0.1:631 0.0.0.0:* LISTEN 969/cupsd
tcp 0 0 127.0.0.1:25 0.0.0.0:* LISTEN 1785/exim4 

again some panic, what is exim4!!!  exim4 comes with rkhunter........(really)

You're right, but one can't learn when the answer to the question is 'I don't want to talk about it'; at least through conversation, the OP can put their mind at ease.  50% of the problems on here could probably be distilled down to 10 stickies.

---

### Post by Soul-Sing on 2011-03-23
> 50% of the problems on here could probably be distilled down to 10 stickies.

Maybe you agree with me that this part. software (rkhunter, chkrootkit) causes a lot of unnecessary concerns for the average user. imho people should be warned to use it.
it is not only the repeating part of these threads which I refer to, but the unnecessary alarm they causes: reinstalls/formatting disks... And possible "damage" to the reputation of Ubuntu.

---

### Post by Grenage on 2011-03-23
> **leoquant said:**
> Maybe you agree with me that this part. software (rkhunter, chkrootkit) causes a lot of unnecessary concerns for the average user. imho people should be warned to use it.
it is not only the repeating part of these threads which I refer to, but the unnecessary alarm they cuases: reinstalls/formatting disks... And possible "damage" to the reputation of Ubuntu.

I agree with you on this, absolutely.

---

### Post by bodhi.zazen on 2011-03-23
> **leoquant said:**
> Maybe you agree with me that this part. software (rkhunter, chkrootkit) causes a lot of unnecessary concerns for the average user. imho people should be warned to use it.
it is not only the repeating part of these threads which I refer to, but the unnecessary alarm they cuases: reinstalls/formatting disks... And possible "damage" to the reputation of Ubuntu.

People come to Linux from a Windows back ground. There are used to running graphical tools (antivirus).

Tools such as rkhunter can not be used in the same way. One either needs to read the man page, then google search any and all "alerts" or not use the tools.

If properly used these tools can be invaluable, but they do require a significant time investment.

---

### Post by tubbygweilo on 2011-03-23
Using a live [DBAN]("http://www.dban.org/about") disk is often a good place to start when scouring or clensing a disk but be warned it may take a good few hours to do the job. 

It is often wise to do it over night.

---

### Post by bodhi.zazen on 2011-03-23
> **tubbygweilo said:**
> Using a live [DBAN]("http://www.dban.org/about") disk is often a good place to start when scouring or clensing a disk but be warned it may take a good few hours to do the job. 

It is often wise to do it over night.

No it is not.

The Gutmann theory has been debunked and you can use one pass with dd .

[http://www.nber.org/sys-admin/overwritten-data-gutmann.html](http://www.nber.org/sys-admin/overwritten-data-gutmann.html)

dd is sufficient, faster then dban, and less wear on the hard drive.

---

### Post by Soul-Sing on 2011-03-23
> Tools such as rkhunter can not be used in the same way. One either needs to read the man page, then google search any and all "alerts" or not use the tools.

The "google part" of your answer is an interesting one. The manpage is imo "no good", or not very clear in many aspects. Suddenly google is our friend to solve problems? Helping to interpret the "scan"results? That is imo very much the windows mindset, if there is any at all: googling the world wide web.(obscure sites/etc./etc.) But that's not the issue. People come here for support, Ubuntu support. And "we" can't give them the support they need. We are left with this mantra:

- these programs come with many "false positives"
- don't worry, relax
- use google(!) to interpret the results (thats asked to much for a beginner)

---

### Post by bodhi.zazen on 2011-03-23
> **leoquant said:**
> The "google part" of your answer is an interesting one. The manpage is imo "no good", or not very clear in many aspects. Suddenly google is our friend to solve problems? Helping to interpret the "scan"results? That is imo very much the windows mindset, if there is any at all: googling the world wide web.(obscure sites/etc./etc.) But that's not the issue. People come here for support, Ubuntu support. And "we" can't give them the support they need. We are left with this mantra:

- these programs come with many "false positives"
- don't worry, relax
- use google(!) to interpret the results (thats asked to much for a beginner)

Those are all valid issues. I suggest you write a wiki page detailing the alerts and how to manage them. I would reference it.

Perhaps you know a better citation ?

---

### Post by Soul-Sing on 2011-03-23
> I suggest you write a wiki page detailing the alerts and how to manage them

Yep thats a good point. Only criticism is no good, and brings us no further. To be honest, I really tried to understand the  software, but I gave up. I didn't saw any logic in it. (which probl. says more bout me than this software.)

---

### Post by deconstrained on 2011-03-23
Some GNU/Linux distributions use scripts in place of certain coreutils, for whatever reason. Arch and Slackware, for instance, use an interactive script that shows up as a rootkit. False positives.
> **JRIDE said:**
> thestalked@stalked:~$ /var/log/rkhunter.log
bash: /var/log/rkhunter.log: Permission denied
thestalked@stalked:~$ sudo /var/log/rkhunter.log
sudo: /var/log/rkhunter.log: command not found

You're trying to run the logfiles as programs? Just view the contents with the "less" or "more" commands. You may need superuser permissions to do so.

---

### Post by JRIDE on 2011-03-23
> **bodhi.zazen said:**
> No it is not.

The Gutmann theory has been debunked and you can use one pass with dd .

[http://www.nber.org/sys-admin/overwritten-data-gutmann.html](http://www.nber.org/sys-admin/overwritten-data-gutmann.html)

dd is sufficient, faster then dban, and less wear on the hard drive.

Dban was exactly what I used and took about 8 hours start to finish. Would have loved a different option that would work from boot.

---

### Post by bodhi.zazen on 2011-03-23
> **leoquant said:**
> To be honest, I really tried to understand the  software, but I gave up. I didn't saw any logic in it. (which probl. says more bout me than this software.)

Not at all. The "problem" is that rootkits are sophisticated tools and not all distros are configured the same.

So tools (such as rkhunter)can scan for the known rootkits, but it would be a poor rootkit if it were so easily detected.

So then all they (rkhunter) can really do is give you a warning along the lines of 'file "foo" might be a problem', or 'user "bar" may be misconfigured'. Along those lines it gives advice about setting system users to use /bin/false ...

So to interpret the output and warnings you need to know how your targeted (host) distro is configured and what is "normal". Typically this means running the tool on a know good fresh install (running rkhunter for the first time on a suspect system is almost always an exercise in futility due the the sheer numbers of false positives).

For Debian / Ubuntu this means starting with a known good (fresh) installation that has not connected to networking and reading

[http://www.debian.org/doc/manuals/securing-debian-howto/](http://www.debian.org/doc/manuals/securing-debian-howto/)

From there you need to know the default contents of /etc/passwd and /etc/group and what binaries are suid, etc, etc.

Once you know all that, then you can look at the output of rkhunter on a suspect system and determine:

1. This warning is the default behavior for Ubuntu.
2. That warning is a false positive.
3. foo bar, however, is a problem.

People who have done the footwork will tell you to relax and not use rkhunter. 

People who do not accept that advice ^^ have a lot of reading ahead of them.

If one is willing to go through all the various alerts and warnings, and do the requite reading will learn a bit about their system and security. This is in fact how rkhunter is intended to be used.

Truth is this is a FAQ on the forums, and there is information on how to start in the security sticky. It is asking a lot to expect people to write detailed explanations on these forums. 

A wiki page would be better, but it would be long.

Likewise, it would be ideal if the MOTU were to review rkhunter, and tweak it so that it is in fact Ubuntu specific, and less generic, and thus did not spit out endless false positives. Same with clamav.

Those who have the interest seem to be able to find the information if they look, so, that seems to work best.

If you are really interested in the issue I suggest you become more involved.

With all of that in mind, after running servers for many years, I have never seen a rootkit and on these forums I can not recall anyone identifying an intrusion via rkhunter.

The most common intrusion is a sloppy intruder who does not clean .bash_history. #2 is a sloppy intruder who does not clear the system logs or incompletely cleans the system logs.

---

### Post by bodhi.zazen on 2011-03-23
> **JRIDE said:**
> Dban was exactly what I used and took about 8 hours start to finish. Would have loved a different option that would work from boot.

You may have used it, but it does not work "from boot", you have to interact with it (and specify what driver to clean or at least hit the enter key to wipe all drives).

You may use dban if you wish, but it has the disadvantages I mentioned in my post and no advantage over dd (the dd command is a "one liner").

dd would be faster then dban as it is a single pass and it places less stress on the hardware.

---

### Post by bodhi.zazen on 2011-03-23
> **bodhi.zazen said:**
> With all of that in mind, after running servers for many years, I have never seen a rootkit and on these forums I can not recall anyone identifying an intrusion via rkhunter.

Just came across this post:

[http://forums.fedoraforum.org/showpost.php?p=1447601&postcount=2](http://forums.fedoraforum.org/showpost.php?p=1447601&postcount=2)

---

### Post by JRIDE on 2011-03-24
Well it booted some rudimentary O/S right after post then. It did take 8 hours to do what I am sure another prog could have done in 30min. Getting to the issue of us windows users freaking out after being compromised or not. I am betting most are not IT guys running a big network. What made me feel safer was your Sticky on SSH and turning off PW auth. If you are like me and are the only one that has physical access to your PC there is a way to make Ubuntu pretty much 100% secure as long as you surf smart. 
Still wouldn't have helped me as I was socially engineered into being stupid and paid.

---

### Post by EJeanmaire on 2011-03-24
> **JRIDE said:**
> Well it booted some rudimentary O/S right after post then. It did take 8 hours to do what I am sure another prog could have done in 30min. Getting to the issue of us windows users freaking out after being compromised or not. I am betting most are not IT guys running a big network. What made me feel safer was your Sticky on SSH and turning off PW auth. If you are like me and are the only one that has physical access to your PC there is a way to make Ubuntu pretty much 100% secure as long as you surf smart. 
Still wouldn't have helped me as I was socially engineered into being stupid and paid.

I have read this entire thread (sadly) and still don't see how you have come to the conclusion that you were hacked, or socially engineered.  What 'symptoms' did you experience to come to this conclusion.  Running 'security' tools as a novice will only confuse you, as you certainly have no idea what looks 'normal'.

Basically, you are chasing a mythical infection/compromise.

---

