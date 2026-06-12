---
title: "Getting a users password"
date: 2010-08-30
forum: Security
---

### Post by ncc1701 on 2010-08-30
I need to be able to capture a users password when they login. I am well aware of the security issues with this and I'm ok with this.

We run a call center and I am working on migrating from windows to Kubuntu for the callers. It's policy that all callers must report their password to me, so I already know of everyone's password. There has to be some variable/script that I can "hack" to get the password they typed in to the login screen.

What I'm trying to do is that when a user logs in in for the first time, their profile is automatically created and set up. Setting up network drives, email, pidgin (which the password is stored in plain text anyway, so forget about security on that one), web apps, etc. 

I've search all over trying to find information on how to capture a users password and all have been responded with the usual lecture on why you shouldn't do this. So I've heard it all before and I know of the risks. Like I said, I already have the callers password on file. If I could capture it, I wouldn't have to manually setup each profile every time we get a new caller, which is often since turnover is quite high in call centers.

I have already considered a NAS, but that only solves part of what I'm trying to do.

So please respond if you have real help or suggestions, rather then posting another lecturer :)

Thank you.

---

### Post by wojox on 2010-08-30
Do your users know you know their passwords?

---

### Post by anomie on 2010-08-30
[QUOTE=ncc1701]What I'm trying to do is that when a user logs in in for the first time, their profile is automatically created and set up. Setting up network drives, email, pidgin (which the password is stored in plain text anyway, so forget about security on that one), web apps, etc.[/QUOTE]

Automatically create their profile using a "dummy" (e.g. pseudo-random) password, and provide them with instructions on how to change it if they'd like. 

Or, if they must use a password that's already been configured in advance on the backend components (i.e. CIFS shares, email), then have a handy script available for them to run which prompts them for their password and takes care of profile creation. 

One more thing: if you're encouraging users to have the same authentication credentials across OSes / apps, you might want to give your security policies a serious look.

[quote=ncc1701]I've search all over trying to find information on how to capture a users password and all have been responded with the usual lecture on why you shouldn't do this.[/quote]

Honestly now, why do you think that may be? Do you suppose your question / grasp of the problem inspires confidence that you're going to carefully handle auth credentials?

---

### Post by dv3500ea on 2010-08-30
You can't view someones password but you can change it to something that you know.
```
man passwd
```

---

### Post by scorp123 on 2010-08-30
This all just sounds soooooo wrong. Spying on user passwords ... hellloooo??? :confused:  Do you work for the Chinese or North Korean government?? :confused:

---

### Post by Iowan on 2010-08-30
Closed for review.

---

