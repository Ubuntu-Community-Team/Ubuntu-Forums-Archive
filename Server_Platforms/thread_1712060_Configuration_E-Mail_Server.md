---
title: "Configuration E-Mail Server"
date: 2011-03-22
forum: Server Platforms
---

### Post by MindController on 2011-03-22
Hi All,

I have one question about email server. I have one local mail server hosted in Mdaemon in my office and ip is 192.168.10.2. My clients can't use the email from the outside. If they want to use the mail, they need to come to office. I want them to use from the outside. How can i set up the mail server. Do i need to host the server on the hosting? I want to synchronize with my local mail server. I don't have the public IP BTW.

---

### Post by falko on 2011-03-22
> I don't have the public IP BTW.You must have a public IP because otherwise you wouldn't be connected to the Internet.

You must configure your router to forward port 25 (SMTP) plus 110 (POP3) and 143 (IMAP) (maybe also 993 (IMAPS) and 995 (POP3S) if your users use these services) to your mail server.

---

### Post by MindController on 2011-03-22
nah........ in our country we can't get the public. If need to surf we use the NAT. That's why I ask do i need to buy hosting or not.
Anyway thanks for the answer

---

