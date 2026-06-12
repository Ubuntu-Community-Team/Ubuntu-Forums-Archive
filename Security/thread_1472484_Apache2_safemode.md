---
title: "Apache2 safemode"
date: 2010-05-04
forum: Security
---

### Post by noone123 on 2010-05-04
Hi!
I'm using Ubuntu x64 (dunno which version, but I don't think it matters) and I'm concerned about security with PHP.
I remember using lighttpd and I had some mystic configuration and the secuirty was perfect for me - if one website gets hacked then the others are still safe (kinda).
Now with apache2 if I enable safemode I'm still able to go outside web directory and actually I can go really far untill user/group matches.
I tested the system with r57shell and I was able to mess up other websites.
Is there a way to disallow access to other websites?

---

### Post by cariboo on 2010-05-04
This looks like an ownership and permissions problem, what user and group own the directories?

---

### Post by noone123 on 2010-05-04
I tried some variations.
One is a user/www-data, another one is www-data/www-data.

---

### Post by cariboo on 2010-05-04
How are you accessing the web sites, remotely, or directly from your computer?

---

### Post by noone123 on 2010-05-04
I'm using a FTP access.
Almost all users are virtual and I set user and group for them www-data/www-data.
Btw, I just remebered for some reasons I added all users to the www-data group, I think this I should have remeber erlier...

---

### Post by cariboo on 2010-05-04
You may be able to see what is in each directory, but can you modify/add/remove anything from the directories, what are the permissions of the directories?

---

