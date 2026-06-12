---
title: "Can I change the location of where my logs are saved?"
date: 2013-10-31
forum: Security
---

### Post by matanzatz on 2013-10-31
Hello everyone!
Im new here and I need some help.

Im trying to harden my ubuntu 12.04 system and among other stuff, I want to change the location of where the logs are saved.
I want to create an encrypted folder somewhere in the system and save my logs there. 

Anyone has an idea how can I do that?

THANKS in advance.

---

### Post by Shrek01 on 2013-10-31
Fastest and easiest way would be to move your /var/log to your encrypted partition/folder and create a symbolic link to it:
ln -s /encrypted/var/log /var/log

---

### Post by matanzatz on 2013-10-31
Thanks for the reply!!
Yet, The reason I wanted to move where the logs are saved is because Im preparing for the worst - lets say that someone hacked or something into my system and now he can get to the logs because there's this shortcut to the new folder - its still in the "default" place so it wont help me to "hide it"... 
one more thing is that i tried doing what you said using Cryptkeeper - but the ubuntu gives me "permission denied" error while trying to move the logs into the encrypted folder because you need to type the password for the folder...

---

### Post by cariboo on 2013-10-31
The problem with moving the log files to an encrypted folder, is that it has to be decrypted when ever you are using the system, as log files are constantly being updated as you use the system.

---

