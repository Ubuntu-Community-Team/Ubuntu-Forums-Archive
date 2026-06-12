---
title: "Check serial console"
date: 2011-01-18
forum: Server Platforms
---

### Post by Tucznak on 2011-01-18
I am trying to connect to serial console, local one, just to verify than it works, is is possible?

Well, I configure serial console

```
# ttyS0 - getty
#
# This service maintains a getty on ttyS0 from the point the system is
# started until it is shut down again.

start on stopped rc RUNLEVEL=[2345]
stop on runlevel [!2345]

respawn
exec /sbin/getty -L 115200 ttyS0 vt102
```

It is started, now I am trying to connect to the console via minicom, is it possible from machine where the console is running?
If not, how could I check it remotely?

---

### Post by compiledkernel on 2011-01-18
[http://www.fit-pc.com/wiki/index.php?title=How_to_Serial_Console](http://www.fit-pc.com/wiki/index.php?title=How_to_Serial_Console)

This wiki link to FitPC has an excellent examination. 

As the article states though, You should be able to dmesg the grep for tty to see how its configured. 

This is not really an ubuntu proper doc, but then most arent anyway.

---

### Post by Tucznak on 2011-01-18
Well, I think my ttyS0 is configured well, but I'm trying to verify without physical access to box ... is it possible?

---

### Post by GDR! on 2011-01-18
> **Tucznak said:**
> Well, I think my ttyS0 is configured well, but I'm trying to verify without physical access to box ... is it possible?

I think it's not and the closest you can get to this is building a loopback plug (tx connected to rx) like here: [http://zone.ni.com/devzone/cda/tut/p/id/3450](http://zone.ni.com/devzone/cda/tut/p/id/3450)

---

### Post by Tucznak on 2011-01-18
> **GDR! said:**
> I think it's not and the closest you can get to this is building a loopback plug (tx connected to rx) like here: [http://zone.ni.com/devzone/cda/tut/p/id/3450](http://zone.ni.com/devzone/cda/tut/p/id/3450)

I know I can, but i'm doing it remotely, because I'm trying to make work kind of Serial over ethernet stuff ...
So 1st I need to verify, than my serial console is working properly ..

---

