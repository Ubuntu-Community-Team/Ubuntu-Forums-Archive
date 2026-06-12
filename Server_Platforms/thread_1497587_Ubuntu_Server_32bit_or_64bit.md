---
title: "Ubuntu Server 32bit or 64bit?"
date: 2010-05-30
forum: Server Platforms
---

### Post by Hawk666 on 2010-05-30
I know this is probably a silly question and I think I already know the answer but I just wanted to check with the community to see if my assumptions are correct or not. I have always been under the impression that it is pointless to run a 64bit OS with a 32bit CPU and vise versa. So, my question is, is this true, I am running an old P4 (32bit obviously) on my "server" it's really just a hobby server, a testing ground for things I wanna mess around with and teach myself, and I want to know if there is any benefit to running Ubuntu server 64bit over 32bit.

---

### Post by Bachstelze on 2010-05-30
> **Hawk666 said:**
> I have always been under the impression that it is pointless to run a 64bit OS with a 32bit CPU

It's not pointless, it's impossible.

> **Hawk666 said:**
> and vise versa.

It used to make sense. It's getting less and less true nowadays, though.

> **Hawk666 said:**
> So, my question is, is this true, I am running an old P4 (32bit obviously) on my "server" it's really just a hobby server, a testing ground for things I wanna mess around with and teach myself, and I want to know if there is any benefit to running Ubuntu server 64bit over 32bit.

Since your CPU is 32-bit only, you cannot run a 64-bit OS, so the question answers itself.

---

### Post by Hawk666 on 2010-05-30
awsome, thats kinda wat i thought, i know it is possible to run a 64bit version of windows on a 32bit CPU and vise versa, maybe not linux tho, I worked in tech support for about 5 years and saw it aaaaall the time, one of the many things that **** me off about big name PC manufacturers

---

### Post by y2kboy23 on 2010-05-31
It's not possible to run any 64-bit software on a 32-bit CPU.  It doesn't matter what operating system it is, its a hardware incompatibility.  Not sure what you saw working as a tech support but sorry to say its not possibly.

---

### Post by Hawk666 on 2010-05-31
well maybe it was just a 32bit OS on a 64bit CPU then

---

### Post by Dayofswords on 2010-05-31
> **Hawk666 said:**
> well maybe it was just a 32bit OS on a 64bit CPU then

which is totally possible :)

---

### Post by Bachstelze on 2010-05-31
> **Dayofswords said:**
> which is totally possible :)

Not on all 64-bit CPUs, though, only those that are specifically backwards-compatible with 32-bit software.

---

### Post by cascade9 on 2010-05-31
> **Hawk666 said:**
>  So, my question is, is this true, I am running an old P4 (32bit obviously) 

Sure its a 32bit only P4? There are 64bit P4s. 

> **Bachstelze said:**
> Not on all 64-bit CPUs, though, only those that are specifically backwards-compatible with 32-bit software.

The vast majority of 64bit CPUs are backward compatible, since x86_64 is. You would have to go looking for exotic architechtures if you want to find a 64bit only CPU.

---

### Post by cusinndzl on 2010-05-31
> **Hawk666 said:**
> well maybe it was just a 32bit OS on a 64bit CPU then

I have a 64-Bit CPU and run a 32-Bit OS because I only have 3GB of RAM. It works fine for me.

---

### Post by Dayofswords on 2010-05-31
> **Bachstelze said:**
> Not on all 64-bit CPUs, though, only those that are specifically backwards-compatible with 32-bit software.

ah, yes, forgot about those pains in the butt

---

### Post by WinstonChurchill on 2010-06-01
> **Hawk666 said:**
> I know this is probably a silly question and I think I already know the answer but I just wanted to check with the community to see if my assumptions are correct or not. I have always been under the impression that it is pointless to run a 64bit OS with a 32bit CPU and vise versa. So, my question is, is this true, I am running an old P4 (32bit obviously) on my "server" it's really just a hobby server, a testing ground for things I wanna mess around with and teach myself, and I want to know if there is any benefit to running Ubuntu server 64bit over 32bit.

I have a laptop with a 3Ghz P4 that is 64-Bit capable. If you're not sure, just burn an Ubuntu x64 ISO and try and boot off of it - if it works, it's a 64-Bit savvy CPU.

One of my favorite things about 64-Bit is that the network counters (that show when you run 'ifconfig') don't overflow - in 32-Bit, they roll over after 4 GB.

---

