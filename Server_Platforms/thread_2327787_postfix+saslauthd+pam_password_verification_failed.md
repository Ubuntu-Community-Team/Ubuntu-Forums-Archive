---
title: "postfix+saslauthd+pam: password verification failed"
date: 2016-06-14
forum: Server Platforms
---

### Post by pgf1234 on 2016-06-14
I'm trying to configure postfix to authenticate to pam via saslauthd  following the instructions at [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix), but I'm beginning to think postfix is not communicating with saslauthd. When I use testsaslauthd it authenticates without a problem:

```
[FONT=Menlo]testsaslauthd -u testuser -p testpassword[/FONT]
[FONT=Menlo]0: OK "Success."[/FONT]

```

Postfix, though, gives an authentication failure for the same user/password combination:

```

[FONT=Menlo]Jun 14 10:44:38 fs1 postfix/smtpd[21212]: Anonymous TLS connection established from unknown[192.168.236.156]: TLSv1 with cipher ECDHE-RSA-AES256-SHA (256/256 bits)[/FONT]
[FONT=Menlo]Jun 14 10:44:38 fs1 postfix/smtpd[21212]: xsasl_cyrus_server_create: SASL service=smtp, realm=(null)[/FONT]
[FONT=Menlo]Jun 14 10:44:38 fs1 postfix/smtpd[21212]: name_mask: noanonymous[/FONT]
[FONT=Menlo]Jun 14 10:44:38 fs1 postfix/smtpd[21212]: watchdog_pat: 0x7f4c58e08100[/FONT]
[FONT=Menlo]Jun 14 10:44:38 fs1 postfix/smtpd[21212]: < unknown[192.168.236.156]: EHLO [192.168.236.156][/FONT]
[FONT=Menlo]Jun 14 10:44:38 fs1 postfix/smtpd[21212]: match_list_match: unknown: no match[/FONT]
[FONT=Menlo]Jun 14 10:44:38 fs1 postfix/smtpd[21212]: match_list_match: 192.168.236.156: no match[/FONT]
[FONT=Menlo]Jun 14 10:44:38 fs1 postfix/smtpd[21212]: > unknown[192.168.236.156]: 250-mail.home4now.ca[/FONT]
[FONT=Menlo]Jun 14 10:44:38 fs1 postfix/smtpd[21212]: > unknown[192.168.236.156]: 250-PIPELINING[/FONT]
[FONT=Menlo]Jun 14 10:44:38 fs1 postfix/smtpd[21212]: > unknown[192.168.236.156]: 250-SIZE 10240000[/FONT]
[FONT=Menlo]Jun 14 10:44:38 fs1 postfix/smtpd[21212]: > unknown[192.168.236.156]: 250-VRFY[/FONT]
[FONT=Menlo]Jun 14 10:44:38 fs1 postfix/smtpd[21212]: > unknown[192.168.236.156]: 250-ETRN[/FONT]
[FONT=Menlo]Jun 14 10:44:38 fs1 postfix/smtpd[21212]: > unknown[192.168.236.156]: 250-AUTH DIGEST-MD5 NTLM CRAM-MD5 PLAIN LOGIN[/FONT]
[FONT=Menlo]Jun 14 10:44:38 fs1 postfix/smtpd[21212]: > unknown[192.168.236.156]: 250-AUTH=DIGEST-MD5 NTLM CRAM-MD5 PLAIN LOGIN[/FONT]
[FONT=Menlo]Jun 14 10:44:38 fs1 postfix/smtpd[21212]: > unknown[192.168.236.156]: 250-ENHANCEDSTATUSCODES[/FONT]
[FONT=Menlo]Jun 14 10:44:38 fs1 postfix/smtpd[21212]: > unknown[192.168.236.156]: 250-8BITMIME[/FONT]
[FONT=Menlo]Jun 14 10:44:38 fs1 postfix/smtpd[21212]: > unknown[192.168.236.156]: 250 DSN[/FONT]
[FONT=Menlo]Jun 14 10:44:38 fs1 postfix/smtpd[21212]: watchdog_pat: 0x7f4c58e08100[/FONT]
[FONT=Menlo]Jun 14 10:44:38 fs1 postfix/smtpd[21212]: < unknown[192.168.236.156]: AUTH PLAIN dGVzdHVzZXIAdGVzdHVzZXIAbGV0bWVpbg==[/FONT]
[FONT=Menlo]Jun 14 10:44:38 fs1 postfix/smtpd[21212]: xsasl_cyrus_server_first: sasl_method PLAIN, init_response dGVzdHVzZXIAdGVzdHVzZXIAbGV0bWVpbg==[/FONT]
[FONT=Menlo]Jun 14 10:44:38 fs1 postfix/smtpd[21212]: xsasl_cyrus_server_first: decoded initial response testuser[/FONT]
[FONT=Menlo]Jun 14 10:44:38 fs1 postfix/smtpd[21212]: warning: SASL authentication failure: Password verification failed[/FONT]
[FONT=Menlo]Jun 14 10:44:38 fs1 postfix/smtpd[21212]: warning: unknown[192.168.236.156]: SASL PLAIN authentication failed: authentication failure[/FONT]
[FONT=Menlo]Jun 14 10:44:38 fs1 postfix/smtpd[21212]: > unknown[192.168.236.156]: 535 5.7.8 Error: authentication failed: authentication failure[/FONT]

```

Since it appears to be impossible to tell which path Postfix is going to use to communicate with saslauthd I have tried both of the "usual" paths: [FONT=Menlo]/var/run/[/FONT][COLOR=#C33720][FONT=Menlo]**sasl**[/FONT][/COLOR][FONT=Menlo]authd and [/FONT][FONT=Menlo]/var/spool/postfix/var/run/saslauthd. Neither works. I've gone around on this for over a week now. Any useful suggestions would be appreciated. saslfinger output follows:

[/FONT]```
[FONT=Menlo]saslfinger -s[/FONT]
[FONT=Menlo]saslfinger - postfix Cyrus sasl configuration Tue Jun 14 10:04:38 EDT 2016[/FONT]
[FONT=Menlo]version: 1.0.4[/FONT]
[FONT=Menlo]mode: server-side SMTP AUTH[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]-- basics --[/FONT]
[FONT=Menlo]Postfix: 2.9.6[/FONT]
[FONT=Menlo]System: Ubuntu 12.04.5 LTS \n \l[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]-- smtpd is linked to --[/FONT]
[FONT=Menlo]    libsasl2.so.2 => /usr/lib/x86_64-linux-gnu/libsasl2.so.2 (0x00007f58bbfc6000)[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]-- active SMTP AUTH and TLS parameters for smtpd --[/FONT]
[FONT=Menlo]broken_sasl_auth_clients = yes[/FONT]
[FONT=Menlo]smtpd_sasl_auth_enable = yes[/FONT]
[FONT=Menlo]smtpd_sasl_local_domain =[/FONT]
[FONT=Menlo]smtpd_sasl_path = smtpd[/FONT]
[FONT=Menlo]smtpd_sasl_security_options = noanonymous[/FONT]
[FONT=Menlo]smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem[/FONT]
[FONT=Menlo]smtpd_tls_auth_only = no[/FONT]
[FONT=Menlo]smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt[/FONT]
[FONT=Menlo]smtpd_tls_key_file = /etc/ssl/private/smtpd.key[/FONT]
[FONT=Menlo]smtpd_tls_loglevel = 1[/FONT]
[FONT=Menlo]smtpd_tls_received_header = yes[/FONT]
[FONT=Menlo]smtpd_tls_security_level = may[/FONT]
[FONT=Menlo]smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache[/FONT]
[FONT=Menlo]smtpd_tls_session_cache_timeout = 3600s[/FONT]
[FONT=Menlo]smtpd_use_tls = yes[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]-- listing of /usr/lib/sasl2 --[/FONT]
[FONT=Menlo]total 36[/FONT]
[FONT=Menlo]drwxr-xr-x  2 root root  4096 Jun  9 11:38 .[/FONT]
[FONT=Menlo]drwxr-xr-x 97 root root 24576 Jun  9 14:36 ..[/FONT]
[FONT=Menlo]-rw-r--r--  1 root root     1 May  4  2012 berkeley_db.txt[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]-- listing of /etc/sasl2 --[/FONT]
[FONT=Menlo]total 20[/FONT]
[FONT=Menlo]drwxr-xr-x   2 root root  4096 May 15 09:32 .[/FONT]
[FONT=Menlo]drwxr-xr-x 146 root root 12288 Jun 14 09:06 ..[/FONT]
[FONT=Menlo]-rw-r--r--   1 root root    62 May 15 09:32 smtpd.conf[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]-- listing of /etc/postfix/sasl --[/FONT]
[FONT=Menlo]total 20[/FONT]
[FONT=Menlo]drwxr-xr-x 2 root root 4096 Jun 14 09:32 .[/FONT]
[FONT=Menlo]drwxr-xr-x 4 root root 4096 Jun 14 09:55 ..[/FONT]
[FONT=Menlo]-rw-r----- 1 root root   49 Jun  1 12:11 passwd-old[/FONT]
[FONT=Menlo]-rw-r--r-- 1 root root  227 Sep  5  2013 README[/FONT]
[FONT=Menlo]-rw-r--r-- 1 root root   62 Jun 14 09:08 smptd.conf[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]-- content of /etc/sasl2/smtpd.conf --[/FONT]
[FONT=Menlo]pwcheck_method: saslauthd[/FONT]
[FONT=Menlo]mech_list: PLAIN LOGIN[/FONT]
[FONT=Menlo]log_level: 5[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]-- active services in /etc/postfix/master.cf --[/FONT]
[FONT=Menlo]# service type  private unpriv  chroot  wakeup  maxproc command + args[/FONT]
[FONT=Menlo]#               (yes)   (yes)   (yes)   (never) (100)[/FONT]
[FONT=Menlo]smtp      inet  n       -       -       -       -       smtpd -v[/FONT]
[FONT=Menlo]pickup    unix  n       -       -       60      1       pickup[/FONT]
[FONT=Menlo]cleanup   unix  n       -       -       -       0       cleanup[/FONT]
[FONT=Menlo]qmgr      unix  n       -       n       300     1       qmgr[/FONT]
[FONT=Menlo]tlsmgr    unix  -       -       -       1000?   1       tlsmgr[/FONT]
[FONT=Menlo]rewrite   unix  -       -       -       -       -       trivial-rewrite[/FONT]
[FONT=Menlo]bounce    unix  -       -       -       -       0       bounce[/FONT]
[FONT=Menlo]defer     unix  -       -       -       -       0       bounce[/FONT]
[FONT=Menlo]trace     unix  -       -       -       -       0       bounce[/FONT]
[FONT=Menlo]verify    unix  -       -       -       -       1       verify[/FONT]
[FONT=Menlo]flush     unix  n       -       -       1000?   0       flush[/FONT]
[FONT=Menlo]proxymap  unix  -       -       n       -       -       proxymap[/FONT]
[FONT=Menlo]proxywrite unix -       -       n       -       1       proxymap[/FONT]
[FONT=Menlo]smtp      unix  -       -       -       -       -       smtp[/FONT]
[FONT=Menlo]relay     unix  -       -       -       -       -       smtp[/FONT]
[FONT=Menlo]showq     unix  n       -       -       -       -       showq[/FONT]
[FONT=Menlo]error     unix  -       -       -       -       -       error[/FONT]
[FONT=Menlo]retry     unix  -       -       -       -       -       error[/FONT]
[FONT=Menlo]discard   unix  -       -       -       -       -       discard[/FONT]
[FONT=Menlo]local     unix  -       n       n       -       -       local[/FONT]
[FONT=Menlo]virtual   unix  -       n       n       -       -       virtual[/FONT]
[FONT=Menlo]lmtp      unix  -       -       -       -       -       lmtp[/FONT]
[FONT=Menlo]anvil     unix  -       -       -       -       1       anvil[/FONT]
[FONT=Menlo]scache    unix  -       -       -       -       1       scache[/FONT]
[FONT=Menlo]maildrop  unix  -       n       n       -       -       pipe[/FONT]
[FONT=Menlo]  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}[/FONT]
[FONT=Menlo]uucp      unix  -       n       n       -       -       pipe[/FONT]
[FONT=Menlo]  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)[/FONT]
[FONT=Menlo]ifmail    unix  -       n       n       -       -       pipe[/FONT]
[FONT=Menlo]  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)[/FONT]
[FONT=Menlo]bsmtp     unix  -       n       n       -       -       pipe[/FONT]
[FONT=Menlo]  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient[/FONT]
[FONT=Menlo]scalemail-backend unix    -    n    n    -    2    pipe[/FONT]
[FONT=Menlo]  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}[/FONT]
[FONT=Menlo]mailman   unix  -       n       n       -       -       pipe[/FONT]
[FONT=Menlo]  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py[/FONT]
[FONT=Menlo]  ${nexthop} ${user}[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]-- mechanisms on localhost --[/FONT]
[FONT=Menlo]250-AUTH DIGEST-MD5 NTLM CRAM-MD5 PLAIN LOGIN[/FONT]
[FONT=Menlo]250-AUTH=DIGEST-MD5 NTLM CRAM-MD5 PLAIN LOGIN[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]-- end of saslfinger output --
[/FONT]
```
[FONT=Menlo]

[/FONT]

---

### Post by pgf1234 on 2016-06-16
Someone over at the postfix-users list noticed a typo in my configuration. The file
```
/etc/postfix/sasl/[COLOR=#000000][FONT=Menlo]smptd.conf
```
should have been
[/FONT][/COLOR]```
/etc/postfix/sasl/[COLOR=#000000][FONT=Menlo]sm[/FONT][/COLOR][FONT=Menlo]tp[/FONT][COLOR=#000000][FONT=Menlo]d.conf
```
note the transposed "tp" in the first file name.

Once I corrected this typo it all worked.[/FONT][/COLOR]

---

