---
title: "Word Count in pdf file?"
date: 2008-05-21
forum: The Cafe
---

### Post by Maratonda on 2008-05-21
Hi,
is there an application/reader/CLI utility that is able to count the number of words in a pdf file? thanks

---

### Post by aeiah on 2008-05-21
as a quick work around, you could just copy it all into open office or whatever office progam you use and do a word count from there. you should be able to ctrl+a ctrl+c to grab everyword in the file.

there is probably another way though if you're going to be doing this a lot. most things can be manipulated and automated

---

### Post by brunovecchi on 2008-05-22
Take a look at pdfinfo. It's in the repositories.

---

### Post by Maratonda on 2008-05-23
mm..couldn't find info about the number of words...it's kind of weird that major readers, acrobat included, don't have this feature.

---

### Post by aeiah on 2008-05-23
there's an app called pdf to text. you could probably pipe it to word count with something like
```

pdftotext nameof.pdf | wc -w -
```

thats assuming -w means 'words' and pdftotext is used like that. the end hyphen will pipe the output to stdout (ie, it'll print it to the terminal screen).

i dunno if this will do strange things though. it depends how your pdf is set out and whether pdftotext does something weird when converting. if you find it leaves a lot of slashes or weird symbols where images are or something you could always pipe it to sed to remove them before piping it to wc

---

### Post by adking80 on 2009-04-01
[QUOTE=aeiah;5024198]there's an app called pdf to text. you could probably pipe it to word count with something like
```

pdftotext nameof.pdf | wc -w -
```

Thanks!  This worked great except the STDOUT hyphen should be before the pipe instead of after.  Even though I have a lot of equations and figures, the text file looked like a reasonable approximation, except I think wc counts all the dots in the table of contents -- might have added a thousand extra words but it's ok for a ballpark :p

---

### Post by s.fox on 2009-04-01
Necromancy :D

---

### Post by kaibob on 2009-04-13
> **adking80 said:**
> [QUOTE=aeiah;5024198]...
Thanks!  This worked great except the STDOUT hyphen should be before the pipe instead of after.  Even though I have a lot of equations and figures, the text file looked like a reasonable approximation, except I think wc counts all the dots in the table of contents -- might have added a thousand extra words but it's ok for a ballpark :p


I was curious about wc counting periods and ran a few tests using the command line shown below. As expected, wc does not count dots that follow a word. However, dots were counted as words when they were on a separate line. I guess this is consistent with the wc definition of word:

> The wc utility shall consider a word to be a non-zero-length string of characters delimited by white space.

Not important but I was curious.

```
pdftotext nameof.pdf - | tr -d '.' | wc -w -
```

---

