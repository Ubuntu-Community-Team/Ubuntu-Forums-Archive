---
title: "Local Mail Delivery?"
date: 2008-09-21
forum: Server Platforms
---

### Post by trmentry on 2008-09-21
I just setup a Hardy 8.04.1 server.  During install I just installed OpenSSH.

'root' isn't getting any mail from cron or other daemons that I would expect.  

My guess is that there isn't a local mail delivery program on the server.

My goal is to have local mail delivery for root, etc.  But to also allow daemons to send out to the net as well.  However this server will not accept incoming connections.  I just want it to smtp.  DOes it need to be a smart host and send to say smtp servers at google using my gmail account?

Any suggestions?

Thanks

---

### Post by 1/0 on 2008-09-21
[Postfix](http://flurdy.com/docs/postfix/)?

---

### Post by cariboo on 2008-09-21
Usually when setting up the server exim4 gets installed by default when using the lamp script.

Jim

---

### Post by trmentry on 2008-09-21
> **cariboo907 said:**
> Usually when setting up the server exim4 gets installed by default when using the lamp script.

Jim

I did the LAMP thing but no exim or any other mailer on here.

#1/0
I know I can put on Postfix but was thinking that was complete overkill.  Not sure though.

---

