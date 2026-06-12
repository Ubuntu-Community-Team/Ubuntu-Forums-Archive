---
title: "New WildDog Desktop locking up"
date: 2015-05-04
forum: System76 Support
---

### Post by eightbits2010 on 2015-05-04
Sytem76 WildDog Desktop   (Purchased < 3 months)
 OS: Ubuntu 14.10  64-bit
 
 
 Mother Board: Asus H97-PLUS
 Memory 7.7 GiB
 Processor Intel Core i5-4460CPU @ 3.20 GHZ x 4
 Graphics Intel Haswell Desktop
 
 
 Crucial_CT120M500SSD4 (MU05)  SSD 120 GB   Disk 113.8 GB
 SMART Data & Self-Tests indicate no failures.
 
 
 I am getting intermittent system 'lock ups' about every two weeks or less.  
 When the system locks up only the cursor moves on the screen, but nothing else works.
 The keyboard is dead also. The only way to return the PC back to operation is to force
 a shutdown using the power key.
 
 
 I have an open service ticket with System76 but so far have not received any solution.
 I have sent a system log(s) but got a somewhat vague response which I am not connecting
 any dots that makes sense.
   
 At a loss and I am hoping someone can offer so suggestions.

---

### Post by tgalati4 on 2015-05-05
These are the worst problems to troubleshoot.  New hardware that was working and now not working.  Could be infant mortality--some component has failed after being stressed.

Check the power supply voltages in BIOS or with a voltmeter.  Anything 10% below nominal values may be an issue.

Pull out everything from the machine except a minimal condition, no hard disk, 2 GB of RAM, on-board video, etc and boot with a USB stick.  Run a Live Ubuntu session for several days.  You want to determine if the motherboard, CPU, and power supply are OK and stable at their current settings.  If you get a lockup, then try declocking--lowering CPU and RAM timings and boot again.  If it runs at slower speeds, then it could be a motherboard/CPU issue.

Sometimes a motherboard firmware issue will fix these issues--unfortunately, new hardware needs to be put back into the oven to be "fully baked."

I would expect an RMA on such a machine, however how do you know the replacement machine won't have similar issues? . . .

---

### Post by eightbits2010 on 2015-05-05
Thanks for the input tgalati4. I have thought of running on a live disk for a while. I actually need the PC on a daily basis. I did supply System76 with their request for the
system logs. I did get a response back but doesn't offer any approach to isolate the problem. As you mentioned, any part of the PC could be the problem: RAM, HD, Power Supply, Mother Board, cables .........
Below is the response from System76. Any ideas from this response ?
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------
This is logged right before you reboot

May  4 12:17:01 jlo-Wild-Dog-Performance CRON[4187]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  4 13:17:01 jlo-Wild-Dog-Performance CRON[4768]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

Not  sure what it's doing, or if it was configured from something else.   Nonetheless, it's pretty apparent that it's doing something.  

The log is littered with a number of entries like this also  

May   4 11:29:44 jlo-Wild-Dog-Performance kernel: [ 2282.440245]  systemd-hostnamed[3803]: Warning: nss-myhostname is not installed.  Changing the local hostname might make it unresolveable. Please install  nss-myhostname!

The entry is innocuous, but indicating something odd or not behaving.  Maybe a web service of some type configured?  

One  of the other events at the end also seems to be pertaining to the  printer.  I might suggest unplugging that and seeing that happens again.
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
BTW, what is nss-myhostname ?
Thanks for your reply.

---

### Post by jweber53 on 2015-05-06
Hi,

I agree with tgalati4 that it seems to be a hardware problem. The only thing I might add is that it might be a video driver problem. Sometimes I've seen an apparent system lockup, but one can still ssh into the machine from another. In this case the display manager can usually be restarted and system fixed without a hard reboot. Did you try ctrl-alt-F1 to see if you can get a terminal? Even if the keyboard seems unresponsive, this sometimes works. In either the ssh case or getting a terminal, it can be informative in tracking down the problem.

The log messages you posted are normal.
  
```
[COLOR=#000000]May 4 12:17:01 jlo-Wild-Dog-Performance CRON[4187]: (root) CMD ( cd / && run-parts --report /etc/cron.hourly)

[/COLOR]
```[COLOR=#000000]messages are part of normal system operation. The

[/COLOR]```
[COLOR=#000000]Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!

[/COLOR]
```[COLOR=#000000]Is a known bug and it's recommended to ignore it rather than install any packages in an attempt to fix it.

[/COLOR]https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1277608[COLOR=#000000]





[/COLOR]

---

