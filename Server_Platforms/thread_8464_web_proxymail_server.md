---
title: "web proxy/mail server?"
date: 2004-12-17
forum: Server Platforms
---

### Post by Scythe on 2004-12-17
I'm new to linux and am looking to utilize it to help manage my home network.  The two things that I'd really like to accomplish are:

1) proxy server - a central machine that all other machines on my home network connect to the internet through.  This machine should also be able to restrict access to sites of my choosing and also inform me of what sites are being visited (as a parent I want to be aware of my children's travels in the WWW)

2) mail server - a central machine that retrieves email from the email account offered by the ISP (with aliases for each family member) and that all other machines on my home network connect to to manage their email.  Ideally I'd like it to be able to provide other family members to have only access to emails written to *their* alias (and again, as a parent I want to be aware of my children's correspondence in the WWW)

Are these two things possible, and if so, how do I set this up in Ubuntu?  I appologize in advance that I'm a linux noob and may ask a few questions for clarification.  Thanks in advance!

---

### Post by jdong on 2004-12-18
Ok, moving to the Server forum...

The FAQ/Howto forum is for people posting how-to guides, not for questions :)

---

### Post by jdong on 2004-12-18
These are all possible. You can find plenty of guides online for these programs.

1. You want to use **squid** for this. Squid also has many 'log parsers' that can show you who's accessing what.

2. I'm no mail expert, but it seems like a **fetchmail** based solution.

I'll leave it to someone else to elaborate.

---

### Post by gkhewitt on 2004-12-19
[QUOTE=Scythe]

1) proxy server - a central machine that all other machines on my home network connect to the internet through.  This machine should also be able to restrict access to sites of my choosing and also inform me of what sites are being visited (as a parent I want to be aware of my children's travels in the WWW)

[/quote]

[Squid](http://www.squid-cache.org)  is your friend. The restriction stuff can be done using [dansguardian](http://dansguardian.org/) 

> 
2) mail server - a central machine that retrieves email from the email account offered by the ISP (with aliases for each family member) and that all other machines on my home network connect to to manage their email.  Ideally I'd like it to be able to provide other family members to have only access to emails written to *their* alias (and again, as a parent I want to be aware of my children's correspondence in the WWW)


[Postfix](http://www.postfix.org) and an appropraite POP server sounds good for you. Postfix will take the user accounts and have a mailbox for each one. You can then use software such as [Fetchmail](http://catb.org/~esr/fetchmail/)  that will download mail messages from your ISP and then dump them in the appropriate mailbox

For all of this, [Webmin](http://www.webmin.com) is undoubtably your bestest friend, for administering all this in a more graphical way.

However... if this box is going to be dedicated, and not used for desktop purposes, I would STRONGLY suggest going for a dedicated server distro of Linux. I use and heartily recommend [ClarkConnect](http://www.clarkconnect.org/index.php). Use the current Home 2.2 version, it has automatic setup of all of the above that you want to use, and then has a very nice and straightforward web interface to change settings, add accounts and so on.

I hope this helps.

---

### Post by Scythe on 2004-12-20
Thanks for the information!  I think I'll be spending a bit of time figuring out the Postfix/Fetchmail deal over the holidays because my wife and I share one email account with two aliases so there's an immediate benefit.  The Squid will be looked into in time because my 8 month old daughter has a bit of time to go before she's ready for the Internet.   :-)

---

### Post by socrazy143 on 2004-12-24
I agree with Squid for the proxy server and Dansguardian is good as well.  The dude at PublicIP.net uses Dansguardian for their wireless captive portal CD.

For the mail system you might be better served to check out [http://www.qmailrocks.org](http://www.qmailrocks.org).  This guy has a step-by-step setup of qmail with spam guards and the whole nine yards.  You download all software and patches from his site during the install.  It is worth a look.  I was impressed.

---

