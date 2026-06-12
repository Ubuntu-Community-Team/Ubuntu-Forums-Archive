---
title: "mantic keyboard problem: wrong letters"
date: 2023-07-30
forum: Ubuntu Development Version
---

### Post by Claus7 on 2023-07-30
Hello,

after today's update I cannot type properly. For example if I type d, then on screen it shows sd. If I type p, I get /p\. If I try to erase what I typed then I get ////. 

Regards!

---

### Post by #&amp;thj^% on 2023-07-30
I turned "numlockx off for Xfce4 that worked for me.
```
setxkbmap -query
rules:      evdev
model:      pc105
layout:     us

```
```
xset q | grep LED
  auto repeat:  on    key click percent:  0    LED mask:  00000002
```
The first entry is Cap Lock the Second is Numlock

---

### Post by Claus7 on 2023-07-30
Hello,

> **1fallen said:**
> I turned "numlockx off for Xfce4 that worked for me.
```
setxkbmap -query
rules:      evdev
model:      pc105
layout:     us

```
```
xset q | grep LED
  auto repeat:  on    key click percent:  0    LED mask:  00000002
```
The first entry is Cap Lock the Second is Numlock

thank you *1fallen* for your prompt response. Some additional info:
a) trying to connect to ubuntu box saw this problem
b) two restarts, trying in each one to type some characters, same problem
c) entered another user and saw the same response: couldn't type the correct characters/letters
d) closing computer
e) attempting a third fresh boot, things are working as normal

In the meantime:
```
setxkbmap -help

```
> Usage: setxkbmap [options] [<layout> [<variant> [<option> ... ]]]
Options:
  -?, -help           Print this message
...
  -**query**              Print the current layout settings and exit
...

> 
NAME
       xset &#8208; user preference utility for X
...
q       The q option gives you information on the current settings.


the results I'm getting are exactly the same as yours, from both commands. I suppose that this is because now things are back to normal.
In case this happens again, I will try to issue the command: numlockx off, and see what will happen.

Regards!

---

