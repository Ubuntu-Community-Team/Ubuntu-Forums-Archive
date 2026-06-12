---
title: "Installing VMware"
date: 2007-10-26
forum: Virtualisation
---

### Post by CWBillow on 2007-10-26
Vmware player comes as an RPM, and I can't get it to install.
 
I am entirely unclear as to whether I need something I haven't got yet, or whether it's a command string I don't know.
 
How can I install this?
 
Regards,
Chuck Billow

---

### Post by bodhi.zazen on 2007-10-26
I advise you install VM Server :

[https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)

---

### Post by CWBillow on 2007-10-26
> **bodhi.zazen said:**
> I advise you install VM Server :
 
[https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)
 
Why server instead of Player?  Are both free?  Major differences?
 
Regards,
Chuck Billow

---

### Post by jespdj on 2007-10-26
> **CWBillow said:**
> Why server instead of Player?  Are both free?  Major differences?
Because with Player you cannot create your own virtual machines; it can only run existing virtual machines.
Not Workstation because it costs money.
Server does not cost money and does allow you to create your own VMs.

See [https://help.ubuntu.com/community/VMware](https://help.ubuntu.com/community/VMware) and [http://www.vmware.com](http://www.vmware.com)

---

### Post by CWBillow on 2007-10-26
> **jespdj said:**
> Because with Player you cannot create your own virtual machines; it can only run existing virtual machines.
Not Workstation because it costs money.
Server does not cost money and does allow you to create your own VMs.
 
See [https://help.ubuntu.com/community/VMware](https://help.ubuntu.com/community/VMware) and [http://www.vmware.com](http://www.vmware.com)
''Gotcha. 
 
Thanks,
Chuck Billow

---

### Post by CWBillow on 2007-10-26
> **jespdj said:**
> Because with Player you cannot create your own virtual machines; it can only run existing virtual machines.
Not Workstation because it costs money.
Server does not cost money and does allow you to create your own VMs.
 
See [https://help.ubuntu.com/community/VMware](https://help.ubuntu.com/community/VMware) and [http://www.vmware.com](http://www.vmware.com)
 
I downloaded Vmware server;  got through the 'tar' sequence; got to vmware-server-distrib; 
 
But on
 
Sudo vmware-install.pl
 
I get
 
No such command
 
I ran a dir, and the file IS there.
 
??
 
Regards,
Chuck Billow

---

### Post by csat on 2007-10-26
>Sudo vmware-install.pl

Shouldn't be sudo ./vmware-install.pl   ??

Csat

---

### Post by TwiceOver on 2007-10-26
ANyone know when VMware Server will be in the Repos?  It was easy enough to install in 7.04.

---

### Post by CWBillow on 2007-10-27
> **csat said:**
> >Sudo vmware-install.pl
 
Shouldn't be sudo ./vmware-install.pl ??
 
Csat
 
Csat:
 
Exactly.  That did it.
 
Thanks,
Chuck

---

