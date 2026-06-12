---
title: "[SOLVED] All users can access /sbin"
date: 2008-03-31
forum: Security Discussions
---

### Post by samona on 2008-03-31
How come /sbin can be accessed by all users by default.  Shouldn't only admin account be able to access /sbin?

---

### Post by p_quarles on 2008-04-01
I'm not sure I understand the question. While all normal scripts in /sbin are set to be executable by all users, any root functions within those scripts will still require root privileges in order to complete successfully. 

"Access" is too broad a term to describe the way that *nix permissions work. There are too many layers of control for that to be a meaningful term by itself.

---

### Post by brian_p on 2008-04-02
> **samona said:**
> How come /sbin can be accessed by all users by default.  Shouldn't only admin account be able to access /sbin?

In a terminal type /sbin/ldconfig and /usr/sbin/visudo. What do you observe? Try all the commands in those directories.

(/sbin/ifconfig works for a user, you say? Are you sure all the options work?)

---

### Post by samona on 2008-04-04
/sbin/ifconfig work for all users but /usr/sbin/visudo only works for root.

---

### Post by p_quarles on 2008-04-04
> **samona said:**
> /sbin/ifconfig work for all users but /usr/sbin/visudo only works for root.
Some arguments for ifconfig should work for everyone, but making changes to interfaces should only work for root.

---

### Post by samona on 2008-04-04
oh ok, yeah i just tried ifconfig eth0 down and it said Permission denied.  Thanks all!

---

