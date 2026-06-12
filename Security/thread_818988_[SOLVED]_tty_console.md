---
title: "[SOLVED] tty console"
date: 2008-06-04
forum: Security
---

### Post by janskey on 2008-06-04
Hi,

Is it possible to to see what a user is doing when he logs in through ssh?

ex.
# w
USER TTY    FROM    LOGIN@   IDLE   JCPU   PCPU WHAT
choy pts/0 10.0.1.61  13:11 1.00s  3.53s  0.26s sshd: choy [priv]
naka pts/2 10.0.1.27  20:04 11:49m 0.27s  0.05s sshd: naka [priv]

Is it possible to see what he is doing? can i send naka a message? Thanks!

---

### Post by tamoneya on 2008-06-04
```
man wall
sudo wall message.txt
```

---

### Post by unutbu on 2008-06-04
To see all processes owned by naka:
```
ps -U naka -u naka uww
```

---

### Post by janskey on 2008-06-05
so wall can send messages. how about looking on what he is doing in the terminal?

---

### Post by Dr Small on 2008-06-05
> **tamoneya said:**
> ```
man wall
sudo wall message.txt
```
I always used 'write'. Me and tronyx used that alot to talk to Sega when we were rooting eric's box. :D

---

### Post by janskey on 2008-06-05
> **Dr Small said:**
> I always used 'write'. Me and tronyx used that alot to talk to Sega when we were rooting eric's box. :D

thanks for write..i tried and works smoothly..but how about looking on what a user is doing on his terminal? i know 'w' would show what a user is doing. any other tools?

---

### Post by Dr Small on 2008-06-05
> **janskey said:**
> thanks for write..i tried and works smoothly..but how about looking on what a user is doing on his terminal? i know 'w' would show what a user is doing. any other tools?
Not really, I don't know off hand. But to see a list of proccesses the user is running, you can try:
```
ps aux | grep *user*
```

---

### Post by janskey on 2008-06-05
yes i tried that and i tried "history" also. my problem is that we have the same user account. so its hard to track down. :)

---

### Post by unutbu on 2008-06-05
Have naka open up a terminal with

```
gnome-terminal -e "script"
```

This will record a transcript of the terminal session in a file called (by default) typescript.

Then you can view the typescript with

```
cat typescript | less -r
```

---

### Post by janskey on 2008-06-07
is there any other tool that i could sniff up on what he is doing except typescript? what if we have the same user account? thanks...

---

### Post by daleus on 2008-06-08
I once logged on as the other user, ran screen, and didn't close the screen session, when they logged in, I did screen -r, and I could see what they were doing in realtime, even messing with what they were typing. They did not have to load screen or anything.

I havn't been able to make this work since.

---

