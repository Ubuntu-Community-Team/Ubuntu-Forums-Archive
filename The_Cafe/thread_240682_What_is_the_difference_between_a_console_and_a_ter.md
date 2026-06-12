---
title: "What is the difference between a console and a terminal?"
date: 2006-08-21
forum: The Cafe
---

### Post by drtvasudevan on 2006-08-21
I am translating Ubuntu packages to Tamil (ta) and I am faced with the following problem: how to translate the words terminal and console. First I need to know what is the difference in their meaning. 

The Wikipedia articles on [console]("http://en.wikipedia.org/wiki/Console") and [terminal]("http://en.wikipedia.org/wiki/Terminal") are not so helpful. In fact, the latter article almost says that terminal means a console (and hence vice versa).

Please, geeks, clarify the situation authoritatively - what is the difference between a console and a terminal?

---

### Post by Princey on 2006-08-21
> **drtvasudevan said:**
> I am translating Ubuntu packages to Tamil (ta) and I am faced with the following problem: how to translate the words terminal and console. First I need to know what is the difference in their meaning. 

The Wikipedia articles on [console]("http://en.wikipedia.org/wiki/Console") and [terminal]("http://en.wikipedia.org/wiki/Terminal") are not so helpful. In fact, the latter article almost says that terminal means a console (and hence vice versa).

Please, geeks, clarify the situation authoritatively - what is the difference between a console and a terminal?

There isn't a difference. Both are the same. I think one name gets burrowed from pure unix if I'm not mistaken. But there isn't a difference between the console and terminal window.

---

### Post by mips on 2006-08-21
As far a I know they refer to the same thing in linux. They both seem to be a shortened version of "Terminal Console"

*"The console is the text output device for system    administration messages.  These messages come from the kernel, from    the init system and from the system    logger.*

*On modern small computers the console is usually the    computer's attached monitor and keyboard."*


A terminal in my book usually refers to remote hardware connected to a terminal server via RS-232 or whatever means.


[http://www.webopedia.com/TERM/T/terminal.html](http://www.webopedia.com/TERM/T/terminal.html)
[http://www.webopedia.com/TERM/c/console.html](http://www.webopedia.com/TERM/c/console.html)



Very confusing if you ask me. I would rather use the term Console. I would use 'terminal' when it is a **remote** display & keyboard.

---

### Post by Christmas on 2006-08-21
You can also look [here](http://www.tuxfiles.org/linuxhelp/shell.html). I think both are the same, they are command line interfaces that allow you to enter commands which the shell program (Bash in most of the Linux systems) interprets.

---

### Post by SeanHodges on 2006-08-21
I have read on a magazine once: (therefore must be CONCRETE! ;) )

Terminals are the sessions you get (Ctrl-Alt-F1, each Terminal tab in Konsole, etc)... they are found as tty devices and communicate with the applications.

You have a single console on your computer - it represents the equivelent to the monitor/keyboard/mouse communication.

The console communicates with the terminals.

Similar to X-Windows, where you have an X-Server communicating with your devices, and an X-Client communicating with the applications.

Though I think that people tend to interchange them anyway, and there doesnt seem to be a solid agreement to the difference.

I'm not claiming this to be correct, as I said I read it in a magazine, and haven't ever seen an agreed definition for the terms.

---

### Post by saracen on 2006-08-21
A "Konsole" kan be written with a 'k' and so the term is used by KDE guys who have a global domination konspiracy and want every program in existence to begin with the letter 'k'.  But it's really just a terminal...

---

### Post by tribaal on 2006-08-21
Don't want to confuse, but...

> Terminals are the sessions you get (Ctrl-Alt-F1, each Terminal tab in Konsole, etc)... they are found as tty devices and communicate with the applications.

I use the exact opposite phrasing on a day to day basis, and so do people around me (consoles would be the ttys, terminal the physical thing). But since your set of words don't sound too strange to me either... I conclude they are equivalent :)

Just my 2c...

- trib'

---

### Post by jotagab on 2006-08-21
I use terminal when refering to the command-line application ('terminal emulator' in the Terminal Wikipedia article) and console to whatever application is receiving input from the keyboard, right after boot.
You can have several terminals (across the network or not), but there's only one console, physically attached to the computer.
Cheers!

---

### Post by SeanHodges on 2006-08-21
> **saracen said:**
> A "Konsole" kan be written with a 'k' and so the term is used by KDE guys who have a global domination konspiracy and want every program in existence to begin with the letter 'k'.  But it's really just a terminal...

The problem is, people would laugh at names like Gonsole and Fluxinal...

I love Konsole, but really, what takes so long to load up?!

lol I love choice!

---

### Post by jamadagni on 2006-08-21
I think the consensus is largely that "console" means the physical keyboard and monitor in front of you, and it's only one for one computer, but "terminal" can be physical as well as virtual. 

Your console is allotted a terminal device ID /dev/tty0 and according to [this Wikipedia article]("http://en.wikipedia.org/wiki/Virtual_console_(computer_user-interface)") first paragraph I think upto /dev/tty5 is available to this console all as text terminals. X Windows starts in /dev/tty6. And one can login to a remote computer, and you would still use your monitor and keyboard but the terminal belongs to that other computer. 

I hope this clears things up.

---

### Post by Compucore on 2006-08-21
Well think of it this way. Before KDE, Gnome and other related gui for Ubuntu or other related unixes/linuxes. Console or terminal usually means the command line prompted only on a dummy terminal that was either a amber or green screen that the terminal was hooked up to the computer itself like a vax, minicomputer, mainframe, or supercomputer.  But that is my interpretation of both. When someone  mentions to me I went into the console or terminal. They usually mean by my interpretation just the command line in the GUI interface of linux/unix. 

I used to learn on a vax machine studying Pascal on it in my first semester in college in the 90's.

Compucore

---

### Post by drtvasudevan on 2006-08-22
just to mention that i *am* watching the answers.
till such a time something very definite comes up i shall use them as meaning the same.

---

