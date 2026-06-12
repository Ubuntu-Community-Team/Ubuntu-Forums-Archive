---
title: "Ubuntu 7.10 stack security"
date: 2007-10-30
forum: Server Platforms
---

### Post by m00n on 2007-10-30
Hello everyone !!!
I'm running ubuntu 7.10 and i'm facing some problems with overwriting eip in memory.
I have disabled Virtual Adressspace Randomisation
and im compiling my poccodes with -fno-stack-protector flag in gcc.
Im overwriting ebp address successfully but eip cant be overwritten
here is a sample :
eax            0x0      0
ecx            0x31313131       825307441
edx            0xb7fd40d0       -1208139568
ebx            0xb7fd2ff4       -1208143884
esp            0x3131312d       0x3131312d
ebp            0x31313131       0x31313131
esi            0xb8000ce0       -1207956256
edi            0x0      0
eip            0x804848e        0x804848e

please help me why is that like this, any suggestions solutions?
i have to finish my project about the stack overflows and im a newbie. I dont want to install old redhat releases without stack protection, is it possible to do a stack overflow research on ubuntu?
Thanks in advance!

---

### Post by m00n on 2007-10-30
Anyone? :(

---

### Post by m00n on 2007-10-30
I couldn't find any exec-shield presence on system, correct me if it's there, so which kind of patch or security is preventing eip of being overwritten on Ubuntu 7.10 ???

or just give me a clue were to search about ubuntu stack security or whom to contact. i really need it.
thank you.

---

### Post by wirelessmonkey on 2007-10-30
I can't answer your question, but I do suggest you repost it in the Programming forum, you may find more help there.
\

---

### Post by m00n on 2007-10-30
finally ive got it :)))
(gdb) r aaaaaaaaaaaaaaaaaaa
Starting program: /media/disk/tmp/stack aaaaaaaaaaaaaaaaaaa

Program received signal SIGSEGV, Segmentation fault.
0x61616161 in ?? ()
f**cking gcc security drives me crazy :)
for those who will have the same problem
use gcc v3.3 <= it will work

---

