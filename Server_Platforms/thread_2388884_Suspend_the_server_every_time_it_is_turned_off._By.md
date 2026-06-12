---
title: "Suspend the server every time it is turned off. By the button, or any other command."
date: 2018-04-08
forum: Server Platforms
---

### Post by marcio.prado on 2018-04-08
How do I program Ubuntu Server 16.04 to suspend every time I shut down?


Regardless of whether it is for the on / off button or another command?


I set pm-suspend to no avail.

[COLOR=#000000]1. Install acpid, pm-suspend[/COLOR]
[COLOR=#000000]2. edit "/etc/acpi/events/powerbtn" to say;

[/COLOR]event=button[ /]power
#action=/etc/acpi/powerbtn.sh 
**action=/usr/sbin/pm-suspend**

---

### Post by wildmanne39 on 2018-04-08
*Thread moved to **Server Platforms, a more appropriate forum**.*

---

### Post by TheFu on 2018-04-09
Perhaps /etc/systemd/logind.conf can help?
There are also some BIOS settings which might need to be modified.  "Server" hardware can be different.

---

### Post by marcio.prado on 2018-04-10
Hello TheFu.


Thanks a lot for the help.


I was suspicious of the same BIOS...


The server is a Dell R620 and has the following options in the power management issue:

Performance Per Watt (DAPC-System) - System DBPM (DAPC -Dell Active Power Control) has the decision control according to the load running on the server.
**Performance Per Watt (OS)** - Operating System decides to handle the power management.
**Performance** - Maximum system utilization can be obtained using this option.
Dense Configuration (DAPC-System) - Here the decision is controlled by System DBPM with a disabled &#8220;Turbo Boost&#8221; function.
Custom - Customization can be obtained here by setting various subsystem levels (CPU, memory and fan).
[IMG]http://en.community.dell.com/resized-image.ashx/__size/1024x0/__key/communityserver-blogs-components-weblogfiles/00-00-00-37-45/1016.12g.jpg[/IMG]



Currently the option is enabled: Performance


I think I'm going to have to move to: Performance Per Watt (OS)


When you do, notice it here.


If anyone has any more ideas, please help me.

---

### Post by TheFu on 2018-04-10
[https://askubuntu.com/questions/771653/suspend-does-not-work-on-dell-t20-with-16-04](https://askubuntu.com/questions/771653/suspend-does-not-work-on-dell-t20-with-16-04) - bios support might be an issue, as you mentioned.  I didn't find anything for the specific dell model you have.

---

### Post by marcio.prado on 2018-04-11
Thank you again. It helped a lot.


When I make the modifications notice what happened ...


See you.

---

