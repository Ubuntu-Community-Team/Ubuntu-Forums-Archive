---
title: "any known webmail compatible with mobile devices?"
date: 2019-03-31
forum: The Cafe
---

### Post by marchello_lippi2 on 2019-03-31
Hi all, 
I use squirrelmail and it works fine for me. Ok, well, it opens folders with a looot of emails too long, but it's rather normal. I use to separate those huge folders into few smaller to avoid this kind of stuff. 
I would say, I'm pretty satisfied with squirrelmail in general.

Now I'm talking about using it from my phone. Squirrelmail just does not do anything special for mobile, it displays everything as usually. Imagine reading long email and scrolling text from left to right... even turned screen horizontally... 
As far as I know, I can install few different webmails on my vps and they all can theoretically look into the same mailbox files. Sure it will be better to check with separate test-user so that it will not do anything wrong, also better to use different vps (I got few). 

Though before I start checking other products, I'd like to ask Dear All, maybe someone already went this path before. Could you please recommend some webmail that is mobile-friendly? 
Thanks!

---

### Post by coffeecat on 2019-03-31
Not an Ubuntu support question.

*Thread moved to **The Cafe**.*

---

### Post by thenailedone on 2019-03-31
Anything by Google integrates well with Android... so Gmail is an option.

---

### Post by TheFu on 2019-03-31
> **marchello_lippi2 said:**
> Hi all, 
I use squirrelmail and it works fine for me. Ok, well, it opens folders with a looot of emails too long, but it's rather normal. I use to separate those huge folders into few smaller to avoid this kind of stuff. 
I would say, I'm pretty satisfied with squirrelmail in general.

Now I'm talking about using it from my phone. Squirrelmail just does not do anything special for mobile, it displays everything as usually. Imagine reading long email and scrolling text from left to right... even turned screen horizontally... 
As far as I know, I can install few different webmails on my vps and they all can theoretically look into the same mailbox files. Sure it will be better to check with separate test-user so that it will not do anything wrong, also better to use different vps (I got few). 

Though before I start checking other products, I'd like to ask Dear All, maybe someone already went this path before. Could you please recommend some webmail that is mobile-friendly? 
Thanks!

I self-host email using Zimbra, but use thick clients for Android - K9-Mail is what I've been using for about 8 yrs using standard protocols into Zimbra.
IMAPS: 993/tcp
SMTP: 587/tcp

There is a mobile interface for Zimbra - I never use it.  There are simple HTML and full Ajax interfaces too. You can choose between those at login.  They added 2FA support in 8.7, if you care about that.

---

### Post by marchello_lippi2 on 2019-03-31
I believe there are plenty of email android apps, it is way to go for those who are willing to open imap port of self-hosted system to the world. In my case I would rather use webmail. BTW, looking into horde/imp solution [https://www.horde.org/apps/imp/](https://www.horde.org/apps/imp/) 
(found pretty good review on reddit).

---

