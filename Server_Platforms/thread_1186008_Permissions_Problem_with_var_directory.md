---
title: "Permissions Problem with var directory"
date: 2009-06-12
forum: Server Platforms
---

### Post by regnumimbrium on 2009-06-12
Hey Everyone,

I think I really screwed some things up. While on my user "main", I executed the following command in terminal:

sudo chown -R main:root /var

I'm having all sorts of problems with MySQL and I think it's because of that command. I tried to undo it with the following command:

sudo chown -R root /var

Things looked as though they'd returned to normal inside the directory but I still can't connect to MySQL.

Any help would be tremendously appreciated.

---

### Post by llamaX on 2009-06-12
```
sudo chown -R mysql /var/run/mysqld
```

---

### Post by regnumimbrium on 2009-06-13
Awesome, thanks llamax - I'll try that right away.

Do you think that a lot of other permissions got screwed up in the /var directory? There's quite a lot of stuff in there.

There's no way to just 'undo' what I did, huh?

---

### Post by regnumimbrium on 2009-06-13
Well, that didn't do the trick, llamaX. MySQL still won't boot up.

---

