---
title: "Locking Down 10.04"
date: 2011-07-25
forum: Security
---

### Post by IWantFroyo on 2011-07-25
I know that Ubuntu doesn't need antivirus, and a firewall isn't imperative.

I would, however, like to know what I could do to make my Lucid box a bit more secure, as I'm using it as my work system. 

So... Any firewall tips or anything?

---

### Post by iavor on 2011-07-26
Another way to secure your box is to encrypt your home folder or even better "full disk encryption"

Use strong passwords preferably generated, always lock your pc when you are not around. You could at least enable ufw.

P.S. i'm not sure that ubuntu supports full disk encryption but truecrypt does and is a great tool.

---

### Post by nd456 on 2011-07-26
if you don't wanna be tracked get tor
get a randomly generated password with caps numbers and symbols
password protect your BIOS
make your screen saver setting stricter 
(Ubuntu is pretty DAMN secure without any configuration)

---

### Post by Thewhistlingwind on 2011-07-26
Noscript.

The must-have firefox addon.

---

### Post by bodhi.zazen on 2011-07-26
1. Read the security sticky.

2. Learn to use apparmor.

---

### Post by IWantFroyo on 2011-07-26
Thanks for all the great replies! :)

---

### Post by doas777 on 2011-07-26
as you start working throught he security documentation and advice from around the web, you will notice that "secure" is a word with many meanings. there are many things I can do to lock down ubuntu that may or may not make me more secure, depending on how the system is used, and what attack vectors I am most concerned about. 

Encryption for instance is a two-edged sword. it can help secure systems that would otherwise be insecurable (field staffer laptops, shared computers, evil roommates), but it may also lead to scenarios where your data is damaged and cannot be recovered. if you lose your keys, then there is little hope you will ever retain your data.
to me, being secure implies that my data will never become inaccessible to me, so encryption in low-risk facilities is more of a danger than a boon. use encryption with a scaple, not a sledghammer (eg: full disk encryption).

never underestimate the value of physical security, as it allows all the other layers of security to function correctly. if the box is not physically secure, then non of the other security functions you implement will have any real meaning.

---

