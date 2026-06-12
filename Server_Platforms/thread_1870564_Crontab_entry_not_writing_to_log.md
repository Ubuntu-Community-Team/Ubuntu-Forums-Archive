---
title: "Crontab entry not writing to log"
date: 2011-10-27
forum: Server Platforms
---

### Post by mcquaim on 2011-10-27
Hi folks,
 
I am new to ubuntu and crontab so I'm probably doing something stupid..
 
I have the following crontab entry that I'd like to run every so often, currently trying every 5 minutes:
 
*/5 * * * * ifconfig eth0|grep "RX bytes" >>/var/oscamlog/ServerData.txt
 
I want to check data sent/received in a time period. The problem is that the command does not pipe out to my log file when executed via crontab but if I run this maually on the command line then it will work fine.
 
Any ideas where I'm going wrong?
 
Thanks,
mcquaim

---

### Post by collisionystm on 2011-10-27
> **mcquaim said:**
> Hi folks,
 
I am new to ubuntu and crontab so I'm probably doing something stupid..
 
I have the following crontab entry that I'd like to run every so often, currently trying every 5 minutes:
 
*/5 * * * * ifconfig eth0|grep "RX bytes" >>/var/oscamlog/ServerData.txt
 
I want to check data sent/received in a time period. The problem is that the command does not pipe out to my log file when executed via crontab but if I run this maually on the command line then it will work fine.
 
Any ideas where I'm going wrong?
 
Thanks,
mcquaim


I think it needs to be made into a script and then edit crontab to run the script instead

---

### Post by collisionystm on 2011-10-27
one other question... 

when you run **crontab -e** are you running it as sudo?

if not, does your user account have read/write privledges to this file? /var/oscamlog/ServerData.txt

---

### Post by matt_symes on 2011-10-27
Hi

> */5 * * * * ifconfig eth0|grep "RX bytes" >>/var/oscamlog/ServerData.txt

Use the full path for ifconfig and grep.

to find that 

```
which ifconfig
```

same for grep.

On my current install it's **/sbin/i**fconfig for ifconfig. However, i am not currently using what you are so double check.

*/5 * * * * **/sbin/**ifconfig eth0| **/bin/**grep "RX bytes" >>/var/oscamlog/ServerData.txt

Kind regards

---

### Post by mcquaim on 2011-10-27
Hi lads,
 
Thanks for the quick replies. Yeah, I am using sudo when I am running crontab -e.
 
I will check the location of ifconfig and try the full path and report back. 
 
Thanks again,
mcquaim

---

### Post by mcquaim on 2011-10-27
That was the problem exactly matt_symes, working a treat now thanks.
 
One more thing, how would a append the time to the start or end of the RX bytes text?
 
Cheers,
Mac

---

### Post by matt_symes on 2011-10-27
Hi

You could do something simple like.


```
*/5 * * * * /bin/date >> /var/oscamlog/ServerData.txt; /sbin/ifconfig eth0| /bin/grep "RX bytes" >>/var/oscamlog/ServerData.txt
```

Kind regards

---

### Post by mcquaim on 2011-10-27
Thanks Matt_symes,

That works great! Thanks for all the help

Cheers,
mcquaim

---

