---
title: "SSH allowing login with partial passwords?"
date: 2007-10-19
forum: Server Platforms
---

### Post by brainyron on 2007-10-19
I just noted a disturbing behavior in the SSH server on my Ubuntu server (6.06 LTS/32bit).  For logins, only the first 8 characters of the password are taken into account for users with longer passwords.  This is a major concern.  Is there a way to correct this behavior?

---

### Post by tkharris on 2007-10-19
It sounds like your system is using crypt() for storing passwords instead of md5.  I don't know how this would be fixed in ubuntu, though.

---

### Post by brainyron on 2007-10-19
Well at least its a place to start.  Conversion might be difficult on this system though, there are hundreds of users...Please, anyone, any suggestions?

---

### Post by MJN on 2007-10-19
Have a look in /etc/shadow and see the encrypted passwords (after username:). If they start $1$ then they are using MD5 (which supports >8 characters), if not then it's something else (e.g. DES) which may not differentiate between >8 character passwords as tkharris says.

How have you created the user passwords? With passwd? I assumed MD5 was the default mechanism...

Mathew

Edit: In case you're using Webmin I see form the last post [here](http://ubuntuforums.org/showthread.php?t=488046) that it needs telling to use MD5 (with the MD5 Perl module) as opposed to DES. Of course, if you're not using Webmin...

---

