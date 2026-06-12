---
title: "Keyring on Auto Login"
date: 2010-06-16
forum: Security
---

### Post by tealio on 2010-06-16
I'm on 10.04...

Is there a way to make autologin give the keyring credentials also? 

I am trying to use the remote desktop feature to manage a "media" PC... I have set the machine to autologin, but in order to access it using Remote Desktop i have to put in the password.

I have read some posts about using libpam-something-or-another... it doesn't seem to solve the issue with auto login... 

On a normal login, i don't have to give any other passwords.  
If it's going to automatically log me in, why wouldn't it work just like a "normal" login? 

I just want to be able to reboot remotely and still access using Remote Desktop

I am aware of the many vnc packages, but i need to access the same screen as the terminal so i can start a movie playing remotely and it plays on my TV...

---

### Post by tealio on 2010-06-16
I found a similar problem in another thread... of course i found it AFTER i posted... here's the solution anyway

Applications >> Accessories >> Passwords And Encryption Keys

Right Click "Passwords: login"

Select "Change Password"

Change the password to a blank password

While this leaves my passwords unencrypted, it's not that big a deal on that machine.

I would *N*O*T* recommend this on a mission critical machine...

---

