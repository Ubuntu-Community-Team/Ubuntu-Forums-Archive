---
title: "cedega install"
date: 2009-05-19
forum: Wine
---

### Post by Cavs23 on 2009-05-19
When I try and install a game I get this error in the terminal.
```
Perhaps you have not properly edited or created your Wine configuration file.
This is (supposed to be) '/home/ron/.cedega/Battlefield 2/config'

```

It also says that cedega is certified for Python 2.3 - 2.5 should I downgrade from 2.6?

---

### Post by nolliecrooked on 2009-05-19
> **Cavs23 said:**
> When I try and install a game I get this error in the terminal.
```
Perhaps you have not properly edited or created your Wine configuration file.
This is (supposed to be) '/home/ron/.cedega/Battlefield 2/config'

```It also says that cedega is certified for Python 2.3 - 2.5 should I downgrade from 2.6?

is your Cedega legit, ot torrented?

---

### Post by Cavs23 on 2009-05-19
Its legit yes. Friend bought it a while back and recently switched over to a mac so he gave me his rights to cedega. On the #cedega channel they told me to downgrade to python 2.5 but that means  I must give up advant and adblock plus and many other programs.

---

### Post by Grishka on 2009-05-19
> **Cavs23 said:**
> Its legit yes. Friend bought it a while back and recently switched over to a mac so he gave me his rights to cedega. On the #cedega channel they told me to downgrade to python 2.5 but that means  I must give up advant and adblock plus and many other programs.

you can have as many python versions on your system as you like. there's no need to uninstall 2.6 to have 2.5 as well. the only problem is telling the program to use the correct python version. try "alias python=python2.5".

---

### Post by Cavs23 on 2009-05-19
Where abouts do I enter that alias?

---

### Post by Grishka on 2009-05-19
> **Cavs23 said:**
> Where abouts do I enter that alias?

in terminal. or you can press alt+f2 and enter this command.
oh, and be sure to actually have python 2.5 installed.

---

### Post by Sef on 2009-05-19
Moved to WINE forum.

---

### Post by Cavs23 on 2009-05-19
I still get "Invalid path 'c:\windows' for windows directory: does not exist
Perhaps you have not properly edited or created your Wine configuration file.
This is (supposed to be) '/home/ron/.cedega/Battlefield 2/config'"

---

### Post by erlkonig on 2009-06-17
Be aware that the "alias" mentioned earlier is pretty much useless, since they aren't copied into subprocesses (like into cedega when you run it), he didn't suggest where to save it (not that it would be useful to most apps even saved), and finally that aliases are a strange, backwards mechanism used mainly by csh folks who never started using bash.  Aliases are nearly useless (a bizarre compatibility element for the crippled csh from the mid-1980s), and with one weird macro-like exception (read the docs on bash aliases about a trailing space), should never be used for anything, since functions and scripts do virtually everything better.  In fact, "unalias -a" tends to be really handy.

---

