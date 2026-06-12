---
title: "Reason for 100Hz kernel timer setting?"
date: 2010-12-23
forum: Server Platforms
---

### Post by dbanks on 2010-12-23
Ubuntu Server (at least since 8.04LTS, but let's stick to 10.04LTS for the sake of discussion) uses a 100Hz kernel timer setting.

As the kernel timer frequency is increased, task switching latencies go down at the expense of additional processor overhead (and associated power consumption).  It appears that the "tickless" option (enabled on Ubuntu Server) allows a processor that is idle to mask the timer interrupts in order to save power under low load.

My question is this:  It would seem that a lower kernel timer frequency would be desirable for battery-powered applications while a higher kernel timer frequency would be appropriate for applications like servers that are less power sensitive but more latency sensitive.  However, the fact that the Ubuntu server timer is 100Hz and the Ubuntu desktop timer is 250Hz implies the opposite.

Can anyone shed light as to why the timer setting is 100Hz on Ubuntu Server?  Clearly the decision was made for a reason--it just seems very non-intuitive to me.

Cheers,

Dean

---

### Post by Thirtysixway on 2010-12-30
From [http://www.serverwatch.com/tutorials/article.php/3715071/Ubuntu-Server--Kernel-Configuration-Considerations.htm](http://www.serverwatch.com/tutorials/article.php/3715071/Ubuntu-Server--Kernel-Configuration-Considerations.htm)

> Ticks and HZ

Both kernels support on-demand interrupt timers (CONFIG_NO_HZ=y), or the so-called "tickless" option. This means that during periods of no activity, the system goes into a truly idle state, which is supposed to save on power and cooling.

The server kernel is set to a timer interrupt rate of 100 Hz (CONFIG_HZ=100, CONFIG_HZ_100=y), which means it accepts 100 interrupts per second. Another way to think of this is the kernel looks up and peers around 100 times per second for something to do. The desktop kernel is set to 250 Hz &#8212; lower numbers equal lower overhead and higher latency; higher numbers equal higher overhead and lower latency. Higher numbers generally mean the system feels more responsive, at the price of higher CPU usage. Some processes require more interrupts; for example, video processing and VoIP servers need 1000 Hz. If you need to change the Hz value it requires a kernel re-compile.

Server applications may run better with more interrupts, that's why.

---

### Post by JPorter on 2010-12-30
> **Thirtysixway said:**
> From [http://www.serverwatch.com/tutorials/article.php/3715071/Ubuntu-Server--Kernel-Configuration-Considerations.htm](http://www.serverwatch.com/tutorials/article.php/3715071/Ubuntu-Server--Kernel-Configuration-Considerations.htm)


Server applications may run better with more interrupts, that's why.

Yes, but the opposite of that is what we have here... the server kernel has fewer interrupts per second.

---

### Post by stmiller on 2010-12-30
100Hz the default on 2.6.35-24-generic as well for 10.10 desktops as well. Ugh.

---

### Post by disabledaccount on 2010-12-31
> **dbanks said:**
> My question is this:  It would seem that a lower kernel timer frequency would be desirable for battery-powered applications while a higher kernel timer frequency would be appropriate for applications like servers that are less power sensitive but more latency sensitive.  However, the fact that the Ubuntu server timer is 100Hz and the Ubuntu desktop timer is 250Hz implies the opposite.
This setting has nothing to do with battery saving - although there will be some very little difference in power consumption (propably less than 1%)
More interrupts/sec means better responsivity - each process gets CPU time more often, but for **shorter time**. This can significantly lower the performance, because task switching takes extra time and what is most important: causes CPU pipelines and caches to be reloaded from relatively slow system RAM.
In extreme situation it is possible, that CPU will only be switching tasks, but none of usable code will be executed (similar to "IRQ flood" phenomenon).
On the other side, if You have only one application that supports many clients then  lower task switching frequency can raise performance and responsivity  from client point of view.

So this setting should be balanced for each particular case.

---

### Post by shantanu18 on 2011-12-15
Server needs to give service to multiple client. So server is capable to service more interrupt than desktop.

---

