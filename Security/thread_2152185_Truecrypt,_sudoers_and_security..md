---
title: "Truecrypt, sudoers and security."
date: 2013-06-07
forum: Security
---

### Post by eddie3000 on 2013-06-07
Ok! Hello everybody, and good morning.

I am using truecrypt for fun really on one of my drives. I was bothered by the system always asking for administrator password for mounting the drive after entering the truecrypt password. I found the solution by editing the sudoers file. But I have found two slighlty different methods on the internet, both of which edit the sudoers file, but in different ways. 

One method adds a line to  my /etc/sudoers file:
*username ALL=(root) NOPASSWD:/usr/bin/truecrypt*

The other method (the one I am currently using) implied creating a new group called truecrypt from the user and groups configuration window in the system administration menu. After that it adds this to my sudoers file:
%truecrypt* ALL=(root) NOPASSWD:/usr/bin/truecrypt*

Both seem to work. But which one is best? What is the difference? Which is more secure? I always log on as the same user, and nobody else uses my laptop (well... I think nobody else uses my laptop ;-)

Thanks.

---

### Post by Soul-Sing on 2013-06-07
You can add truecrypt to "users-groups"
and add: %truecrypt ALL=(root) NOPASSWD:/usr/bin/truecrypt
to the sudoers file. thats how I do it.
Interesting to here if its "alright".:)

---

### Post by eddie3000 on 2013-06-07
Yes, me too. But is the first method better or worse? Do both disable the password for a given user? Does the second disable the password for other users too or only the one's enables in user-groups?

---

### Post by markbl on 2013-06-07
I'm going a bit off topic here but although everybody talks about Truecrypt I find that most really just want one encrypted folder under which they can put all sensitive files and folders. For this the age-old encfs utility works best. No mucking around with partitions, sizes, root user, etc. Simple and works well. I have used it for years.

---

### Post by eddie3000 on 2013-06-08
Hello markbl! I use truecrypt so I can mount the fs with windows too (dual boot). I'm not doing that much for security reasons, but entertainment. If I didn't use windows at all, mint mate (and ubuntu) already offer disk encryption that I think is equally good. I might look at your option using encfs one day, for fun.

But going back to the first question, what is the difference between the two methods in the first post? Anyone? ):P

---

### Post by paperplate9 on 2013-06-09
More secure? The first. Only a single user can elevate to root to execute truecrypt. Second mechanism allows any number of users (as long as they belong to truecrypt).

In practice, it probably doesn't matter. However, if someone can sneak their way into adding a user to the truecrypt group, they probably already have root & wouldn't need to be modifying sudoers...that is unless they want to drop an egg to get into your encrypted drive as non-root later.   

E.g., someone could create a user named "truecrypt" & add it to the truecrypt group. If you're not careful & you happen to look at auth logs every once in a while, you might not catch it, as it's common to have services be run as a user with the same name as that service.

---

### Post by eddie3000 on 2013-06-10
Thank you very much paperplate9 for your answer. What you said seems to make sense. According to you I'm using the less secure method. I'll have to change over it then. 
Now I have one more question if it's ok. Is the user-group window meant for managing large numbers of users easily? Would it be safer to add as many lines to the sudoers file as users instead of a group? 
THanks again.

---

### Post by Soul-Sing on 2013-06-11
thx paperplate9

---

