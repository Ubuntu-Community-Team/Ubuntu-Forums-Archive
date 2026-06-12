---
title: "xdotool gives me a headache"
date: 2009-05-05
forum: The Cafe
---

### Post by Amazona aestiva on 2009-05-05
Hello,

I've recently tried to use xdotool without much success.

I would like to type a string for example: ```
this&that
``` but using the command```
xdotool type 'this&that'
```unfortunately the & character is not typed...

I can type it by pressing AltGr+C on my keyboard, but I can't figure out how to do it with xdotool.

I have tried these commands so far:
```
xdotool key alt+c
xdotool key Alt_R+c // Alt_r is unknown
xdotool key AltGr+c // and AltGr too
```

If you could tell me how to do it rightly I'd appreciate it.

EDIT:
I've just downloaded its source and found some defines about keys like:
```
  { "Return", '\n', },
  { "ampersand", '&', },
  { "apostrophe", '\'', },
  { "asciicircum", '^', },
  { "asciitilde", '~', },
  { "asterisk", '*', },
  { "at", '@', },
```
Unfortunately these don't work either. Please help!

Some more details:
I run Intrepid and Xdotool from repo, but current release from its homepage doesn't work better either.
Language of my system is Hungarian. Could it be the trouble? (I've already tried to change locals and keyboard settings)

---

### Post by Amazona aestiva on 2009-07-19
I've finally found out :D

```
xdotool key ISO_Level3_Shift+c
```
This does the trick:D

---

