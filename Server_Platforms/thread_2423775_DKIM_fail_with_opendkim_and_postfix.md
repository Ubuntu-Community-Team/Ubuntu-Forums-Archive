---
title: "DKIM fail with opendkim and postfix"
date: 2019-07-29
forum: Server Platforms
---

### Post by antirix on 2019-07-29
-

---

### Post by SeijiSensei on 2019-07-29
I just implemented DKIM for a listserver I manage this past weekend. I used the "simple" example configuration file which has none of those various tables that seem so popular in the online documentation I read.  I wanted to sign messages from a single domain, let's call it example.com, and have an opendkim.conf file that looks like this:
```

# This is a simple config file for signing and verifying

LogWhy                  yes
Syslog                  yes
SyslogSuccess           yes

Canonicalization        relaxed/simple

Domain                 example.com
Selector                default
KeyFile                 /usr/local/etc/opendkim/keys/example.com/default.private

Socket                  inet:8891@localhost

ReportAddress           admin@example.com
SendReports             yes

## Hosts to sign email for - 127.0.0.1 is default
## See the OPERATION section of opendkim(8) for more information
#
# InternalHosts         192.168.0.0/16, 10.0.0.0/8, 172.16.0.0/12

## For secondary mailservers - indicates not to sign or verify messages
## from these hosts
#
# PeerList              X.X.X.X

PidFile         /var/run/opendkim/opendkim.pid
UserID          opendkim:opendkim

```
The only modification I made was to add the UserID directive.

I had problems delivering mail to places like yahoo.com before implementing this. I haven't had any problems since.

I decided to ignore online blogs about how to implement DKIM and instead relied on the README file that accompanies the opendkim source.  Since I built opendkim from source, it was in my /usr/local/src/opendkim-2.10.3/opendkim directory.

I use sendmail, not Postfix. The only change I needed to make to sendmail's configuration was to add the line 
```
INPUT_MAIL_FILTER(`opendkim', S=`inet:8891@localhost')dnl
```
to sendmail.mc and use m4 to create sendmail.cf.  From my reading of the material about Postfix, it shouldn't be much more difficult than that.  I chose to use a TCP socket implementation because it appeared using Unix sockets could be more problematic because of permission issues.

---

### Post by antirix on 2019-07-29
Finally solved it. Turns out it had nothing to do with opendkim, it was postfix. smtp_generic_maps. I was rewriting www-root@ to server@ and that was violating the From address validation.

---

### Post by SeijiSensei on 2019-07-29
I had a similar issue with messages where the domain part appended was host.domain.name rather than domain.name.

Glad you got it working!

---

