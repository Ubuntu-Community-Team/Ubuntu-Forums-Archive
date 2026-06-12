---
title: "Isolated Web Server on Ubuntu Server (Virtualization?)"
date: 2008-06-26
forum: Server Platforms
---

### Post by lixoman100 on 2008-06-26
Hello,

I'm setting up a couple Ubuntu servers on a company in the near future. One of them is going to offer authentication for Windows machines backed up by LDAP and a SVN server.

It would be cheaper if it was also possible to run some random web services on that machine (DotProject, a Wiki, some random projects) but, since this machine has some very important and sensitive data, I wouldn't like to run those alongside the important stuff.

The first solution would be to run another computer as a dedicated web server, but this is a small company and I am sure there is no need of a dedicated hardware for that. Installing everything on the same server would work, but I do have several security concerns.

The ideal solution, the way I see it, would be to virtualize another machine on this one just for the web services. That way, if things go haywire and the web server gets compromised, it won't affect directly the LDAP and SVN server since there will be some isolation in place.

The thing is, it seems that the most cited solutions for this (KVM and Xen) need hardware support for that on the processor, and the processor of the machine I intend to run this on does not have the required extensions. I'd like to ask, then, if anyone here has any experience or insight regarding this and any suggestions to make regarding the direction I should take with this. Right now I see 3 possibilities:

1 - Find some solution that is able to virtualize a server without hardware support, like VMWare does, but something that is able to run on the command line, that can be started with the machine etc. despite the performance problems;

2 - Put a request for new hardware with support for the virtualization extensions, installing Xen or KVM on it (which one would be better, by the way?). I don't know if the company will be able to provide the budget for this (I know that all I would need would be a computer with a modern processor, even my notebook has the required extensions, but it is still a new machine that will have to be bought);

3 - Give up virtualization and get a existing machine exclusevily for the web services (the company can spare a machine for this, but they have no machines with a processor that supports hardware virtualization).


I appreciate any tips regarding this. Thanks in advance for your time.

---

### Post by rickyjones on 2008-06-26
> **lixoman100 said:**
> Hello,

I'm setting up a couple Ubuntu servers on a company in the near future. One of them is going to offer authentication for Windows machines backed up by LDAP and a SVN server.

It would be cheaper if it was also possible to run some random web services on that machine (DotProject, a Wiki, some random projects) but, since this machine has some very important and sensitive data, I wouldn't like to run those alongside the important stuff.

The first solution would be to run another computer as a dedicated web server, but this is a small company and I am sure there is no need of a dedicated hardware for that. Installing everything on the same server would work, but I do have several security concerns.

The ideal solution, the way I see it, would be to virtualize another machine on this one just for the web services. That way, if things go haywire and the web server gets compromised, it won't affect directly the LDAP and SVN server since there will be some isolation in place.

The thing is, it seems that the most cited solutions for this (KVM and Xen) need hardware support for that on the processor, and the processor of the machine I intend to run this on does not have the required extensions. I'd like to ask, then, if anyone here has any experience or insight regarding this and any suggestions to make regarding the direction I should take with this. Right now I see 3 possibilities:

1 - Find some solution that is able to virtualize a server without hardware support, like VMWare does, but something that is able to run on the command line, that can be started with the machine etc. despite the performance problems;

2 - Put a request for new hardware with support for the virtualization extensions, installing Xen or KVM on it (which one would be better, by the way?). I don't know if the company will be able to provide the budget for this (I know that all I would need would be a computer with a modern processor, even my notebook has the required extensions, but it is still a new machine that will have to be bought);

3 - Give up virtualization and get a existing machine exclusevily for the web services (the company can spare a machine for this, but they have no machines with a processor that supports hardware virtualization).


I appreciate any tips regarding this. Thanks in advance for your time.

I would recommend the free VMWare Server product. This should accomplish what you want to do.

Sincerely,
Richard

---

### Post by dca on 2008-06-26
If you run VMware on a headless server or more to the point Ubuntu Server, I think the only other req'd dependency is the xorg-devel package, not all of 'X'...
 
This may help...
 
[http://www.ubuntu-unleashed.com/2007/12/howto-install-vmware-server-on-ubuntu.html](http://www.ubuntu-unleashed.com/2007/12/howto-install-vmware-server-on-ubuntu.html)

---

### Post by lixoman100 on 2008-06-26
Thank you for the tips. I actually managed to install VMWare Server, but it seemed to give me some problems regarding running it without a GUI. According to your link, I need to take a look at VMWare Console. I'll go in that direction. Thanks!

---

### Post by rickyjones on 2008-06-26
> **lixoman100 said:**
> Thank you for the tips. I actually managed to install VMWare Server, but it seemed to give me some problems regarding running it without a GUI. According to your link, I need to take a look at VMWare Console. I'll go in that direction. Thanks!

What you'll end up doing is running the VMWare Console program from another PC (Linux or Windows) and you will use this tool to create and manage your virtual machines.

-Richard

---

### Post by lixoman100 on 2008-06-26
Yes, I finally figured out I could use the VMWare Console. I just installed, configured it, created the virtual machine, installed Ubuntu with LAMP, configured it to start automatically with the host machine and everything is working perfectly. Thanks for all the help!

---

