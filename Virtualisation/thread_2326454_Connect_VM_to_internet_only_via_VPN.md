---
title: "Connect VM to internet only via VPN"
date: 2016-06-01
forum: Virtualisation
---

### Post by rasmus91 on 2016-06-01
Hey you guys.

I work at a company where we use windows all the time. At home, however i use only Ubuntu, yet sometimes i do need Visual Studio, or some other proprietary windows-only software from Microsoft.

As a solution for me instead of dualbooting, i got this idea into my head that i could do a Windows 10 install in a VM (because of snapshot management and stuff, this makes maintaining a "windows partition" so much easier) and then make it connect (as if through a hardware VPN) directly to the network at work, so the VM can be joined to the work domain. I am, however, quite uncertain how to do that networking part.

I've been googling it quite a bit, but i don't seem to find anything addressing this particular problem directly. So any help in this regard will be deeply appreciated. 

My machine, btw. is easily capable of handling a VM along side the OS, with 8 cores @3.5 ghz and 16 Gb of RAM.

Thank you.

---

### Post by MAFoElffen on 2016-06-01
Yes. I do Win 10 VM guest, vpn software (I use Cisco VPN). Then a Remote Desktop. Does not matter if the guest is VM net External (NAT) or Host ... as the connection is internet to the remote site. You can do this with your choice of Virtual hypervisors.

Was that what you are asking about?

---

