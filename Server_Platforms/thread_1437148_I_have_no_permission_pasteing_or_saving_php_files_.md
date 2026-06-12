---
title: "I have no permission pasteing or saving php files in var/www"
date: 2010-03-23
forum: Server Platforms
---

### Post by Edgar09 on 2010-03-23
Hey Linux & php pros
Right when i thought i had the whole php,mysql & apache under my power! Now i see that i cant save or paste any php files in the carpet of www?!

Any clues linux pros?
:D

---

### Post by voja15 on 2010-03-23
Try pasting as root.
Open terminal (applications>accesories>terminal) and type the following command:
```
sudo cp /file/location /var/www/
```

You can also change the owner of www folder:
```
cd /var
```
```
sudo chown -R <username> <group> www
```

Ofcourse, write username and group without "<" and ">" signs.

---

### Post by KB1JWQ on 2010-03-23
Concur. Ownership or perms issue-- fix this and the problem sorts itself out, but be careful!  If you open it up too far you wind up with security problems.

---

### Post by Edgar09 on 2010-03-23
> **voja15 said:**
> Try pasting as root.
Open terminal (applications>accesories>terminal) and type the following command:
```
sudo cp /file/location /var/www/
```

You can also change the owner of www folder:
```
cd /var
```
```
sudo chown -R <username> <group> www
```

Ofcourse, write username and group without "<" and ">" signs.


What do you mean by group

---

### Post by Edgar09 on 2010-03-23
O.k i just fixed the problem but i dont know how i fixed.! xD
Thanks any way Linux Pros.!
:popcorn:

---

### Post by dudumomo on 2010-03-23
Well..it would have been nice to see how did you do...

---

### Post by Edgar09 on 2010-03-24
> **dudumomo said:**
> Well..it would have been nice to see how did you do...

Well.... I really dont know how to explain it.
I just opened the Browser "FireFox" then
I out local host then opened up a php file
The i reopened the file var/www
Then with out any problems i could copy & paste php or any other files...
Weird huh?!
;)

---

