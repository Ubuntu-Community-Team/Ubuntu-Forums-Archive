---
title: "Users can access ant directory they want on PURE-FTPD"
date: 2006-12-01
forum: Server Platforms
---

### Post by pzhukke on 2006-12-01
Hi!
I've just installed Pure-ftpd with MYSQL Auth... and it's works fine  

BUT!
When I login to any user, I can get access to any directory I want... Such as te root directory on my server ](*,) 
(I only push the "Up one directory" -button)

I thinks it a setting somewhere as I havent fixxed, so if you had a similar problem, or know how to fix it;
PLEASE PLEASE PLEASE reply on this thread :-D 

Greetings
Eric

---

### Post by Compact on 2006-12-01
You have to chroot everyone. Create a text file in /etc/pure-ftpd/conf named ChrootEveryone and write "1" indside it.

---

