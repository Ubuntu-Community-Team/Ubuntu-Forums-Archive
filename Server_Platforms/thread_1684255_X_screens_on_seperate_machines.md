---
title: "X screens on seperate machines"
date: 2011-02-08
forum: Server Platforms
---

### Post by mikmikmikmik on 2011-02-08
What i want to do is ssh to another machine and have gui interface as if i was using the other machine. anywhere from a single program like just nautilus run from the server on my machine to a desktop like i was sitting at it helps. Also being able to display something on the server would be nice.

---

### Post by cjhabs on 2011-02-08
> **mikmikmikmik said:**
> What i want to do is ssh to another machine and have gui interface as if i was using the other machine. anywhere from a single program like just nautilus run from the server on my machine to a desktop like i was sitting at it helps. Also being able to display something on the server would be nice.

If you ssh to the remote server using:
ssh -X remote_server_name
the -X will allow you to tunnel gui apps back to your machine.
You can then simply run "nautilus".
If you want to run the whole desktop then you'll need to run "gnome-session" and embed it within xnest as you are already running a window manager on your local machine.

---

### Post by mikmikmikmik on 2011-02-09
thanks! it works.
 but... how do i embed within an xnest?

---

### Post by cjhabs on 2011-02-11
> **mikmikmikmik said:**
> thanks! it works.
 but... how do i embed within an xnest?

Easiest way is to fire up Xnest (note the cap X) with something like:
Xnest :3
(man Xnest will give you details on the parameters)
Then fire up a program to run in the Xnest session using "-display xnest_host_ip:3.0" 
e.g.
Xnest :3&
ssh -X remote_host
xterm -display ip_xnest_host:3.0
or
gnome-session -display ip_xnest_host:3.0
etc

---

### Post by doogy2004 on 2011-02-11
You may want to check out NoMachine NX - [http://www.nomachine.com/select-package.php?os=linux&id=1](http://www.nomachine.com/select-package.php?os=linux&id=1)

---

