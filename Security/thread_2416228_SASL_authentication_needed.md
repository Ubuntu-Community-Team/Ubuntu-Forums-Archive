---
title: "SASL authentication needed"
date: 2019-04-07
forum: Security
---

### Post by huff2 on 2019-04-07
Hi everyone! Hope everyone is having a great day!

I'm working on a python project that needs to connect to an IRC; I'm using freenode to attempt to connect to. I'm getting an error that says that I need to identify using SASL, since I didn't, I get rejected from the server. 

I've been researching SASL and I'm very new to networking and security protocols. I'm just unclear, is this a problem on my end (i.e. do I need to install some package to my OS that gives me SASL authentication?) or is this something that needs to be coded into the program? 

Anyone that can shed light on SASL, how this is working and what I need to be researching will be greatly appreciated. It's an overwhelming sea of knowledge out there, ha. 

Thanks!!

FYI - I'm running the latest, stable Ubuntu release: 18.04.2 and simply using my Verizon cell phone as a mobile hot spot to access the internet with my laptop.

---

### Post by TheFu on 2019-04-07
I don't know the answer, but ... there are lots of IRC clients out there which do work with freenode.  Grab the source code from them and look at their implementation of the login methods.

---

### Post by jeremy31 on 2019-04-07
A verizon cell phone likely has an IP address that requires SASL on freenode, it may be easier to try a different IRC network

---

### Post by TheFu on 2019-04-07
> **jeremy31 said:**
> A verizon cell phone likely has an IP address that requires SASL on freenode, it may be easier to try a different IRC network

Last fall, there were hundreds of spambots on freenode's servers, so they switched to a default block mode for unregistered users.  The different channel ops have attacked this in different ways. Some block all unregistered accounts, some block accounts who they don't know, some force waiting 10 minutes before any messages can be posted.  If you contact the channel op, they can tell you their policy about logins. Perhaps they will whitelist your bot?

One policy:
>  A recent spam flood on Freenode means that the channel for the time beeing is moderated. We will give you voice a short time after you join, so be patient.

But I still haven't a clue beyond being an IRC user. ;)  I cheat by having a BNC setup so my accounts always _appear_ to be connected to the channels where I'm active.  And I don't spam.

---

### Post by huff2 on 2019-04-07
Guys, this is great advice, thank you! The project is of course an IRC bot but not for spamming or any other ill intention. It's merely for learning. I did think that the problem may stem from my Verizon hot spot access (which I hate using, btw, I just have to for now ... too poor hahahaha). The more I read about the SASL authentication system, the more I am realizing that this will require code, not just a package that I need. 

I had thought about attempting to access through a VPN, but then I wouldn't learn or apply anything in regards to SASL. So, I'm just going to keep plugging away until I figure it out. Besides, the whole point of the project is to learn something that I use to think was elusive. 

Thanks again, guys!!

---

### Post by QIII on 2019-04-07
While we certainly do not question your intent, providing help here would provide a resource for those whose intent is nefarious.

Closed.

---

