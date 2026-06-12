---
title: "How can I access my home network?"
date: 2009-09-13
forum: Virtualisation
---

### Post by tthurston on 2009-09-13
Here is my situation:
     I have a dell studio 1535 laptop running Ubuntu 9.04. I have internet conectivity through a wireless router (link sys). I am running an xp pro guest on an Ubuntu host with virtualbox 3.0. My question is how can I access my home network while inside virtualbox and connect to my desktop pc running xp pro and make use of the shared network printer and other shared folders. My desktop is connected to the router by use of an ethernet cable.
     I need this soulution because my printer is not supported so the only way to make use of it is from a windows platform, but I am not willing to give up linux on my laptop to do so, and dual booting is a waste of time and adds to my aggravation level.

Any help would be greatly appreciated.

---

### Post by Inifekt on 2009-09-13
Hello tthurston,

I am still a little new at all of this, but I had this problem the other day. In short, you have to install guest additions. I used Virtual Box, as well, so it was a simple menu click, then running the CD drive. (Devices -> Install Guess Additions) After you check that, open My Computer and run your CD drive autoplay.

After I installed guest enhancements/additions, I rebooted with in the VM and then went to My Network Places. Add a new network folder. Do a specific location, browse the entire network, and then \\VBOXSVR (this is how it was for me) should be the list, with the public folders you already made on the other machines.

I hope that helps out.

---

### Post by tthurston on 2009-09-13
[Inifekt]("http://ubuntuforums.org/member.php?u=911541") 
     I already had guest additions installed and I can access the shared folder on my laptop but not on my home network. My printer is attached to my desktop not my laptop. I want to access my desktop through the guest xp pro o/s inside the vm, through my laptop with a linux host o/s. Nothing seems to be accessable from within the vm.

---

### Post by Zhwazi on 2009-09-13
Make sure you have the NIC set to "Host adapter" or "Bridged adapter", that way your VM will be communicating on the real network. If set to "NAT" or "Internal network", Virtualbox shows the VM a fake network, and your desktop and thus printer are on a totally different network from the Virtualbox guest.

Your host's IP should be 192.168.1.1XX probably. If your guest's IP is not also in the 192.168.x.x range, it's talking to the fake network. Virtualbox usually uses the 10.x.x.x range for it's fake network.

---

