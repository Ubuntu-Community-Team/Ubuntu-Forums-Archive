---
title: "Solved - 18.04 Server unable to login via tty, ssh OK"
date: 2019-02-02
forum: Server Platforms
---

### Post by britton_bowman on 2019-02-02
Recently performed a dist-upgrade on an ubuntu-server 18.04 (no desktop env installed) where the following were updated:
```
apt:amd64 (1.6.6ubuntu0.1 1.6.8)apt-transport-https:amd64 (1.6.6ubuntu0.1 1.6.8)
apt-utils:amd64 (1.6.6ubuntu0.1 1.6.8)
avahi-daemon:amd64 (0.7-3.1ubuntu1.1 0.7-3.1ubuntu1.2)
grub2-common:amd64 (2.02-2ubuntu8.9 2.02-2ubuntu8.10)
grub-common:amd64 (2.02-2ubuntu8.9 2.02-2ubuntu8.10)
grub-efi-amd64:amd64 (2.02-2ubuntu8.9 2.02-2ubuntu8.10)
grub-efi-amd64-bin:amd64 (2.02-2ubuntu8.9 2.02-2ubuntu8.10)
grub-efi-amd64-signed:amd64 (1.93.10+2.02-2ubuntu8.9 1.93.11+2.02-2ubuntu8.10)
libapt-inst2.0:amd64 (1.6.6ubuntu0.1 1.6.8)
libapt-pkg5.0:amd64 (1.6.6ubuntu0.1 1.6.8)
libasound2:amd64 (1.1.3-5ubuntu0.1 1.1.3-5ubuntu0.2)
libasound2-data:amd64 (1.1.3-5ubuntu0.1 1.1.3-5ubuntu0.2)
libavahi-client3:amd64 (0.7-3.1ubuntu1.1 0.7-3.1ubuntu1.2)
libavahi-common3:amd64 (0.7-3.1ubuntu1.1 0.7-3.1ubuntu1.2)
libavahi-common-data:amd64 (0.7-3.1ubuntu1.1 0.7-3.1ubuntu1.2)
libavahi-core7:amd64 (0.7-3.1ubuntu1.1 0.7-3.1ubuntu1.2)
libavahi-glib1:amd64 (0.7-3.1ubuntu1.1 0.7-3.1ubuntu1.2)
linux-generic:amd64 (4.15.0.44.46 4.15.0.45.47)
linux-headers-4.15.0-45:amd64 (4.15.0-45.48 automatic)
linux-headers-4.15.0-45-generic:amd64 (4.15.0-45.48 automatic)
linux-headers-generic:amd64 (4.15.0.44.46 4.15.0.45.47)
linux-image-4.15.0-45-generic:amd64 (4.15.0-45.48 automatic)
linux-image-generic:amd64 (4.15.0.44.46 4.15.0.45.47)
linux-libc-dev:amd64 (4.15.0-44.47 4.15.0-45.48)
linux-modules-4.15.0-45-generic:amd64 (4.15.0-45.48 automatic)
linux-modules-extra-4.15.0-45-generic:amd64 (4.15.0-45.48 automatic)
linux-signed-generic:amd64 (4.15.0.44.46 4.15.0.45.47)
linux-signed-image-generic:amd64 (4.15.0.44.46 4.15.0.45.47)
python3-distupgrade:amd64 (1:18.04.29 1:18.04.30)
python3-update-manager:amd64 (1:18.04.11.8 1:18.04.11.9)
tar:amd64 (1.29b-2 1.29b-2ubuntu0.1)
ubuntu-release-upgrader-core:amd64 (1:18.04.29 1:18.04.30)
update-notifier-common:amd64 (3.192.1.4 3.192.1.5)
Upgrade: update-manager-core:amd64 (1:18.04.11.8 1:18.04.11.9)
```

After a reboot I have been unable to login via tty.  I enter username and press Enter, then the password prompt is shown with immediate 'login incorrect' response, then prompt of username input 4 more times.  This occurs with no other user input (other than the initial username & Enter).  The relevant entries from the auth.log
```
Feb  2 13:34:08 server login[1545]: pam_unix(login:auth): conversation failed
Feb  2 13:34:08 server login[1545]: pam_unix(login:auth): auth could not identify password for [XXXX]
Feb  2 13:34:11 server login[1545]: FAILED LOGIN (1) on '/dev/tty1' FOR 'XXXX', Authentication failure
Feb  2 13:34:12 server login[1545]: pam_securetty(login:auth): cannot determine username
Feb  2 13:34:14 server login[1545]: FAILED LOGIN (2) on '/dev/tty1' FOR 'UNKNOWN', Error in service module
Feb  2 13:34:14 server login[1545]: pam_securetty(login:auth): cannot determine username
Feb  2 13:34:17 server login[1545]: FAILED LOGIN (3) on '/dev/tty1' FOR 'UNKNOWN', Error in service module
Feb  2 13:34:17 server login[1545]: pam_securetty(login:auth): cannot determine username
Feb  2 13:34:20 server login[1545]: FAILED LOGIN (4) on '/dev/tty1' FOR 'UNKNOWN', Error in service module
Feb  2 13:34:20 server login[1545]: pam_securetty(login:auth): cannot determine username
Feb  2 13:34:23 server login[1545]: FAILED LOGIN (5) on '/dev/tty1' FOR 'UNKNOWN', Error in service module
Feb  2 13:34:23 server login[1545]: TOO MANY LOGIN TRIES (5) on '/dev/tty1' FOR 'UNKNOWN'
Feb  2 13:34:23 server login[1545]: pam_mail(login:session): cannot determine username
Feb  2 13:34:23 server login[1545]: pam_unix(login:session): close_session - error recovering username
```
Thinking that a keyboard may the issue, used a different keyboard with the same result.  To ensure correct keyboard mapping performed the following with no change in the problem: 
```
sudo dpkg-reconfigure keyboard-configuration
```

I am able to login with the same username successfully via SSH client with authorized key:
```
Feb  2 14:31:06 server sshd[3593]: Accepted publickey for XXXX from 192.168.aa.bb port 35230 ssh2: RSA SHA256:/..hidden..
Feb  2 14:31:06 server sshd[3593]: pam_unix(sshd:session): session opened for user XXXX by (uid=0)
Feb  2 14:31:06 server systemd-logind[608]: New session 6 of user XXXX.
```
and with password prompt (enabled password only for testing purposes):
```
Feb  2 14:31:41 server sshd[3701]: Accepted password for XXXX from 192.168.yy.zz port 63158 ssh2
Feb  2 14:31:41 server sshd[3701]: pam_unix(sshd:session): session opened for user XXXX by (uid=0)
Feb  2 14:31:41 server systemd-logind[608]: New session 7 of user XXXX.
```

Appreciate help to get this issue resolved.

---

### Post by howefield on 2019-02-02
Thread moved to the "*Server Platforms*" forum.

---

### Post by elisdg on 2019-02-04
It seems, that there is a problem with the Kernel: `linux-headers-4.15.0-45:amd64 (4.15.0-45.48 automatic)`

There is a Question on askubuntu about that: [https://askubuntu.com/a/1115514/414159](https://askubuntu.com/a/1115514/414159)

Mainly: just choose an older Kernel in grub (as a workaround) - for me, **4.15.0.-43 **,worked.

---

### Post by britton_bowman on 2019-02-04
Rolling back to **4.15.0.-43 **worked.

Thanks

---

