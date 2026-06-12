---
title: "Password protecting files / folders"
date: 2006-04-04
forum: Server Platforms
---

### Post by Cyclops_ on 2006-04-04
Is there a way to password protect certain files or folders.  Say for example, I wanted to lock people out of gaining access to /etc/games, is there a way to require a password for everyone (including a sudo user) to get into that folder?

Thank you for any help!

---

### Post by LKRaider on 2006-04-04
You could try this how-to:
[Encrypted directory with EncFS](http://ubuntuforums.org/showthread.php?t=148600)

Sorry, but I don't know any other way to make this work (including sudo users), without using encryption.

---

### Post by Cyclops_ on 2006-04-04
What I want is to be able to grant another user rights to an existing folder or file but no one else, including myself and other sudoers...  and for the life of me i can't think of a good way to do it.  I could set the owner to the individual and set the permissions to 0755, but that doesn't work, cuz sudoers could still get to it.  I just want to lock everyone out but the one individual...

Does anyone know of a way to do this?

---

### Post by LKRaider on 2006-04-04
What I said, use encryption.

Changing ownership doesn't work, since the administrator (sudoers) can have access to everything.

---

### Post by Cyclops_ on 2006-04-05
OK... I will have to try that...  
 
Two questions on it, though.. 
Will it encrypt an existing directory, or do I have to start a new one?  
And would on encrypted directory affect programs that use the directory at runtime?
 
(Thanks for your help, By the way!)

---

### Post by LKRaider on 2006-04-07
I never really tried to encrypt a folder yet, so I'm not sure how to assist you on that.

You may have more luck asking directly at that thread.

---

