---
title: "postfix connect from unknown[]"
date: 2009-09-02
forum: Server Platforms
---

### Post by root1234 on 2009-09-02
Hi all.

I have a server running postfix and dovecot.
All was fine but the last few days dovecot keeps on stopping and have to restart it.

the error it is giving me is ... imap-login: Disconnected: Inactivity: method=PLAIN

the other thing I see in the logs , there is a lot of 
connect from unknown[***.***.***.***]
disconnect from unknown[***.***.***.***]

The Ip address in these logs is not any of my clients...

Could someone help me blocking these IP address or stop dovecot from stopping.

It will be great!
Thanks
Root1234

---

### Post by noway2 on 2009-09-02
If you have IPTables installed, you can block the addresses pretty easilly.  I may not have the sytanx exactly correct but it would be something like: (sudo) iptables -I INPUT -s (the ip address) -j DROP.

Otherwise, I am not sure what the error code means, but I suspect that it is important to find out WHAT is going on so that you can correct the root problem rather than masking the symptom by blocking this particular IP.

---

