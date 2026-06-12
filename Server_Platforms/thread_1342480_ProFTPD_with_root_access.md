---
title: "ProFTPD with root access?"
date: 2009-11-30
forum: Server Platforms
---

### Post by cablejimmy on 2009-11-30
I've read like a million forums, yet I still can not figure out how to get root access through ftp. I'm using proftpd for the server. For now, only I can access the server, so I wanted to be able to have full control over it.

---

### Post by hictio on 2009-11-30
Why on Earth would you want to do this?

---

### Post by Paul Weaver on 2009-12-01
This is a *really* bad idea. Use sftp if you must have that level of needless access, but it's likely your system is not set up correctly. It's not just obvious problems which can be worked around with separate networks and iptables, it's the danger of things like worms, and the danger of proftpd having a security flaw.

You'll need to pop this into your ftp config:
[http://www.proftpd.org/docs/directives/linked/config_ref_RootLogin.html](http://www.proftpd.org/docs/directives/linked/config_ref_RootLogin.html)

---

### Post by lemuriaX on 2009-12-01
Why would you want to use FTP rather than SSH for this?

---

### Post by cablejimmy on 2009-12-01
Like I said, I'm the only one in this home network, so I don't really have to worry. It's not like I'm controlling a subway system that NEEDS stability. It's just a little home network. But thank you lemur guy. I don't know why I didn't think of ssh before. That's what I'm using instead.

---

