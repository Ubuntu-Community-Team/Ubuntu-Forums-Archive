---
title: "New Proliant Racked Server System"
date: 2008-04-22
forum: Server Platforms
---

### Post by Ferret-Simpson on 2008-04-22
Hi, I'm waiting for my new SOHO server system to arrive. Proliant DL360 G1 and a Storageworks 4100 FC RAID Array. Hardware wise I know how to set it all up, my FC basics etc. Software wise it's more of a leap for me, since this is my first real server setup. As it stands, I know that the drivers for both my Compaq RAID arrays (Proliant internal and the Storageworks) are available, as well as that for my Fibre Channel card.

I'm aware of the basics of setting up and installing the OS, and basic guides should help me get my RAID accessible. However there's three things I don't know about yet.

1: APC 1400 UPS. Since I'm setting up a Dual RAID-5 server array, I'm not going to want to lose data suddenly. So my Servers (And possibly Leopard workstation) are going to be hooked into this. I need to know how to interface that with the Ubuntu Server OS.

2: XFCE. I have a great love of Graphical configuration, so I plan on using XFCE as a DE on my server. However, I don't want to be tied to the on board Graphics to USE it - how do I set up a VNC server as a virtual "Display" so that I can use VNC as the primary interface to the computer?

3: Which way round do I install the OS?
Ubuntu-Server then Xubuntu-Desktop?
Xubuntu-Desktop then Ubuntu-Server?


Thanks, iGraham.

---

### Post by rustybronco on 2008-04-22
questions 1 & 2 I can't help you with, much of this information you may already know, so forgive me if you do.

you will need the smart start 5.5 cd available from hp to set up your smart array.
[http://h20000.www2.hp.com/bizsupport/TechSupport/DriverDownload.jsp?prodNameId=344318&lang=en&cc=us&prodTypeId=18964&prodSeriesId=345557&taskId=135](http://h20000.www2.hp.com/bizsupport/TechSupport/DriverDownload.jsp?prodNameId=344318&lang=en&cc=us&prodTypeId=18964&prodSeriesId=345557&taskId=135)

what version of ubuntu-server do you plan on installing? 6.06.2-lts, 7.04, 7.10, hardy/8.04?

an iso of 7.04 set-up for the smart array is available here [http://ubuntuforums.org/showpost.php?p=3351077&postcount=30](http://ubuntuforums.org/showpost.php?p=3351077&postcount=30)

the problem installing  ubuntu is in the order that it loads the sym53c8xx driver. there are work-a-rounds for it, such as when you start to install ubuntu press F6 and add to the kernel line sym53c8xx.blacklist=yes sym53c8xx_2.blacklist=yes or sym53c8xx=true it all depends on the version being installed. you can search on this site or in launchpad to find more about it.

have you considered installing webmin to administer your server?
[http://www.webmin.com/](http://www.webmin.com/)

QUESTION 3. you would install xbuntu-desktop after you install the base server.
but why would you need to, when you can administer/ssh into it remotely and not have the overhead of a gui.

centos 5 is also an option, although is a rpm based distro.
[http://www.centos.org/](http://www.centos.org/) you can install it as a gui server.
 
Question's? I'm here to help all I can.

---

### Post by Ferret-Simpson on 2008-04-30
> **rustybronco said:**
> questions 1 & 2 I can't help you with, much of this information you may already know, so forgive me if you do.

you will need the smart start 5.5 cd available from hp to set up your smart array.
[http://h20000.www2.hp.com/bizsupport/TechSupport/DriverDownload.jsp?prodNameId=344318&lang=en&cc=us&prodTypeId=18964&prodSeriesId=345557&taskId=135](http://h20000.www2.hp.com/bizsupport/TechSupport/DriverDownload.jsp?prodNameId=344318&lang=en&cc=us&prodTypeId=18964&prodSeriesId=345557&taskId=135)

what version of ubuntu-server do you plan on installing? 6.06.2-lts, 7.04, 7.10, hardy/8.04?

the problem installing  ubuntu is in the order that it loads the sym53c8xx driver. there are work-a-rounds for it, such as when you start to install ubuntu press F6 and add to the kernel line sym53c8xx.blacklist=yes sym53c8xx_2.blacklist=yes or sym53c8xx=true it all depends on the version being installed. you can search on this site or in launchpad to find more about it.

QUESTION 3. you would install xbuntu-desktop after you install the base server.
but why would you need to, when you can administer/ssh into it remotely and not have the overhead of a gui..

Hi! Ok, the two servers (PL and SW) should be being shipped today or tomorrow, so this will be my weekend project.

Thanks for the heads up on the Smart-Start CD, didn't know that one. I'm installing 8.04LTS because of it's improved SAN support and better security.

I want a GUI because I like shinies. That's the most part of it. ssh is great, but I really detest most command line text editors, so it would be easier (Read: More comfortable) for me to VNC into the machine and use graphical utilities as much as possible.

I'll check up on the specs for the DL360G1 so that I can handle the kernel options, thanks for letting me know about them.

Another option for me would be to just install a few GUI packages and only start X11 when I need it.

I've also given Sol10 a consideration considering it's apparently a "Supported" OS.

---

### Post by rustybronco on 2008-04-30
> **Ferret-Simpson said:**
> I want a GUI because I like shinies. That's the most part of it. ssh is great, but I really detest most command line text editors, so it would be easier (Read: More comfortable) for me to VNC into the machine and use graphical utilities as much as possible.You can also download the tar.gz of webmin and administer the server "remotely" without a need for a gui on the server

> **Ferret-Simpson said:**
> I'll check up on the specs for the DL360G1 so that I can handle the kernel options, thanks for letting me know about them.
one more thing, If you run into not being able to install the base system and it stopping at 2%, you may be having a problem with the cd-rom and dma. you may have to update the firmware, use a different cd-rom or do a net install on your server. want to guess what is giving me a fit on my DL380 g1 installing a debian based os? 
[https://bugs.launchpad.net/fedora/+source/linux-source-2.6.22/+bug/148466](https://bugs.launchpad.net/fedora/+source/linux-source-2.6.22/+bug/148466)
[http://ubuntuforums.org/showpost.php?p=2880515&postcount=7](http://ubuntuforums.org/showpost.php?p=2880515&postcount=7)

---

### Post by Deathrend on 2008-04-30
Any SmarStart CD will work, They're all backwards compatable.  

As for CD-Rom, the 360 suffers from the same as the DL580's, they use Laptop roms to save space, however as old as they are, the support is lacking.

I've had problems with the newer 580's (g3-4, 5's seem to work fine) booting to most CD's.  A quick fix is to just use an Externl CD-Rom.  The only down side, older DL's (At least my 580 G1's) don't support USB, so it's a bit more tricky.

---

### Post by rustybronco on 2008-05-01
[https://forums11.itrc.hp.com/service/forums/questionanswer.do?admit=109447626+1209645707283+28353475&threadId=1013991](https://forums11.itrc.hp.com/service/forums/questionanswer.do?admit=109447626+1209645707283+28353475&threadId=1013991)
> There were issues with the TEAC model CD-ROM drive on Proliant DL380G1 and other systems. This was resolved with Softpaq SP16293.EXE. The drive was identified as Compaq CD-224E (Spare Part number 323332-001)


See the README.TXT file that comes with the Softpaq to identify the drive without removal. This also has the firmware update procedure if this is the type of drive you have. The hardware removal procedure for the CD-ROM drive (if required) is attached to this reply.

I hope this helps.

[http://h20000.www2.hp.com/bizsupport/TechSupport/Home.jsp?lang=en&cc=us&prodTypeId=15351&prodSeriesId=254886&submit.y=0&submit.x=0&lang=en&cc=us&y=0&x=0](http://h20000.www2.hp.com/bizsupport/TechSupport/Home.jsp?lang=en&cc=us&prodTypeId=15351&prodSeriesId=254886&submit.y=0&submit.x=0&lang=en&cc=us&y=0&x=0)

> **Ferret-Simpson said:**
> 
I've also given Sol10 a consideration considering it's apparently a "Supported" OS.so is centos5/rhel

---

### Post by Cadmus on 2008-05-01
On point one I'm fairly sure APC have good linux support, take a look at their pages for more details on the software.

On point 2 as I understand VNC it's a 'photo' of a desktop that has to be rendered somewhere on the host machine, however I do recall stuff from the post after mine in [this thread]("http://ubuntuforums.org/showthread.php?t=716641") which had advice on switching a gui on and off, so you could have a script to start it and the vnc server on an as-and-when basis.

---

### Post by Ferret-Simpson on 2008-05-01
However I've never used any RH based OS. I HAVE used Solaris. A lot. I'm comfortable with it. And while most UNIX is a muchness, quirks can be irritating. 

There was already an array set up with mirrored RAID, so no need to touch SmartStart. 8.04 server disc went in, partitioned and installed with no problems. Boots fine.

To be honest, the biggest reason I want the GUI is for network configuration. I've never done wifi in CLI before. Besides, I can always :: sudo apt-get remove xubuntu-desktop ; sudo apt-get autoremove :: if the machine's running too slowly, but I'm not expecting to be using it for anything heavy, just a SAN:NAS and possible later webserver/mailserver. (I'm not worried about heavy traffic, I figure by the time this thing can't handle it - my ad's will pay for a replacement Xserve. :D)

Basically, apart from wifi/vnc configuration (And the hintherto unknown-to-me onboard graphics can deal with rendering) - the server is up running and ready.

Now I need to make it connect to the Storageworks RAID Array.

---

### Post by rustybronco on 2008-05-01
> **Ferret-Simpson said:**
> However I've never used any RH based OS.With a gui install its almost idiot proof. > **Ferret-Simpson said:**
>  8.04 server disc went in, partitioned and installed with no problems. Boots fine.I wish I had your luck!

> **Ferret-Simpson said:**
> To be honest, the biggest reason I want the GUI is for network configuration. I've never done wifi in CLI before.see the link in my signature. [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by JAID on 2008-12-13
It is unlikely that I am as skilled as Ferret. I have never set up servers before or used Ubuntu. Hope to set up using the 64bit server in a few days. There are similarties with the setup.

The equipment is a DL380 G4 (Dual Xeon 3.6 and 6GB RAM) It is stacked full of U320 300GB drives. A compaq R3000XR UPS will be used.

I have the HP Proliant smart start Essentials Disks and can download the updates (currently to 8.1) but have no idea which version of Linux or Debian or whatever should be referred to during the process as I understand there is no reference to Ubuntu.

Have read a lot of good advice on the forum and will have things ready but it would be terrific if someone was able to give an in-depth guidance similar to the one given for the Opteron processor on, I think, the G3. Very well composed. But I would be grateful for any advice.

The little found relating to a similar server makes me wonder whether I should just load MS Server and forget Ubuntu as none have indicated successful loading. Any comment, any success stories?

Thanks 
Ian

---

### Post by JAID on 2008-12-16
Hi all,

Disregard the last post please. I read everything I could get my hands on regarding this and did'nt see one indication that Ubuntu would likely run painlessly on my machine. 

So...way against my whim, I have gone out and bought Win Server 2008. 

An IT contact similarly to one respondent in another thread, said ..."you're running a business not a server installation, you have some legacy equipment, forget Ubuntu and forget 64-bit, if Windows runs a few percent slower, the time will be well made up by not having to fiddle." The local said my combination of use as storage server, server and ocasional processing of intensively rendered material will make the quality of the XP relationship vital. 

It will remain to be seen whether I have to fiddle (I can't imagine a windows where you don't)but the rest sounds sensible enough(that will remain to be seen also.)

Anyway, I am not here but there.

Regards

Ian

---

### Post by Ferret-Simpson on 2008-12-16
> **JAID said:**
> Hi all,
An IT contact similarly to one respondent in another thread, said ..."you're running a business not a server installation, you have some legacy equipment, forget Ubuntu and forget 64-bit, if Windows runs a few percent slower, the time will be well made up by not having to fiddle." The local said my combination of use as storage server, server and ocasional processing of intensively rendered material will make the quality of the XP relationship vital. 


Well, both hardy and w2003sp2 both installed flawlessly on my G1 (And now the 3 G2's as well) - everything is fully supported out of the box, RAID, net cards, everything. The only reason I keep a windows server on the G1 (The oldest machine) is because linux hates RA4100 Fibre RAID arrays. (of which GQ.o has several).

I can't find fault with your decision. The install for me was painless and configuration was less painful than most server UNICes. However, File sharing over Samba (The reason I have Windows) is most practical using the original OS.

Personally, my judgement would have been to use 2003 not 2008 (Pretty heavy load for a machine as old as yours. :p) but obviously, the 2008 security model is much improved.

The last thing I can advise.... If you do want to try linux, you can get a DL360 G2 (Dual 1.4Ghz P3's with a gig of ram and mirrored 36GB 10K SCA's) for £40 and less delivered on eBay. It's where I got all four. Grab one, install hardy (Unfortunately, an intrepid bug means grub won't work on old Proliants - but as it's the LTS, most production servers should use hardy anyway)
Just try to avoid giving your Windows server web accessible IP's. n.n

---

### Post by JAID on 2008-12-16
> **Ferret-Simpson said:**
> ...hardy and w2003sp2 both installed flawlessly on my G1 (And now the 3 G2's as well) - everything is fully supported out of the box, RAID, net cards, everything...

Thanks for your comments Ferret-Simpson. I wish I had perceived that as actually the case behind the forum comments as my preference was to give a Linux based OS a try.

Still, despite fiddling with PC's for a quarter century servers and their OS's would want to be simple if I am likely to handle them successfully. Your level of expertise may underwrite this OS's ease of use a bit.  


QUOTE=Ferret-Simpson;6379122]...my judgement would have been to use 2003 not 2008... If you do want to try linux,...get a DL360 G2 ...install hardy ...Just try to avoid giving your Windows server web accessible IP's. n.n

Maybe I should have stayed with 2003. Another told me too but I thought the deal I got on 2008 too good to go by. I do want to get to know Linux and your suggestion makes sense. 

But...the avoid giving Windows web accessible IP's point sends a shiver. 

That was to be one of the server's key tasks. 

I have a fixed IP and was looking forward to setting up access for myself while away and to clients for controlled project materials. Maybe something like Crushftp which I bought but have'nt got around to installing can operate more securely than native Server. Good to get the alert though, I will have a read around and try and see what the state of play is.

Thanks again, Regards

ian

---

### Post by JAID on 2008-12-16
:-) see that you can't copy the text with Quotes twice, edit and expect the quotes to sit between paragraphs of response. My multiple effort above linked together and turned my respose, sandwiched into part of the whole. Somehow rustybronco pulls it off. ah! he uses the quote button above.

---

### Post by Ferret-Simpson on 2008-12-16
> **JAID said:**
> 
But...the avoid giving Windows web accessible IP's point sends a shiver. 

That was to be one of the server's key tasks. 

I have a fixed IP and was looking forward to setting up access for myself while away and to clients for controlled project materials. 
ian

Well, you'd hardly be the first person to put a Windows Server on the web, I just don't trust it's infamously secure operating model. :/

If you're only using internal storage, (Or simple external storage such as SCSI and USB) I would give Hardy Heron a shot. Especially if your system is hosting sensitive (I.E. Not your) data. It has guided partitioning, so it'll kick out a bit of space for itself and offer dual boot options. I would give it a try if you can spare 10GB, but make sure it's Hardy 8.04LTS you use and NOT Intrepid 8.10.

---

### Post by JAID on 2008-12-16
Then I will. Perhaps 8.10 will become proliant-happy in the next update.

Your dual boot experience gives confidence also. There are a half dozen 300gb U320 drives in this DL380 G4 and plenty of room spare.

The only storage I have is in the PC's and this server and all SCSI except in one laptop and one USB external drive so it that all fits with your prescription.

Security is important. I can (I imagine) isolate the RAID drives which will deal with simply backing up the PC's and also separate the internal serving drive/s/partitons but there would be fairly sensitive information on the area they could access by password. Probably not sensitive enough that anybody would bother wasting time breaking into it I would have thought but you don't know. The other interest is in drilling in generally from outside my/ourselves but I suppose that opens up all the areas drilled to potential abuse. We would not need to go past the server but that exposes enough.

You can see how raw I am at this. Interested in a play but pretty time-poor so am glad of your advice. Thanks.

---

### Post by windependence on 2008-12-16
> **JAID said:**
> Hi all,

Disregard the last post please. I read everything I could get my hands on regarding this and did'nt see one indication that Ubuntu would likely run painlessly on my machine. 

So...way against my whim, I have gone out and bought Win Server 2008. 

An IT contact similarly to one respondent in another thread, said ..."you're running a business not a server installation, you have some legacy equipment, forget Ubuntu and forget 64-bit, if Windows runs a few percent slower, the time will be well made up by not having to fiddle." The local said my combination of use as storage server, server and ocasional processing of intensively rendered material will make the quality of the XP relationship vital. 

It will remain to be seen whether I have to fiddle (I can't imagine a windows where you don't)but the rest sounds sensible enough(that will remain to be seen also.)

Anyway, I am not here but there.

Regards

Ian

Highly disagree here.

Running Windows as a web server without being behind a PIX box is suicide. If security concerns you, think again. Go to [www.netcraft.com](www.netcraft.com) and look what the web runs on. Mostly BSD, Linux, Solaris, etc. The Windoze you see is most likely protected using a DMZ and multiple enterprise class firewalls.

I have the Smart Start CD and could put up an image for you or I could fin the link to the free download for you. Someone mentioned they are backwards compatible. They are not. Anyway, you will only need the CD to configure the RAID array. Linux should run just fine on the DL360. I had it running on an 1850, which is much older. Remember, Ubuntu isn't the only distro out there and you don't have to use the latest version either. 6.06 may run better on your hardware than 8.10. CentOS is also a great choice as well as SuSE. All of these have graphical installers including network setup.

You should really re-think the GUI thing. You can load a text editor such as nano or pico if you don't like VI (don't feel bad, I don't like it either). If you MUST have a GUI, XCFE is a good choice, but you really don't need it. You can use a web interface such as WebMin or Ebox if you really need graphics. If you are going to run this thing commercially or to get experience on enterprise hardware, you should really think about forcing yourself to learn to admin via the command line. This is the way servers are meant to be administered. Even Windoze admits this by coming up with their new "Power Shell".

-Tim

---

### Post by JAID on 2008-12-17
Thanks for the reply, Tim. 

First, I have no problem with CLI's having used them before though would have to work at it for fluency. Only a matter of time. With this server CLI use should be fine.

Mine is a DL380 rather than 360 but I imagine that with the exception apparently of 8.10 said to not like the Proliants, Ubuntu would run similarly on it. My original post came of thinking that the latest version would be useful in handling recent development but if you have no trouble with earlier versions it is worth a try.

Worth a try before Server2008 I think. If it works I can either sell that or consider dual booting. You both mention security as a bonus and the cost of wasting Server2008 is nothing to possible cost of poor security.

I use Adobe and CAD applications which from time to time have to render massive detail and would like to let these dual Xeon 3.6 processors loose on that while I get on with other stuff on a PC. That is assuming the OS is smart enough to do that in the background letting it's routine operations continue.  

Netcraft was an interesting look. Your security alert also.

Thanks for the offer of the SmartStart CD. I do have it though, mine is 7.10 and I have downloaded and made an image of 8.something. This had started here because I was'nt confident that it would start into Ubuntu despite its support for Linux and Debian. Have picked up a lot of cautions and work-arounds on this forum and will not overlook your listing of editors and other modules either. 

Time I think that I just launch into and see what happens.

No doubt you will hear how it goes pretty soon.

Thanks again.

Ian

---

### Post by Ferret-Simpson on 2008-12-20
Smartstart CD's have Periodic backwards compatibility. In any case, newer servers like the G2 and G3 have better on board controls, and you should be able to do everything you need to in the System and RAID bios's on board.

Again, Centos etc are good OS's - but Ubuntu server is a very easy server OS to use (As CLI's go) and has great community support. Also, I know it works on these machines. :D

I'm personally looking forward to a stable OpenSolaris. n.n

---

### Post by JAID on 2008-12-21
I am not sure what all my concern was about. Heeding advice, I loaded 8.04.1 Hardy Heron 64-bit server edition last night and all went very smoothly. Well, not quite, I accidentally hit ESC during the final cleanup stage and it stopped at 85%, the result would'nt boot. Simply re-loading with my hands off the keyboard it went beautifully.

The machine is a DL380 G4 dual 3.6 Xeon with 6GB Ram and a half dozen U320 300gb drives.

Two drives were formatted Raid 1+0 and take the OS while the other 4 are Raid 5.

Is it true that the Gnome desktop isn't loaded with the server edition?

True or not, my installation didn't start with it. That is probably a good thing as it was a chance to get acquainted with the CLI. That seems clean and intuitive. Although i installed all the options offered in the install, Gnome does not appear to be in any of the folders and available for loading. Likewise the CD doesn't appear to hold it.

Whether it gets a lot of use or not, I will load it, also open office. 

I messed up apparently with the network connection. The machine isn't getting out and others don't see it. The D-link DIR-655 here is set to dynamically allocate IP addresses but does not appear to see it either. When I set an address in the appropriate range that does not work either. This is not a concern, it is just a matter of fiddling around until I see where I am going wrong. But it does mean not being able to get out directly and load other applications. 

(It just occurred to me that I put the subnet mask in as 255.255.255.0 I bet that is too restricting and it should just be 255.0.0.0 for my current setup - if so, I should have known what it was as there has been a lot of fiddling around here over the years with other machines.)

Regards

Ian

---

### Post by JAID on 2008-12-23
Thanks gents, going well now. I did put ubuntu-desktop on this as I was having a bit of trouble editing files in vi (not sure why but must have missed something basic in its use.) Hope to get fluent in CLI use which seemed clear and effective in the areas I did'nt mess up it will be interesting to see whether I am tenacious enough.

Ian

---

### Post by windependence on 2008-12-23
> **JAID said:**
> Thanks gents, going well now. I did put ubuntu-desktop on this as I was having a bit of trouble editing files in vi (not sure why but must have missed something basic in its use.) Hope to get fluent in CLI use which seemed clear and effective in the areas I did'nt mess up it will be interesting to see whether I am tenacious enough.

Ian

Ian, you can use nano instead of VI. It should be installed on your system. I'm no big VI fan either. I can use it, but I don't like it.

-Tim

---

### Post by JAID on 2008-12-24
Thanks Windependence,

My next challenge is to dual boot WinServer2008 (which I had hoped not to do.) 

You are obviously staying independent but I need to run Adobe Master Collection CS4 in it to handle some of the more calculation intensive stuff as that slows my PC to a standstill. (Premier pro editing AVCHD particularly) Apparently there has been no thorough success in running it on Ubuntu through Wine.

I would like to install the second OS to a another SCSI drive on this system rather than partition the Ubuntu drive. Currently there are a half dozen U320 hot-plug drives in this.

Two drives are linked in RAID 1+0 currently dedicated to Ubuntu (unless Ubuntu deletes the RAID connection upon installation - I havent looked.) At Ubuntu installation I let it have the whole drive which would mean both in RAID - probably not too wise but it sounds like something changeable. 

Four drives are currently set up as RAID 5. These are already NTFS drives. One will probably get removed from that setup and have WinSrvr2008 and Adobe MC CS4 stuck on it.

The thing I am ignorant of which stands out now is how to get the new Win 2008 boot loader and the Ubuntu loader picked up together and presented for selection at startup.

The SCSI bios permit establishment of a boot order and that will have to be directed to wherever the utility for presenting the selection is rather than either of the OS's. 

There are a number of good coverages of dual boot setups here but if concerning separate drives they seem to revolve around using Master and secondary IDE or SATA drives. 

The drives on this machine being hot plug SCSI drives, I was hoping just to:

- Remove an NTFS drive from the present RAID 5 set
- pull the present boot drive with Ubuntu off the system.
- Plug the drive taken from the RAID 5 set into the 0 slot

(These SCSI systems allocate SCSI ID's by position and there would be no need even to change the boot order in BIOS that way -Currently SCSI ID0 boots after the CD has the opportunity) 

- Load WinServer2008 on the newly plugged in drive. 
- Pull that and put it back in its own slot
- Re-plug the Ubuntu ext3 drive in the 0 slot
- Boot to ubuntu
- Somehow edit the GRUB menu list or map so that it picks up the other drive and offers it a choice for booting at startup. But it beats me yet how that will be done when these are SCSI drives as the examples have not dealt with SCSI.

Highly appreciative of any advice. Thanks

Ian

---

