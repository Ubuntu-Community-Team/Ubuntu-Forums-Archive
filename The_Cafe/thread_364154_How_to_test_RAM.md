---
title: "How to test RAM?"
date: 2007-02-17
forum: The Cafe
---

### Post by blastus on 2007-02-17
I've just ordered RAM modules from the shop I bought my computer from. The chips should be in next week. I'm trading in the chips I have now for the new ones. I'll be installing them myself. My motherboard supports PC1600 and PC2100 DDR (DDR1) but the memory I've ordered is PC3200. They told me that the memory chips should work...the memory will downgrade to PC2100. I currently have 2 x PC2700 and will be replacing them with 2 x PC3200.

The shop uses a program called GoldMemory to test RAM modules. They said that I should run this program and let it run for at least an hour. I know Ubuntu includes a program called memtest86+ and I just tried it today.

My question is, is running memtest86+ enough to assume that there is nothing wrong with the modules? Is it possible for the modules to pass all the tests yet not work properly (i.e. is it possible for there to be some kind of timing issue or something that would cause the modules to pass the tests but perform very poorly or consume an abnormal number of CPU cycles?)

Also, I'm not an expert in RAM testing, but it seems to me that ANY program that runs under an OS (like HCI Design's MemTest program for example) that claims it can test RAM modules is full of it. Since memory management is a function of the kernel, it cannot be controlled by programs that run under an OS or am I missing something?

---

### Post by maxamillion on 2007-02-17
memtest86+ in my opinion and in my personal history of troubleshooting is the best way to test ram.

is it possible for RAM to pass memtest86+ and still have errors? no, I don't think that is possible.

---

### Post by macogw on 2007-02-17
memtest86+ tests every bit on the ram, so unless your ram modules are spontaneously generating new bits, you should be alright

it'll take all day though

---

### Post by codejunkie on 2007-02-17
> **blastus said:**
> I've just ordered RAM modules from the shop I bought my computer from. The chips should be in next week. I'm trading in the chips I have now for the new ones. I'll be installing them myself. My motherboard supports PC1600 and PC2100 DDR (DDR1) but the memory I've ordered is PC3200. They told me that the memory chips should work...the memory will downgrade to PC2100. I currently have 2 x PC2700 and will be replacing them with 2 x PC3200.

The shop uses a program called GoldMemory to test RAM modules. They said that I should run this program and let it run for at least an hour. I know Ubuntu includes a program called memtest86+ and I just tried it today.

My question is, is running memtest86+ enough to assume that there is nothing wrong with the modules? Is it possible for the modules to pass all the tests yet not work properly (i.e. is it possible for there to be some kind of timing issue or something that would cause the modules to pass the tests but perform very poorly or consume an abnormal number of CPU cycles?)

Also, I'm not an expert in RAM testing, but it seems to me that ANY program that runs under an OS (like HCI Design's MemTest program for example) that claims it can test RAM modules is full of it. Since memory management is a function of the kernel, it cannot be controlled by programs that run under an OS or am I missing something?

as far as i know memtest86 just checks the memory for defects, i don't think it will notify you if there are any timing issues but i could be wrong. i have personally had problems on some motherboards when using faster memory modules though and trying to downgrade them like your suggesting, and the system was totally unstable. but yet the memory showed no errors with memtest86 or the windows memory diagnostic tool so speaking from personal experience id say if your motherboard only supports pc2100 don't use the faster memory. i have seen some motherboards that can work just fine like this but it's a crap shoot, and it can end up costing you more money replacing the memory modules again if you have a tricky motherboard and that shop won't refund your money.

---

### Post by Polygon on 2007-02-17
> **macogw said:**
> memtest86+ tests every bit on the ram, so unless your ram modules are spontaneously generating new bits, you should be alright

it'll take all day though

it doesnt take all day though, does it? it just loops forever doesnt it?

---

### Post by maxamillion on 2007-02-17
> **Polygon said:**
> it doesnt take all day though, does it? it just loops forever doesnt it?

Yes, it does loop forever but depending on the ram speed it can take up to a few hours to complete a test.

---

### Post by mcduck on 2007-02-18
..and running memtest once through is worth nothing. It really should be left to run at least over night, as sometimes it can take hours of repeated testing until errors start to appear.

---

### Post by az on 2007-02-18
> **blastus said:**
> 
My question is, is running memtest86+ enough to assume that there is nothing wrong with the modules? Is it possible for the modules to pass all the tests yet not work properly (i.e. is it possible for there to be some kind of timing issue or something that would cause the modules to pass the tests but perform very poorly or consume an abnormal number of CPU cycles?)

The ram does not consume cpu cycles, but needs a certain mnumber of clock cycles each time it is used.  In your case, the new ram will be ready after, say, two clock cycles, but will only be read by the motherboard after three.  The ram is more efficient than the rest of the system.  When you have a timin mismatch, the motherboard will use the timing of the slowest ram.  If it can't, it won't work.  

So as far as memtest, if your timings are compatible, the ram will pass the test just fine,  If there is a timing mismatch, you will find out right away.

And the later tests that memtest performs involve writing to the memory and waiting thirty minutes to see if the ram is pattern is still there.  It does this several times with different patterns.  So it does not loop around and around, it just keeps doing differnt tests, using different patterns.  It can take a couple of days (with a lot of ram or a slow computer) to do one loop.



> **blastus said:**
> 
Also, I'm not an expert in RAM testing, but it seems to me that ANY program that runs under an OS (like HCI Design's MemTest program for example) that claims it can test RAM modules is full of it. Since memory management is a function of the kernel, it cannot be controlled by programs that run under an OS or am I missing something?

Memtest only takes up a few kilobytes of ram, and all the rest is tested.  Loading your OS and all the stack plus the ram tester does indeed take up a lot of ram that cannot be tested properly.

---

### Post by blastus on 2007-02-23
Hello everyone, thanks for all the help!

I just got the new RAM and ran memtest86+ and everything works. I let it run for 10 hours while I was at work and there were no errors. I haven't noticed anything unusual in CPU usage or experienced any stability issues so far. The shop assured me even before I placed the order for the PC3200 memory that if it didn't work they would take it back and we could try PC2700. I traded in my old memory for the new and got a nice discount. 

I now have 2GB and am quite happy :)

---

### Post by maniacmusician on 2007-02-23
> **blastus said:**
> Hello everyone, thanks for all the help!

I just got the new RAM and ran memtest86+ and everything works. I let it run for 10 hours while I was at work and there were no errors. I haven't noticed anything unusual in CPU usage or experienced any stability issues so far. The shop assured me even before I placed the order for the PC3200 memory that if it didn't work they would take it back and we could try PC2700. I traded in my old memory for the new and got a nice discount. 

I now have 2GB and am quite happy :)
congratulations :)

---

### Post by linux_kid on 2007-02-23
memtest86+ just gives me headaches, it's gone from my menu.lst

---

