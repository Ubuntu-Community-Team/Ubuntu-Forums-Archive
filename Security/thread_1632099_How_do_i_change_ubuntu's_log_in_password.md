---
title: "How do i change ubuntu's log in password?"
date: 2010-11-27
forum: Security
---

### Post by dogdo on 2010-11-27
Is it best to do this via the terminal or gui interface? 

does this mean that the home folder encryption password is the same as the old login password?

---

### Post by FuturePilot on 2010-11-27
System > Preferences > About Me
This also updates your encryption passphrase for your /home so there's nothing extra to do there.

---

### Post by irelandisruined on 2010-11-27
> **FuturePilot said:**
> System > Preferences > About Me
This also updates your encryption passphrase for your /home so there's nothing extra to do there.

I did this and now if i want to access the wireless passphrase for my home network i have to enter my old login password to access the gnome keyring. 

So i went to Applications>Accessories>Passwords and encryptions keys  and changed my login password to my new password and now the i dont get a prompt from gnome keyring when i access the wireless passphrase. Have i done this right? have i borked my system now?

---

### Post by FuturePilot on 2010-11-27
> **irelandisruined said:**
> I did this and now if i want to access the wireless passphrase for my home network i have to enter my old login password to access the gnome keyring. 

So i went to Applications>Accessories>Passwords and encryptions keys  and changed my login password to my new password and now the i dont get a prompt from gnome keyring when i access the wireless passphrase. Have i done this right? have i borked my system now?

Yes you did that correctly, but About Me should also update the gnome-keyring password. I'm not sure why it didn't for you. Did you change your password with another method previously?

---

### Post by cariboo on 2010-11-28
After you changed the login password, did you log out and then back in again? A password change only takes affect  after a log out.

---

