---
title: "Something interesting (no password root)"
date: 2005-11-22
forum: The Cafe
---

### Post by Matthias4444 on 2005-11-22
I accidentally found a rather large security hole.  If you type in "sudo su root" you will have root privlages without entering a password, this needs to be fixed I believe.  Also if you type "sudo sudo (command)" you can execute commands that usually require a password without needing one.

---

### Post by narcolept on 2005-11-22
This is only if you have previously sudo'd within x amount of time, kind of like how you don't have to type your password after the first time if you run a sudo command and then one immediately after. not sure what the default time is though, maybe someone else could shed some light on that.

---

### Post by Matthias4444 on 2005-11-22
ah thats good, i just tried it by closing the terminal and then reopening.  I'm glad that its not that big of a deal.

---

### Post by ubuntu27 on 2005-11-22
[QUOTE=narcolept]This is only if you have previously sudo'd within x amount of time, kind of like how you don't have to type your password after the first time if you run a sudo command and then one immediately after. not sure what the default time is though, maybe someone else could shed some light on that.[/QUOTE]

I heard that it's 6 min.

---

