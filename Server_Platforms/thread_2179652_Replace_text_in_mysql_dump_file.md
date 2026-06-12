---
title: "Replace text in mysql dump file"
date: 2013-10-09
forum: Server Platforms
---

### Post by hersdyanata on 2013-10-09
[COLOR=#000000][FONT=Arial]Hi everyone,
I have a mysql dump file, which is a database of social wordpress blog. In it there are about 800 blogs that have been made, the company where I currently work change their domain, and they don't want to lose the blogs. what i need is changing the domain in that dump database. How to do the replacement domain with awk?


how to do this with awk ?
searching for the **"old domain"** and replace with a **"new domain"**.


i did it with notepad++ in windows before, but didn't work well.


or maybe there's is the other way? the better way?


thanks
[/FONT][/COLOR]

---

### Post by SeijiSensei on 2013-10-09
Actually you want to use [sed]("http://www.gnu.org/software/sed/manual/sed.html"):

```
sed 's/old_domain/new_domain/g' < olddb.sql > newdb.sql
```

If the domain is something like example.com, "escape" the dot like this:

```
sed 's/example\.com/newdomain.com/g' < ... 
```

The first entry is a regular expression, but the replacement text is just a string.  I enclosed the command in single quotes to force bash to treat the whole thing as a literal.

Make sure you have backups of the original dump before proceeding.  Even though the procedure above will create a new file, it's always good to have backups just in case.

---

