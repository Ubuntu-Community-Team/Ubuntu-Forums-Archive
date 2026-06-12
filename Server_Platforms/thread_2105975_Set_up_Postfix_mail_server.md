---
title: "Set up Postfix mail server"
date: 2013-01-17
forum: Server Platforms
---

### Post by jdb91 on 2013-01-17
Hi all,
I've got an AWS server that I've pointed my domain at.  I have set up a webserver which runs fine, but would also like to be able to send / receive emails too.  I followed this guide:
[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)
but get this error when I try to send emails:

```
Delivery to the following recipient failed permanently:

     root@josephb.org

Technical details of permanent failure:
Google tried to deliver your message, but it was rejected by the recipient domain. We recommend contacting the other email provider for further information about the cause of this error. The error that the other server returned was: 554 554 5.7.1 <root@josephb.org>: Relay access denied (state 13).
```

If possible, i'd like all addresses to go into one box, that I can then IMAP.

---

### Post by aerokid240 on 2013-03-06
try sending from a different account, rather than root. Also, you should have an alias for the root account that delivers any messages destined for root, to a different local account.

---

