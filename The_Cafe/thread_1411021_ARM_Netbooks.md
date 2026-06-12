---
title: "ARM Netbooks?"
date: 2010-02-19
forum: The Cafe
---

### Post by Gone fishing on 2010-02-19
I read here and there that ARM based netbooks are going to take over. OK I want one - anyone got one is is it good? Where could I get a 10 inch netbook with real hard drive?

How about Ubuntu on an ARM how is it? any problems?

---

### Post by Warpnow on 2010-02-19
The ARM netbooks are mostly still a bit away. A couple to a few months. Ubuntu on ARM won't be a problem, though.

---

### Post by blueshiftoverwatch on 2010-02-19
> **Warpnow said:**
> The ARM netbooks are mostly still a bit away. A couple to a few months. Ubuntu on ARM won't be a problem, though.
Wouldn't running Linux on a non-x86 based architecture result in a lot of compatiblity issues? Proprietary applications like Flash aren't going to work at all. Would most open source applications be usable by just compiling them from source?

---

### Post by Warpnow on 2010-02-19
> **blueshiftoverwatch said:**
> Wouldn't running Linux on a non-x86 based architecture result in a lot of compatiblity issues? Proprietary applications like Flash aren't going to work at all. Would most open source applications be usable by just compiling them from source?

You won't need to compile from source. Debian has had an ARM version for a while now, and Ubuntu has already developed an ARM version, and recently a UNR for ARM.

Adobe has also commited to an ARM port. I am unsure if its been released yet, though.

---

### Post by blueshiftoverwatch on 2010-02-19
> **Warpnow said:**
> You won't need to compile from source. Debian has had an ARM version for a while now, and Ubuntu has already developed an ARM version, and recently a UNR for ARM.

Adobe has also commited to an ARM port. I am unsure if its been released yet, though.
I know that Ubuntu and Debian have ARM versions. But what percentage of the software avalible in the repos (or, Linux software in general) is ported to ARM?

---

### Post by NoaHall on 2010-02-19
> **blueshiftoverwatch said:**
> I know that Ubuntu and Debian have ARM versions. But what percentage of the software avalible in the repos (or, Linux software in general) is ported to ARM?

100%. Except closed source applications.

---

### Post by hessiess on 2010-02-19
As long as an application does not include any assembly language and is open source, it can normally be ported with a simple recompilation. Assuming no platform dependent code is used. I am looking forward to seeing another architecture in the marketplace, X86 is a dump, unfortunately its everywhere.

---

### Post by lykwydchykyn on 2010-02-19
I was wondering this myself; I was looking at ebay the other day and saw the netbook category was full of cheap ARM-based netbooks that were going for around $50-$100 USD (pre-shipping, and most were shipping from Asia) and running WinCE.

I was tempted to get one and see if I could get Debian loaded or something (then I remembered that I don't have that kind of expendable income).  They had pretty low RAM, though.

---

### Post by Mark76 on 2010-02-19
I suspect ARM netbooks (or "Smartbooks", as they're officially known) are one of those "just around the corner" things. 

Like practical fusion, intelligent machines and flying cars.

---

### Post by lykwydchykyn on 2010-02-19
> **Mark76 said:**
> I suspect ARM netbooks (or "Smartbooks", as they're officially known) are one of those "just around the corner" things. 

Like practical fusion, intelligent machines and flying cars.

:confused::confused:

I may be unclear on what a "smartbook" is, but what are these:
[ebay linkage](http://computers.shop.ebay.com/PC-Laptops-Netbooks-/177/i.html?Type=Netbook&Processor%2520Type=!&Processor%2520Speed%2520%2528per%2520Core%2529=Less%2520than%2520500%2520MHz&_dmpt=Laptops_Nov05&_fln=1&_mdo=Computers-Networking&_mspp=&_pcats=58058&_ssov=1&_trksid=p3286.c0.m282)

Looking through them they all claim to have ARM processors and WindowsCE.

---

### Post by Mark76 on 2010-02-19
[http://en.wikipedia.org/wiki/Smartbook](http://en.wikipedia.org/wiki/Smartbook)

I'm not sure what's preventing them from getting to western markets "officially", but I suspect it's an anagram of Neil T.

---

### Post by hobo14 on 2010-02-19
See a round-up of recent ones here: [http://ubuntuforums.org/showthread.php?t=1377293]("http://ubuntuforums.org/showthread.php?t=1377293")

---

### Post by blueshiftoverwatch on 2010-02-20
> **hessiess said:**
> As long as an application does not include any assembly language and is open source, it can normally be ported with a simple recompilation. Assuming no platform dependent code is used. I am looking forward to seeing another architecture in the marketplace, X86 is a dump, unfortunately its everywhere.
Then why do companies say that Linux's market share is too low to support the costly procedure of porting their applications? Do lots of proprietary applications use assembly language or platform dependent code?

---

### Post by mustang on 2010-02-20
> **blueshiftoverwatch said:**
> Then why do companies say that Linux's market share is too low to support the costly procedure of porting their applications? Do lots of proprietary applications use assembly language or platform dependent code?

When you say porting to Linux, that's changing code so that it runs on a particular operating system. When you say porting to ARM, that's changing code so that it runs on a particular ISA (instruction set architecture).

The former is more difficult because most applications are built upon operating system specific libraries. Take DirectX for example. A lot of games need directx to do their graphics. Who writes DirectX? Microsoft. Is it in their interest to port the DirectX library to Linux? Not one bit. It's a substantial investment to port across operating systems. 

The latter is easier because compilers support many architectures. Porting an application to run on a particular architecture can be be simple as changing a switch for the compiler. Some applications use inline assembly (that is, x86 specific instructions) to optimize certain processes in the application (these processes tend to repeat often i.e. they are usually enclosed inside a loop). These cases, which I'm going to guess are the exception and typically found in scientific computing applications, will require some time to change the code.

Hope that makes sense.

---

