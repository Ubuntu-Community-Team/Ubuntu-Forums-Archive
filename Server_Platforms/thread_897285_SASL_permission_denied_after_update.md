---
title: "SASL permission denied after update"
date: 2008-08-22
forum: Server Platforms
---

### Post by rockney on 2008-08-22
Installed the Postfix update tonight using the Update Manager in 8.04 server.  Now SMTP mail cannot be sent to the server running Postfix + Courier suite + SASL.

The mail.info log shows "postfix/smtp...warning: SASL authentication failure: cannot connect to saslauthd server: permission denied".

What happened, and how do I fix it ??

---

### Post by windependence on 2008-08-22
Check your permissions on /var/spool/postfix/var/run/saslauthd.

-Tim

---

### Post by rockney on 2008-08-23
The permissions are the same as the backups:
  710 with owner root and group sasl

The options in /etc/default/saslauthd have not changed:
  OPTIONS="-c -m /var/spool/postfix/var/run/saslauthd"

All files in /etc/pam.d are identical to those in the backups (rsync).

It does work when email is sent from another domain, e.g. gmail.com, but does not work when sending from Thunderbird.

Thanks a lot for the help - this has me stumped.

---

### Post by windependence on 2008-08-23
OK, I think you need to do a

  ```
      adduser postfix sasl
```

since postfix probably could not read the mux file.

-Tim

---

### Post by rockney on 2008-08-23
Fabulous!  That was it.  Thank you!!

But - because this server was already setup and working all I did was go into /etc/passwd and change the group for the postfix user back to the sasl group (45). The Postfix update had changed it to postfix (113). I verified that by looking in the backups.

Thanks again.

---

### Post by windependence on 2008-08-23
No problem. That happened when you did the upgrade. It set everything back to default.

-Tim

---

