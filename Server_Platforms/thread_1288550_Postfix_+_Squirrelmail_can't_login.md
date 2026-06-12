---
title: "Postfix + Squirrelmail can't login"
date: 2009-10-11
forum: Server Platforms
---

### Post by serlex on 2009-10-11
Hi

I have setup postfix as a mail server, can receive mail from outside (by checking Maildir of the user)

I'm now trying to setup Squirrelmail, however I cannot login...

/var/log/mail.log
```

Oct 11 16:56:12 acarfaa1 imapd: Connection, ip=[::ffff:127.0.0.1]
Oct 11 16:56:12 acarfaa1 imapd: LOGIN FAILED, user=comeon, ip=[::ffff:127.0.0.1]
Oct 11 16:56:17 acarfaa1 imapd: LOGOUT, ip=[::ffff:127.0.0.1], rcvd=43, sent=323

```

I must of missed something...

---

### Post by serlex on 2009-10-11
Fixed by editing /etc/courier/authdaemonrc, should look like this (if you not using MySQL authentication)

```

#authmodulelist="authmysql"
authmodulelist="authcustom authcram authuserdb authpam authpwd"
authmodulelistorig="authcustom authcram authuserdb authpam authpwd"

```

---

