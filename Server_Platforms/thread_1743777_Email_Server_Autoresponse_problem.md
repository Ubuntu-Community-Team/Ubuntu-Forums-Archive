---
title: "Email Server Autoresponse problem"
date: 2011-04-29
forum: Server Platforms
---

### Post by rule-of-three on 2011-04-29
Hi,

I have a problem with Email Server made with this manual:
[http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu-10.04](http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu-10.04)

I am installed this for Autoreply:
[http://www.howtoforge.com/autoresponders_for_virtual_postfix_users](http://www.howtoforge.com/autoresponders_for_virtual_postfix_users)

In error log we can se possible issue with Yaa! connect to MySQL fails:

```

Apr 28 08:56:03 alm postfix/virtual[18270]: 3D6D72147BE: to=<xxxx.xxxx@i4ware.fi>, relay=virtual, delay=0.17, delays=0.08/0.01/0/0.08, dsn=2.0.0, status=sent (delivered to maildir)
Apr 28 08:56:03 alm yaa.pl[18272]: Warning: setting empty lookup query order for attribute 'subject'.
Apr 28 08:56:03 alm yaa.pl[18272]: Warning: setting empty lookup query order for attribute 'forward'.
Apr 28 08:56:03 alm yaa.pl[18272]: Warning: setting empty lookup query order for attribute 'active'.
Apr 28 08:56:03 alm yaa.pl[18272]: Warning: setting empty lookup query order for attribute 'charset'.
Apr 28 08:56:03 alm yaa.pl[18272]: Warning: setting empty lookup query order for attribute 'message'.
Apr 28 08:56:03 alm yaa.pl[18272]: Warning: setting empty lookup query order for attribute 'rewrite_recipient'.
Apr 28 08:56:03 alm yaa.pl[18272]: Warning: setting empty lookup query order for attribute 'rewrite_sender'.
Apr 28 08:56:03 alm yaa.pl[18272]: Warning: setting empty lookup query order for attribute 'local_domains'.
Apr 28 08:56:03 alm yaa.pl[18272]: 1621570: Processing new request, id 1621570
Apr 28 08:56:03 alm yaa.pl[18272]: 1621570: Warning: Your MTA does not provide Delivered-To header. Yaa will have to rely on message headers which are very easy to fake. You've been warned.
Apr 28 08:56:03 alm yaa.pl[18272]: 1621570: Warning: Your MTA violates RFC 822 by not adding Return-Path header in message. Yaa will have to rely on message headers which are very easy to fake. You've been warned.
Apr 28 08:56:03 alm yaa.pl[18272]: 1621570: Message sender: , recipients: matti.kiviharju@i4ware.fi
Apr 28 08:56:03 alm yaa.pl[18272]: 1621570: Autoresponse will not be sent to empty or undefined sender address.
Apr 28 08:56:03 alm postfix/pipe[18271]: 3D6D72147BE: to=<xxxxx.xxxx@autoreply.i4ware.fi>, orig_to=<xxxxx.xxxx@i4ware.fi>, relay=yaa, delay=0.2, delays=0.08/0.01/0/0.12, dsn=2.0.0, status=sent (delivered via yaa service)
Apr 28 08:56:03 alm postfix/qmgr[14577]: 3D6D72147BE: removed

```How to fix this? Any ideas?

---

### Post by falko on 2011-04-30
Do you use the correct MySQL settings in yaa.conf?

---

### Post by rule-of-three on 2011-05-08
> **falko said:**
> Do you use the correct MySQL settings in yaa.conf?

I am not sure.

What I have to do you can answer is settings correct?

---

### Post by rule-of-three on 2011-05-10
Anyone can help me on this?

---

### Post by lisati on 2011-05-10
My first thought is that the table for the autoresponder is empty. With the applications I've used that use MySql databases, there has usually been an installation script somewhere that creates the tables within the database.

---

### Post by rule-of-three on 2011-05-10
> **lisati said:**
> My first thought is that the table for the autoresponder is empty. With the applications I've used that use MySql databases, there has usually been an installation script somewhere that creates the tables within the database.

autoresponder table is not empty

---

