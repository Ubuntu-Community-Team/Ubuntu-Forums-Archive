---
title: "How to plan for setting up 3-4 VM images on one server"
date: 2007-11-18
forum: Virtualisation
---

### Post by Alt69 on 2007-11-18
Hi, I would like to ask suggestions on how to set up the following server  to allow for virtualization.
First off, I’m a newbie to Ubuntu and linux. I have been practicing and doing lots of reading but am still getting my feet wet. Also, I have tried many “professional” sources in the Toronto area, but none have been able to step up to the challenge.

So here is what I would like to do:

Goal:
I would like to have a fully virtualized Ubuntu servers. I would like to run 3 or 4 virtual images off one box. 

Image 1:
-  Email
- Monitorining software
- Virtualization software 
- Print server

Image 2 :
-  Webserver 
- Web source code
- If the web server crashes  and I need to reboot it,  I don’t want to have it affect anything else.
- Is it recommended to run this in its own image or should I combine this with Image 1?

Image 3:
- Database
- If the database crashes and I need to reboot it,  I don’t want to have it affect anything else. As well

Image 4 :
- File server?
- Samba
- I also need to have a great deal of storage for lots of documents and I am not sure how to divide up the 500G drive. Does this become Image 4 – a file server?

Other info:
I would like to set up the partitions to allow for at least the /file system,  /usr, and / home are on their own partitions.  Does this mean I have to set up the partions for all the vm inages or just for the one running the as the file server? The home directory will consist of both public and private shares.

If I am running Ubuntu 7.10 on each image, how do I go about thinking about partitioning before I install anything? Do I leave the 80G main drive and slice it up into 4 partitions of 20G each? 
Do I do the same with 500G drive but ensure the largest section is for shared documents?

I will be using a Dell Poweredge 2900 with the following config. I have not received the hardware yet.


Processor:  
2 - Dual Core Xeon 2nd Processor 5130, 4MB Cache, 2.00GHz 1333MHz FSB, PE 2900 

Memory:  
 8GB 667MHz (8x1GB), Dual Ranked DIMMs 

Hard Drive:
RAID 0:  
 2- 80GB 7.2K RPM Serial ATA 3Gbps3.5-in HotPlug Hard Drive
 PERC 5/i, Integrated Controller Card 
 
Raid 1:
 3- 500GB 7.2K RPM Universal SATA 3Gbps 3.5-in HotPlug Hard Drive 
 Integrated SAS/SATA RAID 1/RAID 5, PERC 5/I Integrated


Any thoughts, suggestions would be greatly appreciated.

thanks

---

### Post by flat4 on 2007-11-19
wow, i like to know how too

---

### Post by bodhi.zazen on 2007-11-19
OpenVZ

---

### Post by Alt69 on 2007-11-19
Hi bodhi.zazen, I am not sure what you mean by OpenVZ. 

Does OpenVZ tell me how to set up the hardware prior to installing the software? Does this mean I don't have to do any prep work and just install this software and I will get everything I need? 

Still confused......
:)

---

### Post by bodhi.zazen on 2007-11-19
You can do this easily with OpenVZ. Take a look at my how-to or the OpenVZ wiki pages.

Basically you install the Open VZ kernel and then you need a template. You can download a template or make your own.

With a template you can set up and start a new machine with 3 commands in less then 2-3 min per VE (machine).

Once you have the template you can fire up a virtual machine and install and configure the server software you want on each machine.

Once you get a machine set the way you like, you can save the templates or rsync the directories in the VE.

viola

Image 1 = your desktop install

Image 2 , 3, 4 + would all be VE

I suggest you take one of the OpneVE live CD's for a spin to get a feel for just how easy it is (I like the Centos version).

---

### Post by Alt69 on 2007-11-20
I will give it try.

thanks.

---

