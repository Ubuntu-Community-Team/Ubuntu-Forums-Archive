---
title: "Micro-controller programming in GNU/Linux"
date: 2007-11-01
forum: The Cafe
---

### Post by technomaniac on 2007-11-01
Is there any IDE in Linux that helps to write programs for micro-controller like 8051, AVR etc? I need something similar to Keil. Something which lets me write the code in embedded C and simulate the execution. It would also be good if I could burn it to the mircocontroller from within the IDE.

---

### Post by 23meg on 2007-11-01
libc and GCC have been ported to AVR (package *gcc-avr* is in the repos). There's also a simulator called *simulavr*, and AVR programmers such as *avrdude* and *avrp*.

I program an [Arduino]("http://arduino.cc") board, which uses Atmel ATmega168 microcontroller, in Ubuntu. It has its own IDE, which is derived from [Processing]("http://proce55ing.net"), and runs on Ubuntu without problems.

---

### Post by technomaniac on 2007-11-01
Thanks. Will check that out.

---

