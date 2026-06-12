---
title: "Debugging server crash"
date: 2008-07-09
forum: Server Platforms
---

### Post by upnix on 2008-07-09
I have an Ubuntu 8.04.1 server that I'm using as an NFS server.

While under heavy NFS load, the server just dies. When I go plug in a monitor there's nothing on the screen. When I reboot it, there's nothing written down anywhere that any problem had occurred.

Can someone tell me what I can do so that this server leaves behind more information when this happens?


Thanks,
Chris

---

### Post by windependence on 2008-07-09
Unfortunately, if it's a hardware problem, and I think it is, there is nothing you can do to get logs because the server is not expecting it. 

Tell me more about your hardware, how many drives, processors, memory, and other add-ons do you have. What brand and type of hardware is it? 

Finally, have you checked /var/log/messages?

-Tim

---

### Post by promodus on 2008-07-09
pending on the type of failure.

Check kern.log.0, kern.log.1 depends on when the last time you restarted the machine.

The obvious:
You won't get any log of the error if the location of the log resides where the failure is. Example being if the failure is the hard drive, it's difficult to write the log there. (or the disk controller.)

Power failure, where the machine has no power to write the log. 
CPU Failure, no processor ability to process logic.
In some cases memory failure will give no log but even then in some cases you'll still get a log with a memory failure.

Having said all that, an example would be:
```
Jul  8 05:43:06 server kernel: [553162.405479] NETDEV WATCHDOG: eth0: transmit timed out
Jul  8 05:43:06 server kernel: [553162.405485] eth0: Got tx_timeout. irq: 00000000
Jul  8 05:43:06 server kernel: [553162.405487] eth0: Ring at 1286d0000
Jul  8 05:43:06 server kernel: [553162.405488] eth0: Dumping tx registers
Jul  8 05:43:06 server kernel: [553162.405492]   0: 00000000 000000ff 00000003 01e103ca 00000000 00000000 00000000 00000000
Jul  8 05:43:06 server kernel: [553162.405497]  20: 06255300 ff701365 00000000 00000000 00000000 00000000 00000000 00000000
Jul  8 05:43:06 server kernel: [553162.405501]  40: 0420e20e 0000a855 00002e20 00000000 00000000 00000000 00000000 00000000
Jul  8 05:43:06 server kernel: [553162.405505]  60: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
Jul  8 05:43:06 server kernel: [553162.405509]  80: 003b0f3c 00000001 00040000 007f0088 0000061c 00000001 00000000 00007fed
```

In the event you have no log, then use various techniques for quality control. Memtest, cpu burn, some motherboards have stress test utilities, etc.

---

### Post by upnix on 2008-07-10
Thanks for the input guys. I suspect the NIC card, because the previous NVIDIA one I was using would hang. This new one is an Intel one.

I suspect that I would have output on the screen if it didn't go blank on it's own in however many minutes.

This weekend I'll sit in front of it and try to recreate it.


Thanks,
Chris

---

