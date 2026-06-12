---
title: "modify eucalyptus.local.conf"
date: 2011-01-03
forum: Ubuntu Cloud and Juju
---

### Post by oldhoot on 2011-01-03
How do you modify eucalyptus.local.conf to change things like the VNET_SUBNET?

---

### Post by raymdt on 2011-01-04
You should never edit eucalyptus.local.conf directly.
you can use euca_conf or override eucalyptus.local.conf settings in eucalyptus.conf.
Also remove the '#' Character bevor  VNET_SUBNET in eucalyptus.conf, put the new value and make a clean restart.

---

### Post by oldhoot on 2011-01-04
I understand from reading the file that eucalyptus.local.conf should never be edited directly.  However, it's not clear from the help file how to use euca_conf to modify VNET_SUBNET settings.  Can you explain?  Also, I have tried modifying eucalyptus.conf and doing a restart (and also a reboot) but changes are not getting reflected in eucalyptus.local.conf.  Are you telling me that changes in eucalyptus.conf supercede settings in eucalyptus.local.conf (so changes in .conf are not directly made to .local.conf)?

---

### Post by raymdt on 2011-01-04
The eucalyptus.local.conf  is an UEC specific file ( There is none on eucalyptus  :mad:).
Changes in eucalyptus.conf are not direct  reflected in local.conf. do your Instances work now?
 What about the files, i asked you to post.

---

### Post by raymdt on 2011-01-04
Sorry i didn't see your last Post :confused:

---

### Post by oldhoot on 2011-01-04
Here's what I'm talking about in terms of the IPs being the same....

[email]hoot@cloud-master:~/.euca[/email]$ euca-describe-instances
RESERVATION	r-53540945	admin	default
INSTANCE	i-4E500911	emi-DF13106C	172.19.1.2	172.19.1.2	running	tues010410	0		c1.medium	2011-01-04T20:11:18.413Z	crux	eki-F56110EC	eri-09E6115D

---

### Post by viswacse02 on 2011-04-27
> **oldhoot said:**
> Here's what I'm talking about in terms of the IPs being the same....

[EMAIL="hoot@cloud-master:%7E/.euca"]hoot@cloud-master:~/.euca[/EMAIL]$ euca-describe-instances
RESERVATION    r-53540945    admin    default
INSTANCE    i-4E500911    emi-DF13106C    172.19.1.2    172.19.1.2    running    tues010410    0        c1.medium    2011-01-04T20:11:18.413Z    crux    eki-F56110EC    eri-09E6115D
Hi, infact myself have to get the same ip address like what you have got. 

RESERVATION    r-53540945    admin    default
INSTANCE    i-4E500911    emi-DF13106C    **172.19.1.2    172.19.1.2**    running     tues010410    0        c1.medium    2011-01-04T20:11:18.413Z    crux    eki-F56110EC     eri-09E6115D

 I have to know how you got the same ip address?

How to change it manually because the dhcp autommatically assigns the ip 

[EMAIL="hoot@cloud-master:%7E/.euca"]~/.euca[/EMAIL]$ euca-describe-instances

RESERVATION    r-42470853    admin    default
INSTANCE    i-417607C6    emi-210F15BA    **10.1.1.106    172.19.1.2**    running    mykey    0        m1.large    2011-04-26T11:42:18.567Z    cluster1eki-6E341ABC

I know the ip address 10.1.1.106 is the vm instance ip which i have given during clc installation. Why it automatically assigns another ip 172.19.1.2? Is it possible to change to 10.1.1.106 because i couldn't ping internet with this ip.

I need to know how to change the ip address 172.19.1.2 to 10.1.1.106 like yours. The ip address 172.19.1.2 is assigned automatically by the dhcp server and indeed i have changed manually the ip address in clc ( var/run/eucalyptus/net/euca-dhcp.conf) but still i could resolve the problem.

---

