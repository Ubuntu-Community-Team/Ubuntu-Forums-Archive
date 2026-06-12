---
title: "Send mail through another service"
date: 2018-03-05
forum: Server Platforms
---

### Post by rackover on 2018-03-05
Hello,
I'm using a home server with Ubuntu16.04 running on a Rpi 3. 
As you probably know, most of the internet providers block the SMTP ports so you cannot send mails using a homemade server, for security reasons.
That's fine : but I still need to send mails with it, as part of an automated PHP subscription script. So I wondered if there was a way to create a @outlook.fr address, and to make my server use it as a relay instead.
That would help me a lot. I've tried with GMail and SASL authentification etc, but that didnt work out.

May anyone recommand a good approach to this problem ? I'm a bit lost.

Regards,

---

### Post by TheFu on 2018-03-05
Use a relay host.  Most ISPs provide one.  A business internet connection with a static IP shouldn't block any outbound ports.  DHCP public addresses are generally blocked by pretty much every SMTP server in the world as part of the anti-spam efforts.

There are also examples in these forums for setting up gmail as the FROM account.  I've never done that, but others do. That setup should work for your needs.

---

### Post by rackover on 2018-03-05
Thank you for your answer.
Can you link me one of the examples you're talking about ? Maybe simply setting a different From: might be enough.

---

### Post by TheFu on 2018-03-06
It isn't a "FROM:" problem.

---

### Post by mastablasta on 2018-03-06
if you only need to send email (e.g. information that certain script ran, information on hack attempt etc.) you can use ssmpt and gmail:
[https://wiki.debian.org/sSMTP](https://wiki.debian.org/sSMTP)

this basically uses Gmail to send e-mail. 
i suggest a separate gmail account to do this and i also suggest keeping the amount o sent emails to as little  as possible so that they do not identify the address as spam.

---

