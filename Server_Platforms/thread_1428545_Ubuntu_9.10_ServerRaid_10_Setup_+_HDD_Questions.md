---
title: "Ubuntu 9.10 Server/Raid 10 Setup + HDD Questions"
date: 2010-03-12
forum: Server Platforms
---

### Post by TechMansoor on 2010-03-12
[ATTACH]149923[/ATTACH]
I have a total of 4 hdd's, 500gb 7.2rpm that I would like mirrored using raid 10. As you can see from the image, ubuntu 9.10 server isn't recognizing the full 2tb's. In fact, I'm not even sure about the configuration as I was thinking the HDD's would come up as four 500gb hdds. Instead I have the configuration above set and ready for Ubuntu to be installed on.

1. Is this typical of a server pre-configured from Dell(perc6 raid controller.

2.Why is ubuntu not recognizing the full capacity of the drives especially when it's a server install?

Thanks for any help you guys can offer! :-)

---

### Post by Zeosa on 2010-03-13
Raid10 is a mirrored and striped set, an easy way to think of it is having 2 raid0 arrays which are mirrored to one another. Having 4 500GB drives configured in raid10 will yield approximately 1TB of usable disk space (2x500GB mirrored to 2x500GB = 1TB)

As for Ubuntu not seeing the individual drives, my assumption would be that they are attached to a hardware raid controller, which presents the array to the operating system as one drive once configured.

---

### Post by TechMansoor on 2010-03-13
> **Zeosa said:**
> Raid10 is a mirrored and striped set, an easy way to think of it is having 2 raid0 arrays which are mirrored to one another. Having 4 500GB drives configured in raid10 will yield approximately 1TB of usable disk space (2x500GB mirrored to 2x500GB = 1TB)

As for Ubuntu not seeing the individual drives, my assumption would be that they are attached to a hardware raid controller, which presents the array to the operating system as one drive once configured.

Ok.It makes sense indeed. But, if I went through with Ubuntus software raid configuration, and installed ubuntu on the presented 1tb of space, how would i check if the data is being mirrored?

---

### Post by TechMansoor on 2010-03-13
Also, does most raid configurations come straight of the box pre-configured from the manufacturer? In my case I chose raid10 when setting up my server via Dell. That would be awesome to know that the work has been done in that instance, and all I have to do now is begin setting up my ubuntu server for my present purposes.

But I need solidification on that first! Any help you awesome guru's can provide is considered invaluable. I live for that stuff and literally nothing more... 

This weekend I'm getting my hands on every piece material possible. :-) :-) :-)

---

### Post by Zeosa on 2010-03-13
If you in fact have a hardware raid controller (as it seems you do) you don't need to mess with software raid at all. The operating system sees the array as a single disk which you can install to. It sounds as if Dell has already created the array for you.

---

### Post by lifsuchy on 2010-03-30
If you want to know for sure pull one of the hard drives from the system.  You should still be able to boot with 3 hard drives in a Raid 10 configuration, technically if you pull the right drives you should be able to boot with only 2.  To confirm redundancy and failure ability.
 
The only other way might be to turn of the raid in the bios and boot to a live disk and see if two of the disk match the other two, since they are striped though you won't be able to access the data you will have to look at the physical make up on a hexadecimal level.  Even then when you turn the raid back on I am not sure if it will see it properly and rebuild itself.
 
Like previous said though if it is at the hardware level you just have to trust that it is doing its job since there is no software at work here.  Better performance and reliability anyway.

---

