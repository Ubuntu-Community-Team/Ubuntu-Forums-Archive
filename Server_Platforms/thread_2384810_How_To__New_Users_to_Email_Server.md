---
title: "How To:  New Users to Email Server"
date: 2018-02-12
forum: Server Platforms
---

### Post by rduhb on 2018-02-12
So, looks like I've got the server configured and ready to go, (which was not too easy).  Still doing some testing and learning, but in the meantime, can someone tell me how do I add new email user accounts (e.g., [email]John@mystore.com[/email], [email]Jane@mystore.com[/email], and so on.)?  I'm using Postfix and Dovecot.  Thanks in advance!!!!

---

### Post by TheFu on 2018-02-12
How depends on where the users are stored.
* normal password DB
* LDAP
* mysql
* postgres
* some other database
I've only used the normal password method with dovecot and that was last in 2008 - create userids in the normal way and they can use postfix over port 25/tcp  and dovecot over the IMAP/IMAPS port(s).

There are lots and lots of caveats about having an email server as we try to fight against spammers. It wasn't always this way.  Must have a static IP. IP can't be on DHCP (home) public networks. IP can't be from a former spammer.  Many VPS IPs are on spam block lists, so it is best to check that before doing much work.  Get a new IP from the provider.  Setup DNS with MX records and both forward and reverse DNS need to match.  Those are the minimums.  To get email more accepted, then adding SPF TXT DNS records and DKIM TXT DNS records helps.

So ... as you can see, explaining all the details here really isn't possible.  You are probably better off searching for "Perfect Server" and following a guide at HowToForge.  Or perhaps the Ubuntu Server Guide explains? [https://help.ubuntu.com/lts/serverguide/email-services.html](https://help.ubuntu.com/lts/serverguide/email-services.html)

---

### Post by rduhb on 2018-02-12
> **TheFu said:**
> How depends on where the users are stored.
* normal password DB
* LDAP
* mysql
* postgres
* some other database
I've only used the normal password method with dovecot and that was last in 2008 - create userids in the normal way and they can use postfix over port 25/tcp  and dovecot over the IMAP/IMAPS ...............................................   


Thanks for the feedback.  I'm totally new at this so you may have to dumb it down a bit for me.  Lets assume I go the normal password DB route.  I still don't understand how to create an email account for a new user.  What are the command lines?  I've been researching online but no luck yet.  The link you provided talked about setting up the server and didn't really address the mail account setup.  Thanks again for your help!!

---

### Post by TheFu on 2018-02-12
There is nothing special about an email account. Make a new userid on the system in the normal way. That provides an email account for each user.

However, I'm concerned.  Running an email server is one of the more advanced administration skills. An incorrectly configured email server can easily be pwned. Running an email server is "the deep end" of the admin pool.

---

### Post by rduhb on 2018-02-12
Thanks for your help.

---

