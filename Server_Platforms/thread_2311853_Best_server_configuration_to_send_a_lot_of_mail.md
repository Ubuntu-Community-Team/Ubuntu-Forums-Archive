---
title: "Best server configuration to send a lot of mail"
date: 2016-01-30
forum: Server Platforms
---

### Post by WaelSan on 2016-01-30
Hello everyone,
I want to configure postfix to send a lot of mail (more than 5000) per day. I am using ubuntu server 14.04, so what's the best server configuration (I mean RAM, disk size etc ...)
Can anyone help me please.
Thank you.

---

### Post by nerdtron on 2016-01-30
Depends if your postfix server also has antivirus (clamAV) and Spam filtering (spam assassin), these can be heavy on resources especially when you send emails with attachments. If not, then a 2 CPU and 4GB and lots or disk space will be enough to send those mails.

More importantly though is to have a good reputation for your domain such as: Reversed DNS records, SPF records and Valid TLS/SSL certificate if you use it. This is because when you send a lot of emails (when blasting email notification like 1000 per hour), your domain can be blocked by other email servers due to sending too much, thus marking you as spam.

---

### Post by WaelSan on 2016-02-01
Thank you for your help ^^ .

---

