---
title: "Problem with dovecot setup"
date: 2010-08-11
forum: Server Platforms
---

### Post by bnelson01 on 2010-08-11
Hi everyone, I'm attempting to setup postfix and dovecot.  I've gotten postfix setup properly and can send and receive mail, however dovecot won't start and is dying with a permissions error that I can't find the source of.

Here's the error from mail.log
```
Aug 11 19:41:16 server dovecot: Dovecot v1.2.9 starting up (core dumps disabled)
Aug 11 19:41:16 server dovecot: auth(default): unlink(/var/spool/postfix/private/auth) failed: Permission denied
Aug 11 19:41:16 server dovecot: auth(default): Fatal: Socket already exists: /var/spool/postfix/private/auth
Aug 11 19:41:16 server dovecot: dovecot: Fatal: Auth process died too early - shutting down

```And here is my dovecot -n
```
# 1.2.9: /etc/dovecot/dovecot.conf
# OS: Linux 2.6.32-24-server x86_64  ext4
log_timestamp: %Y-%m-%d %H:%M:%S 
protocols: imaps pop3s
ssl_cert_file: /etc/ssl/certs/bserver.crt
ssl_key_file: /etc/ssl/private/bserver.key
disable_plaintext_auth: no
login_dir: /var/run/dovecot/login
login_executable(default): /usr/lib/dovecot/imap-login
login_executable(imap): /usr/lib/dovecot/imap-login
login_executable(pop3): /usr/lib/dovecot/pop3-login
mail_privileged_group: mail
mail_location: maildir:/home/%u/Mail
mbox_write_locks: fcntl dotlock
mail_executable(default): /usr/lib/dovecot/imap
mail_executable(imap): /usr/lib/dovecot/imap
mail_executable(pop3): /usr/lib/dovecot/pop3
mail_plugin_dir(default): /usr/lib/dovecot/modules/imap
mail_plugin_dir(imap): /usr/lib/dovecot/modules/imap
mail_plugin_dir(pop3): /usr/lib/dovecot/modules/pop3
auth default:
  mechanisms: plain login
  passdb:
    driver: pam
  userdb:
    driver: passwd
  socket:
    type: listen
    client:
      path: /var/spool/postfix/private/auth
      mode: 432
      user: postfix
      group: postfix

```One thing I don't understand is the line mode:432 since in dovecot.conf it says mode: 0660

I appreciate any and all help.

---

