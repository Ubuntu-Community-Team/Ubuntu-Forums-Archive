---
title: "Network events/traffic monitor required"
date: 2008-06-25
forum: Security
---

### Post by skew on 2008-06-25
I have a question regarding the monitoring of incoming and outgoing internet events on my system.

  I use Guarddog as my firewall and have for a long time, preferring it to Firestarter. This is just MY personal preference so I'm not interested in a drawn out debate on the merits of one firewall over another.  I do though, like the way Firestarter reports in real time any unsolicited access attempts as well as which IPs and their clients are currently using any active open port/s.  Is there a program for Hardy which I can run which will provide a similar real time monitoring service like that currently provided in Firestarter?  Something which doesn't take a degree in computer science to install, run and most importantly, one that provides a data set that's fairly easy to interpret.   I did find a program which appears to provide the kind of service I'm interested in but it's currently in a early alpha stage (Watchdog [http://www.simonzone.com/software/watchdog/](http://www.simonzone.com/software/watchdog/)). I'd prefer something more established, possibly some application that already tried and true and resting in the Ubuntu repositories?  

Any thoughts?

Thanks

---

### Post by kevdog on 2008-06-25
Few things

Are you looking specifically for a gui?

Do you want to monitor in real time?

Would a command line output similar to top be sufficient?  

Basicallly you are looking for inbound/outbound traffic and rejected packets to be logged by the firewall and this logged and displayed somewhere.  I used to use Guarddog, I don't remember if there is an option to log?  Is this one of the options this program allows.

---

### Post by skew on 2008-06-26
**Thanks for replying Kevdog.**

> **kevdog said:**
> Few things
Are you looking specifically for a gui?
Do you want to monitor in real time?
Would a command line output similar to top be sufficient?  


I'd prefer an gui and having the data it in real time. Having said that I'm open to all options, so I would use it a command line utility if that is all that's available.


> **kevdog said:**
> 
Basically you are looking for inbound/outbound traffic and rejected packets to be logged by the firewall and this logged and displayed somewhere.  I used to use Guarddog, I don't remember if there is an option to log?  Is this one of the options this program allows.

Yes to the first, I'll check on Guarddogs logging abilities and see if it provides some of what I'm after. 

  Did you check the link i provided in my last post to the **Watchdog** program?  Essentially that is what I'm after, plain and simple. Too bad it's only in Alpha.

*Not many responses to this post. Maybe I would have been better off If I had placed it in the networking section rather then security.*

Thanks again.

---

### Post by kevdog on 2008-06-26
Just off the top of my head, if you could get guarddog to log to a file or even the system log (I know how to do this directly by editing the IPtables by hand, but not through guarddog), you could use the tail -f command, that would continuously follow the log file in the terminal, giving you real time output as the connections through the firewall are logged.  My not be the most elegant solution, but its a real easy solution.

---

### Post by skew on 2008-06-26
> **kevdog said:**
> Just off the top of my head, if you could get guarddog to log to a file or even the system log (I know how to do this directly by editing the IPtables by hand, but not through guarddog), you could use the tail -f command, that would continuously follow the log file in the terminal, giving you real time output as the connections through the firewall are logged.  My not be the most elegant solution, but its a real easy solution.

Okay thanks I'll look into doing this with the guarddog logs. In the mean time ,how would I implement your alternative solution by editing the IPtables directly?

---

