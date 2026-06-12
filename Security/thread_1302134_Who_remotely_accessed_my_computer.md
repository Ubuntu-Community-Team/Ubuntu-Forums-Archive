---
title: "Who remotely accessed my computer?"
date: 2009-10-26
forum: Security
---

### Post by adlin5000 on 2009-10-26
I had my bosses computer setup for remote access so I could do some work on it without having to keep using two sets of keyboards/mice. I was getting ready to work, but had not yet connected. I noticed the screen-saver go off so I looked over at it and noticed the pop-up saying that someone was remotely controling my computer. I shutdown the computer, disconnected the network, restarted and put in a password for the remote-access.

My question is, is there a log that can tell me who connected?

---

### Post by blur xc on 2009-10-26
I did.




j/k....

I don't even know how to remotely connect to my own computer...

sad...

BM

---

### Post by ApEkV2 on 2009-10-26
> **blur xc said:**
> I did.




j/k....

I don't even know how to remotely connect to my own computer...

sad...

BM
You could've made it sound better lol.

@adlin. How long is your password, and is there a good variety of characters/numbers?
Go to [http://www.passwordmeter.com/](http://www.passwordmeter.com/) and tell us what the score is.

---

### Post by Sarmacid on 2009-10-27
System -> Administration -> Log file viewer

auth.log is the authentication log, but you might wanna check out others like syslog too see if the attacker actually did anything.

---

