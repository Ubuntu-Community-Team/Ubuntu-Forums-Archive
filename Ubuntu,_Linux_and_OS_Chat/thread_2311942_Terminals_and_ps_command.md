---
title: "Terminals and ps command"
date: 2016-01-31
forum: Ubuntu, Linux and OS Chat
---

### Post by big_z2 on 2016-01-31
How come I can't see the processes on other terminals, other then its original terminal. 

So basically, if I start gimp from a terminal, and then run ps, i'm able to see it. However, if i open a new terminal and type ps, i can't see gimp or  its PID. Can someone tell me why  this is happening?

---

### Post by sudodus on 2016-01-31
You can run ```
ps -A
``` or ```
ps -Af
``` to see all processes, including ***gimp*** from another window. See ```
man ps
``` for more details about the command ***ps***.

---

