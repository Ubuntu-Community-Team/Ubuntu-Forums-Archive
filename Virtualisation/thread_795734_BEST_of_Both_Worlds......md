---
title: "BEST of Both Worlds....."
date: 2008-05-15
forum: Virtualisation
---

### Post by himagain on 2008-05-15
Hi people,
Quick history:
Been a trier of Linux for years and years - never got a single distro to work fully/properly. Ubuntu has been closest. I'm a serious 'Net user (trying to make a living).
I do a lot of research (am a writer) and get hit with viruses and nasties non-stop. (Get 800+ emails per day, on net av. 9 hours seriously - do not play games - do not have a single on on my system.

I only need a few programs from Windows, but can't find their equals in Linux.
1. DragonDictate (professional voice-2-text program) The only one of its kind that works.  
2. Dreamweaver (Website building seriously) 
3. EudoraPro (THE email program for serious users) 
(No Penelope is not gonna make it I fear)

I have bitten the bullet and started using VIRTUAL MACHINES.
Settled on VirtualBox after lots of pain. It is STILL painful, but works.

SO:
Installed Kbuntu on a clean new machine.  
Installed Vbox.
Installed XP inside the Vbox.

It looks like the only course to take for someone like me who needs certain programs (really needs them) and has many advantages. Not to be confused with DUAL BOOTING.

I am going to post my experiences in more depth here on the VIRTUALISATION  Discussion shortly under "Best Of Both Worlds" heading and hope to get a good flow there for **normal business-type users -** not too technical and full of COMMAND LINE scary stuff.

Please, if you are a serious user, do join in to the thread - who knows we may finish up with a very useful Group.

Cheers!

---

### Post by himagain on 2008-05-15
OKAY....
For openers, I am still a bit confused as to getting data from my VBOX  XP to my host Kubuntu and back safely. Does simply shutting XP in VBox down somehow stop backdoors and viruses? 
(Assuming I don't then open an exe or something later)

I have found it difficult to understand the process of making data available from one to the other, but am going to install and run my nominated  Windoze programs inside VBox on  Kubuntu 8.04 

As soon as I get one BIG problem fixed:  I have no sound at all in Kubuntu or the XP Vbox.  ( Strangely, I have Video).

I will keep up a running report here of my results and comments on aspects that confused this old non-too-tech USER.  :-)

 Note: Am going to install NVU Webmaker program - it is very good, free and... cross-platform

Cheers!

---

### Post by jrusso2 on 2008-05-15
I am wondering what is special about Eudora Pro that other email programs cannot do?  Even Qualcomm has stopped development on it and give the source code to Thunderbird developers who don't seem to be very excited about it

---

### Post by himagain on 2008-05-16
> **jrusso2 said:**
> I am wondering what is special about Eudora Pro that other email programs cannot do? 

Hi there,
There is a whole pile of messages on the Penelope BBS about this very point. There are soooo many things that none of the others can do - or can't do as well.  It is a mystery why somebody didn't buy the whole thing and do something serious with it.  *I'd* pay for it again! 

My own specifics are its crashproofness for one (think Windoze!) and the ease with which a small biz can control the most difficult part of a small internet biz:
big numbers of emails. 
E.G.'s:
1. Can act as a magic multiple-autoresponder in conjunction with very easy filtering.
2. Pull down messages under numerous accounts very easily, or just specific accounts as desired.
3. Many of the serious small biz users did/do use EudoraPro and have *tons* of historical (and specially filtered) messages that  other progs can't handle.
 3.  It's been around so long and we know its quirks! :-)

I've been going bats trying out all the Linux options and so far think Evolution is most under-rated of all. 

NOW it's easy!
Get  VBox, put Windoze inside a "cage" and run the critical/needed  Windoze  programs  there and  Kubuntu for everything else.  
Easy???? Well, that's the adventure I will share here with other pioneers bravely going lux/Box!

---

### Post by TerryNewton on 2008-05-17
> **himagain said:**
> OKAY....
For openers, I am still a bit confused as to getting data from my VBOX  XP to my host Kubuntu and back safely.


I noticed this "problem" elsewhere, I had no luck getting XP Home to share files using normal sharing methods - I think this takes XP Pro but might also be related to the artificial 5 device limit, which includes the hard disk, floppy and all usb devices.

But I found an effective workaround - FTP. Install an ftp server such as proftp, read the docs and edit the config file(s) to serve a single directory (and anything else in it) ONLY to the local machine (mine is set to prompt for my user name and PW), set up networking Eth0 to use a fixed address, then in Windows use an FTP client to connect to the Eth0 address.

I have a directory in Ubuntu set to the FTP server, and a directory in VirtualBox|Windows XP Home which a graphical FTP client is set to, so I drag what I want to transfer to these directories. Works great, no file-sharing needed.

Terry

---

### Post by himagain on 2008-06-14
> **TerryNewton said:**
> I noticed this "problem" elsewhere, I had no luck getting XP Home to share files using normal sharing methods - I think this takes XP Pro but might also be related to the artificial 5 device limit, which includes the hard disk, floppy and all usb devices.

But I found an effective workaround - FTP. Install an ftp server such as proftp, read the docs and edit the config file(s) to serve a single directory (and anything else in it) ONLY to the local machine (mine is set to prompt for my user name and PW), set up networking Eth0 to use a fixed address, then in Windows use an FTP client to connect to the Eth0 address.

I have a directory in Ubuntu set to the FTP server, and a directory in VirtualBox|Windows XP Home which a graphical FTP client is set to, so I drag what I want to transfer to these directories. Works great, no file-sharing needed.

Terry

Hi Terry,
Hope you are still looking in this  topic - been several weeks since I was here due to a Windoze problem.

Will try and follow what you did above -  bit of study there for me as an old def-no-tech type :-)

In the meanwhile a report update:
Tried to install a current XPPRO  to my main Drive (was just Kubuntu + Vbox XP's ) to try and resolve the no audio problem.  
  
The XP install trashed my whole system AND went on as a demo 30 day thing. 

M$ Support was not only no help - and wanted to charge me AFTER admitting they had no idea what to do. 
Apparently their weird licensing/security setup doesn't live well even in a multi-boot setup much less a Vbox. :confused:
I deleted it but no go. 
No Kubuntu!:(

Just today I obtained and tried out a fixit disk Grubfix and it did get Kubuntu back. :)
So your fix above can be most valuable for me at moment - TONS of vital stuff stuck inside the Vbox.

In amongst several messages I've received is the info that my ASUS Motherboard must have specific audio drivers for Linux installed. 
Apparently any drivers must be installed in the parent system (Kubuntu) and not in the VBox itself. ????
 
Not sure how to do that yet either.     

The saga continues........

---

### Post by himagain on 2008-08-10
NOW it's easy!
Get  VBox, put Windoze inside a "cage" and run the critical/needed  Windoze  programs  there and  Kubuntu for everything else.  
Easy???? Well, that's the adventure I will share here with other pioneers bravely going lux/Box![/quote]

If anyone is still looking here, I'm moving to a new thread title: 
VBOX+K8+XP = Sound Problem.

UPDATE: 
I just get more and more impressed with the evolution of Linux and the growth of Ubuntu is amazing - except that nobody seems to be seriously using it. I'm on the Net constantly - WORKING FOR A LIVING - and on the Servers that we use, almost no traffic ever comes from anything except M$'s I.E..  (We track browsers and pretty constantly Firefox will be around 4%, the rest insignificant.) 

It is very apparent that most of the time (75% + ) OU's (Ordinary Users) and BU's (Business Users) who try Lux versions will give up due to install related incompatibility problems. 
HOWEVER: 
 Our recent survey of 6,000 members  showed an amazing result: Most people did try "technicians" to fix the problems.  Most failed. Same 75%!:shock:

Almost no knowledge of VMachines  was evidenced in both D.I.Y and paid support! :confused:
This of course, is probably the reason for so much negativity about Lux - aside from the M$ generated stuff! :)
The lack of knowledge in the PC Industry means Lux/VM is *automatically* knocked!  
It is apparent that the best boost Lux ever got was from Vista! :-)
(Apple also zoomed up in sales - same reason AND the buyers didn't realise it was now a Lux machine!)
 
  -----------------------------------
Just threw this in for those who may come here late!

---

