---
title: "Ubuntu Server: How to I run a bash script each time I login"
date: 2016-07-27
forum: Server Platforms
---

### Post by YQ002lc2 on 2016-07-27
Currently, when I log into Ubuntu Server, it displays information like:

Last Login:...
Welcome to Ubuntu....


I want to know how I can edit this to show things like weather, time, a bible verse...  ?

I just don't know where to put my bash script file.....?

I'm familiar with the verse command, but don't know of many other non-graphical commands for making logins a little more interesting?

Thank you!

---

### Post by CantankRus on 2016-07-27
Add to your ~/.bashrc file.
eg I have a section which displays fortune when I use the terminal when not in an Xsession.

I could just add a line...
```
fortune -os | cowsay -f tux | lolcat -s 64
```

but because I usually ssh via phone, I add a section...
```
## fortune when no $DISPLAY
if [ -z "$DISPLAY" ]; then
fortune -os | cowsay -f tux | lolcat -s 64
read
clear
fi
```

Because the phone screen is small I add a "read" command which pauses the output so I can read.
Hitting the Enter key continues on to clear the screen and show the command prompt.

---

### Post by YQ002lc2 on 2016-07-27
Thank you! That is awesome!

---

### Post by howefield on 2016-07-27
And moved to the "*Server Platforms*" forum.

---

### Post by CantankRus on 2016-07-27
There is also [**_[COLOR="#B22222"]archey[/COLOR]_**]("https://github.com/djmelik/archey/downloads") that shows sysinfo.

---

### Post by YQ002lc2 on 2016-07-27
## verse when no $DISPLAY
if [ -z "$DISPLAY" ]; then

verse
verse | espeak

verse
read
fi

:) Thanks again!

---

