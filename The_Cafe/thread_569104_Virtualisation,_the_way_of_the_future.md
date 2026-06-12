---
title: "Virtualisation, the way of the future?"
date: 2007-10-06
forum: The Cafe
---

### Post by starbase1 on 2007-10-06
Hi all,
I am extremely interested in Virtualisation - by which I mean systems like VM Ware. Now I've not tried using it in anger yet, beyond trying some of the free utility machines, but certainly talking to industry experts, some are calling it the biggest thing since the invention of the microprocessor...

That may be over the top, but I really do think it's importance will grow, and also that it will bring a huge shift of focus towards open source operating systems.

I am thinking that if you can code for one operating system, bundle it up as a virtual machine, and have it run on pretty much any hardware, you would be silly to choose one with the extra costs and licensing issues of Windows.

But I also curious - does this software open up a reasonable way for me to run XP applications I have on my PC under Ubuntu? Can I capture them and them under the other OS?

---

### Post by n3tfury on 2007-10-06
> **starbase1 said:**
> Hi all,
I am extremely interested in Virtualisation - by which I mean systems like VM Ware. Now I've not tried using it in anger yet, beyond trying some of the free utility machines, but certainly talking to industry experts, some are calling it the biggest thing since the invention of the microprocessor...

That may be over the top, but I really do think it's importance will grow, and also that it will bring a huge shift of focus towards open source operating systems.

I am thinking that if you can code for one operating system, bundle it up as a virtual machine, and have it run on pretty much any hardware, you would be silly to choose one with the extra costs and licensing issues of Windows.

But I also curious - does this software open up a reasonable way for me to run XP applications I have on my PC under Ubuntu? Can I capture them and them under the other OS?

i run both XP and Vista Ultimate under 7.10 using virtualbox because there are some apps that i cannot live without that require windows.  i also have a windows partition because i game and that doesn't work so well under virtualization.  

virtualization is indeed the future, especially from a business aspect.  there are way too many articles on the net about this, so if you're up for some reading, there's plenty to be had.

---

### Post by starbase1 on 2007-10-06
So have you successfully virtualised any of your windows applications and persuaded them to run under Ubuntu?

Nick

---

### Post by n3tfury on 2007-10-06
> **starbase1 said:**
> So have you successfully virtualised any of your windows applications and persuaded them to run under Ubuntu?

Nick

virtualized applications?  you virtualize the operating system. so the answer is no.

---

### Post by Frak on 2007-10-06
> **n3tfury said:**
> virtualized applications?  you virtualize the operating system. so the answer is no.
You can virtualize applications, Java VirtualMachine does just this, and it runs on just about every OS.

But, the OP is refering to is running native XP/Vista apps, which would refer to Wine, which is not a virtualization technique, but a compatability technique.

---

### Post by n3tfury on 2007-10-06
> **Frak said:**
> 
But, the OP is refering to is running native XP/Vista apps, which would refer to Wine, which is not a virtualization technique, but a compatability technique.

okay....  then he's as confused as me starting out his post with

> **starbase1 said:**
> 
I am extremely interested in Virtualisation - by which I mean **systems like VM Ware**

---

### Post by Frak on 2007-10-06
@starbase1, would you like a better explanation of what a VM does?

---

### Post by FranMichaels on 2007-10-06
In the case of Free and Open source software, you are likely to have a port on another platform or architecture.

If you want binary compatibility, or running several OS's within one OS (to save on hardware). Then virtualization and emulation is the way to go! :KS

Take a look at this
[http://en.wikipedia.org/wiki/Qemu](http://en.wikipedia.org/wiki/Qemu)

If you have hardware that has special support for virtualization, take a look at the kvm entry toward the bottom.

P.S. Starbase1, that clippy avatar makes me feel uncomfortable. ;)

---

### Post by AndyCooll on 2007-10-06
starbase1: As has been hinted at, there are essentially a couple of ways you can use Windows apps while in Linux (there are actually more, but let's keep it simple for now). 

1. You can virtualise a Windows environment and then run the app of your choice within that environment. So, while running your Linux desktop you fire up the virtualisation program and it appears as a window with an XP or Vista or whatever desktop inside of it ...and of course within that you run your app. To do this you'd use something like Vmware, VirtualBox or Qemu. 
2. The other way is to run your app directly in Linux itself. To do this you need something like Wine or Cedega. The way these operate is as a "layer" between the Linux OS and the Windows program. Essentially Wine "interprets" the commands. So you fire up the Windows app and Wine kicks in in the background. For instance, I'm currently playing my Football Manager game. It hasn't been ported to Linux but is running quite happily in it. This is because behind the scenes Wine is interpreting Windows commands into Linux ones and vice-versa. You should be aware however that not all programs can run under Wine.

:cool:

---

### Post by starbase1 on 2007-10-07
> **Frak said:**
> @starbase1, would you like a better explanation of what a VM does?

Yes Please! Lots of posts here since I went to bed...

I understand that virtualisation can be used to run entire operating systems. But I was under the impression it could also work at the application level - I was under the impression that yhis was what the "virtual appliances" were, as seen here:

[http://www.vmware.com/appliances/directory/cat/48](http://www.vmware.com/appliances/directory/cat/48)

They seem to be applications that will run under any OS that has a playr available, and this is what I was getting at. Is it possible to capture an installed application, and turn it into a portable appliance?

Nick

---

### Post by starbase1 on 2007-10-07
O, and I think I understand what WINE does, (at base) intercepts calls to Windows and provides equivalents, yes? I am aware of it, but have not yet tried it.

---

### Post by popch on 2007-10-07
What you can run in a 'virtual machine' is an operating system, which then in turn runs your applications.

Thus, in order to run applications designed to run under Windows, you need a Windows which is installed in your virtual machine. That means that you need a license and that you have install and maintain Windows.

Virtual appliances are complete virtual machines with the OS already set up and the applications installed and ready to run. Needless to say, no virtual appliance which can be downloaded for free can include any version of Windows (or any other piece of software which involves paying for a licence).

---

### Post by starbase1 on 2007-10-07
> **popch said:**
> What you can run in a 'virtual machine' is an operating system, which then in turn runs your applications.

Thus, in order to run applications designed to run under Windows, you need a Windows which is installed in your virtual machine. That means that you need a license and that you have install and maintain Windows.

Virtual appliances are complete virtual machines with the OS already set up and the applications installed and ready to run. Needless to say, no virtual appliance which can be downloaded for free can include any version of Windows (or any other piece of software which involves paying for a licence).

Yes, this is very much as I understood it originally.

This is why I was asking about virtualising my own applications - I was planning on booting into my (legal) copy of Windows, and running the relevant software to turn the ones I need into a VM.

Nick

---

### Post by Lord Illidan on 2007-10-07
With Virtualbox, I understand you can customise it to look almost as though your virtualised apps are native apps.

---

### Post by n3tfury on 2007-10-07
> **Lord Illidan said:**
> With Virtualbox, I understand you can customise it to look almost as though your virtualised apps are native apps.

maybe you mean seamless mode? if not, i'd be interested in knowing the other.

my seamless mode:

[http://img241.imageshack.us/my.php?image=seamlessaf0.jpg](http://img241.imageshack.us/my.php?image=seamlessaf0.jpg)

---

### Post by DeltaPHC on 2007-10-07
> **Lord Illidan said:**
> With Virtualbox, I understand you can customise it to look almost as though your virtualised apps are native apps.
Yes. In the very latest version of VirtualBox (1.5.0) there is a "seamless windows" feature. After installing Windows and 'VM additions' inside the VM, you can press a certain key combo (RightCtrl+L I believe) and it'll switch to seamless mode. There used to be a more complicated way of doing seamless windows, but it's no longer necessary with 1.5.0.

What it does is make it so windows from Windows appear side-by-side with your Linux desktop. It's really more like an illusion, but it works pretty well. It's probably the best way to run Windows apps "in" Linux (when in reality they're running in a full-blown Windows install).

---

### Post by Lord Illidan on 2007-10-07
Yes, I mean that. Never did it myself, but I hear it's good.

---

### Post by incidence on 2007-10-07
> **starbase1 said:**
> Hi all,
I am extremely interested in Virtualisation - by which I mean systems like VM Ware. Now I've not tried using it in anger yet, beyond trying some of the free utility machines, but certainly talking to industry experts, some are calling it the biggest thing since the invention of the microprocessor...


You should read about [Xen]("http://en.wikipedia.org/wiki/Xen"). Most of the hosting companies use it to provide virtual server solutions. It's *a lot* better solution than vmware, cause its GPL, and built for linux/unix servers, of course it supports others too. Virtualization is the future in many forms, i.e. in schools, instead of buying dozens of workstations, they are now able to buy only one centralized server to host the workstations, that way they'll save in hardware costs.

---

### Post by boast on 2007-10-07
> **incidence said:**
>  in schools, instead of buying dozens of workstations, they are now able to buy only one centralized server to host the workstations, that way they'll save in hardware costs.

but with each thin client costing like $300, doesn't it almost come out the same?

---

### Post by incidence on 2007-10-07
> **boast said:**
> but with each thin client costing like $300, doesn't it almost come out the same?

No cause you don't have to pay for harddrives, and such. And most of the time, these solutions are bundled (clients and the host server).

---

### Post by n3tfury on 2007-10-07
> **incidence said:**
> No cause you don't have to pay for harddrives, and such. And most of the time, these solutions are bundled (clients and the host server).

don't forget the power savings!

---

### Post by popch on 2007-10-07
> **boast said:**
> but with each thin client costing like $300, doesn't it almost come out the same?

In a 'corporate' setting, the price of the hardware is almost negligible and the price of the software is not much more relevant.

If each PC is a separate box in a separate room, then you need more staff to maintain all those machines, which can become massively more expensive than the costs of the hardware and software combined.

Any means of centralising the maintenance will almost immediately lower the costs per workstation while raising the quality of the service delivered by those workstations.

Virtualization, Terminal servers and other kinds of server based computing are means to do that. There are other useful means.

---

### Post by Frak on 2007-10-07
> **boast said:**
> but with each thin client costing like $300, doesn't it almost come out the same?
Actually, I had to buy each computer for our school at around $427 each.

---

### Post by starbase1 on 2007-10-07
So trying to get back to my original question, can I virtualise my own Windows applications running on my own Windows PC, (OS included)?

And then run the result under Ubuntu?

Nick

---

### Post by Frak on 2007-10-07
If I understand you right, then yes.

---

