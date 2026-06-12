---
title: "is there such a thing as a terminal clock?"
date: 2008-05-04
forum: The Cafe
---

### Post by chucky chuckaluck on 2008-05-04
you know, a clock for the terminal/console, without having to install something else just so you can use the clock, and not something you have to fly to the moon just to get working. something that you just go 'clock' for and voila - "i'm already late!"

---

### Post by Ozor Mox on 2008-05-04
```
date
```

---

### Post by chucky chuckaluck on 2008-05-04
i mean something that keeps on ticking. date is a one shot deal.

---

### Post by elmer_42 on 2008-05-04
```
date
date
date
date
```
Rinse, repeat. :) :P

---

### Post by chucky chuckaluck on 2008-05-04
i suppose i could just get a nice clock for my wall.

---

### Post by klange on 2008-05-04
```
while true; do date; done
```

or better yet:
```
while true; do date; echo -ne "\033[1F"; sleep 1; done
```

---

### Post by Dr Small on 2008-05-04
Like this?
```
#!/bin/bash
# clock - A bash clock that can run in your terminal window. 

while true;do clear;date +"%r";sleep 1;done 


```

---

### Post by chucky chuckaluck on 2008-05-04
> **Dr Small said:**
> Like this?
```
#!/bin/bash
# clock - A bash clock that can run in your terminal window. 

while true;do clear;date +"%r";sleep 1;done 


```

our winner! thanks.


edit: that sure is clean looking.

---

### Post by Ozor Mox on 2008-05-04
Wouldn't you have to keep a separate terminal window or tab open for that though? And then typing 'date' when you want to know the time is probably just as fast as switching windows/tabs :)

---

### Post by DBO on 2008-05-04
watch -n 1 echo ""

---

### Post by chucky chuckaluck on 2008-05-04
> **Ozor Mox said:**
> Wouldn't you have to keep a separate terminal window or tab open for that though? And then typing 'date' when you want to know the time is probably just as fast as switching windows/tabs :)

it's just one more xterm. i don't see it as much of a problem. i could always just use *date* if it became one.

---

### Post by Ozor Mox on 2008-05-04
> **chucky chuckaluck said:**
> it's just one more xterm. i don't see it as much of a problem. i could always just use *date* if it became one.

Ohh split screen terminals, didn't know that was possible!

---

### Post by chucky chuckaluck on 2008-05-04
> **Ozor Mox said:**
> Ohh split screen terminals, didn't know that was possible!

it's xmonad, a tiling wm. i think it's available in hardy (it wasn't in gutsy). there's also awesome, wmii, dwm and a bunch of others (ion3, ratpoison, etc).

---

### Post by bettlebrox on 2008-05-04
U can set your prompt to tell the time (it updates after each carriage return).

---

### Post by ubuntu-freak on 2008-05-04
This is the most interesting thread on page 1 of the cafe, seriously. I also like the thread concerning the MS keyboad and mouse seemingly made for Kubuntu as well, though.
 
Nathan

---

### Post by original_jamingrit on 2008-05-04
My user account:
```
PS1="\[\e[01;34m\][\t]\[\e[01;32m\]\W $\[\e[00m\] "
```
My root account:
```
PS1="\[\e[01;34m\][\t]\[\e[01;31m\]\W #\[\e[00m\] "
```

Copy and paste into your terminal, and if you like it, also you .bashrc.  Updates whenever an operation is finished, so maybe not as useful as a regular clock.

---

### Post by soapytheclown on 2008-05-04
> **chucky chuckaluck said:**
> it's xmonad, a tiling wm. i think it's available in hardy (it wasn't in gutsy). there's also awesome, wmii, dwm and a bunch of others (ion3, ratpoison, etc).

could also use terminator which is just a normal terminal u can split horizontally or vertically as many times as you like :)

---

### Post by init1 on 2008-05-04
watch -n 1 date

---

### Post by mali2297 on 2008-05-05
If you use mpd, then ncmpc has a nice clock-screen (if compiled with this option).

[[IMG]http://hem.bredband.net/kaw/ncmpc/images/thumb-ncmpc-tux3.png[/IMG]]("http://hem.bredband.net/kaw/ncmpc/images/ncmpc-tux3.png")

---

### Post by rolnics on 2008-05-05
very interesting thread, i'm amazed at what can so simply be done through terminal!

on another note, how would you set one of the suggestions to run every time you opened a terminal?

---

### Post by chucky chuckaluck on 2008-05-05
> **mali2297 said:**
> If you use mpd, then ncmpc has a nice clock-screen (if compiled with this option).

[[IMG]http://hem.bredband.net/kaw/ncmpc/images/thumb-ncmpc-tux3.png[/IMG]]("http://hem.bredband.net/kaw/ncmpc/images/ncmpc-tux3.png")

i used to use ncmpc like a clock, but i've found just tossing a bunch of music in a file called 'playlist', then playing it with mplayer, to be much simpler. as i already need mplayer, it's one less app, so to use it just for a clock would be like getting a drink of water out of a fire hose.

---

### Post by elmer_42 on 2008-05-05
Now I just have to get this working in conky.

---

### Post by mkeuter on 2012-05-02
I use dclock, although not in terminal, using xmonad it does the trick you're looking for. Other option could be xclock, cairo-clock did not work.

---

### Post by nothingspecial on 2012-05-02
[IMG]http://img696.imageshack.us/img696/7058/necrov.png[/IMG]

---

