---
title: "Postfix"
date: 2009-04-24
forum: Server Platforms
---

### Post by PJDouglas on 2009-04-24
Hi,

I've just installed postfix and need to know how to rewrite the sender domain / address for all outbound mail.

Basically, I'am using postfix to rewrite the sender address before all mail is sent to a smarthost.

I'm new to ubuntu and would appreciate any help.

I've edited the main.cf file and configured the smarthost but not sure what the correct command is to use to rewrite the domain sender / return address.

Ive entered the command - Rewrite "user" to "user@$myorigin in the main.cf and restart postfix and get an error saying that the '=' is missing.

Myorigin in main.cf reads - myorigin = pjdouglas.co.uk
This is the domain name I want all outbound mail to show as the sender address.

Is this the correct command for rewriting the domain name and is the syntax correct?

Would appreciate it if anyone could tell me ehat the correct syntax / command is for rewiting the sender address to pjdouglas.co.uk for all outbound mail.

Many Thanks


Paul.

---

### Post by dipeshmehta on 2009-04-24
please read: [http://www.postfix.org/ADDRESS_REWRITING_README.html](http://www.postfix.org/ADDRESS_REWRITING_README.html) for details about rewriting.

moreover, I do not understand what exactly you want to rewrite, you may be in search of [http://www.postfix.org/postconf.5.html#smtp_generic_maps](http://www.postfix.org/postconf.5.html#smtp_generic_maps)

hope this helps.

Dipesh

---

### Post by PJDouglas on 2009-04-27
> **dipeshmehta said:**
> please read: [http://www.postfix.org/ADDRESS_REWRITING_README.html](http://www.postfix.org/ADDRESS_REWRITING_README.html) for details about rewriting.

moreover, I do not understand what exactly you want to rewrite, you may be in search of [http://www.postfix.org/postconf.5.html#smtp_generic_maps](http://www.postfix.org/postconf.5.html#smtp_generic_maps)

hope this helps.

Dipesh


Thanks Dipesh,

I have read the article but seem to be getting the syntax wrong.

Basically all emails forwarded to postfix will have a sender address of 'xxxx@domain.com'.

All emails that postfix receives I need to rewrite the sender address to 'xxxx@ pjdouglas.co.uk' before it forwards the mail to the smarthost.

Our version of exchange does not allow us to rewrite the sender address which is what I need postfix for.

Mail we are sending to a secure domain down a private link has to have a sender address of '@pjdouglas.co.uk'.

I have setup a smtp connector in exchange to forwarded all mail for the secure domain to postfix for the address rewrite to take place before it is forwarded to the smarthost.

Hope this makes sense???

Thanks for your help.


Paul.

---

### Post by dipeshmehta on 2009-04-27
You may use domain.com as myorigin into postfix's main.cf, and use generic maps to rewrite the address.  This way mail from [email]user1@domain.com[/email] would be forwarded as [email]user1@pjdouglas.co.uk[/email]

---

### Post by PJDouglas on 2009-04-28
> **dipeshmehta said:**
> You may use domain.com as myorigin into postfix's main.cf, and use generic maps to rewrite the address.  This way mail from [EMAIL="user1@domain.com"]user1@domain.com[/EMAIL] would be forwarded as [EMAIL="user1@pjdouglas.co.uk"]user1@pjdouglas.co.uk[/EMAIL]


Thanks dipeshmehta,

I have used the following command to rewrite the address,

remote_header_rewrite_domain = pjdouglas.co.uk

Would this be the correct syntax?

Also, I need to accept mail from say host 192.168.1.1. What is the correct command to accept relaying from this host?

Thanks for your help.


Paul.

---

