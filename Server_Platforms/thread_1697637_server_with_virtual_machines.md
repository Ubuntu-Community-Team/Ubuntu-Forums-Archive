---
title: "server with virtual machines"
date: 2011-03-01
forum: Server Platforms
---

### Post by yashar on 2011-03-01
what is the best way to run a server with virtual machines? i have a ubuntu server for my connections access and firewall but that is command line base, so what steps do i have to take to run a GUI base ubuntu server with virtual machines?

Xen looks very powerful but is that also easy to setup?

i want to run a small mail server, web server and also another machine on my server.

---

### Post by artheus on 2011-03-01
I am just curious, why would you want to have the mail and web servers on separate machines? Would be much more efficient to have those on the host machine instead.

I think you should reconsider.

What is it you want to achieve?

Tell me what parts your system should have, and how you want the different servers/applications to interact. And I would gladly help you.

Cheers,
Artheus

---

### Post by elico on 2011-03-01
it depends on the purpose of the machine and your hardware.
cause virtualization is pretty heavy duty  stuff.
xen is nice but you will might want to use headless virtualbox or KVM if you are not into doing things on the hard way.

---

### Post by yashar on 2011-03-05
artheus, my idea about separating web server and mail server is because mail server is windows base and web server is linux base, also i dont like to run all on the same os ( even if i switch to linux mail server that i'm not confident yet ) as the web server is not a popular one that web servers usually use.

thanks for help, could i run a linux server without GUI but my virtual machines has GUI, i think it is possible but if it is possible how could i access them by from server?

---

### Post by Demented ZA on 2011-03-05
As elico said: You can run virtual machines using only the command line. You can typically use vnc/kvm for displays of these virtual machines. Thus you don't need a screen even connected to your server and a gui is useless. Adding a gui to the server is unneccesary overhead, and increases possibility that something can go wrong. Plus, setting up a gui is extra effort and difficulties for something that would otherwise be fairly easy to set up.

As for running multiple virtual machines, well virtual machines are heavy on resources. You need some decent hardware and a cpu with virtualization helps.

I'm currently building a server to run at least one virtual machine to host Windows as a torrent box (for all the windows users on the network that want to use easy rdp with windows button support) and then my firewall, mail server, web server and file server will all be native Ubuntu goodness. I'd like to run an additional one or two virtual machines, but only for playing around. I ordered an intel sandybridge 2500k and an Asus P67 motherboard, with lots of ram, planning to overclock to 4.5GHz to run this system. Keep in mind only one virtual machine will be running permanently. The others will only run when I'm playing around.

I'm still deciding on what Virtual machine platform to use under the cli, but its a toss between Virtualbox(opensource) or VMware(free, but not opensource). Virtualbox is pretty good, but VMware is a little more faster and more robust at times. For my needs either will do. Also, the fact that Virtualbox is opensource has a lot more pull for me, making it an even competition.

---

### Post by TheR on 2011-03-06
> **yashar said:**
> what is the best way to run a server with virtual machines? i have a ubuntu server for my connections access and firewall but that is command line base, so what steps do i have to take to run a GUI base ubuntu server with virtual machines?

Xen looks very powerful but is that also easy to setup?

i want to run a small mail server, web server and also another machine on my server.

In my opinion it is more problem of how much experiences you have. I started with gui but after a year I almost don't use it at all. I have configured my servers to start in text mode and only when I need it I start gui. Virt manager runs perfectly good from remote system, so when I must access  windows console I can do it from remote system.

My only real problem is when I reattach for example cd image (That is because I haven't learned yet how to do it from command line:-). Remote console doesn't know about devices on server so I have to do it with Virt manager localy on server.

by
TheR

---

### Post by rubylaser on 2011-03-06
I know you said you've already got your server setup on Ubuntu, but if you want a very nice way to have web based management of your virtual machines and have support for both KVM and OpenVZ, I personally love Proxmox. [http://pve.proxmox.com/wiki/Main_Page]("http://pve.proxmox.com/wiki/Main_Page")

It's Debian based (the packages Ubuntu's based off of), so you wouldn't have a learning curve to transistion, and it's a breeze to setup / manage.

---

### Post by runeh76 on 2011-03-06
U could use gui when u need it and then when ur done, remove it.

example: [http://community.spiceworks.com/how_to/show/156]("http://community.spiceworks.com/how_to/show/156")

---

### Post by matt_symes on 2011-03-07
Hi

GUI = Webmin

[http://www.webmin.com/](http://www.webmin.com/)

Don't bother with a desktop

Kind regards

---

### Post by St_Iron on 2011-03-07
> **elico said:**
> it depends on the purpose of the machine and your hardware.
cause virtualization is pretty heavy duty  stuff.
xen is nice but you will might want to use headless virtualbox or KVM if you are not into doing things on the hard way.
Virtualbox? Have you got any performance tests with Virtualbox Headless servers? What is your experience?

---

### Post by stlsaint on 2011-03-07
With the setup you currently have you should run with lxc. It will give you the multiple machine setup you want and if you really NEED to you can also install a desktop environment. But since you say you want to run windows i would second the above notion of going with proxmox as it has kvm support along with openvz. (Thats if your server can handle kvm!)

---

