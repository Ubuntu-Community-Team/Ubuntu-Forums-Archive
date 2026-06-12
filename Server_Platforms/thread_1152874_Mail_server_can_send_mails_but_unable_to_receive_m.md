---
title: "Mail server can send mails but unable to receive mails"
date: 2009-05-08
forum: Server Platforms
---

### Post by satimis on 2009-05-08
Hi folks,


OpenVZ
Guest - Ubuntu 8.04
postfix
mysql


Mail server can send mails but unable to receive mails.


# tail /var/log/mail.log```

May  8 10:03:24 vz2 postfix/qmgr[1919]: 1181E3C8826: removed
May  8 10:03:27 vz2 postfix/smtpd[1963]: disconnect from localhost.localdomain[127.0.0.1]
May  8 10:05:30 vz2 postfix/smtpd[1970]: connect from web35208.mail.mud.yahoo.com[66.163.179.87]
May  8 10:05:51 vz2 postfix/smtpd[1970]: warning: 87.179.163.66.sbl.spamhaus.org: RBL lookup error: Host or domain name not found. Name service error for name=87.179.163.66.sbl.spamhaus.org type=A: Host not found, try again
May  8 10:05:51 vz2 postfix/smtpd[1970]: warning: connect to 127.0.0.1:60000: Connection refused
May  8 10:05:51 vz2 postfix/smtpd[1970]: warning: problem talking to server 127.0.0.1:60000: Connection refused
May  8 10:05:52 vz2 postfix/smtpd[1970]: warning: connect to 127.0.0.1:60000: Connection refused
May  8 10:05:52 vz2 postfix/smtpd[1970]: warning: problem talking to server 127.0.0.1:60000: Connection refused
May  8 10:05:52 vz2 postfix/smtpd[1970]: NOQUEUE: reject: RCPT from web35208.mail.mud.yahoo.com[66.163.179.87]: 451 4.3.5 Server configuration problem; from=<satimis@yahoo.com> to=<satimis@satimis.com> proto=SMTP helo=<web35208.mail.mud.yahoo.com>
May  8 10:05:52 vz2 postfix/smtpd[1970]: disconnect from web35208.mail.mud.yahoo.com[66.163.179.87]

```


# /etc/init.d/clamav-daemon start```

 * Starting ClamAV daemon clamd  
LibClamAV Warning: ***********************************************************
LibClamAV Warning: ***  This version of the ClamAV engine is outdated.     ***
LibClamAV Warning: *** DON'T PANIC! Read http://www.clamav.net/support/faq ***
LibClamAV Warning: ***********************************************************
                                                                            [fail]

```


# clamdscan - </etc/hosts```

connect(): Connection refused
WARNING: Can't connect to clamd.
root@vz2:/# clamscan ./virtualmin-install.log 
LibClamAV Warning: ***********************************************************
LibClamAV Warning: ***  This version of the ClamAV engine is outdated.     ***
LibClamAV Warning: *** DON'T PANIC! Read http://www.clamav.net/support/faq ***
LibClamAV Warning: ***********************************************************
WARNING: Can't access file ./virtualmin-install.log
./virtualmin-install.log: No such file or directory

----------- SCAN SUMMARY -----------
Known viruses: 548954
Engine version: 0.94.2
Scanned directories: 0
Scanned files: 0
Infected files: 0
Data scanned: 0.00 MB
Time: 3.114 sec (0 m 3 s)

```


# whereis freshclam```

freshclam: /usr/bin/freshclam /usr/share/man/man1/freshclam.1.gz

```


# whereis clamscan ```

clamscan: /usr/bin/clamscan /usr/share/man/man1/clamscan.1.gz

```


/# ldd `which freshclam````

	libclamav.so.5 => /usr/lib/libclamav.so.5 (0xb7f16000)
	libbz2.so.1.0 => /lib/libbz2.so.1.0 (0xb7f06000)
	libgmp.so.3 => /usr/lib/libgmp.so.3 (0xb7ec1000)
	libz.so.1 => /usr/lib/libz.so.1 (0xb7eac000)
	libresolv.so.2 => /lib/tls/i686/cmov/libresolv.so.2 (0xb7e99000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7e81000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7d32000)
	/lib/ld-linux.so.2 (0xb7fca000)
root@vz2:/# 

```


Please advise where shall I check?  How to fix the problem?

TIA


B.R.
satimis

---

### Post by a9k3d on 2009-05-14
What is supposed to be running on 127.0.0.1 port 60000? That is failing when postfix/smtpd calls it.

---

### Post by kustomjs on 2009-05-15
do you have your mx records and cname pointing at your ip address with your domain name? because I had same issue as you intill I fixed it with mx records and cname.

---

### Post by satimis on 2009-05-15
> **kustomjs said:**
> do you have your mx records and cname pointing at your ip address with your domain name? because I had same issue as you intill I fixed it with mx records and cname.

Hi kustomjs and a9k3d,


Problem solved after installing "postgrey" which I left out on building the server.  Thanks

B.R.
satimis

---

