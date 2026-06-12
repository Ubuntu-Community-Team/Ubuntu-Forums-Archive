---
title: "dovecot failed to start - status 89"
date: 2010-12-30
forum: Server Platforms
---

### Post by Nunnsby on 2010-12-30
Hey All

Helping hand that took me over 3 hours to solve!

If you are having problems getting dovecot to start, and you can't see errors in /var/log/mail.log, but do see errors in /var/log/syslog stating:

 [FONT="Courier New"]init: dovecot main process (xxxxx) terminated with status 89[/FONT]

check your dovecot config (/etc/dovecot/dovecot.conf) to make sure that you have terminated ALL brackets {}. If you have an open bracket in a paragraph {, it must be terminated by at closing bracket }.

eg:

[FONT="Courier New"]protocol pop3 **{**
  pop3_uidl_format = %08Xu%08Xv
**}**[/FONT]

This is usually the standard, but if you hack your config like I have been doing, you might miss a closing bracket somewhere. Especially in cascading paragraphs.

eg:

[FONT="Courier New"]auth default **{**
  mechanisms = plain login
  socket listen **{**
  client **{**
      path = /var/spool/postfix/private/auth-client
      mode = 0660
      user = postfix
      group = postfix
    **}**
  **}**
**}**[/FONT]

**THREE **opening brackets, **THREE **cosing brackets.

Hope this helps someone out there! Very little results, if none, on search engines for Dovecot Error 89! :(

Regards, and Happy New Year All

Nunnsby

---

### Post by aslok on 2011-02-04
I have this

[aslok@3r]2011.02.05-04:51:17:~$ tail -F /var/log/syslog
Feb  5 05:11:58 3r dovecot: Dovecot v1.2.12 starting up (core dumps disabled)
Feb  5 05:11:58 3r dovecot: auth(default): Fatal: No passdbs specified in configuration file. PLAIN mechanism needs one
Feb  5 05:11:58 3r dovecot: dovecot: Fatal: Auth process died too early - shutting down
Feb  5 05:11:58 3r init: dovecot main process (23120) terminated with status 89

---

### Post by Nunnsby on 2011-02-09
Aslok, your problem definitely relates to the one line in your log:

dovecot: auth(default): Fatal: No passdbs specified in configuration file. PLAIN mechanism needs one

Check the section where it mentions passdb. This is under the following section:


##
## Authentication processes
##

It would appear that you have not selected a method of verifying Passwords, or it is not terminated properly. I am definitely NOT an expert at Dovecot by any means, in fact hardly know how it works, but check that all brackets are terminated. Sometimes they only have 2, not 3 closing brackets.

As per here: 

# Password database is used to verify user's password (and nothing more).
# You can have multiple passdbs and userdbs. This is useful if you want to
# allow both system users (/etc/passwd) and virtual users to login without
# duplicating the system users into virtual database.

basically you need to tell Dovecot how to auth users. The passdb tell it what database to use for authentication.

Hope that helps.

---

### Post by neca on 2012-09-11
> **Nunnsby said:**
> Hey All

Helping hand that took me over 3 hours to solve!

If you are having problems getting dovecot to start, and you can't see errors in /var/log/mail.log, but do see errors in /var/log/syslog stating:

 [FONT="Courier New"]init: dovecot main process (xxxxx) terminated with status 89[/FONT]

check your dovecot config (/etc/dovecot/dovecot.conf) to make sure that you have terminated ALL brackets {}. If you have an open bracket in a paragraph {, it must be terminated by at closing bracket }.

Nunnsby, will you marry me? :)

---

### Post by tylmaster on 2012-10-24
thanks, this was a great help to me.

but it doesn't have to be necessarily a missing bracket, seems as it could be any other misconfiguration.

in our case it was a missing (commented) *driver = pam* in the file auth-system.conf.ext

```

passdb {
  #driver = pam
  # [session=yes] [setcred=yes] [failure_show_msg=yes] [max_requests=<n>]
  # [cache_key=<key>] [<service name>]
  args = mail
}
```

---

