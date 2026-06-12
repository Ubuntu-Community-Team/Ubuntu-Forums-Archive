---
title: "maradns bug"
date: 2018-03-05
forum: Server Platforms
---

### Post by Loggy on 2018-03-05
I reported this on the github list but as maradns author says, it is a Debian issue and he doesn't have the resources to support that.  

As I am using Ubuntu 16.04 LTS, I can't use the Debian bug report system either.

MaraDNS is a very neat and powerful small footprint nameserver that will also handle TCP enquiries using maradns-zoneserver (which also needs to be started).  I have been using it on a CentOS platform for a number of years with no problem but when I mounted it on 16.04LTS, it refused to work - on 4 nameservers.

It turned out that there are two bugs in the maradns that stop it working properly:

1) When maradns chroots to its own user, it is no longer bound to port 53 as the lower ports are reserved for root.  Therefore it doesn't work at all. To get round this you need to install authbind and set /etc/authbind/byuid to a file named the uid (eg 102) and containing 0.0.0.0/53,53.

2) The tcp managing program maradns-zoneserver does not migrate to the maradns uid but to uid 99 which was the default maradns UID in earlier versions.

Can a moderator elevate this to a bug report?

TIA

---

### Post by cariboo on 2018-03-05
Bug reports are created at [https://bugs.launchpad.net](https://bugs.launchpad.net). To create a bug report, open a terminal and type:

```
ubuntu-bug maradns
```

**Note:** You need to have an account to create a bug report.

---

