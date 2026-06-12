---
title: "One-Second Boot?"
date: 2010-03-08
forum: The Cafe
---

### Post by lakelovers on 2010-03-08
You all probably know about this but it's new to me. While messing around the web I came across this Linux innovation:*Innovators get Linux to boot in 1 second*. Here's a link the article:

[http://www.edn.com/article/CA6720353.html](http://www.edn.com/article/CA6720353.html)

Frankly, I don't know why I would want to boot at near instantaneous time, but I suppose it's important to some people. Anyway, it would be interesting to hear some of your thoughts and comments.

---

### Post by Ric_NYC on 2010-03-08
1... ready!
;)

---

### Post by Ric_NYC on 2010-03-08
> **lakelovers said:**
> You all probably know about this but it's new to me. While messing around the web I came across this Linux innovation:*Innovators get Linux to boot in 1 second*. Here's a link the article:

[http://www.edn.com/article/CA6720353.html](http://www.edn.com/article/CA6720353.html)

**Frankly, I don't know why I would want to boot at near instantaneous time**, but I suppose it's important to some people. Anyway, it would be interesting to hear some of your thoughts and comments.


Why not?

---

### Post by kaldor on 2010-03-08
Link seems dead.

On the topic though, why wouldn't we want a 1 second boot? It's not like waiting 10-60 seconds is fun, we have just gotten used to waiting with computers :)

---

### Post by gsmanners on 2010-03-08
The interesting portion of the article:

> The 1-second-boot-time achievement came in three stages. The first stage was optimization in all the obvious places, including the boot loader. The team could eliminate some of the boot time in the boot loader because the hardware is the same for everything the system boots. The team also omitted many drivers the OS didn&#8217;t need and minimized the OS configuration. &#8220;Even [Linux founder] Linus Torvold admits that Linux is getting pretty bloated,&#8221; says Kaliadin. This first stage got the team members down to a 7-second boot time.

The second stage required an intimate knowledge of the hardware. The Linux boot loader is a serial process. The team&#8217;s epiphany came when the developers realized that they could use DMA (direct-memory-access) methods to parallel many tasks in the boot process.

The DMA agents can move many boot tasks between flash memory and the processor memory and can accomplish this task in the background without processor overhead. &#8220;These days, CPUs have a pretty large cache memory, so they are capable of doing all these things in parallel,&#8221; says Kaliadin. Using DMA and the processor cache saves 3 more seconds, which further reduces the optimized boot time to 4 seconds from 7.

The next logical place to reduce the boot was in the user&#8217;s application, but customers fix and determine that variable. The MontaVista team then looked at the loading of the customer&#8217;s applications. The developers could use the RAM disk that has been available in the Linux kernel since Revision 2.4, but Linux still cached that memory, and that process slowed things down. Since the development of the 2.6 kernel, Linux has supported loading the file system into this RAM disk. &#8220;We ditched the whole buffer scheme and just loaded the customer&#8217;s application into the Linux page-cache memory,&#8221; says Kaliadin.

The second part of this innovation was the developers&#8217; realization that they didn&#8217;t have to load the customer&#8217;s entire application, just the parts that the initial application required to start up. That realization allowed the boot time to near 1 second. &#8220;We made some big advances but then had to find 100 milliseconds here and there,&#8221; he says.

---

### Post by NightwishFan on 2010-03-08
I dont mind 20 seconds, any less wont matter to me as I can just suspend or hiberate.

---

### Post by Post Monkeh on 2010-03-08
i remember my spectrum's funny tunes while it took 5 minutes to load a game. everyone's in such a rush these days

---

### Post by NightwishFan on 2010-03-08
Why wait, there is a difference between that and being patient.

---

### Post by forrestcupp on 2010-03-08
Two questions:

I assume they somehow bypassed getting through the bios?

What was the Linux-based application it loaded?  It must have been very minimal.

No one should think that they booted a whole usable operating system in 1 second.

---

### Post by Post Monkeh on 2010-03-08
> **forrestcupp said:**
> Two questions:

I assume they somehow bypassed getting through the bios?

What was the Linux-based application it loaded?  It must have been very minimal.

No one should think that they booted a whole usable operating system in 1 second.

i'd say it's a 1 second boot from when the actual os starts booting. i don't see how they could bypass the bios since it's needed to run the storage the os would be on. the only other way would be a custom mobo.

my splashtop boots in about 5 seconds (after the bios) to an interface with web browser/email/chat.
never used it myself but i can see how it'd be useful for some people - there's a lot of people these days and that's all they use computers for.

---

