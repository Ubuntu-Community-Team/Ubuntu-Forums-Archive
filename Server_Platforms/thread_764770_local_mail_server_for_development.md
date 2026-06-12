---
title: "local mail server for development"
date: 2008-04-24
forum: Server Platforms
---

### Post by r557 on 2008-04-24
I have an Ubuntu 7.10 development server for web development.  I would like to be able to set up a mail server for testing purposes only.  The mail server doesn't need to accept message outside of my own LAN.  

I'm looking for more of a how-to on this issue.  Not sure where to start.

---

### Post by Monicker on 2008-04-24
> **r557 said:**
> I have an Ubuntu 7.10 development server for web development.  I would like to be able to set up a mail server for testing purposes only.  The mail server doesn't need to accept message outside of my own LAN.  

I'm looking for more of a how-to on this issue.  Not sure where to start.


Postfix is a great email server:  [http://doc.ubuntu.com/ubuntu/serverguide/C/postfix.html]("http://doc.ubuntu.com/ubuntu/serverguide/C/postfix.html")

One thing you did not mention is how people will be retrieving their email from this server.  Pop3? Imap? Directly from user accounts on the mail server itself?

---

### Post by r557 on 2008-04-24
> **Monicker said:**
> Postfix is a great email server:  [http://doc.ubuntu.com/ubuntu/serverguide/C/postfix.html]("http://doc.ubuntu.com/ubuntu/serverguide/C/postfix.html")

One thing you did not mention is how people will be retrieving their email from this server.  Pop3? Imap? Directly from user accounts on the mail server itself?

Thanks Monicker.  In terms of how many people etc. will be checking the email, it's really only me.  Just want an area that for each site i'm working on i can set up like 5-10 email accounts.  It's main purpose is for development, so i can verify that my applications are sending the notifications properly.  It is not intended to be used as any sort of corporate email system.  In terms of Pop3 or Imap, i assume it would be POP3.

---

### Post by Monicker on 2008-04-24
> **r557 said:**
> Thanks Monicker.  In terms of how many people etc. will be checking the email, it's really only me.  Just want an area that for each site i'm working on i can set up like 5-10 email accounts.  It's main purpose is for development, so i can verify that my applications are sending the notifications properly.  It is not intended to be used as any sort of corporate email system.  In terms of Pop3 or Imap, i assume it would be POP3.


Qpopper would be a good choice then.  Detail can be found here: [http://www.eudora.com/products/unsupported/qpopper/index.html]("http://www.eudora.com/products/unsupported/qpopper/index.html")

---

### Post by Ububum on 2009-12-15
i was wondering how well this worked for you. I to wanna do something similar to this. I am installing postfix on ubuntu server, at the postfix configuration do i choose:

No configuration
Internet site
internet with smarthost
satellite system
local only

i am guessing local only however, there is no network with this option, i want to be able to send email to other computers in the local network

---

