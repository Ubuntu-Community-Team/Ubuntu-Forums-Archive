---
title: "Search through Binary files, similarly to Grep- SearchBin"
date: 2012-06-19
forum: Tutorials
---

### Post by Sepero on 2012-06-19
This is a shameless promotion to publicize a piece of open source software I created to [search through binary files]("http://seperohacker.blogspot.com/2012/04/binary-grep-program-searchbin.html"). It works a little bit like grep.

The program name is `[searchbin]("http://seperohacker.blogspot.com/2012/04/binary-grep-program-searchbin.html")`

To find offset matches in binary files using [searchbin]("http://seperohacker.blogspot.com/2012/04/binary-grep-program-searchbin.html"), run it like this:
```
$ ./searchbin.py -p "0xFF14DE" gamefile.db
Match at offset:            907          38B in  gamefile.db
Match at offset:           1881          759 in  gamefile.db
Match at offset:           7284         1C74 in  gamefile.db
Match at offset:           7420         1CFC in  gamefile.db
Match at offset:           8096         1FA0 in  gamefile.db
```


LINK:
[http://seperohacker.blogspot.com/2012/04/binary-grep-program-searchbin.html](http://seperohacker.blogspot.com/2012/04/binary-grep-program-searchbin.html)
It also allows for limited wildcard searching ("FF??DE"), and searching using an intermediate binary file. Find out more:


New suggested features may be added if they are reasonable. I'm currently working on adding the capability to also search for plain text strings.

Can you think of any good uses for [searchbin]("http://seperohacker.blogspot.com/2012/04/binary-grep-program-searchbin.html")? If so, please post a reply to this thread about what you might use it for.

---

