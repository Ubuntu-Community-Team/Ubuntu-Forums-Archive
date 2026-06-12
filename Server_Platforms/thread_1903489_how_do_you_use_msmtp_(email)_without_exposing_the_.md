---
title: "how do you use msmtp (email) without exposing the password?"
date: 2012-01-02
forum: Server Platforms
---

### Post by anon0 on 2012-01-02
How do you configure msmtp to know the password without storing the password as plain text in /etc/msmtprc?

In other words, could you show how ‘passwordeval’ works? This is from the manual:
"If no password is set but one is needed during authentication, msmtp will try to find it.
First, if ‘passwordeval’ is set, it will evaluate that command. 
If ‘passwordeval’ is not set, msmtp will try to find the password in ~/.netrc. 
If that fails, it will try to find it in SYSCONFDIR/netrc 
(use --version to find out what SYSCONFDIR is on your platform). 
If that fails, it will try to get it from a system specific keyring (if available). 
If that fails but a controlling terminal is available, msmtp will prompt you for it."
[http://msmtp.sourceforge.net/doc/msmtp.html](http://msmtp.sourceforge.net/doc/msmtp.html)

---

