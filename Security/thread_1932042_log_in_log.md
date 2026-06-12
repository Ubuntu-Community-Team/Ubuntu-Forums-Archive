---
title: "log in log"
date: 2012-02-26
forum: Security
---

### Post by Diametric on 2012-02-26
Hello,

What file is written to when a user has logged into the system?  I'm assuming it's in var/log - but which file?  Also, does said file capture failed attempts and track the IP?

Thank you!

---

### Post by Dangertux on 2012-02-26
The file /var/log/auth.log (/var/log/secure on RHEL based systems) should contain most of your failed logins.

---

### Post by Diametric on 2012-02-26
Cool - thank you for your reply.  That is exactly what I was looking for.  Some D-bag is attempting to brute-force their way into an ssh session.  Only thing I can't figure is how is my system allowing more then three attempts.  I thought it failed out after three.

---

### Post by Dangertux on 2012-02-26
It will only fail after 3 attempts if you have enabled pam-tally in /etc/pam.d/system-auth

You can also consider iptables rate limiting. Fail2ban or denyhosts.

Hope this helps.

---

### Post by Diametric on 2012-02-26
It does.  If for no other reason, I didn't know about the pam.d directory, and I can now learn. Thanks again.

Cheers.

---

