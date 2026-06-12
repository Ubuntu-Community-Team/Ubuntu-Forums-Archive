---
title: "The BIOS has corrupted hw-PMU resources"
date: 2015-06-01
forum: Server Platforms
---

### Post by lawdt on 2015-06-01
Hi all, there is a problem to boot ubuntu server 14.10 at Hp Microserver gen8.
the message is:

[firmware bug] The BIOS has corrupted hw-PMU resources (MSR 38d is 330).
power meter ACPI000D:00: Ignoring unsafe software power cap

and ubuntu is hanging, rotating , and nothing.

can anyone help please?

---

### Post by coffeecat on 2015-06-01
Welcome to the forum.

You posted in the [Resolution Centre]("http://ubuntuforums.org/forumdisplay.php?f=123"), which is not for technical questions.

*Thread moved to **Server Platforms**.*

---

### Post by houstonbofh on 2015-06-04
Have you updated the server to the latest BIOS release?

---

### Post by matt_symes on 2015-06-05
Hi

> **lawdt said:**
> Hi all, there is a problem to boot ubuntu server 14.10 at Hp Microserver gen8.
the message is:

[firmware bug] The BIOS has corrupted hw-PMU resources (MSR 38d is 330).
power meter ACPI000D:00: Ignoring unsafe software power cap

and ubuntu is hanging, rotating , and nothing.

can anyone help please?

From this HP advisory...

[http://h20565.www2.hp.com/hpsc/doc/public/display?sp4ts.oid=4268690&docId=emr_na-c03265132&lang=en&cc=us](http://h20565.www2.hp.com/hpsc/doc/public/display?sp4ts.oid=4268690&docId=emr_na-c03265132&lang=en&cc=us)

> 
<snip>

On an HP ProLiant server  running Red Hat Enterprise Linux 6, the following message is displayed  during the initial startup screen of Red Hat Linux: 
      *[Firmware Bug]: the BIOS has corrupted hw-PMU resources*  
  
<snip>

For the following ProLiant servers, the error message can be avoided by performing the steps detailed below: 
 
    
[LIST]
[*]All ProLiant Gen8 Servers
[*]ProLiant DL580 G7
[*]ProLiant BL620 G7
[*]ProLiant BL680 G7
[/LIST]
  
    **Note:**  For the servers listed above, perform the following to avoid the above message from being displayed:   
 
    **IMPORTANT:**  Disabling "Processor Power and Utilization Monitoring" limits the HP ProLiant server capabilities. 
    
[LIST=1]
[*]Boot machine to RBSU (F9).
[*]Press CTRL+A.
[*]Select "Service Options."
[*]Select "Processor Power and Utilization Monitoring."
[*]Select "Disable."
[*]Press F10 to save and exit.
[*]Reboot.
[/LIST]
  


Hopefully that will fix your problem although the advisory suggests...

> Advisory: (Revision) Red Hat Enterprise Linux 6 - "[Firmware Bug]: The  BIOS Has Corrupted Hw-PMU Resources" **Message Can Be Safely Ignored**

Kind regards

---

