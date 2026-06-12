---
title: "Why not use nopasswd in sudo"
date: 2007-01-12
forum: Server Platforms
---

### Post by adaniels on 2007-01-12
Hi,

Sudo asks for you password when doing an administrative task by default. What are security risks of using the nopasswd flag? Especially since gksudo caches my password anyway. 

It seems that if anyone getting into my computer as my user, would already have my password. The only risk I can think of, involves someone sitting behind my computer while I'm logged on. But that issue is better solved by letting the screensaver lock the screen so they don't have access at all.

Thanks for replying,
Arnold

---

### Post by Moldz on 2007-01-12
Let's suppose there is a security hole in your favorite app.  I'll use Firefox as an example, but really it could be anything.  Suppose this attacker can trick Firefox into running any program he wants on your machine by showing it a "special" webpage.  He could do some damage to your user and your files in the home directory, but he can't easily take over the entire box.  That's because he needs your password to do anything important as root.  Unless you don't require a password.

One day you have one too many burritos.  As you run to the bathroom clutching your ***, some jerk realizes you did not lock your screen.  He opens up a term window and types "sudo rm -rf /".

---

