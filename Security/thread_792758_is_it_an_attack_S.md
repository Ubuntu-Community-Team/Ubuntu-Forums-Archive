---
title: "is it an attack? :S"
date: 2008-05-13
forum: Security
---

### Post by scoobymad555 on 2008-05-13
ok so .... box installed with fiesty (what we had on cd at the time) purely to run a large screen on an intranet style page as a live noticeboard.

system was stable and happy when we left at 5 but was down when we turned up this morning. Looked through the logs for anything obvious (and checked power saving was disabled) but couldn't see anything major until i came accross ....

an entry saying a connection was made on port 2208 at just after 6 and then further on a disk failure .....

google turns up a service called hpiod but also a trojan called rux.psw that operate on that port. This appears to be the first time anything like this has happened but then, the rest of the system is m/s and the logs there don't seem to show anything at all.

Frustration is the router is owned and supported by isp (educational site) and as such i can't access that to look at any logs etc.

peeps opinions? - are we worrying about nothing or are we looking at a potential attack using rux.psw?

cheers :)> 

---

### Post by mattress on 2008-05-13
It could possibly be a false positive, but all the same I'd install  chkrootkit or rkhunter and run their scans to see if anything
on your system is amiss. 

You did mention something about hardware / disk failure, could that not be the main source of the problem ? Have you run smartctl checks on the drive ?

HTH

-m

---

### Post by Chayak on 2008-05-13
There are some legitimate services that can run on the port hplip for one.  I really doubt it's rux.psw as it's a windows trojan circa 2002.

Can you post the log entries where that port shows up?  What kind of security is set up on the box?

---

