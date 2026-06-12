---
title: "How to remove my VMware installation"
date: 2008-03-08
forum: Virtualisation
---

### Post by DGentry on 2008-03-08
I did the following 

VMware Server (Run Windows and Windows applications in Ubuntu 7.10)
1.) Register for a VMware Server serial number here.
2.) from terminal “sudo apt-get install build-essential”
3.) download VMware Server for Linux - Binary (.tar.gz) here.
4.) from terminal cd dir to the downloaded file and type “tar zvxf VMware-server-1.0.4-56528.tar.gz”
5.) from terminal “cd vmware-server-distrib/”
6.) from terminal “sudo ./vmware-install.pl”
7.) hit the “enter” key for every question asked, if question doesn’t accept the “Enter” key then select “Yes”.
8.) Run VMware Server by selecting “Applicatoins –> System Tools 


 All looked like it was going well until the very end it came up with the 

What is the location of the directory of C that 
match your running kernel? [/usr/src/linux/include] 

he proposal (/usr/src/linux/include) was correct, I hit Enter.

and received: 

What is the location of the directory of C that 
match your running kernel? [/usr/src/linux/include] 

Ok, it seemed that VMware was not compatible to the new Kernel. Why didn't you say so in the first place??


Any idea on how or the step by step commands to remove this VMware?

Thanks guys

Doug Gentry

---

### Post by dcstar on 2008-03-08
> **DGentry said:**
> I did the following 

VMware Server (Run Windows and Windows applications in Ubuntu 7.10)
1.) Register for a VMware Server serial number here.
2.) from terminal “sudo apt-get install build-essential”
3.) download VMware Server for Linux - Binary (.tar.gz) here.
4.) from terminal cd dir to the downloaded file and type “tar zvxf VMware-server-1.0.4-56528.tar.gz”
.........

Just install the VMware-server package in the Partner repositories, there is no need whatsoever to stuff around with these other methods.

---

### Post by fjgaude on 2008-03-08
The normal way to uninstall:

```
sudo ./vmware-server-distrib/bin/vmware-uninstall.pl
```

or

```
sudo /usr/bin/vmware-uninstall.pl
```

Now if you have manually deleted some files this may not work.

BTW, what kernel are you using?

---

### Post by frogotronic on 2008-03-23
> **fjgaude said:**
> The normal way to uninstall:

```
sudo ./vmware-server-distrib/bin/vmware-uninstall.pl
```

or

```
sudo /usr/bin/vmware-uninstall.pl
```

Now if you have manually deleted some files this may not work.

BTW, what kernel are you using?

If I installed by Synaptic, should I manually uninstall, or just do a remove  completely?

Thanks,
CH

---

### Post by fjgaude on 2008-03-23
If did a Synaptic then try a complete remove first. If that doesn't work try the other ways.

---

