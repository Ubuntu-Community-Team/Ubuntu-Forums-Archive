---
title: "Ubuntu Server 7.10 Complete Crash"
date: 2008-01-09
forum: Server Platforms
---

### Post by sss-server on 2008-01-09
I have made as much research as I could, but with no luck on finding a reason or a solution to the problem.

I hope you can help me, since this is my last attempt before go ahead and reinstall everything on the server.

This a server we have here at the office to run some apps like OpenFire, Apache, the company's web site, among others. Ubuntu Server 7.10 was installed on a Virtual Machine on a Dell Blade Server.

The server was working fine until we came to the office and the Spark client could not connect to the server at the beginning of the day, I think this happened on a Monday.

The images attached are the messages I got when booting up, the segmentation fault error appears in almost all the lines of the start up scripts. Also, there is no way to log in since for whatever user is entered no password request is done by the system.

If you need further info, just let me know. Thanks in advance.

---

### Post by k_grdn on 2008-01-09
Hi,

Have you tried reseating the RAM?

Also try memcheck from the grub prompt (takes a while).

Regards,

k_grdn

---

### Post by MJN on 2008-01-09
It looks to me like disk/partition problems given the mount failures and read-only filesystem state (this usually happens as a result of fs failure if configured to do so in fstab).

Boot with a LiveCD, or similar, and run fsck on all partitions.

Mathew

Edit: Oops - just realised this is a virtual machine in which case ignore everything I've said - will keep the post here for future reference though!

---

### Post by sss-server on 2008-01-09
I am doing the memtest with the option available in the grub menu, as soon as I have the results I will post again.

Regarding the RAM resetting, besides shutting down the virtual machine, I have not done anything else. The VMWare server has other vm's running so make a server shutdown will not be possible very soon. 

Is there any other way to reset the RAM? Do I need to reset the vm RAM or the whole server? Thanks.

---

### Post by k_grdn on 2008-01-09
Missed the bit VM too!

Have you got adequate swap space?

Also check how much memory there is allocated to the VM, try increasing allocation.  

Tmpfs a virtual memory based filesystem looks like this is where your problems stem from.

Regards,

k_grdn

---

### Post by k_grdn on 2008-01-09
Sorry I meant reseat as in reseat the DIMMS.

How many VM's are you running and how are they allocated memory, Is it possible a VM is hogging the RAM, have you got enough RAM installed to cover the overall allocated memory to all the running VM's.

Try running top or free on the system the VM's are running on, then monitor the memory usage.

k_grdn

---

### Post by k_grdn on 2008-01-09
Also try vmstat on the host system. Use vmstat -s to review the system memory usage.

k_grdn

---

### Post by sss-server on 2008-01-10
OK. I run the memtest from GRUB and I didn't get any errors.

I am attaching the result of the fsck, just in case, and to my understanding it doesn't show any problem.

I have 411 MB of swap space and the RAM is 512 MB (there is image attached with the partition structure). The VM has 512 MB for RAM and 8 GB of HD, I tried to increase the RAM to 1024 and it doesn't help.

There are 5 in total VMs running on this server: 3 has 1024MB of RAM (WinServer 2003 SE), 1 has 1536MB of RAM (ubuntu server 7.10) and the one crash which has 512MB of RAM. The server total RAM is 3.86GB.

This might be a problem, I haven't notice this before, even though the Webmin for the server does not show much usage on the RAM (580MB with all the VM running).

The vmstat -s command on the host system result is:

~$ vmstat -s
      4048868  total memory
      4002508  used memory
      3035452  active memory
       459352  inactive memory
        46360  free memory
         5804  buffer memory
      3416172  swap cache
      5831552  total swap
       139564  used swap
      5691988  free swap
     10906270 non-nice user cpu ticks
        15005 nice user cpu ticks
    199024539 system cpu ticks
   2630693382 idle cpu ticks
     69459172 IO-wait cpu ticks
       297738 IRQ cpu ticks
       730581 softirq cpu ticks
            0 stolen cpu ticks
    145607603 pages paged in
   1766654328 pages paged out
        74407 pages swapped in
        73942 pages swapped out
   2654454557 interrupts
   3686101849 CPU context switches
   1192727141 boot time
        45541 forks

---

### Post by MJN on 2008-01-10
My fsck suggestion was an error as I didn't spot you were using a virtual machine.

However, it's worth pointing out that you really ought to heed the warning about running fsck on a mounted filesystem - don't do it!!

Mathew

---

### Post by sss-server on 2008-01-18
Thanks for the advice MJN. I guess my excuse is that since the system is almost dead, I did not care about the fsck message, but anyway the lesson is learned to be more careful in the future.

If you have any other advice for this case, please let me know. The systems is still down and I don't have a clue how to fix it. 

Some more info about the VMs. Most of them were shutdown since we don't need them anymore, so there are only 2 left: the one with the problem and another one for testing. So in this moment I can do anything on the server in order to try to find the issue.

---

### Post by MJN on 2008-01-19
I'm afraid I don't have any experiences of VM's hence cannot be of much use...

Mathew

---

