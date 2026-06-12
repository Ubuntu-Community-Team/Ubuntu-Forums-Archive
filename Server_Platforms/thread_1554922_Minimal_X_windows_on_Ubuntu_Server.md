---
title: "Minimal X windows on Ubuntu Server"
date: 2010-08-17
forum: Server Platforms
---

### Post by ecampbell on 2010-08-17
First, I'm new to Ubuntu and I'm remote from the server.  I'm setting up an Ubuntu server 10.04 x64.  My intention is to load Oracle 11g, however I know I will need to be able to export an X display back to my desktop (Solaris) to run the Oracle installer.  What do I need to load to get X working enough to export the display back to myself.

Thanks for any assistance you can provide and let me know if I need to provide additional information.  Since I'm new I may not have adequately covered what's needed.

---

### Post by CharlesA on 2010-08-17
Just forward X over SSH. 

You should be able to connect with: 

```
SSH -X user@host
```

Then start the program. If sshd is configured to X forwarding, the program should show up on yer local machine.

---

### Post by bodhi.zazen on 2010-08-18
X does not help all that much on servers.

Take a look at web based options such as webmin ;)

---

### Post by ecampbell on 2010-08-20
That seems to work. Thanks, didn't know the X option to ssh.

---

### Post by ecampbell on 2010-08-20
Thanks, I really just need to send a display back to my workstation and it was suggested to use ssh -X and that seems to work.

---

