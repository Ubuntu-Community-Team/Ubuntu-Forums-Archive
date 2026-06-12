---
title: "VMWare Virtual Network Editor"
date: 2016-05-09
forum: Virtualisation
---

### Post by asearle on 2016-05-09
Hallo Everyone,

I am current trying to set up a Bridged Network from a host PC (lubuntu) to a linux (fedora) client and vmnet0 seems to be missing.

During my googling I have found that the VM-Ware tool "Virtual Network Editor" is recommended for fixing this problem.

Vmware say that it is available here: /usr/sbin/vmware-netcfg ... but on my installation it isn't there (although vmware-player installed fine and runs well).

However, the install files for vmware-netcfg seem to have found their way into the directory:  /etc/vmware-installer.

So what I need to know is hope to get the Virtual Network Editor installed, open and running?  Can I force an install?  Or get it via Synaptic (although I couldn't seem to find it there)

Does anyone have any tips for me?  Any information would be gratefully received.

Many thanks,
Alan Searle
Cologne, Germany

PS:  And generally any tips or links to good HOWTOs on setting up Bridged Networking to a VMWare client would also be a great help.

---

### Post by asearle on 2016-05-09
I found it here ...

sudo /usr/lib/vmware/bin/vmware-netcfg

Relief  :-)

---

