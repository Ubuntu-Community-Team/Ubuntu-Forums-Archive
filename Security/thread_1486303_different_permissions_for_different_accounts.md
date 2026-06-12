---
title: "different permissions for different accounts?"
date: 2010-05-17
forum: Security
---

### Post by id10twork on 2010-05-17
I have upgraded to Lucid, but was having the same issues on Karmic. I made a 2nd user acct we'll call X and we'll call the original acct Y. **_All of these issues only happened after creating X_**.

_On X I have_: sound
_Things wrong with X_: I don't have the ability to modify any folders (even ones that are made from X's acct), I can't change the password or even access the Users and Groups, I can't modify any browser settings in Firefox but can on Chromium, the option for wireless is completely gone

_On Y I have_: the ability to access users and groups, the ability to modify all folders on either acct, the ability to change any settings on anything
_Things wrong with Y_: no sound (doesn't even show the driver, but the driver is there on X's acct), wireless is completely gone (just like X's acct), even though I can access Users and Groups I cannot modify anything about X's acct

My first thought was to completely delete X since that's when all the problems began, but I'm afraid that since X seems to have "stolen" my sound card, that will be lost forever. I am also afraid that since neither account has wireless deleting X might hinder ever getting it back.

---

### Post by Jakob Lundberg on 2010-05-18
With user Y you should be able to edit the access in Users and Groups.
This is because the original user should be part of the admin group giving it sudo rights.

You can check who has sudo rights by looking at the admin group in Users and Groups or at the line starting with admin in /etc/group

There appears to be some problems with Xs home folder
Make sure it is owned by X and the owner has read and write access.
You can list this with ```
ls -l /home/
```

---

