---
title: "skype blocking"
date: 2010-07-06
forum: Security
---

### Post by learnbash on 2010-07-06
Hello folks,

I want to block skype via iptables, i have search alot but all efforts are fail, can someone recommend anything.

Thanks.

---

### Post by yeleek on 2010-07-06
[http://blog.tmcnet.com/blog/tom-keating/skype/block-skype.asp](http://blog.tmcnet.com/blog/tom-keating/skype/block-skype.asp)

which could lead you here

[http://l7-filter.clearfoundation.com/#documentation](http://l7-filter.clearfoundation.com/#documentation)

but thats nothing I've tried to implement.

---

### Post by learnbash on 2010-07-06
I have already tried these things, not working.

---

### Post by bodhi.zazen on 2010-07-06
You can try squid

This is for BSD, but squid runs on Linux.

Install then configure squid

[http://lists.grok.org.uk/pipermail/full-disclosure/2005-November/038646.html](http://lists.grok.org.uk/pipermail/full-disclosure/2005-November/038646.html)

---

### Post by HermanAB on 2010-07-06
You cannot block Skype.  Simple as that.

Resistance is futile, you will be VoIPed.

---

### Post by yeleek on 2010-07-07
You sure?

[http://l7-filter.sourceforge.net/protocols](http://l7-filter.sourceforge.net/protocols)

As that lists skype as a supported protocol........

---

### Post by HermanAB on 2010-07-07
One baaaaaad way to prevent the use of Skype and most other troublesome programs, is to drop every tenth packet on all ports except the usual web and email ports.  It will still work, but it will sound so crappy that no-one will want to use it and Skype-out will be broken completely.

---

### Post by WinstonChurchill on 2010-07-08
> **learnbash said:**
> Hello folks,

I want to block skype via iptables, i have search alot but all efforts are fail, can someone recommend anything.

Thanks.What about blocking all UDP traffic to and from the internet? If this is a business/school situation (which would make sense, since he/she's trying to block Skype), the end-users should never be doing anything that requires UDP anyway. But the question is, can Skype function over TCP alone? My experience trying to stream video over SSH/SFTP TCP connections would suggest that even if it could, it would be nigh unusable.
```

iptables --append FORWARD --protocol udp --dst [Server that needs UDP] --jump ACCEPT
iptables --append FORWARD --protocol udp --src [Server that needs UDP] --jump ACCEPT
iptables --append FORWARD --protocol udp --jump DROP
# Of course, if your policy is DROP, the last rule is implied

```I know this reeks of bad practice, but it's an idea...

---

