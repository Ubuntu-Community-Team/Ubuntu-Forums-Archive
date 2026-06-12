---
title: "Dovecot setting problem"
date: 2010-03-20
forum: Server Platforms
---

### Post by neopage on 2010-03-20
Hey guys, I am setting up a new mail server with Ubuntu Server Edition 9.10.
I am using postfix and dovecot. I followed the instruction on how to set up
postfix and dovecot from help.ubuntu.com

If I test this new email system with Alpine, I am receiving email fine. But I cannot
view email by using email client. I am using Thunderbird. I also tried with gmail
and it does not work. I guess something's wrong with my dovecot setting.

I followed the following instruction.

[https://help.ubuntu.com/community/Dovecot](https://help.ubuntu.com/community/Dovecot)

My Dovecot.conf is setup like the above link.

protocols = pop3 pop3s imap imaps

I left this line like this to use all four protocols. 

telnet localhost pop3 and telnet localhost imap2 both giving me OK message.

Also I don't have problem with sending email from Thunderbird but I guess this is handled by postfix.

Any advice for me?



Additionally, I found out that if I tried to send an email to this new email server by using Thunderbird,
I am getting 5.1.1 User Unknown error. Sending an email to this new email server by using gmail is working fine though.

---

