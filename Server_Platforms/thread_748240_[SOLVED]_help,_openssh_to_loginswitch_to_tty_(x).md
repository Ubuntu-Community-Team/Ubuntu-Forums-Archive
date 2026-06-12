---
title: "[SOLVED] help, openssh to login/switch to tty (x)"
date: 2008-04-07
forum: Server Platforms
---

### Post by Markkreuzz on 2008-04-07
hello,
I have successfully installed **openssh** on my ubuntu server, and i am also able to login using putty from a remote pc on a LAN.  Now my problem is i want to switch tty or terminal so that i can view the processes that has been started on those tty/terminals. Is there a way, or has anyone been able to do this???
I hope someone can give me answers, or point me to the correct direction   T_T

---

### Post by rickyjones on 2008-04-07
I think you can use the screen program for that.

-Richard

---

### Post by pseudo-random on 2008-04-07
Why can you not view the processes on your terminal with ps ax?
What about opening two ssh sessions simultaneously?

---

### Post by Dr Small on 2008-04-07
You can not switch to a TTY while in a ssh session. If you want to start multiple sessions while logged in on the ssh server, use screen.

Dr Small

---

### Post by Markkreuzz on 2008-04-07
well thanks for the quick reply
... will try screen

@pseudo-random
i think ps aux will allow me to view the process. but what i want is  to own the process, like when you press alt+f(3) it will change to that terminal and you can freely manipulate the program as if you are working locally. or is there a way of getting the process to load to the ssh terminal? i dont thind loading 2 ssh sessions will help since the applications are started locally into a tty

well to further explain my problem, i have several programs that is started on my bash.rc and assinged some of them to tty3 and tty4, (e.g. my rtorrent starts on tty3) i tried pressing alt+f3 on putty but no joy. i was hoping that i can change tty easily :confused:

(edited)

> [B][I]Dr Small: You can not switch to a TTY while in a ssh session. If you want to start multiple sessions while logged in on the ssh server, use screen.

Dr Small [/I][/B]

Ouch!.. kinda have a feeling that it is impossible through ssh. Oh well i gues i have to find other ways then. thanks for the replies.

(updated)

Ok i guess it is really a limitation. I have tried screen and i have found a way to start it up on a background, so i updated my bash.rc file.
i am now able to restore session now from an ssh.

Here is what i did (well just for refferrence if someone else have the same problem) 
i installed GNU/screen: apt-get install screen

#started process during startup by adding these command in ~/.bash.rc 

```
screen -S web -md elinks &   
``` 
# this creates  a session named web by the command -S, and putting the session into background using -md and actually executing  the command elinks.

```
screen -r web
```
#this one restores the session into your current screen wether ssh or ttyX, and now i am quite happy. except for some bugs (function keys) when you restore.

for more info on GNU/screen go here [HERE]("http://www.delorie.com/gnu/docs/screen/screen_toc.html")

... thanks for the replies anyways.

---

