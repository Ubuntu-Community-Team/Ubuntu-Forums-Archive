---
title: "Account(s) with Two Passwords"
date: 2011-03-10
forum: Security
---

### Post by Imber on 2011-03-10
Hi!

Is it possible to have two passwords associated with one account, one that is the real one and leads to the actual encrypted home partition, and the other that shows, upon entering the bogus password, a home partition (also encrypted) to hide the real sensitive data on the first one? 

The idea is to have the fake password lead to a home drive that looks as if it were the real deal, but it is wiping particular sensitive data (not necessarily everything, as that would take too long) in the background, so that the actual data are not compromised. I think it's possible when you add a wrong password, but that means anyone who wants to delete your data might do that without much ado, so that is not a viable option.

I'm interested to hear your thoughts.

- Imber.

---

### Post by whatthefunk on 2011-03-10
But the original problem still remains, doesnt it?  If somebody gets your real password, then your data is compromised.
And if youd rather have data erased than compromised, do you really need to keep it?

---

### Post by Imber on 2011-03-10
Not necessarily, if they have the original password, they still need to decrypt (some of) the sensitive data. On the other hand, if someone "thinks" (s)he has the right password, it might be enough time to make sure the real data never get accessed by the wrong people.

The data are very important, so it is necessary to keep them, but it's best to have them erased than have others see/have the files.

---

### Post by robsoles on 2011-03-10
Got one thing to say to the 'encrypters' of this world.

Pinhole camera over your shoulder sweetie ;)



Pressed, I might go on; Get your sensitive data on two adequate capacity memory sticks (or SSD's) and keep one with yourself and the other with the most trusted 'other' you know - now it'll just take torturing/menacing/scaring either of you enough to get to the sensitive data.

Have a nice day ;)

---

### Post by robsoles on 2011-03-10
Actually, better on topic:

If they have access to the actual physical media then they would be foolish to boot from it - they boot it up from LiveCD or similar and whatever amount of scripting or coding you have is on it's ear.

If you can encrypt it with your known key then rest assured that it can be decrypted with an unknown key applied with diligence, patience, skill/common-savantness(idiot genius, LOL) and time - deal with it.


Also, everybody is connected in a bizarre psychic way and we all know your secrets to some or other degree - I'm drunk right now but if you catch me sober and press me to explain I might make the hair on the back of your neck creep, I might just as equally make you roll your eyes :p :roll:

---

### Post by Imber on 2011-03-10
I know that there are other ways of getting at the information but it was merely a query into the possibility not a request for a lecture in security.

---

### Post by Grenage on 2011-03-10
> **Imber said:**
> Hi!

Is it possible to have two passwords associated with one account, one that is the real one and leads to the actual encrypted home partition, and the other that shows, upon entering the bogus password, a home partition (also encrypted) to hide the real sensitive data on the first one? 

The idea is to have the fake password lead to a home drive that looks as if it were the real deal, but it is wiping particular sensitive data (not necessarily everything, as that would take too long) in the background, so that the actual data are not compromised. I think it's possible when you add a wrong password, but that means anyone who wants to delete your data might do that without much ado, so that is not a viable option.

I'm interested to hear your thoughts.

- Imber.

It sounds like you're after is a 'duress' password; I think that's what they're called.  The correct password will display the data, the duress password (as in, you're being poked with a cattle prod) will open another section.

I believe that products such as Truecrypt offer this.

---

### Post by Imber on 2011-03-10
> **Grenage said:**
> It sounds like you're after is a 'duress' password; I think that's what they're called.  The correct password will display the data, the duress password (as in, you're being poked with a cattle prod) will open another section.

I believe that products such as Truecrypt offer this.

Thank you very much. I'll look into it.

---

### Post by BkkBonanza on 2011-03-10
I don't think this feature is available natively in Ubuntu encrypted home (ecryptfs) and I recall once reading that they had no plans to do it. However, this type of thing is available with **Truecrypt** which works very well on Ubuntu (I use it). 

You can likely add a login script to mount a truecrypt partition where you need. When you enter the duress password it mounts the fake data and when you enter the real password it mounts the real data. The only limitation is that both data overlay the same partition space (starting at top/bottom) and so you need to fix how much fake data and not exceed that limit. Usually it's just static fake data. 

Oh, unless you can get fancy it would require a second password. Maybe there's a way to hook it into PAM and have a single password... google.

Just don't be a journalist being caught out in the desert where you were told not to go!

---

### Post by bodhi.zazen on 2011-03-10
The closest you can come to this is to use one password to log int and a second password to decrypt your home directory.

Probably easier to use cryptkeeper or LUKS to keep a crypt separate from your home directory for sensitive data.

---

