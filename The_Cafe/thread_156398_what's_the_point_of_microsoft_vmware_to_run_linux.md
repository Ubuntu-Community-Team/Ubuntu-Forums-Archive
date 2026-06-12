---
title: "what's the point of microsoft vmware to run linux?"
date: 2006-04-06
forum: The Cafe
---

### Post by Jawbreaker4Fs on 2006-04-06
I don't intend to tell you how to run your system, but why not just dual boot? I never understood the point of running a VM in windows to run Linux when you could just dual boot. Sure, you might want to use an application for Linux in windows or vice versa.... but tools such as cygwin and wine should make this irrelevant, shouldn't they?

---

### Post by Kindred on 2006-04-07
I have XP in a VM because I think it's a cleaner solution, and is fairly temporary anyway.  

I don't have to have XP installed, nor require a reboot to use it. 

I imagine this works the other way around..

---

### Post by paul cooke on 2006-04-07
[QUOTE=Kindred]I have XP in a VM because I think it's a cleaner solution, and is fairly temporary anyway.  

I don't have to have XP installed, nor require a reboot to use it. 

I imagine this works the other way around..[/QUOTE]

correct, at work I have to use XP, but I'm able to run Kubuntu using VMware Player. I'd never be allowed to install Kubuntu, plus I can simply minimise Linux and be using our windows apps immediately... 

It works the other way at home, I'm stuck having to run windows for some software that's part of my distance learning course and duel booting is simply not on. I hate duel booting as it destroys uptime and wastes time changing environments... at home I've got XP currently snapshotted and ready to resume in less than 5 seconds so I can easily switch to do some more coursework and then simply minimise it to do some browsing etc.

ps and thread starter... It's NOT microsoft vmware. VMware is an entirely different company... please do NOT conflate the two. It's like calling a Dyson a hoover... and another thing, VMware runs on Linux and ms-windows equally well, Microsoft's product, surprise, surprise, ONLY runs on ms-windows so it's useless to me as a virtual machine I create on this Linux box using VMware workstation runs fine at work on my XP box... and vice versa

I'd love to switch to using QEMU properly, but QEMU, to put it politely, is a real pain to get working properly.

---

### Post by prizrak on 2006-04-07
There is probably very little point to a home user but to an organization the advantage is clear. You can have one machine run more than one OS and use the strengths of both at the same time.
For instance you might have an Active Directory or application server run on Windows and your web and DB server run on Linux w/o having to get two different physical machines. Of course whichever one is running emulated will be quite a bit slower but if you have a small company with modest speed requirenments it could be a pretty big savings. 
You also can test another OS w/o having to get another machine or taking one offline, in case you say want to switch to RHEL from Server 2003.

---

### Post by AndyCooll on 2006-04-07
I disagree that there is very little point even for a home user, for some purposes running XP under VMWare Player is actually more convenient than having a dual-boot system.

I have an XP VMWare image for two reasons. For one website that doesn't render properly in Firefox, and to play Football Manager 2006. Most of us multitask and since I'm 99% Linux just about all my apps that I use are Linux ones. Having to reboot in to XP would be inconvenient since while in XP I wouldn't have immmediate access to all my other apps. 

So having XP as an image means I can play FM **and** still run all my other Linux apps at the same time. I don't have to reboot and it doesn't limit me.

:cool:

---

### Post by wishyjr on 2006-04-07
well, im still in a windows to linux transition and most the way there. At the moment i'm finding that vmware helps me i way i didnt at first realise. I thought "sod windows, linux can do anything windows can plus a bit more -i like the idea of this" but after dual booting for a few months, i kept finding myself returning to windows for trivial tasks that i seem to be perfectly capable to linux but i just didn't like it as much as my windows' version of whatever.
Now, using vmware, i'm re-creating my windows installation as a virtual machine running very easily ontop of linux. Dual booting is annoying for me and an inconvienience. now i can run those things i use to in windows while at the same time use/learn/get use to linux. Completlely seemlessly. 

..and at the end of the day, it feels to me like linux is in charge of my system -thats nice to know. :)

---

### Post by Marshall2day on 2006-04-07
I can't wait for the new generation processors that support virtualisation. No need to run one OS on top of another. They can just run side by side.

---

### Post by drummer on 2006-04-07
Well, at uni we have comps running Fedora in all the computer labs which have the option of logging in to a windows 2000 session in gdm, which logs in using gdm and loads win2k with vmware. I imagine they do this for specific software needed by some subjects, and i see many people using it in my classes probably because it's what they're used to. Running both OSs dual boot wouldn't be a viable option here because it would make it hard for some to get to windows having to choose it in a boot loader.

Even though I'm doing an IT course, IT isn't a prerequisite, so there are many people who have only experienced windows and don't have the faintest idea about linux, booting, hardware, etc. just know how to use windows. Booting windows in this way (VMWare) is the best approach in this case IMO.

It would also be easier to manage. Think about administering literally *hundreds* of computers... then double that work because of the 2 OSs on each in dual boot ;)  When VMWare loads, I think it's loaded from a disk image on the main server and a connection to the user's /home directory is made and mounted as a drive. I think this because there's a remote 'images' volume mounted on the machines, which I assume is for this purpose. So only one image to administer.

---

