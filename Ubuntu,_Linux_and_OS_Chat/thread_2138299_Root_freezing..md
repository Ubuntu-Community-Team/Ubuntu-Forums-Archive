---
title: "Root freezing."
date: 2013-04-23
forum: Ubuntu, Linux and OS Chat
---

### Post by Nicbi on 2013-04-23
Hello,

I would like to know, if there would be a way to lock a root account (for special uses that don't need further configurations, nor installations). That is : do some think (encrypting it or whatever), so that an intruder, or even the regular user, would never be available to access it, and this by ane mean (this would be a sort of root freezing).

Nicolas

---

### Post by deadflowr on 2013-04-23
The root account, by default is already locked.
What you could do is a create a normal non-admin user, then delete the admin user.

---

### Post by CharlesA on 2013-04-23
> **deadflowr said:**
> The root account, by default is already locked.
What you could do is a create a normal non-admin user, then delete the admin user.

It would be easier just to remove them from the sudo group instead of deleting them as that can screw up permissions something fierce.

Although, with a locked root account (default) and no one with sudo access = who will be doing updates? Hmmm....

---

### Post by kuifje09 on 2013-04-23
I don't get this story, but deleting the root account is not a wise decission. You can delete the root-home dir. but why?
But the root-id is realy needed, if you delete is I bet your system is dead. ( would be nice if someone can test/verify )
And a user with admin-right is something else then root itself.

---

### Post by deadflowr on 2013-04-23
> **CharlesA said:**
> It would be easier just to remove them from the sudo group instead of deleting them as that can screw up permissions something fierce.

Although, with a locked root account (default) and no one with sudo access = who will be doing updates? Hmmm....

That's probably easier.
This thread actually made me wonder if you could make an entire directory immutable or not, which would probably make it even more locked down.

> **kuifje09 said:**
> I don't get this story, but deleting the root account is not a wise decission. You can delete the root-home dir. but why?
But the root-id is realy needed, if you delete is I bet your system is dead. ( would be nice if someone can test/verify )
And a user with admin-right is something else then root itself.

Locking accounts and deleting accounts are different things.

Though, if you really want a super safe machine, then don't connect it to the internet.

---

