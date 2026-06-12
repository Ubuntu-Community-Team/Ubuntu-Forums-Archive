---
title: "Trying to get VMWare"
date: 2008-01-21
forum: Virtualisation
---

### Post by RadiationHazard on 2008-01-21
Ok, so i'm sure this is a really stupid question but i have supplied a screen shot below. what do i put in the freaking yellow box??? hahaha

---

### Post by jleaker01z on 2008-01-21
You have to apply for a serial number.  Go to VMWares site and there is a form you can fill out that will then grant you a serial number.

---

### Post by RadiationHazard on 2008-01-21
thanks for the reply. :) and i know i'm already there. but what serial number is it talking about? :confused:

and VMWare is free correct?

---

### Post by bobbilda on 2008-01-21
just enter the number of virtual machines that you will be installing, you'll get a serial number for each!


if it's a server that your after, one server can 'run' many guest virtual machines ie. winxp, ubunto, etc. etc.

hope this helps

bob

---

### Post by bobbilda on 2008-01-21
the serial number is require when you install the virtual server.

bob

---

### Post by RadiationHazard on 2008-01-21
wait. so do i put a # for every os that i want to run through vm or just the number one since this is the only computer that i will be installing it too?:lolflag:

---

### Post by jleaker01z on 2008-01-21
> **RadiationHazard said:**
> wait. so do i put a # for every os that i want to run through vm or just the number one since this is the only computer that i will be installing it too?:lolflag:

Just the one, if you are installing VMWare Server...which is what you actually want.  VMWare Player will run a VIrtual Machine, but doesnt create one.

---

### Post by RadiationHazard on 2008-01-21
thank you very much for all your help! :):):)

---

### Post by bobbilda on 2008-01-21
just the one if its one machine that you will be using it on, although I had 3 for when i install it on another 2 machines. Its a good product, I'm very pleased with it, although it's a bit quirky when you need to install the tools with ubuntu, and believe me you WILL need install the tools.

bob

---

### Post by RadiationHazard on 2008-01-21
Ok, I lied. Sorry bout that! Haha this thread isn't solved just yet. I'm getting an error. What do i do? :confused: Screen shot below. Do i actually have to have the installation disk to run these programs???:(

---

### Post by RadiationHazard on 2008-01-21
Ok, so i'm trying to mount the tools or whatever. but i'm haveing a REALLY hard time finding how too? I'm not able to for the VM options screen shot below. so what do i do. This is like my 3rd or 4th time to try this and i've never been able to get it even this far. so please people i think i've almost got it! please help me!:(:(

---

### Post by bodhi.zazen on 2008-01-21
You are doing just fine.

You need to boot (ie start) the guest OS. Once the guest is running you can install the tools. How to install the tools depends on the Guest OS.

See if these links help :

[https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)

[http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto](http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto)

[https://help.ubuntu.com/community/VMware/Tools](https://help.ubuntu.com/community/VMware/Tools)

---

### Post by RadiationHazard on 2008-01-22
Ok, so the only one that seemed like it would help was the last one. and i tryed doing it and the install VMWare tools is still blocked.:( there is a screen shot below it shows the site i was at. the command they were telling me to use. me using the command in the terminal and that the option is still blocked

---

### Post by bodhi.zazen on 2008-01-22
I am guessing, but I think you need to power the virtual machine on first.

I am not sure if the VMTools are available for Solaris, you can try, compile it from source.

---

### Post by RadiationHazard on 2008-01-22
what do you mean compile it from sorce? i'm still not very good with linux.

---

### Post by RadiationHazard on 2008-01-22
ok, so i never really wanted to run soloris anyways i just randomly picked it. what i'm really wanting to run is windows xp home edition i installed the vmware tools after i ran the xp or w/e and then after i looked and saw that the vmware tools was installed i restarted it and i'm still getting this error.(screen shot below.)

---

### Post by RadiationHazard on 2008-01-22
do you think that i could get a reply someone?? haha please and thank you. i'd LOVE to get this up and going if someone would be willing to help me. =[

---

### Post by Zenthes on 2008-01-23
> **RadiationHazard said:**
> ok, so i never really wanted to run soloris anyways i just randomly picked it. what i'm really wanting to run is windows xp home edition i installed the vmware tools after i ran the xp or w/e and then after i looked and saw that the vmware tools was installed i restarted it and i'm still getting this error.(screen shot below.)

Ok I'll try to answer your question.  What your trying to do is install xp on the VM machine.  VMserver can't actually release windows XP or any other of there series of software because that would be piracy.  So you need to get your hands on a copy of XP, 95, 98, 2000.  What ever version of windows you'd like to run and actually install it like you were installing it on a regular computer.  

As for not actually having a CD ?  and just trying to install from an ISO i have no idea how to do that but i'd love to learn :)

---

### Post by tszanon on 2008-01-23
> **Zenthes said:**
> and just trying to install from an ISO i have no idea how to do that but i'd love to learn :)
Edit the properties of the virtual machine. Set the CD driver to an ISO instead of a device and, of course, tell it where's the ISO image you want it to use.

If I'm not clear enough, I can post some screenshots later, just ask. :)

---

