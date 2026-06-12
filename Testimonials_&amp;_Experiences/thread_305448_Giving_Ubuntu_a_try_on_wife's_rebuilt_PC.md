---
title: "Giving Ubuntu a try on wife's rebuilt PC"
date: 2006-11-23
forum: Testimonials &amp; Experiences
---

### Post by StanMeis on 2006-11-23
My two year old out of warranty Sony Vaio burnt out at the end of July.  The quote for reparing it was close to $700 US so I bought a new (different brand) computer and set the Sony aside until I had time to salvage the parts.  The motherboard had gone out but it was a P4 3gig with 512mb ram, 160gig hard drive, a 128mb video card as well as a tv tuner, CD/DVD burner and DVD drive.  My wife was using an old home built 486 running on Win98 and the AT case was obsolete so it had reached it's limits.  I had built my own computers up until a couple of years ago and knew what had to be done so I wasn't intimidated by the idea of tearing into the Sony.  

A new motherboard, case and power supply had it up and running in short order.  Anyone familiar with the Vaio cases knows that they're as close to an oven as one could get so I can see now that it probably overheated and that's what led to the board failing.

The motherboard must have been coded to match up with the Sony proprietory version of XP because I couldn't install XP.  Sony would not re-register because the repair was not performed by a factory authorized service center.  Without an OS I remembered that the IT guy at work had given me a CD of an OS called Ubuntu 5.1 to use if I had a problem reloading XP.  I loaded Ubuntu on the rebuild and it saw all the hardware right out of the box.  That's a good sign. 

The next step was to update to 6.06 which was a pretty lengthy download but it was worth the wait as everything went well.  So far in less that a week I have mastered how to do downloads both via the GUI and via Terminal commands.  I love this operating system but will admit that there's a learning curve.  I've got the PC's seeing each other on the network, sound and everything working on the rebuild.  There are a few tweaks that I'm researching and finding the information here on this forum.

Working with Ubuntu kind of reminds me of when I first got into home computing over a decade ago before the masses embraced home computing.  At that time it was common for hobbyists to have to deal with DOS commands and edit the registry.  It has gotten easier with Windows machines and most of the stuff they sell nowadays is configured to work out of the box.  If I hadn't built my own PC's and learned the Windows file structure as well as how to troubleshoot my own problems Ubuntu probably would have intimidated me too much to stick with it.  In other words, my opinion is that Ubuntu isn't to the point where Ma & PA are going to install it on their computer they got at Best Buy.  I'm comfortable learning the commands and sticking with Ubuntu on the wife's computer.  It's a solid OS and meets all her needs.

I'd like to do video editing on the rebuild seeing as it has a TV tuner and found that it's going to take some additional research.  I have identified the preferred program but haven't attempted to install it yet.  I'm currently working on getting some other applications going but the basic stuff, email, internet, word processing, all work out of the box.  I have been using the Windows version of Open Office for several years so there was no surprises in that area.

I do auto racing photography and have a website [www.gotomn.com]("http://www.gotomn.com") where I post photos.  I'm currently still using Windows XP on my main box but like Ubuntu and the open source community concept so I'd like to eventually migrate this PC to Ubuntu as well.  There are certain applications such as Noise Ninja, Paint Shop Pro 8, Photoshop 7 and several other Windows programs that I need.  I'm not certain if I can install the OEM version of Windows that came with this Compaq PC to work with VM and Ubuntu.  If my research provides satisfactory answers to those questions I will make the switch.

---

### Post by cilynx on 2006-11-24
[http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software](http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software)

I'm sure there are better resources, but I found that right off the bat...

---

### Post by StanMeis on 2006-11-24
> **cilynx said:**
> [http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software](http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software)

I'm sure there are better resources, but I found that right off the bat...

Thank you for the information.  Noise Ninja is a specialty application for photographers available in Win & Mac that I'm sure has no equivalent in Linux.  I'm certain that Gimp has the same capabilities as PSP and Photoshop, layers, masks, etc. but the time it would take to learn a new application and get back to square 1 (where I'm at now with familiar programs) will be the determining factor.

By way of example, I spent the better part of a weekend trying to do a simple little thing like changing my IP address in Ubuntu.  Come to find out Ubuntu was mirroring the IP from my router and I had to change it in there.  It never affected my interent connection in XP and I wouldn't have never found the answer to this problem if someone on my vanpool wasn't using Ubuntu.  Half the weekend spent trouble shooting something I would have known right where to go in XP.  It's not the complexity of Ubuntu but the learning curve and finding answers to those simple little routine tasks.  I like Ubuntu so far but don't know if I have the time to make a complete switch.

---

### Post by cilynx on 2006-11-25
Quite understandable.  I never recommend that people try to switch cold-turkey to Linux.  This is especially so when you rely on specialty applications.  It's a slow process.  What I generally tell people is to start using Linux for web surfing and office work.  Go ahead and boot Windows for your specialty applications.  

Also, for if the time comes that you're comfortable enough in Linux to do away with your Windows setup:

*July 12, 2006 -- New Noise Ninja release for Mac Intel, Mac PowerPC, Windows, and Linux*
[http://www.picturecode.com/news.htm#update_7_12_06](http://www.picturecode.com/news.htm#update_7_12_06)

---

### Post by StanMeis on 2006-11-25
I found an application called Wine that would allow me to run select windows programs in Ubuntu.  Paint Shop Pro 7 is listed on a website called Frank's Corner as running in Wine.  I presume that 8 would work too as it's not much different than 7.  Photoshop works so that's not a problem.  Noise Ninja is not listed but it's not a very complex program so it would probably work.  I like the concept of Wine better than Virtual Machine as I don't want to run two complete OS's, only a few programs.  If I was going to have to run dual boot with the complete XP OS I can't see a reason to do it.

The XP machine is an AMD64 and I understand that there are some issues using Ubuntu in that configuration that require additional tweaking.  Ubuntu works great on my wife's PC so I will do some testing on it when she's not using it and take it from there.

---

### Post by cilynx on 2006-11-25
In my experience, Wine is hit and miss.  It's a fantastic piece of kit when it works.  As for Ubuntu on amd64, I'm running it on my HP dv8135nr.  On amd64, Wine isn't really an option at all.  Flash also doesn't work well.  The binary drivers for video cards are hit and miss.  The open-source drivers work great.  All of this can be taken care of through 32-bit libraries and replacement applications, but that requires some wizardry and kinda dispells the point of running 64-bit in the first place.  Everything else works well.  As a final thought, the 32-bit version of Ubuntu will run on 64-bit machines just as well as it does on 32-bit machines.  You just don't get the advantages of 64-bit.  Just as a point of reference, just about every 64-bit PC on the market now ships with a 32-bit version of Windows.

---

