---
title: "telnet localhost 110 says trying ::1"
date: 2010-08-14
forum: Server Platforms
---

### Post by Apot on 2010-08-14
Hello

I am trying to set up postfix on my ubuntu server.

When I try to login to the pop accounts through telnet


```
user@ubuntu1:/$ telnet localhost 110
Trying ::1...
Connected to localhost.
Escape character is '^]'.
+OK Hello there.
```

Which is ok because it lets me start, but i can't login to any or my setup mailboxes that i created using postfixadmin.

If I try to login to a mailbox through telnet it produces the following entries in /var/log/mail.log:

```

Aug 14 11:40:00 ubuntu1 pop3d: Connection, ip=[::1]
Aug 14 11:40:13 ubuntu1 pop3d: LOGIN FAILED, user=userm@domain.com, ip=[::1]
Aug 14 11:40:21 ubuntu1 pop3d: LOGOUT, ip=[::1]
Aug 14 11:40:21 ubuntu1 pop3d: Disconnected, ip=[::1]

```

I suspect that the fact that telnet pogs into POP3 at [::1] could be a problem.
* I have changed the user and doamins to 'user' and 'domain'

Any help or suggestions would be greatly appreciated.

---

### Post by CharlesA on 2010-08-14
::1 is the IPv6 loopback address.


Try using telnet 127.0.0.1 110

---

### Post by Apot on 2010-08-14
Thanks for the reply

I used telnet 127.0.0.1 and it logged me in trying 127.0.0.1 exactly what I wanted to do but the same thing happened. I am still not able to login to my mailboxes.

The mail.log just changed [::1] to [::ffff:127.0.0.1] ha, now it shows:

```
Aug 14 12:34:14 ubuntu1 pop3d: Connection, ip=[::ffff:127.0.0.1]
Aug 14 12:34:36 ubuntu1 pop3d: LOGIN FAILED, user=user@domain.com, ip=[::ffff:127.0.0.1]
Aug 14 12:35:12 ubuntu1 pop3d: LOGOUT, ip=[::ffff:127.0.0.1]
Aug 14 12:35:12 ubuntu1 pop3d: Disconnected, ip=[::ffff:127.0.0.1]
```

Now I know it has nothing to do with telnet trying ::1!

Thanks for your suggestion

---

### Post by CharlesA on 2010-08-14
I've not used postfix, so I don't know how you would configure it.

---

