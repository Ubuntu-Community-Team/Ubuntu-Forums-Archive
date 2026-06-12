---
title: "dkim-filter problem - can't read SMFIC_OPTNEG reply packet header"
date: 2009-03-19
forum: Server Platforms
---

### Post by leonhongkong on 2009-03-19
Hi. I use ubuntu 8.10 server 64 bit + postfix + dkim-filter + dovecot
There is a problem with dkim-filter. I followed the instruction at [https://help.ubuntu.com/community/Postfix/dkim-milter](https://help.ubuntu.com/community/Postfix/dkim-milter)
Everything worked fine until I ran apt-get upgrade.

The dkim-filter didn't work. When I sent mail, syslog said
```
...
Mar 19 16:40:57 myubuntu postfix/smtpd[6166]:warning: milter inet:127.0.0.1:8891: can't read SMFIC_OPTNEG reply packet header: Connection timed out
Mar 19 16:40:57 myubuntu postfix/smtpd[6166]: warning: milter inet:127.0.0.1:8891:read error in initial handshake
...
```
The mail is sent successful but without dkim's header. Hotmail just send my mail directly to the junk folder :(



when I tried to restart dkim-filter the syslog said
```
...
Mar 19 06:31:18 myubuntu dkim-filter[14604]: can't configure DKIM library; continuing
Mar 19 06:31:18 myubuntu dkim-filter[14604]: Sendmail DKIM Filter v2.6.0 starting (args: -x /etc/dkim-filter.conf -p local)
...
```
After restarted dkim-filter. It ran normally but didn't work with postfix!?!


any idea to fix dkim-filter? 
Thanks.

---

### Post by leonhongkong on 2009-03-19
:(

---

### Post by Jayock on 2009-03-26
I get a similar error, everything is the same but it doesn't give the failed hand shake after the SMFIC error, it just dies and needs to be restarted.  

Did you get anywhere on this.

I am running fully up to date intrepid server x86_64 on 2x Quad Core Xeon server.

---

