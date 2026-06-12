---
title: "[SOLVED] Postfix SASL via dovecot fails with &amp;quot;fatal: no SASL authentication mechanism"
date: 2008-12-29
forum: Server Platforms
---

### Post by timandjulz on 2008-12-29
I configured postfix to use SASL to authenticate via dovecot.  Pop3 authenticates fine.  SMTP does not.  I get this in the log file "fatal: no SASL authentication mechanisms"

These are the facts and how I validated.

**Postfix has support for dovecot sasl:**
postconf -a returns "dovecot" and "cyrus"

**Dovecot creates the auth file for postfix:**
I removed the auth file and restarted dovecot.  auth is recreated

**Postfix is looking at the same auth file that dovecot created:**
I stopped postfix and dovecot, removed the auth file and started postfix.  Postfix logs "warning: SASL: Connect to private/auth failed: No such file or directory"

**Postfix is configured for sasl in main.cf:**
smtpd_sasl_auth_enable = yes
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
smtpd_sasl_authenticated_header = yes


**auth's mode is correct:**
Results of ls -l /var/spool/postfix/private/auth
srw-rw---- 1 postfix postfix 0 2008-12-29 19:20 auth
Dovecot configuration:
    client {
          # Assuming the default Postfix $queue_directory setting
          path = /var/spool/postfix/private/auth
          mode = 0660
          # Assuming the default Postfix user and group
          user = postfix
          group = postfix
    }


I need to narrow down where the problem is.  Right now it looks like a problem with postfix.

**_HOW DO I TROUBLESHOOT THIS?_**
Is there a way to open the auth socket and validate dovecot is exposing the socket correctly?  Are there other configurations I should check?

Thanks,
Tim

---

### Post by albinootje on 2008-12-29
> **timandjulz said:**
> 
ls -l /var/spool/postfix/private/auth
srw-rw---- 1 postfix postfix 0 2008-12-29 19:20 auth


On where mail-server where I successfully use postfix+dovecot+SASL :

```

 ls -l /var/spool/postfix/private/auth
srw-rw---- 1 postfix mail 0 Oct 28 02:38 /var/spool/postfix/private/auth

ls -l /var/spool/postfix/auth/dovecot 
srw-rw---- 1 postfix mail 0 Dec 23 22:50 /var/spool/postfix/auth/dovecot

```

```

smtpd_sasl_auth_enable          = yes
#smtpd_sasl_local_domain        = $myhostname
smtpd_sasl_exceptions_networks  = $mynetworks
smtpd_sasl_security_options     = noanonymous
broken_sasl_auth_clients        = yes
smtpd_sasl_type                 = dovecot
# Can be an absolute path, or relative to $queue_directory
##smtpd_sasl_path                 = private/auth
smtpd_sasl_path = auth/dovecot

```

Do you use postfix chrooted ? See : /etc/postfix/master.cf
See also here :
[http://wiki.dovecot.org/HowTo/PostfixAndDovecotSASL](http://wiki.dovecot.org/HowTo/PostfixAndDovecotSASL)
[http://www.postfix.org/SASL_README.html#server_dovecot](http://www.postfix.org/SASL_README.html#server_dovecot)

---

### Post by timandjulz on 2008-12-29
Thanks albinootje.  It looks like you have reconfigured to use auth/dovecot instead of private/auth.  I assume your dovecot config for "client { }" points to the same folder.  Can you paste that?

Thanks again,
Tim

---

### Post by albinootje on 2008-12-29
> **timandjulz said:**
> Thanks albinootje.  It looks like you have reconfigured to use auth/dovecot instead of private/auth.  I assume your dovecot config for "client { }" points to the same folder.  Can you paste that?

I forgot to include that at first, but I've just edited my last comment to include it.

---

### Post by albinootje on 2008-12-29
And here's the relevant part of my dovecot.conf file :
```

}
auth default {
  mechanisms = plain
  passdb sql {
    args = /etc/dovecot/dovecot-sql.conf
  }
  userdb sql {
    args = /etc/dovecot/dovecot-sql.conf
  }
  userdb prefetch {
  }
  user = nobody
  socket listen {
    master {
      path = /var/run/dovecot/auth-master
      mode = 0600
      user = vmail
      group = mail
    }
    client {
      path = /var/spool/postfix/auth/dovecot
      mode = 0660
      user = postfix
      group = mail
    }
  }
}

```

---

### Post by timandjulz on 2008-12-29
I switched back to an older config and it is working again.  Apparently there was a conflict between the previous authentication method (mysql query vs dovecot).  I have no idea what was causing the problem.  Troubleshooting something like this is darn near impossible.

I am closing this thread.  Thanks to albinootje for your input.  :-)

---

### Post by albinootje on 2008-12-29
> **timandjulz said:**
> Troubleshooting something like this is darn near impossible.


That's not correct.
I have years of experience with postfix and dovecot, and I can tell you that it all boils down to using the logfiles properly.

What is however really unpleasant to (not) debug is a setup with Courier Maildrop.

---

### Post by Techjacker on 2010-10-17
> **albinootje said:**
> On where mail-server where I successfully use postfix+dovecot+SASL :

```

 ls -l /var/spool/postfix/private/auth
srw-rw---- 1 postfix mail 0 Oct 28 02:38 /var/spool/postfix/private/auth

ls -l /var/spool/postfix/auth/dovecot 
srw-rw---- 1 postfix mail 0 Dec 23 22:50 /var/spool/postfix/auth/dovecot

``````

smtpd_sasl_auth_enable          = yes
#smtpd_sasl_local_domain        = $myhostname
smtpd_sasl_exceptions_networks  = $mynetworks
smtpd_sasl_security_options     = noanonymous
broken_sasl_auth_clients        = yes
smtpd_sasl_type                 = dovecot
# Can be an absolute path, or relative to $queue_directory
##smtpd_sasl_path                 = private/auth
smtpd_sasl_path = auth/dovecot

```Do you use postfix chrooted ? See : /etc/postfix/master.cf
See also here :
[http://wiki.dovecot.org/HowTo/PostfixAndDovecotSASL](http://wiki.dovecot.org/HowTo/PostfixAndDovecotSASL)
[http://www.postfix.org/SASL_README.html#server_dovecot](http://www.postfix.org/SASL_README.html#server_dovecot)



you are THE man!
that dovecot wiki troubleshooting guide saved me.

anyone else who has been having troubles sending mail after following [this guide]("http://library.linode.com/email/postfix/postfix-dovecot-mysql-ubuntu-10.04-lucid"), that wiki article holds the solution.

Thanks!

---

### Post by aadmi on 2011-11-08
I struggled with this issue for a while before finding out the correct solution. It is important that you place the queue_directory path before smtpd_sasl_path, that is if your smtpd_sasl_path is relative. In my case:

queue_directory = /var/spool/postfix
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth

did the trick for me.:D

Bill

---

