---
title: "SSH logout - keep programs running"
date: 2006-05-24
forum: Server Platforms
---

### Post by tkjacobsen on 2006-05-24
Is it possible to exit a ssh-sesseion and keep some of the programs running on the server. 

Eg if i want to start a download on my server at home from my university via ssh, then exit the ssh session, and the download is continuing until i get home.

Or should i use another service..

Thanks in advance.

---

### Post by koolguynet on 2006-05-24
Type Ctrl Z <Enter>
They bg 

That lets the process run in the background.  Now you are safe to exit.

---

### Post by koolguynet on 2006-05-24
Sorry my typing that command sucked.  Here you are

Ctrl Z  <Enter>
bg <Enter>

Now it is in the background.

---

### Post by tkjacobsen on 2006-05-24
Then how do i resume the program, if i want to use it again.. This could from another terminal on another client

---

### Post by imagine on 2006-05-24
**bg** sends the process into background and **fg** brings it back into foreground.


You can also use a program like **screen** to get virtual terminals which you can detach and reattach from and to your session. Check [http://ubuntuforums.org/showthread.php?p=959188#post959188](http://ubuntuforums.org/showthread.php?p=959188#post959188)

---

### Post by hagen00 on 2006-05-25
this works for me...example is to start a java program

```
nohup java myprogram &
```

Nohup tells it "not to hang up" or something like that, look at the man page and the & puts the process in the background.

---

### Post by Schmots on 2006-05-25
Easier way...

screen.

apt-get install screen

first time you run it. just

screen

when you want to detach from it use 
ctral+a d

to reconnect later like when you ssh back in
screen -x

have fun

---

### Post by tkjacobsen on 2006-05-25
should screen run on the server or the client

---

### Post by tkjacobsen on 2006-05-25
nohup did the job. Thanks everyone.

---

### Post by mlind on 2006-05-25
definetly use screen. You can re-attach (deattached) screen sessions, like
continuing from where you last time left. And leave tasks running too.

---

### Post by MJN on 2006-05-25
[quote=tkjacobsen]nohup did the job. Thanks everyone.[/quote]

...although with nohup you won't be able to resume control (like you implied you wanted).

Mathew

---

### Post by tkjacobsen on 2006-05-26
i responded a little to soon when i told nohup was good for the job.. It only does some of the jobs... 

Is there a good screen howto somwhere???


edit: i found this myself if anyoun should be interested:
[http://jmcpherson.org/screen.html](http://jmcpherson.org/screen.html)

---

### Post by mlind on 2006-05-26
[QUOTE=tkjacobsen]i responded a little to soon when i told nohup was good for the job.. It only does some of the jobs... 

Is there a good screen howto somwhere???


edit: i found this myself if anyoun should be interested:
[http://jmcpherson.org/screen.html](http://jmcpherson.org/screen.html)[/QUOTE]

Thanks for the article, I only used screen few years back on Solaris OS and 
I had forgotten this stuff already.

---

