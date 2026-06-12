---
title: "/etc/passwd script question"
date: 2012-11-07
forum: Server Platforms
---

### Post by Loki57701 on 2012-11-07
Hello all, I need some scripting help. I need to modify the /etc/passwd file using a script.

I want to change the 2nd column of a user field from x to *.

As an example:

**From**

```
test:x:123:123:some comment:/bin/bash:/home/test
```

**to**

```
test:*:123:123:some comment:/bin/bash:/home/test
```

I've tried various combinations of sed and awk, but the /'s in the path names, and the wildcard '*' seem to mess things up.

Does anyone have an idea of how I can go about this?

---

### Post by drmrgd on 2012-11-07
Maybe something like this:

```
awk -F: '{ sub(/x/,"*",$2); print }' /etc/passwd
```

Not sure if that's what you were looking to do.  You can redirect the output to a file too, if you like.  Just add '> somefile.txt' to the end

---

### Post by sisco311 on 2012-11-07
Check out: BashFAQ 001 and [http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes)

---

### Post by koenn on 2012-11-08
you can 'escape' the * wildcard with \, like so

```
sed s/:x:/:\*:/ /path/file
```
(you need to add the -i option or redirect the output to make changes permanent)

make sure you know what you're doing wrt /etc/shadow vs. /etc/passwd, and the effects of '*' in the password field !

---

### Post by Loki57701 on 2012-11-08
Thank you everyone, for all the help.

Using your advice I was able to get my script working.

---

