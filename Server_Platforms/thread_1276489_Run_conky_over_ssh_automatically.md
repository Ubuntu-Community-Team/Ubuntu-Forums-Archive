---
title: "Run conky over ssh automatically"
date: 2009-09-27
forum: Server Platforms
---

### Post by virtuoosi on 2009-09-27
Hello,

I have just recently set up conky on my server machine. I run it over 

```
screen ssh -X eclipse
conky --daemonize &
```eclipse being the name of my server. This transfers the conky over ssh to my laptops desktop. 

This command combination works nicely, but I have to enter it manually each time I start my laptop or return from sleep. Also, I run it on screen because I dont want additional terminal windows open. This way I can just issue the command, and close the window and the screen will continue running the ssh connection. 

I would like to start the remote conky automatically when I start up my computer, and I havent been able to figure out how to accomplish this. I have tried all kinds of commands, for example 

```
screen -X eclipse 'conky --daemonize &'
or
screen -X eclipse && conky --daemonize  &
```but none of them works out. If I knew which command to issue, I could make an .sh script and have it run on startup.

Thanks in advance.

---

