---
title: "Software Clock Loops Every Few Seconds"
date: 2008-07-24
forum: Server Platforms
---

### Post by jbulcher on 2008-07-24
One of our newer servers running "Ubuntu 7.10 i686 kernel 2.6.22-14-server" (as a VMWareguest OS) and MySQL Ver 14.12 Distrib 5.0.45 on VMWare Server 1.04 build-56528 exhibited some very strange symptoms.

MySQL queries were not completing, and MySQL was acting unresponsive to new requests. The weblogs from another server showed that a few SELECT queries had been able to complete, but during troubleshooting MySQL would not even connect to any of the databases. There was also a long list of queued process, most of which were write operations, but there were a few read operations as well. SHOW PROCESSLIST also displayed strange results in the 'Time' column, including 4294967295, 4294967294, 0, 1, and 2 seconds. The larger numbers make sense if MySQL mis-interpreted -2 and -1 respectively as a positive 32 bit number.

The software clock was stuck in a 5 second loop from late the previous night, which started during a bzip operation that apparently succeeded, although the success of the operation was not logged. The command 'hwclock', however, did display the correct time.

Both messages and syslog do not contain any logs from after the time loop began.

We have searched the web, and discovered a few possible causes, such as APIC or possibly even VMWare, but the results are meager and we haven't been able to find enough information to follow up with. The only way we have managed to get MySQL going again is to reboot the system, which has obvious implications. We need to find out what exactly is causing this problem so that we can fix it. Can someone help us troubleshoot / point us in the proper direction?

---

### Post by windependence on 2008-07-24
Have you tried setting up ntp?

-Tim

---

### Post by jbulcher on 2008-07-25
Yes, we are using ntp. Specifically, we are using openntp implementation of ntp.

I forgot to mention earlier that the host system for VMWare is running on software raid 1.

---

### Post by pmarty on 2008-07-30
Hi there!

Did you find the answer to your problem?

I had the same strange behavior on a mandriva 2008.0 box (installed a few weeks ago, everything went well until Fri 18 July 18:11:05 when it looped back to 18:11:01 and then again every 5 seconds...).

Syslog was still logging, but with broken time.

Consequences were some processes were hanging indefinitely and not completing (e.g. console login, "top", halt/reboot/shutdown... a vi session and a grep -ir commands also blocked after about 5 seconds and never recovered...).

Network activity was not affected. NTPDATE adjustment worked but clock still looped every 5 seconds (hence preventing any other cronned adjustement... and we don't like ntpd!).

I had to power off in a hard way (power cord!) and after reboot it seemed to run again correctly.

However I've seen on google 2 other threads (and only 2 other):
* one back from Jul 2005, on a debian sarge box, with exactly the same behavior; but the clock loop was occuring again after about one hour after reboot... some people were thinking about a hw clock problem (arguments were given to exclude glibc bugs) but it seemed to be solved by installing another kernel...

* one back from Feb 2005, on a windows laptop, with slightly different symptoms (different loop duration and some jumps in the future occuring more or less at random but with the same slew each time); again people were thinking about a hw clock problem and it was solved by the vendor hotline (HP) requesting a BIOS upgrade...

Any idea or evolution of your situation?

Thanks,

---

### Post by Dianoga on 2008-08-11
Any news on this? I don't know if we are having the exact same problem, but ours appears similar. Everything will run fine for a while and then I end up with different reported dates in different places. For example: the command "watch date" gives one date that does not change in the top right and the expected output of date underneath. The top right date does not change on exiting and restarting the watch command. Top, htop, aptitude all behave incorrectly.

---

### Post by windependence on 2008-08-11
There can be an issue with the default time tick in most Linux kernels. It is usually set for 1000 which is way too fast. In Ubuntu server 8.04, the kernel is optimised for VMs and the default tick is 100. 

If you do a google search on "Timekeeping in VMWare Virtual Machines" you will find tons of answers on this. Below is a link to an official VMware PDF on the issue:

[http://www.vmware.com/vmtn/resources/238](http://www.vmware.com/vmtn/resources/238)

-Tim

---

### Post by pmarty on 2008-08-14
I do precise that in my case I do not run VM, just a native Mandriva 2008.0 on a physical dual x86_64 box.

The only news I have:
* in my case, it occured twice, and in both cases just after a ntpdate cron run (please, don't ask why I use cronned ntpdate instead of ntpd... ;) )

* I did not find (google) more than 2 other reports (on physical linux boxes), and both are 1 to 3 years old (in one case, they suspected the motherboard / bios / battery on a µ$ Windown laptop ; the other one seemed also related to ntpdate / ntpd problems ...)

I'll try to upgrade the kernel.

---

### Post by windependence on 2008-08-14
> **pmarty said:**
> I do precise that in my case I do not run VM, just a native Mandriva 2008.0 on a physical dual x86_64 box.

The only news I have:
* in my case, it occured twice, and in both cases just after a ntpdate cron run (please, don't ask why I use cronned ntpdate instead of ntpd... ;) )

* I did not find (google) more than 2 other reports (on physical linux boxes), and both are 1 to 3 years old (in one case, they suspected the motherboard / bios / battery on a µ$ Windown laptop ; the other one seemed also related to ntpdate / ntpd problems ...)

I'll try to upgrade the kernel.

Well this issue is an entirely different issue for you since you are not running VMs. Timekeeping is an issue on Virtual servers. You may wish to start a new thread on this since it really isn't the same as the OP's problem.

-Tim

---

