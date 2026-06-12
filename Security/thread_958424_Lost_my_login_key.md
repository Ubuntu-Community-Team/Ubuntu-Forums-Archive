---
title: "Lost my login key"
date: 2008-10-25
forum: Security
---

### Post by xdarkness2 on 2008-10-25
This will be difficult to translate but ill give it a try (dutch)

From the Applications (toepassingen) -> Tools (hulpmiddelen) -> Passwords and key's (Wachtwoorden en sleutels) 

In that application under edit -> preferences there is a 
default key called Login (Automaticly unlock when a user logs in)

I experimented with my wireless and i think i messed up, i deleted that key and am unable to replace / add it again... how do i fix this ?

None of my application passwords are able to be saved.. :( 

Greetz, Jan

---

### Post by lemming465 on 2008-11-15
I'm not sure, but I think if you delete *~/.gnome2/keyrings/login.keyring* and log out and in again you should get to make a new one.  Maybe save a copy in case I'm wrong.

---

### Post by mothraman on 2008-11-16
> **lemming465 said:**
> I'm not sure, but I think if you delete *~/.gnome2/keyrings/login.keyring* and log out and in again you should get to make a new one.  Maybe save a copy in case I'm wrong.
I have the same problem. I have seen reference to ~/.gnome2/keyrings in other posts, but I can't find any such directory...even searching on "gnome2" and on "keyrings" with "view hidden files" checked.  Any suggestions?

---

### Post by Dave_Connor on 2008-11-16
try ls -A | grep .gnome2 in your home folder.

---

### Post by mothraman on 2008-11-16
Thank you...but I found it: "Applications/Accessories/Passwords and Encryption keys."

Click on Edit then Preferences, then highlight the key that's there and delete it.

Wireless then asks for the security key, enter it, you get a password dialog, leave it blank and tell the warnings you really mean it.

Wireless connects.

No need to do this manually by searching through directories.

---

