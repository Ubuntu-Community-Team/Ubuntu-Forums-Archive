---
title: "trick passwords"
date: 2015-08-18
forum: Security
---

### Post by haplorrhine on 2015-08-18
I think it could be useful, a trick password that notifies you of its use(s).  Maybe it could actually log in, but it would at least hide the notification.  Suppose you wrote some passwords down somewhere, so you mix in some trick passwords.  Suppose you want to test a sketchy wifi connection, so you log in with the trick password.  If this feature became common, then nobody could tease them out.

---

### Post by TheFu on 2015-08-18
Sounds like a Honeypot.

Security is hard.
OpSec is even harder.

On any open wifi - never do anything on the network until your VPN is working - PERIOD.  There are too many reasons to list all of them. A quick search on the topic will explain. There is never anything so important that open wifi without a VPN should be used. NOTHING.

BTW, if you are using passwords to login, you've already failed from a security perspective.  There are 2FA methods available for both local and remote authentication - something you have, something you know. They just aren't standard.

I've been doing security stuff on the side for 15 yrs and what I've learned is that creating anything secure is a subtle balance that takes multiple experts to see the flaws in an idea. For non-experts, it is best to follow what others have done and vetted for 5+ yrs.  Oh - and if anything claims to be FIPS compliant - RUN AWAY!

---

### Post by bashiergui on 2015-08-18
[quote=TheFu]Sounds like a honeypot[/quote] Honeywords
[http://people.csail.mit.edu/rivest/pubs/JR13.pdf](http://people.csail.mit.edu/rivest/pubs/JR13.pdf)

> Businesses should seed their password databases with fake passwords and then monitor all login attempts for use of those credentials to detect if hackers have stolen stored user information. That's the thinking behind the 'honeywords' concept first proposed this month in 'Honeywords: Making Password-Cracking Detectable,' a paper written by Ari Juels, chief scientist at security firm RSA, and MIT professor Ronald L. Rivest (the 'R' in 'RSA'). Honeywords aren't meant to serve as a replacement for good password security practices. But as numerous breaches continue to demonstrate, regardless of the security that businesses have put in place, they often fail to detect when users' passwords have been compromised.

---

### Post by TheFu on 2015-08-18
I wouldn't do this on a production system, but if a honeypot was setup on a firewalled segment away from the production systems, sure.
[https://sysdig.com/fishing-for-hackers/](https://sysdig.com/fishing-for-hackers/) - would you want that on your network?

---

### Post by bashiergui on 2015-08-23
> **TheFu said:**
> I wouldn't do this on a production system, but if a honeypot was setup on a firewalled segment away from the production systems, sure.
[https://sysdig.com/fishing-for-hackers/](https://sysdig.com/fishing-for-hackers/) - would you want that on your network?
Honeypot in the network with prod systems- no. That would be inviting hackers in.

Honeywords could be in the production network though. They don't do anything other than sit in Active Directory (or whatever you're using). If the accounts ever got used you would know your SAM/LDAP/AD got dumped.

---

### Post by tgalati4 on 2015-08-23
I used to do that with junk mail.  Whenever I signed up for a service, I would use a different middle initial A, B, C etc., and kept a log book.  Then as the junk mail came in, I could correlate the middle initial on the address with what service I signed up for.  It was an interesting exercise.  Didn't reduce the junk mail, but now I knew where my name and address was being sold.

The problem with honeywords is that by the time you have detected such an intrusion, it may be too late.  It gives you an after-the-fact warning, that your systems have been compromised.

---

### Post by bashiergui on 2015-08-25
> **tgalati4 said:**
> The problem with honeywords is that by the time you have detected such an intrusion, it may be too late.  It gives you an after-the-fact warning, that your systems have been compromised.
Sure. This is post-compromise, but in the world of detection "better late than never."

---

