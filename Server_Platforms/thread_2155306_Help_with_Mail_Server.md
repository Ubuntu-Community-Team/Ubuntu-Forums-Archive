---
title: "Help with Mail Server"
date: 2013-06-17
forum: Server Platforms
---

### Post by zankara on 2013-06-17
Hi there,

We have purchased a business and as part of that deal was given their email server (which is running Ubuntu [COLOR=#333333]Linux 8.04.3).

I have updated the IP settings since we changed service provider but no emails seem to be coming in.

The guy who set up the server left the below notes for the previous owners:
"The server uses fetchmail to receive email from pop servers, then strips the form header and pipes them straight back into SMTP server (Postfix) with the original form header."

Now this doesn't mean that much to me but from what I can tell Fetchmail is getting the emails as they are dissapearing from the website webmail.  

But I can't seem to get the emails from the server to the computer?

Any ideas?

Thanks[/COLOR]

---

### Post by ahallubuntu on 2013-06-17
~

---

### Post by Cheesemill on 2013-06-18
*Thread moved to **Server Platforms**.*

---

### Post by 3L33T on 2013-06-18
> **zankara said:**
> 
I have updated the IP settings since we changed service provider but no emails seem to be coming in.


Do you use some NAT or port-forwarding in youre firewall?  Check the rules in the router/firewall and perhaps you need to change that rule to forward to the *new IP* you assigned to the internal mail server.

> 
The guy who set up the server left the below notes for the previous owners:
"The server uses fetchmail to receive email from pop servers, then strips the form header and pipes them straight back into SMTP server (Postfix) with the original form header."

Now this doesn't mean that much to me but from what I can tell Fetchmail is getting the emails as they are dissapearing from the website webmail.  

But I can't seem to get the emails from the server to the computer?

Any ideas?

Thanks[/COLOR]


Did you try to restarting the Postfix service yet?  Do this:

> sudo /etc/init.d/postfix restart

And finally, have a look at the How-to-Configure-Postfix write-up [HERE]("https://help.ubuntu.com/community/Postfix") and compare your settings to the example in hopes that perhaps you missed a step?

---

### Post by SeijiSensei on 2013-06-18
As a guess, I bet fetchmail is retrieving the mail from your outside account, but the server has no SMTP server of its own like Postfix or sendmail to deliver the messages to the accounts on the server itself.  The messages are probably queued up on the server somewhere awaiting delivery.

Have you looked at any logs like /var/log/mail.log?

---

