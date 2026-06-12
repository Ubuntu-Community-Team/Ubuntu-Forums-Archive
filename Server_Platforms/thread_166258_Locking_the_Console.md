---
title: "Locking the Console"
date: 2006-04-26
forum: Server Platforms
---

### Post by charlie. on 2006-04-26
As the IT Manager in my business, I frequently get up and leave my desk. I always lock my windows PC if I am away from my desk - so I don't have to log out. How do I lock a Linux terminal? An exposed terminal with root privileges is not something that I want to leave available to anyone who can type.

I know that I can use Ctrl+Z to suspend a job, such as EMACS, but Linux terminates these jobs if I force a logout. How do I lock the terminal so that I can resume later (with my password) without stopping all the jobs in progress.

Additionally, as a side note, if I lost my SSH session for some reason, could I log in again and resume the jobs that were in progress? With Remote Desktop, I can login later and resume a session that may have been lost due to connection problems or other reasons. (I can also leave a session that might be doing something that takes time, such as an update, and log in later to view the results)

---

### Post by steele.campbell on 2006-04-26
[QUOTE=charlie.]As the IT Manager in my business, I frequently get up and leave my desk. I always lock my windows PC if I am away from my desk - so I don't have to log out. How do I lock a Linux terminal? An exposed terminal with root privileges is not something that I want to leave available to anyone who can type.
[/QUOTE]

I would check out vlock -- it should be in the universe repos. I just installed it, and it works like a charm on console or virtual terminal (Say PuTTY for example).

---

### Post by localzuk on 2006-04-26
To lock a console, take a look at vlock. [http://www.die.net/doc/linux/man/man1/vlock.1.html](http://www.die.net/doc/linux/man/man1/vlock.1.html)

I would also suggest taking a look at screen as this allows for sessions to be reconnected to.

---

### Post by charlie. on 2006-04-26
Thanks...

I installed vlock and tried it out. It said that my TTY (What does that acronym stand for anyway?) was not a Virtual Console (VC) and that it could not be securely locked - but locked it anyway. Hmm... strange...

What is "screen"? Words like that are not usefull Google terms and, you guessed it, "apt-cache search screen" returned way-too-many results!

---

### Post by nocturn on 2006-04-26
[QUOTE=charlie.]Thanks...

I installed vlock and tried it out. It said that my TTY (What does that acronym stand for anyway?) was not a Virtual Console (VC) and that it could not be securely locked - but locked it anyway. Hmm... strange...

What is "screen"? Words like that are not usefull Google terms and, you guessed it, "apt-cache search screen" returned way-too-many results![/QUOTE]

This is the one:
p   screen                                  - a terminal multiplexor with VT100/ANSI terminal

---

### Post by imagine on 2006-04-26
[QUOTE=charlie.]TTY (What does that acronym stand for anyway?)[/QUOTE]
Teletypewriter.

[QUOTE=charlie.]What is "screen"? Words like that are not usefull Google terms and, you guessed it, "apt-cache search screen" returned way-too-many results![/QUOTE]
$ **apt-cache show screen**
$ **sudo apt-get install screen**
$ **man 1 screen**

Screen is useful to detach and reattach your terminals and to have multiple terminals when you're logged in remotely.

Login and start screen.
Run a program, eg ls /var.
Press Ctrl+a c. That creates a new screen terminal.
Run another program, eg pico ~/.bashrc.
Press Ctrl+a d. That detaches screen from your session and sends it into the background.
Logout.
Go to another computer and login.
Type screen -r and your screen terminals will be reattached.
Press Ctrl+a n or Ctrl+a p to cycle through your terminals.
Type exit to terminate this screen session including all its terminals.

---

### Post by charlie. on 2006-04-27
Now THAT is support! Thanks imagine.

Cool! Now I can REALLY sound like a geek without people catching me out with ancient acronyms that I don't know! (Not only that, I can do it asynchronously and reattach my geek sessions too!)

"Screen" is part of the GNU project, is it not?

Will the C-a shortcut interfere with the C-a shortcut (home) in GNU Emacs?

---

