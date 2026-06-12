---
title: "Highmem / PAE Support"
date: 2008-10-09
forum: Ubuntu Brainstorm
---

### Post by mizzouxc on 2008-10-09
I recently read an archived e-mail here:

[https://lists.ubuntu.com/archives/kernel-bugs/2008-June/037755.html]("https://lists.ubuntu.com/archives/kernel-bugs/2008-June/037755.html")

It's contents kind of disturbed me a bit. Honestly, it's one of the primary reasons I don't use Ubuntu for personal use or at work. We, as the users, are being told to run a server kernel or use an x64 kernel to have decent memory support in newer machines. However, there are a number of reasons that x64 isn't really an option. 

The primary two (2) reasons are:
[LIST]
[*]No (stable) flash support (browser)
[*]No (stable) java support (browser)
[/LIST]

The author also discusses that PAE isn't supported by processors in the 586 class. I can't imagine that there are that many PC's with VIA, Pentium, or Pentium MMX era CPU's left. Additionally, given the (large) footprint of Ubuntu/Kubuntu, I couldn't imagine that it'd be a delightful experience on these machines. 

Aren't we to the point where we can start shipping an i686 kernel, i686 kernel with pae with Ubuntu/Kbuntu and leave the i386 kernel for the Xbuntu branch?

To give this a reality check, the i686 architecture was released in 1995; 13 years ago. The i586 architecture was released in 1993, 15 years ago.

Instead of developing for the few, I propose we develop and optimize the kernel for the many. Let's start at least supporting technology from 1995 in our x86 kernels in 2008. I understand the need for a broad audience, but this is turning out like the "no child left behind" legislation in the US. 

Better yet, give us the option. Include a highmem kernel in the package tree like many other distributions; including Ubuntu's parent distribution, Debian.



PS. Please don't tell me to recompile my kernel, I already do that and it doesn't solve the problem for everyone.

---

### Post by ilrudie on 2008-10-09
This only matters if you have more than 3 gigs of memory and refuse for some reason to run x64.  Also flash and java seem pretty stable in my experience on x64 Hardy so I'd say x64 is very much an option for anyone with a 64-bit processor.  
Your proposal to develop for the many is really just a proposal to develop for the few that includes you.  I'd venture to guess that the majority of 32-bit users don't have more than 3 gigs of memory so changing to i686 doesn't benefit them.

---

### Post by mizzouxc on 2008-10-09
> **ilrudie said:**
> This only matters if you have more than 3 gigs of memory and refuse for some reason to run x64.  Also flash and java seem pretty stable in my experience on x64 Hardy so I'd say x64 is very much an option for anyone with a 64-bit processor.  
Your proposal to develop for the many is really just a proposal to develop for the few that includes you.  I'd venture to guess that the majority of 32-bit users don't have more than 3 gigs of memory so changing to i686 doesn't benefit them.

Pretty stable and stable are two different things. x64 java plugins and flash are not stable enough. Additionally, I doubt there are more Pentium/Pentium MMX systems still around from 12-15 years ago than there are systems with >4GB ram. 

Regarding "additional development effort", it's minimal. Select a proper architecture, enable pae and select a max amount of memory; compile. As I previously stated, Debian can do it; why does Ubuntu alienate and hinder people with new machines with 4+ GB of ram? Heck, even the Pentium II is an i686 architecture chip. 

All I'm asking for is the _option_ to install a more optimized kernel for processors newer than 13 years old. Living 15+ years in the past could be part of the reason so many people growing up are stuck on Windows. 

And FYI, i686 processors have been developed for the last 13+ years starting with the Pentium Pro. Compiling a kernel on a restricted i386 instruction set can only hamper performance potential. In addition, I'm sure the i686 user base is MUCH MUCH larger than the i386 base now.

---

### Post by cdenley on 2008-10-09
> **mizzouxc said:**
> Pretty stable and stable are two different things. x64 java plugins and flash are not stable enough. Additionally, I doubt there are more Pentium/Pentium MMX systems still around from 12-15 years ago than there are systems with >4GB ram. 

Regarding "additional development effort", it's minimal. Select a proper architecture, enable pae and select a max amount of memory; compile. As I previously stated, Debian can do it; why does Ubuntu alienate and hinder people with new machines with 4+ GB of ram? Heck, even the Pentium II is an i686 architecture chip. 

All I'm asking for is the _option_ to install a more optimized kernel for processors newer than 13 years old. Living 15+ years in the past could be part of the reason so many people growing up are stuck on Windows. 

And FYI, i686 processors have been developed for the last 13+ years starting with the Pentium Pro. Compiling a kernel on a restricted i386 instruction set can only hamper performance potential. In addition, I'm sure the i686 user base is MUCH MUCH larger than the i386 base now.

I thought enabling PAE would decrease the performance for users running less than 4GB memory. I also thought that the x86 kernel used i686 optimizations if they were supported by the user's processor, which is why it is linux-generic, not linux-i386. I could be mistaken, though.

[https://lists.ubuntu.com/archives/ubuntu-devel/2006-August/019983.html](https://lists.ubuntu.com/archives/ubuntu-devel/2006-August/019983.html)
[http://ubuntuforums.org/showthread.php?t=123556](http://ubuntuforums.org/showthread.php?t=123556)

I do think there should be a highmem kernel in the repo's. Does the realtime kernel use PAE?

---

### Post by mizzouxc on 2008-10-09
Enabling PAE could decrease peformance, due to the overhead; swapping significantly decreases overall performance. 

The primary problem I have with the original link I posted, is that in an i686 based kernel, which shouldn't run properly on an i586 box; the developer has a problem giving users an option to enable PAE on a PAE capable platform. 

SuSE and RedHat both have a mechanism to detect available memory, PAE capability and install the appropriate kernel. I understand bandwidth and CD size limitations, thus, make the option available. I like debian's approach. Install a generic kernel and let the user apt-get the highmem/hugemem kernel if they need it. Most users won't care, but the high end users can have their memory support and you won't have to change a single thing about the release CD.

Instead of arguing why you shouldn't enable a technology due to philisophical reasons, or "just use x86_64", realize that there are legitimate users out there that can utilize this capability. Make technology available and people will use it.

Ubuntu makes strides to enable desktop effects, use the latest releases of gnome, but refuses to make kernel changes because someone with a Pentium MMX couldn't install Ubuntu. I say give the legacy support to Xubuntu and move forward with the kernel for Ubuntu. 

I view the current state of things like sticking a ferrari on a go-kart chassis with a 5hp lawnmower engine. Yeah, it looks pretty, but underneath the hood it's ugly.

---

### Post by cdenley on 2008-10-09
> **mizzouxc said:**
> Enabling PAE could decrease peformance, due to the overhead; swapping significantly decreases overall performance. 

The primary problem I have with the original link I posted, is that in an i686 based kernel, which shouldn't run properly on an i586 box; the developer has a problem giving users an option to enable PAE on a PAE capable platform. 

SuSE and RedHat both have a mechanism to detect available memory, PAE capability and install the appropriate kernel. I understand bandwidth and CD size limitations, thus, make the option available. I like debian's approach. Install a generic kernel and let the user apt-get the highmem/hugemem kernel if they need it. Most users won't care, but the high end users can have their memory support and you won't have to change a single thing about the release CD.

Instead of arguing why you shouldn't enable a technology due to philisophical reasons, or "just use x86_64", realize that there are legitimate users out there that can utilize this capability. Make technology available and people will use it.

Ubuntu makes strides to enable desktop effects, use the latest releases of gnome, but refuses to make kernel changes because someone with a Pentium MMX couldn't install Ubuntu. I say give the legacy support to Xubuntu and move forward with the kernel for Ubuntu. 

I view the current state of things like sticking a ferrari on a go-kart chassis with a 5hp lawnmower engine. Yeah, it looks pretty, but underneath the hood it's ugly.

I agree with you that there should be a highmem kernel available. However, I don't think it is as necessary as you make it seem. 4GB is much more memory than I would compare to a "5hp lawnmower engine". I don't think there are many legitimate reasons to have more than 4GB of memory on a desktop system. I have 2GB, and I think that's overkill. 1GB would be plenty. How many desktop users that need flash would actually need that much memory? However, the option should be available. Maybe maintaining an extra kernel would be more expensive than I realize, and wouldn't be worth it.

---

### Post by mizzouxc on 2008-10-09
Not everyone is a consumer level desktop user. Some of us use our 4-8 core boxes for simulation and design. Unfortunately, our/my code base is entirely 32 bit. 

In addition to my simulation and design, I also have to do my timecard which uses a corporate Java App that will NOT run using 64 bit java. Flash...well it's just convenient. You can't even visit sites like nvidia.com without it anymore. 

I'm sure that I'm not the only user out there that prefers to run 1 OS and have 1 PC to do it all. Until x64 support matures, some of us are stuck with x86 architecture. 

I really like Ubuntu, but I've had to move to Debian because they support my needs. 

If the Ubuntu community is this close-minded, I guess you've helped make my decision. Cheers.

---

### Post by cdenley on 2008-10-09
> **mizzouxc said:**
> Not everyone is a consumer level desktop user. Some of us use our 4-8 core boxes for simulation and design. Unfortunately, our/my code base is entirely 32 bit. 

In addition to my simulation and design, I also have to do my timecard which uses a corporate Java App that will NOT run using 64 bit java. Flash...well it's just convenient. You can't even visit sites like nvidia.com without it anymore. 

I'm sure that I'm not the only user out there that prefers to run 1 OS and have 1 PC to do it all. Until x64 support matures, some of us are stuck with x86 architecture. 

I really like Ubuntu, but I've had to move to Debian because they support my needs. 

If the Ubuntu community is this close-minded, I guess you've helped make my decision. Cheers.

I know there are some instances where more than 4GB of ram are needed, I'm just saying its rare. I hope when you call the Ubuntu community "closed-minded", you weren't responding to my post. My comments don't reflect the opinion of the whole community, and I did agree with you. Unfortunately, people seem to have used all the channels available to request it, and the developers don't seem to want to build a highmem kernel. I would be interested to know their reason, because I assume there is one. Luckily, it sounds like Debian meets your needs.

I think x64 support is fully mature as far as open-source software goes, by the way.

---

### Post by ilrudie on 2008-10-09
> **mizzouxc said:**
> Not everyone is a consumer level desktop user. Some of us use our 4-8 core boxes for simulation and design. Unfortunately, our/my code base is entirely 32 bit. 

In addition to my simulation and design, I also have to do my timecard which uses a corporate Java App that will NOT run using 64 bit java. Flash...well it's just convenient. You can't even visit sites like nvidia.com without it anymore. 

I'm sure that I'm not the only user out there that prefers to run 1 OS and have 1 PC to do it all. Until x64 support matures, some of us are stuck with x86 architecture. 

I really like Ubuntu, but I've had to move to Debian because they support my needs. 

If the Ubuntu community is this close-minded, I guess you've helped make my decision. Cheers.

I feel your pain regarding corporate software.  My last job required IE6 to fill in your time card and had banned Firefox because the security team decided it wasn't secure!  This was 6 months ago.  IE6?  Firefox insecure? Really?  That said:  
You did not fully explain your situation in your first post.  Instead you gave your opinion that not including a highmem option is an unforgivable decision.  Others responded with their opinions.  It's unfortunate that you called an entire community of volunteers (the forums) "closed-minded" because you didn't like the opinions of a few users.  

The 3 options for highmem that Ubuntu provides (1. x86_64, 2. server kernel, 3. compile it yourself) don't meet your needs.  Luckily Linux gives you tons of choices so you can find the one that suits you.  Instead of blasting a distro for not having 1 feature that you want maybe it would be more productive to celebrate the diversity of Linux.  If all disto's shared your goal of providing high-end workstation OSes for people who require tons of memory and flash and 32-bit java then the Linux comunity as a whole would suffer.  Furthermore the goal of Ubuntu is not to eclipse all other Linux distros but rather to provide an easy to use distro for the average joe/jane consumer.  As you stated your needs are beyond that of the average user and Ubuntu isn't working out for you.  That does not mean that the developers of Ubuntu should be faulted or should be forced to spend valuable resources trying to meet the needs of a few users.  

Enjoy Linux in whatever form or forms ends up fitting your needs best.

---

### Post by mizzouxc on 2008-10-09
I meant the developers. Isn't Java fully open source now?

I do have a few compute nodes at work that have 64GB of ram, 16 cores, etc. There have been times that I've also gotten myself into swap when I mis-calculated a matrix size for a simulation. I think the whole Pentum MMX is about as rare now days as users who use lots of ram. :(

I was hoping to provide some rational feedback to the developers regarding the needs of users. It really irks me that something is available, but people blatently ignore and "won't fix" something that there's a lot of need for. 

I've read complete posts from developers (can't find one now grr) trying to lie the userbase into thinking PAE / Highmem / More than 3GB of ram isn't addressable in the 32 bit kernel. Oh well, *sad panda*

---

### Post by mizzouxc on 2008-10-09
> **ilrudie said:**
> I feel your pain regarding corporate software.  My last job required IE6 to fill in your time card and had banned Firefox because the security team decided it wasn't secure!  This was 6 months ago.  IE6?  Firefox insecure? Really?  That said:  
You did not fully explain your situation in your first post.  Instead you gave your opinion that not including a highmem option is an unforgivable decision.  Others responded with their opinions.  It's unfortunate that you called an entire community of volunteers (the forums) "closed-minded" because you didn't like the opinions of a few users.  

The 3 options for highmem that Ubuntu provides (1. x86_64, 2. server kernel, 3. compile it yourself) don't meet your needs.  Luckily Linux gives you tons of choices so you can find the one that suits you.  Instead of blasting a distro for not having 1 feature that you want maybe it would be more productive to celebrate the diversity of Linux.  If all disto's shared your goal of providing high-end workstation OSes for people who require tons of memory and flash and 32-bit java then the Linux comunity as a whole would suffer.  Furthermore the goal of Ubuntu is not to eclipse all other Linux distros but rather to provide an easy to use distro for the average joe/jane consumer.  As you stated your needs are beyond that of the average user and Ubuntu isn't working out for you.  That does not mean that the developers of Ubuntu should be faulted or should be forced to spend valuable resources trying to meet the needs of a few users.  

Enjoy Linux in whatever form or forms ends up fitting your needs best.

I think the developers should be faulted for being so closed minded (see min initial link) Additionally, Ubuntu is a rather heavy distro, so supporting CPU's in the default kernel back to the i386/i586 is absurd. While they spend time getting Compiz/Desktop effects working, they neglect to acknowledge that most i586 era computers cannot support the video card nor the ram to run it properly. In the scheme of things, gnome is pretty darn resource heavy. I'm blasting the distro because they fail to see the aforementioned. Additionally, it's not just a few users that have been requesting this support; although their cries are usually subjected to the same treatment I receive from you and muffled by the devs. I wouldn't be surprised if this thread didn't get locked or deleted.   

Someone needed to say it. DEVS: we need Highmem support...please.

---

### Post by Sef on 2008-10-09
> I meant the developers. Isn't Java fully open source now?

Yes, it is.  It is called [OpenJDK]("http://ubuntuforums.org/showthread.php?t=774956").

---

### Post by cdenley on 2008-10-10
I don't think ubuntu developers come here much. If you want to make your argument to developers, there are probably better places, such as here.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/243113](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/243113)
[https://bugs.launchpad.net/ubuntu/+bug/179025](https://bugs.launchpad.net/ubuntu/+bug/179025)
[https://bugs.launchpad.net/ubuntu/+bug/116842](https://bugs.launchpad.net/ubuntu/+bug/116842)
The Ubuntu kernel team actually reads those posts.

---

### Post by highlandsun on 2008-10-12
Speaking as a full time software developer, running a 32 bit OS on a machine with 128GB RAM is Plain Stupid.

You don't need PAE, you need x64. Period. Go clamor for something that will actually improve your computing experience. Better x64 support will improve your productivity. PAE support *won't*. It will make everything on your system slower.

By the way, last time I checked, PAE only expands you to 36 bit addressing. That means 64GB max addressable. So again, clamoring for PAE because you have a box with 128GB RAM is ... Stupid. There's no other word for it.

re: Java and Flash ... Java was supposed to be this wonderful write-once-run-anywhere VM that can do anything. The fact that it has problems in x64 should tell you something about the value of its claims to fame. (I.e., little to none.) And Flash has no business existing at all; it's a blatant attempt to destroy the free and open web (e.g. the open HTML standards) and chain it down to closed-source proprietary interests. There's nothing you can do in Flash that you can't do in Javascript. There's no excuse for it, and you should be rejecting its use everywhere you encounter it.

---

### Post by smartboyathome on 2008-10-12
> **highlandsun said:**
> There's nothing you can do in Flash that you can't do in Javascript. There's no excuse for it, and you should be rejecting its use everywhere you encounter it.

[off-topic]Actually, the statement should be "There's nothing you can do in Flash that you can't do in Javascript **and Scalable Vector Graphics**." Javascript alone can't create images quite as complex as flash, but combining SVG and Javascript to create sites renders flash obsolete imo.[/off-topic]

Anyway, this is not needed imo. If you really need stuff like that, you can use a VM or even compile 32 bit libs as needed.

---

### Post by s0cket on 2008-10-19
> **highlandsun said:**
> Speaking as a full time software developer, running a 32 bit OS on a machine with 128GB RAM is Plain Stupid.

You don't need PAE, you need x64. Period. Go clamor for something that will actually improve your computing experience. Better x64 support will improve your productivity. PAE support *won't*. It will make everything on your system slower.

By the way, last time I checked, PAE only expands you to 36 bit addressing. That means 64GB max addressable. So again, clamoring for PAE because you have a box with 128GB RAM is ... Stupid. There's no other word for it.

re: Java and Flash ... Java was supposed to be this wonderful write-once-run-anywhere VM that can do anything. The fact that it has problems in x64 should tell you something about the value of its claims to fame. (I.e., little to none.) And Flash has no business existing at all; it's a blatant attempt to destroy the free and open web (e.g. the open HTML standards) and chain it down to closed-source proprietary interests. There's nothing you can do in Flash that you can't do in Javascript. There's no excuse for it, and you should be rejecting its use everywhere you encounter it.

PAE can support up to 128 GB of RAM.  The only OS to actually implement full IA-32 PAE is Windows 2003/2008 32bit Data Center Edition.

I have a large amount of reasons why my 32bit workstation needs 8 GB of RAM.  The performance implications of PAE are real but a necessary evil for some of us.  So just discounting people who need it and saying just run x64 isn't helpful at all.

As for performance you lose some due to TLB shoot-down.  But I'd rather have that happen and get 4.5 GB of my RAM back.  It would be nice to see a 64 GB kernel in the repo for those of us who want it.  I wouldn't advocate pushing PAE on everyone but what would it hurt to get an extra kernel in the repo?

---

### Post by highlandsun on 2008-10-21
No. PAE gives you 36 bits maximum. 2^36 = 64GB. Do the math, PAE + 128GB means you're wasting 64GB of your RAM.

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

Talking about a reality check, i686 released in 1995, fine. x86_64 was designed in 2000. If you're going to update your technology, don't just take one step, go forward as far as you can.

The only reason you'd be stuck on a 32 bit OS is if there isn't a 64 bit version of some device driver that you need. So, what driver are you having trouble with? What are the obstacles to getting someone to adapt it to 64 bit? Again - you're arguing to move the distro forward, so *do that* - but make sure you actually move forward.

---

### Post by mizzouxc on 2008-11-23
<sarcasm> The Ubuntu community is so helpful </sarcasm>

Instead of helping you just argue and say "use 64 bit" I love you all.

---

### Post by cdenley on 2008-11-23
> **mizzouxc said:**
> <sarcasm> The Ubuntu community is so helpful </sarcasm>

Instead of helping you just argue and say "use 64 bit" I love you all.

We told you the options that are available to you. What were you expecting? We can't add a new kernel to the repos.

---

### Post by yelo3 on 2008-11-24
But... are there any disadvantages on installing the 64bit versions? Does all software work? also propietary software like google earth or skype? what about non-free codecs?
Thanks

---

### Post by cdenley on 2008-11-24
> **yelo3 said:**
> But... are there any disadvantages on installing the 64bit versions? Does all software work? also propietary software like google earth or skype? what about non-free codecs?
Thanks

Almost all open-source software has worked fine on 64-bit for years. Some closed source software hasn't, such as adobe flash. There is a plugin wrapper to make it work, but it still seems a little buggy to me. Google earth works, never tried skype. I never had a video or audio file I couldn't play with 64-bit ubuntu. If you limit yourself by using non-free software that isn't supported well, then there will be disadvantages.

---

### Post by jespdj on 2008-11-24
Flash 10 (32-bit) works without any problems on 64-bit Ubuntu and there is now even a 64-bit alpha version of Flash 10 which works quite well. So, Flash is definitely not a problem anymore on 64-bit.

There is currently no 64-bit Sun Java browser plugin, but it is coming early next year (this is planned for Sun Java 6 update 12). In the meantime, you can use the IcedTea Java plugin, which works with most (but unfortunately not all) Java applets.

IMO, there's really very little reason to not use 64-bit if you want to be able to use your 4 GB or more RAM.
> **yelo3 said:**
> But... are there any disadvantages on installing the 64bit versions?
Read the sticky in the [64-bit forum](http://ubuntuforums.org/forumdisplay.php?f=343).

> **yelo3 said:**
> Does all software work? also propietary software like google earth or skype? what about non-free codecs?
Thanks
Yes, yes, and yes. 32-bit software also runs on 64-bit Ubuntu. Google Earth, Skype and non-free codecs all work and can be installed from [Medibuntu](http://medibuntu.org), it's just as easy as on 32-bit.

---

