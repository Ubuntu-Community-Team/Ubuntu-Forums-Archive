---
title: "Postfix mail unable to configure properly."
date: 2014-03-06
forum: Security
---

### Post by amitray2 on 2014-03-06
Dear friends,
  I need help in configuring mail in my Ubuntu 13+ Server. I installed postfix, dovecote and squirrelmail to see message. But i am unable to make it work properly. I followed the instructions here [https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto) and also another link  that showed me path to install dovecote but i am not able to integrate everyhgting properly. On giving this command
"$ tail -n 50 /var/log/mail.log"
 i am getting this message:

```
Mar  5 08:55:20 prepage dovecot: pop3-login: Aborted login (tried to use disallowed plaintext auth): user=<>, rip=187.54.71.135, lip=140.207.27.250[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.250[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.250, session=
Mar  5 08:55:21 prepage dovecot: pop3-login: Aborted login (tried to use disallowed plaintext auth): user=<>, rip=187.54.71.135, lip=140.207.27.252[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.252[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.252, session=
Mar  5 08:55:21 prepage dovecot: pop3-login: Aborted login (tried to use disallowed plaintext auth): user=<>, rip=187.54.71.135, lip=140.207.27.250[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.250[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.250, session=
Mar  5 08:55:21 prepage dovecot: pop3-login: Aborted login (tried to use disallowed plaintext auth): user=<>, rip=187.54.71.135, lip=140.207.27.252[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.252[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.252, session=

Mar  5 08:55:22 prepage dovecot: pop3-login: Aborted login (tried to use disallowed plaintext auth): user=<>, rip=187.54.71.135, lip=140.207.27.250[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.250[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.250, session=
Mar  5 08:55:22 prepage dovecot: pop3-login: Aborted login (tried to use disallowed plaintext auth): user=<>, rip=187.54.71.135, lip=140.207.27.252[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.252[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.252, session=
Mar  5 08:55:22 prepage dovecot: pop3-login: Aborted login (tried to use disallowed plaintext auth): user=<>, rip=187.54.71.135, lip=140.207.27.250[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.250[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.250, session=<7rU5X9zzrgC7NkeH>
Mar  5 08:55:23 prepage dovecot: pop3-login: Aborted login (tried to use disallowed plaintext auth): user=<>, rip=187.54.71.135, lip=140.207.27.252[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.252[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.252, session=
Mar  5 08:55:23 prepage dovecot: pop3-login: Aborted login (tried to use disallowed plaintext auth): user=<>, rip=187.54.71.135, lip=140.207.27.250[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.250[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.250, session=

Mar  5 08:55:24 prepage dovecot: pop3-login: Aborted login (tried to use disallowed plaintext auth): user=<>, rip=187.54.71.135, lip=140.207.27.252[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.252[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.252, session=
Mar  5 08:55:24 prepage dovecot: pop3-login: Aborted login (tried to use disallowed plaintext auth): user=<>, rip=187.54.71.135, lip=140.207.27.250[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.250[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.250, session=
Mar  5 08:55:24 prepage dovecot: pop3-login: Aborted login (tried to use disallowed plaintext auth): user=<>, rip=187.54.71.135, lip=140.207.27.252[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.252[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.252, session=
Mar  5 08:55:24 prepage dovecot: pop3-login: Aborted login (tried to use disallowed plaintext auth): user=<>, rip=187.54.71.135, lip=140.207.27.250[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.250[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.250, session=
Mar  5 08:55:25 prepage dovecot: pop3-login: Aborted login (tried to use disallowed plaintext auth): user=<>, rip=187.54.71.135, lip=140.207.27.252[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.252[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.252, session=
Mar  5 08:55:25 prepage dovecot: pop3-login: Aborted login (tried to use disallowed plaintext auth): user=<>, rip=187.54.71.135, lip=140.207.27.250[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.250[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.250, session=
Mar  5 08:55:26 prepage dovecot: pop3-login: Aborted login (tried to use disallowed plaintext auth): user=<>, rip=187.54.71.135, lip=140.207.27.252[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.252[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.252, session=
Mar  5 08:55:26 prepage dovecot: pop3-login: Aborted login (tried to use disallowed plaintext auth): user=<>, rip=187.54.71.135, lip=140.207.27.250[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.250[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.250, session=<8tuX9zz0QC7NkeH>
Mar  5 08:55:27 prepage dovecot: pop3-login: Aborted login (tried to use disallowed plaintext auth): user=<>, rip=187.54.71.135, lip=140.207.27.252[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.252[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.252[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.252, session=
Mar  5 08:55:27 prepage dovecot: pop3-login: Disconnected (no auth attempts in 11 secs): user=<>, rip=187.54.71.135, lip=140.207.27.252[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.252, session=
Mar  5 08:55:27 prepage dovecot: pop3-login: Aborted login (tried to use disallowed plaintext auth): user=<>, rip=187.54.71.135, lip=140.207.27.250[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.250[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.250[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.250, session=
Mar  5 08:55:27 prepage dovecot: pop3-login: Disconnected (no auth attempts in 11 secs): user=<>, rip=187.54.71.135, lip=140.207.27.250[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.250[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.250[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.250, session=
Mar  5 09:19:28 prepage postfix/postdrop[14906]: warning: unable to look up public/pickup: No such file or directory
Mar  5 10:02:28 prepage postfix/postdrop[15423]: warning: unable to look up public/pickup: No such file or directory
Mar  5 10:53:29 prepage postfix/postdrop[15543]: warning: unable to look up public/pickup: No such file or directory
Mar  5 12:16:30 prepage postfix/postdrop[15659]: warning: unable to look up public/pickup: No such file or directory
Mar  6 01:41:05 prepage postfix/postdrop[16306]: warning: unable to look up public/pickup: No such file or directory
Mar  6 01:41:08 prepage postfix/postdrop[16309]: warning: unable to look up public/pickup: No such file or directory
Mar  6 02:05:35 prepage postfix/postdrop[16325]: warning: unable to look up public/pickup: No such file or directory
Mar  6 03:42:23 prepage postfix/postdrop[16435]: warning: unable to look up public/pickup: No such file or directory
Mar  6 04:16:47 prepage postfix/postdrop[16459]: warning: unable to look up public/pickup: No such file or directory
Mar  6 04:55:27 prepage postfix/postdrop[16505]: warning: unable to look up public/pickup: No such file or directory
Mar  6 05:06:40 prepage postfix/postdrop[16518]: warning: unable to look up public/pickup: No such file or directory
Mar  6 05:08:44 prepage postfix/postdrop[16521]: warning: unable to look up public/pickup: No such file or directory
Mar  6 08:49:13 prepage postfix/master[17189]: fatal: listen: Address already inuse
Mar  6 08:49:28 prepage postfix/postfix-script[17214]: fatal: the Postfix mail system is not running
Mar  6 08:50:32 prepage postfix/master[17342]: fatal: listen: Address already in use
Mar  6 08:52:06 prepage postfix/postfix-script[17402]: the Postfix mail system is not running
Mar  6 08:54:16 prepage dovecot: config: Warning: NOTE: You can get a new cleanconfig file with: doveconf -n > dovecot-new.conf
Mar  6 08:54:16 prepage dovecot: config: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:99: 'imaps' protocol is no longer necessary, remove it
Mar  6 08:54:16 prepage dovecot: config: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:99: 'pop3s' protocol is no longer necessary, remove it
Mar  6 08:54:16 prepage dovecot: config: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:102: ssl_cert_file has been replaced by ssl_cert = <file
Mar  6 08:54:16 prepage dovecot: config: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:103: ssl_key_file has been replaced by ssl_key = <file
Mar  6 08:55:15 prepage dovecot: imap-login: Disconnected (no auth attempts in 59 secs): user=<>, rip=140.207.27.250[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.250, lip=140.207.27.250[IMG]resource://skype_ff_extension-at-jetpack/skype_ff_extension/data/call_skype_logo.png[/IMG]140.207.27.250, TLS handshaking: SSL_a                                                                                                                     ccept() failed: error:140760FC:SSL routines:SSL23_GET_CLIENT_HELLO:unknown protocol, session=
Mar  6 08:57:08 prepage sm-mta[17597]: alias database /etc/mail/aliases.db out of date
Mar  6 08:57:08 prepage sm-mta[17597]: s26DuPWo017597: fmaster@localhost... User unknown
Mar  6 08:57:32 prepage sm-mta[17597]: s26DuPWo017597: from=root@localhost, size=0, class=0, nrcpts=0, proto=ESMTP, daemon=MTA-v4,relay=localhost.localdomain [127.0.0.1]
Mar  6 09:02:03 prepage sm-mta[17622]: s26DwohE017622: from=root@localhost, size=0, class=0, nrcpts=0, proto=ESMTP, daemon=MTA-v4, relay=localhost.localdomain [                                                                                                                     127.0.0.1]
Mar  6 09:03:13 prepage sm-mta[17624]: s26E2ZhZ017624: localhost.localdomain [127.0.0.1] did not issue MAIL/EXPN/VRFY/ETRN during connection to MSP-v4
Mar  6 09:03:56 prepage postfix/postfix-script[17642]: fatal: the Postfix mail system is not running
Mar  6 09:07:43 prepage postfix/postfix-script[17672]: fatal: the Postfix mail system is not running
```

---

### Post by SeijiSensei on 2014-03-06
You need to put text like that inside of [noparse]```

```[/noparse].

Did you read the errors?  "Aborted login (tried to use disallowed plaintext auth)" means your mail client is sending your username and password in clear text, but dovecot expects you to be using an encrypted method instead.  You can either change your server to accept plain text, or change your client to use TLS.

---

### Post by amitray2 on 2014-03-08
> **SeijiSensei said:**
> You need to put text like that inside of [noparse]```

```[/noparse].

Did you read the errors?  "Aborted login (tried to use disallowed plaintext auth)" means your mail client is sending your username and password in clear text, but dovecot expects you to be using an encrypted method instead.  You can either change your server to accept plain text, or change your client to use TLS.

Thanks a lot for the help sir. Actually I am new to linux and i just purchased an open vz VPS. Slowly I am trying to understand how this works. I will try to implement that solution and come back if I still have issues. 
Regards
Amit.

---

