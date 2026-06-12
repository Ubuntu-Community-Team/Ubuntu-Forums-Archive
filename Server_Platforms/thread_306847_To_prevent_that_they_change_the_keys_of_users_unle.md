---
title: "To prevent that they change the keys of users unless is root"
date: 2006-11-25
forum: Server Platforms
---

### Post by mogotocoro on 2006-11-25
Hello friends I have installed ubuntu in my machine and wanted that nobody can change the user key to him unless he is the bony administrator root, exists an option to block the change of the keys of inision of session of the users, who those that fence to enter cannot change that key and siempr etengan the same one? thanks

---

### Post by MJN on 2006-11-25
Let me guess, you fed that through a something-English translator? Unfortunately it didn't do a very good job... ;)

Can you try and re-phrase it? (Unless someone else has guessed the issue)

Mathew

---

### Post by drphilngood on 2006-11-25
Are you asking if installing a firewall will keep someone from rooting your PC?

---

### Post by mogotocoro on 2006-11-25
No, I want to know since the user would do so that a user of ubuntu cannot change his key of session, but only root.

---

### Post by MJN on 2006-11-26
It's still not very clear. What's your native language? May I suggest posting to one of the groups at [https://wiki.ubuntu.com/LoCoTeamList](https://wiki.ubuntu.com/LoCoTeamList) ?

Mathew

---

### Post by gnaunited on 2006-11-26
I think he wants to prevent password changes on user accounts.

He only wants the root user to be able to change the user password.

---

### Post by mogotocoro on 2006-11-26
Exact that what I want, my language is Spanish but the forums in that language do not accede the people

---

### Post by MJN on 2006-11-27
Okay, in that case simply run **chmod 0700 /usr/bin/passwd** and this will stop anyone but root executing the passwd command.
 
Mathew

---

### Post by mogotocoro on 2006-11-27
Thanks and how would make him to reestablish it again? originally it has permission - rwsr-xr-x but has a “s” never seems me strange because had seen that permission and when it change to 777 does not work, what I do?

---

### Post by MJN on 2006-11-28
The 's' represents *setuid* i.e. when executed the process will take on the identity of the owner (root in this case).
 
To restore the orginal permission use chmod 4755 /usr/bin/password.
 
I appreciate that me telling you these numbers may solve this issue but doesn't teach you much so if you're interested in working out the 'whys' then check out the following links (there's no point us reinventing the wheel here).
 
[http://en.wikipedia.org/wiki/Chmod](http://en.wikipedia.org/wiki/Chmod)
[COLOR=#bd5900][http://en.wikipedia.org/wiki/File_system_permissions](http://en.wikipedia.org/wiki/File_system_permissions)[/COLOR][]("http://en.wikipedia.org/wiki/Chmod")
 
Mathew

---

