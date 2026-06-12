---
title: "Mail server... very confused!"
date: 2005-03-16
forum: Server Platforms
---

### Post by ElricOfGrans on 2005-03-16
G'Day,

I am trying to set things up for the redistribution of mail and, ultimately, sending more later on. This isn't my area, so please forgive me if the way I describe things sounds odd.

The situation is that there is an external mail server which collects all mail (user1@domain.com, [email]user2@domain.com[/email]) together, and I need to get this, sort it, and send it to the appropriate people. I then need to set it up so each individual can send emails from their own systems.

I think what needs doing is that I use fetchmail to get the mail from the external server, then somehow in .fetchmailrc sort it; these are then delivered to mailboxes on the mail server system. At the moment, everything goes to the user calling fetchmail :(

Then, using dovecot to set up an internal mail server, users can get their mail from this system and read it on their own. This actually does work!

I then believe I need to use Postfix to handle sending emails back out again, but don't really know exactly how, and to be honest I've not really looked too much - I'm more concerned with making it so that I can recive mail first.

I've done a lot of Googling on this, but as it's not my area I'm not making much of what I find. I probably just need a little direction - or perhaps someone to tell me that I've got completely the wrong idea :)

---

### Post by garyng on 2005-03-16
fetchmail is in general considered as a client side tool. If each of your user has an account on the server(in *nix sense, i.e. can login and have a shell), they can just run fetchmail on login and get the mail. The mail would be deposited to their mailbox by fetchmail which can be read by a number of mail clients(evolution etc.) or served to remote through imap/pop server.

You may not need postfix for outgoing as evolution etc. can use your upstream(ISP) smtp server as smart host. postfix is in general used for receiving mail directly on the internet(or other more generic use).

Can't say more without knowing exactly what you intend to do.

---

### Post by deuce868 on 2005-03-16
Oreilly has a really good postfix book I used (with their Bind & DNS book) to get a good system up and running at work. You really might consider picking it up. It's a very complex subject with a ton of misc things from one install to the next.

---

### Post by ElricOfGrans on 2005-03-17
``If each of your user has an account on the server(in *nix sense, i.e. can login and have a shell), they can just run fetchmail on login and get the mail. The mail would be deposited to their mailbox by fetchmail which can be read by a number of mail clients(evolution etc.) or served to remote through imap/pop server.''

That's what I'm trying to ultimately do (and that part does work at the moment), but first I need to sort the mail into each of these mailboxes on the server. The mail currently resides all on one external system irregardless of who it is addressed to. When I get the mail from the external server to my mail server, I want to sort it so it ends up in the right accounts, but at the moment it just ignores who it is to and puts them all in the same account.

``Oreilly has a really good postfix book...''

I've seen that. I may have to read it when I get up to that bit. Honestly, who'd have thought mail would be so complicated? ;)

---

### Post by garyng on 2005-03-17
different login account run fetchmail would automatically put them in their mailbox(sorting). If you want one central fetchmail operation(security?), feed them to procmail that would do the distribution/sorting etc.

---

### Post by ElricOfGrans on 2005-03-17
That does the job! Procmail is doing exactly what I wanted. Well, almost: I'm having one small problem with it. I seems to sort twice. When I check my procmail.log, it matches the regexp and forwards to the correct box. However, the procmail.log for the user it is forwarded to shows that it is matched to this regexp (obviously) so it forwards to itself (which results in a Mailer Daemon message). How do I stop it from double-checking?

---

### Post by garyng on 2005-03-17
my WAG, your system has been setup to run procmail automatically whenever there is mail deposit to a user's mailbox.  Logically it is like this :

1. "superuser" collect all the mails and use procmail to split them
2. promail would deposit/delivery them to desired user
3. since there is a new mail comes in, the user's procmail kick in again(this is desirable in many case as they can do their own cat/sorting).

Have you by any chance put the procmail rule to /etc which could become a "global" rule ?

---

### Post by ElricOfGrans on 2005-03-17
Thanks for that, garyng! I knew I had to have done some silly little thing like that. It was in /etc/. I moved it to the directory of the user running fetchmail, and it works like a charm. I'm now reciving mail, it's being sorted, and each user gets what they should be. The next challenge will be setting it up to send mail; now's where that book on Postfix may come in handy!

Thanks again!

---

