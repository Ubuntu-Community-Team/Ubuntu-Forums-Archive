---
title: "qla-tools on 14.04, how to make them work?"
date: 2014-11-12
forum: Server Platforms
---

### Post by curmudge1 on 2014-11-12
I have a new server install, Ubuntu 14.04, with Qlogic 2560 HBAs.   So, I'm trying to use the Qlogic HBA tools, package, qla-tools.

I installed the qla tools, but when I try the qla-snapshot I get this: 

$ sudo  ql-hba-snapshot 

Only Kernel version 2.6 and above are supported 


Got any quick suggestions or fixes?

Of course, Qlogic does not seem to support Ubuntu/Debian.  

--
Dave

---

### Post by tgalati4 on 2014-11-13
Perhaps it is a 32-bit versus 64-bit issue?  Have you tried to open the code in *gedit* and see if it is a script?  There is probably a kernel version check that is failing that could be fooled by setting an environment variable to a helpful value.

---

### Post by gompa2 on 2014-11-14
what are you trying to do ? there are integrated qla drivers in the kernel now
the module is called qla2xxx 
you can use them with lio and for target mode use targetcli : [http://www.linux-iscsi.org/wiki/Fibre_Channel](http://www.linux-iscsi.org/wiki/Fibre_Channel)
you can put the card in target mode by adding a file : /etc/modprobe.d
and adding:  options qla2xxx qlini_mode="disabled"

---

### Post by curmudge1 on 2014-11-17
> **gompa2 said:**
> what are you trying to do ? there are integrated qla drivers in the kernel now
the module is called qla2xxx 
you can use them with lio and for target mode use targetcli : [http://www.linux-iscsi.org/wiki/Fibre_Channel](http://www.linux-iscsi.org/wiki/Fibre_Channel)
you can put the card in target mode by adding a file : /etc/modprobe.d
and adding:  options qla2xxx qlini_mode="disabled"

It's not about the drivers, which seem to be OK, rather the Qlogic tools:

 	 	[h=2]QLogic Linux tools for work with QLogic HBAs[/h] 	 QLogic provides some tools that makes LUN handling (add / remove) and adminstration of QLogic HBAs much easier.  You can scan for newly added LUNs, display details about the QLogic HBA attached to the system, change the state of LUNs from offline to online/running and set the timeout on the devices connected to the QLogic FC HBA. 	  

For examble, ql-hba-snapshot:


**ql-hba-snapshot** <Host number> [*OPTIONS*]
 [h=2]Description[/h] FC HBA Snapshot Utility
 This utility displays the details of the QLogic HBA attached to the system.

---

### Post by gompa2 on 2014-11-18
is that for the target or the initiator ? if its the target you can use targetcli to set up the luns.
if its on the initiator i have no idea to be honest ( my luns where detected when i configured them on the target and rebooted the initiator)

ps. i think the qlogic hba tools are for the propatary drivers ? and i think you have to rebuild the kernel to use them ( correct me if iam wrong)

---

### Post by curmudge1 on 2014-11-18
I have no  whether the kernel needs to be rebuilt... I just tried  apt-get install qla-tools & they installed from the standard Ubuntu  repository.    Then, I tried one of the commands as a test & it won't run.

I thought that meant that the programs should work/ run.   The error  message in my original post suggests that they probably do need to be  rebuilt for this version (14.04). 

Maybe I should try a bug report?

---

