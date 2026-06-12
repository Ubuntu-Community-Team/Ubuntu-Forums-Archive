---
title: "dovecot connection problems.."
date: 2006-02-10
forum: Server Platforms
---

### Post by HS-L on 2006-02-10
Hello,

I've got dovecot installed on my server (running dapper)
it's running and i can connect to port 143 with telnet,
but my mail application does not work, i get the error:
```

You can not login because the server has disabled login.

```

```
## Dovecot 1.0 configuration file

protocols = imap
listen = *
log_timestamp = "%Y-%m-%d %H:%M:%S "
login_greeting = ctu ready.
mail_extra_groups = mail
default_mail_env = ~/Maildir
protocol imap {}
auth default {
  mechanisms = plain
  passdb passwd {/etc/shadow }
  passdb pam { %u }
  userdb passwd {  }
  user = root
}

## Dovecot log

Feb 10 12:24:02 ctu dovecot: Killed with signal 15
Feb 10 12:24:03 ctu dovecot: Dovecot v1.0.alpha5 starting up
Feb 10 12:24:12 ctu dovecot: imap-login: Aborted login: rip=194.109.1.245, lip=82.94.255.234

```

above i pasted the ldovecto.conf and a part of the system log.
i must be doing something wrong, but what?

can somebody help me?

greetings Harold

---

### Post by drogoh on 2006-02-10
```
# Disable LOGIN command and all other plaintext authentications unless
# SSL/TLS is used (LOGINDISABLED capability). Note that 127.*.*.* and
# IPv6 ::1 addresses are considered secure, this setting has no effect if
# you connect from those addresses.
#disable_plaintext_auth = yes
```

That is from dovecot-example.conf on my mail server, and is the default for Dovecot.  To remedy that, you would either need to add "disable_plaintext_auth = no" to dovecot.conf or enable SSL/TLS.  Personally, I'd just enable the plaintext auth because it was a pain to get SSL/TLS enabled.

---

### Post by HS-L on 2006-02-10
jups, that was the problem, found it out myself 10 minutes ago, now time to get it working with SSL :)

---

