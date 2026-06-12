---
title: "So i read VMware broke the GPL?"
date: 2010-05-11
forum: The Cafe
---

### Post by themarker0 on 2010-05-11
I read Vmware's ESX server has a GPL driver in it. Did anyone ever follow up on that?

---

### Post by Bachstelze on 2010-05-11
So I read u liek mudkipz?

Also, even if ESX had a GPL driver in it, that probably wouldn't make it violate the GPL, as long as the sources of the driver are available.

---

### Post by themarker0 on 2010-05-11
> **Bachstelze said:**
> So I read u liek mudkipz?

Also, even if ESX had a GPL driver in it, that probably wouldn't make it violate the GPL, as long as the sources of the driver are available.

I really don't know. In Linux Pro Magazine in the kernal dev area, it had that, in a recent issue. I wanted to simply know if anyone took it further then accusations.

---

### Post by koenn on 2010-05-11
> **themarker0 said:**
> I really don't know. In Linux Pro Magazine in the kernal dev area, it had that, in a recent issue. I wanted to simply know if anyone took it further then accusations.

There's a lot of linux in ESX. The entire service console (the ESX "shell" you get when you log on to an ESX through ssh) is linux - RedHat based, or so I'm told. 
(see also [http://www.petri.co.il/5_ways_to_adminster_esx_server.htm](http://www.petri.co.il/5_ways_to_adminster_esx_server.htm) )

GPL software os freely redistributable, even embedded in ESXen, as long as you get a copy of the GPL with it, and access to the relevant source code, as Bachstelze said.
I'm not sure how VMware handles that.

---

### Post by themarker0 on 2010-05-11
From what i read because how it was packed, and now the entire ESX system should've become GPL now.

---

### Post by phrostbyte on 2010-05-11
The kernel is a bit of a gray area. One could probably argue that Nvidia drivers and AMD fglrx violating the copyright agreement on the kernel as well. Just no one has really been taken to court on the idea of kernel-mode binary blobs (yet?).

---

