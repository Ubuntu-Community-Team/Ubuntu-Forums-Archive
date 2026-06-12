---
title: "&quot;'Strong' Passwords May Not Be All They're Cracked Up to Be&quot;"
date: 2010-04-27
forum: The Cafe
---

### Post by MasterNetra on 2010-04-27
A interesting article about strong passwords and how conventional wisdom about them is outdated.

[http://esecurityplanet.com/features/article.php/3878821/Strong-Passwords-May-Not-Be-All-Theyre-Cracked-Up-to-Be.htm](http://esecurityplanet.com/features/article.php/3878821/Strong-Passwords-May-Not-Be-All-Theyre-Cracked-Up-to-Be.htm)

---

### Post by Bachstelze on 2010-04-27
This article makes a capital mistake: just because strong password don't protect users against phishing attacks, it concludes they are useless. This is wrong. As anyone who actually operates a server could tell you, dictionary-based attack are still commonplace today. Dictionary-based and phishing attacks are different, and different measures must be taken to protect against them, but just because the latter gets in the news more often nowadays is not a reason to stop caring about the former.

Also see [this](https://blogs.apache.org/infra/entry/apache_org_04_09_2010). The Apache group mentions, as one of the mistakes that led to one of their servers getting compromized, weak enforcement of password-related policies.

> Theoretically, a &#8220;difficult&#8221; password will take longer for a software algorithm to unlock because it will have to go through more permutations to hit upon it&#8212;but how much longer? Computers are so fast these days,

The guy should learn his math is all I can say.

---

### Post by MasterNetra on 2010-04-27
> **Bachstelze said:**
> This article makes a capital mistake: just because strong password don't protect users against phishing attacks, it concludes they are useless. This is wrong. As anyone who actually operates a server could tell you, dictionary-based attack are still commonplace today. Dictionary-based and phishing attacks are different, and different measures must be taken to protect against them, but just because the latter gets in the news more often nowadays is not a reason to stop caring about the former.

Also see [this](https://blogs.apache.org/infra/entry/apache_org_04_09_2010). The Apache group mentions, as one of the mistakes that led to one of their servers getting compromized, weak enforcement of password-related policies.



The guy should learn his math is all I can say.

You didn't read it all the way apparently.

> 
...

To be fair, the conclusion to be drawn from reconsidering password security is probably not that strong passwords are entirely worthless. The problem is that our conventional wisdom still treats passwords like a first line of defense when, in fact, in today&#8217;s security environment, passwords should really be a last line of defense.


---

### Post by chessnerd on 2010-04-27
I can see the point they are trying to make, but they are under the assumption that most attacks nowadays are done far away by someone we don't know. How many of us are going to have our accounts attacked on a regular basis? Unless we are celebrities or someone important, not many. Yes, phishing scams happen and company's get password information stolen, but that doesn't mean that passwords are the "last line of defense" in all cases. 

Think of this: how many of us have children, parents, significant others, siblings, friends, co-workers, etc. who might try to get into one of our accounts some times? Probably most of us. In that case, a good password will always work. 

How many nosy parents are going to use a phishing scam to get into their daughter's Facebook? How many kids are going to break out their super-fast 8-CPU computer and brute force attack the child-block software? How many friends are going to try to hack an account and send fake e-mails after using a key-logger? In all those day-to-day cases a good password is the best way to stop someone.

---

### Post by stmiller on 2010-04-27
The 'secret questions' are more of a security concern. It's easy to find out basic info about a person and go through an online reset.

---

### Post by conradin on 2010-04-27
Every science Class Ive ever had has mocked Social Science. In the End, humans use computers. Social Attacks are based in a realm computer science doesn't want to go. 

I see strong passwords on servers without IDS's as an equation to who can crunch numbers fastest. How many times can I send out a series of login attempts before Im shut down? 1000 times a second? More?  Brute Force is a good book for anyone who wants to read about trials and tribulations in hacking the Data Encryption Standard.

---

### Post by kavon89 on 2010-04-27
> **Bachstelze said:**
> 

> Theoretically, a &#8220;difficult&#8221; password will take longer for a software algorithm to unlock because it will have to go through more permutations to hit upon it&#8212;but how much longer? Computers are so fast these days,


The guy should learn his math is all I can say.

Well, when you look at the number of possible keys along with the increasing speeds at which conventional computers can try to brute force the key, he's got a good point. The folks over at OpenBSD created eks-blowfish and bcrypt to combat this problem.

[**Paper**]("http://www.usenix.org/event/usenix99/provos/provos.pdf")

Abstract:
> Many authentication schemes depend on secret passwords. Unfortunately, the length and ran-
domness of user-chosen passwords remain fixed over time. In contrast, hardware improvements
constantly give attackers increasing computational power. As a result, password schemes such as the
traditional UNIX user-authentication system are failing with time.

This paper discusses ways of building systems in which password security keeps up with hardware
speeds. We formalize the properties desirable in a good password system, and show that the compu-
tational cost of any secure password scheme must increase as hardware improves. We present two al-
gorithms with adaptable cost - eksblowfish, a block cipher with a purposefully expensive key schedule,
and bcrypt, a related hash function. Failing a major breakthrough in complexity theory, these al-
gorithms should allow password-based systems to adapt to hardware improvements and remain secure
well into the future.

---

