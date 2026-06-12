---
title: "Setting up SOHO Network"
date: 2010-10-07
forum: Server Platforms
---

### Post by schmutztaucher on 2010-10-07
I have a good grasp on windows server 2003 but I don’t want to pay outrageous license fees for software and services and clients.
 
I am newish to terminal as I only know a few commands. I have no problem installing services for the server edition for 10.04. Its just understanding whats going wrong to troubleshoot. I guess there is you guys and I have good working knowledge of Cisco's IOS's so I understand things like routing tables and interfaces and such for troubleshooting.
 
Questions I have...
 
Can I install the desktop version of 10.04 and just install the server services? I was looking at the server guide [https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html) and would like to know if these can all be installed on the desktop edition without too much trouble. I would imagine one could just use the server edition but I would really want a graphical user environment for some of the activities, if not all that I can. This would be becuase on my skills in the CLI.
 
 
I priced out a server from Dell. I fits my budget perfectly if I go the Ubuntu 10.04 route. I was wondering if anyone sees any conflicts with the hardware for the Ubuntu OS....
 
PowerEdge T110
Subtotal
$615.00
 
PowerEdge T110: PowerEdge T110 Chassis with up to 4 Cabled Hard Drives
 
Processor: Intel® Xeon® X3450, 2.66 GHz, 8M Cache, Turbo, HT
 
Memory: 4GB Memory (2x2GB), 1333MHz, Dual Ranked UDIMM
I can get 4x4GB to max it out for 100 each. Dell charges like 1200!
 
Operating System: No Operating System
Will put on Ubuntu 10.04 LTS
 
Primary Controller: No Controller
I read of some people having problems with the PERC controller. Since my Hard drives are connected to the onboard SATA controller im hoping not to have those problems like here....
 
[http://ubuntuforums.org/showthread.php?t=1305472&highlight=mpt2sas](http://ubuntuforums.org/showthread.php?t=1305472&highlight=mpt2sas) [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530361](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530361)
 
Hard Drives: 250GB 7.2K RPM SATA 3.5" Cabled Hard Drive. 
I have 700GB SATA 7.5ish 3.5”
 
Primary Hard Drive: HD Multi-Select
 
Power Cords: Power Cord, NEMA 5-15P to C13, wall plug, 10 feet
 
Network Adapter: On-Board Single Gigabit Network Adapter
Why would I need two? Redundancy?
 
Embedded Management: Baseboard Management Controller
 
Internal Optical Drive: DVD Drive, Internal 16XDVD
 
System Documentation: Electronic System Documentation and OpenManage DVD Kit
 
Configuration never mentioned anything about the video card. I gather it is a CPLD based Matrox from my research. I have no idea if that is supported because it doesn't give the make and model of it.
 
 
 
This is quite a list of demands. I guess the biggest question is it worth it to save the money. I believe so but I am all ears to anyone elses suggestions.
 
~Schmutztaucher

---

### Post by confusedstingray on 2010-10-07
may i ask why go so dell
could get alot more for less if you built it your self,

regarding your question about the GUI i have tried the reverse,
i installed the server version then installed the desktop portion after
if you do a search you should fine something,
have you checked out this how to 
[http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3)
i have used this and did everything but did not install ispconfig

---

### Post by kevinthecomputerguy on 2010-10-07
Schmutztaucher-
 
I know this doesnt directly answer your GUI question. But you can aviod the gui all together using this. [http://woodel.com](http://woodel.com)  give it a read, you may never go gui again :- )
 
-Kevin

---

### Post by CharlesA on 2010-10-07
If you are going to install a full blown GUI onto it, just install Ubuntu desktop and then install whatever services you want it to run.

Webmin is also an option, as is SSH.

That machine looks decent, I don't believe you'd need 2 network cards unless you wanted to use it as a proxy/router/gateway/whatever.

I've got something "similar" except it's only running a dual core processor with 6GB of RAM. I use it for SSH, Samba, Virtual Machines and Apache.

---

### Post by schmutztaucher on 2010-10-08
Thanks for the help guys.

Yeah ive been doing a lot of looking into this.
I have been finding quite the array of responses to the GUI on server edition.
I understand the benefits of not having a GUI and having one.

You guys Answered all my questions with great success.
 I guess I'll give the server edition a try.

I was looking at this Dell pretty much for the lower price than other companies.
I would build my own if I had the time.

It's going to pretty much be a LAMP server with ldap, dns, and mail.

Thanks for all your help guys!

~s

---

