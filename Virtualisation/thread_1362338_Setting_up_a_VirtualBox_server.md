---
title: "Setting up a VirtualBox server"
date: 2009-12-23
forum: Virtualisation
---

### Post by caseyfw on 2009-12-23
Hi,

I've been running a LAMP [TurnKey]("http://www.turnkeylinux.org/") virtual appliance on my laptop as a development sandbox for some time, and I'd like to make a more permanent environment for this VM out of a server box I have lying around.

I'm basically looking for the best way to setup a server if my only intention is to run further virtual servers on it. From what I can tell, I need to:
[LIST]
[*]Install Ubuntu Server.
[*]Install VirtualBox-OSE (I don't really need remote desktop access to the VMs).
[*]Create a special user of some variety that will actually 'run' VirtualBox (or should VirtualBox be ran as root?).
[*]Copy my saved virtual appliances from my laptop to somewhere on the server this special user can access (I have no idea where this should be).
[*]Create an init.d script that launches VirtualBox (using said special user) at some time during the boot process - I don't know much about the Linux boot phases, but I'm assuming this should happen once multi-user starts, or something like that.
[*]Edit said script so it shuts down the VMs gracefully, and preserves memory contents.
[/LIST]
Can someone tell me if I'm barking up completely the wrong tree? At the moment I've just gone and installed Ubuntu Server 9.10, the GUI, and finally VirtualBox and am running two LAMP VMs through the account I created at install time. Not exactly typical server behaviour.

Thanks,
Casey.

---

### Post by gradinaruvasile on 2009-12-23
You dont have to be root to run VirtualBox. Only a restricted user added to the vboxusers group. And its very portable - you can copy the virtual hdd (and the .xmls, but thats not mandatory) to another machine with VBox on it and it runs without problems.
VirtualBox has an excellent command-line interface, it can be scripted easily. I used it to run Windows XP under CentOS in a production environment and it was really stable (and i am talking about older versions, 2.0-3.0).
Otherwise, if your setup works, it means its good - you will have to experiment with it.

---

### Post by caseyfw on 2009-12-23
Looks like this wasn't actually the solution I was looking for - I guess I just wanted a good Virtualisation platform to run on a server box, and after some more research further afield, turns out ESXi is the better deal.

Cheers VMware! Your party at WWDC '08 was kickin'.
Casey.

---

