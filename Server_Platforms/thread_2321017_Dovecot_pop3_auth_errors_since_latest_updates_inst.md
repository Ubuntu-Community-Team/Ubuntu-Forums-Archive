---
title: "Dovecot pop3 auth errors since latest updates installed."
date: 2016-04-19
forum: Server Platforms
---

### Post by Stephen_at on 2016-04-19
I ran an apt-get upgrade and an apt-get dist-upgrade this morning and since then dovecot pop3 has been throwing random errors like:


dovecot: pop3-login: Disconnected (auth failed, 1 attempts in 4 secs)

When accepting connections from thunderbird running on my laptop.

I am also getting lots of errors like :

Apr 19 19:43:13 Debussy dovecot: auth: Error: userdb(wibble,192.168.0.52,<NwVA2dowmQDAqAA0>): user not found from userdb passwd
Apr 19 19:43:13 Debussy dovecot: pop3: Error: Authenticated user not found from userdb, auth lookup id=1345847297 (client-pid=18920 client-id=163)
Apr 19 19:43:13 Debussy dovecot: pop3-login: Internal login failure (pid=18920 id=163) (internal failure, 1 successful auths): user=<wibble>, method=PLAIN, rip=192.168.0.52, lip=192.168.0.1, mpid=23345, TLS, session=<NwVA2dowmQDAqAA0>


I thought restarting dovecot and postfix had fixed this problem but it looks like it didn't work.

The logs are clear before this morning so it would seem to be related to what was installed this morning:


2016-04-19 07:02:41 status installed man-db:amd64 2.6.7.1-1ubuntu1
2016-04-19 07:02:41 status installed libtalloc2:amd64 2.1.5-0ubuntu0.14.04.1
2016-04-19 07:02:41 status installed libtdb1:amd64 1.3.8-0ubuntu0.14.04.1
2016-04-19 07:02:41 status installed python-tdb:amd64 1.3.8-0ubuntu0.14.04.1
2016-04-19 07:02:41 status installed libtevent0:amd64 0.9.26-0ubuntu0.14.04.1
2016-04-19 07:02:41 status installed python-talloc:amd64 2.1.5-0ubuntu0.14.04.1
2016-04-19 07:02:41 status installed samba-doc:all 2:4.3.8+dfsg-0ubuntu0.14.04.2
2016-04-19 07:02:41 status installed optipng:amd64 0.6.4-1ubuntu0.14.04.1
2016-04-19 07:02:41 status installed tdb-tools:amd64 1.3.8-0ubuntu0.14.04.1
2016-04-19 07:02:41 status installed libc-bin:amd64 2.19-0ubuntu6.7
2016-04-19 07:03:08 status installed ureadahead:amd64 0.100.0-16
2016-04-19 07:03:08 status installed man-db:amd64 2.6.7.1-1ubuntu1
2016-04-19 07:03:08 status installed ufw:all 0.34~rc-0ubuntu2
2016-04-19 07:03:09 status installed liblzo2-2:amd64 2.06-1.2ubuntu1.1
2016-04-19 07:03:09 status installed libnettle4:amd64 2.7.1-1ubuntu0.1
2016-04-19 07:03:09 status installed libarchive13:amd64 3.1.2-7ubuntu2.1
2016-04-19 07:03:09 status installed libldb1:amd64 1:1.1.24-0ubuntu0.14.04.1
2016-04-19 07:03:09 status installed python-ldb:amd64 1:1.1.24-0ubuntu0.14.04.1
2016-04-19 07:03:09 status installed libwbclient0:amd64 2:4.3.8+dfsg-0ubuntu0.14.04.2
2016-04-19 07:03:09 status installed samba-libs:amd64 2:4.3.8+dfsg-0ubuntu0.14.04.2
2016-04-19 07:03:09 status installed samba-dsdb-modules:amd64 2:4.3.8+dfsg-0ubuntu0.14.04.2
2016-04-19 07:03:09 status installed python-samba:amd64 2:4.3.8+dfsg-0ubuntu0.14.04.2
2016-04-19 07:03:10 status installed samba-common:all 2:4.3.8+dfsg-0ubuntu0.14.04.2
2016-04-19 07:03:10 status installed samba-common-bin:amd64 2:4.3.8+dfsg-0ubuntu0.14.04.2
2016-04-19 07:03:10 status installed libsmbclient:amd64 2:4.3.8+dfsg-0ubuntu0.14.04.2
2016-04-19 07:03:10 status installed smbclient:amd64 2:4.3.8+dfsg-0ubuntu0.14.04.2
2016-04-19 07:03:10 status installed libpam-smbpass:amd64 2:4.3.8+dfsg-0ubuntu0.14.04.2
2016-04-19 07:03:10 status installed samba-vfs-modules:amd64 2:4.3.8+dfsg-0ubuntu0.14.04.2
2016-04-19 07:03:10 status installed samba:amd64 2:4.3.8+dfsg-0ubuntu0.14.04.2
2016-04-19 07:03:10 status installed ureadahead:amd64 0.100.0-16
2016-04-19 07:03:11 status installed winbind:amd64 2:4.3.8+dfsg-0ubuntu0.14.04.2
2016-04-19 07:03:11 status installed libc-bin:amd64 2.19-0ubuntu6.7

In detail this is what was added:

Start-Date: 2016-04-19  07:02:39
Commandline: apt-get upgrade
Upgrade: tdb-tools:amd64 (1.2.12-1, 1.3.8-0ubuntu0.14.04.1), python-tdb:amd64 (1.2.12-1, 1.3.8-0ubuntu0.14.04.1), libtevent0:amd64 (0.9.19-1, 0.9.26-0ubuntu0.14.04.1), optipng:amd64 (0.6.4-1build1, 0.6.4-1ubuntu0.14.04.1), libtdb1:amd64 (1.2.12-1, 1.3.8-0ubuntu0.14.04.1), samba-doc:amd64 (4.1.6+dfsg-1ubuntu2.14.04.13, 4.3.8+dfsg-0ubuntu0.14.04.2), libtalloc2:amd64 (2.1.0-1, 2.1.5-0ubuntu0.14.04.1), python-talloc:amd64 (2.1.0-1, 2.1.5-0ubuntu0.14.04.1)
End-Date: 2016-04-19  07:02:41

Start-Date: 2016-04-19  07:03:04
Commandline: apt-get dist-upgrade
Install: libarchive13:amd64 (3.1.2-7ubuntu2.1, automatic), liblzo2-2:amd64 (2.06-1.2ubuntu1.1, automatic), libnettle4:amd64 (2.7.1-1ubuntu0.1, automatic)
Upgrade: libpam-smbpass:amd64 (4.1.6+dfsg-1ubuntu2.14.04.13, 4.3.8+dfsg-0ubuntu0.14.04.2), python-samba:amd64 (4.1.6+dfsg-1ubuntu2.14.04.13, 4.3.8+dfsg-0ubuntu0.14.04.2), winbind:amd64 (4.1.6+dfsg-1ubuntu2.14.04.13, 4.3.8+dfsg-0ubuntu0.14.04.2), samba:amd64 (4.1.6+dfsg-1ubuntu2.14.04.13, 4.3.8+dfsg-0ubuntu0.14.04.2), samba-dsdb-modules:amd64 (4.1.6+dfsg-1ubuntu2.14.04.13, 4.3.8+dfsg-0ubuntu0.14.04.2), samba-common-bin:amd64 (4.1.6+dfsg-1ubuntu2.14.04.13, 4.3.8+dfsg-0ubuntu0.14.04.2), libldb1:amd64 (1.1.16-1ubuntu0.1, 1.1.24-0ubuntu0.14.04.1), samba-libs:amd64 (4.1.6+dfsg-1ubuntu2.14.04.13, 4.3.8+dfsg-0ubuntu0.14.04.2), smbclient:amd64 (4.1.6+dfsg-1ubuntu2.14.04.13, 4.3.8+dfsg-0ubuntu0.14.04.2), libwbclient0:amd64 (4.1.6+dfsg-1ubuntu2.14.04.13, 4.3.8+dfsg-0ubuntu0.14.04.2), samba-vfs-modules:amd64 (4.1.6+dfsg-1ubuntu2.14.04.13, 4.3.8+dfsg-0ubuntu0.14.04.2), python-ldb:amd64 (1.1.16-1ubuntu0.1, 1.1.24-0ubuntu0.14.04.1), samba-common:amd64 (4.1.6+dfsg-1ubuntu2.14.04.13, 4.3.8+dfsg-0ubuntu0.14.04.2), libsmbclient:amd64 (4.1.6+dfsg-1ubuntu2.14.04.13, 4.3.8+dfsg-0ubuntu0.14.04.2)
End-Date: 2016-04-19  07:03:11



Anyone else seeing similar problems?

---

### Post by Stephen_at on 2016-04-19
Another thread shows problems with one of the pam modules for Samba.

I'm not using them so did

dpkg --purge libpam-winbind libpam-smbpass

And iI've had no errors in an hour....

Will update this thread tomorrow morning with the final result.

---

### Post by Stephen_at on 2016-04-20
As a follow up - after 12 hours not one more error has been logged - so the problem was the updates to the PAM files for winbind and samba.

---

