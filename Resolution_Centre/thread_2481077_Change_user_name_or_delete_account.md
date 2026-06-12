---
title: "Change user name or delete account"
date: 2022-11-18
forum: Resolution Centre
---

### Post by ygoe on 2022-11-18
Cross-posting [this]("https://ubuntuforums.org/showthread.php?t=2480163") here as suggested by the FAQ.

Hello,

after lots of trouble with the forum login through the Ubuntu One  account which caused lots of trouble because I have a Launchpad account  from 50 years ago, I finally managed to log in here again. It seems like  I already have an equally old account in this forum, with completely  outdated user name, e-mail address and other data. The data provided  through SSO seems to be completely ignored here. E-mail address, user  name, none of the shared information is actually used by this forum.  Then why do I need a SSO at all? This was already a very much  frustrating user experience.

Now I was looking into updating this account but the user name doesn't  seem to be changeable. Since I'm not too much interested in my old posts  here, I might as well just delete the account and create a new one. But  that also doesn't seem to be possible.

So what should I do? Delete and create a new Ubuntu One account? I'm not  really sure why I have that anyway. I'm using Ubuntu on servers and IoT  devices but don't really need this account. Sometimes I have questions,  so I need an account for this forum, but nothing else, really. That SSO  thing seems overcomplicated, and terribly integrated.

---

### Post by coffeecat on 2022-11-18
What is it you want? Rather than diluting your post with grumbles about SSO, please state clearly what it is you want a forum admin to do for you. For instance:

Do you want to recover your "equally old account"? if so, what is its username? Link to profile page?

Do you want to an admin to change your username for this account?

Something else?

> **LonelyPixel said:**
> Delete and create a new Ubuntu One account?

Do not do that, please. If you do and log into the forum with it you will simply create yet another forum account, complicate everything, and cause unnecessary work for the volunteer staff here.

And, by the way, SSO was forced on us years ago. The forum admins dislike it as much as anyone here and have no control over it. Complaints directed to the forum staff about it merely alienate said forum staff.

---

### Post by ygoe on 2022-11-18
Sorry, I didn't know the forum operators also don't like how their system works.

Please change my forum name to "ygoe", that is the user name in the SSO account anyway and should have been picked up by the forum.

Can I change my e-mail address here? It wasn't picked up from SSO. What's the password field in my forum settings for? Should I care about that?

I'm curious, how could a company force an independent volunteer community to use their authentication system?

---

### Post by coffeecat on 2022-11-18
> **ygoe said:**
> Please change my forum name to "ygoe"

Done. We usually ask for 3 alternatives in case your first choice is already taken. Fortunately, it was available. 

> **ygoe said:**
> that is the user name in the SSO account anyway and should have been picked up by the forum.

The system worked exactly as required. You created your account, and chose the original username, in 2010, several years before SSO was introduced. The system only creates a username based on the SSO username when a new forum account is being created. Where accounts predate first login with SSO, the match is made on email and the system respects and retains the pre-existing forum username.

> **ygoe said:**
> Can I change my e-mail address here? It wasn't picked up from SSO.

Yes, you can. You are at liberty to change your email in your forum account and in your SSO account as many times as you want, and they no longer have to match. After initial email matching SSO accounts and forum accounts are linked by means of a unique openID string. You might want changes to your SSO email mirrored in your forum account. Others do not. That is why the forum email is not automatically changed. Please do not assume that features that do not accord with your preferences are flaws. 

> **ygoe said:**
> What's the password field in my forum settings for? Should I care about that?

You can ignore that. The forum password field is kept for certain staff functions. It is irrelevant to non-staff users, and all such passwords were randomised some years ago. 

> **ygoe said:**
> I'm curious, how could a company force an independent volunteer community to use their authentication system?

It's Canonical's forum. They fund it. They provide the servers. Their sysadmins do the sysadmin work. They can do what they want. And, despite the staff's reservations about certain aspects, it provides far better security than the native vBulletin login functionality.

---

