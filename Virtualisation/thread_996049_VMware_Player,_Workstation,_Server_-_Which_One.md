---
title: "VMware Player, Workstation, Server - Which One?"
date: 2008-11-28
forum: Virtualisation
---

### Post by cforput on 2008-11-28
I'm trying to figure out which vmware application to use. It seems that there is vmware-player, vmware-server and vmware-workstation. All I want to do is run XP under a vmware session. I am using 7.10. I have found instructions but not much on how to use it once you get it installed.

But, my first question is which one do I use and why?

---

### Post by bodhi.zazen on 2008-11-28
Both player and server are freely available. My understanding is that Server is more powerful as you can not make new virtual machines with player (you need server or workstation).

Workstation is more powerful, as are other paid options.

So, if you wish to stay with freely available, IMO, go with Server.

Other options depend on budget.

As an alternate to VMWare you can look at VirtualBox or KVM (if you have the hard ware).

---

### Post by zero244 on 2008-12-06
Ive used all three and I prefer Vmware Player.
1. Vmware Workstation is not ready for 3d acceleration yet. Wait till they get that down before you plunk down 180 dollars. I figure it will be at least two more versions.
2. Vmware server works good. I dont like they way it switches between Linux and Windows. It has more features like being able to create VM's ect. But once you get the VM created and installed you dont need the bloat of Vmware Server.
3. What I would suggest is creat a VM with a third party program or install Vmware server temporarily to create the VM and install Windows. Then uninstall VMware server and install Vmware Player and point player to the VM created and by Server.
The VM will work just as well without the bloat and you can copy and paste files to and from Linux and Windows.
What I like about player is you can resize the Window and switch between linux and the VM much better and easier.
Just remember when you create the Windows VM have it created in a different folder than the default. That way it will be easier to point vmware Player to it. Put your XP VM in a folder called Windows XP Professional or something along those lines.
Once you have the VM create and install XP you can use on any computer.
Good luck

---

