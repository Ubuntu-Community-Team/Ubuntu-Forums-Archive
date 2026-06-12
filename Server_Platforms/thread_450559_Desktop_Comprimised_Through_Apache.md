---
title: "Desktop Comprimised Through Apache?"
date: 2007-05-21
forum: Server Platforms
---

### Post by technick on 2007-05-21
I've been running a small wiki (dokuwiki) off of my desktop machine using apache2 and I believe it has been hacked over the weekend. I don't know how it happened, if anyone can shed some light on the subject, I would appreciate it.

The Setup

I have a static IP from my ISP and a IPCOP router. The only port visible to the outside world is port 80 which is mapped directly to my machine (I know, probably mistake #1)

The Desktop

Fiesty (Kubuntu)

Machine is pretty stock with the exception of Apache2, PHP and MySQL. Root account was enabled (probably mistake #2).

This morning I noticed a strange directory in my home directory called "h????C???". I couldn't view anything in it and it had a strange time
stamp of 5/20/07 (I have been out of town since the 16th). Digging into my history file I found the following (after booting into knoppix found lots of stuff in the history that I couldn't see while booted into KDE)

```
PROMPT_COMMAND='pwd>&7;kill -STOP $$'
 cd "`echo -e '\0057home\0057nick\0057\0056config'`"
 cd "`echo -e '\0057home\0057nick\0057\0056config\0057xfce\0064\0055session'`"
 cd "`echo -e '\0057home\0057nick\0057\0056config'`"
 cd "`echo -e '\0057home\0057nick\0057\0056config\0057xfce\0064'`"
 cd "`echo -e '\0057home\0057nick\0057\0056config\0057xfce\0064\0057mcs\0137settings'`"
 cd "`echo -e '\0057home\0057nick\0057\0056config\0057xfce\0064'`"
 cd "`echo -e '\0057home\0057nick\0057\0056config\0057xfce\0064\0057panel'`"
 cd "`echo -e '\0057home\0057nick\0057\0056config\0057xfce\0064'`"
 cd "`echo -e '\0057home\0057nick\0057\0056config\0057xfce\0064\0057mcs\0137settings'`"
 cd "`echo -e '\0057home\0057nick\0057\0056config\0057xfce\0064'`"
 cd "`echo -e '\0057home\0057nick\0057\0056config\0057xfce\0064\0057mcs\0137settings'`"
 cd "`echo -e '\0057home\0057nick\0057\0056config\0057xfce\0064'`"
 cd "`echo -e '\0057home\0057nick\0057\0056config'`"
 cd "`echo -e '\0057home\0057nick\0057\0056config\0057gtk\0055\0062\0056\0060'`"
 cd "`echo -e '\0057home\0057nick\0057\0056config'`"
 cd "`echo -e '\0057home\0057nick\0057\0056config\0057Thunar'`"
 cd "`echo -e '\0057home\0057nick\0057\0056config'`"
 cd "`echo -e '\0057home\0057nick'`"
 cd "`echo -e '\0057home\0057nick\0057\0056easytag'`"
 cd "`echo -e '\0057home\0057nick'`"
 cd "`echo -e '\0057home\0057nick\0057\0056gconf'`"
 cd "`echo -e '\0057home\0057nick\0057\0056gconf\0057apps'`"
 cd "`echo -e '\0057home\0057nick\0057\0056gconf'`"
 cd "`echo -e '\0057home\0057nick\0057\0056gconf\0057desktop'`"

```

Apache2 Mods Enabled

```

knoppix@Knoppix:/media/hdb3/etc/apache2/mods-enabled$ ls
alias.load            authz_host.load  dir.load          php5.load
auth_basic.load       authz_user.load  env.load          rewrite.load
authn_file.load       autoindex.load   mime.load         setenvif.load
authz_default.load    cgi.load         negotiation.load
authz_groupfile.load  dir.conf         php5.conf

```

Attached is a copy of my apache.conf file. 

The log files in /var/log/apache2/error.log shows only one wierd entry, I assume that those have been wiped already.

```

[Tue May 15 19:01:44 2007] [error] [client 213.190.152.147] client sent HTTP/1.1
 request without hostname (see RFC2616 section 14.23): /w00tw00t.at.ISC.SANS.DFind:)
[Sun May 20 07:35:48 2007] [notice] caught SIGTERM, shutting down

```

Thanks in advance, this is going to drive me up a wall until I figure out how this happened through apache.

---

### Post by elst on 2007-05-21
Were you running PHPMyAdmin on this system?

---

### Post by technick on 2007-05-21
yup it was installed

---

### Post by elst on 2007-05-21
That might be the explanation, then - PHPMyAdmin has had vulnerabilities that have been actively exploited. I've seen the w00t message and probes for PHPMyAdmin in my own server logs a couple of times.

---

