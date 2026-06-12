---
title: "Ubuntu 11.10 sieve problem"
date: 2012-01-29
forum: Server Platforms
---

### Post by littlepitt on 2012-01-29
I've an ubuntu 11.10 server with dovecot and postfix running.
Everything works fine, and sieve filters are correctly working.
The problem is that when i try a telnet on the machine:
telnet 127.0.0.1 2000
the connection is refused. :confused:
Since the filters are processed correctly and dovecot is running, and since I've turned off apparmor and I've not installed any kind of firewall...
How can I proceed?
Thanks in advance...
Pietro

---

### Post by littlepitt on 2012-01-30
Solved...
Don't know why but, although in the configuration file I specify the sieve port as 2000, the default port for sieve is now 4190. :shock:
Correcting this I can access also from external (web interface) to the sieve management.
:guitar:

---

