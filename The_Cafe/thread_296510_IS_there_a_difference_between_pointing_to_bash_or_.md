---
title: "IS there a difference between pointing to /bash or /sh ??"
date: 2006-11-09
forum: The Cafe
---

### Post by user1397 on 2006-11-09
i just want to know if there's a difference when you start a script with #!/bin/bash or #!/bin/sh ???  does it affect the script in any way if one is used over the other?  (aren't bash and sh the same thing?  i guess thats what im trying to say...)

---

### Post by po0f on 2006-11-09
erik1397,

Typically, /bin/sh is a symlink to /bin/bash, so in most situations it doesn't matter.  On Edgy /bin/sh is a symlink to */bin/dash*, so you might run into some compatibility issues.  My suggestion would be to use `#!/bin/bash`.  Search the forums, there have been some people having problems installing stuff on Edgy using shell scripts.

---

### Post by shining on 2006-11-09
Actually, that's a very common mistake to use #!/bin/sh when using bash specific features.
There should never have been a symlink from sh to bash in the first place, that's what caused these scripts to work on some systems (a certain number of linux distributions) and not on others (like *bsd, or other linux distributions, like ubuntu which is now using dash).

---

### Post by user1397 on 2006-11-09
im asking because the tovid installation script i made seemed to not work in edgy if it was pointing to bash, but it worked when pointing to sh.  

does anyone know why edgy devs decided to symlink to dash in the first place?  (and what exactly is dash!)

---

### Post by kuja on 2006-11-09
Dash is the debian almquist shell. It's lighter and somewhat faster than bash, and it's more strictly POSIX compliant. Bash seems to make the better login shell; however, which is why it's still the default login shell.

---

### Post by user1397 on 2006-11-10
hey whastup with this!!!

i tried to execute my tovid script (which starts with #!/bin/bash) but it returned this error:
```
bash: ./installtovid.sh: /bin/bash^M: bad interpreter: No such file or directory
```i dont know why it does that...it has executable permissions, and i tried aysiu's songbird script, (which starts out with bash also, )and that worked fine.

???

edit: btw, im using dapper again

---

### Post by po0f on 2006-11-11
erik1397,

^M is a carriage return I believe (\r).  You must have downloaded this file either from a Windows or Mac box and transferred it over or something along those lines.  Use [tr](http://www.die.net/doc/linux/man/man1/tr.1.html) to remove the \r's from your script.

---

### Post by user1397 on 2006-11-11
yes i did transfer it from a windows machine.  thanks for the reply.  i don't really get how to use tr yet, but i'll get the hang of it soon enough.

---

### Post by po0f on 2006-11-11
erik1397,

Try:
```
$ cat script.sh | tr -d \r > newscript.sh
```

---

### Post by user1397 on 2006-11-11
> **po0f said:**
> erik1397,

Try:
```
$ cat script.sh | tr -d \r > newscript.sh
```well i didn't do what you suggested, but i still got it to work.  i had saved my script in .txt format, and then uploaded it to my web server, so that i could just copy/paste the script into a new document, and it worked.
thanks for all ur help.

---

