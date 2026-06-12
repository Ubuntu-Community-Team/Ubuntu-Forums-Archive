---
title: "stuck on recording"
date: 2008-04-09
forum: Server Platforms
---

### Post by amai on 2008-04-09
have configured/changed Ip address of server 7.10 from DHCP to STATIC.

using the command
sudo vi /etc/network/interfaces

but i am getting stuck with the cursor flashing and at the bottom left corner have RECORDING.

How do i proced from, tried restarting but still same problem

---

### Post by Dr Small on 2008-04-09
If vi is too complicated for you, try using nano.

---

### Post by amai on 2008-04-12
Thanks nano worked fine

Learning VI in the meantime

---

### Post by Dr Small on 2008-04-12
Consider learning Vim, as it is generally easier than Vi. :)

These three links should help you in your quest to learn Vim:
[http://www.apmaths.uwo.ca/~xli/vim/vim_tutorial.html](http://www.apmaths.uwo.ca/~xli/vim/vim_tutorial.html)
[http://www.biochem.ucl.ac.uk/~mckenzie/vim/tutorial.html](http://www.biochem.ucl.ac.uk/~mckenzie/vim/tutorial.html)
[http://blog.interlinked.org/tutorials/vim_tutorial.html](http://blog.interlinked.org/tutorials/vim_tutorial.html)

Dr Small

---

### Post by garfonzo on 2008-04-12
Just to chime in (even though the above replies answer the question) would this work:

<ESC>
:w  <ENTER>
:q  <ENTER>

Won't that write the file, then exit you from vi? 

I'm not sure why I like vi, it is kinda hard, but it's fun too. Nano or Vim are, indeed, easier.

Cheers!

---

### Post by Dr Small on 2008-04-12
Yes, that will save and close Vi(m).
But to edit the file, press "i" then edit.

Then you can save and exit.
Vi just seemed harder and overly mind consuming, so I tried Vim and love it :)

---

### Post by andguent on 2008-04-13
Recording mode usually pops up if you press the q without doing a : (colon) first. Vi is without a doubt, worth learning.

When learning VI(M) here are a few tips:
* When in doubt, mash the ESC key multiple times to reset whatever you just accidentally pressed.
* 'u' (lowercase) will undo your ENTIRE last insert session
* '.' (period) will repeat your entire last insert session
* '~' (tilde) will toggle uppercase/lowercase on whatever letter you are positioned over
* 57G (#G) will go to line 57 -- handy for 'syntax error on line 57' debuging
* :%s/find/replace/gc (colon, percent, s....) will take all places that have 'find', and replace it with 'replace, prompting you each time.
* Dump the following code into ~/.vimrc for pretty color formatting: ([http://nosheep.net/story/vi-color-schemes/](http://nosheep.net/story/vi-color-schemes/))
```
syntax on
set nocompatible
color darkblue
```

---

