---
title: "What i do to get like this terminal"
date: 2015-09-13
forum: Ubuntu/Debian BASED
---

### Post by secofshadow on 2015-09-13
hi all>>what i do to get like that terminal    [http://im55.gulfup.com/kfvchs.png](http://im55.gulfup.com/kfvchs.png)

---

### Post by Bucky Ball on 2015-09-13
*Thread moved to **General Help**.*

That is a transparent terminal and that is easy to do. I think what you're after is the desktop wallpaper behind it. It is not part of the terminal.

How you go about setting your terminal's transparency level depends on what terminal you're using.

---

### Post by secofshadow on 2015-09-13
no i mean like the name color how i can change my name like that

how i chnage my name to like that name i thing its code

---

### Post by Lars Noodén on 2015-09-13
The shell prompt is set by the variable $PS1.  If you set that to something colorful then you have colors:

```

PS1='\[\e[0;31m\]\u\[\e[m\] \[\e[1;34m\]\w\[\e[m\] \[\e[0;31m\]\$ \[\e[m\]\[\e[0;32m\]'

```

The colors are set by using [ANSI escape codes](https://en.wikipedia.org/wiki/ANSI_escape_code) in the prompt.  So, [choose a color](http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/x329.html).  The **\e** stands for the Escape character.  For the others, such as **\u** and  **\w**, see the section on [prompting in the bash manual](http://manpages.ubuntu.com/manpages/trusty/en/man1/bash.1.html) by typing *man bash*

---

### Post by flaymond on 2015-09-13
or this one, step-by-step - [http://mylinuxbook.com/ubuntu-command-line-prompt-colour/](http://mylinuxbook.com/ubuntu-command-line-prompt-colour/)

---

### Post by secofshadow on 2015-09-13
i dont under stand  :(plz give me code with my name :r00ted

---

### Post by flaymond on 2015-09-13
Just type the code given by Lars Nooden with/without export to try -

```

PS1='\[\e[0;31m\]\u\[\e[m\] \[\e[1;34m\]\w\[\e[m\] \[\e[0;31m\]\$ \[\e[m\]\[\e[0;32m\]'


```

if you like that color and wanna keep it for next boot session, simple type this -

```
echo "export PS1='\[\e[0;31m\]\u\[\e[m\] \[\e[1;34m\]\w\[\e[m\] \[\e[0;31m\]\$ \[\e[m\]\[\e[0;32m\]'" >> ~/.bashrc 
```

and if you to delete it, open the .bashrc file with text editor, and delete the ```
echo export PS1='\[\e[0;31m\]\u\[\e[m\] \[\e[1;34m\]\w\[\e[m\] \[\e[0;31m\]\$ \[\e[m\]\[\e[0;32m\]'
``` in it.


I suggest to try take a look about basic bash commands, especially *man*.

---

### Post by secofshadow on 2015-09-13
where i type it ??!:     [http://im56.gulfup.com/MQR0LA.png](http://im56.gulfup.com/MQR0LA.png)  [http://im56.gulfup.com/JrsfQn.png](http://im56.gulfup.com/JrsfQn.png) plz  help ?idont under stand and forgiveme my enghlish is bad

give me the hole .bashrc with my name r00ted and i need him like that [http://im55.gulfup.com/kfvchs.png](http://im55.gulfup.com/kfvchs.png) color plz give the hole .bashrc and edit it with my name like the picroot@r00ted:~#

---

### Post by flaymond on 2015-09-13
You can type it in your terminal, by copy & paste it. However, I don't really understand what you're saying, what do you mean by *hole?*

---

### Post by Bucky Ball on 2015-09-13
I'm using lxterminal but have used others. Open terminal, Edit, Preferences, Appearances get me there. How about you?

---

### Post by secofshadow on 2015-09-13
no idont have Appearances

---

### Post by flaymond on 2015-09-13
Which Terminal do you use? Is it GNOME shell? XFCE4 terminal? Konsole? Lxterminal? Mate?

---

### Post by secofshadow on 2015-09-13
i use terminal kali linux

---

### Post by howefield on 2015-09-13
Thread moved.

---

### Post by ajgreeny on 2015-09-13
One of the links given has already shown you how to get a coloured prompt by a simple edit of one line in the hidden file **.bashrc** in your home.

[http://mylinuxbook.com/ubuntu-command-line-prompt-colour/](http://mylinuxbook.com/ubuntu-command-line-prompt-colour/)

There is no simpler way to do this that I know of, though of course you now tell us you are using Kali which may be different from Ubuntu.

---

### Post by Bucky Ball on 2015-09-13
Yes. You might have better luck [here]("https://forums.kali.org/"). Kali is Debian based but not supported here as not one of official Canonical flavours.

---

