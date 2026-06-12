---
title: "can hardware from 1991 still work on today's Linux kernel"
date: 2019-09-09
forum: Ubuntu, Linux and OS Chat
---

### Post by ardouronerous on 2019-09-09
I choose 1991, because it's the birth year of the Linux kernel.

What if I find in an antique shop old computer hardware from the 1991, hardware like monitors, PS/2 keyboards and mouse, printers, etc, still in working order, would this hardware still work on modern Linux systems?

---

### Post by uRock on 2019-09-09
From looking at this, yes. [https://docstore.mik.ua/orelly/linux/run/ch01_09.htm](https://docstore.mik.ua/orelly/linux/run/ch01_09.htm)

---

### Post by webaake on 2019-09-09
The big question will be RAM memory. Some old motherboards will not support bigger RAM modules. But without a GUI you can go a long way.

---

### Post by kansasnoob on 2019-09-09
The big issue is browsing the internet. Even with the lightest of browsers I find much less than a 2mhz cpu and 3GB of RAM to be painfully slow. And it's not the browsers themselves that are to blame. Web content is simply much heavier than anything encountered in the dial-up days. I do however have a few Dell Latitude 2110's (1.6mhz + 2GB RAM) running and they'll even stream videos fairly well with a decent internet connection but opening most web pages is downright painful because I'm used to things moving faster than the blink of an eye.

But I'd almost bet Puppy or AntiX would run on that prehistoric stuff. It just wouldn't be a truly enjoyable experience beyond having a historic chuckle. OTOH a lot of the higher end Intel C2D 10 to 12 year old stuff is now dirt cheap so you can come up with something fairly decent for well under $40. I just snagged a Latitude E6400 for $27 and all it needed was cleaning and a WLAN card which can be had for under $5 (but I have spare parts anyway). I also have spare power adapters and the battery was pooped but if need be a new battery and power adapter can be had for under $20.

---

### Post by kansasnoob on 2019-09-09
For sure old monitors should work as well as PS2 interface keyboards and mice. I have doubts about old printers but I have an old legal size HP scanner that's got to be 18 years old and it still works, although it makes more noise than a 50 year old track loader that's badly in need of a lube job :)

---

### Post by deadflowr on 2019-09-09
Actually, support for 386 processors was dropped sometime back:
[https://www.phoronix.com/scan.php?page=news_item&px=MTI0OTg]("https://www.phoronix.com/scan.php?page=news_item&px=MTI0OTg")

---

### Post by mastablasta on 2019-09-10
only 486 at best. not even sure if the version do have latest kernel.
 DSL works on 486, but has old kernel.

maybe Tiny core
[COLOR=#000000][FONT=Verdana]An absolute minimum of RAM is 46mb. TC won't boot with anything less, no matter how many terabytes of swap you have.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Microcore runs with 28mb of ram.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]The minimum cpu is i486DX (486 with a math processor).[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]A recommended configuration:[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Pentium 2 or better, 128mb of ram + some swap[/FONT][/COLOR]

---

### Post by guiverc on 2019-09-10
Modern 32bit requires 586/686 kernels I thought.

[I][COLOR=#000000][FONT=&amp]"However, Debian GNU/Linux jessie will [/FONT][/COLOR][COLOR=#000000][FONT=&amp]not[/FONT][/COLOR][COLOR=#000000][FONT=&amp] run on 486 or earlier processors. Despite the architecture name "i386", support for actual 80386 and 80486 processors (and their clones) was dropped with the Sarge (r3.1) and Squeeze (r6.0) releases of Debian, respectively. The Intel Pentium and clones, including those without an FPU (Floating-Point Unit or math coprocessor), are supported."
   [/FONT][/COLOR][/I][https://www.debian.org/releases/jessie/i386/ch02s01.html.en](https://www.debian.org/releases/jessie/i386/ch02s01.html.en)

Closer to home

*[COLOR=#000000][FONT=&amp]"However, Ubuntu bionic will [/FONT][/COLOR][COLOR=#000000][FONT=&amp]not[/FONT][/COLOR][COLOR=#000000][FONT=&amp] run on 586 (Pentium) or earlier processors. Support for i586 and lower processors, as well as for i686 processors without the cmov instruction, was dropped in Ubuntu 10.10. Most i686 and later processors are still supported. The Intel Quark is [/FONT][/COLOR][COLOR=#000000][FONT=&amp]not[/FONT][/COLOR][COLOR=#000000][FONT=&amp] supported, due to hardware errata."[/FONT][/COLOR]*
[https://help.ubuntu.com/lts/installation-guide/i386/ch02s01.html](https://help.ubuntu.com/lts/installation-guide/i386/ch02s01.html)

---

### Post by Dev'olution on 2019-09-11
I'd say it'd depend on the distro.

Surely some of the commercial distro's would have legacy support for older CPU's and RAM.

---

### Post by pcfan1234 on 2019-09-23
Old mice (PS/2/serial) and keyboards (ps/2, 5/6 pin) and VGA monitors are working without any problems.
Scanners depend on their driver support. If they are still supported by sane, they work.
Motherboard are a problem because their amount of RAM. Additional, you need a non-PAE kernel.

---

### Post by kansasnoob on 2019-11-21
I just pulled an old ASUS P5NSLI mobo out of the closet recently to set up a PC with a floppy drive to read some old discs and things worked out perfectly using 18.04. I think the kernel developers just recently decided to finally drop support for floppy drives so it might be a good idea to keep an old ISO laying around just in case. That doesn't date back as far as 1991 though - more like circa 2005/2006. The biggest challenge I had was finding an old enough LGA775 CPU in my collection to run on that board. The BIOS was from January 2006. Still being able to run 14 to 15 year old hardware gives Linux some bragging rights I think ;)

---

### Post by jetsam on 2019-11-21
I found 386 beyond economical to use with Linux/BSD back in the 1998-99 era.  I couldn't get X windows working, KDE was out of the question.  

You could make it work, but it would be a lot of work and probably require advanced steps: recompiling kernel modules and what-not.  I'd recommend Gentoo or BSD if you were serious.  Distros meant to compile from source make it easier to target troublesome platforms like an old 386, I think.

It's not worth it in my opinion unless your primary interest is historic or academic or hobbyist oriented...  Recreating Linux's first platforms for a public display at a convention would make it worthwhile to pursue a project like this, and you'd probably be able to find ready helpers and people who want to have a gander at what you're up to...

---

### Post by Skaperen on 2019-11-23
one can always go back and grab an old kernel version for old hardware and start a project team to scan through all the change logs since then to fix all the bugs and adopt new compatible features, starting your own kernel fork.  you might want to fork a custom toolchain, too.  at least, you won't worry about issues of porting to other processors since you'll be focusing on old 386s and maybe some of today's embedded SoCs.

to the extent that an OS tries to keep working with old technology, that may limit its ability to take advantage of new technology.  OTOH there are many technological options of finite resource, today, like raspberry-Pi and such, that we also want to use.  my old Apple II with 48k will never run Linux even though i did manage to implement multitasking on it way back then.

---

### Post by jetsam on 2019-11-23
>  my old Apple II with 48k will never run Linux even though i did manage to implement multitasking on it way back then. 

...

explain yourself. 

...

Please.  ;)

---

