---
title: "cowsay on one line?"
date: 2007-05-16
forum: The Cafe
---

### Post by Sqwishy on 2007-05-16
When i use the cowsay command in the console it looks normal, but say i echo it like
```
echo `./cowsaydefenition` > outcow
nano outcow
```
It's all one line. Anyone know why or how to fix it?
Oh yeah cowsaydefenition is a script that just runs the command " cowsay `fortune definitions` "

---

### Post by jyba on 2007-05-16
'**echo**' is old, eccentric and cranky. It was originally only intended to print out a single line of space-separated text followed by a newline. It's better to use '**printf**' for anything more complicated.

Anyway, one way around it is to use double-quotes to preserve the text formatting...

```
echo "`./cowsaydefenition`" > outcow
```

...but I am left wondering why you are using '**echo**' at all. If it's an executable file why not just execute it?...

```
./cowsaydefenition > outcow
```

---

### Post by Sqwishy on 2007-05-16
yeah well see in evolution i have cowsaydefenition as a script it runs to get the signature thingy but it doesn't have any linebreaks or w/e so i'm trying to make it be all nice.

Yeah i just made a python script instead :P

---

