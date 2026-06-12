---
title: "can /bin/sh handle [ &quot;$1&quot; == &quot;$2&quot; ] ?"
date: 2007-09-29
forum: The Cafe
---

### Post by patrick295767 on 2007-09-29
can /bin/sh handle if [  "$1" == "$2"  ] ; then  bla bla, is your distro still buggy as hell, guys ?
 
The **==** was the bug with /bin/sh, but = worked.

Best regards

---

### Post by walkerk on 2007-09-29
With /bin/sh or bash
```
#!/bin/sh

string1="blah"
string2="blah"

if [ $string1 = $string2 ]; then
  echo "$string1 $string2"
fi
```

or

With /bin/bash
```
#!/bin/bash

string1="blah"
string2="blah"

if [ $string1 == $string2 ]; then
  echo "$string1 $string2"
fi
```

---

### Post by patrick295767 on 2007-09-29
> **walkerk said:**
> With /bin/sh or bash
```
#!/bin/sh

string1="blah"
string2="blah"

if [ $string1 = $string2 ]; then
  echo "$string1 $string2"
fi
```

or

With /bin/bash
```
#!/bin/bash

string1="blah"
string2="blah"

if [ $string1 == $string2 ]; then
  echo "$string1 $string2"
fi
```

That I knew. :)
  
So, why hence :
```
#!/bin/sh
string1="blah"
string2="blah"
if [ $string1 == $string2 ]; then
  echo "$string1 $string2"
fi
```
  
Fails with Ubuntu, gives error, but on the other hand works with all other linux distros ? 
(Are Ubuntu allowed to decide such things ? That's not Debian way, for sure)

---

### Post by FuturePilot on 2007-09-29
Maybe we need to file a bug

---

### Post by patrick295767 on 2007-09-29
> **FuturePilot said:**
> Maybe we need to file a bug

It's not maybe .... :)  :lolflag::lolflag: 
It's there since edgy  !!

Man, Ubuntu is really amazing ... :lolflag:

---

### Post by Polygon on 2007-09-29
because defenitly its such a serious bug that it hasnt been fixed in 2 releases. I still dont get sound after i resume from suspend, and thats been there since dapper. I think thats a more serious problem then if ubuntu can handle two equal signs rather then one

file a bug, and if its already reported go post a comment to bump it. and dont come here and bash ubuntu, we dont care and it says something about yourself every time you do it

---

### Post by dabeej on 2007-09-29
When using arithmetic operators such as "==", I suggest you use "-eq" instead.

---

### Post by dabeej on 2007-09-29
/bin/sh isn't bash, btw

Binary files /bin/sh and /bin/bash differ

---

### Post by DoktorSeven on 2007-09-29
I honesty wonder why we even bother with Dash in Ubuntu, seriously.  It creates problems with scripts that use /bin/sh (which is symlinked to dash) when some things in that script behave differently or don't work at all with dash's implementation of bash's shell script.

Why not just symlink /bin/sh to bash to begin with, get rid of dash, and let that be that?  Why the extra shell?

---

### Post by Matthew Wiebelhaus on 2007-09-29
Id was jut wondering if you knew that there were no animated avatars just to let you know.

---

### Post by Polygon on 2007-09-30
he made his account when there were no restrictions on animated avatars, so therefore he has one

---

### Post by patrick295767 on 2007-10-02
It is quite an annoying bug for servers and experienced users, unfixed and present since 1-2 years in Ubuntu-Distros  (?).  Imagine what can they do with all the  sh scripts ? Have to convert all them or look everywhere replacing sh by bash... well. Not too much servers are running Ubuntu. 
  Ok, no worries. I am sorry if you felt attacked by the thread.

---

### Post by master_kernel on 2007-10-02
I'm not sure. "$1" = "$2" works in Gutsy though.

---

### Post by patrick295767 on 2007-10-15
I am a bit worry, since sh is rather well used ...
a very simple example, compiling :
```
**sh** ./configure 
make 
make install
```

---

### Post by dwhitney67 on 2007-10-15
dash is Ubuntu's pathetic substitute for bash.  On most Linux distros, sh is linked to bash, but not on Ubuntu.

If you do not already have it, install bash and specify that in your scripts.  If you are concerned about other scripts, then do what I did... blow away /bin/sh and relink it to /bin/bash.

Here's another bash construct, which if I recall correctly, won't work with dash:

```
cp somefile{,.copy}
```

It is supposed to make a copy of "somefile" with a .copy extension.  The use of {} brackets does not work with dash.  It is almost as if dash was designed/implemented to function as a minimal-bash.  If that is the case, then busybox should have been used.

Also if you have not already discovered it, Ubuntu ships with a lame vim editor.  If you want to real McCoy, then you need to install vim-full (or full-vim?).  Anyhow, the bash & vim issues make me question the worthiness of Ubuntu.  Who knows what other "corners" have been cut.  For a true development system, I tend to pass on it and favor Fedora.  For me, Ubuntu is a mere curiosity, but not something to be taken seriously.

---

### Post by toupeiro on 2007-10-15
I know a lot of people use bash.  Don't use dash or sh as my shell.  Many years ago I changed over to tcsh and integrated vi into my command line editor across all platforms, UNIX and Linux.  It has all the power of the Bash and C shell.  No tcsh bugs in ubuntu that I can find thus far.  all my scripts are still easily runnable under tcsh on */UX

---

### Post by patrick295767 on 2007-10-17
> **dwhitney67 said:**
>  ...
vim issues make me question the worthiness of Ubuntu.  Who knows what other "corners" have been cut.  For a true development system, I tend to pass on it and favor Fedora.  For me, Ubuntu is a mere curiosity, but not something to be taken seriously. 
   
Well, I also think the same. Fedora or Debian. If you knew all problems with Ubun., that you discover when digging just a little bit with the box, that are unconsidered or not fixed at all. That's amazing... and rather weird in fact. Additionally, the wonderfully claimed Automatix is not supported by Debian, e.g..  
 
An example, give for instance a try to that [http://linuxgazette.net/issue72/chung.html](http://linuxgazette.net/issue72/chung.html)  with your ubuntu box ? is the bug fixed yet ?  :)

---

