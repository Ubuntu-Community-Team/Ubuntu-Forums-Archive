---
title: "change the location of the keyring files where passwords are stored"
date: 2011-06-10
forum: Security
---

### Post by luca5am on 2011-06-10
Hi,

I'd like to change the location of the keyring files where passwords are stored, is that possible?

Thank you

---

### Post by cariboo on 2011-06-10
If you place the file in any other directory besides your home directory, things may not work. With proper directory permissions and safe computing habits, they should be safe enough where they are.

---

### Post by luca5am on 2011-06-10
Well I thought that if there was a setting for specifying where the keyring files are located it wouldn't be a problem to put them somewhere else. It just seemed to me that just the one layer encryption might not be ultra-safe. I'm not the only one using the computer (although I am the only one to have the keyring password)

Thank you anyway.

---

### Post by cariboo on 2011-06-10
If you aren't the only one using the computer, create a separate account for the other user. Check to make sure the permissions on ~/.gnome2/keyrings, in your home directory, is set to at least 700, that way only you and root can access the directory.

---

### Post by luca5am on 2011-06-10
Yeah that is how it is set up :)

---

