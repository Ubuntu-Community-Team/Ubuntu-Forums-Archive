---
title: "a little sql &amp; grep help?"
date: 2013-03-06
forum: Server Platforms
---

### Post by SlugSlug on 2013-03-06
Hi 

I've got a sql db with a IP column. I want to somehow use that column as a variable in grep so I can get the results like

grep $IP /var/log/auth.log


Many Thanks,

---

### Post by drmrgd on 2013-03-06
Maybe a little clunky, but could you extract that column to a file with something like awk, and then use that file as a lookup with the '-f' option of grep?

```
 grep -f <lookup_file> /var/log/auth.log 
```

I don't know much about sql, so maybe it's not so easy to extract columns of data to a file, though.

---

### Post by SlugSlug on 2013-03-06
ahh thanks didn't know about -f option :)

---

### Post by schragge on 2013-03-06
I guess fgrep/grep -F would do it, too
```

fgrep "`psql -A -t -q -c 'SELECT ip FROM table;' db_name username`" /var/log/auth.log

```
or
```

fgrep "`mysql -B -r -e 'SELECT ip FROM table;' -u username db_name`" /var/log/auth.log

```

---

### Post by SlugSlug on 2013-03-06
Thanks

---

