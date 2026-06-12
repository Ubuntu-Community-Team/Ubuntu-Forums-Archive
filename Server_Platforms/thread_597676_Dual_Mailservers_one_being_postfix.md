---
title: "Dual Mailservers one being postfix"
date: 2007-10-30
forum: Server Platforms
---

### Post by macka` on 2007-10-30
Hi all, 

This might be a case of someone saying.. "you're crazy", but we've installed and configured up postfix etc to be our mailserver, however my boss being a windows lover, wants to see both mailservers (exisiting Mdaemon runs on windows) collecting mail etc side by side...
This is so that we don't loose any mail, and we can do a (sorta) test switch. 

So what i'd like to know or pointed in a direction, is to... 
have both my mailservers receiving mail for users, and I'm thinking that you can only ever send through one host (i'm accepting this). 

I think that this might not be possible based on the fact that its going to be a bit of a race condition to whole gets the mail first. 

Anyhow - suggestions welcomed! Or different ways to do the same/similar thing?

Cheers
Grant

---

### Post by macka` on 2007-10-30
Thinking about this a little further, 
i think i'd have to put the Ubuntu server in the middle and use it to send/recieve emails from the current mailserver so it would look like...


router <------> postfix (new Mailserver) <-------> Mdaemon (current mailserver)


So using that model, how would one tell postfix to deliver the email locally, but also send a copy off to a final destination?

Does that make sense?

Cheers
Grant

---

### Post by HermanAB on 2007-10-31
Use always_bcc in main.cf (somewhere around the middle of this):
[http://www.postfix.org/ADDRESS_REWRITING_README.html](http://www.postfix.org/ADDRESS_REWRITING_README.html)

to forward all incoming mail to the other machine.

Cheers,

Herman

PS.  I always have to plug this one: [http://www.citadel.org](http://www.citadel.org)
'Cause it is way better than anything else...

---

### Post by macka` on 2007-11-01
is citadel a full mailserver as well?

---

### Post by macka` on 2007-11-01
Ok - got that working, BUT (there's always a but), I can't get postfix to deliver a local copy of the message. I can get it to send it off to my other mailserver, but id like it stuck in the users box as well... is that possible?

Grant
> **HermanAB said:**
> Use always_bcc in main.cf (somewhere around the middle of this):
[http://www.postfix.org/ADDRESS_REWRITING_README.html](http://www.postfix.org/ADDRESS_REWRITING_README.html)

to forward all incoming mail to the other machine.

Cheers,

Herman

PS.  I always have to plug this one: [http://www.citadel.org](http://www.citadel.org)
'Cause it is way better than anything else...

---

### Post by HermanAB on 2007-11-01
Postfix by default delivers to /var/spool/mail.  It should create a mbox format mailbox for each user all by itself.  For users to download their mail, you need to install a POP and IMAP server - Dovecot is a good one.  To use Dovecot, you have to configure Postfix to deliver in maildir format.  The problem with Postfix is that if someone sends a message with a large attachment to all users, then Postfix stores a full copy of that for each user, gobbling up disk space.

Regarding Citadel: It can do everything and all protocols.  It is a very efficient and self contained mail system that can handle tremendous amounts of mail, because it uses a BerkeleyDB back-end (up to 256 terrabytes!).  Citadel only stores ONE copy of a message irrespective of how many users it is delivered to.   

I have a few hundred users on a Dell PE750 and it is really just idling with about 0.2% load most of the time.  There is nothing easier to install - it takes about 20 minutes - thanks to their 'Easy Install' script and then it Just Works.

Citadel is actually very old and mature and therefore the core system is bug free.  It dates back to circa 1982, when it was a popular BBS.

Cheers,

Herman

---

