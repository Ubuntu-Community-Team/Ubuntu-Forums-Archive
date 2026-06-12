---
title: "What does id the evil command?"
date: 2009-04-27
forum: The Cafe
---

### Post by bobmatino17 on 2009-04-27
OK, I know that <snip> (Do not us that command, it is bad.) freezes your computer, forcing you to do a hard reset. But exactly what is it? I think that : is a shorthand for bash and when i just typed in :() it lead me to another command line. So what is it?

stupid smilies. the frowns are a colon ":" then open parenthesis "(", the confused ones are a colon then a pipe "|"

---

### Post by Namtabmai on 2009-04-27
*edit* removed due to forum guidelines *edit*

Actually, why doesn't Ubuntu have the ulimits set to prevent this?

---

### Post by sisco311 on 2009-04-27
: is the name of the function.

Here is more human readable code:

```
bomb() { 
 echo \<removed\> # :) 
}; 
bomb
```

DON'T RUN THIS CODE!!!

[http://www.cyberciti.biz/faq/understanding-bash-fork-bomb/]("http://www.cyberciti.biz/faq/understanding-bash-fork-bomb/")

---

### Post by MaxIBoy on 2009-04-27
It's a fork bomb. It constantly spawns child processes, then these spawn their own child processes, and so on, until you run out of room to keep track of them all. Every time you manage to kill some, the others instantly spawn new ones before you can do anything.

---

### Post by skymera on 2009-04-27
I've run it in the past :)
Was interesting

---

### Post by MaxIBoy on 2009-04-27
I've come up with a more-potent one before, using a bash quine and the "yes" command.

---

### Post by ddrichardson on 2009-04-27
[http://en.wikipedia.org/wiki/Fork_bomb](http://en.wikipedia.org/wiki/Fork_bomb)

That's assuming it's intentional, I've worked on projects where there have been logical errors with the same result.

---

### Post by cariboo on 2009-04-27
This thread doesn't look like it is going anywhere. If you need to discuss fork bombs, do it in the [Security Discussion]("http://ubuntuforums.org/forumdisplay.php?f=338") forum.

This thread is closed

---

