---
title: "is there anyway that I can extracting smtp traffic from logs"
date: 2009-05-20
forum: Server Platforms
---

### Post by kustomjs on 2009-05-20
Hi Guys
I am just wondering if there is anyway that I could extracting smtp traffic from logs?  because my setup is with postfix+dovecot+mysql?

---

### Post by kustomjs on 2009-05-20
here is what I want to do:

outbound
May 20 22:13:37 mail sm-mta[47291]: n4L2DaNl047291 from=<xxxxx@domain.net>, size=1370, class=0, nrcpts=1, msgid=<E2E640AC5BCD49DF8FC380DFAE2F4670@xxxxx>, proto=SMTP, daemon=IPv4, relay=xxx.xxx.xxx.xxx[xxx.xxx.xxx.xxx]

incoming
May 20 00:32:47 mail sm-mta[49233]: n4K4Wkeg049233 from=<1-8100100-domain.net?xxxxx@mxx.xxx.com>, size=0, class=0, nrcpts=1, proto=SMTP, daemon=IPv4, relay=xxxxx1.xxxxxx.com [xx.xx.x.xxx]

dovecot pop3/imap
May 20 22:10:00 mail dovecot: POP3(xxxx): Disconnected: Logged out top=0/0, retr=0/0, del=0/0, size=0


is there anyway I can do this?

---

### Post by kustomjs on 2009-05-21
any help here please.

---

### Post by kustomjs on 2009-05-26
any help here?

---

### Post by kustomjs on 2009-05-31
over 65 views and still no help?

---

### Post by gombadi on 2009-05-31
> **kustomjs said:**
> Hi Guys
I am just wondering if there is anyway that I could extracting smtp traffic from logs?  because my setup is with postfix+dovecot+mysql?

Myself and the other people who have seen this thread have all been asking ourselves - what?

What do you mean by extracting smtp traffic from logs?  The next post you showed us some log entries. What are you trying to extract? The actual email messages, the number of messages, from who and to who etc?


If no one replies then it is a good bet that they don't know what you want so instead of bumping the thread it is a good ides to explain more about what you want or to describe the problem in a different way.

---

### Post by rehilliard on 2009-05-31
[http://www.onlamp.com/pub/a/onlamp/2004/01/22/postfix.html](http://www.onlamp.com/pub/a/onlamp/2004/01/22/postfix.html)

---

### Post by kustomjs on 2009-05-31
ok gombadi in my previous reply I wanted to do this:
here is what I want to do:

outbound
May 20 22:13:37 mail sm-mta[47291]: n4L2DaNl047291 from=<xxxxx@domain.net>, size=1370, class=0, nrcpts=1, msgid=<E2E640AC5BCD49DF8FC380DFAE2F4670@xxxxx>, proto=SMTP, daemon=IPv4, relay=xxx.xxx.xxx.xxx[xxx.xxx.xxx.xxx]

incoming
May 20 00:32:47 mail sm-mta[49233]: n4K4Wkeg049233 from=<1-8100100-domain.net?xxxxx@mxx.xxx.com>, size=0, class=0, nrcpts=1, proto=SMTP, daemon=IPv4, relay=xxxxx1.xxxxxx.com [xx.xx.x.xxx]

dovecot pop3/imap
May 20 22:10:00 mail dovecot: POP3(xxxx): Disconnected: Logged out top=0/0, retr=0/0, del=0/0, size=0


I want to be able to make a log on per user onto a viewable web page is that possible to do?


also I explained what I wanted to do.


> **gombadi said:**
> Myself and the other people who have seen this thread have all been asking ourselves - what?

What do you mean by extracting smtp traffic from logs?  The next post you showed us some log entries. What are you trying to extract? The actual email messages, the number of messages, from who and to who etc?


If no one replies then it is a good bet that they don't know what you want so instead of bumping the thread it is a good ides to explain more about what you want or to describe the problem in a different way.

---

### Post by grantemsley on 2009-06-01
Even after reading that, I still have no idea what you are trying to do.

Pretend you haven't told us anything yet, and explain in detail, step by step, what you are trying to do, and there are plenty of people here who will be glad to help.  We just don't understand what you are asking for.

Is english your native language?  Perhaps there is a language barrier here?

---

### Post by kustomjs on 2009-06-01
ok I want to do is use the mail log per email user like a page for dovecot then a page for incoming and outgoing?

---

### Post by grantemsley on 2009-06-02
> **kustomjs said:**
> ok I want to do is use the mail log per email user like a page for dovecot then a page for incoming and outgoing?

You want a page that shows users the mail logs related to just their email?

---

### Post by kustomjs on 2009-06-03
yes is that possible?

---

### Post by kustomjs on 2009-06-05
any ideas how I would put the data into a database then to the page?

---

### Post by iponeverything on 2009-06-05
I have to admit that looked you original post post and didn't really know what you wanted to do.

I think that you just want to parse a log or logs (you don't specify) and have the data viewable via a web page. -- If that is the case, its pretty basic and there 7 ways from Sunday to do it. off hand -

- use php to parse on the fly
- use cron to run grep to parse and redirect the output to a file in /var/www/

Using php and mysql is also pretty.

---

### Post by kustomjs on 2009-06-05
could anybody show me what parse would look like? and how would I setup the cron job? and I wanted to put the logs into database by mysql and use php to view the logs on a private page.

---

