---
title: "Ubuntu and Dovecot2"
date: 2014-02-05
forum: Server Platforms
---

### Post by kevinwincott2 on 2014-02-05
Im trying to get a "public" mailbox to collect generic emails like sales@, info@ etc, ive followed the guide on the Dovecot page, making sure I was following the wiki for Dovecot2 but I cant for the life of me getting it working. This is the relevant part of 10-mail.conf

```
namespace {
  type = public
  separator = /
  prefix = Public/
  location = maildir:/var/vmail/public
  subscriptions = yes
  inbox = no
}

plugin {
  acl = vfile
}
```

and the contents of public

```
root@server:/etc/dovecot/conf.d# ls -lah /var/vmail/public/
total 12K
drwxr-xr-x 2 vmail vmail 4.0K Feb  5 17:18 .
drwxr-xr-x 4 vmail vmail 4.0K Feb  5 17:28 ..
-rw-r--r-- 1 root  root    10 Feb  5 17:18 dovecot-acl
lrwxrwxrwx 1 root  root     9 Feb  5 17:12 info -> info/
```

and dovecot-acl:

```
anyone lr
```

When I connect via IMAP it doesnt find any folders under public to subscribe to

---

