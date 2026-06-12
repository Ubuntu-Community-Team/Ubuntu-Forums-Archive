---
title: "Ready to change the world? - Web based OS development"
date: 2007-08-20
forum: The Cafe
---

### Post by vinod_potty on 2007-08-20
[SIZE="4"][FONT="Arial"][COLOR="Blue"]:smile:Hi,

I am just curious if a web-based Operating System can be a reality if the open source community put their hands to gether.

Also putting distributed computing to use, we can create a OS that runs on a 500 MHz 128 MB machine and gives the user the power of the community's un used OS resources.

i.e. The OS which is running on the web can direct the process to different computers in the network and can direct the output to the required machine. The OS needs to do nothing but operate as a Web-based UI (web-browser like) and send and receive operation requests on the web. Therefore, a single computer that is better suited for doing a specific kind of operation will do mostly that particular operation only and other system on the network will benefit from this.

This is Just a seed.

Please water and fertilize to help this idea grow into a reality.

I promise that if this bears a fruit, it will change the world as we know it \\:D/.

Thanks and Regards,

*_Vinod*\\:D/[/COLOR][/FONT][/SIZE]

---

### Post by Tomosaur on 2007-08-20
I'm afraid you're a little late :P

There are already quite a few web-based OSs out there, and while none are fully functional yet as far as I'm aware, they're making some decent headway.

The idea of distributing workload over the users of the OS is a decent one, but distributed computing on such a scale is a very difficult task, and is a major point of research. It's basically not ready for things of this complexity right now.

What you're describing, however - is essentially a distributed SSH network, which can already be achieved, but is generally slower and just more annoying than having your own local OS.

---

### Post by kellemes on 2007-08-20
I better upgrade bandwidth.

---

### Post by init1 on 2007-08-20
[https://desktopondemand.com/](https://desktopondemand.com/)
[http://www.cosmopod.com/](http://www.cosmopod.com/)
[https://www.youos.com/](https://www.youos.com/)
[https://desktoptwo.com/](https://desktoptwo.com/)
Many others as well.

---

### Post by LanDan on 2007-08-20
if you install FreeNX or something else on your box and connect it to the internet you have exactly that......

the only thing you need to do is to find people who are willing to pay you to use your services or sponsors off course.

the technology is here already, so what's stopping you?

---

### Post by BDNiner on 2007-08-20
I don't know if an OS that runs strictly on the web would work. So all you need is a monitor, keyboard and mouse. But the super client/ thin client model has been i use for a while now. This is the second job that I have worked at that used a Novell environment to deliver most of the applications. 

The first job I worked at a stripped down version of windows 2000 was used, and the only software installed to the local machine was Norton Anti Virus. Everything was delivered to the desktop when a user logged in, even the MS office applications. That way even when one user tried to be malicious and uninstall outlook; because they were mad, we just laughed it off, logged off the machine and logged back in. I wish i had a pic of the look on their face.

The only problem with having a web based OS, is you rely on the web. The web is redundant and therefore reliable. But when things go down all work stops. It is frustrating when you are having network problems like 25% packet loss. It is not a total outage, but try downloading e-mail to an e-mail client. The web needs 98% reliability like the landline phone system. Once this is achieved then maybe a web OS would be viable.

One last point it would probably have to be on a GIGABIT network to get anything accomplished.

---

### Post by init1 on 2007-08-20
> **BDNiner said:**
> I don't know if an OS that runs strictly on the web would work. So all you need is a monitor, keyboard and mouse. But the super client/ thin client model has been i use for a while now. This is the second job that I have worked at that used a Novell environment to deliver most of the applications. 

The first job I worked at a stripped down version of windows 2000 was used, and the only software installed to the local machine was Norton Anti Virus. Everything was delivered to the desktop when a user logged in, even the MS office applications. That way even when one user tried to be malicious and uninstall outlook; because they were mad, we just laughed it off, logged off the machine and logged back in. I wish i had a pic of the look on their face.

The only problem with having a web based OS, is you rely on the web. The web is redundant and therefore reliable. But when things go down all work stops. It is frustrating when you are having network problems like 25% packet loss. It is not a total outage, but try downloading e-mail to an e-mail client. The web needs 98% reliability like the landline phone system. Once this is achieved then maybe a web OS would be viable.

One last point it would probably have to be on a GIGABIT network to get anything accomplished.
You could set up a network boot. That's an OS on the web, right?

---

### Post by BDNiner on 2007-08-20
Network boot is an OS over a LAN. I used it to reimage corporate desktops at work. I don't know how well it would work if you are looking for a server that is not on your LAN. The way we have PXE boot setup is that once a computer receives an IP address it scans that subnet for a server to deliver the applications it needs. I don't know how to get it to scan another subnet for the server. That would require some kind of VPN setup. I am no networking guy but i will find out here at work.

---

### Post by init1 on 2007-08-20
> **BDNiner said:**
> Network boot is an OS over a LAN. I used it to reimage corporate desktops at work. I don't know how well it would work if you are looking for a server that is not on your LAN. The way we have PXE boot setup is that once a computer receives an IP address it scans that subnet for a server to deliver the applications it needs. I don't know how to get it to scan another subnet for the server. That would require some kind of VPN setup. I am no networking guy but i will find out here at work.
You seem to know more than I. But I guess it would be possible to boot via a floppy or CD that would then continue booting via a server. It seems possible, but I have never heard of such a thing.

---

### Post by jgrabham on 2007-08-20
Adobe are spending millions on this, I dont really think we can compete with that TBH

---

### Post by BDNiner on 2007-08-20
> **init1 said:**
> You seem to know more than I. But I guess it would be possible to boot via a floppy or CD that would then continue booting via a server. It seems possible, but I have never heard of such a thing.

You don't need a floppy. All newer computers have PXE boot or RPL boot. You can select in the BIOS to boot from the network. So right after your POST the computer will try and get an IP address, if it receives one then the computer will load a modified version of the linux kernel. It takes about 1 minute for the OS to load.

---

