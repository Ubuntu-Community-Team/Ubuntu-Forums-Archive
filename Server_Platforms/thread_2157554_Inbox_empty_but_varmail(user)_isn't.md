---
title: "Inbox empty but /var/mail/(user) isn't"
date: 2013-06-25
forum: Server Platforms
---

### Post by owen777 on 2013-06-25
Hello,

I followed Step-by-Step the following article "The Perfect Server Ubuntu 12.04" [here]("http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3"). The problem I have is that I cannot view my inbox of my user in squirrel mail or even when I set up my mail account on my phone, my inbox shows up empty. However, every time I log into SSH on my account, I always see "You have new mail". Once I installed "mail-utils" to see the mail in "/var/mail/myuser", the emails there are what I should be seeing in my inbox on squirrel mail AND on my phone (there is a "Welcome to ISPConfig" email in their too).

Any ideas? I'm completely stumbled as according to people, this should just work.

Regards,

- Owen

---

### Post by owen777 on 2013-06-26
Any ideas anyone?

---

### Post by nerdtron on 2013-06-26
The permissions on the emails. Kindly recheck them. It depends on what webmail you are using. In my roundcube install, the emails should be owned by vmail and group vmail and has 600 permissions. In Squirrel (old and ugly :D) the emails are owned by vpopmail, group vchkpw and 600 permissions.

Anyway, if you are just building you email server from scratch, I recommend iRedMail with Roundcube Webmail. Easy install in just a few minutes and works great out of the box. [http://www.iredmail.org/index.html](http://www.iredmail.org/index.html)

---

### Post by owen777 on 2013-07-04
Hi,

Thanks a lot for that, i'll definitely replace squirrel mail with it. However the problem still persists when I'm trying to refresh my inbox on my phone. I can't see any of the emails. My current dovecot config looks like this;

```
listen = *,[::]protocols = imap pop3
auth_mechanisms = plain login
disable_plaintext_auth = no
log_timestamp = "%Y-%m-%d %H:%M:%S "
mail_privileged_group = mail
mail_location = mbox:/var/empty:INBOX=/var/mail/%u:INDEX=MEMORY
ssl_cert = </etc/postfix/smtpd.cert
ssl_key = </etc/postfix/smtpd.key
passdb {
  args = /etc/dovecot/dovecot-sql.conf
  driver = sql
}
userdb {
  args = /etc/dovecot/dovecot-sql.conf
  driver = sql
}
plugin {
  quota = dict:user::file:/var/vmail/%d/%n/.quotausage
  sieve=/var/vmail/%d/%n/.sieve
}
service auth {
  unix_listener /var/spool/postfix/private/auth {
    group = postfix
    mode = 0660
    user = postfix
  }
  unix_listener auth-userdb {
    group = vmail
    mode = 0600
    user = vmail
  }
  user = root
}
protocol imap {
  mail_plugins = quota imap_quota
}
protocol pop3 {
pop3_uidl_format = %08Xu%08Xv
  mail_plugins = quota
}
protocol lda {
  mail_plugins = sieve quota
}
```

The permissions looks like this after running a check:

```
root@homeserver:/home/owen# ls -ld /var/mail
drwxrwsrwt 2 root mail 4096 Jun 30 06:31 /var/mail
```

---

### Post by nerdtron on 2013-07-04
If you're going to deploy Roundcube, might as well start with a fresh install of Ubuntu 12.04 server with no extra packages  installed (except for updates). See the installation here [http://www.iredmail.org/install_iredmail_on_ubuntu.html](http://www.iredmail.org/install_iredmail_on_ubuntu.html)

This is only a part of my dovecot conf. Your's is a lot smaller and I'm sure you haven't deployed roundcube yet. (iRedMail that is)
```
service auth {
    unix_listener /var/spool/postfix/dovecot-auth {
        user = postfix
        group = postfix
        mode = 0666
    }
    unix_listener auth-master {
        user = vmail
        group = vmail
        mode = 0666
    }
    unix_listener auth-userdb {
        user = vmail
        group = vmail
        mode = 0660
    }
}


```

And mail isn't stored in /var/mail, it is in /var/vmail folder.
```
drwx------ 5 vmail vmail 44 Jul  3 09:26 /var/vmail
```

Again, as I have said before, I can't help you much if manualy installed, postfix, dovecot, and other mail services seperately. Configuring them individually can be very complicated.
Just follow the link I gave you and all will be setup for you. When roundcube is up and running, then you can modify the configuration files that you want.

---

