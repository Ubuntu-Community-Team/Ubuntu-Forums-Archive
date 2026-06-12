---
title: "Headless server power saving"
date: 2008-05-04
forum: Server Platforms
---

### Post by smiler_jerg on 2008-05-04
Hello all,

I've set up a computer running Hardy Heron Server for home use. It will eventually serve files, web pages, subversion repositories and manage torrents. I intend to implement these one at a time as I get round to them.

In the meantime however, I'd like to minimise the power use of the machine. It's a 2GHz Pentium D with 1GB RAM, three HDDs (one system, two in an LVM for files) and a very capable graphics card (PCIe).

Here are the main areas I can see potential power savings:
[LIST]
[*] Disable the graphics card.

If I remove it, I don't think the computer will boot and I don't think there's a graphics chip on the motherboard. At the moment, the graphics card's fan is always on. Can I 'switch off' the graphics card when it's not in use?

[*] Spin down the disks wherever possible.

Can this be done independently for disks? For example, when there's no file-serving demands, the LVM disks needn't be spinning, but the system disk might for logs and swapping.

[*] Spinning down system and CPU fan when possible.

These are both variable-speed fans, and the CPU's hardly being pushed with these tasks. When the disks are idle, the system fan is useless. Can Linux control these?

[*]Entering standby after long periods of inactivity.

Entering one of the standby modes would obviously save considerable power. Is it possible to wake the computer from standby on any direct network addressing (i.e. not multicast)? WoL won't work for this, as clients won't be sending a magic packet.
[/LIST]

Power consumption is of a higher priority to me than performance. I can live with a little latency if I know that my power bill isn't going to be extortionate. This machine tends to get hot too (which isn't too surprising with a Pentium D. Maybe I can under-clock this somehow?).

I suppose there's a lot of questions there. Any suggestions are gladly welcomed.

---

### Post by iSplicer on 2008-05-04
> Disable the graphics card.

If I remove it, I don't think the computer will boot and I don't think there's a graphics chip on the motherboard. At the moment, the graphics card's fan is always on. Can I 'switch off' the graphics card when it's not in use?

Unfortunately, no. If you dont have onboard GFX, you cannot disable your only GFX adapter. Which one is it? You might be able to take the fan off and replace it with a heatsink if you have one.

> Spin down the disks wherever possible.

Can this be done independently for disks? For example, when there's no file-serving demands, the LVM disks needn't be spinning, but the system disk might for logs and swapping.

I think that is automatically managed by your motherboard. Your discs aren't going crazy when you are not writing to them.

> Spinning down system and CPU fan when possible.

These are both variable-speed fans, and the CPU's hardly being pushed with these tasks. When the disks are idle, the system fan is useless. Can Linux control these?

That is controlled through your Motherboard BIOS. Depending on the model, you can enable "auto" fan that slows down when usage is low.

> Entering standby after long periods of inactivity.

Entering one of the standby modes would obviously save considerable power. Is it possible to wake the computer from standby on any direct network addressing (i.e. not multicast)? WoL won't work for this, as clients won't be sending a magic packet. 

Not on a server.



In any case, even with a server running 24/7, it should not take up a crazy amount of power, dont worry.

---

### Post by windependence on 2008-05-05
Yes, I think your going a bit nuts here but here is my suggestion. Put in an older graphics card, just PCI with a heat sink if you don't want fans running. AMD chips are much more power concious with cool 'n quiet but I'm sure you don't want to replace MB and CPU. 

Biggest way to save power? Virtualize. All my servers run on just 2 4u rack boxes. I  have 5 servers running on 2 under VMware server. Power consumption is not bad considering we get about 12,000 page views per day. Really, a regular PC doesn't take that much power in the scheme of things.

-Tim

---

### Post by hyper_ch on 2008-05-05
If you really just want to operate a file server, you might want to have a look at [NSLU2]("http://en.wikipedia.org/wiki/NSLU2") (and put debian on it).

---

### Post by cox377 on 2008-05-06
> **hyper_ch said:**
> If you really just want to operate a file server, you might want to have a look at [NSLU2]("http://en.wikipedia.org/wiki/NSLU2") (and put debian on it).


I've seen debian for the NSLU2 but is ubuntu available?

---

### Post by hyper_ch on 2008-05-06
why do you want to run ubuntu on it? In the end it will be a headless server.

---

### Post by smiler_jerg on 2008-05-06
> **hyper_ch said:**
> If you really just want to operate a file server, you might want to have a look at [NSLU2]("http://en.wikipedia.org/wiki/NSLU2") (and put debian on it).
That's a good suggestion, though a little late for me. I have this machine now, and would rather not go to extra expense - this is only a hobby task. Thanks though, I'll certainly bare it in mind for the future.

Besides this, is there really no way I could get the computer into standby after a period on inactivity?

---

### Post by songshu on 2008-05-06
depending on your box, you just might want to calculate the wattage on your box and calculate the yearly spending....it might even be worth investing in new more efficient hardware, especially if you already consider to keep it running day and night for the next few years.

p.s.

if you would go with virtualisation as suggested (good idea anyway) then i would like to suggest something like vserver if you go for energy efficiency.

---

### Post by smiler_jerg on 2008-05-07
> **songshu said:**
> if you would go with virtualisation as suggested (good idea anyway) then i would like to suggest something like vserver if you go for energy efficiency.
I don't really see that I have anything to gain from virtualisation. The server's only for home use, with a maximum of seven users, and will only be performing several discrete tasks. Surely virtualisation would only help if I had several appliances for several people to administer?

Have I got something confused? Should I run each task on a separate virtual server? How does this improve efficiency compared to running the same tasks on the same server without virtualisation?

---

### Post by windependence on 2008-05-07
> **smiler_jerg said:**
> I don't really see that I have anything to gain from virtualisation. The server's only for home use, with a maximum of seven users, and will only be performing several discrete tasks. Surely virtualisation would only help if I had several appliances for several people to administer?

Have I got something confused? Should I run each task on a separate virtual server? How does this improve efficiency compared to running the same tasks on the same server without virtualisation?

Indeed, running each service on it's own virtual machine will gain you some benefits, and make it easier to back up what you have. Each VM is just a directory so you can just take a copy of the directory and move it off somewhere. That file is very portable because it's hardware independent. This means in the event of a hardware failure, you could build a completely new box and just copy the files to the new box and be up and running without any hassles at all in minutes.

Also, each VM can be allocated resources based on it's use. You may not want to give one box much RAM, but you may also have a database server you need to give a fair amount to. CPU resources are generally allocated by the scheduler in the VM software. you will also be able to run different OSs in eahc VM and there are many pre-loaded and configured VM appliances you can just download and run.

Once you start playing with virtualization you will never want to go back. It has totally changed the way I build machines.

-Tim

---

### Post by cox377 on 2008-05-22
> **hyper_ch said:**
> why do you want to run ubuntu on it? In the end it will be a headless server.


I meant ubuntu server

---

### Post by vpsville on 2008-05-22
> **smiler_jerg said:**
> 

Here are the main areas I can see potential power savings:
[LIST]
[*] Disable the graphics card.
[*] Spin down the disks wherever possible.
[*] Spinning down system and CPU fan when possible.
[*]Entering standby after long periods of inactivity.
[/LIST]



It might be helpful to plug the machine into a meter to see how many amps its drawing when fully engaged, and compare that to being idle and in 'sleep' mode.  You might be surprised to see there isn't much difference there.

Modern CPU's already scale power, and disks don't use much when they are not writing/reading.

Stopping and starting disks causes wear and will reduce the life of your server.  

As for the graphics card, it might make sense to put in a dirt cheap PCI card without a fan.  A powerful GPU can suck a lot of power but its unlikely to do so if you aren't rendering graphics.

---

### Post by encore2097 on 2010-01-27
I have a headless media server running Karmic, would it be feasible to have it sleep or enter a low power state and then wake on lan ( WOL ) when it is needed?

---

### Post by ZEROtech on 2011-08-18
> **smiler_jerg said:**
> Hello all,

I've set up a computer running Hardy Heron Server for home use. It will eventually serve files, web pages, subversion repositories and manage torrents. I intend to implement these one at a time as I get round to them.

In the meantime however, I'd like to minimise the power use of the machine. It's a 2GHz Pentium D with 1GB RAM, three HDDs (one system, two in an LVM for files) and a very capable graphics card (PCIe).

Here are the main areas I can see potential power savings:
[LIST]
[*] Disable the graphics card.

If I remove it, I don't think the computer will boot and I don't think there's a graphics chip on the motherboard. At the moment, the graphics card's fan is always on. Can I 'switch off' the graphics card when it's not in use?

[*] Spin down the disks wherever possible.

Can this be done independently for disks? For example, when there's no file-serving demands, the LVM disks needn't be spinning, but the system disk might for logs and swapping.

[*] Spinning down system and CPU fan when possible.

These are both variable-speed fans, and the CPU's hardly being pushed with these tasks. When the disks are idle, the system fan is useless. Can Linux control these?

[*]Entering standby after long periods of inactivity.

Entering one of the standby modes would obviously save considerable power. Is it possible to wake the computer from standby on any direct network addressing (i.e. not multicast)? WoL won't work for this, as clients won't be sending a magic packet.
[/LIST]

Power consumption is of a higher priority to me than performance. I can live with a little latency if I know that my power bill isn't going to be extortionate. This machine tends to get hot too (which isn't too surprising with a Pentium D. Maybe I can under-clock this somehow?).

I suppose there's a lot of questions there. Any suggestions are gladly welcomed.

I am running a Debian headless server and i don't have a graphics card and it works. i don't think that the mother board cares if you have a graphic card but keep in mind that for it to boot you have to change the settings in bios. disable "halt on all errors"  so that the bios doest stop at boot if you do not have a keyboard or mouse other than that i think it should work. And install the package for poweroff on power button i don't believe ubuntu server has that but i might be wrong.

---

