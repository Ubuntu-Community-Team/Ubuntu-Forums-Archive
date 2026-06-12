---
title: "No login possible on vsftpd"
date: 2013-03-21
forum: Server Platforms
---

### Post by Sworddragon on 2013-03-21
I remember vsftpd was working on a previous release on my system but now I'm unlucky. local_enable=YES was already the default and I needed just to change write_enable to YES. But after restarting vsftpd and trying to login it fails:

```
sworddragon@ubuntu:~$ ftp localhost
Connected to localhost.
220 (vsFTPd 3.0.2)
Name (localhost:sworddragon): sworddragon
331 Please specify the password.
Password:
530 Login incorrect.
Login failed.

```

/var/log/vsftpd.log contains:

```
Thu Mar 21 09:00:33 2013 [pid 2] CONNECT: Client "127.0.0.1"
Thu Mar 21 09:00:48 2013 [pid 1] [sworddragon] FAIL LOGIN: Client "127.0.0.1"

```

I have even created a new user but this doesn't work too. Has somebody an idea?

---

### Post by dino99 on 2013-03-21
have you some usefull info inside /var/log/auth.log ?

---

### Post by Sworddragon on 2013-03-21
This file doesn't exist on my system. It seems I'm missing the related non-essential package. I'm using GDM as login manager and ecryptfs for my home directory if this helps.

---

### Post by dino99 on 2013-03-21
you need to narrow down that missing auth.log file  (rsyslog)
[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

---

### Post by Sworddragon on 2013-03-21
I have installed rsyslog and rebooted the system. Here is my /var/log/auth.log:

```
Mar 21 12:16:38 localhost dbus[1185]: [system] Rejected send message, 1 matched rules; type="method_call", sender=":1.2" (uid=0 pid=1213 comm="gdm ") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.3" (uid=0 pid=1323 comm="/usr/lib/gdm/gdm-simple-slave --display-id /org/gn")
Mar 21 12:16:49 localhost gdm-launch-environment][1498]: pam_unix(gdm-launch-environment:session): session opened for user gdm by (uid=0)
Mar 21 12:16:55 localhost polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session1 (system bus name :1.16 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale de_DE.UTF-8)
Mar 21 12:16:56 localhost dbus[1185]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.17" (uid=103 pid=1817 comm="/usr/lib/gdm/gdm-simple-greeter ") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.7" (uid=0 pid=1509 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Mar 21 12:16:58  dbus[1185]: last message repeated 4 times
Mar 21 12:16:58 localhost gdm][1833]: PAM unable to dlopen(pam_gnome_keyring.so): /lib/security/pam_gnome_keyring.so: Kann die Shared-Object-Datei nicht öffnen: Datei oder Verzeichnis nicht gefunden
Mar 21 12:16:58 localhost gdm][1833]: PAM adding faulty module: pam_gnome_keyring.so
Mar 21 12:16:58 localhost gdm][1833]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "sworddragon"
Mar 21 12:17:01 localhost CRON[1838]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar 21 12:17:01 localhost CRON[1838]: pam_unix(cron:session): session closed for user root
Mar 21 12:17:03 localhost gdm][1833]: pam_unix(gdm:session): session opened for user sworddragon by (uid=0)
Mar 21 12:17:03 localhost dbus[1185]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.17" (uid=103 pid=1817 comm="/usr/lib/gdm/gdm-simple-greeter ") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.7" (uid=0 pid=1509 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Mar 21 12:17:03 localhost polkitd(authority=local): Unregistered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session1 (system bus name :1.16, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale de_DE.UTF-8) (disconnected from bus)
Mar 21 12:17:03 localhost gdm-launch-environment][1498]: pam_unix(gdm-launch-environment:session): session closed for user gdm
Mar 21 12:18:29 localhost vsftpd: PAM audit_log_acct_message() failed: Operation not permitted

```

---

### Post by dino99 on 2013-03-21
compared to your messages above, i've also the same first comment on my system (something new since a few days, but im using the gnome3-team ppa) about "dbus rejecting send message ..."
cant say if that matter, i've not yet get such issue as yours.

but then you get pam troubles: is it "dbus" related or "gdm" ?  As your "sworddragon" user cant met pam requirement, maybe check the "users & groups" settings to see if sworddragon is activated

---

### Post by Sworddragon on 2013-03-21
I have looked with google about the last line and it seems it is a bug. I will check it later again and open a bugreport if needed.

---

### Post by dino99 on 2013-03-21
When i get troubles, the first thing im doing is to clean the system as much as i can (clean/autoclean/autoremove/gtkorphan/bleachbit) and check for missing update/install (sudo apt-get install -f)
then i do a reconfiguration after having closed the running apps : 
> sudo dpkg-reconfigure -phigh -a 

---

### Post by Sworddragon on 2013-03-26
As expected it hasn't worked. But I have now opened a bugreport: [https://bugs.launchpad.net/ubuntu/+source/vsftpd/+bug/1160372](https://bugs.launchpad.net/ubuntu/+source/vsftpd/+bug/1160372)

---

### Post by dino99 on 2013-03-26
I've seen your report, is it supposed to work without "sudo" ?

---

### Post by Sworddragon on 2013-03-27
I have tried it now with root permissions but it still doesn't work.

---

### Post by mörgæs on 2013-04-06
The bug is still present. Does anybody have more information on it or a workaround?

Also, could people please add "affects me too" in Launchpad if you experience the same?

---

### Post by nixxle on 2013-05-02
Fresh Ubuntu 13 install on Rackspace, probably also this bug? 

 PAM audit_log_acct_message() failed: Operation not permitted

---

### Post by cariboo on 2013-05-02
Moved to server platforms, as there may be better help available there.

---

### Post by TomtheWombat on 2013-05-02
> **nixxle said:**
> Fresh Ubuntu 13 install on Rackspace, probably also this bug? 

 PAM audit_log_acct_message() failed: Operation not permitted

The bug report on [#9]("http://ubuntuforums.org/showthread.php?t=2127780&p=12574699#post12574699") has instructions on building a patched vsftpd deb and precompiled packages for i386 and x64.

---

### Post by GrayBear on 2013-05-10
I also have the same problem. I can't connect to FTP server (vsftpd)
First, I got this error (auth.log):
```
ubuntu vsftpd: PAM unable to dlopen(pam_smbpass.so): /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory
```
[I already asked for help]("http://ubuntuforums.org/showthread.php?t=2143073") about that error on this forum.

then I applied the advice given [here]("http://www.howtoforge.com/forums/showpost.php?p=123231&postcount=6"): 
```
In /etc/pam.d/common-auth and /etc/pam.d/common-password comment out the lines that have pam_smbpass.so in them. 
```

But now when I try to connect to the FTP server I get the same error the original poster gets (auth.log):

```
May 10 10:22:16 ubuntu vsftpd: PAM audit_log_acct_message() failed: Operation not permitted
```

---

### Post by GrayBear on 2013-05-10
It works, I updated vsftpd with the package posted on launchpad and added "allow_writeable_chroot=YES" in /etc/vsftpd.conf
Details [here]("http://ubuntuforums.org/showthread.php?t=2143073")

---

### Post by mörgæs on 2013-05-20
According to the bug report a [fix]("https://bugs.launchpad.net/ubuntu/+source/vsftpd/+bug/1160372") is available in raring-proposed.

---

