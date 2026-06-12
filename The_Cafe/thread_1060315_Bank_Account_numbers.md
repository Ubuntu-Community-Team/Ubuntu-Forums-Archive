---
title: "Bank Account numbers"
date: 2009-02-04
forum: The Cafe
---

### Post by cartisdm on 2009-02-04
Does anybody know if an account number can be broken down to tell if it's specifically a checking account, business account, or savings account?  I'm working on a project at work where we want to limit the number of fields a user has to enter.

I know there is a specific formula for a banks routing number 

```
(( 3 (d_1 + d_4 + d_7) + 7 (d_2 + d_5 + d_8) + d_3 + d_6 + d_9 ) \mod10 = 0)
```

We're going to use a database to determine the bank's name based on the routing number entered, but what about the account number?  I've exhausted google and found nothing of use.  Naturally, this forum yields the next best results:D:D

---

### Post by cariboo on 2009-02-04
Every bank has a different numbering scheme as far as account numbers go, for instance my bank uses a - in business chequing accounts numbers, while personal chequing and savings account numbers don't.

Jim

---

### Post by Polygon on 2009-02-04
on my checks, the format is this:

:XXXXXXXXX:XXXXX:XXXXXXXXXX:

the first set of numbers is the routing number, i dunno what the middle one is, the last one is the account number

---

### Post by yabbadabbadont on 2009-02-04
> **Polygon said:**
> on my checks, the format is this:

:XXXXXXXXX:XXXXX:XXXXXXXXXX:

the first set of numbers is the routing number, i dunno what the middle one is, the last one is the account number

The second is probably either the check serial number (if a personal size check) or a combination field that indicates type of account/branch number/check number.  By the way, it is the MICR symbols that delineate fields, not spaces.  (at least that is how the hardware reads it)  So if there is just a space between the middle field and the account number, then it would all end up in the account field that the hardware reader sends back to the software.  (which can then break it up according to bank-specific patterns)

You learn a few things after writing software for high speed check capture systems for 12 years.  :D

---

### Post by cartisdm on 2009-02-04
In other words you guys are saying that I'm pretty much out of luck for being able to decipher what type of account it is, huh?

---

### Post by tazz4vr on 2009-02-04
The routing number is usually that of the actual bank and I believe it specifies which division it goes to for processing, it is suppose to specify which bank it is when processing the checks via electronic means,  the middle numbers are usually the check number, and then lastly the account number.  However, due to all the counterfeit issues, it is possible this may have changed a bit, but having a peek at both my personal and business checks, they appear to follow same suit, with the exception of a few spaces..

---

### Post by tazz4vr on 2009-02-04
> **yabbadabbadont said:**
> The second is probably either the check serial number (if a personal size check) or a combination field that indicates type of account/branch number/check number.  By the way, it is the MICR symbols that delineate fields, not spaces.  (at least that is how the hardware reads it)  So if there is just a space between the middle field and the account number, then it would all end up in the account field that the hardware reader sends back to the software.  (which can then break it up according to bank-specific patterns)

You learn a few things after writing software for high speed check capture systems for 12 years.  :D

Small world yabba...I was a proof operator for about 6 years for a corp branch with 6 little ones...the amount of checks that came through, they weren't all that little either, they lied to me!

---

### Post by yabbadabbadont on 2009-02-04
> **tazz4vr said:**
> Small world yabba...I was a proof operator for about 6 years for a corp branch with 6 little ones...the amount of checks that came through, they weren't all that little either, they lied to me!

I remember the first time that I saw a large cash transaction report for a bank in Miami.  We would run the report, see how many pages it was, kill the print job, up the exemption limit and try again.  I think we got it up to $25,000 and still had a 10 page report for one of the days with which we were testing.  <sarcasm>Gee, I wonder where all that cash was coming from?</sarcasm>  :lol:

---

### Post by yabbadabbadont on 2009-02-04
> **cartisdm said:**
> In other words you guys are saying that I'm pretty much out of luck for being able to decipher what type of account it is, huh?

Yep.  Every banking institution uses its own means of identifying accounts.  It can be a real pain in the tucus too.  Especially with large institutions who may have acquired and/or merged with several other banks.  Then you have to try to handle multiple numbering schemes until such time as all customers are converted to the new scheme.  (which sometimes never happens)

---

### Post by tazz4vr on 2009-02-04
yeah...ha ha...my fingers are still feeling the pain, most of the time the checks and their info were manually entered, at least when I did it, now i'm sure everything is just read right off them, with only a few glitches here and there.

---

### Post by yabbadabbadont on 2009-02-04
> **tazz4vr said:**
> yeah...ha ha...my fingers are still feeling the pain, most of the time the checks and their info were manually entered, at least when I did it, now i'm sure everything is just read right off them, with only a few glitches here and there.

The trend when I left the industry in 2005 was for everything to be done using small teller scan imaging stations.  I still have friends in the biz and they have said that almost all of the large capture machines (reader/sorters) are out of use these days, except for very large remittance operations like bill payment processors.  I think that very little proofing work is done now.  Even before I left, everything was switching over to image amount entry and image reject correction and balancing.  That facilitated the use of CAR/LAR (courtesy amount read/legal amount read) automation.  Our company even had a product that allowed for the outsourcing of image amount entry work to remote locations (even overseas) using secure internet connections.

---

### Post by tazz4vr on 2009-02-04
A client of mine currently does the outsourcing as well...very much in use these days, unfortunately can be found off in la-la land floating around, sometimes too risky I think, as in the IE issue a month or so back....depending on the nature of the product it's usually pretty secure.

---

