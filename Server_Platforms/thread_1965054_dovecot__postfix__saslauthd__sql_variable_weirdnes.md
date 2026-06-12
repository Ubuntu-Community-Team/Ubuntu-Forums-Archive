---
title: "dovecot / postfix / saslauthd / sql variable weirdness"
date: 2012-04-25
forum: Server Platforms
---

### Post by luserbackslashunderscore on 2012-04-25
Hi guys n gals, im on an ubuntu 11 VPS on linode. ive spent a lot of time and googling trying to get postfix, dovecot, ssl, saslauthd and mysql to all play nice together and im quite close now but theres something going on i cant quite explain and id really appreciate some help. I have been going for ten hours on this today and it seems in direct conflict with what dovecot themselves say...

*the problem is a variable in dovecot (%u) which is normally used as a full username in sql query strings (i.e. user@domain) and is simply dropping the domain for no reason...*

From dovecot docs ([http://wiki2.dovecot.org/Variables):]("http://wiki2.dovecot.org/Variables%29:")
```

The variables that work *everywhere* are:
    %u    user full username (e.g. user@domain) 
```so i have postfix and stuff set up ok to send at least and i know this because ive tested it by hard-coding the string in the sql query myself with a successful send...
but, anyway, the problem with the '%u' variable is it is doing stuff like this: (from mail.log and mysql.log)
```

localhost dovecot: auth: Debug: sql(admin@microhard.com,xx.xx.xx.xx): SELECT home,uid,gid FROM users WHERE id = 'admin@microhard.com'
```this was derived from the following query in /etc/dovecot/dovecot-sql.conf.ext
```
user_query = SELECT home,uid,gid FROM users WHERE id = '%u'
```so no problem there....

but then this happens when i attempt to send mail and this means the user gets rejected because dovecot cant find the user id in the db without the correct string (i.e. user@domain):
```
localhost dovecot: auth: Debug: sql(admin,xx.xx.xx.xx): query: SELECT id as user, crypt as password FROM users WHERE id= 'admin'
``````
Query    SELECT id as user, crypt as password FROM users WHERE id= 'admin'
```which is derived from the following query also in /etc/dovecot/dovecot-sql.conf.ext
```
password_query = SELECT id as user, crypt as password FROM users WHERE id= '%u'
```and to further confuse me, this 'unchangeable' variable sometimes decides to right itself without any obvious reason...
```
localhost dovecot: auth: Debug: sql(admin@microhard.com,xx.xx.xx.xx): query: SELECT id as user, crypt as password FROM users WHERE id= 'admin@microhard.com'
```im wondering if its something to do with my client (thunderbird) dropping the domain, or whether dovecot has an error, or some other thing ive overlooked...

my dovecot.conf looks a lot like this:
```
# 2.0.13: dovecot.conf
# OS: Linux 3.0.18-x86_64-linode24 x86_64 Ubuntu 11.10 ext3
first_valid_uid = 5000
last_valid_uid = 5000
login_greeting = I likes my ducks n geese I do.
mail_location = maildir:/var/spool/mail/virtual/%u

#enables logging all failed authentication attempts.
auth_verbose=yes

#enables all authentication debug logging (also enables auth_verbose). Passwords are logged as <hidden>.
auth_debug=yes

#does everything that auth_debug=yes does, but it also removes password hiding.
auth_debug_passwords=yes

#enables all kinds of mail related debug logging, such as showing where Dovecot is looking for mails.
mail_debug=yes

#enables logging SSL errors and warnings. Even without this setting if connection is closed because of an SSL error, the error is logged as the disconnection reason (v1.1+). 
verbose_ssl=yes

passdb {
  args = /etc/dovecot/dovecot-sql.conf.ext
  driver = sql
}
plugin {
  acl = vfile:/etc/dovecot/acls
  #quota = maildir:storage=10240:messages=1000
  trash = /etc/dovecot/trash.conf
}
protocols = " imap"
service auth {
  unix_listener /var/spool/postfix/private/auth {
    group = postfix
    mode = 0660
    user = postfix
  }
  unix_listener auth-master {
    group = dovecot
    mode = 0660
    user = dovecot
  }
  user = dovecot
}

ssl_ca = /etc/pki/dovecot/certs/ca-bundle.crt
ssl_cert = </etc/ssl/certs/dovecot.pem
ssl_key = </etc/ssl/private/dovecot.pem

userdb {
  args = /etc/dovecot/dovecot-sql.conf.ext
  driver = sql
}

userdb {
  driver = prefetch
}
userdb {
  driver = passwd
}
protocol imap {
  mail_plugins = quota imap_quota
}
protocol pop3 {
  mail_plugins = quota
  pop3_client_workarounds = outlook-no-nuls oe-ns-eoh
}
protocol lda {
  info_log_path = /var/log/dovecot-deliver.log
  log_path = /var/log/dovecot-deliver.log
  mail_plugins = quota
  postmaster_address = admin@microhard.com
}
```any help *much* appreciated!

---

### Post by luserbackslashunderscore on 2012-04-25
ah its ok i figured it out. the solution was not to ask ubuntu users.

---

### Post by 95yj on 2012-04-25
> **luserbackslashunderscore said:**
> ah its ok i figured it out. the solution was not to ask ubuntu users.

Glad you were able to solve the issue.  Rather than post a comment that it was fixed even though no one replied to you, you could post your solution so that others doing searches could benefit from your solution when searching.  That would be helpful information for everyone.

---

### Post by luserbackslashunderscore on 2012-04-27
cant be arsed, this forum is retarded anyway, its like a collection of the most clueless linux users on the net. ubuntu - for divs. gawd knows why i came here, its obvious nothings got better ere....

**** everyone.

---

