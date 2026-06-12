---
title: "Server hijacked...help"
date: 2010-10-20
forum: Security
---

### Post by tottenham12712 on 2010-10-20
[http://pharmalert.zoomshare.com/1.html](http://pharmalert.zoomshare.com/1.html)

Basicly my webserver picked up a virus and just need some imput on what you guys think....its currently shut down and will do no harm but i think a clean install is the way to go

---

### Post by wojox on 2010-10-20
Nothing beats a clean install. What services are you running?

---

### Post by rookcifer on 2010-10-21
From the link:

> The pharmacy hijacker breaks into public web sites by performing a dictionary attack on the root user password.

Looks like you were using a weak root password.  Hopefully a lesson learned, especially if you are running a server.

Do a fresh install.

---

### Post by mainerror on 2010-10-21
To prevent this in the future I recommend deactivating password login and setting up authentication via key.

In the reverse order of course.

---

### Post by tottenham12712 on 2010-10-21
yeah:( it was a very weak key....what did you mean by auth key?

---

### Post by mainerror on 2010-10-22
[This]("http://www.debian-administration.org/articles/152") article pretty much sums it up.

---

### Post by tottenham12712 on 2010-11-06
thank you, for the time being i put a 14 charc password in so im pretty sure itll be ok untill i figure that out

---

