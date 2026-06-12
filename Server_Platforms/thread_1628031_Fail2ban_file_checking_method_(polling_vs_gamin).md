---
title: "Fail2ban file checking method? (polling vs gamin)"
date: 2010-11-22
forum: Server Platforms
---

### Post by James78 on 2010-11-22
Fail2ban has 2 methods of checking if files are changed. Polling (which I'd assume just keeps checking the file, probably not as good as gamin), or python-gamin, which is some type of library to check changed files, and is probably better and preferred.

As you can see, it states that for some reason, debian shipped python-gamin doesn't work as expected, but for all I know, it's been resolved for some time. I'd much rather set the setting to auto.

By default, Fail2ban in Ubuntu uses polling. Does anyone know if python-gamin will work with fail2ban?

```
# "backend" specifies the backend used to get files modification. Available
# options are "gamin", "polling" and "auto".
# yoh: For some reason Debian shipped python-gamin didn't work as expected
#      This issue left ToDo, so polling is default backend for now
backend = polling
```

---

### Post by schirpich on 2010-12-31
bump for curiosity

---

### Post by Vegan on 2011-01-01
I suggest using Google and look at various other users posts and see what you can find.

---

### Post by James78 on 2011-01-03
I had already looked around as much as I could before making this topic. ;)

---

### Post by notuncommon on 2011-02-09
I'd like to know the same thing as the first two posters.  This thread illustrates the two biggest problems with using Linux:

 1) Sparse to non-existent documentation coupled with a lack of professionalism among some developers who seem to think documentation is some kind of** bonus**, or that a wiki is the same as documentation.

2) People who post to forums suggesting that the questioner should have used google first. Ocasionally that is true, but in most cases I find such statements after having already spent considerable time trying to find an answer. The web is more than 99% garbage and the point of forums such as this is to provide people with a place to ask questions. If the answer is so trivially found, then perhaps this could be pointed out by providing a link or a search term.

To be fair, this second point is not just a problem with using Linux, but more a problem of trying to get any useful answer on almost any forum.

---

