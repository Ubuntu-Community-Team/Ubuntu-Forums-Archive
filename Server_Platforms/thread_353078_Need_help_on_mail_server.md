---
title: "Need help on mail server"
date: 2007-02-04
forum: Server Platforms
---

### Post by katiad on 2007-02-04
Been reading stuff on mail servers, and I'm getting more confused the more I do, so I thought that perhaps I oughta outline what I want to do, and see if anyone can point me in the right direction. 

I'm not looking to have a full fledged mail server. I have hosting services that are up 24/7 whereas my computer is not, and I have several accounts that I need to keep track of. Setting up a server with a domain, etc. etc. is not the goal here.

[LIST=1]
[*]I have several pop accounts from different places.
[*]I'd like them all stored on my local machine permanently. I would really prefer that my messages ultimately be stored in MH or some similar format, where each message is an individual file in a folder. I have ten billion messages, and I've learned the hard way that corruption of a large mail file really sucks.
[*]I'd prefer to be able to use any mail client to read these messages - from mutt over ssh to sylpheed. (imap?) 
[*]I want to run these messages through a good spam filter, because the ones on my isp and other accounts mostly suck.
[*]I need be able to send email and reply to emails from each of these accounts separately and transparently. Unfortunately, not one of my accounts will allow email from another domain to be sent through their smtp servers, so setting up a single account's smtp server to do the job for all of them is not possible. I'd guess I'd need my own smtp server... In the same vein, I need to ensure that the reply-to addresses are correct. This is where I've run into problems - haven't found much yet explaining it, and I'm not sure it's even possible.
[*]I need to sort these messages out according to to/from headers so I don't have ten billion messages dumped into the same folder needing hand-sorting.
[*]Some sort of web-accessible interface would also be lovely, if at all possible. I don't care to attach a domain to the box, but I do have a static IP that I use for my sshing needs.
[/LIST]

I'm guessing I'd start with fetchmail. From there, I need a wee bit of guidance, please!

---

### Post by jtc on 2007-02-04
> **katiad said:**
> 
[*]  I have several pop accounts from different places.
[*]  I'd like them all stored on my local machine permanently. I would really prefer that my messages ultimately be stored in MH or some similar format, where each message is an individual file in a folder. I have ten billion messages, and I've learned the hard way that corruption of a large mail file really sucks.

As you mention yourself below, *fetchmail* is the place to start. Considering what you want to do later on I'd say you'll want the fetched mails sent into an MTA (Mail Transfer Agent). Myself I like *postfix*.

> **katiad said:**
> 
[*] I'd prefer to be able to use any mail client to read these messages - from mutt over ssh to sylpheed. (imap?) 

If just going to read the mails by running mutt locally you don't have to do anything more. When it comes to other MUAs (Mail User Agents) such as Sylpheed I assume you plan to run them from another computer, since you talk about IMAP? Then you'll need an IMAP-server, such as *Courier*

> **katiad said:**
> 
[*]I want to run these messages through a good spam filter, because the ones on my isp and other accounts mostly suck.

An updated *Spamassassin* should do the trick, especially if you train the Bayesian filter. You might want to run it through *amavisd-new*, which often simplifies spam- and virus filtering.

> **katiad said:**
> 
[*]I need be able to send email and reply to emails from each of these accounts separately and transparently. Unfortunately, not one of my accounts will allow email from another domain to be sent through their smtp servers, so setting up a single account's smtp server to do the job for all of them is not possible. I'd guess I'd need my own smtp server... In the same vein, I need to ensure that the reply-to addresses are correct. This is where I've run into problems - haven't found much yet explaining it, and I'm not sure it's even possible.

By now you already have your own SMTP-server (see the MTA above). But it might not do the trick, since a lot of ISPs block port 25 (SMTP) outbound. About the reply-to part I don't think I understood it entirely. Perhaps an example?

> **katiad said:**
> 
[*]I need to sort these messages out according to to/from headers so I don't have ten billion messages dumped into the same folder needing hand-sorting.

Here *Procmail* is the way to go. 

> **katiad said:**
> 
[*]Some sort of web-accessible interface would also be lovely, if at all possible. I don't care to attach a domain to the box, but I do have a static IP that I use for my sshing needs.

I kind of like *Squirrelmail*. It isn't fancy in any way, but defiantly does the trick.

---

