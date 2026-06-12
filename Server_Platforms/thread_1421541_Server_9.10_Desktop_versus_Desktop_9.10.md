---
title: "Server 9.10 Desktop versus Desktop 9.10"
date: 2010-03-04
forum: Server Platforms
---

### Post by drivelab on 2010-03-04
I already posted a problem I am having with my server accepting 9.10 server. But I am loading 9.10 desktop per an article I ran accross on the net. Is there going to be any significant difference, or lack of performance in desktop versus only using server?
 
May sound like a stupid question. but I am new to working on servers
 
Thanks
 
drivelab

---

### Post by Bachstelze on 2010-03-04
The answer to your question depends on two things: the hardware configuration of the machine in question, and what you want to do with it.

---

### Post by drivelab on 2010-03-04
It is a Dell Poweredge 2550 Server.... I am setting up a RAID array for RAID 5 as we speak....  I am going to use this machine as a server for doing Multi-Hard Drive Wipes (up to 30 drives) to D.O.D specs. as well as networking with another 2 servers so that I can have one setup as my Lab Server (the one now with Desktop 9.10), and the other one where I can interface with my primary server (via cross over cable as it is mounted in a rack directly above it) all with network access to my company server, as well as remote access to the network from my home.  I don't know much on how to set these things up, by I am moving very slowly forward...;)
   Again any help at this point is much appreciated

---

### Post by Bachstelze on 2010-03-04
Then you'll probably be bound by I/O rather than by CPU and RAM, so you should be able to run a GUI with minimal impact on performance. Alqso remember that if you install a GUI and feel it's hurting performance, you can remove it without reinstalling the whole system, so it won't really hurt to try.

---

### Post by drivelab on 2010-03-04
Any advice on what kind of apps to use, or how to set something like this up....?
 
As I said I am a server virgin as it were... The SCSI interfaces I can take care of for the Multi-Drive units but it's the server to server, and communication between computers that I am not sure on how to pursue.
 
Eventually, I want to use this as my independant server apart from the company's server so that I am only using the Cat5 line as a network, and internet interface.  I have many questions... and no knowledge on how to get things going.... yet...and does this sound like I should re-think my OS platform, or is this something that can be done with just a little fine tunning?
 
Thanks again,
 
drivelab

---

### Post by FiveSidedPoly on 2010-03-04
If you are strictly using the 2550 to wipe multiple hard drives to DoD specs, you are sort of wasting the server, you are better off using a standalone computer hooked to a switch or a drive station.  Then use UPT, if you have access to it, this is a DoD standard tool.  You can boot off the UPT cd and wipe the drives that way.
 
Personally, that is how I would do it, I would not have it connect to a company network if it's purpose is to wipe dirty or classified data drives. (I say "classified" since you are wanting to wipe per DoD specs)  Also make sure you check your company's IA and other policies that concern this.
 
I myself have not loaded Ubuntu or Ubuntu Server on a 2250, check through Dell to see if it's even possible or supported, but I don't see why it shouldn't be able to handle Ubuntu Server.  
 
And like Bachstelze said, you can load a minimal GUI, like Xfce using apt-get.  Just make sure you don't load the Xubuntu setup, unless you want to.
 
As far as your other questions, what specifically are you unsure about?

---

### Post by drivelab on 2010-03-04
I understand what you are saying about "Wasting" the server... and your right.  But I already have 2 other stand alone computers, and each is set up for different drive types.  

I have a homemade setup for using a stand alone computer, and it works fine for up to 4 at a time... I have close to 30 or more drives that are SCSI and I don't feel like spending all week wiping drives 4 at a time.  

I guess I really want to build and use a server for education sake... I never really did anything like this before.... 

The Dell support for Ubuntu and the PowerEdge 2550 series I am using, is unheard of.. but they can work together... I just had a read error with the CD/DVD drive I was using, but once the OS was installed, they worked together...I just couldn't do anything because some of the files that were supposed to be installed were not.  

As for the D.O.D. program I use... it works great and yes, I know I can boot off of the CD and I do actually.  The unit that was doing the Wiping was set up for a one at a time setup.... and when you have alot of drives.... it's a headache, as I am sure you can imagine...and to top it all off the setup for doing SCSI drives was a server, and the guy before me burned up power cards left and right until he finally gave up, and eventually left the company.  

As for the company policy about server using, no I don't need to use a remote link or anything of that nature, but right now I'm interested in learning about how to use, and unlock the power of a server more than anything else.  And I don't want to use windows if I don't have to, I am sure you can understand why.

I'll be honest I don't know anything about Linux or any of its flavors, but I want to learn and figured the best way is to dive right in and see what happens.  I don't know how to install anything outside of GUI unless I read alot about it and try it a few times.  I am also trying to learn Cisco at the same time while working here and if memory serves me Cisco, and Linux are good partners.  So back to the other questions part.... What can you tell me about Linux (Ubuntu), and servers and how to make them work together.

Thanks,

drivelab

---

### Post by FiveSidedPoly on 2010-03-04
Since these are SCSI drives you are trying to wipe, I assume they are from desktops or servers, and I'm not clear as to the actual process both hardware and software you are trying to use.  Or what the previous person at your work used.  Please share it if you think it will help.
 
My particular experience is with using UPT or similar software on a stand alone machine connected to a switch, which other workstations are connected to.  Or doing it across a network to wipe and baseline systems.  Also with using a Kanguru Hard Drive Duplicator to wipe several drives at once.
 
As far as your questions about Linux/Ubuntu, I wish I could help more, but honestly I am far from a Linux guru.  By trade I am a Windows  :-$  network/system administrator as well as specializing in many proprietary digital and voice communication systems for the military.  I have had the pleasure of using a few Solaris and Red Hat systems in the past.  But right now I have a few Ubuntu workstations, HTPCs, and a Home Server all which I built myself. 
 
Everything you are attempting to do is more then capable on either the server or desktop editions.  For what you are trying to accomplish I think the desktop edition on a desktop might be best for now.  Using the server would be more difficult unless you learn how to use the CLI (command line interface) or install a GUI.   I would use the desktop edition to wipe your drives, don't want to waste any time at work, and at the same time research and learn about server and networking technology.  This will also help you get familiar/comfortable with Linux in general, which makes moving to server work easier.
 
 
Sorry this isn't the most specific question:
[INDENT]*"What can you tell me about Linux (Ubuntu), and servers and how to make them work together."*
[/INDENT]What I can tell you about Linux and servers is that it is just another server OS and can do everything you need to make a server to do.  Examples:  file sharing, web page serving, email exchange, etc.  Where it differs is in how it does it and how you make it do it.  More specific questions could get more specific answers.  :)
 
Now as far as "Cisco" training goes, if you haven't done it, hitting up the CCENT and CCNA areas is a good start.  I say this since you didn't say what "Cisco" type of training, but you seem very interested in server technology.  I wouldn't concern yourself too much with just the name "Cisco".  (Sorry if that is all overkill, but I don't know what training you've had, or to what level)
 
If you have specific questions, I can probably be more help, or I can at least point you in the right direction.  It may even help other more knowledgeable people help.

---

### Post by drivelab on 2010-03-05
Well I am not sure on what you mean by the hdwr, and sftwr process.  What I am doing is building a Lab that will have the abilities to wipe multi HD's  of any type weither SCSI, SATA, IDE, etc.
 
As for the previous person...well he did some strange things with the server, and some RAID boards, and he kept burning up the boards, and the power control cards (I don't know how, and don't want to) 
 
Now the software is just a simple DOS / Linux OS based program call Wipe Drive... it is completely independant and requires no HD at all just a CD, or Floppy to run.
 
What I have in this rack is a SUN StorEdge D1000, and a Dell PowerVault 2205 along with the 2 Servers both of them Dell PowerEdge 2550 one of which is the primary, and the other is going to be used for either wiping, or strage.  The PowerVault, and the SUN unit both hold upto 15 drives each all SCSI.
 
So right now I have the 2 Stand alone computers with No HDs in either of them just a CD Rom and hook ups for the appropriate Drive type and the Rack with all the Hrdwr I just told you.
 
Stupid question... What exactly is it that a server does??? Hold progams for other computers to access, or what... or is it a matter of what you program/design it for?
 
What I am trying to do is become versitile with servers, and the Unix/ Linux platforms.. I am already well versed in Mac... and the dreaded Windows...lol....
 
The other thing I wish to do is learn to create a network from the ground up, and manage it... not a home network, I am already doing that to an extent right now.
 
I am just looking to be able to call myself an IT pro, therefore learn as much as possible on every platform, and situation possible, consiquently put myself into any situation that may come up in the future here at work since it is a laid back environment where I can learn all day in front of the computer.  To give you an idea of the environment I am working in... the only other person in the company here that knows anything about computers is the Warehouse manager.... and he is very smart, but limited in the extent of networking, server platforms, and operation, etc. not to mention he is not multi-platform orientated.  So pretty much when someone asks me what I am doing.. it's more like "I'm just trying to make this thing work," and then they leave me alone.
 
But that is what I have, and what I am trying to do.....I'd love to talk voice or private and just kind of leech some of your knowledge on things... lol
 
Later,
 
drivelab

---

### Post by FiveSidedPoly on 2010-03-05
This reply will be short, as I'm short on time, but I'll add what I can about your last post.
 
Your post gives me a better idea of what you have going on there.
 
I have used Wipe Drive before, although quite a long time ago, it should do what you need if I can remember correctly but I only used it on stand alone computers.
 
Are you currently trying to wipe the drives using the server and the disks in the Disk Arrays you have setup?
 
I don't mind sharing information or helping out.  Even to the extent of "leeching", we all have to start somewhere.  :)
 
As for what a server actually does, depends on what you are needing it for.  They can do many things, but as I stated in my other post they specifically can be used for file sharing, web page serving, email storage/exchange.  Yes they can hold programs for other computers to access as well as be set up to access computers on a network for things such as virus scanning, intrusion detection, software updating, etc, etc.
 
It seems you want to go in a lot of different directions with your learning right now.
 
With that said what official/unofficial training have you had in the past?  This way myself of someone else can help point you in some directions to begin with.

---

### Post by drivelab on 2010-03-08
My training both official and un-official consisits of 2 yrs in a Tech School for Electronics... and from that point onward I have been taking computers apart, re-building, networking (1 or 2 home computers) since '95.  
 
I have a very strong background in both Macintosh, and Windows :-$.  I have been playing with Linux / Ubuntu for a little while now (on and off about 6-8 months).  
 
So yes as you can immagine I am trying to learn a new to me OS, and imediately intigrate it into my work environment.  The only thing I think that I am very weak on is admin functions on the windows platform, and obviosly now in Linux / Ubuntu.  
 
Networking is something I am working on (Hands-on) and finding it's just a matter of getting the computers to see and talk with eachother to get the result you want, which as I am finding out can be a pain in the a*s at times especially when it is cross platform.8-)
 
Well I must go... the servers are calling.... lol.... servers require special software to "Share" programs do they not?? For example.. I want to run a program or two on the network/ terminal computers off of the server.
 
 
drivelab

---

