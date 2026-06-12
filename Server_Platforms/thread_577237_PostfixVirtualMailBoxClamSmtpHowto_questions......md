---
title: "PostfixVirtualMailBoxClamSmtpHowto questions....."
date: 2007-10-16
forum: Server Platforms
---

### Post by huggy77 on 2007-10-16
[https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto](https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto)

is a great tutorial - but i think the dovecot.conf is no longer valid because the auth method on this tutorial have been depreicated...  i have it kinda working using this
```

base_dir = /var/run/dovecot/
protocols = imap
log_path = /var/log/dovecot/dovecot.log
info_log_path = /var/log/dovecot/dovecot-info.log
login_dir = /var/run/dovecot/login
login_chroot = yes
login = imap
login_executable = /usr/lib/dovecot/imap-login
login_user = dovecot
valid_chroot_dirs = /var/spool/vmail
default_mail_env = maildir:/home/vmail/%d/%n
mail_executable = /usr/lib/dovecot/imap
#auth = default
disable_plaintext_auth = no
auth_mechanisms = plain digest-md5
auth default {
        mechanisms = plain digest-md5
        passdb passwd-file {
        # Virtual Users from file
                args = /etc/dovecot/passwd
        }
        userdb passwd-file {
        # Virtual Users from file
                args = /etc/dovecot/users
        }
user=root
}
auth_executable = /usr/lib/dovecot/dovecot-auth
auth_user = root
auth_verbose = yes

```


i am having relaying issues(logs):
```

Oct 15 13:40:09 mailworks postfix/smtpd[8561]: warning: 24.225.250.54: hostname static-host-24-225-340-54.patmedia.net verification failed: Name or service not known
Oct 15 13:40:09 mailworks postfix/smtpd[8561]: connect from unknown[24.225.250.54]
Oct 15 13:40:09 mailworks postfix/smtpd[8561]: NOQUEUE: reject: RCPT from unknown[24.225.250.54]: 554 5.7.1 <webgeneral@gmail.com>: Relay access denied; from=<webmaster@huggyworld.com> to=<webgeneral@gmail.com> proto=ESMTP helo=<chris-legges-computer.local>

```




```

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu/GNU)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

myhostname = localhost
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = $myhostname
mynetworks = 127.0.0.0/8, 192.0.0.0/2
mailbox_size_limit = 0
home_mailbox = Maildir/
virtual_mailbox_domains = /etc/postfix/vhosts
virtual_mailbox_base = /home/vmail
virtual_mailbox_maps = hash:/etc/postfix/vmaps
virtual_minimum_uid = 1000
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
recipient_delimiter = +
inet_interfaces = all

```

i can send email when i am home, on my recognized network...  the relay issues occur when i try and send mail outside my castle...  On the outside i can send email from virtual user to virtual user as well

pls advise....

i think i have to add some type of AUTH to postfix but i am not sure....

---

### Post by K.Mandla on 2007-10-24
Moved to Servers and Security.

---

