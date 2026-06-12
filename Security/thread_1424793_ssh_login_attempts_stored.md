---
title: "ssh login attempts stored?"
date: 2010-03-08
forum: Security
---

### Post by shortridge11 on 2010-03-08
I have a box i shared with a friend.  I changed my password a little bit ago and then tried connecting over ssh, but he changed that port.  Can he see my usr/psswd in a log somewhere?

---

### Post by wojox on 2010-03-08
They'll see your username but not your password.

---

### Post by shortridge11 on 2010-03-08
phew. is there a way for them to crack my password since it's on their box? It's a standard ubuntu 8.10 install, 9 char psswd alternating alpha then numeric then alpha then numeric.... etc. ie a1b2c3d4e

---

### Post by wojox on 2010-03-08
The password won't even show up in the log file and no they won't crack it.

---

### Post by cdenley on 2010-03-08
I modified openssh once to log all failed passwords for a honeypot, so it is certainly possible for a server to store your password, but with an unmodified version of openssh, it is impossible. It would be a huge security problem on an actual server, since many failed password attempts would be a slight variation of an actual password resulting from caps-lock, num-lock, or a typo.

If you tried connecting to a port which had no listening server, then there wouldn't have even been a service to log that attempt, but then you wouldn't have been prompted for a password, either. Your client wouldn't have established a connection to send the password over.

---

