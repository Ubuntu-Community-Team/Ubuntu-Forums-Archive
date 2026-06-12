---
title: "I need a simple program made..."
date: 2010-04-11
forum: The Cafe
---

### Post by themarker0 on 2010-04-11
I need a simple program made for my teacher. Its quite simple.

When in terminal i type

"Make me a sandwhich"
Reponse
"No"

But if we add sudo
it tuns out this image 
** [http://imgs.xkcd.com/comics/sandwich.png](http://imgs.xkcd.com/comics/sandwich.png)**


I can run the image through a generator to make it in ASCII or whatever, can anyone help me with that? 

(My teacher makes fun of that everytime i bring my laptop into class >__>)

---

### Post by NightwishFan on 2010-04-11
You could write one in python that pretends to need sudo perhaps, but I am assuming the best quick option is to write a bash script. Ill poke around.

---

### Post by themarker0 on 2010-04-11
> **NightwishFan said:**
> You could write one in python that pretends to need sudo perhaps, but I am assuming the best quick option is to write a bash script. Ill poke around.

Thank you so much :)

---

### Post by Sporkman on 2010-04-11
I have an ASCII generator on my website, but it doesn't render that image very well - it does better with photos.

This is what I end up with, after converting it to jpg & enlarging:

```

$                                                                                                                      
$ ________________________________________________________________________________________________________________   _ 
$ ________________________________________________________________________________________________________________   _ 
$ ___________, _______________________________________________________________________________________________________ 
$ ______ $k.#$._@k.y_@ywc  ;pg@xww.___@L__,,g,.p_,,_y,w._,_ g.__,.. ,  _______________________________________________ 
$ ______ $J@.4LJMME3$L$PL  @HE3HML __@W$. %wg.@M$JRkEJL;E$gL$JL@^3M*$.________________________________________________ 
$ ______ F   'K"` "?L?4P*. ?.  `*** "* JF ?W#F* "^*"F'*^ ?F"`"`%wF` X?. ______________________________________________ 
$ ____________________________________________________________________________________________________________________ 
$ __________________________@L ____________________________________________y___,__,_____,,.,,___ _____________________ 
$ ________________________ :$  ___________________________________________ 3L,:E$g$uE3F"$ `y#` _ J$@$_@L$u#3F** ______ 
$ ________________________ JE ____________________________________________ JBM@L$.$@F3L $  ]. __ $F`$3P$JHkJE[________ 
$ ________________________ JE ____________________________________________  `_,,,_ `  . ! _ .,_,_` ,]' `` '"7"` ______ 
$ ________________________ JL ____________________________________________ JL"3F`` "$@5#F$$L:EE@F`M&[3E2L$ :$F*' _____ 
$ ________________________ JL ____________________________________________ JL JL __ 3F4LJF?wF3E"%L:L@3Ei=@,/@F y _____ 
$ ________________________ 3L ____________________________________________       __ `              `        `    _____ 
$ ________________________    ___________________________________________________ _y _________________________________ 
$ ______ @F"*y 4L@mw..pmL_ _g.yk_@Q.Jkyn@MF  J@gMk@MM. ___________________________@F _________________________________ 
$ ______ ;*3F$.@L$.;F3L_$L :E$F$uBME:Nk.$F _ JEK=$$P._ _________________________ ;E __________________________________ 
$ ______ "%F "*` **l_ Y*`  :F" ?*L *`` *"**` ``  `**** __________________________@. __________________________________ 
$ _______ _@ML _ :E[73ML_@LJE@F*%qL_:Ey..@MLg.:L________________________________@F ___________________________________ 
$ _______ ;P*$.  _ `$@P%L$"@F$LgFJ@M@F3LJL_,@P5L_______________________________   ____________________________________ 
$ ______  #  ?L   ***`   `        ` ` '  "```  `'` ______________________,,,__________________________________________ 
$ _________________________ __ _________________________________________@F"%L$g#L@L:@.@F _____________________________ 
$ _________________________ JE ________________________________________ $._JL$MLJb@L $._______________________________ 
$ _________________________ :E_________________________________________ "%#* * '" JF " "`_____________________________ 
$ _________________________  $._________________________________________  _ ______  __________________________________ 
$ __________________________ $. _________________________________________ _yL ________________________________________ 
$ __________________________ JL__________________________________________ JF _________________________________________ 
$ ___________________________ $ ________________________________________ ;E  _________________________________________ 
$ ___________________________ 3. _____________________________________,,__ ___________________________________________ 
$ ___________________________ Jk ___________________________________@F``"@.___________________________________________ 
$ ____________________________   _________________________________ JF __ $L___________________________________________ 
$ __________________________ ;#P*%._______________________________ 3L __ @.___________________________________________ 
$ __________________________:$    4L _____________________________ '%L,,#' ___________________________________________ 
$ _______________________@PMW@L___:$ _______________________________  3E. ____________________________________________ 
$ ______________________ $.  "@$@w#` ______________________________ _gNF%L ___________________________________________ 
$ ______________________ $.__ JM@k._ ______________________________ ;FJL %L  _________________________________________ 
$ ______________________ 3L___ $$WM@@@@w.,________________________ ;E 3L  %L _________________________________________ 
$ ______________________ JL __-$.    `"%kJk _____________________ -#.:E$._   _________________________________________ 
$ ______________________ JL___  "%mmmmmM@$. _______________________ .# "$. ___________________________________________ 
$ ______________________ JL____________ $ %L _______________________JL  Jk____________________________________________ 
$ ______________________ 4kggwwmW0W0mmgg@. *L ____________________ :E __ $L __________________________________________ 
$ _______________________  $P _______ ##._________________________    __  ` __________________________________________ 
$ ________________________   _________________________________________________________________________________________ 
$ ____________________________________________________________________________________________________________________ 
$ ____________________________________________________________________________________________________________________ 


```

---

### Post by NightwishFan on 2010-04-11
Here is a tiny python script I made for you. To use:

[LIST=1]
[*]Save it to your home folder.
[*]Open a terminal and type: ```
python sandwich.py
```
[*]It will seem like your normal console, but it should say user@linux-desktop. This means the program is running.
[/LIST]

Try it out tell me what you think!

---

### Post by themarker0 on 2010-04-11
> **NightwishFan said:**
> Here is a tiny python script I made for you. To use:

[LIST=1]
[*]Save it to your home folder.
[*]Open a terminal and type: ```
python sandwich.py
```
[*]It will seem like your normal console, but it should say user@linux-desktop. This means the program is running.
[/LIST]

Try it out tell me what you think!

Yes it does! Thank you so much! You should make it into a full program and add it to the repos, i'm sure many people would have fun with it. Kinda like cowsay.

---

### Post by NightwishFan on 2010-04-11
I am not really a coder, but if you have any requests I will mod the script to fit your needs better. Glad you like it. :D

---

### Post by themarker0 on 2010-04-11
> **NightwishFan said:**
> I am not really a coder, but if you have any requests I will mod the script to fit your needs better.

No its perfect, he makes that joke any time hes sees the computer. So i thought this would be nice.

---

### Post by tica vun on 2010-04-11
You could just do it on [http://xkcd.com/unixkcd/](http://xkcd.com/unixkcd/) :P

---

### Post by themarker0 on 2010-04-11
> **tica vun said:**
> You could just do it on [http://xkcd.com/unixkcd/](http://xkcd.com/unixkcd/) :P

I don't have wireless at school.

---

### Post by NightwishFan on 2010-04-11
Here is a modified version without my credits at the end. Edit: Yes that site is much better than my measly python. :D

---

### Post by Bodsda on 2010-04-11
> **NightwishFan said:**
> Here is a tiny python script I made for you. To use:

[LIST=1]
[*]Save it to your home folder.
[*]Open a terminal and type: ```
python sandwich.py
```
[*]It will seem like your normal console, but it should say user@linux-desktop. This means the program is running.
[/LIST]

Try it out tell me what you think!

Nice attempt. But I think this is overly complicated and very limited. My way would be to make use of that important rule. A sentence always starts with a capital.

Since Linux is case sensitive, 'sudo' and 'Sudo' are two different things, as are 'make' and 'Make'

Heres my solution, this will set everything up to go straight away.

```

cat > Make << "EOF"
#! /bin/bash
echo "What? Make it yourself."
EOF

cat > Sudo << "EOF"
#! /bin/bash
echo "Okay"
EOF

sudo mv Sudo /bin/
sudo mv Make /bin/
sudo chmod a+x /bin/Sudo
sudo chmod a+x /bin/Make

```Just copy and paste that into your terminal and then ask for anything you like. As long as your capitalization is correct, you will get the right response

```

bod@bod-linux:~$ Make me a sandwhich
What? Make it yourself.
bod@bod-linux:~$ Sudo make me a sandwhich
Okay

bod@bod-linux:~$ Make me a woman
What? Make it yourself.
bod@bod-linux:~$ Sudo make me a woman
Okay
bod@bod-linux:~$

```Bodsda

---

### Post by J V on 2010-04-11
I'll make you a small script that will do that...

```
#!/bin/bash
if [ "$1 $2 $3" = "me a sandwich" ]
then
if [ "$USER" = "root" ]
then
eog location/of/sandwhich.png
else
echo "What? Make it yourself."
fi
else
echo "Huh?"
fi
```Name/place it ~/bin/Make

Re-login and voila :)

---

### Post by Tibuda on 2010-04-11
use a Makefile
[http://overbenny.wordpress.com/2009/07/25/sandwich-makefile/](http://overbenny.wordpress.com/2009/07/25/sandwich-makefile/)

---

### Post by tom66 on 2010-04-11
Try making an alias in bash for "make me a sandwich" or similar. Point it to a program like this (Python):

```

#!/usr/bin/python
import os
if os.getuid() == 0:
    print "OK. Ham and cheese or jam and peanut butter?"
else:
    print "No, go make it yourself."

```

I had this working in 9.10 as a little joke, but I can't get it working in 10.04.

---

### Post by themarker0 on 2010-04-11
Wow, thank you all for such an interest, but what nightwishfan gave me its quite nice already.

---

### Post by Phrea on 2010-04-11
[http://forums3.xkcd.com/viewtopic.php?f=7&t=58597&start=0](http://forums3.xkcd.com/viewtopic.php?f=7&t=58597&start=0)

---

### Post by Mr. Picklesworth on 2010-04-11
[http://xkcd.com/unixkcd/](http://xkcd.com/unixkcd/) :)

---

### Post by 3rdalbum on 2010-04-11
The number of different replies given reminds me of a Perl programming contest.

---

### Post by NightwishFan on 2010-04-11
Whats the prize for my nooby python? The fact that somehow it had some use. :popcorn:

---

