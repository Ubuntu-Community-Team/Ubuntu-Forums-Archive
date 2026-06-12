---
title: "What to do?"
date: 2007-04-20
forum: Server Platforms
---

### Post by borahshadow on 2007-04-20
I know that people shoulden't spam forums with the same question in multiple places but I posted this in General Help and it was just getting drowned by other posts (second page in 20min probably halfway down the 3rd page by now ) besides i didn't know where to post it in the first place so I'll try here
> Ok I was not sure where to post this so sorry if it is in the wrong spot.
I don't know weather to use the server the desktop or the alternate install. here are my circumstances

I just built a new computer it has an ECS GeForce6100Sm-M mother board(I don't know why they named the mother board after the integrated graphics chipset)and an AMD 64 X2 3600+ with 1 GB DDR2 Ram 2 250Gb SATA harddrives and a dvdburner. The two harddrives will be on a RAID 1

The Goal of this Computer in to be a fileserver for my house which at any time would have less than 5 users using it (i know overkill but it was a steal). But I also do some webdesign and I like to have a local webserver that serves my home network so this will also function as that. It will be serving a printer on the network also. and I plan on using it to serve vm(s) from vmware server.

So as you can see this is a pretty multi purpose machine but it actually does not completely stop there it will need a GUI because it will serve Vm(s) to the network but my mom will actually beusing it as a workstation.
Before people start yelling and saying do not mix workstations and servers this is the deal it is serving <5 users my mom does not use the computer superfrequently and most of her programs will be on a vm she might use linux for the Gimp or openoffice and even then she won't use it frequently

Ok now that I have provided background about my setup or wanted setup here is my question. I asked my friend who is pretty good with linux and maintains a bunch of servers and he said he would install the desktop and then manually install LAMP (webserver) components rather then the server install which will install a LAMP server for you but then you have to install GUI, GIMP, open office, firefox, utilities etc. and i agreed. But from what I read and from experimenting with the livecd you need the alternate installer for RAID setup not the desktop or server unless you installed and then RAIDED it. 

I was also wondering which version of ubuntu to use 6.06 LTS 6.10 or the new feisty 7.04 I was leaning to 7.04
ps Why does 6.06 have Long term support why did they decide to do that?
pps. Where do the version #s come from why is one 6.06 and the next 6.10 and the next 7.04?

I was reading about the new features of Feisty and it said 
Quote:
Ubuntu 7.04 Server Edition adds support for hardware facilities that speed up the use of virtual machines as well as other improved hardware support, making it an excellent choice as a web, database, mail, file and print server, the fastest growing area of Linux server use.  

From what That says it sounds like only the server edition has that support but I thought they were all about the same
But then

Quote:
Kernel
Virtualization support: KVM (the Kernel-based Virtual Machine) is included in Ubuntu 7.04, which takes advantage of the virtualization capabilities of recent Intel and AMD processors. Each virtual machine has private virtualized hardware: a network card, disk, graphics adapter, and so on. 

The 7.04 kernel is also VMI enabled, for improved performance when running on VMware hypervisors. VMI paravirtualization can be enabled in VMware Workstation 6.0 beta.  

That sounds like it is in all the editions (in the kernel) but will only help with Vmware Workstation I will be using VMware Server 
ps. My CPU does have Support for the virtualization Technology support

I don't know much about the alternate does it install a GUI and desktop programs like the desktop does can it setup a LAMP server? is it the only one with RAID support during the install? etc.

from what I can read it sounds like I need the Alternate but I don't know

sorry for any mistakes with my english I tried to make it easy to read and understand

Thanks in advance I want to start configuring this and hopefully have it mostely installed and running by tonight (my mostely Imean raid working core installed and GUI with al the programs installed and hopefully Vmware and then Ican configure things like Samba Shares tomorrow

again sorry for posting this in two places but most people don't look past the 1stor 2nd page unless they are looking for something specific

---

### Post by jtc on 2007-04-20
Before answering your questions I have a few of my own? Any particular reasons why you want to include virtualization and raid in the setup? Both of the can be really useful, but if you are rather new at running servers perhaps it would be easier to take things one step at a time?

Now to answering your questions. Hopefully I'll manager to cover at least most of them.

Regarding which versions to go for I'd say Fesity, if the serverpart is primarly for home-use and you want to use it as a desktop as well.

About the LTS-thing, it has a lot of value of you run servers in production envirement. It is simply nice then to be able to run the same installations for a couple of years.

The numbering of the version is in regards to when they were released. The system is Year.Month.

If you decide to go with RAID you probably have to go with the server-install (or possibly the alternative one). Otherwise I'd probably agree with your friends about you might just as well go with the desktop-install. When it comes to installing server daemons you'll find a lot of good instructions at [https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

What did I miss? :)

---

### Post by borahshadow on 2007-04-20
Ok Thank you
to anwser your questions 
I want RAID because this will be a file server and i have recently become semi obsessed with RAID and redundancy
and I have already been into Vm wares and vmware server before and my mom who will be using this occasionaly is into scrapbooking and most of her programs run on windows (not very wine compatable) and she does not like to learn new things technology wise but once she does she loves them so some day she might not use her vm as much but for now she will and she can access her vm from any ware in the house
wow that was long winded sorry

I agree I think I'll go Feisty for the distro version

Thanks for the explanation about the version numbers it makes perfect sense now
but what bade the ubuntu team decide to make 6.06 LTS I understand why LTS is good but why did they decide to make that version LTS

so the server install does have RAID install support from what I read only the alternate one did

and is there virtuilization support in all editions (desktop server and alternate) or does it not even matter for Vmware server?

and I was just realizing if I do the server or alternate install can't I just install the ubuntu-desktop or kubuntu- desktop package and do the same thing as the desktop install?

I have in the past installed ubuntu and installed kubuntu-desktop to turn it into a kubuntu distro

thanks again for replying I still have no replys on my other post ps a Moderator could remove that i guess as it is becoming more and more buired

---

### Post by jtc on 2007-04-20
Yes, if you'r going to run Windows on it, then I guess vmware is the obvious choice.

I really don't know why 6.06 became the first LTS, but I guess Ubuntu had progressed enough at that time for LTS to be a logical progression. The next LTS is rumored to be Feisty+2.

I'm pretty sure Server-install has support for RAID. At least that is what my memory tells me. Anyhow, it shouldn't be to hard to look up.

You'r correct in the fact that you simply can add ubuntu-desktop or kubuntu-desktop ontop of a server upgrade. No matter the install, all variants get their packages from the same repository. For that same reason it won't matter which install you choose regarding vmware.

---

### Post by borahshadow on 2007-04-20
ok thankyou
one last question does the alternate install a GUI or not thanks a ton

---

### Post by jtc on 2007-04-20
> **borahshadow said:**
> does the alternate install a GUI or not 
I'm sure you'll be able to look that one up yourself :)

---

