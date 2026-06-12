---
title: "All Processes SLEEPING (help?!)"
date: 2009-08-19
forum: Server Platforms
---

### Post by antdgar on 2009-08-19
[[IMG]http://img193.imageshack.us/img193/3615/picture4soa.png[/IMG]]("http://img193.imageshack.us/i/picture4soa.png/")

Now my server's SWAP is under high use than before:
[[IMG]http://img20.imageshack.us/img20/2582/picture5urd.png[/IMG]](http://img20.imageshack.us/i/picture5urd.png/)


** How to wake them up? And why is everything sleeping??**

---

### Post by regala on 2009-08-19
> **antdgar said:**
> 

Now my server's SWAP is under high use than before:
[[IMG]http://img20.imageshack.us/img20/2582/picture5urd.png[/IMG]](http://img20.imageshack.us/i/picture5urd.png/)


** How to wake them up? And why is everything sleeping??**

take a deep breath, don't panic, this is **normal**
at a time, on a "regular" box, not too loaded, only a few (really 1, 2 or 3-4...) processes are running, because when a process's got nothing to, it sleeps, waiting for something to happen (and still, this is **normal** :)

By the way, a process appears in this chart as sleeping, when, the monitor sees it's flagged "SLEEPING", at the very end of the small "lapse" of time it takes to estimate percentage of CPU usage. This means really nothing in nearly every case.

---

### Post by antdgar on 2009-08-19
> **regala said:**
> take a deep breath, don't panic, this is **normal**
at a time, on a "regular" box, not too loaded, only a few (really 1, 2 or 3-4...) processes are running, because when a process's got nothing to, it sleeps, waiting for something to happen (and still, this is **normal** :)

By the way, a process appears in this chart as sleeping, when, the monitor sees it's flagged "SLEEPING", at the very end of the small "lapse" of time it takes to estimate percentage of CPU usage. This means really nothing in nearly every case.

But why does it say SSH and NX are sleeping? I am using those right now... doing commands through SSH. And using NX to view the desktop...
Even though I'm using the processes it still says sleeping :confused:

---

### Post by grantemsley on 2009-08-19
Sleeping basically means it's sitting there waiting for something to do.

On modern machines (especially ones that have only a few users) the system is sitting there waiting most of the time.  Even if you are using those processes, they may take your input, process it, and go back to sleep in a matter of milliseconds.

---

### Post by credobyte on 2009-08-19
You are sitting at the classroom - unless teacher asks you to show your homework, you are sleeping ( tough, you are still listening to her and waiting for a <command> ) :p

---

### Post by scorp123 on 2009-08-19
> **antdgar said:**
> But why does it say SSH and NX are sleeping? I am using those right now... doing commands through SSH. And using NX to view the desktop...
Even though I'm using the processes it still says sleeping :confused: You know what they say ... If you're _really_ good at something, you could do it in your sleep :D

---

### Post by regala on 2009-08-20
> **antdgar said:**
> But why does it say SSH and NX are sleeping? I am using those right now... doing commands through SSH. And using NX to view the desktop...
Even though I'm using the processes it still says sleeping :confused:

a sleeping process's not to be compared to a sleeping man

---

