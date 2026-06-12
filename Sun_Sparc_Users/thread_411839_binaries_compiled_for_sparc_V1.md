---
title: "binaries compiled for sparc V1"
date: 2007-04-17
forum: Sun Sparc Users
---

### Post by erm67 on 2007-04-17
I managed to install xubuntu on my old Ultra2 and it works like a charm. I am wondering why are all binaries compiled for the Sparc V1 architecture? Since Ubuntu only supports Ultra sparc there aren't compatibility reason for that, and since the sparc V1 (if I am not wrong) doesn't even make use of MUL and DIV (hardware mulktiplication and division) it is usually slower. There is the so called sparc V8+ ( the same as Sparc V9 but with 32bit) to take full advantage of the Ultrasparc architecture in a 32bit userland.
Is this going to change? 
I also tried to compile a kernel by myself since my ultrasparc has 2CPU and the kernel on xubuntu is single processor, but I couldn't even use make --menuconfig because ncurses-dev was not installed (and I could not find it anywhere). Had to vi .config to turn SMP on.

---

