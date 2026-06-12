---
title: "Question:  Hardware requirements for various server types?"
date: 2007-06-16
forum: Server Platforms
---

### Post by ehull82 on 2007-06-16
Hi everyone,
I'm researching and thinking about starting a web hosting business.  I don't have much experience with linux other than minor desktop use and some CLI scripting, though I've been working as an assistant windows administrator to a medium sized bank for the last 3 years.  I have been researching using linux for my various server needs, to act as a firewall, a router, etc.  

As a sort of business test I was hoping to setup some servers at home and to run a few small websites for the next few years to gain some experience with the server environment.  I don't plan on having more than 35 users.

My major concern at the moment is hardware.  I have read repeatedly that linux has vastly different hardware requirements than Windows and that the requirements are much lower.

I was hoping to build a few small computers to act as dedicated boxes to certain tasks.  I wanted to build a box to act as a Router/DNS/DHCP Server to my small home network, a computer to act as a Proxy Server/Firewall, an e-mail server and then a LAMP box.

Any advice on any of the things I've mentioned here is most welcomed.

-Eric

---

### Post by dmizer on 2007-06-16
if you do not install a graphical desktop (command line only server), you can get away with very very small system resources.  i have a very responsive samba file server at my office, and it's set up on a 400MHz PII desktop machine.  it's probably 2 or 3 times faster than the old 700Mhz PIII windows 2000 server it replaced.

my current home web server machine is a 700mhz pIII and the only thing that is slowing it down is my blasted connection.

memory is probably the most important resource for a server (aside from diskspace anyway).  i know of people who host dedicated servers on older equipment, but i wouldn't suggest anything older than a pII for a number of reasons (not the least of which is simply the age of the hardware)

---

### Post by Gimpy_Rob on 2007-06-17
I run a LAMP and smb file server on a PIII box with 256 ram... I've yet to make it skip a beat.  Though do be carefull if just slapping them together, I had a problem with overheating hard drives.

---

