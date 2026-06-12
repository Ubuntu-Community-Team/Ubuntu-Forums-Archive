---
title: "MySQL Administrator locks up"
date: 2007-04-10
forum: Server Platforms
---

### Post by gargo2000 on 2007-04-10
I'm new to working with MySQL.  I spent most of the day toying with it and other server stuff.  I am trying to add a user through the MySQL Adminstrator and when I press on "User Administration" button, it totally freezes up on me.  All the other buttons are working.  I tried rebooting as well as re-installing MySQL.  

Any Ideas?

Thanks, Gargo

---

### Post by NeoGreen on 2007-04-10
I am new to MySQL and when it freezes up on me. What I usually do is restart MySQL with this command:
```
 # /etc/init.d/mysqld restart
```

It works most of the time.  Hope this works:)

---

### Post by Spyke on 2007-04-14
I ran into the same problem this morning. After looking around I found the following [fix](http://forums.mysql.com/read.php?34,113738,124883#msg-124883), which worked for me:

Simply export the following variable before executing the administration program:

```
export DEBUG_DONT_SPAWN_FETCHES=1
```

---

### Post by shadowcat77 on 2007-04-17
Yeah.. I just solved this problem with one of my older laptops that I have running. It's a memory issue. My old laptop had 256mb and I was having the same problem. When I added an extra 128mb sodimm, it no longer froze. I'd suggest upgrading or adding more memory.

---

### Post by Dark Angel on 2007-07-14
I'm having the same problem but with a gig of ram.  My memory test fine so I'd say in my case it's not a memory issue.

---

