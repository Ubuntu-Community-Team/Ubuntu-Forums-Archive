---
title: "Some Basic Server Questions"
date: 2008-12-08
forum: Server Platforms
---

### Post by zenarcher on 2008-12-08
I'm a complete dummy from the aspect of servers, but relatively familiar with Linux on the desktop.  I'm trying to help a friend, who wants to switch his small insurance company (server and about 6 desktop systems) to Linux.  I have switched him from Windows XP to Ubuntu on his home computer and he loves it enough to want to make the move in his business.  Unfortunately, I can't answer basic questions.  I hope this is the appropriate place to ask.

The current setup consists of a very old server running Windows ME.  It probably is going to die in the near future.  There are about 6 desktop systems in the office running Windows XP.  He has a couple of Windows only special insurance company programs (won't work under WINE) installed on the server and accessed by the desktops.  The key is that his employees are so fed up with Windows problems, they are open to using and learning Linux.

I am beginning a process now with him, to convert his office desktop systems, initially, to dual boot with Windows XP and Ubuntu or Kubuntu.  Since 98% of their work can be managed with Firefox, OpenOffice and Evolution email, they will primarily be using Linux on the desktops.  I can pretty well support him in this area.

Servers are totally out of my league.  Here is what we need to know:

Would there be a reasonably easy and appropriate way to replace his antique Windows ME server (they only have one), with a new server running Ubuntu or Kubuntu?  This server would have to handle his two Windows only programs (they are basically Windows-only based programs updating insurance information) and serve his Linux desktop computers.  The Linux desktop systems must be able to access the server and see the information from those two Windows only applications.  The server is connected to an AT&T DSL connection, which should not be a problem.

I hope I've asked this question clearly enough, but if more information is needed, I will be happy to clarify or explain further.

My friend's business is located in the Upper Peninsula of Michigan and I'm in Oklahoma, so I'm not a physical presence to assist him with this matter.  If anyone knows someone able to set up a new server for him in the Michigan Upper Peninsula area, I'd like to know that, as well, since he would be very interested in talking to you about doing so.

Thanks for any assistance,
zenarcher

---

### Post by gtdaqua on 2008-12-08
> 
He has a couple of Windows only special insurance company programs (won't work under WINE) installed on the server and accessed by the desktops. 

.....

Would there be a reasonably easy and appropriate way to replace his antique Windows ME server (they only have one), with a new server running Ubuntu or Kubuntu?

If you say that the Windows-only programs  won't work on Wine, then I can't see a way to switch the server to Linux. 

How is this program accessed by the clients?

---

### Post by zenarcher on 2008-12-08
From what he tells me, the Windows programs are actually on the server and the updates come from there.  From the Windows desktops, they are able to click on an icon located on the "P" drive (which is the server), allowing them to see the information.  Apparently, there is no actual software on the desktop systems for those programs.

Hope this helps.

Cheers,
zenarcher

---

### Post by theDaveTheRave on 2008-12-08
Zenarcher.

I can definately say that setup of Samba on any of the Ubuntu desktops is painless and very easy.

Chack out this thread by Stormbringer  [here]("http://ubuntuforums.org/showthread.php?t=202605")

One thing to watch out for, if you are intending to use static IP ensure that all the terminals have the same network mask, Ubuntu seems to do some strange things if the netmasks aren't all the same!

You may want to use one of the desktops as a "server" initially, for proof of concept, etc. You could then conceivable keep hold of the Windows ME server with the systems that are windows only residing on that - not sure how well it will work though.

I'm not entirely sure if it would work, or how to do it. But if each terminal has to have access to a windows system virtualisation would seem the way to go, Have you though about having this work through a "thin client" type system - not sure how to set this up, but it may be interesting for the windows dedicated stuff.

This program that is being used, maybe the producers have a "web based" version, that would make life really easy as you then just turn the server into a web server also.

good luck with the project, and why not write down what you do and then post it too the forums as a "howto" I know that there are lots out there on everything, but there often seems to be a multitude of methods for doing the same stuff, and no-one has the exact same setup of Hardware etc..

David

---

### Post by zenarcher on 2008-12-08
Thanks much for that info on Samba.  As I say, attempting to set up a server is going to be way out of my league, so I'm going to have to try to track down someone in his area with the expertise to physically go into his office and set it up for him.  I'm trying to get an idea as to whether this can be done/or will work, before I proceed.  That way, hopefully, I can ask some intelligent questions.  All the input is great, as it helps me with that.

The company which makes the Windows only software he uses is quite cooperative.  They sent me a copy of the program to try with WINE.  It almost installs under WINE, but I get one error, toward the end of the install, which prevents it from installing.  The error is: "Could not locate entry for HAL.dll in setup log to determine type of HAL to update."  I can't seem to get around that.  I thought I had it made, as it appeared to be installing properly, right to the end.  The company said no one had asked about running their software with Linux until we asked.  Their tech guy happens to be a Linux fan, so he was interested, as well.

If I can determine there is a way to manage what we want to do, I can most likely find someone located near his location in Michigan he can contract to do the setup and installation.  That's another task I haven't explored yet, until I know whether what he wants is feasible.  Their current Windows desktops have been a nightmare of viruses, spyware, reinstalls, etc.  The typical, so they are ready to go to Linux, if we can manage.

Cheers,
zenarcher

---

### Post by gtdaqua on 2008-12-08
Take a look at this post: (little long, but could help)

[http://forum.winehq.org/viewtopic.php?p=16176&sid=8562993d722082d87f567297d818dec8]("http://forum.winehq.org/viewtopic.php?p=16176&sid=8562993d722082d87f567297d818dec8").

From your last post, migrating the clients to linux and having them access the "P:\" is going to be easy. I can walk you through that.

---

### Post by happyhacker on 2008-12-08
Hmm, interested in your problem as I am trying to setup a Ubuntu server for file sharing in a small office. Why not consider as a phase of your changes just getting a 2nd hand PC (800Mhz and above) and setting this up as a server and interworking with the old server (which sounds as though it will need to be replaced soon anyway). That way they can continue to work as normal untill you have phased out the software (and other functions) on the old server with new versions on the new server. That way you will become expert on managing the network - best way to learn I say! I am intending to get a VPN link so I can access the Ubuntu server remotely - that's my next stage.

---

### Post by zenarcher on 2008-12-08
gtdaqua, thank you very much for the offer of assistance.  I sincerely appreciate that and will call on you, as soon as we start getting things moved in this direction.

Right now, my friend is ordering one new desktop computer from Dell, which he is having shipped directly to me, as he wants me to do the dual boot install (Win XP and Ubuntu) for him, then ship it on to him.  We will then have one system set up in his office and I will ask for your assistance getting access to the "P" drive.  He is just starting to learn Linux.  I walked him through, by telephone, two Ubuntu installs on his computers at home and he's loving it.  That was a real motivation for his wanting to switch at work.  Likewise, I can usually answer most of his questions regarding the desktops.  I suppose I'm going to be his "Linux Support," as I'm retired and home all the time.  Keeps me thinking, which is good and helps him out, too.

That was my post in the WINE forum, so I am watching that and I think the WINE Wiki they sent me may be of help.  I'm reading through that now.  

cantthinkofanickname, I would say that second server is a pretty good idea.  He has several old computers around, I know.  He just replaced one of his home computers with a new one.  Likewise, I built him a custom system a couple of years ago, he is not using now and is sending back to me to do a Linux setup on it.  It has an AMD XP2000 or better processor...I can't actually remember at the moment.  Way better than the old 266MHz CPU in his current server.  I know it's very old and Windows ME certainly isn't the showpiece of server software.:)  There should be no problem setting up one of those for a second server during a transition.  I'll continue to post as we work on this problem and you might find something in the process to help your situation.

Cheers,
zenarcher

---

### Post by theDaveTheRave on 2008-12-09
ZenArcher

Have you thought about virtualising windows through QEMU or another similar?

That way each desktop could have an virtual windows system. Thinking about it, I see no reason why the virtual windows system couldn't sit on your server and behave like a "thin client". I they are using it for just this one peice of software you could probably get the system well trimmed to that one thing only?

As the tech guys at the production company seem helpfull maybee they would be willing to help experiment with the setup in this clients office? It would be good for them, good for your friend ("a partner of such and such company").

The DLL problem sounds like it should be an easy one to solve.... (:lolflag:).

I've got a similar issue with a peice of Mac software, but then my team are all running Windows or Mac systems (it's only me on Ubuntu, and the server).

David

good luck with it.

---

### Post by zenarcher on 2008-12-09
theDavetheRave.....I think I'm now thinking somewhere along the same line you have mentioned here.  I don't know if this could resolve the problem or not, but it's my thought (and question) at the moment.  It wouldn't be a "perfect" solution, but a viable solution, nonetheless.  I wish I understood more about all this, but I'm pretty much just a simple Linux desktop user, not a pro on the server/virtualization/etc. game.  I don't even run any Windows stuff here.  I'm retired and playing with these computers is a bit of a hobby.  Between my wife and I, we run 6 computers in the house, all with Linux. :)

I've been doing more reading and researching and I'm wondering about this:

As best I understand at the moment, the "Windows only" applications my friend is using are installed and run only on his Windows server.  From their desktops, they merely access the "P" drive (which is the server) and run the programs from there and can read the information.  I wonder if this is feasible and maybe one of you could tell me.

Since he's going to need a new server before long, I wonder if we could install Ubuntu Server on the new server.  Then, install and use something like "VirtualBox" on the server and install one of his legitimate copies of Windows XP to run with VirtualBox.  In doing so, I would guess we could install and run the "Windows Only" programs in Windows there.

As I say, I don't really understand anything about it, but it would seem to me that the desktop systems would then only need an Ubuntu install on them.  They should be able to access the server and the VirtualBox in the server, where they could run and use the "Windows Only" applications and see that on the Linux desktops.  

I hope I've explained that clearly enough.  Since his Windows stuff will not run under Wine or Codeweaver (I tried that, as well), it seems this might work.  I also hope I can work with their people to possibly come up with a Linux application in the future, as well.

It seems the insurance business is just plain, "Linux unfriendly."  He has two or three policy websites which can only be accessed with Internet Explorer, as well.  I have managed to get around that problem by using IE in Codeweaver.  So, that's not going to be an issue.

Anyway, any input on what I'm thinking now would be appreciated, if someone has some experience with doing this.

Cheers,
zenarcher

---

### Post by hyper_ch on 2008-12-09
with samba you can easily share files with windows networked computers (someone here told me that after I switched their server to debian that samba now is a lot faster... well, I can't verify that but that's the feedback).

However running a program from the server and on the server is somethign else altogether. Are you sure that program is not installed on the clients and just the "data" directory for those clients is on the server?

---

### Post by zenarcher on 2008-12-09
Thanks for that info on Samba.  I've read a little bit about it, but haven't had any experience, at all with it.

I had that same question about the Windows program running on the server as you are asking.  It really confused me, as well.  I've asked him several times, trying to get it clear in my mind, as well.

The tech guy at the company which has the software has been quite cooperative, in any way he can be, so I may have to talk to him about it.  In fact, he sent me a copy of the software, so I could see if I could get it to run with Wine or any other emulator.  No luck, as I get a HAL.DLL problem, trying to install with either Wine or Codeweaver.

According to my friend, they have nothing installed on the clients in respect to the program.  He says it resides strictly on their server....that they access their "P" drive (which is the server) and run it there.  It is some sort of "updater" for insurance information and he runs it about once a week, just for update information.  I'm still a bit confused about it, myself, but that's how I understand it at the moment.  As I say, I have a copy of it and it's not all that big.  It's a DOS/Windows executable at 79M in size.  It runs through most of the install in Wine, then errors out at the end with "Setup has detected that the Service Pack version of the system installed is newer than the update you are applying to it.  You can only install this update on a computer with no Service Packs installed."  That's what I got after downloading HAL.DLL and copying it to \windows\system32\ in Wine.

Cheers,
zenarcher

---

### Post by hyper_ch on 2008-12-09
then it might just run. Possible it's a standalone application that can be run from a network share. If that's the case then you don't need a windows server... you just need samba to provide a "windows network share". By "running" it it will the copy itself into the clients memory and run there.

Well, it's just a guess of mine.

---

### Post by zenarcher on 2008-12-10
hyper_ch, I think you may be correct in your guess.  I'm thinking the same thing.

Actually, I am making a bit of progress with the companies my friend has to use in his business.  A couple of websites he must access for policy processing are "IE Only," websites.  After contacting them, they agreed that IE is not the only browser (nor the most secure, considering personal client information is entered there) in use today and are exploring an upgrade to their websites, so they will compatible with Firefox.  At least they are open to change.

In respect to this updater application I've been fighting with, their tech people have advised me that they are the actual developers and writers of their software.  It is not something they have had created by another party.  So, I am now talking to them about the possibility of somehow creating a Linux version of their application. We will see what is involved in that attempt.

Thanks again,
zenarcher

---

### Post by hyper_ch on 2008-12-10
good luck :)

---

### Post by zenarcher on 2008-12-11
After talking to the software company, creators of the software giving me the problems with Linux, there appears to be hope.  It seems they realize this isn't a total "Windows world."  They have assured me they are working on the concept of making their application web based and non O/S reliant and hope to have something available within the first quarter of 2009.  This would solve the problem!

Cheers,
zenarcher

---

