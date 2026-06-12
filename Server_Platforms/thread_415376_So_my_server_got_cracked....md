---
title: "So my server got cracked..."
date: 2007-04-20
forum: Server Platforms
---

### Post by malder on 2007-04-20
I wasn't certain before (just had a password that wouldn't work and very large - 10x from day before - auth.log), but now I am. Postfix sent ~3500 bouced email notifications in a very short time period to my admin user system mailbox. So it appears my server has been commandeered for nefarious purposed. Bumber. I have been a bit lazy with my security efforts. I know - my bad. I'm a nieve noob, etc... I understand. I don't need a lecture on that topic. I stopped Postfix, so hopefully that will prevent any more spam from going out, so....

What I **do** need is help on where to go next. Reading around the forums it seems the safest route is to just wipe everything and start with a clean slate. Is there any way that I can back-up and preserve some of my settings and such(e.g. databases, email, webalizer data, user info/settings, ispconfig settings/info, etc...)?

Any good reasource/list on how to prevent this in the future is also welcome.

Thanks for the help

Matt

---

### Post by BitHosts on 2007-04-21
A firewall - shorewall - is usually a good way to start.

Personally I wouldnt trust any of the configuration youve got at the moment - clean slate all the way.

---

### Post by Swab on 2007-04-21
How did the cracker get in? ssh?  Was it a brute force attack?  If so, make sure that next time you change the ssh port number and only allow certain (preferably one) users access.

---

### Post by codingmaster on 2007-04-21
Hello!

First of all, I would suggest to check how the system break-in happened.

For backup, try to get all data from:
/etc + /var
and there where you actually have saved other data.

But also try to dump your databases.

You have said, that you are really new to the topic of system security.

I guess, that it will be really hard for you to check, whether your data has been 
changed or not. It needs a deep knowledge to see changes on the system.

But I really do not want to make you sad: really try to backup those things you will need
and at least try to have a look at them, e.g. database dumps, configuration files.

If you are in doubt, then just setup the configuration file from scratch and try to remember what you have wanted to achieved in the first configuration.

I would suggest to really take care about services running on your machine.
There are pretty much things, that you can do wrong.

Do you really know, that someone break into your system?

That email flood can occur, when you misconfigure your MTA.
The worst mistake that can happen and it hurts really much, when you 
see that spammers are using your server for spam, because you have 
configured an open mail relay for them.

A good hint is to use a paper, where you write down the needed services, the needed ports and the permissions. You can enhance that manual and add more and more things, so you will be able to recover your system really fast, when something will happen.
This will also will train your eye for system configuration and the changes you have done.

Good luck!

Best regards, Georgy Berdyshev

---

### Post by jtc on 2007-04-21
Codingmaster: Excellent post!

I couldn't have written it better myself :)

---

### Post by codingmaster on 2007-04-21
Hello!

> **jtc said:**
> Codingmaster: Excellent post!

I couldn't have written it better myself :)

Thanks a lot!

Best regards, Georgy Berdyshev

---

### Post by TyphoonJoe on 2007-04-23
Sounds like you have a good idea how to start, but here is a pretty nice checklist of security considerations:

[http://www.cert.org/tech_tips/usc20_full.html]("http://www.cert.org/tech_tips/usc20_full.html")

---

