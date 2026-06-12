---
title: "ReWrite help"
date: 2010-04-19
forum: The Cafe
---

### Post by Nano on 2010-04-19
Hi guys, this might not be the best place to post this question but during all these years the Ubuntu Community has always helped me, so here it goes.

I need a rewrite rule that does the following (in pseudo-code).
Can someone help me?

```

If request contains ( ("jpg" or "gif" or "png") and "/static/images/products" )
when I say /static/images/products/large/some-text-written-here_ID2304.jpg
I mean /static/images/products/large/ID2304.jpg

```

In other words, everything between the last slash (/) and the underscore (_) has to be removed.

Thanks in advance, guys.

---

### Post by sandyd on 2010-04-19
try using awk

---

### Post by sisco311 on 2010-04-19
You can use one of the GUI tools to rename the files:
[list]
[*]thunar (file manager)
[*]gprename (gtk)
[*]purrr (gtk)
[*]pyrenamer (gtk)
[*]gwenrename (qt)
[*]krename (qt)
[/list]

or the perl based rename command:
```
cd /path/to/dir
rename --no-act 's/.*_//' *.jpg *.png *.gif
```

remove the --no-act option to actually rename the files. 

or:
```

cd /path/to/dir
for file in *.jpg *.png *.gif; do **echo** mv -b "${file}" ${file/*_/}; done

```

remove the echo command to actually rename the files.

---

### Post by Nano on 2010-04-19
I'm afraid I didn't explain myself.
I mean Apache Mod ReWrite :)

---

### Post by sisco311 on 2010-04-19
> **Nano said:**
> I'm afraid I didn't explain myself.
I mean Apache Mod ReWrite :)

OOPS!

Try something like:
```
RewriteEngine On
RewriteRule static/images/products/(.*/).*_(.*\.jpg) static/images/products/$1/$2
```

---

### Post by utnubuuser on 2010-04-19
Are you trying to prevent hot-linking to images?  Why not say what the purpose of the rewrite rule is.

---

