---
title: "Telnet Problem on port 25"
date: 2006-06-20
forum: Server Platforms
---

### Post by izzyonstage on 2006-06-20
Hi,
I have just set-up a mail server on my ubuntu Breezy, using courier, postfix and roundcube. While installing everything telnet worked fine. Now i have finnished installing, and went to test roundcube. Could log in but could not send an email. So decided to check using telnet again and all i get now is: -

Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.

It will not bring up the 220 line so i can 'ehlo'. Can anyone point me in the right direction?]

](*,) ](*,)

---

### Post by jvl on 2006-06-22
Have you set up packet filtering? 

what does "sudo iptables -L -n" and "sudo netstat -tanp" say?

---

### Post by herald on 2006-06-23
In past experiences, I have not always been prompted with the 220 line.  Some servers turn this off as to run security through obscurity.  Obviously this is a poor excuse for security, but, have you tried typing in the "helo localhost" (and pressing enter) anyway?

---

### Post by herald on 2006-06-23
and I forgot to mention...if you are even getting a Connect to... IPTables by default is properly configured.  If the port was blocked, you wouldn't even be able to telnet to it.  Therefore, it sounds to me like a configuration issue.

---

