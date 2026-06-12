---
title: "x2go : cannot connect to server since addition of x2go client"
date: 2018-03-08
forum: Server Platforms
---

### Post by Mamoth on 2018-03-08
Hello.

I have a Xubuntu virtual machine running on a physical server.
I normally connect to it using x2go although I have other means (TeamViewer, VMWare's vSphere console) in case it is needed.

Everything had been working fine since I had installed x2go server on this machine until today. I wanted to connect from this machine to another which also has x2go server, so I installed x2go client on the Xubuntu machine (precision : I was not connected through x2go when I installed x2go client, but using TeamViewer).

And now, I cannot connect to this machine using x2go any more.
I have tried with 2 different users, rebooted the machine, and even eventually uninstalled x2go client. I always get the same mistake : 

when I try to connect using my laptop, I get the following error : "*The remote proxy closed the connection while negotiating the session. This may be due to the wrong authentication credentials passed to the server.*"
I am sure of that the login / password are correct (I have been using them for months, made over a dozen attempts making sure to type them well, tried two different users and they work fine when I use TeamViewer).

I went looking at the logs in /var/log/auth.log and here is what I found :
```

Mar  8 08:50:57 XubuntuVirtualServer sshd[21903]: Accepted password for hector from 192.168.1.111 port 57386 ssh2
Mar  8 08:50:57 XubuntuVirtualServer sshd[21903]: pam_unix(sshd:session): session opened for user hector by (uid=0)
Mar  8 08:50:57 XubuntuVirtualServer systemd-logind[1122]: New session 152 of user hector.
Mar  8 08:50:57 XubuntuVirtualServer systemd: pam_unix(systemd-user:session): session opened for user hector by (uid=0)
Mar  8 08:51:00 XubuntuVirtualServer sshd[21978]: error: connect_to localhost port 37530: failed.
Mar  8 08:51:00 XubuntuVirtualServer sshd[21978]: Non-public channel 0, type 11.
Mar  8 08:51:00 XubuntuVirtualServer sshd[21978]: Disconnecting: Received ieof for nonexistent channel 0.
Mar  8 08:51:00 XubuntuVirtualServer sshd[21903]: pam_unix(sshd:session): session closed for user hector
Mar  8 08:51:01 XubuntuVirtualServer systemd-logind[1122]: Removed session 152.
Mar  8 08:51:01 XubuntuVirtualServer systemd: pam_unix(systemd-user:session): session closed for user hector
Mar  8 08:51:19 XubuntuVirtualServer sshd[22390]: Accepted password for hector from 192.168.1.111 port 57394 ssh2
Mar  8 08:51:19 XubuntuVirtualServer sshd[22390]: pam_unix(sshd:session): session opened for user hector by (uid=0)
Mar  8 08:51:19 XubuntuVirtualServer systemd-logind[1122]: New session 153 of user hector.
Mar  8 08:51:19 XubuntuVirtualServer systemd: pam_unix(systemd-user:session): session opened for user hector by (uid=0)
Mar  8 08:51:29 XubuntuVirtualServer su[22519]: Successful su for hector by root
Mar  8 08:51:29 XubuntuVirtualServer su[22519]: + ??? root:hector
Mar  8 08:51:29 XubuntuVirtualServer su[22519]: pam_unix(su:session): session opened for user hector by (uid=0)
Mar  8 08:51:29 XubuntuVirtualServer systemd-logind[1122]: New session c15 of user hector.
Mar  8 08:51:29 XubuntuVirtualServer su[22519]: pam_unix(su:session): session closed for user hector
Mar  8 08:51:29 XubuntuVirtualServer systemd-logind[1122]: Removed session c15.
Mar  8 08:51:29 XubuntuVirtualServer su[22531]: Successful su for hector by root
Mar  8 08:51:29 XubuntuVirtualServer su[22531]: + ??? root:hector
Mar  8 08:51:29 XubuntuVirtualServer su[22531]: pam_unix(su:session): session opened for user hector by (uid=0)
Mar  8 08:51:29 XubuntuVirtualServer systemd-logind[1122]: New session c16 of user hector.
Mar  8 08:51:30 XubuntuVirtualServer su[22531]: pam_unix(su:session): session closed for user hector
Mar  8 08:51:30 XubuntuVirtualServer systemd-logind[1122]: Removed session c16.
Mar  8 08:51:30 XubuntuVirtualServer sshd[22421]: Received disconnect from 192.168.1.111 port 57394:11: Bye Bye
Mar  8 08:51:30 XubuntuVirtualServer sshd[22421]: Disconnected from 192.168.1.111 port 57394
Mar  8 08:51:30 XubuntuVirtualServer sshd[22390]: pam_unix(sshd:session): session closed for user hector
Mar  8 08:51:30 XubuntuVirtualServer systemd-logind[1122]: Removed session 153.
Mar  8 08:51:30 XubuntuVirtualServer systemd: pam_unix(systemd-user:session): session closed for user hector
Mar  8 08:51:31 XubuntuVirtualServer sshd[22545]: Accepted password for hector from 192.168.1.111 port 57396 ssh2
Mar  8 08:51:31 XubuntuVirtualServer sshd[22545]: pam_unix(sshd:session): session opened for user hector by (uid=0)
Mar  8 08:51:31 XubuntuVirtualServer systemd-logind[1122]: New session 154 of user hector.
Mar  8 08:51:31 XubuntuVirtualServer systemd: pam_unix(systemd-user:session): session opened for user hector by (uid=0)
Mar  8 08:51:34 XubuntuVirtualServer sshd[22583]: error: connect_to localhost port 35105: failed.
Mar  8 08:51:34 XubuntuVirtualServer sshd[22583]: Non-public channel 0, type 11.
Mar  8 08:51:34 XubuntuVirtualServer sshd[22583]: Disconnecting: Received ieof for nonexistent channel 0.
Mar  8 08:51:34 XubuntuVirtualServer sshd[22545]: pam_unix(sshd:session): session closed for user hector
Mar  8 08:51:34 XubuntuVirtualServer systemd-logind[1122]: Removed session 154.
Mar  8 08:51:34 XubuntuVirtualServer systemd: pam_unix(systemd-user:session): session closed for user hector
Mar  8 08:52:02 XubuntuVirtualServer su[23138]: Successful su for hector by root
Mar  8 08:52:02 XubuntuVirtualServer su[23138]: + ??? root:hector
Mar  8 08:52:02 XubuntuVirtualServer su[23138]: pam_unix(su:session): session opened for user hector by (uid=0)
Mar  8 08:52:02 XubuntuVirtualServer systemd-logind[1122]: New session c17 of user hector.
Mar  8 08:52:02 XubuntuVirtualServer systemd: pam_unix(systemd-user:session): session opened for user hector by (uid=0)
Mar  8 08:52:03 XubuntuVirtualServer su[23138]: pam_unix(su:session): session closed for user hector
Mar  8 08:52:03 XubuntuVirtualServer su[23155]: Successful su for hector by root
Mar  8 08:52:03 XubuntuVirtualServer systemd-logind[1122]: Removed session c17.
Mar  8 08:52:03 XubuntuVirtualServer su[23155]: + ??? root:hector
Mar  8 08:52:03 XubuntuVirtualServer su[23155]: pam_unix(su:session): session opened for user hector by (uid=0)
Mar  8 08:52:03 XubuntuVirtualServer systemd: pam_unix(systemd-user:session): session closed for user hector
Mar  8 08:52:03 XubuntuVirtualServer systemd-logind[1122]: New session c18 of user hector.
Mar  8 08:52:03 XubuntuVirtualServer systemd: pam_unix(systemd-user:session): session opened for user hector by (uid=0)
Mar  8 08:52:03 XubuntuVirtualServer systemd-logind[1122]: System is rebooting.
Mar  8 08:52:03 XubuntuVirtualServer su[23155]: pam_unix(su:session): session closed for user hector
Mar  8 08:53:52 XubuntuVirtualServer systemd-logind[1126]: New seat seat0.
Mar  8 08:53:52 XubuntuVirtualServer systemd-logind[1126]: Watching system buttons on /dev/input/event0 (Power Button)
Mar  8 08:53:53 XubuntuVirtualServer sshd[1287]: Server listening on 0.0.0.0 port 22.
Mar  8 08:53:53 XubuntuVirtualServer sshd[1287]: Server listening on :: port 22.
Mar  8 08:53:54 XubuntuVirtualServer sshd[1287]: Received SIGHUP; restarting.
Mar  8 08:53:54 XubuntuVirtualServer sshd[1287]: Server listening on 0.0.0.0 port 22.
Mar  8 08:53:54 XubuntuVirtualServer sshd[1287]: Server listening on :: port 22.
Mar  8 08:53:54 XubuntuVirtualServer sshd[1287]: Received SIGHUP; restarting.
Mar  8 08:53:55 XubuntuVirtualServer sshd[1287]: Server listening on 0.0.0.0 port 22.
Mar  8 08:53:55 XubuntuVirtualServer sshd[1287]: Server listening on :: port 22.
Mar  8 08:53:56 XubuntuVirtualServer lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Mar  8 08:53:56 XubuntuVirtualServer lightdm: PAM adding faulty module: pam_kwallet.so
Mar  8 08:53:56 XubuntuVirtualServer lightdm: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared object file: No such file or directory
Mar  8 08:53:56 XubuntuVirtualServer lightdm: PAM adding faulty module: pam_kwallet5.so
Mar  8 08:53:56 XubuntuVirtualServer lightdm: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)
Mar  8 08:53:56 XubuntuVirtualServer systemd-logind[1126]: New session c1 of user lightdm.
Mar  8 08:53:56 XubuntuVirtualServer systemd: pam_unix(systemd-user:session): session opened for user lightdm by (uid=0)
Mar  8 08:54:01 XubuntuVirtualServer lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Mar  8 08:54:01 XubuntuVirtualServer lightdm: PAM adding faulty module: pam_kwallet.so
Mar  8 08:54:01 XubuntuVirtualServer lightdm: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared object file: No such file or directory
Mar  8 08:54:01 XubuntuVirtualServer lightdm: PAM adding faulty module: pam_kwallet5.so
Mar  8 08:54:01 XubuntuVirtualServer lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "hector"
Mar  8 08:54:19 XubuntuVirtualServer sshd[1869]: Accepted password for hector from 192.168.1.111 port 57422 ssh2
Mar  8 08:54:19 XubuntuVirtualServer sshd[1869]: pam_unix(sshd:session): session opened for user hector by (uid=0)
Mar  8 08:54:19 XubuntuVirtualServer systemd-logind[1126]: New session 1 of user hector.
Mar  8 08:54:19 XubuntuVirtualServer systemd: pam_unix(systemd-user:session): session opened for user hector by (uid=0)
Mar  8 08:54:23 XubuntuVirtualServer sshd[1943]: error: connect_to localhost port 57440: failed.
Mar  8 08:54:23 XubuntuVirtualServer sshd[1943]: Non-public channel 0, type 11.
Mar  8 08:54:23 XubuntuVirtualServer sshd[1943]: Disconnecting: Received ieof for nonexistent channel 0.
Mar  8 08:54:23 XubuntuVirtualServer sshd[1869]: pam_unix(sshd:session): session closed for user hector
Mar  8 08:54:23 XubuntuVirtualServer systemd-logind[1126]: Removed session 1.
Mar  8 08:54:23 XubuntuVirtualServer systemd: pam_unix(systemd-user:session): session closed for user hector
Mar  8 08:54:52 XubuntuVirtualServer su[2457]: Successful su for hector by root
Mar  8 08:54:52 XubuntuVirtualServer su[2457]: + ??? root:hector
Mar  8 08:54:52 XubuntuVirtualServer su[2457]: pam_unix(su:session): session opened for user hector by (uid=0)
Mar  8 08:54:52 XubuntuVirtualServer systemd-logind[1126]: New session c2 of user hector.
Mar  8 08:54:52 XubuntuVirtualServer systemd: pam_unix(systemd-user:session): session opened for user hector by (uid=0)
Mar  8 08:54:53 XubuntuVirtualServer su[2457]: pam_unix(su:session): session closed for user hector
Mar  8 08:54:53 XubuntuVirtualServer systemd-logind[1126]: Removed session c2.
Mar  8 08:54:53 XubuntuVirtualServer su[2476]: Successful su for hector by root
Mar  8 08:54:53 XubuntuVirtualServer su[2476]: + ??? root:hector
Mar  8 08:54:53 XubuntuVirtualServer su[2476]: pam_unix(su:session): session opened for user hector by (uid=0)
Mar  8 08:54:53 XubuntuVirtualServer systemd-logind[1126]: New session c3 of user hector.
Mar  8 08:54:53 XubuntuVirtualServer systemd: pam_unix(systemd-user:session): session closed for user hector
Mar  8 08:54:53 XubuntuVirtualServer systemd: pam_unix(systemd-user:session): session opened for user hector by (uid=0)
Mar  8 08:54:53 XubuntuVirtualServer su[2476]: pam_unix(su:session): session closed for user hector
Mar  8 08:54:53 XubuntuVirtualServer systemd-logind[1126]: Removed session c3.
Mar  8 08:54:53 XubuntuVirtualServer systemd: pam_unix(systemd-user:session): session closed for user hector
Mar  8 08:54:58 XubuntuVirtualServer sshd[2534]: Accepted password for hector from 192.168.1.111 port 57436 ssh2
Mar  8 08:54:58 XubuntuVirtualServer sshd[2534]: pam_unix(sshd:session): session opened for user hector by (uid=0)
Mar  8 08:54:58 XubuntuVirtualServer systemd-logind[1126]: New session 2 of user hector.
Mar  8 08:54:58 XubuntuVirtualServer systemd: pam_unix(systemd-user:session): session opened for user hector by (uid=0)
Mar  8 08:55:01 XubuntuVirtualServer CRON[2804]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  8 08:55:01 XubuntuVirtualServer CRON[2804]: pam_unix(cron:session): session closed for user root
Mar  8 08:55:01 XubuntuVirtualServer sshd[2566]: error: connect_to localhost port 40746: failed.
Mar  8 08:55:01 XubuntuVirtualServer sshd[2566]: Non-public channel 0, type 11.
Mar  8 08:55:01 XubuntuVirtualServer sshd[2566]: Disconnecting: Received ieof for nonexistent channel 0.
Mar  8 08:55:01 XubuntuVirtualServer sshd[2534]: pam_unix(sshd:session): session closed for user hector
Mar  8 08:55:01 XubuntuVirtualServer systemd-logind[1126]: Removed session 2.
Mar  8 08:55:01 XubuntuVirtualServer systemd: pam_unix(systemd-user:session): session closed for user hector
Mar  8 08:55:18 XubuntuVirtualServer lightdm: pam_unix(lightdm-greeter:session): session closed for user lightdm
Mar  8 08:55:18 XubuntuVirtualServer lightdm: pam_unix(lightdm:session): session opened for user hector by (uid=0)
Mar  8 08:55:18 XubuntuVirtualServer systemd-logind[1126]: New session c4 of user hector.
Mar  8 08:55:18 XubuntuVirtualServer systemd: pam_unix(systemd-user:session): session opened for user hector by (uid=0)
Mar  8 08:55:19 XubuntuVirtualServer su[3150]: Successful su for hector by root
Mar  8 08:55:19 XubuntuVirtualServer su[3150]: + ??? root:hector
Mar  8 08:55:19 XubuntuVirtualServer su[3150]: pam_unix(su:session): session opened for user hector by (uid=0)
Mar  8 08:55:19 XubuntuVirtualServer systemd-logind[1126]: New session c5 of user hector.
Mar  8 08:55:19 XubuntuVirtualServer su[3153]: Successful su for hector by root
Mar  8 08:55:19 XubuntuVirtualServer su[3153]: + ??? root:hector
Mar  8 08:55:19 XubuntuVirtualServer su[3153]: pam_unix(su:session): session opened for user hector by (uid=0)
Mar  8 08:55:19 XubuntuVirtualServer systemd-logind[1126]: New session c6 of user hector.
Mar  8 08:55:19 XubuntuVirtualServer su[3150]: pam_unix(su:session): session closed for user hector
Mar  8 08:55:19 XubuntuVirtualServer su[3153]: pam_unix(su:session): session closed for user hector
Mar  8 08:55:19 XubuntuVirtualServer systemd-logind[1126]: Removed session c5.
Mar  8 08:55:19 XubuntuVirtualServer systemd-logind[1126]: Removed session c6.
Mar  8 08:55:20 XubuntuVirtualServer gnome-keyring-daemon[2995]: The SSH agent was already initialized
Mar  8 08:55:20 XubuntuVirtualServer gnome-keyring-daemon[2995]: The Secret Service was already initialized
Mar  8 08:55:20 XubuntuVirtualServer gnome-keyring-daemon[2995]: The PKCS#11 component was already initialized
Mar  8 08:55:22 XubuntuVirtualServer polkitd(authority=local): Registered Authentication Agent for unix-session:c4 (system bus name :1.58 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale fr_FR.UTF-8)
Mar  8 08:55:27 XubuntuVirtualServer pkexec: pam_unix(polkit-1:session): session opened for user root by (uid=1000)
Mar  8 08:55:27 XubuntuVirtualServer pkexec: pam_systemd(polkit-1:session): Cannot create session: Already running in a session
Mar  8 08:55:27 XubuntuVirtualServer pkexec[3591]: hector: Executing command [USER=root] [TTY=unknown] [CWD=/home/hector] [COMMAND=/usr/lib/update-notifier/package-system-locked]
Mar  8 08:55:30 XubuntuVirtualServer su[3701]: Successful su for hector by root
Mar  8 08:55:30 XubuntuVirtualServer su[3701]: + ??? root:hector
Mar  8 08:55:30 XubuntuVirtualServer su[3701]: pam_unix(su:session): session opened for user hector by (uid=0)
Mar  8 08:55:30 XubuntuVirtualServer systemd-logind[1126]: New session c7 of user hector.
Mar  8 08:55:30 XubuntuVirtualServer su[3701]: pam_unix(su:session): session closed for user hector
Mar  8 08:55:30 XubuntuVirtualServer systemd-logind[1126]: Removed session c7.
Mar  8 08:55:30 XubuntuVirtualServer su[3717]: Successful su for hector by root
Mar  8 08:55:30 XubuntuVirtualServer su[3717]: + ??? root:hector
Mar  8 08:55:30 XubuntuVirtualServer su[3717]: pam_unix(su:session): session opened for user hector by (uid=0)
Mar  8 08:55:30 XubuntuVirtualServer systemd-logind[1126]: New session c8 of user hector.
Mar  8 08:55:31 XubuntuVirtualServer su[3717]: pam_unix(su:session): session closed for user hector
Mar  8 08:55:31 XubuntuVirtualServer systemd-logind[1126]: Removed session c8.
Mar  8 08:55:48 XubuntuVirtualServer dbus[1143]: [system] Failed to activate service 'org.bluez': timed out
Mar  8 08:55:56 XubuntuVirtualServer systemd-logind[1126]: Removed session c1.
Mar  8 08:55:56 XubuntuVirtualServer systemd: pam_unix(systemd-user:session): session closed for user lightdm
Mar  8 08:56:13 XubuntuVirtualServer dbus[1143]: [system] Failed to activate service 'org.bluez': timed out
Mar  8 09:05:01 XubuntuVirtualServer CRON[6238]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  8 09:05:01 XubuntuVirtualServer CRON[6238]: pam_unix(cron:session): session closed for user root
Mar  8 09:10:40 XubuntuVirtualServer su[7695]: Successful su for hector by root
Mar  8 09:10:40 XubuntuVirtualServer su[7695]: + ??? root:hector
Mar  8 09:10:40 XubuntuVirtualServer su[7695]: pam_unix(su:session): session opened for user hector by (uid=0)
Mar  8 09:10:40 XubuntuVirtualServer systemd-logind[1126]: New session c9 of user hector.
Mar  8 09:10:40 XubuntuVirtualServer su[7695]: pam_unix(su:session): session closed for user hector
Mar  8 09:10:40 XubuntuVirtualServer systemd-logind[1126]: Removed session c9.
Mar  8 09:12:19 XubuntuVirtualServer systemd-logind[1126]: System is rebooting.
Mar  8 09:14:01 XubuntuVirtualServer systemd-logind[1173]: New seat seat0.
Mar  8 09:14:01 XubuntuVirtualServer systemd-logind[1173]: Watching system buttons on /dev/input/event0 (Power Button)
Mar  8 09:14:02 XubuntuVirtualServer sshd[1292]: Server listening on 0.0.0.0 port 22.
Mar  8 09:14:02 XubuntuVirtualServer sshd[1292]: Server listening on :: port 22.
Mar  8 09:14:04 XubuntuVirtualServer sshd[1292]: Received SIGHUP; restarting.
Mar  8 09:14:04 XubuntuVirtualServer sshd[1292]: Server listening on 0.0.0.0 port 22.
Mar  8 09:14:04 XubuntuVirtualServer sshd[1292]: Server listening on :: port 22.
Mar  8 09:14:04 XubuntuVirtualServer sshd[1292]: Received SIGHUP; restarting.
Mar  8 09:14:04 XubuntuVirtualServer sshd[1292]: Server listening on 0.0.0.0 port 22.
Mar  8 09:14:04 XubuntuVirtualServer sshd[1292]: Server listening on :: port 22.
Mar  8 09:14:05 XubuntuVirtualServer lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Mar  8 09:14:05 XubuntuVirtualServer lightdm: PAM adding faulty module: pam_kwallet.so
Mar  8 09:14:05 XubuntuVirtualServer lightdm: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared object file: No such file or directory
Mar  8 09:14:05 XubuntuVirtualServer lightdm: PAM adding faulty module: pam_kwallet5.so
Mar  8 09:14:06 XubuntuVirtualServer lightdm: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)
Mar  8 09:14:06 XubuntuVirtualServer systemd-logind[1173]: New session c1 of user lightdm.
Mar  8 09:14:06 XubuntuVirtualServer systemd: pam_unix(systemd-user:session): session opened for user lightdm by (uid=0)
Mar  8 09:14:10 XubuntuVirtualServer lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Mar  8 09:14:10 XubuntuVirtualServer lightdm: PAM adding faulty module: pam_kwallet.so
Mar  8 09:14:10 XubuntuVirtualServer lightdm: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared object file: No such file or directory
Mar  8 09:14:10 XubuntuVirtualServer lightdm: PAM adding faulty module: pam_kwallet5.so
Mar  8 09:14:10 XubuntuVirtualServer lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "hector"
Mar  8 09:14:45 XubuntuVirtualServer sshd[1947]: Accepted password for hector from 192.168.1.111 port 57578 ssh2
Mar  8 09:14:45 XubuntuVirtualServer sshd[1947]: pam_unix(sshd:session): session opened for user hector by (uid=0)
Mar  8 09:14:45 XubuntuVirtualServer systemd-logind[1173]: New session 1 of user hector.
Mar  8 09:14:45 XubuntuVirtualServer systemd: pam_unix(systemd-user:session): session opened for user hector by (uid=0)
Mar  8 09:14:49 XubuntuVirtualServer sshd[2019]: error: connect_to localhost port 51750: failed.
Mar  8 09:14:49 XubuntuVirtualServer sshd[2019]: Non-public channel 0, type 11.
Mar  8 09:14:49 XubuntuVirtualServer sshd[2019]: Disconnecting: Received ieof for nonexistent channel 0.
Mar  8 09:14:49 XubuntuVirtualServer sshd[1947]: pam_unix(sshd:session): session closed for user hector
Mar  8 09:14:49 XubuntuVirtualServer systemd-logind[1173]: Removed session 1.
Mar  8 09:14:49 XubuntuVirtualServer systemd: pam_unix(systemd-user:session): session closed for user hector
Mar  8 09:15:01 XubuntuVirtualServer CRON[2392]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  8 09:15:01 XubuntuVirtualServer CRON[2392]: pam_unix(cron:session): session closed for user root
Mar  8 09:15:18 XubuntuVirtualServer su[2532]: Successful su for hector by root
Mar  8 09:15:18 XubuntuVirtualServer su[2532]: + ??? root:hector
Mar  8 09:15:18 XubuntuVirtualServer su[2532]: pam_unix(su:session): session opened for user hector by (uid=0)
Mar  8 09:15:18 XubuntuVirtualServer systemd-logind[1173]: New session c2 of user hector.
Mar  8 09:15:19 XubuntuVirtualServer systemd: pam_unix(systemd-user:session): session opened for user hector by (uid=0)
Mar  8 09:15:19 XubuntuVirtualServer su[2532]: pam_unix(su:session): session closed for user hector
Mar  8 09:15:19 XubuntuVirtualServer systemd-logind[1173]: Removed session c2.
Mar  8 09:15:19 XubuntuVirtualServer su[2550]: Successful su for hector by root
Mar  8 09:15:19 XubuntuVirtualServer su[2550]: + ??? root:hector
Mar  8 09:15:19 XubuntuVirtualServer su[2550]: pam_unix(su:session): session opened for user hector by (uid=0)
Mar  8 09:15:19 XubuntuVirtualServer systemd: pam_unix(systemd-user:session): session closed for user hector
Mar  8 09:15:19 XubuntuVirtualServer systemd-logind[1173]: New session c3 of user hector.
Mar  8 09:15:19 XubuntuVirtualServer systemd: pam_unix(systemd-user:session): session opened for user hector by (uid=0)
Mar  8 09:15:19 XubuntuVirtualServer su[2550]: pam_unix(su:session): session closed for user hector
Mar  8 09:15:19 XubuntuVirtualServer systemd-logind[1173]: Removed session c3.
Mar  8 09:15:19 XubuntuVirtualServer systemd: pam_unix(systemd-user:session): session closed for user hector
Mar  8 09:15:32 XubuntuVirtualServer sshd[2635]: Accepted password for hector from 192.168.1.111 port 57586 ssh2
Mar  8 09:15:32 XubuntuVirtualServer sshd[2635]: pam_unix(sshd:session): session opened for user hector by (uid=0)
Mar  8 09:15:32 XubuntuVirtualServer systemd-logind[1173]: New session 3 of user hector.
Mar  8 09:15:32 XubuntuVirtualServer systemd: pam_unix(systemd-user:session): session opened for user hector by (uid=0)
Mar  8 09:15:35 XubuntuVirtualServer sshd[2667]: error: connect_to localhost port 38440: failed.
Mar  8 09:15:35 XubuntuVirtualServer sshd[2667]: Non-public channel 0, type 11.
Mar  8 09:15:35 XubuntuVirtualServer sshd[2667]: Disconnecting: Received ieof for nonexistent channel 0.
Mar  8 09:15:35 XubuntuVirtualServer sshd[2635]: pam_unix(sshd:session): session closed for user hector
Mar  8 09:15:35 XubuntuVirtualServer systemd-logind[1173]: Removed session 3.
Mar  8 09:15:35 XubuntuVirtualServer systemd: pam_unix(systemd-user:session): session closed for user hector
Mar  8 09:15:45 XubuntuVirtualServer sshd[3016]: Accepted password for hector from 192.168.1.111 port 57594 ssh2
Mar  8 09:15:45 XubuntuVirtualServer sshd[3016]: pam_unix(sshd:session): session opened for user hector by (uid=0)
Mar  8 09:15:45 XubuntuVirtualServer systemd-logind[1173]: New session 4 of user hector.
Mar  8 09:15:45 XubuntuVirtualServer systemd: pam_unix(systemd-user:session): session opened for user hector by (uid=0)
Mar  8 09:15:57 XubuntuVirtualServer sshd[3048]: error: connect_to localhost port 47746: failed.
Mar  8 09:15:57 XubuntuVirtualServer sshd[3048]: Non-public channel 0, type 11.
Mar  8 09:15:57 XubuntuVirtualServer sshd[3048]: Disconnecting: Received ieof for nonexistent channel 0.
Mar  8 09:15:57 XubuntuVirtualServer sshd[3016]: pam_unix(sshd:session): session closed for user hector
Mar  8 09:15:57 XubuntuVirtualServer systemd-logind[1173]: Removed session 4.
Mar  8 09:15:57 XubuntuVirtualServer systemd: pam_unix(systemd-user:session): session closed for user hector
Mar  8 09:16:26 XubuntuVirtualServer su[3726]: Successful su for hector by root
Mar  8 09:16:26 XubuntuVirtualServer su[3726]: + ??? root:hector
Mar  8 09:16:26 XubuntuVirtualServer su[3726]: pam_unix(su:session): session opened for user hector by (uid=0)
Mar  8 09:16:26 XubuntuVirtualServer systemd-logind[1173]: New session c4 of user hector.
Mar  8 09:16:26 XubuntuVirtualServer systemd: pam_unix(systemd-user:session): session opened for user hector by (uid=0)
Mar  8 09:16:26 XubuntuVirtualServer su[3726]: pam_unix(su:session): session closed for user hector
Mar  8 09:16:26 XubuntuVirtualServer systemd-logind[1173]: Removed session c4.
Mar  8 09:16:26 XubuntuVirtualServer su[3744]: Successful su for hector by root
Mar  8 09:16:26 XubuntuVirtualServer su[3744]: + ??? root:hector
Mar  8 09:16:26 XubuntuVirtualServer su[3744]: pam_unix(su:session): session opened for user hector by (uid=0)
Mar  8 09:16:26 XubuntuVirtualServer systemd: pam_unix(systemd-user:session): session closed for user hector
Mar  8 09:16:26 XubuntuVirtualServer systemd-logind[1173]: New session c5 of user hector.
Mar  8 09:16:26 XubuntuVirtualServer systemd: pam_unix(systemd-user:session): session opened for user hector by (uid=0)
Mar  8 09:16:26 XubuntuVirtualServer su[3744]: pam_unix(su:session): session closed for user hector
Mar  8 09:16:26 XubuntuVirtualServer systemd-logind[1173]: Removed session c5.
Mar  8 09:16:26 XubuntuVirtualServer systemd: pam_unix(systemd-user:session): session closed for user hector
Mar  8 09:17:01 XubuntuVirtualServer CRON[3919]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  8 09:17:01 XubuntuVirtualServer CRON[3919]: pam_unix(cron:session): session closed for user root
Mar  8 09:21:26 XubuntuVirtualServer lightdm: pam_unix(lightdm-greeter:session): session closed for user lightdm
Mar  8 09:21:26 XubuntuVirtualServer lightdm: pam_unix(lightdm:session): session opened for user hector by (uid=0)
Mar  8 09:21:26 XubuntuVirtualServer systemd-logind[1173]: New session c6 of user hector.
Mar  8 09:21:26 XubuntuVirtualServer systemd: pam_unix(systemd-user:session): session opened for user hector by (uid=0)
Mar  8 09:21:27 XubuntuVirtualServer su[5221]: Successful su for hector by root
Mar  8 09:21:27 XubuntuVirtualServer su[5221]: + ??? root:hector
Mar  8 09:21:27 XubuntuVirtualServer su[5221]: pam_unix(su:session): session opened for user hector by (uid=0)
Mar  8 09:21:27 XubuntuVirtualServer systemd-logind[1173]: New session c7 of user hector.
Mar  8 09:21:27 XubuntuVirtualServer su[5224]: Successful su for hector by root
Mar  8 09:21:27 XubuntuVirtualServer su[5224]: + ??? root:hector
Mar  8 09:21:27 XubuntuVirtualServer su[5224]: pam_unix(su:session): session opened for user hector by (uid=0)
Mar  8 09:21:27 XubuntuVirtualServer systemd-logind[1173]: New session c8 of user hector.
Mar  8 09:21:27 XubuntuVirtualServer su[5221]: pam_unix(su:session): session closed for user hector
Mar  8 09:21:27 XubuntuVirtualServer su[5224]: pam_unix(su:session): session closed for user hector
Mar  8 09:21:27 XubuntuVirtualServer systemd-logind[1173]: Removed session c7.
Mar  8 09:21:27 XubuntuVirtualServer systemd-logind[1173]: Removed session c8.
Mar  8 09:21:29 XubuntuVirtualServer gnome-keyring-daemon[5078]: The SSH agent was already initialized
Mar  8 09:21:29 XubuntuVirtualServer gnome-keyring-daemon[5078]: The Secret Service was already initialized
Mar  8 09:21:29 XubuntuVirtualServer gnome-keyring-daemon[5078]: The PKCS#11 component was already initialized
Mar  8 09:21:30 XubuntuVirtualServer polkitd(authority=local): Registered Authentication Agent for unix-session:c6 (system bus name :1.64 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale fr_FR.UTF-8)
Mar  8 09:21:35 XubuntuVirtualServer pkexec: pam_unix(polkit-1:session): session opened for user root by (uid=1000)
Mar  8 09:21:35 XubuntuVirtualServer pkexec: pam_systemd(polkit-1:session): Cannot create session: Already running in a session
Mar  8 09:21:35 XubuntuVirtualServer pkexec[5646]: hector: Executing command [USER=root] [TTY=unknown] [CWD=/home/hector] [COMMAND=/usr/lib/update-notifier/package-system-locked]
Mar  8 09:21:46 XubuntuVirtualServer systemd-logind[1173]: Removed session c1.
Mar  8 09:21:46 XubuntuVirtualServer systemd: pam_unix(systemd-user:session): session closed for user lightdm
Mar  8 09:21:56 XubuntuVirtualServer dbus[1107]: [system] Failed to activate service 'org.bluez': timed out
Mar  8 09:22:21 XubuntuVirtualServer dbus[1107]: [system] Failed to activate service 'org.bluez': timed out
Mar  8 09:22:24 XubuntuVirtualServer sudo:  hector : TTY=pts/6 ; PWD=/home/hector ; USER=root ; COMMAND=/usr/sbin/service x2goserver restart
Mar  8 09:22:24 XubuntuVirtualServer sudo: pam_unix(sudo:session): session opened for user root by hector(uid=0)
Mar  8 09:22:24 XubuntuVirtualServer sudo: pam_unix(sudo:session): session closed for user root
Mar  8 09:23:07 XubuntuVirtualServer sshd[6182]: Accepted password for bob from 192.168.1.111 port 57758 ssh2
Mar  8 09:23:07 XubuntuVirtualServer systemd-logind[1173]: New session 6 of user bob.
Mar  8 09:23:07 XubuntuVirtualServer systemd: pam_unix(systemd-user:session): session opened for user bob by (uid=0)
Mar  8 09:23:10 XubuntuVirtualServer sshd[6213]: error: connect_to localhost port 50681: failed.
Mar  8 09:23:10 XubuntuVirtualServer sshd[6213]: Non-public channel 0, type 11.
Mar  8 09:23:10 XubuntuVirtualServer sshd[6213]: Disconnecting: Received ieof for nonexistent channel 0.
Mar  8 09:23:10 XubuntuVirtualServer sshd[6182]: pam_unix(sshd:session): session closed for user bob
Mar  8 09:23:10 XubuntuVirtualServer systemd-logind[1173]: Removed session 6.
Mar  8 09:23:10 XubuntuVirtualServer systemd: pam_unix(systemd-user:session): session closed for user bob
Mar  8 09:23:20 XubuntuVirtualServer sshd[6564]: Accepted password for bob from 192.168.1.111 port 57766 ssh2
Mar  8 09:23:20 XubuntuVirtualServer sshd[6564]: pam_unix(sshd:session): session opened for user bob by (uid=0)
Mar  8 09:23:20 XubuntuVirtualServer systemd-logind[1173]: New session 7 of user bob.
Mar  8 09:23:20 XubuntuVirtualServer systemd: pam_unix(systemd-user:session): session opened for user bob by (uid=0)
Mar  8 09:23:45 XubuntuVirtualServer sudo:  hector : TTY=pts/6 ; PWD=/home/hector ; USER=root ; COMMAND=/usr/sbin/service x2goserver status
Mar  8 09:23:45 XubuntuVirtualServer sudo: pam_unix(sudo:session): session opened for user root by hector(uid=0)
Mar  8 09:23:07 XubuntuVirtualServer sshd[6182]: pam_unix(sshd:session): session opened for user bob by (uid=0)


```I am unsure if these logs don't mix ssh connections for x2go and TeamViewer. So to be sure, all connections for user Bob were tried using x2go (those tried with user Hector were with either x2go or TeamViewer).

What I can see is the lines with "*error: connect_to localhost port <a different port number every time>: failed*".

Anybody has clues ?

I need this x2go connection to work.

---

### Post by TheFu on 2018-03-08
I've never tried to use x2go from a system running x2go server already.  If the 2 servers are on a 100Mbps network or faster, I just use X11 forwarding via ssh using ssh-keys.  I'm positive this works and works really well. No need for x2go.

x2go uses ssh, it is part of the NX protocol.  Teamviewer does not.

Always prefer ssh-keys - actually making keys required for internet-based connections is a best practice.

Sorry I cannot help.

I'm seeing root in the logs.  Is there any use of root with ssh?

---

### Post by wildmanne39 on 2018-03-08
*Thread moved to **Server Platforms, a more appropriate forum**.*

---

### Post by Mamoth on 2018-03-09
Hello.
I tried uninstalling all the x2go packages (x2goclient, x2goserver and x2goserver-xsession) and reinstalling the server packages (x2goserver and x2goserver-xsession).
It did not work but the error message is now different : "The connection with the remote server was shut down. Please check the state of your network connection."

The connection works perfectly and I have disabled the firewall, just in case.

If somebody can suggest where to look for hints of the problem ...

---

### Post by Mamoth on 2018-03-09
I have tried again reinstalling after I noticed that the installed packages with 'x2go' in their name or description were different on this machine compared to another one that I have also with x2go server running without problem (also XFCE but Debian 9, not Ubuntu).
Still no change. I noticed that the users were not part of the x2gouser group so I added them. Still no change.

I did a *sudo systemctl status sshd* and what I got was :
```
&#9679; ssh.service - OpenBSD Secure Shell server
   Loaded: loaded (/lib/systemd/system/ssh.service; enabled; vendor preset: enabled)
   Active: active (running) since ven. 2018-03-09 18:06:30 CET; 3min 38s ago
  Process: 1376 ExecReload=/bin/kill -HUP $MAINPID (code=exited, status=0/SUCCESS)
 Main PID: 1223 (sshd)
   CGroup: /system.slice/ssh.service
           &#9492;&#9472;1223 /usr/sbin/sshd -D

mars 09 18:06:30 ServeurITeN sshd[1223]: Server listening on 0.0.0.0 port 22.
mars 09 18:06:30 ServeurITeN sshd[1223]: Server listening on :: port 22.
mars 09 18:06:30 ServeurITeN systemd[1]: Started OpenBSD Secure Shell server.
mars 09 18:06:31 ServeurITeN systemd[1]: Reloading OpenBSD Secure Shell server.
mars 09 18:06:31 ServeurITeN systemd[1]: Reloaded OpenBSD Secure Shell server.
mars 09 18:06:31 ServeurITeN sshd[1223]: Received SIGHUP; restarting.
mars 09 18:06:31 ServeurITeN sshd[1223]: Server listening on 0.0.0.0 port 22.
mars 09 18:06:31 ServeurITeN sshd[1223]: Server listening on :: port 22.
mars 09 18:07:39 ServeurITeN sshd[1820]: Accepted password for hectorfrom 192.168.1.111 port 58754 ssh2
mars 09 18:07:39 ServeurITeN sshd[1820]: pam_unix(sshd:session): session opened for user hectorby (uid=0)


```So it looks like ssh is running ok.

And this is what I get when doing a *sudo systemctl status x2goserver* :
```
&#9679; x2goserver.service - X2Go Server Daemon
   Loaded: loaded (/lib/systemd/system/x2goserver.service; enabled; vendor preset: enabled)
   Active: active (running) since ven. 2018-03-09 18:06:29 CET; 12min ago
  Process: 1047 ExecStart=/usr/sbin/x2gocleansessions (code=exited, status=0/SUCCESS)
 Main PID: 1253 (x2gocleansessio)
   CGroup: /system.slice/x2goserver.service
           &#9492;&#9472;1253 /usr/bin/perl /usr/sbin/x2gocleansessions

mars 09 18:06:27 ServeurITeN systemd[1]: Starting X2Go Server Daemon...
mars 09 18:06:29 ServeurITeN systemd[1]: Started X2Go Server Daemon.
mars 09 18:07:43 ServeurITeN /usr/sbin/x2gocleansessions[1253]: hector-50-1520615261_stDXFCE_dp24: state file for this session does not exist: /tmp/.x2go-hector/C-hector-50-1520615261_stDXFCE_dp24/state (this can be ignored during session startups)
``` I first thought I had something because of the last line but on the other machine where x2go works, there is also this last line ...

---

### Post by Mamoth on 2018-03-09
And after checking on the working machine, it seems that the user that connects does not need to belong to the x2gouser group.

---

### Post by TheFu on 2018-03-09
Working ssh is required. Always get that working for the users before touching x2go.  Good that you did it.
Clearly my questions/ideas weren't relevant as they were ignored.
There is an x2go email list. Have you asked for help there?

---

### Post by Mamoth on 2018-03-12
Hi.

I have sent a subscription request to the mailing list but have not received any answer so far (5 days).

---

### Post by TheFu on 2018-03-12
> **Mamoth said:**
> Hi.

I have sent a subscription request to the mailing list but have not received any answer so far (5 days).

email listsrvs are automatic, so if you don't get a confirmation link in 5 minutes, look for errors.  Also, many huge, centralized email providers don't work well with email lists and mark them as spam.  I know my LUGs listsrv programs sometimes fail with both yahoomail and gmail ... because those services don't honor the SMTP standards.

---

### Post by Mamoth on 2018-03-13
Indeed, you were right : the confirmation email had got lost in the spam.

---

### Post by Mamoth on 2018-03-13
I have tried reinstalling everything (done a *apt-get purge* of all x2go packets and reinstalled them - save the client).
It still does not work but I have a different error message :"The connection with the remote server was shut down. Please check the state of your network connection.". 
The network connection is fine. I have disabled the firewall, just in case, but it's still the same.

---

### Post by Mamoth on 2018-03-15
Solved !

Not entering the details, I joined the x2go mailing list and they helped me out.
Eventually, I noticed that the version of x2goclient (less recent because it was the version from the distribution repositories) was not the same as the version of x2goserver (slightly more recent because I had added the ppa to my sources) and that I could connect from another computer which had for client a more recent version.

I added the x2go ppa to my sources, purging the old install, installed the latest version, rebooted and now it works !

---

