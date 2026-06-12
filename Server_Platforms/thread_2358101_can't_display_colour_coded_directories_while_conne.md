---
title: "can't display colour coded directories while connected via ssh"
date: 2017-04-09
forum: Server Platforms
---

### Post by jaytel on 2017-04-09
Hi, I realise that this is a very newbie question and might seem pretty silly to those of you who have used Ubuntu for a long time but I am having problems getting my terminal to display directory names in a different colour to file names while connected to my server via ssh.

When connected to my local machine via a terminal session, directory names display in a blue colour, which makes them stand out as obviously directories and not files but when I connect to my server via ssh, I don't get the blue colour for directory names and all text just appears as black. 

At first, I thought it might have just been a problem with the terminal type not supporting colours via ssh but when I put **echo $TERM** into the terminal I get **xterm-256color** so then I thought that maybe there was a problem with .bashrc or .profile files but there doesn't seem to be anything wrong with them either.  All parts that should be there seem to be there as far as I can tell but I still can't view colours while connected via ssh.

Does anyone have any further ideas about what might be wrong?

Thanks 
Jay

---

### Post by papibe on 2017-04-09
Hi jaytel.

A few thoughts:

To eliminate .bashrc problems try executing the explicit command to see colors instead or relaying on aliases:
```
ls -CF --color=auto
```
or
```
ls -CF --color=always
```

To see if it is the terminal client, try using the same you're using locally: connect from the same machine:
```
ssh localhost
```
If you have colors now, then it is a problem with the terminal/ssh client.

What machine are you connecting from? What is the name of the terminal, and ssh clients?

Regards.

---

### Post by Habitual on 2017-04-09
commands I use frequently in the same situations...

```
type ls
```alias ls="ls -lF" 

and IF it simple must "go", ***without editing***, \escape it via the c-line prefacing it with "\"
```
\ls
```

Alternately without editing, you could declare one, or none using
```
alias ls="ls -lF" 
```

or
```
alias ls=""
```

---

