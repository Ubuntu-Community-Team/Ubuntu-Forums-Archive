---
title: "Users and Groups should always make sure at least one user is in the admin group"
date: 2008-07-13
forum: Ubuntu Brainstorm
---

### Post by aysiu on 2008-07-13
How many times have we seen new users accidentally remove themselves from the *admin* group when they're the only user on the Ubuntu installation?

Here's an example: [im locked out as administrator](http://ubuntuforums.org/showthread.php?p=4876042)

The problem is that they're using the GUI (Users and Groups) to remove themselves, but the only way to get themselves back into the *admin* group is [using recovery mode and terminal commands](http://www.psychocats.net/ubuntu/fixsudo).

Nothing should stop people from using terminal commands and config-file-editing to remove themselves from the *admin* group if they're the only *admin* user, but the GUI (Users and Groups) should not allow you to uncheck yourself from administering the system if you're the only person left in the *admin* group.

Does this make sense?

If so, vote it up at Brainstorm. If not, vote it down.
[Idea #11107: Users and Groups should always make sure at least one user is in the admin group](http://brainstorm.ubuntu.com/idea/11107/)

---

### Post by estyles on 2008-07-13
Absolutely.  It's a bad idea to stop Linux users from ruining their system, but it's a good idea to make it harder for us to ruin our system.  Similarly, I'm against putting a shortcut on the desktop to "format active drive".

---

### Post by aysiu on 2008-07-13
Yes, that's something I want to be clear about.

I'm not proposing we stop users from removing the last *admin* user from the the *admin* group. I'm suggested this just not be allowed to be done through the GUI.

If people want to use the command line or /etc/sudoers to lock themselves out, they'd still be able to do so.

---

### Post by smartboyathome on 2008-07-14
I also agree. Wouldn't this be more of a suggestion for GNOME to impliment, though? They are the ones who makes the Users and Groups GUI. ;)

---

### Post by aysiu on 2008-07-14
> **smartboyathome said:**
> I also agree. Wouldn't this be more of a suggestion for GNOME to impliment, though? They are the ones who makes the Users and Groups GUI. ;)
So this is an upstream bug? It's kind of hard for me to tell. A lot of distros that use Gnome do not even implement *sudo*.

---

### Post by smartboyathome on 2008-07-14
> **aysiu said:**
> So this is an upstream bug? It's kind of hard for me to tell. A lot of distros that use Gnome do not even implement *sudo*.

I think it would be. It could be implimented possibly using policykit or something similar (PolicyKit is what makes sudo not necessary for GNOME, I think).

---

