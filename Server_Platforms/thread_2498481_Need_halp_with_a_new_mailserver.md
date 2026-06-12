---
title: "Need halp with a new mailserver"
date: 2024-06-15
forum: Server Platforms
---

### Post by beepee on 2024-06-15
Hi,

I'm trying to set up a new mailserver using a VM with a new Ubuntu 24.04LTS Server.

I have been following to the letter the instructions found here [https://www.rosehosting.com/blog/email-server-on-ubuntu-24-04](https://www.rosehosting.com/blog/email-server-on-ubuntu-24-04) to install Postfix, Dovecot, Postfixadmin and Roundcube Webmail on this standard LAMP Server. Later I want to install Rspamd and configure DKIM.

My problem is that at this stage there is somewhere a config error relating to those instructions since I am unable to login to any mail account neither with Thunderbird nor Roundcube. have triple checked the passwords but the system doesn't accept any.

Here are the relevant logs:


roundcube errors.log
```
[15-Jun-2024 10:47:08 +0000]: <klkhomsq> IMAP Error: Login failed for me@mydomain against localhost from 192.xxx.xxx.yyy. AUTHENTICATE PLAIN: Temporary authentication failure. [mailserver:2024-06-15 10:47:08] in /usr/share/roundcube/program/lib/Roundcube/rcube_imap.php on line 211 (POST /roundcube/?_task=login&_action=login)
[15-Jun-2024 10:47:22 +0000]: <klkhomsq> IMAP Error: Login failed for me@mydomain against localhost from 192.xxx.xxx.yyy. AUTHENTICATE PLAIN: Temporary authentication failure. [mailserver:2024-06-15 10:47:22] in /usr/share/roundcube/program/lib/Roundcube/rcube_imap.php on line 211 (POST /roundcube/?_task=login&_action=login)
```


mail.err
```
2024-06-15T12:47:06.853198+02:00 mailserver dovecot: auth-worker(57917): Error: conn unix:auth-worker (pid=57915,uid=113): auth-worker<1>: sql(me@mydomain,127.0.0.1,<OOoLdOsaHIJ/AAAB>): Invalid password in passdb: Password is not blowfish password
2024-06-15T12:47:20.953516+02:00 mailserver dovecot: auth-worker(57917): Error: conn unix:auth-worker (pid=57915,uid=113): auth-worker<2>: sql(me@mydomain,127.0.0.1,<QSumdOsaUp9/AAAB>): Invalid password in passdb: Password is not blowfish password
```

mail.log
```
2024-06-15T12:47:06.853198+02:00 mailserver dovecot: auth-worker(57917): Error: conn unix:auth-worker (pid=57915,uid=113): auth-worker<1>: sql(me@mydomain,127.0.0.1,<OOoLdOsaHIJ/AAAB>): Invalid password in passdb: Password is not blowfish password
2024-06-15T12:47:08.355864+02:00 mailserver dovecot: imap-login: Disconnected: Connection closed (auth service reported temporary failure): user=<me@mydomain>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured, session=<OOoLdOsaHIJ/AAAB>
2024-06-15T12:47:20.953516+02:00 mailserver dovecot: auth-worker(57917): Error: conn unix:auth-worker (pid=57915,uid=113): auth-worker<2>: sql(me@mydomain,127.0.0.1,<QSumdOsaUp9/AAAB>): Invalid password in passdb: Password is not blowfish password
2024-06-15T12:47:22.456849+02:00 mailserver dovecot: imap-login: Disconnected: Connection closed (auth service reported temporary failure): user=<me@mydomain>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured, session=<QSumdOsaUp9/AAAB>
```


syslog
```
2024-06-15T12:47:06.853198+02:00 mailserver dovecot: auth-worker(57917): Error: conn unix:auth-worker (pid=57915,uid=113): auth-worker<1>: sql(me@mydomain,127.0.0.1,<OOoLdOsaHIJ/AAAB>): Invalid password in passdb: Password is not blowfish password
2024-06-15T12:47:08.355864+02:00 mailserver dovecot: imap-login: Disconnected: Connection closed (auth service reported temporary failure): user=<me@mydomain>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured, session=<OOoLdOsaHIJ/AAAB>
2024-06-15T12:47:20.953516+02:00 mailserver dovecot: auth-worker(57917): Error: conn unix:auth-worker (pid=57915,uid=113): auth-worker<2>: sql(me@mydomain,127.0.0.1,<QSumdOsaUp9/AAAB>): Invalid password in passdb: Password is not blowfish password
2024-06-15T12:47:22.456849+02:00 mailserver dovecot: imap-login: Disconnected: Connection closed (auth service reported temporary failure): user=<me@mydomain>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured, session=<QSumdOsaUp9/AAAB>
```


So I changed in the dovecot-sql.conf.ext "default_pass_scheme = BLF-CRYPT" to "default_pass_scheme = MD5-CRYPT" and now I get these errors.
I suspect there might be somewhere a permission problem which I can't find...


roundcube errors.log
```
[15-Jun-2024 14:46:40 +0000]: <i924elb9> IMAP Error: Login failed for me@mydomain against localhost from 192.xxx.xxx.yyy. AUTHENTICATE PLAIN: Authentication failed. in /usr/share/roundcube/program/lib/Roundcube/rcube_imap.php on line 211 (POST /roundcube/?_task=login&_action=login)
```

mail.err
nothing

mail.log
```
2024-06-15T16:46:40.281956+02:00 mailserver dovecot: imap-login: Disconnected: Connection closed (auth failed, 1 attempts in 2 secs): user=<me@mydomain>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured, 9
```


syslog
```
2024-06-15T16:46:40.281956+02:00 mailserver dovecot: imap-login: Disconnected: Connection closed (auth failed, 1 attempts in 2 secs): user=<me@mydomain>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured, session=<SnemzO4a8pt/AAAB>

```

rcube_imap.php lines 209 to 212
```

                rcube::raise_error([
                        'code' => 403, 'type' => 'imap',
 'file' => __FILE__, 'line' => __LINE__,
                        'message' => $message

```

Any help would be highly appreciated.

---

### Post by currentshaft on 2024-06-20
Do you have a weird character in one of the passphrases, like a single quote or tilde?

---

### Post by galvan-rv on 2024-06-26
doing the same thing but still stock with this error - 

**Oops... something went wrong!**

[COLOR=#000000][FONT=sans-serif]An internal error has occurred. Your request cannot be processed at this time.[/FONT][/COLOR]
[COLOR=#888888][FONT=sans-serif][I]For administrators: Please check the application and/or server error logs for more information.

[SIZE=4]can anyone help?[/SIZE][/I][/FONT][/COLOR]

---

### Post by currentshaft on 2024-06-26
Check the logs as OP has done for a clue.

---

### Post by beepee on 2024-06-30
Since I have tried several things:
- Password: I have tried with this test Password: Qwertz,123 => same thing
- Added to /etc/dovecot/conf.d/10-auth.conf one line: disable_plaintext_auth = no => same thing
- Changed /etc/dovecot/dovecot-sql.conf.ext comment out the 2 last lines and inserted the new instructions found on linuxize.com
```
#password_query = SELECT username as user, password, '/var/vmail/%d/%n' as userdb_home, 'maildir:/var/vmail/%d/%n' as userdb_mail, 150 as
#user_query = SELECT '/var/vmail/%d/%u' as home, 'maildir:/var/vmail/%d/%u' as mail, 150 AS uid, 8 AS gid, concat('dirsize:storage=', quota) userdb_uid, 8 as userdb_gid FROM mailbox WHERE username = '%u' AND active = '1' AS quota FROM mailbox WHERE username = '%u' AND active = '1'

iterate_query = SELECT username AS user FROM mailbox
user_query = SELECT CONCAT('/var/mail/vmail/',maildir) AS home, \
CONCAT('maildir:/var/mail/vmail/',maildir) AS mail, \
5000 AS uid, 5000 AS gid, CONCAT('*:bytes=',quota) AS quota_rule \
FROM mailbox WHERE username = '%u' AND active = 1
password_query = SELECT username AS user,password FROM mailbox \
WHERE username = '%u' AND active='1
```'
=> still same thing

I'll be searching more in the next few days...

---

### Post by nvanschoote on 2024-07-09
Hello,

Looking at the "Invalid password in passdb: Password is not blowfish password", probably that the password isn't hashed correctly,

 Are your usernames and passwords set through Postfixadmin? If so, double-check how Postfixadmin hashes the passwords.

Check this [page]("https://github.com/postfixadmin/postfixadmin/blob/master/DOCUMENTS/HASHING.md") for more info

---

### Post by beepee on 2024-07-14
Hi,
Thanks for this hint: Postfixadmin was set to sha512 as crypt. Thus I edited  the dovecot-sql.conf.ext "default_pass_scheme = MD5-CRYPT" to "default_pass_scheme = SHA512-CRYPT" and now I get these errors:

roundcube imap.log
> [14-Jul-2024 15:44:01 +0000]: <mimu55m5> [EFDB] Connecting to localhost:143...
[14-Jul-2024 15:44:01 +0000]: <mimu55m5> [EFDB] S: * OK [CAPABILITY IMAP4rev1 SASL-IR LOGIN-REFERRALS ID ENABLE IDLE LITERAL+ STARTTLS AUTH=PLAIN AUTH=LOGIN] Dovecot (Ubuntu) ready.
[14-Jul-2024 15:44:01 +0000]: <mimu55m5> [EFDB] C: A0001 AUTHENTICATE PLAIN ****** [49]
[14-Jul-2024 15:44:03 +0000]: <mimu55m5> [EFDB] S: A0001 NO [AUTHENTICATIONFAILED] Authentication failed.

I wonder if there is a problem in the /etc/dovecot/conf.d/10-auth.conf ?
> auth_mechanisms = plain login
do I need to add some reference to the sha512 crypt - if yes, what would be the correct syntax?

---

### Post by beepee on 2024-07-23
OK folks,
I'm done with postfixadmin! I have lost enough time thus I searched for <postfixadmin alternatives>.
I found the mailcow.email project which is sensational. It's a complete mailserver package. And it is installed within minutes, configuration is easy. It a dockerized install of postfix, dovecot, ClamAV, rspamd, and many more...
IMHO the best way to set up a mailserver.

---

