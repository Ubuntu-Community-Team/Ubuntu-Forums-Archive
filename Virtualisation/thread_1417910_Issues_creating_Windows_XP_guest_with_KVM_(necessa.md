---
title: "Issues creating Windows XP guest with KVM (necessary evil)"
date: 2010-02-27
forum: Virtualisation
---

### Post by Sointense on 2010-02-27
Hey Folks,
Issue: can't access Winxp guest to install it remotely.

Brought up a fresh 9.10 64 bit headless server to use as a proof of concept box to VM some Windows OS's which have Apps that don't play well with each other.
The box has an Intel 3ghz dual processor and I've enable virtualization in the Bios.
2 gig of ram - 150gig SATA drive 

I installed  everything necessary as outlined in the Ubuntu KVM help -
[https://help.ubuntu.com/community/KVM/](https://help.ubuntu.com/community/KVM/)
I also followed the guide as best I could to create the Windows guest

My issue is this:
When I run the virt-install, the process creates the correct storage space and goes up to 100% then lists "Creating Domain..."
And then the next line will just hang saying Domain installation in progress. Waiting fr domain to complete installation.

Since I have no GUI, I cannot use virt viewer locally, so I have been trying to see if I can connect remotely with tightVNC on port 5900 or 5901 (host address), but it fails to connect. If I CTRL-C out of the install on the server, I can see the xpsp2.XML file, and the qcow2 file. If I run virsh list xpsp2, the Domain shows to be running.
If I do a domifstat xpsp2 vnet0, the packet totals go up a few bytes every time I run it so I am guessing its live.
If I do a dominfo, I get a listing but the OS type is hvm. Not sure if this is correct.

Any help would be appreciated. Based on my reading I did not think this would have been a big deal. I'm hoping its just a "dah" thing!!

Thanks in advance
CJ
Long Island, NY](*,)

---

