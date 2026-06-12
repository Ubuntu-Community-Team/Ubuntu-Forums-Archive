---
title: "Shell server"
date: 2005-06-05
forum: Server Platforms
---

### Post by chris2re on 2005-06-05
If I want to be able tu run eggdrop to use on irc on my ubuntu OS, what do I do? Have never done this before.

---

### Post by j0hnny on 2005-06-06
[QUOTE=chris2re]If I want to be able tu run eggdrop to use on irc on my ubuntu OS, what do I do? Have never done this before.[/QUOTE]
 [http://www.egghelp.org/enhance.htm](http://www.egghelp.org/enhance.htm)

---

### Post by chris2re on 2005-06-08
[QUOTE=j0hnny][http://www.egghelp.org/enhance.htm](http://www.egghelp.org/enhance.htm)[/QUOTE]
That, my friend, has nothing to do with my question!

---

### Post by luckie on 2005-06-08
[http://www.egghelp.org/setup.htm](http://www.egghelp.org/setup.htm)  

that should answer your questions.  just make sure you have tcl installed before you try and complie it.

---

### Post by chris2re on 2005-06-08
have installed eggdrop with sudo atp-get install eggdrop. But how do I get the bot on irc? There is no folders or whatsoever named eggdrop anywhere...

---

### Post by ziggyboy on 2005-06-09
[QUOTE=chris2re]have installed eggdrop with sudo atp-get install eggdrop. But how do I get the bot on irc? There is no folders or whatsoever named eggdrop anywhere...[/QUOTE]
It seems to me that you're not only new to Ubuntu but you're new to Linux altogether. Ok, here goes. I have never used eggdrop so I am not sure where its files are located. But *maybe* the config files are located in /etc/eggdrop. You can see if the command 'which eggdrop' shows you where the binary is. If the eggdrop binary is named something else then I'm not sure I can help you here. Also, if you're using bash, try to type 'egg' then press tab to see if there are any executables showing.

But really, the first thing to try should be: 'man eggdrop'

Cheers.

---

### Post by deuce868 on 2005-06-09
[QUOTE=ziggyboy]
But really, the first thing to try should be: 'man eggdrop'
Cheers.[/QUOTE]

Followed by: locate eggdrop

---

### Post by chris2re on 2005-06-09
The only thing I needed to do, was this:
apt-get install build-essential
=)
Problem solved.

---

