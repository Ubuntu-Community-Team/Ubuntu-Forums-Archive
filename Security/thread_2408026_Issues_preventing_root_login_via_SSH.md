---
title: "Issues preventing root login via SSH"
date: 2018-12-12
forum: Security
---

### Post by djsutherland on 2018-12-12
I am attempting to not allow root login via SSH.  I have modified the sshd_config to be this:


# Authentication:
LoginGraceTime 120
#PermitRootLogin prohibit-password
PermitRootLogin no
StrictModes yes

I restarted ssh and even tried to reboot the entire system and root can still login via SSH.  Any ideas?

---

### Post by TheFu on 2018-12-12
Which sshd_config file did you change?  Has to be on the remote system. setting **PermitEmptyPasswords no** can't hurt.
You can also use tcp-wrappers to prevent all ssh except from specific IPs.

From the sshd_config manpage:
```
     DenyUsers
             This keyword can be followed by a list of user name patterns,
             separated by spaces.  Login is disallowed for user names that
             match one of the patterns.  Only user names are valid; a numeri&#8208;
             cal user ID is not recognized.  By default, login is allowed for
             all users.  If the pattern takes the form USER@HOST then USER and
             HOST are separately checked, restricting logins to particular
             users from particular hosts.  The allow/deny directives are pro&#8208;
             cessed in the following order: DenyUsers, AllowUsers, DenyGroups,
             and finally AllowGroups.

             See PATTERNS in ssh_config(5) for more information on patterns.

```

Also, have you removed the client-side public key from the remote ~root/.ssh/authorized_keys file?

---

### Post by djsutherland on 2018-12-12
I forgot some valuable information.
We use SSH for remote administration of various flavors of Unbuntu servers.  We are using PuTTY from windows clients to these servers.
They sshd_config file I changed was on the remote server.  
We do not use DenyUsers, as we are using AllowGroups, my previous testing showed that as they are processed in the order listed in the manpages, if anything existed in DenyUsers, AllowUsers or DenyGroups that it didn't seem to process anything past there.  Not the way I would have anticipated that it would work. I can try setting DenyUsers root and see if that works.

---

### Post by djsutherland on 2018-12-12
Even after the change, root user is still able to log in.  the sshd_config file located it /etc/ssh now looks like this.

# Authentication:
LoginGraceTime 120
#PermitRootLogin prohibit-password
PermitRootLogin no
StrictModes yes
DenyUsers root

---

### Post by Doug S on 2018-12-14
I just do not know what is wrong in your case. I do not normally allow root login on my 16.04 test server (or any) computer, so I enabled it just to test this:

```
$ sudo passwd root
```also testing that I could disable it again:```
$ sudo passwd -dl root
```With this in sshd_config:
```
# Authentication:
LoginGraceTime 120
#PermitRootLogin prohibit-password
PermitRootLogin no
StrictModes yes

```I could not login as root, but with this:
```
# Authentication:
LoginGraceTime 120
#PermitRootLogin prohibit-password
PermitRootLogin yes
StrictModes yes

```I could.
Here is the related area of my /var/log/auth.log file:
```
Dec 14 08:43:05 s15 sudo:     doug : TTY=pts/1 ; PWD=/home/doug/config/etc/ssh ; USER=root ; COMMAND=/bin/cp sshd_config /etc/ssh/sshd_config
Dec 14 08:43:05 s15 sudo: pam_unix(sudo:session): session opened for user root by doug(uid=0)
Dec 14 08:43:05 s15 sudo: pam_unix(sudo:session): session closed for user root
Dec 14 08:43:09 s15 sudo:     doug : TTY=pts/1 ; PWD=/home/doug/config/etc/ssh ; USER=root ; COMMAND=/bin/systemctl restart sshd.service
Dec 14 08:43:09 s15 sudo: pam_unix(sudo:session): session opened for user root by doug(uid=0)
Dec 14 08:43:09 s15 sshd[6696]: Received signal 15; terminating.
Dec 14 08:43:09 s15 sshd[7013]: Server listening on 0.0.0.0 port 22.
Dec 14 08:43:09 s15 sudo: pam_unix(sudo:session): session closed for user root
Dec 14 08:43:22 s15 sshd[7032]: Accepted password for root from 192.168.111.101 port 55705 ssh2
Dec 14 08:43:22 s15 sshd[7032]: pam_unix(sshd:session): session opened for user root by (uid=0)
Dec 14 08:43:23 s15 systemd-logind[1056]: New session 14 of user root.
Dec 14 08:43:23 s15 systemd: pam_unix(systemd-user:session): session opened for user root by (uid=0)
Dec 14 08:43:41 s15 sshd[7032]: pam_unix(sshd:session): session closed for user root
Dec 14 08:43:41 s15 systemd-logind[1056]: Removed session 14.
Dec 14 08:43:41 s15 systemd: pam_unix(systemd-user:session): session closed for user root
Dec 14 08:44:03 s15 sudo:     doug : TTY=pts/1 ; PWD=/home/doug/config/etc/ssh ; USER=root ; COMMAND=/bin/cp sshd_config /etc/ssh/sshd_config
Dec 14 08:44:03 s15 sudo: pam_unix(sudo:session): session opened for user root by doug(uid=0)
Dec 14 08:44:03 s15 sudo: pam_unix(sudo:session): session closed for user root
Dec 14 08:44:20 s15 sudo:     doug : TTY=pts/1 ; PWD=/home/doug/config/etc/ssh ; USER=root ; COMMAND=/bin/systemctl restart sshd.service
Dec 14 08:44:20 s15 sudo: pam_unix(sudo:session): session opened for user root by doug(uid=0)
Dec 14 08:44:20 s15 sshd[7013]: Received signal 15; terminating.
Dec 14 08:44:20 s15 sshd[7171]: Server listening on 0.0.0.0 port 22.
Dec 14 08:44:20 s15 sudo: pam_unix(sudo:session): session closed for user root
Dec 14 08:44:42 s15 sshd[7191]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.111.101  user=root
Dec 14 08:44:45 s15 sshd[7191]: Failed password for root from 192.168.111.101 port 55714 ssh2
Dec 14 08:44:58 s15 sshd[7191]: Failed password for root from 192.168.111.101 port 55714 ssh2
Dec 14 08:44:58 s15 sshd[7191]: error: maximum authentication attempts exceeded for root from 192.168.111.101 port 55714 ssh2 [preauth]
Dec 14 08:44:58 s15 sshd[7191]: Disconnecting: Too many authentication failures [preauth]
Dec 14 08:44:58 s15 sshd[7191]: PAM 1 more authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.111.101  user=root

```I realize there is no value added in this reply, other than to say it works as expected for me.

---

### Post by SagaciousKJB on 2018-12-14
Not to raise unnecessary alarm, but there have been instances of ssh servers being taken over, and the sshd replaced with a compromised daemon.  It's possible that such a daemon would be unable to shut down root access ( though sloppy on the malware writer's part ).  A simple step would be to find the checksum that the binary is supposed to have, and compare it to the checksum of the binary running on your system, or compile and install from source ( also verifying the checksum of the source package you download ).

---

### Post by ubname on 2018-12-16
Probably the OP should specify the system in use.

---

