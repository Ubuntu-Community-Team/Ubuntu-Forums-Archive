---
title: "Shell Script"
date: 2008-05-22
forum: Server Platforms
---

### Post by bobthebob1234 on 2008-05-22
Hello.

I am trying to make a shell script to search for a directory for a folder called todays date.

I can get the date, but how would I format it to DD Month YYYY (eg 22 May 2008)

How would i do this?

Thanks

---

### Post by kerry_s on 2008-05-22
not sure i understand. try reading> man date
according to the man pages the format is> %j %m %Y

---

### Post by wdaniels on 2008-05-22
%b should give you the full month name if that's what you want:

```
date +"%m %b %Y"
```

---

### Post by bobthebob1234 on 2008-05-22
Thanks, thats perfect!

---

