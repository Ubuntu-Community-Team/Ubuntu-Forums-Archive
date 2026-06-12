---
title: "Can an address book get compromised in Ubuntu?"
date: 2019-06-19
forum: Security
---

### Post by MibunoOokami on 2019-06-19
Hi all,

Is it possible for an address book to get compromised in Ubuntu?
I got a spam email using my wife's (very uncommon) name, and a fake email address. An online search suggests the following possibilities: a random fluke due to common names; a compromised address book; or phishing from social media platforms. Also the person whose name is used is more often than not, the one that has a compromised address book.

The thing is neither of us use social media, or Windows, and as mentioned earlier you couldn't fluke getting my wife's name right when randomly spamming, so the only logical thing I can think of is that perhaps her address book has been compromised.

Any suggestions or advice is appreciated as always.

---

### Post by DuckHook on 2019-06-19
It is possible for *anything* to get compromised. However, it is more likely that someone else who has your wife's name in their contact database got compromised. Mind you, this may be no better news than had your wife's address book been directly compromised.

Phishing attacks using real names (no matter how obscure) are dime-a-dozen these days. For goodness' sake, even *Equifax* was hacked resulting in hundreds of millions of personal records stolen. In their case, their security practices were moronic, but not a day goes by without some agency, hospital or entire municipality getting hacked—and those are only the public bodies that have an obligation to report. I would venture to guess that, at this point, all of our private info has been thoroughly compromised from multiple sources many times over. That your wife's unusual name has been exploited in a phishing scheme is no surprise at all.

The world has become a sad place that is indifferent to the integrity of personal info. These days, it is messages from our friends and family that have to be treated with the *most* suspicion, since scumbags are cunning enough to know this to be their best strategy.

---

### Post by DuckHook on 2019-06-19
*Thread moved to **Security** as the more appropriate forum.*

---

### Post by TheFu on 2019-06-19
Anything can be compromised.  It is more likely that she filled out a form at a store and that information was leaked or stolen. 

Teach her to use a few different email accounts for different purposes.  Accounts tied to any sort of money transaction need to be different.  Each bank gets a different email. Each retail company gets a different email if there is a credit card connected.  I use different emails for all other logins too, but many people might reuse those.  And lastly, there's an email that I use with family.  

One of my family members got hacked. The spam from that was pretty huge for a few years.

So, who has your wife shared the email address with over the years?

---

### Post by MibunoOokami on 2019-07-10
Thanks for moving the thread to the appropriate forum.

Whoever has been compromised doesn't seem to have access to any of my wife's other contacts because she's asked everyone if they received spam under her name and none have.

We don't generally give each other's email out to people/companies as there's really no need, but perhaps this has happened at some point.

Regarding the dozens of different email addresses, wouldn't the all be able to be compromised in a sense since you have to provide a mobile number when creating an account?

---

### Post by kpatz on 2019-07-11
Seems like everything's been compromised at one time or another.  Years ago Facebook was compromised and I still get spam emails "from" friends I've had.

An advantage of using separate email addresses is if one gets compromised, you know what was compromised (whatever entity you gave that address to) and you can always delete that address to stop the spam.  Of course, maintaining many email addresses can be cumbersome, but many email providers let you create aliases (additional addresses that go to a single inbox).  If one gets compromised, delete it and create a new one.

If your mobile number gets compromised, you may get spam calls/texts to that number, but whatever database the number was stolen from will only have one of your dozen email addresses.

---

### Post by TheFu on 2019-07-11
I don't use services which require a phone number.

Mobile SIM spoofing is a thing. People trust their cell devices entirely too much.  In fact, your cell phone is probably the least secure device you have. Don't use it for anything sensitive.  Just. Don't.

Anyone can send email using any FROM address they like.  The FROM is not required, not validated. I use to send emails to a family member as [email]god@heaven.net[/email] just to mess with her.  There are anti-spoofing techniques on the receiver side these days which makes sending using certain domains harder, but not impossible.  For example, heaven.net has a restrictive SPF DNS TXT record,
```
heaven.net.             3600    IN      TXT     "v=spf1 mx ip4:74.50.57.154 -all"
``` which says to only allow emails from that single IP address for any email claiming to be from heaven.net.  But it is up to the receiving email server to process the *-all* option correctly.  Many small companies don't.  My domains use a similar restrictive email SPF DNS TXT record to prevent unwanted spam, yet a few times a month someone will claim to have gotten emails from my domain that were never sent from the approved IPs. Their email provider is just lazy.

Some of the worse companies at this stuff are those who outsource contact services - like hotels, airlines, and huge businesses. They don't know all the subnets who should be allowed to send spammy/marketing emails out, so they don't use absolute Yes/No SPF records, they use "Fuzzy" ones.

Ooops. Sorry - probably way off topic now.  What was the issues again?  Ah ... a friend's contact DB has her email and got pulled by all the social networks, then either the social network sold the data, got hacked, or some security researcher was given the data. Plus all her friends have the email address, so it is very likely one or 50 of them have a virus on their PC or smart phone or tablet or ....

This just in today: [https://www.howtogeek.com/427152/why-can-you-get-spam-from-your-own-email-address/](https://www.howtogeek.com/427152/why-can-you-get-spam-from-your-own-email-address/)

---

