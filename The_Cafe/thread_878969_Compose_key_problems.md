---
title: "Compose key problems"
date: 2008-08-03
forum: The Cafe
---

### Post by gryzzly on 2008-08-03
Well, hello there, friends! 
I've got kind of problem with setting up my compose key sequences; 
I used some info from [Daniel Paul's site, which explains how to create custom keyboard on X11]("http://people.uleth.ca/~daniel.odonnell/Blog/custom-keyboard-in-linuxx11").
So what did I do:
first I've created ~/.XCompose file, in which I placed needed sequences. (actually I've also included default sequences by placing this line):
```
include "/usr/share/X11/locale/en_US.UTF-8/Compose"
```
then I set "Compose" key on "menu" key.
Also as recomended I used "im-switch -c" to make my GTK and QT programms to use X Input Method (XIM). 
To assure this I also edited /etc/environment and placed there line:
```
export GTK_IM_MODULE=xim
```
So, after all this I tried to log off and log in. 
What I get is most strange for me:
some of sequences work, and some don't.
and especially this ones that I want to use on several layout groups, that they are assigned on "non-language" dependant keys, like "minus", or "less" or "more", all this don't work.
But this, assigned to "compose" + "a" + "r" for example, or whatever what else - these do work.

Can anybody help?

---

### Post by gryzzly on 2008-08-06
bump

---

