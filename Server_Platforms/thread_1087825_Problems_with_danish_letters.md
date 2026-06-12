---
title: "Problems with danish letters"
date: 2009-03-05
forum: Server Platforms
---

### Post by Anders B on 2009-03-05
When i put danish letters in either a php or html page like this:

```
æ ø å
```

I get this
```
Ã¦ Ã¸ Ã¥ 
```


I bet it's a simpel setting somewhere, but since im not that familiar with linux, I have no idea where.

---

### Post by bluefrog on 2009-03-06
adjusting the charset used by apache in /etc/apache2/conf.d/charset should do the trick

---

### Post by Anders B on 2009-03-08
This is how it looks now:

```
# Read the documentation before enabling AddDefaultCharset.
# In general, it is only a good idea if you know that all your files
# have this encoding. It will override any encoding given in the files
# in meta http-equiv or xml encoding tags.

#AddDefaultCharset UTF-8
```

What should it look like?

---

### Post by JeppeM on 2009-03-09
Hej Anders,

Make it ISO-8859-1, and remove the # infront of the AddDefaultCharset line. This will only take effect on html and text files though..

Håber det virker ;)

---

### Post by Anders B on 2009-03-09
It seems so :D

Thanks, mate :)

---

