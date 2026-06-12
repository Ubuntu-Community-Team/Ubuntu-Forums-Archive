---
title: "Continually running hard drive; what is my problem?"
date: 2008-06-17
forum: Security
---

### Post by Pepse3 on 2008-06-17
Did a search for this and came up with nothing to help.  So, I have KUBUNTU 8.04 GG LTS and I have noticed for the past 4 or 5 days that the hard drive light is constantly flickering like is it running data or something.  I rebooted my computer and checked my other hard drive with KUBUNTU 7.04 FF and after a minute or so after the computer finishes its basic loading the hard drive light is off.  I would check my windows hard drive but I would have to wait an hour or 2 as AVG would be running its check.  I did install AVGFREE for Ubuntu, Saturday and it has performed daily checks and found no problems.  I had Limewire and thought that it might be the problem (I removed it) but NO.  I also have Limewire on my other hard drive and it is normal.  Are there any terminal commands or anything else to run and try to figure out why this hdd is always running??  I disconnected my ehternet and there was NO change.  Not sure what else to try.

Later. Pepse.

---

### Post by hyper_ch on 2008-06-17
run htop in a terminal and see what processes are running.

---

### Post by Pepse3 on 2008-06-18
First to say........ I forgot to check "instant email notification", otherwise I would have answered sooner.  

  Now altho this is a very fascinating little program I hope to be able to completely figure it out.  Now if I understand you correctly I need to be looking at the CPU % to see what you're saying?  Or is it in the upper right side that states:  172 Tasks (or 169) and 1 running.  Or just look at the programs that scroll by?

Later.  Pepse.

---

### Post by hyper_ch on 2008-06-18
you have all tasks listed there and you can see how much cpu, ram, runtime, .... each process takes. By default it is ordered by cpu.

On the top right you have three numbers for load average. In simple terms it means how much the cpu(s) are used over the last 1 / 5 / 10 minutes. A value of 1 means (sort of) 100% cpu... anything below one is great... anything above 1 means more work than the cpu can just handle right now. However if you have multi core cpus then 100% workload for each would be 2, on quad core it would be 4... just very basically expressed. It get a bit more complicated.

So what you should check is the average load, the current load (that bar on the top left) and the actual processes that use the cpu. Use this to find out which process uses so much of your cpu power (or ram)

---

### Post by Pepse3 on 2008-06-18
hyper_ch,

 Problem solved.  It was the software for mythtv, which I had installed recently and forgot about it.  But, I really appreciate the mention of htop.  It's a nice thing to have.

  I thank you for your time on this.  I thought Limewire was actually the indirect cause of this.

Pepse.

---

