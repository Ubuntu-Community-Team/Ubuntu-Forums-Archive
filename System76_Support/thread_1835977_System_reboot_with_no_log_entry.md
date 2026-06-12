---
title: "System reboot with no log entry"
date: 2011-08-30
forum: System76 Support
---

### Post by Mart on 2011-08-30
I recently purchased a LeoX2 and I have a problem with it rebooting under load.  Usually rsync will crash the system within a few minutes.

System
LeoX2
i7 processor
24G Memory Vengance Corsair
Western Digital 2TB SATA / 64MB C Drive
Ubuntu 11.04 64bit

When the system crashes / reboots there are no log entries in the dmesg or syslog that reference the crash. 


Tested the memory with memtest86+and after many passes (8) I found 2 bad chips.  I'm assuming after heat built up they started failing.

I've replaced the bad chips but the system still shuts down so I've tested the processor with mprime and watched the sensors for heat issues (watch -n .5 sensors) but the heat isn't building up past 70C and the system usually reboots within 15 minutes.

I have a request into support.  Any testing options or points in the right direction would be greatly appreciated.

Thanks,
Marty

---

### Post by isantop on 2011-08-30
Try disabling Hyperthreading in the BIOS configuration. This is caused by a bug we have in the current Leopard firmware. We're currently working on a fix, and you can disable hyperthreading to prevent panics until then.

---

### Post by Mart on 2011-08-30
Thanks

I turned off hyper-threading and reran mprime.  Results are the same.  

Core i7 (Nehalem) 
Intel(R) Core(TM) i7 CPU 960 @ 3.20GHz

Torture test > 1 (small fft little memory tested) Runs in both.

Torture test > 2 (large fft some memory tested) halts within 5 minutes on both.

Torture test > 3 (mix of fft lots of memory tested) halts within 5 minutes on both.

linux _stress_ runs with no issue.

memtest86+ reports no errors.  (I am rerunning this with the memtest86+ bootable cd and will update the thread in the morning.)

What makes this even more confusing is the fact I can run it all day as long as it doesn't try to transfer any large files or do a lot of processing.

Any other suggestions for tests?  

Thanks
Mart

---

### Post by isantop on 2011-08-30
Make sure turbo mode is disabled as well. I seem to remember that causing issues as well.

---

### Post by Mart on 2011-08-31
memtest86+ returned no problems after 11 passes.

I disabled turbo in the bios under the processor as well.  So now hyper-threading and turbo are disabled.

The system is running mprime now and after a half hour has not crashed so it looks promising.  I'll report back after a few hours.

I'm glad it isn't a hardware issue.

Thanks for the help isantop.

---

### Post by Mart on 2011-08-31
The system hasn't rebooted all day thanks again for pointing me in the right direction.

Would it be possible to get on a list to be notified when the fix / patch is released?

Thanks,
Marty

---

