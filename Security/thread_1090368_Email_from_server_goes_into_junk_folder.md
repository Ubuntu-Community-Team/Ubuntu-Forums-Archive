---
title: "Email from server goes into junk folder"
date: 2009-03-08
forum: Security
---

### Post by divinequran on 2009-03-08
hi,
email from my server goes into junk mail folder for yahoo/hotmail/gmail. what would be the issue? the user does not make the domain as a spam user but sill they send the mails to spam box.

---

### Post by hyper_ch on 2009-03-08
got a dedicated IP address? check the email headers for clues as to why they end in the spam folder.

---

### Post by cariboo on 2009-03-08
Most email services do a reverse dns lookup, it they don't find the ip address in the database, the message is marked as spam/junk. Do as hyper_ch suggested and get a static ip address.

Jim

---

### Post by hyper_ch on 2009-03-08
or relay through your ISP

---

### Post by The Tronyx on 2009-03-09
Hello,

You could look into implementing SPF records.  Many services check SPF records as well as rDNS records as one individual noted previously.

---

### Post by divinequran on 2009-03-09
Thank i have added MX record in my DNS, What is SPF record?

---

### Post by hyper_ch on 2009-03-10
> **divinequran said:**
> What is SPF record?
[http://tinyurl.com/cq9lug](http://tinyurl.com/cq9lug)

---

