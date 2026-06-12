---
title: "finally figured I'd post the reason virtual machines won't run video"
date: 2012-03-25
forum: Virtualisation
---

### Post by imachavel on 2012-03-25
why virtual machines don't like running video games that take up a lot of gpu i/o processing and caching, whether your processor supports that much memory or not:

[COLOR=#1F497D][FONT=&quot]"Not  sure what the question is here, but you might want to try Citrix if  you’re serious about doing things with VMs. Be aware that until the  underlying hardware  has native support for virtualization (VT-d, VT-x, virtual graphics,  virtual WiFi, virtual machine control structure shadowing, etc.) all the  underlying hardware gets associated with one “home” OS and the other  OS’s have to go through the home OS for use.  That’s why graphics is slow, you have WiFi issues, your mouse doesn’t  work as planned, etc."[/FONT][/COLOR]

---

### Post by CharlesA on 2012-03-25
I'm not quite sure what you are getting at. If you are running a virtual machine, the hardware is virtualized, and the guest OS is shown that hardware instead of the actual hardware of the host machine.

Video support is getting better as time goes on. I believe VMWare supports DirectX9 now, but I don't think it would handle video games too well. They can run stuff like Netflix fine tho.

Also - Citrix has nothing to do with VMs, all it does it run programs on a central server and push them to clients, so the programs don't have to be installed on the client to be used.

---

### Post by haqking on 2012-03-25
> **CharlesA said:**
> I'm not quite sure what you are getting at. If you are running a virtual machine, the hardware is virtualized, and the guest OS is shown that hardware instead of the actual hardware of the host machine.

Video support is getting better as time goes on. I believe VMWare supports DirectX9 now, but I don't think it would handle video games too well. They can run stuff like Netflix fine tho.

Also - **Citrix has nothing to do with VMs**, all it does it run programs on a central server and push them to clients, so the programs don't have to be installed on the client to be used.


apart form xenserver of course ;-)

---

### Post by CharlesA on 2012-03-25
> **haqking said:**
> apart form xenserver of course ;-)
True. Xenserver is a whole different animal. ;)

I was referring to VBox/KVM/VMWare/etc, which as far as I know don't use anything even related to Citrix.

---

### Post by haqking on 2012-03-25
> **CharlesA said:**
> True. Xenserver is a whole different animal. ;)

I was referring to VBox/KVM/VMWare/etc, which as far as I know don't use anything even related to Citrix.

well no i just thought you meant that citrix has nothing to do with virtualisation.

to be honest i have no idea what the OP point or question was anyways ;-)

---

### Post by CharlesA on 2012-03-25
> **haqking said:**
> well no i just thought you meant that citrix has nothing to do with virtualisation.

to be honest i have no idea what the OP point or question was anyways ;-)
Ah, gotcha.

I suppose Citrix could be used as a form of virtualization because it runs the apps on the server and pushes them to the clients. It's not a full-blown VM solution except for Xenserver tho.

It reminds me of PXE booting, but it's not the same as it, obviously. ;)

---

### Post by collisionystm on 2012-03-25
I did see on the vmware website one time something about exploring gaming with vmware fusion. They had a virtualized half-life 2 running. Of course it all comes down to the hardware and I am sure they were running something pretty kick-***. Most modern chips have virtulization support that just needs to be enabled in the bios. Vmware only supports direct 3D for certain video cards.

[http://www.vmware.com/products/fusion/overview.html](http://www.vmware.com/products/fusion/overview.html)

---

### Post by imachavel on 2012-03-25
ok that's what he meant by Xen providing an optimised desktop experience. Well directx9 isn't directx11 now is it? Although I hate to admit that is better then what Ubuntu supports, which isn't directx at all as far as I know. What I meant is that most virtual machines, will run and open games, have suitable drivers for virtual i/o bios, for the gpu etc. But something is not clocked right, or some other error, with bios synching. Many times you try and run a game in virtual box, and the mouse goes haywire, or certain buttons malfunction. It's as if the i/o of the kernel processing the VIRTUAL guest OS, somehow interferes with other libraries. The video libraries may be adequately supported in most cases, I'm just not sure how to explain what the error could be. Perhaps using a more modern build with something more advanced then a dual core processor would fix this issue?

Wrong, basic in put out put cashing of the location of the mouse in relevance to the kernel support routines, should make no difference to how well the guest OS captures the mouse. I'm not sure what virtual code is written from, compiled java?(I know java script is embedded for web interfacing), but it makes a difference with how all the bios is virtualized. Remember that the cache and cycles and catch and processing speed of a processor can FULLY support how well a mouse is integrated and used by an OS interface user. It must have been 800 years ago(practically) that anyone had an issue getting a machine to muster up enough energy to handle mouse movements, it was never an issue with a gui, not even before there really was a gui. A mouse was just not used because a user had no reason to use on with a gui.

Now old machines had perhaps 16 bit processor speed, and a gui that could only support maybe well well under 50,000 tessels or textels in total gui cache, plus I guess no one had compiled software that could address more paged memory anyway. I don't want to get into the math of it all, but let's just say that it's obvious that with a basic low cost onboard gui these days(basic low cost, mind you) doing close to 1 billion processed polygons per second, and probably much more 2 dimension bits, mouse integration is not a memory issue with virtual bios. 

Probably much more likely a code optimization issue. I will one day try citrix xen, I don't want to download it though, I'd rather buy it, anyone know where I can?

---

### Post by haqking on 2012-03-25
> **imachavel said:**
> ok that's what he meant by Xen providing an optimised desktop experience. Well directx9 isn't directx11 now is it? Although I hate to admit that is better then what Ubuntu supports, which isn't directx at all as far as I know. What I meant is that most virtual machines, will run and open games, have suitable drivers for virtual i/o bios, for the gpu etc. But something is not clocked right, or some other error, with bios synching. Many times you try and run a game in virtual box, and the mouse goes haywire, or certain buttons malfunction. It's as if the i/o of the kernel processing the VIRTUAL guest OS, somehow interferes with other libraries. The video libraries may be adequately supported in most cases, I'm just not sure how to explain what the error could be. Perhaps using a more modern build with something more advanced then a dual core processor would fix this issue?

Wrong, basic in put out put cashing of the location of the mouse in relevance to the kernel support routines, should make no difference to how well the guest OS captures the mouse. I'm not sure what virtual code is written from, compiled java?(I know java script is embedded for web interfacing), but it makes a difference with how all the bios is virtualized. Remember that the cache and cycles and catch and processing speed of a processor can FULLY support how well a mouse is integrated and used by an OS interface user. It must have been 800 years ago(practically) that anyone had an issue getting a machine to muster up enough energy to handle mouse movements, it was never an issue with a gui, not even before there really was a gui. A mouse was just not used because a user had no reason to use on with a gui.

Now old machines had perhaps 16 bit processor speed, and a gui that could only support maybe well well under 50,000 tessels or textels in total gui cache, plus I guess no one had compiled software that could address more paged memory anyway. I don't want to get into the math of it all, but let's just say that it's obvious that with a basic low cost onboard gui these days(basic low cost, mind you) doing close to 1 billion processed polygons per second, and probably much more 2 dimension bits, mouse integration is not a memory issue with virtual bios. 

Probably much more likely a code optimization issue. I will one day try citrix xen, **I don't want to download it though, I'd rather buy it, anyone know where I can?**

from citrix would be a good start ;-)

[http://www.citrix.com/English/ps2/products/product.asp?contentID=683148](http://www.citrix.com/English/ps2/products/product.asp?contentID=683148)

---

### Post by CharlesA on 2012-03-25
> **haqking said:**
> from citrix would be a good start ;-)

[http://www.citrix.com/English/ps2/products/product.asp?contentID=683148](http://www.citrix.com/English/ps2/products/product.asp?contentID=683148)
True, but you'd still have to download it and it's quite expensive. ;)

---

### Post by imachavel on 2012-03-25
> **collisionystm said:**
> I did see on the vmware website one time something about exploring gaming with vmware fusion. They had a virtualized half-life 2 running. Of course it all comes down to the hardware and I am sure they were running something pretty kick-***. Most modern chips have virtulization support that just needs to be enabled in the bios. Vmware only supports direct 3D for certain video cards.

[http://www.vmware.com/products/fusion/overview.html](http://www.vmware.com/products/fusion/overview.html)

Oh I see, sorry I'm wrong then. So the mainboard support for virtualized code makes a big difference then? What do you look for in the bios when you reboot the computer to see if virtualized support is in there? Still, I think you more referring to gpu support, not basic input output bugs in mouse movement

---

### Post by imachavel on 2012-03-25
> **CharlesA said:**
> True, but you'd still have to download it and it's quite expensive. ;)

it's got a 'try it' link

I wonder how much more well written it is then virtualbox though. Will it actually give better virtual support? Well, only one way to find out, here I go......

---

### Post by CharlesA on 2012-03-25
> **imachavel said:**
> Oh I see, sorry I'm wrong then. So the mainboard support for virtualized code makes a big difference then? What do you look for in the bios when you reboot the computer to see if virtualized support is in there? Still, I think you more referring to gpu support, not basic input output bugs in mouse movement
99% of all modern CPUs support hardware virtualization, it will be listed in the BIOS as Virtualzation, or something similar.

You can still run VMs on a box that doesn't support hardware virtualization but the performance might be not as good.

Sidenote: I haven't noticed any problems with things with keyboard or mouse input when running either VBox, VMware or KVM outside of connecting to a VM in VBox over VRDP, which skews the mouse until the guest additions are installed.

> **imachavel said:**
> it's got a 'try it' link

I wonder how much more well written it is then virtualbox though. Will it actually give better virtual support? Well, only one way to find out, here I go......

It's enterprise-grade software, which is why it costs so much. I wouldn't use it on a home server/desktop.

---

### Post by imachavel on 2012-03-25
ok, just downloaded it, but won't install it. Well, let me reboot and look for virtual support, seen my bios many times, and don't believe the option exists, using an old dell dimension 4700, so the mainboard is a dell m3918 mainboard, it may not have support. Maybe this is interfering with mouse capture when a game is loaded in vbox(although graphics load just fine, windows drivers load just fine, and of course extensions and additions are installed)

---

### Post by CharlesA on 2012-03-25
> **imachavel said:**
> ok, just downloaded it, but won't install it. Well, let me reboot and look for virtual support, seen my bios many times, and don't believe the option exists, using an old dell dimension 4700, so the mainboard is a dell m3918 mainboard, it may not have support. Maybe this is interfering with mouse capture when a game is loaded in vbox(although graphics load just fine, windows drivers load just fine, and of course extensions and additions are installed)
Xen or VMware?

The system requirements for Xen are here:
[http://www.citrix.com/English/ps2/products/subfeature.asp?contentID=1681139](http://www.citrix.com/English/ps2/products/subfeature.asp?contentID=1681139)

EDIT: The specs for your PC are here: [http://support.dell.com/support/edocs/systems/dim4700/sm/specs.htm](http://support.dell.com/support/edocs/systems/dim4700/sm/specs.htm)

It's running a P4, so I doubt it supports hardware virtuaization, and it looks like it's only a 32-bit chip:
[http://ark.intel.com/products/27459/Intel-Pentium-4-Processor-520-supporting-HT-Technology-%281M-Cache-2_80-GHz-800-MHz-FSB%29](http://ark.intel.com/products/27459/Intel-Pentium-4-Processor-520-supporting-HT-Technology-%281M-Cache-2_80-GHz-800-MHz-FSB%29)

---

### Post by haqking on 2012-03-25
> **CharlesA said:**
> True, but you'd still have to download it and it's quite expensive. ;)

the link i posted has a find a solutions provider if you dont want to download and buy it online.

however as you said it is enterprise software it is not meant for home or single user use

---

### Post by CharlesA on 2012-03-25
> **haqking said:**
> the link i posted has a find a solutions provider if you dont want to download and buy it online.

however as you said it is enterprise software it is not meant for home or single user use
I fail at reading. :p Didn't see the "find a provider" link.

---

### Post by imachavel on 2012-03-25
> **CharlesA said:**
> Xen or VMware?

The system requirements for Xen are here:
[http://www.citrix.com/English/ps2/products/subfeature.asp?contentID=1681139](http://www.citrix.com/English/ps2/products/subfeature.asp?contentID=1681139)

EDIT: The specs for your PC are here: [http://support.dell.com/support/edocs/systems/dim4700/sm/specs.htm](http://support.dell.com/support/edocs/systems/dim4700/sm/specs.htm)

It's running a P4, so I doubt it supports hardware virtuaization, and it looks like it's only a 32-bit chip:
[http://ark.intel.com/products/27459/Intel-Pentium-4-Processor-520-supporting-HT-Technology-%281M-Cache-2_80-GHz-800-MHz-FSB%29]("http://ark.intel.com/products/27459/Intel-Pentium-4-Processor-520-supporting-HT-Technology-%281M-Cache-2_80-GHz-800-MHz-FSB%29")

doesn't look too bad:

**XenServer Host**

       
[LIST]
[*]64-bit x86 server-class system
[*]CPU: 1.5 GHz minimum, 2 GHz or faster multi-core recommended
[/LIST]
but you nailed it on the head, no virtual support in bios. And obviously those system requirements are the requirements to run one, not several. I might try running it, but what I got is xenserver-6.0.0-install-cd.iso. I am doubting that it will run any differently then vbox. Same story, additions + extensions need to be installed? I might skip it, but then I may try burning it to a cd, and trying it on a different computer. I hate installing new virtual hard drives though, for some reason it eats up a lot of memory on a host hard drive. Got some good questions answered today though. Thanks :thumbup:

---

### Post by haqking on 2012-03-25
> **imachavel said:**
> doesn't look too bad:

**XenServer Host**

       
[LIST]
[*]64-bit x86 server-class system
[*]CPU: 1.5 GHz minimum, 2 GHz or faster multi-core recommended
[/LIST]
but you nailed it on the head, no virtual support in bios. I might try running it, but what I got is xenserver-6.0.0-install-cd.iso. I am doubting that it will run any differently then vbox. Same story, additions + extensions need to be installed? I might skip it, but then I may try burning it to a cd, and trying it on a different computer. **I hate installing new virtual hard drives though**, for some reason it eats up a lot of memory on a host hard drive. Got some good questions answered today though. Thanks :thumbup:

xenserver has a convert utility for using existing virtual machines

however that being said if you like the trial you know its like $1000 for basic version to buy right ? ;-)

---

### Post by dcstar on 2012-03-26
Every time I read threads like this I again see that some people have no idea whatsoever what these enterprise class VM platforms do.

They are **not** things that you use to run petty desktop apps like games. They are platforms for running server based OSs that provide services for serious uses.

They replace the half-arsed virtualised platforms that run on top of current desktop OSs - like VMware Workstation, Player and all the other equivalents.

If you use a proper enterprise VM platform you will still need a desktop to access the VM - and you still won't get any high end graphics because that is not what they are designed to do.

---

### Post by haqking on 2012-03-26
> **dcstar said:**
> Every time I read threads like this I again see that some people have no idea whatsoever what these enterprise class VM platforms do.

They are **not** things that you use to run petty desktop apps like games. They are platforms for running server based OSs that provide services for serious uses.

They replace the half-arsed virtualised platforms that run on top of current desktop OSs - like VMware Workstation, Player and all the other equivalents.

If you use a proper enterprise VM platform you will still need a desktop to access the VM - and you still won't get any high end graphics because that is not what they are designed to do.

+1

Why you would want any VM for high end graphics apps such as games i dont know, especially enterprise apps such as Xen.

---

### Post by CharlesA on 2012-03-26
> **dcstar said:**
> Every time I read threads like this I again see that some people have no idea whatsoever what these enterprise class VM platforms do.

They are **not** things that you use to run petty desktop apps like games. They are platforms for running server based OSs that provide services for serious uses.

They replace the half-arsed virtualised platforms that run on top of current desktop OSs - like VMware Workstation, Player and all the other equivalents.

If you use a proper enterprise VM platform you will still need a desktop to access the VM - and you still won't get any high end graphics because that is not what they are designed to do.
+1. I'm not even sure I'd even want to run something like Photoshop on a VM, altho I'm sure it's possible if you have enough resources. Citrix would be a different story tho. ;)

---

### Post by SeijiSensei on 2012-03-26
I wouldn't be so quick to dismiss desktop virtualization in any form.  I run Microsoft Access on occasion in a VirtualBox VM because I want to be able to switch between it and the various Linux apps I'm running on my desktop.  Dual-booting is clearly inferior to such an arrangment, and I'd rather not have to deal with whether something runs under Wine or not.  This situation describes at most about 1% of the time I'm using a computer.  The rest of the time I can accomplish everything I need to do in Linux.

---

### Post by CharlesA on 2012-03-26
> **SeijiSensei said:**
> I wouldn't be so quick to dismiss desktop virtualization in any form.  I run Microsoft Access on occasion in a VirtualBox VM because I want to be able to switch between it and the various Linux apps I'm running on my desktop.  Dual-booting is clearly inferior to such an arrangment, and I'd rather not have to deal with whether something runs under Wine or not.  This situation describes at most about 1% of the time I'm using a computer.  The rest of the time I can accomplish everything I need to do in Linux.
That's true. I've been running a VM of *nix for my web development box and that works well. I can see desktop virtualization being used for stuff like that (and they do similar stuff like that at work too), but if you are really going to be using an enterprise virtualization software, it won't be for something like running games.

---

### Post by dcstar on 2012-03-28
> **CharlesA said:**
> 
........
but if you are really going to be using an enterprise virtualization software, it won't be for something like running games.

Especially since "games" usually require **massive** data throughput to the video output device, which is why these devices run on high-speed hardware busses and have special drivers to take advantage of them.

VM environments running on top of host OSs do not have direct access to hardware like this - and I doubt that they ever will given the complexity of essentially stealing this resource from the host system.

---

