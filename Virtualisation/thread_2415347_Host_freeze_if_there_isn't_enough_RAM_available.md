---
title: "Host freeze if there isn't enough RAM available"
date: 2019-03-24
forum: Virtualisation
---

### Post by maltacastro on 2019-03-24
Hello,
Every time I start a VM, I have to make sure that the amount of free RAM is at least equal to the VM allocated RAM. If it doesn't, the host system freezes and I have to do a hard reset. So, I usually have to close some windows before launching the VM, in order to free up some RAM. Sometimes, I forget to do that and the system freezes. That's annoying.
Is there anything I can do to solve that?

Host:
Ubuntu 18.04 
8 GB RAM
SSD

Guest:
Windows 7
2 GB RAM

---

### Post by TheFu on 2019-03-25
What do the log files show?  Any errors or warnings?
How is the memory usage?
How is the swap usage?
What are the major settings for the virtual hardware provided to the VM?

Can you prove the claim or is it purely coincidence and some other issue is really the problem.

Oh ... and if would be helpful to know which hypervisor is being used, since few people are expert at more than 1.

---

### Post by maltacastro on 2019-03-26
Thanks for your help. 

> Oh ... and if would be helpful to know which hypervisor is being used, since few people are expert at more than 1.
VirtualBox

> What do the log files show?  Any errors or warnings?
How is the memory usage?
I get no errors or warnings, just an unresponsive system. I am attaching two log files. As you can see, in the freeze case, 1391MB were available. After a hard reboot, lots of RAM were available and it worked flawlessly. 

> 
How is the swap usage?
```

Swap:       8375804
cat /proc/sys/vm/swappiness
60

```

> 
What are the major settings for the virtual hardware provided to the VM?
I believe those information are in the log files. Is that right or do you need any more info?

> Can you prove the claim or is it purely coincidence and some other issue is really the problem.
I am posting in the forum just now, but I am observing this behavior for a long time and it is very consistent. I am pretty sure it only freezes if there is not enough RAM, but I don't know how I could prove that.

---

### Post by TheFu on 2019-03-26
I'm not too familiar with vbox. Sorry.

Today my laptop locked up, hard, so I walked to a different room and used a different computer to ssh back into it.  It was fine.  I killed the problem process, walked back to the laptop and everything was fine. Just trying to point out that a lock up isn't always a lockup, just because the GUI isn't working.

With that, hopefully someone else will be able to help.

---

### Post by 1clue on 2019-03-27
I'm not especially versed with vbox either, but you shouldn't get this type of behavior. 


[LIST=1]
[*]Can you give me the results of **free -h**?
[*]Do you have another system from which you can try to ssh into the host in question?
[*]Have you noticed any particular VM causing the problem more than others?
[*]How long have you waited after the lockup to see if it recovers?
[*]Do the VMs have GUI interfaces or are they server-only?
[/LIST]

In some ways this reminds me of a number of things, most of which could be part of the problem.

[LIST=1]
[*]Running out of memory, especially if there is no swap configured on the system, or if the volume is not actually used for some reason.
[*]Some disk error on the guest, and VB is trying to figure out what's going on.
[*]Some remote mount, like NFS or CIFS, which is not available (host down) or is having problems causing network hangs.
[/LIST]

If it's the GUI on your host that locks up, then you could have a fully functional VM running but be unable to reach it. If you can ssh into the host from another system then we can get more information about what's happening.

While it has been years since I saw the problem, I've seen NFS shares where the server had issues either staying up or maintaining the share, where clients would hang forever until the share showed up. It was a crazy hang, multitasking seemed to stop dead on the guest. Not saying that I suspect that the same issue exists today with NFS, only saying it's possible for a network mount to bring a system to its knees. If it were still an issue there would be a lot of discussion about it on the net.

---

### Post by maltacastro on 2019-04-08
> Can you give me the results of **free -h**?
```
free -h
              total       usada       livre    compart.  buff/cache  disponível
Mem.:          7,8G        4,3G        2,8G        260M        661M        3,0G
Swap:          8,0G        1,0G        6,9G


```
> Do you have another system from which you can try to ssh into the host in question? 
Yes, I could try that next time.
> Have you noticed any particular VM causing the problem more than others?
I don't have many VMs, the other one uses much less RAM.

> How long have you waited after the lockup to see if it recovers?
About 20 minutes.
> Do the VMs have GUI interfaces or are they server-only?
It has GUI interface.

> Running out of memory, especially if there is no swap configured on the  system, or if the volume is not actually used for some reason.
My feeling is that the system was supposed to use swap, but for some reason, it doesn't.

---

