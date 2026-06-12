---
title: "Help with website port managment"
date: 2009-11-04
forum: Server Platforms
---

### Post by any.linux12 on 2009-11-04
Hi!

I have one mail server that has web access for clients and this is a feature that I want to keep, the problem is that is being listened on the port 80 and I really don't want that. I want to have my website on the port 80 and my mail's server web access somewhere else from 1 to 99999 \ 80 (not on the 80 pleazzz).

Is there any file that has the port configuration? or can I configure with the webmin?? 

Other thing, I already tried the Virtual Hosting but no success, so that's something that I would like to avoid...

By the way my mail server is a zimbra server and my server is an ubuntu 8.04

thanks...

---

### Post by cdenley on 2009-11-04
I believe this should change the port zimbra's apache instance listens on for non-encrypted connections. I haven't tested it, though.
```

sudo -u zimbra /opt/zimbra/bin/zmprov mcf zimbraMailPort <new port>
sudo -u zimbra /opt/zimbra/bin/zmapachectl restart

```
By the way, zimbra is not an ubuntu-supported piece of software, and zimbra has its own support forum, so I would suggest using their forum in the future. You would probably get better support there.
[http://www.zimbra.com/forums/](http://www.zimbra.com/forums/)

---

