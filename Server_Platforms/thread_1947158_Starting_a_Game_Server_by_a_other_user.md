---
title: "Starting a Game Server by a other user"
date: 2012-03-26
forum: Server Platforms
---

### Post by Teckniel on 2012-03-26
Hello.

I have setup a America's Army 2.5 server for a friend on my server.
The problem is that he cannot start the server 

The command for starting up the server is this:  ./armyops/System/server-bin GLOBAL mapname

If i try it as root everything works fine but with my friends account i get this message:

```

Exception Message:
Exception Error Number: 0
An exception of class NilObjectException was not handled.  The application must shut down.

```Hope anyone can help me.

What my friend only need to be able of is sutdown the AA server and start it

---

### Post by nsnidanko on 2012-03-29
It has something to do with permissions. I am assuming that root account has it and you'r friends accound doesn't. You need to check ./armyops/System/server-bin what directories and such it tries to access and grant appropriate permissions or add your friend's account to the group, which already has permissions on these files and directories.

---

### Post by headvampyre@hotmail.co.uk on 2012-04-01
Apart from the permissions, it could be due to the port being used. Only root can create sockets on ports <= 1024, for other users, it has to be a greater value than that.

---

