---
title: "howto troubleshoot cups segmentation faults?"
date: 2011-04-05
forum: Server Platforms
---

### Post by jringoot on 2011-04-05
Hi all,


I've set up a new virtual server (ubuntu 10.04 LTS on RHEVM, "uname -a
Linux print-me 2.6.32-31-server #60-Ubuntu SMP Thu Mar 17 23:33:39 UTC 2011 x86_64 GNU/Linux")
 2 weeks ago just for cups and samba printing (no other filesharing). Ran tests and it looked fine, then last friday I have added 10 Ricoh printers and 3 hp printers. Looked fine, apart from an issue with one  "HP Color Laserjet 2600n", but resolved this with the help of the driver found here: [http://foo2hp.rkkda.com/](http://foo2hp.rkkda.com/) (recommended by [http://www.openprinting.org/printer/HP/HP-Color_LaserJet_2600n](http://www.openprinting.org/printer/HP/HP-Color_LaserJet_2600n)) 

Since saturday, cups crashes daily in the morning with a segmentation fault (segfault:, eg:

/var/log/kern.log:Apr  3 06:40:39 print-me kernel: [154716.314945] cupsd[20713]: segfault at 7f097c8cd5d0 ip 00007f0ab0f0fb0f sp 00007fff5282dc10 error 4 in libcups.so.2[7f0ab0efb000+47000]

I wanted to trace what happens just before this by changing the LogLevel
( see here: [http://www.cups.org/documentation.php/doc-1.4/ref-cupsd-conf.html](http://www.cups.org/documentation.php/doc-1.4/ref-cupsd-conf.html)) but setting it to anything higher than notice makes cups segfault again, with additional message on CLI: 

 service cups restart
 * Restarting Common Unix Printing System: cupsd                                                                                              cupsd: Child exited on signal 11!
                                                                                                                                       [fail]

So far for trying to debug....

Any suggestions are welcome.
Thanks

(BTW, print-me is short for "printserver for  MEteorological institute")

---

### Post by jringoot on 2011-04-11
To automagically restart cups when it fails, i added a crontab entry:

```
root@print-me:/var/log# crontab -l
# m h  dom mon dow   command
*/3 * * * * /root/scripts/checkcups >> /var/log/checkcups 2>&1
root@print-me:/var/log# cat /root/scripts/checkcups
#!/bin/bash
ps -ef | grep -i cupsd | grep -i conf > /dev/null
if [ $? == 1 ]; then
	date
	echo "cupsd is down, lets try to start it."
	/etc/init.d/cups restart
else
        exit
fi
root@print-me:/var/log# cat /var/log/checkcups
-bash: /root/scripts/checkcups: No such file or directory
/bin/sh: /root/scripts/checkcups: not found
Wed Apr  6 16:27:22 CEST 2011
cupsd is down, lets try to start it.
 * Restarting Common Unix Printing System: cupsd
   ...done.
Fri Apr  8 06:36:01 CEST 2011
cupsd is down, lets try to start it.
 * Restarting Common Unix Printing System: cupsd
   ...done.
Sat Apr  9 06:54:01 CEST 2011
cupsd is down, lets try to start it.
 * Restarting Common Unix Printing System: cupsd
   ...done.
root@print-me:/var/log# 

```
I modified it to get the segfaults in the new log:
```
root@print-me:/var/log# cat /root/scripts/checkcups
#!/bin/bash
ps -ef | grep -i cupsd | grep -i conf > /dev/null
if [ $? == 1 ]; then
        date
        echo "message scrap"
        echo "====================================================================================="
        grep cupsd -A 4 -B 4 cupsd /var/log/messages | tail -n 9
        echo "kern.log scrap"
        echo "====================================================================================="
        grep cupsd -A 4 -B 4 cupsd /var/log/kern.log | tail -n 9
        echo "cups error_log scrap"
        echo "====================================================================================="
        tail /var/log/cups/error_log-print-me
        echo "cupsd is down, lets try to start it."
        /etc/init.d/cups restart
else
        exit
fi


```

I noticed there was an update for cups in the respository, loglevel debug1 works now without segfault, debug2 still generates segfaults.

---

