---
title: "Keyring password issue"
date: 2009-03-29
forum: Security
---

### Post by patman0623 on 2009-03-29
I recently changed my password on Ubuntu because someone who I did not trust had access to it. However, when I sign in, my network manager cannot access my wireless router without a password; I get this message: 
[IMG]http://i42.tinypic.com/2le1hsh.png[/IMG]

The password it requires is my *old* password. It didn't do this before. How can I change the password for my network manager so I don't see this again? And is this a bug or a (poorly designed and implemented) feature?

---

### Post by hyper_ch on 2009-03-29
how about channging the password for the keyring?

---

### Post by patman0623 on 2009-03-29
> **hyper_ch said:**
> how about channging the password for the keyring?um, that's the million dollar question.

---

### Post by XPM on 2009-03-29
Yeah, got the same problem here

---

### Post by XPM on 2009-03-29
> **patman0623 said:**
> um, that's the million dollar question.

Applications > accessories > Passwords and encryption keys

Edit > Preferences

Login : Automatically unlocked when user logs in

Change/Unlock Password (Button)

-

That did the trick for me.
Cheers!

---

### Post by Darbre on 2009-05-25
[QUOTE=XPM;6977511]Applications > accessories > Passwords and encryption keys

Edit > Preferences

Login : Automatically unlocked when user logs in

Change/Unlock Password (Button)

-

That did the trick for me.
Cheers![/QUOTE




My Jaunty doesn't seem to follow the above instructions. After opening Edit > Preferences  where do I login?


Thanks

---

### Post by fballem on 2009-05-25
> **Darbre said:**
> 

My Jaunty doesn't seem to follow the above instructions. After opening Edit > Preferences  where do I login?


Thanks

Accessories > Passwords and Encryption Keys.

Once you have that open, select the Passwords tab (see attached Screenshot-Passwords and Encryption Keys). Right-click on the entry marked passwords and select Change Password from the menu. You'll get a panel to change the password (see attached Screenshot-Change Keyring Password). Use the old password and change the new password to match your login password. Select the Change Button and the Close button and you should be good to go.

---

### Post by Darbre on 2009-05-25
TYVM fballem. That worked\\:D/

---

