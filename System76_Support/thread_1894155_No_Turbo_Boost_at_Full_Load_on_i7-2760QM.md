---
title: "No Turbo Boost at Full Load on i7-2760QM"
date: 2011-12-11
forum: System76 Support
---

### Post by xanadux on 2011-12-11
On my recently constructed gazelle which has an i7-2760QM, when the processor is at full load (all CPUs at 100%), turbo-boost does not engage beyond the standard multiplier of 24x (2.4Ghz). The processor has turbo-boosts of 8/8/10/11, so at full load it should clock up to 3.2Ghz. The machine is on Oneiric, running the latest 3.0.x kernel (I've also tried 2.6.x and 3.1.x kernels). There is some turbo boosting when less than all four processors are at full load, but it should also accelerate in that case. (Turbo boost was monitored with i7z.)

Any ideas what could be causing this behavior?

---

### Post by isantop on 2011-12-12
The processor will only go to Turbo mode when the Tjunc will allow it. So, if the processor is generating too much heat (It could when running all eight threads at 100%), it won't kill itself in turbo. Turbo mode will typically get engaged when one or two threads are kicking really hard, but the other ones are cruising at or around idle.

---

### Post by xanadux on 2011-12-12
Are you suggesting that the laptop has insufficient cooling to handle the  default processor performance? It's not like the chip is overclocked -- it's in the stock configuration. If this is the case, this should have been clearly advertised. Why would I pay extra for a more powerful processor that I cannot fully take advantage of?

I could see heat being a problem at the maximum multiplier, but at this time none of the cores exceed the non-turbo 24x, max temp seems to be 76C, whereas the processor's maximum temperate is 100C.If I only run four threads at max load, the same thing happens, and all  the processors are approx 70C. If I run only two threads then I can get a  33x average multiplier with temperatures in the 65 - 75 range.

I've only had the machine for a couple of months and I seem to remember being able to run all the cores at max load when I first got it, and I didn't notice that it's behavior had changed until I released that tasks started taking more time... is it not possible that something changed in a recent kernel to scale back the temperature at 80 instead of say 90 or so? Is it possible to set this value in some configuration file?

---

### Post by isantop on 2011-12-13
The processor is rated to perform up to 2.4 GHz at all times, and it uses Turbo mode when it's safe for the processor to overclock itself. 

Turbo mode is handled directly by the processor and chipset, and the OS has no bearing on it at all. It takes in a large number of factors, including system stability, thermal overhead, needs, and others. The determination is made entirely by the hardware, and if the hardware deems it inappropriate for a given set of circumstances, it won't go up. 

Here is Intel's page on Turbo Boost:

[http://www.intel.com/content/www/us/en/architecture-and-technology/turbo-boost/turbo-boost-technology.html](http://www.intel.com/content/www/us/en/architecture-and-technology/turbo-boost/turbo-boost-technology.html)

---

### Post by xanadux on 2011-12-13
Thanks for the reply; unfortunately the information is false and/or useless. I have found numerous reports from other users where Turbo Boost does work in other operating systems under these conditions, and in any case, it is blatantly false to say that "the OS has no bearing on it at all". For starters, the OS process scheduling algorithms obviously dictate processor usage and therefore whether or not the conditions for Turbo Boost to activate are reached (or surpassed). Moreover for linux, the kernel sets the boosting profile (defaults to 'ondemand'), and the OS can prevent turbo boost from engaging completely if it wants to. If you mean to say that turbo boost will disengage if conditions make it dangerous for the processor, that is true.

Do you really think, especially in light of the details of my earlier postings, that I had not read Intel's page on Turbo Boost? If you don't want to help me that's fine, just say so, but please don't waste my time.

---

