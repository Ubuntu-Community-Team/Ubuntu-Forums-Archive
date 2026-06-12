---
title: "Cant start Dovecot"
date: 2012-12-23
forum: Server Platforms
---

### Post by QsoftStudios on 2012-12-23
I am trying to setup dovecot from this tutorial: [http://library.linode.com/email/postfix/dovecot-mysql-ubuntu-10.04-lucid]("http://library.linode.com/email/postfix/dovecot-mysql-ubuntu-10.04-lucid") 

When I use Webmin to start dovecot I keep getting this error. 

Failed to start Dovecot :
doveconf: Fatal: Error in configuration file /etc/dovecot/dovecot.conf line 19: Unknown setting: global_script_path


Here is my config file


```
protocols = imap pop3
log_timestamp = "%Y-%m-%d %H:%M:%S "
mail_location = maildir:/home/vmail/%d/%n/Maildir

ssl_cert = /etc/ssl/certs/dovecot.pem
ssl_key = /etc/ssl/private/dovecot.pem

namespace type=private {
    separator = .
    prefix = INBOX.
    inbox = yes
}

protocol lda {
    log_path = /home/vmail/dovecot-deliver.log
    auth_socket_path = /var/run/dovecot/auth-master
    postmaster_address = postmaster@example.com
    mail_plugins = sieve
    global_script_path = /home/vmail/globalsieverc
}

protocol pop3 {
    pop3_uidl_format = %08Xu%08Xv
}

auth default {
    user = root

    passdb sql {
        args = /etc/dovecot/dovecot-sql.conf
    }

    userdb static {
        args = uid=5000 gid=5000 home=/home/vmail/%d/%n allow_all_users=yes
    }

    socket listen {
        master {
            path = /var/run/dovecot/auth-master
            mode = 0600
            user = vmail
        }

        client {
            path = /var/spool/postfix/private/auth
            mode = 0660
            user = postfix
            group = postfix
        }
    }
}
```



How would I fix this? I did some research and apparently this file wont work with a 1.2X dovecot version. I am new to dovecot and not sure what to do. has that command been replaced with another? or do I need a diff config all together? Any help would be gladly appreciated. I'm running on Ubuntu 11.10 Server edition.

---

### Post by craigp84 on 2012-12-24
Hello,

I can't seem to access the linked tutorial you've provided, the site's giving me a domain not found error.

The protocol lda stanza you've listed looks like a dovecot 1.0 or 1.1 config. Sieve changed slightly in 1.2, here's the wiki page it's far more thorough in the steps than i can be: [http://wiki.dovecot.org/LDA/Sieve/Dovecot](http://wiki.dovecot.org/LDA/Sieve/Dovecot)

Hope this helps

---

### Post by chadk5utc on 2012-12-24
This line tells you everything you need or at least where to start
> doveconf: Fatal: Error in configuration file /etc/dovecot/dovecot.conf line 19: Unknown setting: global_script_path

open your config then goto line 19 verify the path is correct. What Version of Dovecot are you running? from what Ive read on a quick Google:"Unknown setting: global_script_path" search indicates a problem if your running newer version with an old config? You could try and remove that line and restart the service to see if that works or shows additional errors?

---

### Post by QsoftStudios on 2012-12-25
> **chadk5utc said:**
> This line tells you everything you need or at least where to start

open your config then goto line 19 verify the path is correct. What Version of Dovecot are you running? from what Ive read on a quick Google:"Unknown setting: global_script_path" search indicates a problem if your running newer version with an old config? You could try and remove that line and restart the service to see if that works or shows additional errors?

I have done this, removeing the line makes the Vuser brake. The path is correct its the setting in the actual config that seems to be the issue.

---

### Post by craigp84 on 2012-12-25
> **chadk5utc said:**
> indicates a problem if your running newer version with an old config?

Correct

> **chadk5utc said:**
> You could try and remove that line and restart the service to see if that works or shows additional errors?

You need to do more than that, see the link i provided.

---

