---
title: "dovecot: doveconf: Warning: ... 'imaps' protocol is no longer necessary, remove it"
date: 2012-02-18
forum: Server Platforms
---

### Post by dchen on 2012-02-18
Ubuntu 11.10 server configured with postfix/dovecot servers with TLS/SSL for IMAP, POP3, and SMTP Auth, got repeating messages (below) in syslog file, however, both postfix and dovecot servers seemed eventually ran.   Can anyone explain ?  thx.

Feb 16 03:23:13 server dovecot: master: Dovecot v2.0.13 starting up (core dumps disabled)
Feb 16 03:23:13 server dovecot: doveconf: Warning: NOTE: You can get a new clean config file with: doveconf -n > dovecot-new.conf
Feb 16 03:23:13 server dovecot: doveconf: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:25: 'imaps' protocol is no longer necessary, remove it
Feb 16 03:23:13 server dovecot: doveconf: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:25: 'pop3s' protocol is no longer necessary, remove it
Feb 16 03:23:13 server dovecot: doveconf: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:100: ssl_cert_file has been replaced by ssl_cert = <file
Feb 16 03:23:13 server dovecot: doveconf: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:101: ssl_key_file has been replaced by ssl_key = <file
Feb 16 03:23:13 server dovecot: doveconf: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:716: protocol managesieve {} has been replaced by protocol sieve { }
Feb 16 03:23:13 server dovecot: doveconf: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:888: add auth_ prefix to all settings inside auth {} and remove the auth {} section completely
Feb 16 03:23:13 server dovecot: doveconf: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:926: passdb pam {} has been replaced by passdb { driver=pam }
Feb 16 03:23:13 server dovecot: doveconf: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:1039: userdb passwd {} has been replaced by userdb { driver=passwd }
Feb 16 03:23:13 server dovecot: doveconf: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:1101: auth_user has been replaced by service auth { user }
Feb 16 03:23:13 server dovecot: config: Warning: NOTE: You can get a new clean config file with: doveconf -n > dovecot-new.conf
Feb 16 03:23:13 server dovecot: config: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:25: 'imaps' protocol is no longer necessary, remove it
Feb 16 03:23:13 server dovecot: config: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:25: 'pop3s' protocol is no longer necessary, remove it
Feb 16 03:23:13 server dovecot: config: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:100: ssl_cert_file has been replaced by ssl_cert = <file
Feb 16 03:23:13 server dovecot: config: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:101: ssl_key_file has been replaced by ssl_key = <file
Feb 16 03:23:13 server dovecot: config: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:716: protocol managesieve {} has been replaced by protocol sieve { }
Feb 16 03:23:13 server dovecot: config: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:888: add auth_ prefix to all settings inside auth {} and remove the auth {} section completely
Feb 16 03:23:13 server dovecot: config: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:926: passdb pam {} has been replaced by passdb { driver=pam }
Feb 16 03:23:13 server dovecot: config: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:1039: userdb passwd {} has been replaced by userdb { driver=passwd }
Feb 16 03:23:13 server dovecot: config: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:1101: auth_user has been replaced by service auth { user }
Feb 16 03:23:15 server dovecot: log: Warning: Killed with signal 15 (by pid=1 uid=0 code=kill)
Feb 16 03:23:15 server dovecot: master: Warning: Killed with signal 15 (by pid=1 uid=0 code=kill)
Feb 16 03:23:15 server dovecot: master: Dovecot v2.0.13 starting up (core dumps disabled)
Feb 16 03:23:15 server dovecot: doveconf: Warning: NOTE: You can get a new clean config file with: doveconf -n > dovecot-new.conf
Feb 16 03:23:15 server dovecot: doveconf: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:25: 'imaps' protocol is no longer necessary, remove it
Feb 16 03:23:15 server dovecot: doveconf: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:25: 'pop3s' protocol is no longer necessary, remove it
Feb 16 03:23:15 server dovecot: doveconf: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:100: ssl_cert_file has been replaced by ssl_cert = <file
Feb 16 03:23:15 server dovecot: doveconf: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:101: ssl_key_file has been replaced by ssl_key = <file
Feb 16 03:23:15 server dovecot: doveconf: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:716: protocol managesieve {} has been replaced by protocol sieve { }
Feb 16 03:23:15 server dovecot: doveconf: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:888: add auth_ prefix to all settings inside auth {} and remove the auth {} section completely
Feb 16 03:23:15 server dovecot: doveconf: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:926: passdb pam {} has been replaced by passdb { driver=pam }
Feb 16 03:23:15 server dovecot: doveconf: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:1039: userdb passwd {} has been replaced by userdb { driver=passwd }
Feb 16 03:23:15 server dovecot: doveconf: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:1101: auth_user has been replaced by service auth { user }
Feb 16 03:23:15 server dovecot: config: Warning: NOTE: You can get a new clean config file with: doveconf -n > dovecot-new.conf
Feb 16 03:23:15 server dovecot: config: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:25: 'imaps' protocol is no longer necessary, remove it
Feb 16 03:23:15 server dovecot: config: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:25: 'pop3s' protocol is no longer necessary, remove it
Feb 16 03:23:15 server dovecot: config: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:100: ssl_cert_file has been replaced by ssl_cert = <file
Feb 16 03:23:15 server dovecot: config: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:101: ssl_key_file has been replaced by ssl_key = <file
Feb 16 03:23:15 server dovecot: config: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:716: protocol managesieve {} has been replaced by protocol sieve { }
Feb 16 03:23:15 server dovecot: config: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:888: add auth_ prefix to all settings inside auth {} and remove the auth {} section completely
Feb 16 03:23:15 server dovecot: config: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:926: passdb pam {} has been replaced by passdb { driver=pam }
Feb 16 03:23:15 server dovecot: config: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:1039: userdb passwd {} has been replaced by userdb { driver=passwd }
Feb 16 03:23:15 server dovecot: config: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:1101: auth_user has been replaced by service auth { user }
Feb 16 03:23:55 server postfix/master[2109]: terminating on signal 15
Feb 16 03:23:55 server postfix/master[4768]: daemon started -- version 2.8.5, configuration /etc/postfix

---

