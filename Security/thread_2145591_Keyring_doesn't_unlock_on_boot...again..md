---
title: "Keyring doesn't unlock on boot...again."
date: 2013-05-15
forum: Security
---

### Post by mobrien118 on 2013-05-15
OK, so I have backups run every night. Great thing, right? Well, when it works.

If I'm out of town and I reboot my computer, when it starts the backup the screen just sits there and says "The login keyring did not get unlocked when you logged into your computer"...

Well, that's annoying!

Anyway, I tried to research this, and it looks like the keyring isn't unlocking. Suggestions for solutions all focus around going into "Passwords and Keys" and changing the keyrings around or changing the password on the keyring. Well, I only have 2 tabs showing up:
"GnuPG keys" and
"OpenSSH keys"

Nothing about "Default Keyring", "Login Keyring" or anything else.

I would desperately like to get this fixed as soon as possible as I'm going out of town again soon and would really like my backups working before I do.

Thanks in advance for any suggestions!

--mobrien118

---

### Post by mobrien118 on 2013-05-16
Did some more digging. Some strange things happening:
- In google chrome, when I go into "Saved passwords" nothing shows up, no matter how long you wait, however, saved passwords work (is this normal for Ubuntu?)
- There are 2 files in .gnome2/keyrings: login.keyring (almost 3 MB) and user.keystore (207k). Are these relevant?
- No passwords ever show up in Ubuntu's "Passwords and Keys" The middle box is always blank for either of the 2 selections I mentioned in my last post

Is my keystore "corrupted" somehow?

Some info:
- This installation has been upgraded all the way from 8.10, so there is a lot of "cruft"
- When I boot up, gnome-keyring-deamon (or something link that) uses 100% CPU for a couple of minutes

Any help would be very much appreciated. This seems like an interesting problem!

Thanks!

--mobrien118

---

### Post by mobrien118 on 2013-05-16
What? Nobody wants to take this on, get some street cred.?

This is an interesting problem! I have exhausted the limits of my knowledge of Ubuntu Keyrings (which is not much)!

I need an expert!

Thank you,

--mobrien118

---

### Post by mobrien118 on 2013-05-16
8-O

Amazingly, when I opened "Passwords and Keys" again, "Login keyring" was there!!!

So, the password was already set to the same as my login password, but I reset it all the same, rebooted, and came back in. No dice.

So I set it to have no password. Not exactly what i wanted, but I am up and running for the short term.

Does anyone know how to make it not ask, AND allow you to have a password?

P.S. The THIRD time I came into "Passwords and Keys" "Root CA Certificates", "Gnome2 Key Storage" and "User Key Storage" were all there now, too! Maybe if I just keep opening it up more keyrings will keep appearing. Who knows.

--mobrien118

---

### Post by ken78724 on 2013-09-03
mobrien, you must have solved the lockring problem. A friend got my acer to open using a routine he found on google. but then for me the lockring for unbuntu blocked my use and I sat the acer aside and used another laptop  & PC. 

this is a problem

---

