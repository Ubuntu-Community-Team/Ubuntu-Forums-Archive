---
title: "Intriguing, cool looking code."
date: 2009-12-28
forum: The Cafe
---

### Post by CJ Master on 2009-12-28
I love code that almost draws a person in and provokes their curiosity.

For example, the bash forkbomb.

**Needless to say, forkbombs=bad. Please don't run the following.**
```
:(){:|:&};:
```

If I didn't know better, I'd be compelled to run this to see what it does. Does anyone else have any examples?

---

### Post by Hells_Dark on 2009-12-28
Actually, it's quite easy to understand. Since the function created here is called ":".

(and you can try it, it will just freeze your machine within a few seconds [COLOR="SlateGray"](unless you set up a thread number limit)[/COLOR], no file is deleted)

---

### Post by ibuclaw on 2009-12-28
```

#!/usr/bin/perl

_((_).(_).(_));     while(<>){chomp;    s}^\s*(.+)}$1}g;    _(_),
,next     if!(~     ~$_);               split      ?\s+?    ;;$_=     
shift     @_;;;     /cd/g               ?(42,      chdir    @_[(_
)]||_exit_("$_"     .qq?\x3A\x20@_?,    $!)):?exit??exit    @_[0+
sqrt(               13+(2               *8-sqrt             (169)
))-!!               sqrt(               256)]  :fork?       wait:
$wait               ?(_):(exec $_,@_    or(1)   ,_exit_(    $_,$!),{_},exit

);sub _{(_)?print qq/\x3E\x20/:exit}sub _exit_ {s__exit__exit_ or exit;print 
qq/\x70\x6c\x73\x68\x3A\x20$_[0]\x3A\x20$_[1]\n/; }_(____)unless(_)};reverse

```
A Basic Login Shell that a friend wrote some time ago...


Also, another dash of warning.

To users who are unfamiliar - see the following for guidance.

[Understand what a fork bomb does.]("http://www.cyberciti.biz/faq/understanding-bash-fork-bomb/")
[How to prevent a fork bomb from escalating.]("http://www.cyberciti.biz/tips/linux-limiting-user-process.html")

And while I'm at it, I would like all users to refresh their memories with our [Malicious Commands]("http://ubuntuforums.org/announcement.php?a=54") thread.

Regards
Iain

---

### Post by gnomeuser on 2009-12-28
An old friend of mine posted [this](http://davybrion.com/blog/2009/12/what-do-you-think-this-does/) the other day..

I'm still trying to wrap my mind around it.

---

### Post by phrostbyte on 2009-12-28
```
:(){:|:&};:
```

```

function with no parameters (:())

pipe the function twice (:|:) in the background (&)

then run the function in the foreground again (;:) (recursive infinite loop)

```

 UbuntuForums smiles it up :)

What happens is a nice mathematically beautiful recursive tree-like fork bomb, which quickly grows out of control. :)

---

### Post by phrostbyte on 2009-12-28
> **gnomeuser said:**
> An old friend of mine posted [this](http://davybrion.com/blog/2009/12/what-do-you-think-this-does/) the other day..

I'm still trying to wrap my mind around it.

Looks a lot like an expression tree you'd find in a compiler. :)

---

### Post by ibuclaw on 2009-12-28
> **gnomeuser said:**
> An old friend of mine posted [this](http://davybrion.com/blog/2009/12/what-do-you-think-this-does/) the other day..

I'm still trying to wrap my mind around it.

It would be easy to understand had he not used mindbendingly long CamelCase variables.

Other than that - it is quite a straightforward design.
Shame about the language schematics...

---

