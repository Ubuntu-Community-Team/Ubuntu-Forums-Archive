---
title: "Network type advice"
date: 2014-08-06
forum: Virtualisation
---

### Post by John_Newson on 2014-08-06
Hi,

I am quite new to Ubuntu and have been left with a major problem.  I do work for a non profit organisation and the guy that set it all up has died so I can't ask him any more unfortunately.  

Basically the system has been set up with VM Ware. The problem is one of ongoing cost and support.  The best way to describe what we do is that we are an online library.  We get paper information (text and images), scan and ocr it then upload it to a database with a web front end to allow public access.  We also record voice information which is transcribed; also we record movies. This means we have a server storing files from collections that are categorised and loaded onto the web server. We have an external server that we back up to across a 100/50 fibre network. Both servers are backed up by an onsite NAS.

The predicament we have is paying for licences to run the VM Ware products and I am trying to get my head around why we need to be so sophisticated.  Would just running a "simple" Ubuntu server and a web server suit our needs?

We have had advice from a company that is used to working in the windows environment and is pushing for us to go that way.

What do you think and why?

Cheers,
John

---

### Post by tgalati4 on 2014-08-06
Yes, you should ask such questions.  A simple Ubuntu server would perform your Use Case quite nicely.  Set up the Ubuntu server along side your existing VM setup and perform the migration over time.  You might get an improvement in speed as well.  When your Ubuntu system is up and running, set a time table for shutdown of the VMWare service (perhaps a year from now) to give people time to adjust--including the Software Salesman.

---

### Post by TheFu on 2014-08-06
Well, the answer depends on which VMware product you have and what each of the VMs is running.
VMware makes 6 different virtualization products. Which, exactly, do you have?

I prefer to use virtualization over running on physical systems for many, many, reasons - mainly flexibility.  However, if there isn't going to ever be any other workload on a physical machine, then there isn't  as many reasons to virtualize - there are still reasons, but not as many.

---

### Post by JKyleOKC on 2014-08-06
Like TheFu, I'm quite happy with running things in virtual machines. Given that the host system has adequate RAM -- at least 3 and preferably more GB -- and plenty of hard drive space -- 500 GB minimum -- performance is adequately fast for all my needs, and the ability to take snapshots and restore them later provides a near-instant backup mechanism.

However after starting out with VMWare Server some six years ago, I rather quickly changed over to use VirtualBox as my virtualization program. It was able to use the virtual disk drives I had created in VMWare, was much easier to maintain, and best of all its license permits full use, even in a business setting, at no charge. I did have to create new virtual machines, but that was quite easy to do. I simply printed listings of all the characteristics for each VM, from VMWare, and used those to specify the same values to the VirtualBox new-VM wizard.

When my wife acquired a new system with Windows 8 factory-installed and using USB 3.0 for its front-panel ports, I discovered that VBox was unable to recognize the USB 3 ports, and had to go back to using VMWare on it in order to keep her beloved Win XP games available. However if you have no USB 3 ports about which to be concerned, I'd still recommend switching over. I would do so on a test box; it's never a good idea to make changes to any production system until you've found all the little "gotchas" that inescapably accompany any conversion effort. Just clone the VMWare virtual drives (the *.VMDK files) onto the test box after installing VBox there, and assign them to the newly created VMs. You should find that they operate exactly as before -- and the question of expense will vanish.

VBox is in the Ubuntu repositories, but it's best to download it direct from the Oracle site at [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads) since the versions in the repositories are almost always out of date...

---

### Post by TheFu on 2014-08-06
VirtualBox **should not** be used on servers.  
Just for desktop-on-desktop needs and only if you can live with the Oracle license.  Check the guest addition license CAREFULLY. Most businesses need to pay for licenses to be legal.

---

### Post by JKyleOKC on 2014-08-06
Thanks for the heads-up! Since my business use is in a one-man shop, I'm still legal under the "personal" definition. Older versions of the license did say explicitly that personal use was still permitted even in an enterprise environment, so long as only the person who installed the software was using it! This was still the case even after Oracle became involved, and it was discussed at some length on the VBox forums.

(EDIT) It's still the case; here's what their licensing FAQ says: "Personal use is when you install the product on one or more PCs yourself and you make use of it (or even your friend, sister and grandmother). It doesn't matter whether you just use it for fun or run your multi-million euro business with it. Also, if you install it on your work PC at some large company, this is still personal use." (END EDIT)

It would still be worthwhile, I believe, for the OP to investigate the costs of using VBox in comparison to that of using the existing VMWare Server. I'm on the board of one 501(c)3 non-profit, and a few years ago we were investigating the cost for upgrading our Microsoft Office installations. We came across one organization that specialized in being a go-between and arranging low-cost or sometimes no-cost licensing for recognized non-profit groups! I've forgotten the details now, but a Google search should bring up a hit or two, and that might solve the OP's problem...

---

### Post by TheFu on 2014-08-06
Until the OP posts which VMware product used, it isn't worth guessing.

VMware Server was EOL - about 5 yrs ago. Nobody should be using that anymore - definitely NOT on a network.

---

### Post by John_Newson on 2014-08-07
Hi all,

Thank you very much for your replies.  
The current software we are running is VMWare ESXi 5.0. The server has 32gb RAM and a 6 TB RAID Array. There is another physical external server with 8Gb Ram and a 6TB Array that we back up to off site. 
We have had a proposal to go to VM Explorer and VMWare essentials. 

Of course the problem is financial - it would be nice to not have to fund licences being a non profit organisation and having to apply for funding to keep things going.  

My background up until February this year has been in Windows consumer products and support so the learning curve has been extreme to say the least.  I am managing the day to day running and have made several improvements to the workstations on site (more ram, going from 32 to 64bit and getting video cards in as  many computers as possible).  

Thanks again guys, look forward to your suggestions.

---

### Post by TheFu on 2014-08-07
How many and what OSes are being run under ESXi?

I'd dump ESXi and switch to KVM.  Actually, I did that a few years ago here.

Video cards don't usually matter too much for Linux. I use a video card until it fails or until it won't fit into the slot on a new motherboard. Of course, for a server no video card is even needed, though they are convenient during install.

---

### Post by John_Newson on 2014-08-07
We have three VM's with Ubuntu, Windows Server 8 and Windows 7 Professional.  

I thought that the video cards may help with the size of the graphics we are scanning - up to 1200 dpi. The increase in ram on the workstations obviously helped a lot.

Hey thanks for your time - I am a little bit like a fish out of water and the local guys are really pushing for the status quo.  I live in New Zealand and there are only around 160,000 people in two towns here in Hawke's Bay so a bit isolated.  Nearest real help is about 320 miles away in our capital city Wellington.

---

### Post by TheFu on 2014-08-07
> **John_Newson said:**
> We have three VM's with Ubuntu, Windows Server 8 and Windows 7 Professional.  

I thought that the video cards may help with the size of the graphics we are scanning - up to 1200 dpi. The increase in ram on the workstations obviously helped a lot.

Hey thanks for your time - I am a little bit like a fish out of water and the local guys are really pushing for the status quo.  I live in New Zealand and there are only around 160,000 people in two towns here in Hawke's Bay so a bit isolated.  Nearest real help is about 320 miles away in our capital city Wellington.

Without knowing the specific workload, it seems like your server is heavy on RAM for just 3 VMs.  

I doubt the video cards matter at all for scanning - though they may help with viewing and graphics processing tools. Those were workstations?  The servers won't care at all. It isn't like anyone sits behind them.  Hope I'm not confusing the server and workstation comments.

With Linux, remote help is just a secure ssh connection away.

---

### Post by John_Newson on 2014-08-11
Yep it is the workstations with the video cards.  I forgot to mention that we have a LTSP server running with a couple of thin clients and that is why the ram is so high.  The original idea was to go with thin clients due to cost but we have had a number of older computers donated from local firms for free so was a cheaper way to go.

Thanks for all your help, at this stage I will be pushing for KVM.  I just have a Manager and a board of Trustees to convince (probably won't be hard though lol).

Cheers,
John

---

### Post by TheFu on 2014-08-13
Please close the thread, if answered.

---

