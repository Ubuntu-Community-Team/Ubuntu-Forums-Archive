---
title: "Post your Shell Prompt"
date: 2008-08-08
forum: The Cafe
---

### Post by klange on 2008-08-08
Alright, there was a topic for this a while ago, but I can't find it after a ~10 minutes of searching with various different terms, so, here goes another "Post your Shell Prompt"!

Simply post your shell prompt, with any formatting you use, as well as the PS1= line for your shell's rc file.

Here's mine:
```
[**[COLOR="Yellow"]klange[/COLOR] [COLOR="Lime"]acerlaptop[/COLOR] [COLOR="Red"]08/08[/COLOR]  [COLOR="Blue"]1:23[/COLOR]**] ~$ 
```
```
PS1="[\[\033[1;33m\]\u \[\033[1;32m\]\h \[\033[1;31m\]\$(date +%m/%d) \[\033[1;34m\]\$(date +%l:%M)\[\033[0m\]] \w$ "
```

I use this on all of my machines for uniformity.

---

### Post by LaRoza on 2008-08-08
```
\e[01;31m\w\$\e[00m
```

[color="red"]~$[/color] On a black background.

---

