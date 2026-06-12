---
title: "Email Server Problems"
date: 2005-06-02
forum: Server Platforms
---

### Post by caeserjk on 2005-06-02
I followed the tutorial on installing Hula as a mail-calendar server. Everthing seems to be working fine, but I have run into a few issues. I can telnet localhost:25 and get access to the hula SMTP server. but if I try that from another computer on the same network I get "Connection refused" error. This is a default install of Ubuntu Hoary, with hula and depends. Any suggestions to be able to access port 25 from another computer?

---

### Post by dataw0lf on 2005-06-02
Check hosts.deny and hosts.allow.  Any iptable rules set up?

---

