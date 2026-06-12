---
title: "MegaRaid Monitoring on Ubuntu 8.04.1 LTS Server"
date: 2008-09-06
forum: Server Platforms
---

### Post by SpaceTeddy on 2008-09-06
Hi Folks, 

i have a Primergy TX150 S6 Server with a MegaRaid SAS Card and 4 SATA drives attached. Everything worked fine for the install and is working smoothly. However, i have no idea how i can monitor the raid Status - i.e. i will never figure out if any of the drives fail - and if, which. 

Here is the appropriate Line from lspci for the device
> RAID bus controller: LSI Logic / Symbios Logic MegaRAID SAS 1078 (rev 04)

Can anybody tell me how i can have some sort of monitoring (some email upon failure would be sufficient for me, really) - but i have no idea where to start... 

thanks in advance

---

### Post by sonicb00m on 2008-09-06
I've just got a raid installed on my server and I was told to download the monitoring tool for linux from the manufacturers homepage.

That's as far as I have got since I haven't had time to install that util.

---

### Post by SpaceTeddy on 2008-09-06
mhm - just checked that... Problem is that they only have RHEL und SuSE packages. And as far as i can see, they only have modules for far outdated kernels (2.6.19 or something like that) which (as far as i know) don't work. So... if i download this - how do i compile the needed modules without having to redo the entire kernel ?

or what am i missing... :confused:

---

### Post by sonicb00m on 2008-09-10
I just sorted out the raid thing for my 3com card.

All I had to do was download a binary version of the software and run it. I think you can try aliening the other binaries you've got there and just running the program. If the raid is installed and working you don't need any kernel interference.

---

