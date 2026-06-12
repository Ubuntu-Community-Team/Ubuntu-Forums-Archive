---
title: "Zombie"
date: 2009-07-29
forum: Security
---

### Post by MindController on 2009-07-29
When I opend System Monitor, i saw one process. Name is sh and status is _Zombie_. I just want to know what is it. I'm start using ubuntu 8.04 for last two weeks ago. I'm really n00b.

---

### Post by wojox on 2009-07-29
I think it's a python process that didn't get shut down all the way. Find the PID and try to kill it.

---

### Post by juancarlospaco on 2009-07-29
LOL, no!
Its a living dead process, waiting for parent *(father)* process to end.
Its normal :)

---

### Post by MindController on 2009-07-29
> **wojox said:**
> I think it's a python process that didn't get shut down all the way. Find the PID and try to kill it.
How can i did it? Please show me the link or the book to do that. But i click the process kill, it didn't work. Thanks wojox u help me a lot :D

---

### Post by XCan on 2009-07-29
I assume you're using the System Monitor to see that the status' Zombie. The fifth column should say "ID". That's the PID you're looking for. If killing it from the system monitor doesn't work, open up a terminal and type
```
 kill -9 ID 
```

---

### Post by movieman on 2009-07-31
> **XCan said:**
> If killing it from the system monitor doesn't work, open up a terminal and type
```
 kill -9 ID 
```

If I remember correctly, a zombie process is already dead and waiting for its parent process to clean up: hence the 'zombie'. It should already have released its address space and other resources so it's using little in the system other than the process ID.

Typically it's the result of a programming error in the parent and will go away when the parent exits.

---

