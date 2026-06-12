---
title: "For Memory Monitoring freaks..."
date: 2005-11-29
forum: The Cafe
---

### Post by jdong on 2005-11-29
I've been getting pretty annoyed recently about people claiming program X is a RAM hog, citing either ps aux output or gnome-system-monitor stats as evidence....


I want to point out that neither output provides an accurate picture of how much of RAM usage can be attributed to each program. For example, see the attached screenshots. System Monitor claims that Java (Azureus in this case), Firefox, and Xorg together are using over 730MB RAM at the moment! This kind of figure brings alarm to anyone's face, guaranteed. However, take a look at the overall resources view. Only 342MB RAM is being genuinely used by applications (as opposed to the cache, etc) altogether.

To further demonstrate the point, how much RAM is actually freed when I shut down Azureus? 30MB, not 300MB. Firefox? 40MB, not 173MB. These true freed values seem to be much better predictors at memory usage.


Am I saying that Azureus, Firefox, and Xorg are conservative with memory? Not really. There are times where even 30MB or 40MB is unacceptable, like on systems with limited amounts of RAM. Also, at times Azureus does indeed use 50-100MB of RAM, when dealing with several simultaneous torrents with hundreds of connections each.

All I'm saying is to carefully investigate your charts and graphs before haphazardly drawing conclusions... Rant over. :)

---

### Post by jdong on 2005-11-29
Note that this is not just a Linux thing... The numbers that the Windows Task Manager gives you also suffer from this very issue... If you read the MSDN article on exactly what "Mem Usage" and "VM Size" means under Task Manager or Performance Counters, you'd be pretty shocked indeed... One is just an overglorified heap size calculation, while the other simply tracks how many MB of RAM has been touched by the process within the past X milliseconds, which really doesn't have much to do with true "usage". I believe that in a multitasking, multithreaded OS with shared libraries left and right, it is pretty difficult to track "true" memory usage.

---

### Post by GreyFox503 on 2005-11-29
I noticed this a while back.  In the System Monitor, I added the sizes listed in the virtual memory column, and they easily exceeded the amount of RAM in my system, and I was using virtually no swap space.

If you click on a process, then at the bottom of the screen click "more info" it will give additional statistics.  Under memory usage, it looks like "RSS" is a more realistic number for how much memory is actually being used.  If anyone knows where these numbers come from I'd like to know.

---

