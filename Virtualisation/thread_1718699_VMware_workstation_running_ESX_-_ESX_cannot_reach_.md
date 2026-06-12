---
title: "VMware workstation running ESX - ESX cannot reach LAN or internets"
date: 2011-03-31
forum: Virtualisation
---

### Post by tommygee on 2011-03-31
Hello,

I would like to have some of the experts chime in on this issue...

So I am running some tests, or at least trying to with VMware workstation 7 (Ubuntu 10.10 host) and ESX as a VM. I have installed the VM from the downloaded iso that I snatched up from vmware.com. I have an internal network of 192.168.1.0/24 and have 2 windows XP machines running already within VMware workstation. These 2 VMs can talk to each other but the ESX cannot speak to anyone nor can it make it to the gateway. I have checked everywhere to ensure that the network configs are correct and they are. However, I cannot for the life of me get this esx box to talk to anything else.

I have set the network card to bridged just like the XP machines that work but no dice. So, i am hoping one of you fine lads or gals could help me out.

I believe there is an issue with the host network device not liking the VMware installation but I have no clue.

Thank you very much in advance.

Tommygee

---

### Post by xOrphenochx on 2011-04-01
[http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=287](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=287)

---

### Post by Fire_Chief on 2011-04-01
What type of network card did you define for the ESX VM (AMD PCnet-PCI II or Intel Pro/1000 MT)?

If it's not the Intel one, I would change it in the settings and try with that instead.

Cheers!

---

### Post by tommygee on 2011-04-02
> **xOrphenochx said:**
> [http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=287](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=287)

This did the trick! Thank you very much!

---

