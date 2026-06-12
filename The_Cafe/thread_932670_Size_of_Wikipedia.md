---
title: "Size of Wikipedia"
date: 2008-09-28
forum: The Cafe
---

### Post by Trzone on 2008-09-28
I know that Wikipedia has these so called "dumps" but does anyone know the actual size of all the information wikipedia has?  Just curious.

---

### Post by jespdj on 2008-09-28
Where else would you find the answer to that than on ...Wikipedia ?! ;)

[http://en.wikipedia.org/wiki/Wikipedia:Size_of_Wikipedia](http://en.wikipedia.org/wiki/Wikipedia:Size_of_Wikipedia)

---

### Post by schauerlich on 2008-09-28
```

wget -R http://wikipedia.org

```


(Just kidding, that will take hours and get you nothing useful. :) )

---

### Post by Trzone on 2008-09-28
theo@Ubuntu:~$ wget -R [http://wikipedia.org](http://wikipedia.org)
wget: missing URL
Usage: wget [OPTION]... [URL]...

Try `wget --help' for more options.



I seriously want to know, and well, wikipedia is only specific in terms of books, not actual computer data! hehe

---

### Post by LaRoza on 2008-09-28
> **Trzone said:**
> theo@Ubuntu:~$ wget -R [http://wikipedia.org](http://wikipedia.org)
wget: missing URL
Usage: wget [OPTION]... [URL]...

Try `wget --help' for more options.

I seriously want to know, and well, wikipedia is only specific in terms of books, not actual computer data! hehe

The data would be stored in a database, MySQL I think they use.

http://stats.wikimedia.org/EN/Sitemap.htm

---

### Post by schauerlich on 2008-09-28
> **LaRoza said:**
> Don't put the "http://" in there.

The data would be stored in a database, MySQL I think they use.

[http://stats.wikimedia.org/EN/Sitemap.htm](http://stats.wikimedia.org/EN/Sitemap.htm)

Also it's -r not -R

---

### Post by t0p on 2008-09-28
> **LaRoza said:**
> Don't put the "http://" in there.

The data would be stored in a database, MySQL I think they use.

[http://stats.wikimedia.org/EN/Sitemap.htm](http://stats.wikimedia.org/EN/Sitemap.htm)

No, the "http://" *does* need to be in there.  But you should use the "-r" flag not the "-R" flag.  Ergo~

```
wget -r http://wikipedia.org
```

---

### Post by LaRoza on 2008-09-28
> **t0p said:**
> No, the "http://" *does* need to be in there.  But you should use the "-r" flag not the "-R" flag.  Ergo~

```
wget -r http://wikipedia.org
```

It was a suggestion, but I see now.

I should have RTM'd first.

---

### Post by snova on 2008-09-28
A static HTML dump is about 14.3 GB, compressed with 7zip. Does that answer your question?

---

### Post by Trzone on 2008-09-28
I think i want to rephrase my question, it was way too vague.  What is the size of the combined databases that wikipedia owns?:)

---

### Post by init1 on 2008-09-28
> **EDavidBurg said:**
> ```

wget -R http://wikipedia.org

```


(Just kidding, that will take hours and get you nothing useful. :) )
Heh yeah I tried that once :D

---

### Post by Trzone on 2008-09-29
That command doesn't seem to be working :P but um, i think that the statistics are behind by at least 2 years due to the absolute maassive scale that is wikipedia

---

### Post by snova on 2008-09-29
> **Trzone said:**
> I think i want to rephrase my question, it was way too vague.  What is the size of the combined databases that wikipedia owns?:)

You can download that too, as a dump of the database tables. You can always find out by trying to start the download; but then, that's textual SQL and possibly not a good indication of the size of the binary MySQL tables.

---

