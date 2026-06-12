---
title: "dovecot: auth-worker ... pam_start() failed: Critical error - immediate abort"
date: 2016-04-18
forum: Server Platforms
---

### Post by John_Coxe on 2016-04-18
This has been working fine with no system changes for some time now.  I have googled and found advice apparently for prior versions of dovecot and different OSes.  It is not even temporarily fixed by system reboots.

```
# cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.4 LTS"

# dovecot --version
2.2.9

# telnet 127.0.0.1 110
Trying 127.0.0.1...
Connected to 127.0.0.1.
Escape character is '^]'.
+OK Dovecot (Ubuntu) ready.
user ********
+OK
pass ********
-ERR [SYS/TEMP] Temporary authentication failure. [****:2016-04-18 17:21:23]
quit
+OK Logging out
Connection closed by foreign host.

```
mail.log:

```
Apr 18 10:21:21 **** dovecot: auth-worker(1891): Error: pam(********,127.0.0.1): pam_start() failed: Critical error - immediate abort
Apr 18 10:21:27 **** dovecot: pop3-login: Aborted login (auth failed, 1 attempts in 6 secs): user=<********>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured, session=<osTalsUwpAB/AAAB>

```
syslog:

```
Apr 18 10:21:21 **** t of memory [1891]
Apr 18 10:21:21 **** dovecot: auth-worker(1891): Error: pam(********,127.0.0.1): pam_start() failed: Critical error - immediate abort
Apr 18 10:21:27 **** dovecot: pop3-login: Aborted login (auth failed, 1 attempts in 6 secs): user=<********>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured, session=<osTalsUwpAB/AAAB>

```

kern.log:

```
Apr 18 10:21:21 **** t of memory [1891]
```

mail.err:

```
Apr 18 10:21:21 **** dovecot: auth-worker(1891): Error: pam(********,127.0.0.1): pam_start() failed: Critical error - immediate abort
```




```

# dovecot -n
# 2.2.9: /etc/dovecot/dovecot.conf
# OS: Linux 3.19.0-58-generic x86_64 Ubuntu 14.04.4 LTS
disable_plaintext_auth = no
mail_location = mbox:~/mail:INBOX=/var/mail/%u
mail_privileged_group = mail
namespace inbox {
  inbox = yes
  location =
  mailbox Drafts {
    special_use = \Drafts
  }
  mailbox Junk {
    special_use = \Junk
  }
  mailbox Sent {
    special_use = \Sent
  }
  mailbox "Sent Messages" {
    special_use = \Sent
  }
  mailbox Trash {
    special_use = \Trash
  }
  prefix =
}
passdb {
  driver = pam
}
protocols = " imap pop3"
ssl_cert = </etc/dovecot/dovecot.pem
ssl_key = </etc/dovecot/private/dovecot.pem
userdb {
  driver = passwd
}

```
Others, from the googling, have suggested increasing auth_worker_max_request_count.  However, that appears to be for earlier versions of dovecot and does not seem to have been universally successful anyway.

Oh, and here is meminfo, since the 't of memory' error seems to suggets and out of memory condition, though that would be odd immediately after a reboot.
```

# cat /proc/meminfo
MemTotal:       15274824 kB
MemFree:        14900584 kB
MemAvailable:   14904420 kB
Buffers:           21736 kB
Cached:           139484 kB
SwapCached:            0 kB
Active:           166408 kB
Inactive:          91148 kB
Active(anon):      96676 kB
Inactive(anon):     6108 kB
Active(file):      69732 kB
Inactive(file):    85040 kB
Unevictable:           0 kB
Mlocked:               0 kB
SwapTotal:      15666172 kB
SwapFree:       15666172 kB
Dirty:                 0 kB
Writeback:             0 kB
AnonPages:         96380 kB
Mapped:            52136 kB
Shmem:              6452 kB
Slab:              39656 kB
SReclaimable:      21832 kB
SUnreclaim:        17824 kB
KernelStack:        2880 kB
PageTables:         9588 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:    23303584 kB
Committed_AS:     622192 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      117704 kB
VmallocChunk:   34359614368 kB
HardwareCorrupted:     0 kB
AnonHugePages:     45056 kB
CmaTotal:              0 kB
CmaFree:               0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:       96720 kB
DirectMap2M:     1939456 kB
DirectMap1G:    14680064 kB



```
Any ideas or other things to check?  I may have to shut down the postfix services and move the mbox contents over to the other server temporarily.  It'll just throw connection erros on all of the clients until I get it resolved.

Thanks, in advance, for any help in this matter.

---

### Post by Peter_Nelson on 2016-04-18
Sorry I can't be more useful, but I'm seeing the exact same thing as of this morning.  I haven't even logged into this server in weeks so it's no change on my part.  I'm also running 14.04.

I trued an apt-get dist-upgrade and a reboot and same problems.

Looking at /var/log/apt/history.log  I see that some pam modules were auto-upgraded overnight.  That seems like a red flag.

Start-Date: 2016-04-18  06:56:25
Install: libarchive13:amd64 (3.1.2-7ubuntu2.1, automatic), libnettle4:amd64 (2.7.1-1ubuntu0.1, automatic)
Upgrade: libpam-smbpass:amd64 (4.1.6+dfsg-1ubuntu2.14.04.13, 4.3.8+dfsg-0ubuntu0.14.04.2), python-samba:amd64 (4.1.6+dfsg-1ubuntu2.14.04.13, 4.3.8+dfsg-0ubuntu0.14.04.2), winbind:amd64 (4.1.6+dfsg-1ubuntu2.14.04.13, 4.3.8+dfsg-0ubuntu0.14.04.2), tdb-tools:amd64 (1.2.12-1, 1.3.8-0ubuntu0.14.04.1), samba:amd64 (4.1.6+dfsg-1ubuntu2.14.04.13, 4.3.8+dfsg-0ubuntu0.14.04.2), python-tdb:amd64 (1.2.12-1, 1.3.8-0ubuntu0.14.04.1), libtevent0:amd64 (0.9.19-1, 0.9.26-0ubuntu0.14.04.1), samba-dsdb-modules:amd64 (4.1.6+dfsg-1ubuntu2.14.04.13, 4.3.8+dfsg-0ubuntu0.14.04.2), libnss-winbind:amd64 (4.1.6+dfsg-1ubuntu2.14.04.13, 4.3.8+dfsg-0ubuntu0.14.04.2), samba-common-bin:amd64 (4.1.6+dfsg-1ubuntu2.14.04.13, 4.3.8+dfsg-0ubuntu0.14.04.2), libldb1:amd64 (1.1.16-1ubuntu0.1, 1.1.24-0ubuntu0.14.04.1), libtdb1:amd64 (1.2.12-1, 1.3.8-0ubuntu0.14.04.1), samba-libs:amd64 (4.1.6+dfsg-1ubuntu2.14.04.13, 4.3.8+dfsg-0ubuntu0.14.04.2), samba-doc:amd64 (4.1.6+dfsg-1ubuntu2.14.04.13, 4.3.8+dfsg-0ubuntu0.14.04.2), smbclient:amd64 (4.1.6+dfsg-1ubuntu2.14.04.13, 4.3.8+dfsg-0ubuntu0.14.04.2), libtalloc2:amd64 (2.1.0-1, 2.1.5-0ubuntu0.14.04.1), python-talloc:amd64 (2.1.0-1, 2.1.5-0ubuntu0.14.04.1), libpam-winbind:amd64 (4.1.6+dfsg-1ubuntu2.14.04.13, 4.3.8+dfsg-0ubuntu0.14.04.2), libwbclient0:amd64 (4.1.6+dfsg-1ubuntu2.14.04.13, 4.3.8+dfsg-0ubuntu0.14.04.2), samba-vfs-modules:amd64 (4.1.6+dfsg-1ubuntu2.14.04.13, 4.3.8+dfsg-0ubuntu0.14.04.2), python-ldb:amd64 (1.1.16-1ubuntu0.1, 1.1.24-0ubuntu0.14.04.1), samba-common:amd64 (4.1.6+dfsg-1ubuntu2.14.04.13, 4.3.8+dfsg-0ubuntu0.14.04.2), libsmbclient:amd64 (4.1.6+dfsg-1ubuntu2.14.04.13, 4.3.8+dfsg-0ubuntu0.14.04.2)
End-Date: 2016-04-18  06:58:21

---

### Post by Peter_Nelson on 2016-04-18
Yup, the samba pam modules are what was causing the problem.  Removing those two and dovecot is happy again.
> dpkg --purge libpam-winbind libpam-smbpass

Considering I'll never use those authentication plugins I'm fine with them being gone.

---

### Post by Peter_Nelson on 2016-04-18
Filed a bug here: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1571883](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1571883)

---

### Post by John_Coxe on 2016-04-19
That was it.  Thanks for identifying it.  I purged those two as well and it all is honky dory. Hope the bug gets resolved before I update my other server, as it does use samba pam.

---

