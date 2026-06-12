---
title: "Setting up Postfix for SMTP"
date: 2008-08-27
forum: Server Platforms
---

### Post by HornedBeast on 2008-08-27
Hello,

I have done a basic install of Postfix on my Ubuntu Server 8.04. What I plan to achieve is a simple SMTP mail server (no need for incoming mail). It only needs to be able to be accessed via a local IP address (192.168.1.20) and doesn't even require authentication (as some of the software that needs to send mail to it to be sent can't handle authentication).

If anyone knows how to set this up or which files to take a look at to do this, that would be appreciated.

Thank-you kindly.

HB!

---

### Post by MJN on 2008-08-27
If you have access to an Internet SMTP server (e.g. your ISP's) then I suggest using Nullmailer instead - it simply acts as a relay for outgoing mail.
 
Mathew

---

### Post by HornedBeast on 2008-08-27
Sadly our ISP will not let us use their mail servers for the out going mail we wish to send.

Thank-you for your suggestion though, my OP should have been clearer!

Any other methods for setting up Postfix?

---

### Post by MJN on 2008-08-27
Ah okay.
 
Well Postfix will work - it's just a sledgehammer to crack a nut in this case but that's okay.
 
It should work out of the box for you, although you may need to add your local subnet to the mynetworks directive (e.g. 192.168.0.0/16) in order that your local clients are trusted enough to relay outgoing mail.
 
Mathew

---

### Post by de0xyrib0se on 2008-08-27
If you plan this server to send outgoing e-mail to the "world" you have to be aware there are tons of spam protection rules on every server out there such as reverse DNS lookups and many many more that would send your e-mails to junk and spam folders, its a lot of work, i would suggest using a third party.

---

### Post by kustomjs on 2008-08-27
just use google.com/a that is what I am using I got 7.7 gb of email  space and try to configure how to get a relay you can use for google aka gmail settings because that what I am trying to figure out right now.

---

