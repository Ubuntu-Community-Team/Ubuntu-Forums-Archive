---
title: "Unsecure ubuntuforums website"
date: 2024-01-16
forum: The Cafe
---

### Post by him610 on 2024-01-16
After attempting to go to ubuntuforums.org using Chrome, I am met with the message,...
> The connection to ubuntuforums.org is not secure
You are seeing this warning because this site does not support HTTPS. 

Any comments?

---

### Post by Tadaen_Sylvermane on 2024-01-17
I'd say something is wrong with Chrome. This is the exact address I'm looking at this thread.

```
https://ubuntuforums.org/showthread.php?t=2494436
```

Looks like https to me. Firefox for the record.

---

### Post by grahammechanical on 2024-01-17
Same on my machine.

Firefox

> [https://ubuntuforums.org/showthread.php?t=2494436](https://ubuntuforums.org/showthread.php?t=2494436)

Google Chrome

> [https://ubuntuforums.org/showthread.php?t=2494436](https://ubuntuforums.org/showthread.php?t=2494436)

There should be a padlock icon to the left of the address panel. Or a review site details icon  Clicking on that icon says: "Connection is Secure". Click on the arrow and I see this

> Connection is secure, Your information (passwords or credit card numbers) is private when sent to this site.

Regards

---

### Post by Paddy Landau on 2024-02-11
I've seen this a number of times on various websites.

Sometimes, when you use a link that has http instead of https, the website isn't set up to immediately redirect to https. This leads to the message. When you continue, though, only then does the http redirect to https.

It's almost always a fault on the side of the website setup, which should (ideally) redirect immediately rather than afterwards, which would have prevented that message.

---

### Post by TheFu on 2024-03-06
TLS isn't really security. It is more about privacy between the client and the server.
Learn more: [https://www.youtube.com/watch?v=eRWbNno4sN4](https://www.youtube.com/watch?v=eRWbNno4sN4)

---

### Post by him610 on 2024-03-31
@TheFu
Thanks for the TLS reference. 
I did not know how much I did not know. My bulb does not burn as brightly as it once did.

---

### Post by TheFu on 2024-03-31
Tech people (and merchants who want our money) have been over-simplifying SSL/TLS as "Security", so it isn't any wonder that most people get that confused.
When there isn't any money involved, it is about privacy and assurances that the packages aren't modified between the client and server, but there are all sorts of ways to trick the client browser into connecting to the wrong server which can also probably have a legal cert in many parts of the world, thanks to govt control over DNS.  It is a house of cards.  If any single part isn't just right, the best we can hope for is privacy between the client and the server.

Banks in much of the world added individual certs to validate the user and bank know each other, above what SSL/TLS provide.  In the US, that usually isn't done because the average person already finds tech too complicated and security with good passwords too hard.  Some of the "added" security in US banks is a joke. I don't know how much online fraud they have, but it must be huge.   I just noticed that ATM fees went up 33% this year.  Probably to fight fraud losses.

---

### Post by Paddy Landau on 2024-03-31
> **TheFu said:**
> Some of the "added" security in US banks is a joke. I don't know how much online fraud they have…
Here in the UK, some banks do well, but others definitely don't. My bank insists on 2FA, but it's actually not; it's 1FA, twice, i.e. two different passwords. That doesn't count as 2FA!

Banks in the UK are legally liable (subject to certain conditions) for their customers' losses due to scams. This means that the banks have upped their game tremendously.

When I make an unusual transaction, or an online payment to a new person or business, the bank needs me to go through a certain procedure to confirm that it's really me, and it still sends a confirmation message via both text and email. Even contactless payments at shops are subject to extra verification when the bank's AI notices something unusual.

The bank's website displays warnings about scams, including while making online payments to a new person or business.

---

### Post by TheFu on 2024-03-31
> **Paddy Landau said:**
>  ...

Banks in the UK are legally liable (subject to certain conditions) for their customers' losses due to scams. This means that the banks have upped their game tremendously.


Individual accounts get protected up to $500K in the US, after a $50 amount.  You've probably seen "FDIC" on bank doors in US created TV and movies and didn't know what it was.  "Federal Deposit Insurance Corporation" ... basically the mandated federal insurance that all banks located in the US must have. It is mandated.  Using a check/debit card with an account usually doesn't even result in the $50 allowed loss being passed on.  The banks learned decades ago that it was better to just replace any money lost due to fraud than to be petty.  For a long time, credit cards had better protections in the USA than ATM/Debit cards did.  I'm not positive exactly when, but maybe between 2005 and 2010, the rules changed and ATM/Debit cards got the same protections as credit cards. Prior to that change, I never, ever, ever, used an ATM/Debit card for anything other than pulling cash from an ATM. I still use credit cards for all non-trivial purchases these days - anything over $50. Who doesn't want to have something for 6 weeks before paying to have it?  I happen to know the monthly closing data for transactions, so I tend to buy things the following week to get the 6-8 week "float" on it before actually needing to pay the credit card bill.  In the US, credit card transactions have a 3-4.5% fee and all the prices are the same regardless, so we pay about 4% too much for everything when we use cash.  It should be illegal to have that much surcharge. It is worse than a loan shark, but it is legal and everyone just pays Visa/Mastercard/Amex charge way, way, too much in these fees.  Cashless countries are doing it wrong if they allow more than 1% fees.

I've never had any online fraud, just credit card stuff showed up after a trip to Argentina.  The fraud happened in NYC, then Miami, on the same day about 4 months after I'd returned from the trip.  I was at home, nowhere near NY or Miami and I hadn't been to either city, not even their airports, that year.  At the time, the US didn't have chip+pin cards.  We still don't.  They are chip+signature cards, but I haven't needed to sign anything except at very small stores in about 5 yrs. They decided that the signatures were never checked and that their fraud software for every transaction was sufficient.  Seems odd to buy $1500 in stuff at a home store, but not have to sign for anything.

Business accounts do not have the same protections. Once the money is taken, it is gone.  As a CFO, I was always worried that someone would steal our payroll from the business account we used to pay our employees.  Whenever I did online banking with that account, I'd boot into a TinyCore Linux running off a CDROM and wouldn't visit any other websites except the bank.  That account was at a huge national bank that was really poor at security, IMHO.  I had an account with them after a "credit union" was bought/transferred to that bank, but closed the account when they disappointed me 1 time and nobody would even talk to me about the reason.  When the company was setting up bank accounts, we all wanted a bank that nobody had any personal accounts at and this 1 bank was the only one.  Plus, they had a full service branch walking distance from my home.  The people at that branch were great.  I could pop in an get anything notarized for free, for example.  Good for important contracts.

---

### Post by oldfred on 2024-03-31
> happen to know the monthly closing data for transactions, so I tend to  buy things the following week to get the 6-8 week "float" on it before  actually needing to pay the credit card bill.  In the US, credit card  transactions have a 3-4.5% fee and all the prices are the same  regardless, so we pay about 4% too much for everything when we use cash.

I think it just has become worse. 
There is a change where stores can charge separately for the credit. So they add 3-4% on receipt.
Multiple restaurants here in Florida are now doing that. Several of my neighbors now refuse to go to those places.
But I bet the price assumes the credit charge & then they charge for it again separately. More double dipping.

---

### Post by TheFu on 2024-03-31
If the cash price and the credit prices are different with cash being lower, then I'm all for that. Only people actually involved in the surcharge should be paying it.  In a few states it is illegal to charge more for credit vs cash ... so everyone paying cash is being screwed.

I look for places with different pricing for cash and strive to visit them.  Of course, if you only carry a credit card (and don't mind every purchase being tracked), you are free to spend your money where you like.  Walk-in places that FORCE the use of a credit card cannot be allowed. That is discriminatory.  The restaurants/groceries that only accept cards like we've all seen in NYC and some west coast places should be forced to accept cash.

Just because someone else doesn't think their privacy is important, than doesn't mean everyone feels that way.  Oppressive govts love cashless mandates.  What shocks me is that a few northern European countries are headed the same way. They don't realize what they are giving up.  Also, when the power/internet is out, how do you buy food?  People in Florida know that happens once every few years in their location.  Sometimes, only cash can be used.

---

