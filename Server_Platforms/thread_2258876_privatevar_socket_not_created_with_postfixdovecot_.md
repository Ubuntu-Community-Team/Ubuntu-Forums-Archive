---
title: "/private/var socket not created with postfix/dovecot sasl"
date: 2014-12-31
forum: Server Platforms
---

### Post by devos50 on 2014-12-31
I'm currently running into a problem I have with my email server. I try to setup Postfix and Dovecot with SASL authentication but I get the following error when I connect with telnet (port 25) to the server:

```

Dec 30 17:42:51 mail postfix/smtpd[2857]: warning: SASL: Connect to private/auth failed: No such file or directory
Dec 30 17:42:51 mail postfix/smtpd[2857]: fatal: no SASL authentication mechanisms

```


After some investigation, it appears that the socket file */var/spool/postfix/private/auth* is not created by postfix/dovecot. When running the *doveconf *command, I get the following entry for *service auth* which contains the entry for private/auth:

```

    service auth {
      chroot =  
      client_limit = 0
      drop_priv_before_exec = no
      executable = auth
      extra_groups = 
      group = 
      idle_kill = 0
      privileged_group = 
      process_limit = 1
      process_min_avail = 0
      protocol = 
      service_count = 0
      type = 
      unix_listener /var/spool/postfix/private/auth {
        group = postfix
        mode = 0666
        user = postfix
      }
      unix_listener auth-client {
        group = 
        mode = 0600
        user = $default_internal_user
      }
      unix_listener auth-login {
        group = 
        mode = 0600
        user = $default_internal_user
      }
      unix_listener auth-master {
        group = 
        mode = 0600
        user = 
      }
      unix_listener auth-userdb {
        group = mail
        mode = 0666
        user = vmail
      }
      unix_listener login/login {
        group = 
        mode = 0666
        user = 
      }
      unix_listener token-login/tokenlogin {
        group = 
        mode = 0666
        user = 
      }
      user = $default_internal_user
      vsz_limit = 18446744073709551615 B
    }

```

And when running *postconf*, I get the following configuration regarding *smtpd_sasl*:

```

    smtpd_sasl_auth_enable = yes
    smtpd_sasl_authenticated_header = yes
    smtpd_sasl_exceptions_networks =
    smtpd_sasl_local_domain =
    smtpd_sasl_path = private/auth
    smtpd_sasl_security_options = noanonymous
    smtpd_sasl_service = smtp
    smtpd_sasl_tls_security_options = $smtpd_sasl_security_options
    smtpd_sasl_type = dovecot

```

So I'm not sure why *private/var* is not created by dovecot or postfix. Could anyone explain this phenomema? I think that the problem is related to Dovecot. I'm using version 2.2.9 of Dovecot.

---

### Post by slickymaster on 2014-12-31
*Moved to the ***Server Platforms*** sub-forum*

---

### Post by schragge on 2014-12-31
Check that your postfix main.cf has this:
```
queue_directory = /var/spool/postfix
```

---

