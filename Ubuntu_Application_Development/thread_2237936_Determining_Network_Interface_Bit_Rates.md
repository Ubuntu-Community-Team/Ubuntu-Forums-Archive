---
title: "Determining Network Interface Bit Rates?"
date: 2014-08-04
forum: Ubuntu Application Development
---

### Post by von Corax on 2014-08-04
I'm writing a program in C that wants to measure the traffic volume on each network interface, as System Monitor does. Can someone tell me which library calls I want and where they're documented?

Thanks.

---

### Post by tgalati4 on 2014-08-04
I would get friendly with netstat:

```
man netstat
```

---

### Post by von Corax on 2014-08-05
netstat is certainly one option. I'm really looking for library calls, though, as I eventually want to run this on a stripped-down system on an SBC so I'd prefer to avoid dealing with forking overhead, mode switches or relying on utilities that I may have removed to save space.

---

### Post by tgalati4 on 2014-08-05
[http://unix.stackexchange.com/questions/21503/source-code-of-netstat](http://unix.stackexchange.com/questions/21503/source-code-of-netstat)

[http://src.gnu-darwin.org/src/usr.bin/systat/netstat.c.html](http://src.gnu-darwin.org/src/usr.bin/systat/netstat.c.html)

I challenge you to write a shorter algorithm (in C) to perform the same functions.

---

### Post by von Corax on 2014-08-05
Thank you. I shall have to read that code in depth this evening, but at first blush it appears to be exactly what I want. With any luck I can mark this thread solved by the end of the week.

---

### Post by tgalati4 on 2014-08-06
I would spend several hours running *netstat* with all of it's functions and get comfortable using it.  Then if it does not do something that you want, you can modify the source code and recompile it (call it netstat2) or look at the System Monitor source code and see how it works.  

There are so many network monitor tools:

```
apt-cache search network monitor
```

---

### Post by ofnuts on 2014-08-15
I have a script that tells me plenty of things about the network just by looking at the contents of /proc/net/dev

---

