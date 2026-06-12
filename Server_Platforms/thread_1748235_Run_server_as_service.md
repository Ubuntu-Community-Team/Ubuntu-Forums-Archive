---
title: "Run server as service"
date: 2011-05-03
forum: Server Platforms
---

### Post by megabuffen on 2011-05-03
[LEFT]I just built a server from some old parts and I would like to use it for playing Minecraft with my friends. The question is how do I run it as a service under Ubuntu 11.04? I can start it with this command:
```
java -Xmx1024M -Xms1024M -jar minecraft_server.jar nogui
```
This works fine and I can connect to the server. However, it is left running in the terminal. I would prefer to create some kind of script that would allow me to send commands to start and stop the process, just like I can do with apache or bind.

This is what I'm trying to achieve:
```
service minecraft start|stop|restart
```

Does anyone know how to do this?
[/LEFT]

---

### Post by ian dobson on 2011-05-03
Hi,

Have a look in your /etc/init directory there you'll find configuration files for upstart (the service/deamon controller under ubuntu).

Regards
Ian Dobson

---

### Post by a2j on 2011-05-03
running MC server on some old parts??

but you can try "screen". works fine for me.

---

### Post by kgatan on 2011-05-03
Dont know jack about init scripts but cant you just start the program by ending the command with a "&" to run it in background?

Make a script to find the pid of the program and kill it.

---

### Post by sisco311 on 2011-05-03
> **ian dobson said:**
> Hi,

Have a look in your /etc/init directory there you'll find configuration files for upstart (the service/deamon controller under ubuntu).

Regards
Ian Dobson

+1

@OP

Check out the *Getting Started* and the *Cookbook* sections at [http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

---

### Post by a2j on 2011-05-04
try this

```
screen -d -m -S minecraft java -Xmx1024M -Xms1024M -jar minecraft_server.jar nogui
```

first make sure you have SCREEN installed

```
apt-get install screen
```

to get back to the screen session type
```
screen -r
```

to get out of the screen: Ctrl+A+D

---

