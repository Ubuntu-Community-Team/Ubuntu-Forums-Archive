---
title: "[SOLVED] Service Dependency"
date: 2008-08-17
forum: Server Platforms
---

### Post by Bang Crash on 2008-08-17
I've tried searching but I can't find an answer to this question :(

How do I make the start up of one service dependent on another?  e.g. I have service that should only start after another service has already started.

Thanks in advance.

---

### Post by fahadsadah on 2008-08-17
I believe there is an order to init scripts-I will try to find you it.

---

### Post by fahadsadah on 2008-08-17
In the relevant rc*.d dir, every file is named S&^, where & is a number and ^ is the name.

---

### Post by Bang Crash on 2008-08-17
Thanks for the information, that looks promising.  It's a bit beyond my current knowledge though, are you able to point me in the direction of some more detailed instructions?

---

### Post by mbeach on 2008-08-17
can you be more specific as to what the services are?

why not just start them both in the same script in the appropriate order?

---

### Post by cariboo on 2008-08-17
Have a look at his tutorial here:

[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

It's not quite what you are looking for, but it gives a good view of the init process.

Jim

---

### Post by Bang Crash on 2008-08-18
Thanks everyone, between those two posts I have managed to figure out what to do and successfully edited the rc*.d files.

The two applications that I wanted to do this for were SqueezeCenter and MusicIP, the MusicIP service has to start before the SqueezeCenter service otherwise the two won't talk to each other.  Custom start up scripts are beyond me at the moment, but I'll get there 8)

---

### Post by fahadsadah on 2008-08-19
You are welcome.

Please mark this thread as solved.

---

