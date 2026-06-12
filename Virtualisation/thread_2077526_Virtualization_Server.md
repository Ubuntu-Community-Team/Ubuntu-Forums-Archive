---
title: "Virtualization Server?"
date: 2012-10-28
forum: Virtualisation
---

### Post by c911darkwolf on 2012-10-28
I've started to research a new project i'm looking into for use at my home.  I've had a rough start to finding information I was hoping some here could help me or at least point me in a direction.

I was wanting to take a gaming pc I have and run copies 3 copies of virtual machines.  I'm already doing this with Virtualbox.
i.e.
Opensuse
WinXp
Fedora 18 Alpha.

What i was hoping to do is find some software where i could use two pent 4 pc's i have to setp virtual machines so that when they boot up instead of loading their normal winxp i could have them load a copy and/or one of my virtual machines on my gaming pc.

some notes

both intended pc's are Pent 4 with 2 gigs of ram and 150+ network cards.  My wireless network only has 3 devices on it and all are 150n compliant or higher.

My gaming pc is:
Quad Core amd
4 gigs of ram
Ethernet 100Mb connection.

Any ideas how i could make virtual machines on my gaming pc and have these 2 pent 4's boot my virtal pc so that the load of what they do is on my gaming pc instead of the pent 4's?

Sort of like a server virtual macine & 2 workstations setup.

Thanks ahead of time!

---

### Post by kow777 on 2012-10-29
If I understand what you are asking, I think you should be able to run the VM's on your gaming pc, enable remote display on each VM, and remote to them on the P4 boxes.

---

### Post by c911darkwolf on 2012-10-29
Ahhh ok!  found the option your referring to in settings under display tab.  Gonna test this tonight when i get home!!

---

### Post by kow777 on 2012-10-30
Take note that you will have to run each remote server on a different port.

---

### Post by c911darkwolf on 2012-10-30
so like many home networks my network ip is 192.168.2.xxx

Now i did start 2 virtual machines on ports 3389 & 3390.

Now what is the best way for my pc's to connect?

I started to use Remote Desktop, but the issue i'm having is the virtual machines are on a 10.0.1.xxx network while my computer is on a 192.168.2.xxx network.  So should i be connecting to the virtual machines iP? or the IP of my host machine and using the virtual machines PORT ?

---

### Post by CharlesA on 2012-10-30
You would be connecting to the virtual machine host IP followed by the port number:

```
192.168.2.xxx:3389
```
```
192.168.2.xxx:3390
```

See here too:
[http://www.virtualbox.org/manual/ch07.html](http://www.virtualbox.org/manual/ch07.html)

---

### Post by c911darkwolf on 2012-10-30
> **CharlesA said:**
> You would be connecting to the virtual machine host IP followed by the port number:

```
192.168.2.xxx:3389
```
```
192.168.2.xxx:3390
```

See here too:
[http://www.virtualbox.org/manual/ch07.html](http://www.virtualbox.org/manual/ch07.html)

Yeah i actually found that before and tried it, i couldn't connect.  Gonna recheck Samba when i get home make sure my work groups are the same on all the PC / VM's

---

### Post by CharlesA on 2012-10-30
Check your firewall too.

---

### Post by papibe on 2012-10-30
Hi c911darkwolf.

A few thoughts:
[LIST]
[*]In order for the remote display to work, you have to install the **extension pack** on the host OS.
[*]Also, it improves considerable the experience if you install the **guest additions** on the guest (specially to adjust the screen resolution).
[/LIST]
Let us know how it goes.
Regards.

---

### Post by kow777 on 2012-10-31
> **papibe said:**
> Hi c911darkwolf.

A few thoughts:
[LIST]
[*]In order for the remote display to work, you have to install the **extension pack** on the host OS.
[*]Also, it improves considerable the experience if you install the **guest additions** on the guest (specially to adjust the screen resolution).
[/LIST]
Let us know how it goes.
Regards.
The extension pack only enables RDP, correct? Without it you can use VNC.

---

### Post by CharlesA on 2012-10-31
> **kow777 said:**
> The extension pack only enables RDP, correct? Without it you can use VNC.
Thought they removed the option to use VNC?

EDIT: Looks like it was removed, so if you want it you would have to compile it yourself:
[https://forums.virtualbox.org/viewtopic.php?f=1&t=39096](https://forums.virtualbox.org/viewtopic.php?f=1&t=39096)

---

### Post by c911darkwolf on 2012-10-31
Going to look into that, as every PC (5) in our home is running the same brand/version of VNC so I can easily maintain that.  

So ill prob be a day or 2 working out the VNC Compile and setting firewall ports before i try this again.  


Also have to route traffic so i can use the VNC on my smartphone to connect.  I can currently use it to connec to our HPTC from work

---

