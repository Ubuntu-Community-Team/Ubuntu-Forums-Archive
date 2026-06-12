---
title: "cron with $(date +&quot;%a&quot;) ?"
date: 2007-02-28
forum: Server Platforms
---

### Post by Sgurd on 2007-02-28
The following cron entry doesn't appear to run for me:
0 0 * * mon,tue,wed,thu,fri mysqldump mydb > /root/mysqldumps/$(date +"%a").mysql

If I remove the '_ +"%a"_' it works find.

Can I have a formatted date for the filename in a cron entry?

   Thanks for any help - JD

---

### Post by mannheim on 2007-02-28
What happens if you remove the double-quotes?

---

### Post by Sgurd on 2007-02-28
Thanks for the reply.

I removed the double-quotes and I still do not get a dump.

---

### Post by Wallace on 2007-02-28
I don't know if you can do what you want, but there is another way (which is what I do):

Write a script to do the mysql dump, and then schedule that script via cron.

Something like:

mybackup.sh:

```
#!/bin/sh

mysqldump mydb > /root/mysqldumps/$(date +%a).mysql
```

and then run mybackup.sh via cron.

---

### Post by mannheim on 2007-02-28
This just worked for me: escape the "%" character with a backslash, like this:

```
* * * * echo foo > /home/username/test.$( date + \%a )
```

I've no idea why.

---

### Post by MJN on 2007-02-28
It's because the % character in crontabs indicate new lines.

The problem, along with a solution (note that \ has its drawbacks), is described in full at [http://www.hcidata.info/crontab.htm](http://www.hcidata.info/crontab.htm) (it even uses a MySQL entry as an example!)

I personally like the 'use a seperate script' workaround like Wallace suggested as then you have the benefit of none of these 'cron peculiarities' as well as making it trivial to make the cron actions even more elaborate with ease.

Mathew

---

### Post by Sgurd on 2007-03-01
Thanks for the replies.
I'll go with the script route.
  - JD

---

