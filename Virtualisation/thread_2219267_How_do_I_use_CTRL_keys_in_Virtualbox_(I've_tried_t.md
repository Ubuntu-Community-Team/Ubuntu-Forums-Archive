---
title: "How do I use CTRL keys in Virtualbox (I've tried the 'solution' and it doesn't work)."
date: 2014-04-23
forum: Virtualisation
---

### Post by Bobby_James on 2014-04-23
This has been asked before but the solutions do not work for me.  

I am using Ubuntu 12.10 in VirtualBox. In the terminal, none of the CRTL keys work e.g. CTRL C provides a 'c'; CTRL V provides a 'v'. This happens whether I use the left or right CTRL key.  

People suggest turning off the "show position of pointer when mouse key is pressed". I've done that and it doesn't change anything.  

Any ideas?  Many thanks!

---

### Post by jdeca57 on 2014-04-24
I see this question remains unanswered so I'll give it a shot.
In a bash terminal ctlr C is the way to interrupt a process. [http://stackoverflow.com/questions/6108953/how-does-ctrl-c-terminate-a-child-process](http://stackoverflow.com/questions/6108953/how-does-ctrl-c-terminate-a-child-process) is an example but there are many examples.
That has nothing to do with a VM since on real hardware the behavior is the same in a terminal.
However, in a terminal you can select text with a mouse and then right-click and copy and paste.
And in an application like LibreOffice the behavior of ctrl C and V is normal, be it in a VM or on real hardware.
So actually your question is not really clear, care to explain more?

---

### Post by Bobby_James on 2014-04-27
In non-VM Ubuntu, I run a program from Terminal. I type CTRL-C and the program will stop with a message like: "Interrupt: exiting cleanly."

In VM Ubuntu, I run a program from Terminal, I type CTRL-C and a 'c' appears on the Terminal.

This is the difference. I want to be able to kill programs in VM Ubuntu using CTRL-C.

---

### Post by sudodus on 2014-04-27
It works for me. I run VirtualBox in the host Ubuntu 12.04.4 LTS. The guest happens to be Lubuntu 13.10. In a terminal window I run

```
ping 8.8.8.8
```

and I can interrupt it with ctrl c.

You need to have the window with the guest system active (so that the ctrl c will go there and not into some other window or process).

---

### Post by jdeca57 on 2014-04-27
I didn't install a Ubuntu version on a VM yet because my 14.04 install is so recent but: host ubuntu 14.04 64-bit and guest 14.04 32-bit and ctrl-c works as advertised. It makes me wonder: what was 'the solution'?

---

