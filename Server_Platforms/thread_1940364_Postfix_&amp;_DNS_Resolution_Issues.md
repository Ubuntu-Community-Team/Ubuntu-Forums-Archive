---
title: "Postfix &amp; DNS Resolution Issues"
date: 2012-03-13
forum: Server Platforms
---

### Post by geudrik on 2012-03-13
Hello all,

I've got postfix set up and running properly, but the issue that I'm running into is that when mail is sent to the server, it is rejected with with the following
```

Mar 12 12:58:13 localhost postfix/smtpd[27152]: connect from unknown[216.93.144.65]
Mar 12 12:58:13 localhost postfix/smtpd[27152]: NOQUEUE: reject: RCPT from unknown[216.93.144.65]: 450 4.7.1 Client host rejected: cannot find your hostname, [216.93.144.65]; from=<prvs=0418d5c8aa=some.student@mymail.champlain.edu> to=<me@myserver.com> proto=ESMTP helo=<nickel.champlain.edu>

```

Thus, postfix is not resolving domain name properly.  I have run both dig and host and I continually am served valid responses. I've also flushed my local DNS cache (I am not running a DNS server locally) and postfix is not in a chroot jail.  I've looked over my /etc/resolv.conf and all is working properly.  Linked below is the config that I'm using.  

Any thoughts why Postfix is rejecting/delaying mail (can't resolve hostnames?)

[http://pastebin.com/Fwj04jRm](http://pastebin.com/Fwj04jRm)

---

### Post by mruiz@ic-sa.com on 2012-03-13
> **geudrik said:**
> Hello all,

I've got postfix set up and running properly, but the issue that I'm running into is that when mail is sent to the server, it is rejected with with the following
```

Mar 12 12:58:13 localhost postfix/smtpd[27152]: connect from unknown[216.93.144.65]
Mar 12 12:58:13 localhost postfix/smtpd[27152]: NOQUEUE: reject: RCPT from unknown[216.93.144.65]: 450 4.7.1 Client host rejected: cannot find your hostname, [216.93.144.65]; from=<prvs=0418d5c8aa=some.student@mymail.champlain.edu> to=<me@myserver.com> proto=ESMTP helo=<nickel.champlain.edu>

```

Thus, postfix is not resolving domain name properly.  I have run both dig and host and I continually am served valid responses. I've also flushed my local DNS cache (I am not running a DNS server locally) and postfix is not in a chroot jail.  I've looked over my /etc/resolv.conf and all is working properly.  Linked below is the config that I'm using.  

Any thoughts why Postfix is rejecting/delaying mail (can't resolve hostnames?)

[http://pastebin.com/Fwj04jRm](http://pastebin.com/Fwj04jRm)

What does your conf file say?  Do you have domains or ip added to the allowed list? Thanks.

---

