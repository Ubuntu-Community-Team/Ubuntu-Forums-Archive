---
title: "Can I disable the keyring for Ubuntu One?"
date: 2010-12-08
forum: Ubuntu One (CLOSED)
---

### Post by xinix on 2010-12-08
I'd like to try to use Ubuntu One to keep certain files backed up for my Mythtv Box and keep them synced with a folder on my laptop.  This way they are backed up and I don't need to remember each one when I re-install my system; and I can edit the files on the laptop and have the changes sync to the Mythbox.

It would be nice if I could have Ubuntu One run without having to unlock the keyring when the system starts up.  This is because I don't want to have to go looking for a keyboard and mouse to plug into the computer just to get Ubuntu One running.

I guess an alternative would be to launch U1 through an ssh shell. 

So, can I disable the keyring and have U1 run without requiring me to use a keyboard, or what ssh command can I use to get U1 running?

Thanks

---

### Post by balise on 2010-12-31
Me too.  Hate the keyring.  Is it necessary for Ubuntu One?

---

### Post by balise on 2010-12-31
Or, what does using ssh to connect to U1.  *Sounds* useful, but what would you do?

---

### Post by areteichi on 2011-01-01
If I understand your concern correctly, you can disable the keyring simply by leaving the keyring password empty. I guess that would disable keyring for all applications but at least you won't be prompted again.

---

### Post by balise on 2011-01-01
> **areteichi said:**
> If I understand your concern correctly, you can disable the keyring simply by leaving the keyring password empty. I guess that would disable keyring for all applications but at least you won't be prompted again.

thanks very much.  This *is* effective for when I want to sign on without interaction, but DOESN't work (I think) for Ubuntu One.  I guess, for Ubuntu One, that you have to get into the damn keyring thing.  

Linux is getting far too complicated and things like printing (cups) and sound (pulseaudio) jut prevent it from being the least bit like a Windows replacement.  IMO.

---

### Post by areteichi on 2011-01-01
I don't know if I experience the same issue. I know I never type in a password for Ubuntu One to start working in the background. It just starts automatically and synchronizes without any authorization.

---

