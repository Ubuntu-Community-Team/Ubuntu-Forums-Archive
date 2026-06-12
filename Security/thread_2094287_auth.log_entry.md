---
title: "auth.log entry"
date: 2012-12-13
forum: Security
---

### Post by pgte3 on 2012-12-13
Why do I see myself successfully logging on in auth.log (below) from port 57111 when I have port 22 specified in my putty client? (port 22 for the server, not the client?)

Dec  9 13:37:04 dovetail sshd[10627]: Failed password for paul from 133.242.56.278 port 57111 ssh2

---

### Post by Doug S on 2012-12-13
Port 57111 is the port you were trying to connect from not to.
The TCP session was from 133.242.56.278 port 57111 to your server port 22.
If you try again with a new puTTY session, you will find it uses a different "from" port, as systems rotate through the available port numbers.

---

### Post by pgte3 on 2012-12-13
Thought so, thanks.

---

