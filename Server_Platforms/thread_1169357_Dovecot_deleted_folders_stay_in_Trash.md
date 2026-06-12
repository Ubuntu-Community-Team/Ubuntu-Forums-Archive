---
title: "Dovecot deleted folders stay in Trash"
date: 2009-05-25
forum: Server Platforms
---

### Post by rconen on 2009-05-25
I have a little problem with my postfix/dovecot mailserver. We're using Thunderbird as IMAP client to the dovecot server and using a Trash folder for deleted stuff.

When a folder is delete it will moved to the Trash. This looks ok but when the Trash is emptied the deleted folders stay in the Trash.
I'm using the following dovecot configuration:

```
base_dir = /var/run/dovecot/
protocols = imap pop3
disable_plaintext_auth = no
shutdown_clients = yes
log_path= /var/log/dovecot
info_log_path = /var/log/dovecot.info
log_timestamp = "%Y-%m-%d %H:%M:%S "
ssl_disable = yes
login_dir = /var/run/dovecot/login
login_chroot = yes
login_user = dovecot
login_greeting = Mailserver ready.
mail_location = maildir:/home/vmail/%d/%n:LAYOUT=fs
mmap_disable = no
valid_chroot_dirs = /var/spool/vmail
protocol imap {
    login_executable = /usr/lib/dovecot/imap-login
    mail_executable = /usr/lib/dovecot/imap
}
protocol pop3 {
    login_executable = /usr/lib/dovecot/pop3-login
    mail_executable = /usr/lib/dovecot/pop3
    pop3_uidl_format = %08Xu%08Xv
}

auth_executable = /usr/lib/dovecot/dovecot-auth
auth_verbose = yes
auth default {
    mechanisms = plain digest-md5
    passdb passwd-file {
        args = /etc/dovecot/passwd
    }

    userdb passwd-file {
        args = /etc/dovecot/users
    }

    user = root

}
```

---

