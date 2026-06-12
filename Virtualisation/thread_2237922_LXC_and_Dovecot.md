---
title: "LXC and Dovecot"
date: 2014-08-04
forum: Virtualisation
---

### Post by daanmeerts-i on 2014-08-04
I did setup postfix and dovecot with the help of [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix) and [https://help.ubuntu.com/community/Dovecot](https://help.ubuntu.com/community/Dovecot). If I install it on a machine this way it works but if I install it into an LXC container it doens't work. The postfix is working. If I do telnet localhost imap2 I get the messag*e telnet: Unable to connect to remote host: Connection refused*. If I do *ps -A | grep dovecot*Ubuntu shows nothing. Im using Ubuntu 14.04 server.

---

