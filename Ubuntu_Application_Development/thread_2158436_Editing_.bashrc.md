---
title: "Editing .bashrc"
date: 2013-06-29
forum: Ubuntu Application Development
---

### Post by Sky001 on 2013-06-29
I was trying to install [pythonbrew]("https://github.com/utahta/pythonbrew") so I could stream line my python installations and prevent errors way beyond my understanding. I couldn't finish the process and because I don't know how to edit the .bashrc file to add ```
[[ -s $HOME/.pythonbrew/etc/bashrc ]] && source $HOME/.pythonbrew/etc/bashrc
``` Needless to say, copy paste didn't work. Is there an into to editing that file. I can open the file with vim. ```
vim .bashrc
``` If this isn't the correct forum section. Anyone mind pointing me in the right direction. Also, I'm new to all this, It would great if the answers were geared towards a beginer. 

Thanks

---

### Post by steeldriver on 2013-06-29
You likely would have got a quicker reply in the 'General' or 'Absolute Beginner' section

You can use any text editor - if you are in the standard Ubuntu desktop then use gedit - either as

```
gedit ~/.bashrc
```

from a terminal or by opening the editor from the dash and navigating to the file after turning on 'show hidden files' in the file selection dialog (with ctrl-h)

If you are in a CLI environment then you will probably find nano easier than vi

```
nano ~/.bashrc
```

FYI, to paste from the X buffer into vim you can hit the 'i' key (to get into insert mode) then do a mouse middle-click, then ESC to get out of insert mode and :wq (write and quit)

---

### Post by Sky001 on 2013-07-13
I know it's been a while, but thank you. The suggestions worked. It was very much human error on my part. 

Thanks

---

