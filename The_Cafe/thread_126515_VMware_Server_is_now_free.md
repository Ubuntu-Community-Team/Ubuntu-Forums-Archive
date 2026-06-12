---
title: "VMware Server is now free"
date: 2006-02-06
forum: The Cafe
---

### Post by dilmah on 2006-02-06
Hey!

Today VMware has announced that they have released [VMware Server free to the public]("http://www.vmware.com/products/server/"). It's essentially a cutdown version of their enterprise [ESX server]("http://www.vmware.com/products/server_comp.html"), but runs on pretty much any hardware because it runs on top of an existing Linux or Windows OS (as opposed to ESX which runs a custom Redhat 7.x derivation and only works on specific high end server hardware AFAIK)

Has anyone tried this yet, perhaps on a base Ubuntu installation? I'd be interested in the performance of such a configuration in terms of Speed (HDD, CPU, Network). I'm always tinkering with my boxes, but have to be careful not to damage the systems I've got running already.

My main aim would be to reduce the number of machines I have running 24/7 and also to give me a place to do testing of new distros, etc. without the extra hardware requirement everytime.
I could potentially consolidate my Ubuntu file/print/web, etc. server and my smoothwall box into one for example.
It would also be awesome to take a running snapshot of a machine before a major upgrade (say if I wanted to test an upgrade of my server to Dapper Drake :-k)

Anyway, if anyone's thinking of trying it or has already tried it let us know your thoughts and experiences.

Dilmah

---

### Post by xequence on 2006-02-06
What exactly is vmware server?

Is it like the normal vmware?

---

### Post by dilmah on 2006-02-06
[QUOTE=xequence]What exactly is vmware server?

Is it like the normal vmware?[/QUOTE]

From what is quoted on their homepage, it seems like it's based on the same designs, but inherits some of the cool features from the ESX server, such as web-based management interface, remote display of virtual machine (instead of having to vnc into my headless server to see the desktop), more CPU support and more.

It'd be interesting to also see if there's any noticable performance difference between this and the workstation product which I've used before at home.

We use VMware ESX at work, and it's very nice, and pretty fast considering there's about 10 other virtual machines also running on the same box. Be interesting to see if I can set up a similar thing at home too :D

Dilmah

---

### Post by majikstreet on 2006-02-06
whats the difference between this and vmware workstation?

---

### Post by dilmah on 2006-02-06
[QUOTE=majikstreet]whats the difference between this and vmware workstation?[/QUOTE]
It does the same basic function as workstation, but if you have a home network for example, with a server that you want to use for all your testing/development/web-hosting/firewalling, etc. you can now more easily do all this with VMware server.

With VMware workstation, you run the host and guest OS on the same system, with the guest OS displayed on a console all on the same physical machine.
With VMware server, it sounds more like the ESX server we use at work, in that there *is no* host interface at all (or it is not a requirement). You can manage all your virtual servers from any machine on the network via a web interface and you can pull up the console of any virtual machine from any machine on the network (as opposed to VNCing into the host machine to see the guest OS's consoles)

So basically, you can have the VMware server running all it's virtual machines on a linux box with no Xorg/X11 installed and access them from anywhere natively.

---

### Post by majikstreet on 2006-02-06
[QUOTE=dilmah]It does the same basic function as workstation, but if you have a home network for example, with a server that you want to use for all your testing/development/web-hosting/firewalling, etc. you can now more easily do all this with VMware server.

With VMware workstation, you run the host and guest OS on the same system, with the guest OS displayed on a console all on the same physical machine.
With VMware server, it sounds more like the ESX server we use at work, in that there *is no* host interface at all (or it is not a requirement). You can manage all your virtual servers from any machine on the network via a web interface and you can pull up the console of any virtual machine from any machine on the network (as opposed to VNCing into the host machine to see the guest OS's consoles)

So basically, you can have the VMware server running all it's virtual machines on a linux box with no Xorg/X11 installed and access them from anywhere natively.[/QUOTE]
that's uber cool. and free too :D

---

### Post by ned.b on 2006-02-07
You can download a pre-built Ubuntu virtual machine :) 

[http://www.vmware.com/vmtn/vm/](http://www.vmware.com/vmtn/vm/)

---

### Post by Orunitia on 2006-02-07
.

---

