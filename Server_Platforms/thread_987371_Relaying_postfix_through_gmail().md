---
title: "Relaying postfix through gmail(?)"
date: 2008-11-19
forum: Server Platforms
---

### Post by Phases on 2008-11-19
8.04 Server

Hey guys. I've been working on getting this email server set up right for a couple days now.

It sends and receives mail fine from CLI. However, my work email and (as I just figured out) yahoo block my emails because my IP's in a residential block.

So, I tried using my gmail account to relay the mail. It works, a little slow, but it works. However, it shows all the emails as coming FROM the gmail account. I was hoping it would still show [email]phases@superstickphase.com[/email] in the from field. 

Is there anything (short of buying a business account with comcast) I can do to get my emails to make it to everyone, as [email]phases@superstickphase.com[/email]?

Thanks for any advice.

---

### Post by amauk on 2008-11-19
I think you can specify alternative <From> addresses by editing your gmail settings

Login to gmail web interface, then
Settings->Accounts->Add another email address

---

### Post by cdenley on 2008-11-19
Are you sure that is the reason your mail is being blocked? What response is their e-mail server giving you?
[http://www.yuki-onna.co.uk/email/smtp.html](http://www.yuki-onna.co.uk/email/smtp.html)

---

### Post by amauk on 2008-11-19
no, I've seen this quite a bit
ISP's tend to block SMTP traffic from known residential IP's
(anti-spam mechanism)

---

### Post by Phases on 2008-11-19
It is the case, yes. Most residential blocks are on the spamhaus PBL list, which many places choose to block from.

I looked into the gmail thing but didn't want ALL my gmail stuff to go out as that, so I was going to create a second one. Then, I hit up google with a thought. And it worked.

Believe it or not, and this amazes me, comcast provides a seperate port you can use instead of 25 to send through - to not be blacklisted. No need to upgrade to a business account - free of charge! 

So I set that up right quick as a regular relay and bam, tested and works with both yahoo and my work account - and shows it as [email]phases@superstickphase.com[/email]! 

Thanks for your time guys, problem resolved.

[http://www.spamhaus.org/pbl/query/PBL191932](http://www.spamhaus.org/pbl/query/PBL191932)  (that's me being blocked)
[http://www.nabble.com/postfix-and-sasl-td19071215.html](http://www.nabble.com/postfix-and-sasl-td19071215.html) (that's the post I found that resolved it)

---

