---
title: "kill Process inquires --need help"
date: 2011-03-12
forum: Ubuntu Studio
---

### Post by MODYSAMA on 2011-03-12
Hello,
I have many question. It'd be great to get reply.
OS: Kubuntu 10.10
     ```

sok@sok-HP-ProBook-4520s:~$ pidof motion
24986
sok@sok-HP-ProBook-4520s:~$ pidof 24986
sok@sok-HP-ProBook-4520s:~$ sudo su
root@sok-HP-ProBook-4520s:/home/sok# kill 24986
[B]root@sok-HP-ProBook-4520s:/home/sok# pidof /bin/sh /home/sok/Scripts/check.sh
24982 7386 3749 3590 1439[/B]
root@sok-HP-ProBook-4520s:/home/sok# kill 24982
root@sok-HP-ProBook-4520s:/home/sok# 
```.
**Q1**: Why **pidof /bin/sh /home/sok/Scripts/check.sh**
           return several ids and the first one only is one, which is used to kill the process. 
**Q2**: What is that several ids stand for?
**Q3**: what *kill option grantee ending the process?*
.
Thanks in advance.
New Linux beginner.

---

### Post by ankspo71 on 2011-03-12
Hi,
> Q2: What is that several ids stand for?
My guess is that there are multiple instances of /bin/sh running at the same time. Certain scripts can also run multiple instances of /bin/sh, so maybe that is what /home/sok/Scripts/check.sh was doing?.

> Q1: Why pidof /bin/sh /home/sok/Scripts/check.sh
return several ids and the first one only is one, which is used to kill the process. 
Maybe all except one instance of /bin/sh have already ended before you issued the kill command, or you killed /home/sok/Scripts/check.sh and that ended all instances of /bin/sh

Just a note: it is probably best to use pidof for one process name at a time so it is less confusing, or maybe use the command 'top' in the terminal at the same time to see what is happening.

> Q3: what kill option grantee ending the process?
```
killall <program-name>
```
Or see these links: _[Controlling Processes]("http://linux.die.net/Linux-CLI/controlling-processes.html")_ and  _[Commands using pidof]("http://www.commandlinefu.com/commands/using/pidof")_

More info on pidof and killall:
[http://linux.die.net/man/8/pidof](http://linux.die.net/man/8/pidof)
[http://linux.die.net/man/1/killall](http://linux.die.net/man/1/killall)

PS, you can read the same information in the terminal by typing:
```
man pidof
man killall
```

Hope this helps.

---

