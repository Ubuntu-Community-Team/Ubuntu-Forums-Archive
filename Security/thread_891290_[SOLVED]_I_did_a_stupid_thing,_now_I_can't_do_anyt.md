---
title: "[SOLVED] I did a stupid thing, now I can't do anything! No longer administrator"
date: 2008-08-15
forum: Security
---

### Post by DSL5 on 2008-08-15
So i was talking with my friend back when I installed Ubuntu and he told me it was a good idea not to give myself full access to prevent messing up anything too seriously. Taking his advice closely, I went into **System > Administration > Users and Groups**, unlocked it, and unchecked the box next to Administer the System under the User Privileges tab in my account.

Now, I can't do anything! I can't unlock anything, I can't use sudo in the terminal, and I can't authenticate the use of anything!

I running Hardy with the latest updates.

If anybody knows a way to fix this and give myself administrator status again without re-installing the whole thing, I would greatly appreciate it!

---

### Post by aysiu on 2008-08-15
This should help you:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

After you fix it, vote for this Brainstorm idea:
[Idea #11107: Users and Groups should always make sure at least one user is in the admin group](http://brainstorm.ubuntu.com/idea/11107/)

---

### Post by lisati on 2008-08-15
Once you've got yourself an admin account up and running, you might want to set up a separate user account for day to day stuff.

---

### Post by DSL5 on 2008-08-15
worked like a charm! Thank you so much!
I will go vote right away!

---

