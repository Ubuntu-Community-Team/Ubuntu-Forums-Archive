---
title: "WinXp in Virtualbox -&gt; Segmentation Fault"
date: 2010-07-31
forum: Virtualisation
---

### Post by Necrophobic on 2010-07-31
Hi Ubuntu Forums! First post here, lol))
So, here's my situation:
host: 10.04 x86
VM: WindowsXP SP3
VirtualBox v3.1.6

When I try to launch this VM, a form with a black screen opens up normally, then all of a sudden closes! Terminal told me that it's a segmentation fault, not good:(. Other VMs work perfectly, and of course this one also worked previously. Any ideas?

---

### Post by greg_ory on 2010-07-31
Try the following(command-line):

VBoxSDL -vm [NAME]

Where 'NAME' is the name of your virtual machine.

Some more information about the error you are getting would be helpful

Cheers

Greg

---

### Post by Necrophobic on 2010-07-31
well, I have already told the output was the following:

> user@laptop:~$ virtualbox --startvm DevCenter2
&#1054;&#1096;&#1080;&#1073;&#1082;&#1072; &#1089;&#1077;&#1075;&#1084;&#1077;&#1085;&#1090;&#1080;&#1088;&#1086;&#1074;&#1072;&#1085;&#1080;&#1103;(segmentation fault)

---

### Post by greg_ory on 2010-07-31
What is when you try to open the virtual machine via command line with the instruction provided?

---

### Post by Necrophobic on 2010-08-01
```
user@laptop:~$ vboxsdl -vm DevCenter2
Sun VirtualBox SDL GUI version 3.1.6_OSE
(C) 2005-2010 Sun Microsystems, Inc.
All rights reserved.

&#1054;&#1096;&#1080;&#1073;&#1082;&#1072; &#1089;&#1077;&#1075;&#1084;&#1077;&#1085;&#1090;&#1080;&#1088;&#1086;&#1074;&#1072;&#1085;&#1080;&#1103;
user@laptop:~$ 


```

---

