---
title: "Properly terminating program with Upstart or RC.x"
date: 2015-03-26
forum: Ubuntu Application Development
---

### Post by Denis_Chmielewski on 2015-03-26
Hi everybody, 

I have a program running in a virtualized (virtualBox) Ubuntu 14.04. My program manages SIGTERM and SIGINT signals to terminate properly( a few files to move and/or close. 
From VirtualBox manager I can send an ACPI message to the OS in order to perform a gracefull shutdown. It works.
I like to terminate my program properly when VirtualBox sending ACPI shutdown.

I tried 2 ways: 1- old scripting way through rc.0 and rc.6   2- using Upstart, first time for me. 
Each tie I simply add the 2 fillowing in a script (method 1) or a conf file (method 2):
pkill myprogramname
sleep 10

Results are:
Method 1 (old script): the sleep is working but my program does not terminate properly. I guess the system enters runlevel 0 or 6 and my program stops running.
Method 2 (Upstart): my program terminates properly but the sleep does not work. It works but I am afraid if my program takes too much time to terminate in the future, or if it is run in a different environment, it will not work anymore. 

Upstart seems to be the right method  IMHO. But it is quite difficult for me, a lot of documentation to read and understand, not much example on the web...

Please could someone guide me (I prefer learning fishing than you give me a fish) to understand the situation ?
TY for any help.
best regards

---

