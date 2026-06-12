---
title: "Virtualization v Dual-Boot"
date: 2010-01-23
forum: Virtualisation
---

### Post by jamesisin on 2010-01-23
The gloves are off...

I have long been an advocate of virtualization.  I can see no reason to choose dual-boot.

Virtualization is pretty clearly the future of multi-system computing and that future has arrived. Even MS finally got on board with virtualization.

Anything that can be accomplished with a separate boot can be better accomplished with virtualization.  The strongest benefit that comes to mind is that a VM is accessible without leaving the host system. By contrast in a dual boot scenario you have to leave one system to access the other.

The biggest problem I see in setting up a dual-boot system is the tendency to boot into your primary system and to ignore the other(s).  One system is favored and any others are neglected.

There is a lot of talk on the forums about working with dual-boot systems.  I see a lot of what appears to be dual-boot advocacy.  Surely there must be some benefit I am not seeing clearly.

Thoughts?

---

### Post by user1397 on 2010-01-23
> **jamesisin said:**
> The gloves are off...

I have long been an advocate of virtualization.  I can see no reason to choose dual-boot.

Virtualization is pretty clearly the future of multi-system computing and that future has arrived. Even MS finally got on board with virtualization.

Anything that can be accomplished with a separate boot can be better accomplished with virtualization.  The strongest benefit that comes to mind is that a VM is accessible without leaving the host system. By contrast in a dual boot scenario you have to leave one system to access the other.

The biggest problem I see in setting up a dual-boot system is the tendency to boot into your primary system and to ignore the other(s).  One system is favored and any others are neglected.

There is a lot of talk on the forums about working with dual-boot systems.  I see a lot of what appears to be dual-boot advocacy.  Surely there must be some benefit I am not seeing clearly.

Thoughts?well sometimes virtualizing an OS can make it seem slower than dual-booting it, especially depending on how much ram you set for it.  also, running 2 OS's at the same time takes up a lot of resources.  if you're gonna do most of your work/play on one OS and only occasionally use the other, why not dual-boot?  it makes more sense.

---

### Post by d3v1150m471c on 2010-01-23
The only trouble I had with vbox running xp was my microphone was buggy as crap. Other than that, screw dual boot.

---

### Post by jamesisin on 2010-01-23
> **ubuntuman001 said:**
> if you're gonna do most of your work/play on one OS and only occasionally use the other, why not dual-boot?

Because I can wake a saved-state VM in seconds.  Takes way more time and is *way* more intrusive to close all my applications and reboot the system.

As to RAM, if your host OS is 64 bit (or 32 with mods) you can add many gigs of RAM and give your VM's plenty to keep them happy-snappy.

---

### Post by John Bean on 2010-01-23
> **jamesisin said:**
> Anything that can be accomplished with a separate boot can be better accomplished with virtualization.

I could almost agree had you not used the words "anything" and "better". As it stands your assertion is not true.

---

### Post by Thomas Garman on 2010-01-23
I have been using a dual boot set up with Vista Ultimate and Ubuntu for a while now.  I just recently tried the Virtualbox PUEL and installed XP Home SP3 in it so that I can watch Netflix streaming and manage my iPod touch without booting into Vista.

I don't think putting my Vista Ultimate system into a virtualmachine and using my sound editing software Magix in there would really make sense because my virtual machine by definition has less RAM and only uses one of my CPU cores.  If I really need to use the software in my Vista Ultimate system, then I really need the full power of my computer.

One question I was wondering about was this:  I am running 32-bit and so my computer cannot address 4 GB of RAM.  BUT  if I install 4GB of RAM and then give 2GB to my Vista Ultimate Virtual Machine, will the virtual machine be able to use it?  Even though my Ubuntu system has 2 GB RAM for it too?  And if it would work to add that much RAM, would it work to install up to 6GB?

The reason, in other words, that I use Dual Boot rather than Virtual Machine exclusively is that in the Virtual Machine my Windows System is restricted to 1 GB of RAM and since I am in 32-bit I can't address more than 3 GB anyway.

---

### Post by jflaker on 2010-01-23
> **Thomas Garman said:**
> One question I was wondering about was this:  I am running 32-bit and so my computer cannot address 4 GB of RAM.  BUT  if I install 4GB of RAM and then give 2GB to my Vista Ultimate Virtual Machine, will the virtual machine be able to use it?  Even though my Ubuntu system has 2 GB RAM for it too?  And if it would work to add that much RAM, would it work to install up to 6GB?

No, the host still being 32 bit can only SEE 3GB or RAM.  It is in the number of ram addresses.  When you assign RAM to a vm, you are borrowing from the avail RAM.  If you have 3GB, give your vm 1536MB (1.5GB) and things should be ok and it still leaves plenty for your host

---

### Post by timd01 on 2010-01-23
> **ubuntuman001 said:**
>   if you're gonna do most of your work/play on one OS and only occasionally use the other, why not dual-boot?  it makes more sense.

Can't agree with this, no offence though.  I'm a virtualisation fan now after years of dual booting.  I run 95% Linux and a rare 5% Wincrap or something like that.  

Anyway reached the stage where rebooting to accomplish a mere 5% of my work really was not worth the effort.  Hence am now running vbox very happily about once a fortnight to look at why I took up Linux in the first place and all with two or three mouse clicks.  Makes sense to me any way. :-)

---

### Post by fjm03 on 2010-01-23
> **jamesisin said:**
> The gloves are off...

I have long been an advocate of virtualization.  I can see no reason to choose dual-boot.

Virtualization is pretty clearly the future of multi-system computing and that future has arrived. Even MS finally got on board with virtualization.

Anything that can be accomplished with a separate boot can be better accomplished with virtualization.  The strongest benefit that comes to mind is that a VM is accessible without leaving the host system. By contrast in a dual boot scenario you have to leave one system to access the other.

The biggest problem I see in setting up a dual-boot system is the tendency to boot into your primary system and to ignore the other(s).  One system is favored and any others are neglected.

There is a lot of talk on the forums about working with dual-boot systems.  I see a lot of what appears to be dual-boot advocacy.  Surely there must be some benefit I am not seeing clearly.

Thoughts?

Yup. 

Since Ubuntu 9.10 doesn't  play well with VMware and no one in either community is apparently able to solve the dilemma, I'm forced to dual boot.

Worse, 9.10 broke Samba and Concanical appears to be making little/no effort to solve the mystery. I'm now back to 9.04.

Network transfers and virtualization are pretty basic tools today. An O/S that  can't or won't accommodate either is of little value to me.

I'm still here because I'm hoping that the next Ubuntu LS edition will work with industry standards like VMware and Samba

---

### Post by jamesisin on 2010-01-23
> **fjm03 said:**
> Since Ubuntu 9.10 doesn't  play well with VMware

Use VirtualBox?  I do and it works great.  But add the VB PPA:

[http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian)

For adding the repo see here:

[http://ubuntuforums.org/archive/index.php/t-1222701.html](http://ubuntuforums.org/archive/index.php/t-1222701.html)

> 9.10 broke Samba

I am running a 9.10 Samba server without any issues.  Try this thread:

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

of this one:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by howefield on 2010-01-23
> **jamesisin said:**
> Anything that can be accomplished with a separate boot can be better accomplished with virtualization.

Complete rubbish. As it stands at the moment.

There are a few examples to rebut your claim, including hardware limitations and gaming.

---

### Post by jamesisin on 2010-01-23
Hardware limitations?

---

### Post by Fire$torm on 2010-01-23
Hi all,

*The main reasons I dual boot over VM are:*
1) I am a gamer :P and none of my games run on Linux. Use wine you say??? The performance hit is just WAY to high, forget it. Wine lovers, sorry.

2) Windows is still my primary OS for my desktop and server. When I get to the point where I am comfortable with using Linux as my PRIMARY OS then I will just switch to Ubuntu and maybe VM Windows. FYI: Last week I installed Karmic on my laptop, and so far I've had to reinstall only twice since. Why, I keep playing with stuff until something breaks. Its the best way to truely learn an OS. :KS

3) All of my computers, Desktop - Server - Laptop, run Boinc continuously. This means that whatever system resources are not being used by the current app or games that I am running are being used by Boinc. I do not want VM gumming up the works.
Note: One of my Boinc apps, MilkyWay@Home, uses my CPU & GPU to crunch nembers on my desktop.

4) VM is not 100%. I have read many threads dealing with VM issues, so I prefer to err on the side of caution, for now.

I hope I have not offened anyone. I guess I just like doing some things the hard way. This probably stems from my DOS 3.3, 4.0 and 6.22 days.......

Peace.

---

### Post by jamesisin on 2010-01-23
> **Fire$torm said:**
> This means that whatever system resources are not being used by the current app or games that I am running are being used by Boinc. I do not want VM gumming up the works.

I'm not trying to sway you but your virtual machine can be put, at a moment's notice, in a saved state which releases all dedicated resources back to the host.  You can also alter those dedicated resources at any time (though I think this requires a shutdown of the VM, change RAM designation, boot the VM).

I have a house filled with computers and I know I'm not making enough use out of virtualization.  For instance I ought to add a second proc and a boat load of RAM to one server downstairs, then virtualize my SBS and my Ubu servers onto that hardware (with 64 bit Ubu as host).  Maybe after I get a job...

---

### Post by rogue_0111 on 2010-01-23
My vote is for virtualbox. 

Last night I had the chance to speak with Brian Leonard (Technology Evangelist) from Sun Micro. We both agree virtualbox is indispensable. 

As a side note OpenSolaris with the ZFS is too cool.

---

### Post by jamesisin on 2010-01-23
> **rogue_0111 said:**
> Brian Leonard (Technology Evangelist) from Sun Micro... agree[s] virtualbox is indispensable.

He does?  Really?  How odd.

---

### Post by bpalone on 2010-01-23
I do both, using virtualization when the job is low demand and a short project.  If I am going to be using the Windows apps all day long then I just go ahead boot into Windoze and drag my feet the rest of the day.

There are some quirks I have found using VirtualBox, but they can be lived around. I say, use both.  Use what fits best at the moment.

---

### Post by andrea000 on 2010-01-23
For some dual booting is the answer others virtualization
is others like myself wine is there answer the first rule
is use what works best for you.Virtualization is good when
you have to much stuff to do in one O.S. and you have the
resources available to do that.Wine is also very good it's
really good for those who do not use a lot of windows
software or were linux doesn't have a software alternative.

---

### Post by rogue_0111 on 2010-01-23
> **jamesisin said:**
> He does?  Really?  How odd.

Wow. My bad. I was just sharing.

---

### Post by howefield on 2010-01-23
> **jamesisin said:**
> Hardware limitations?

That is what I said. :)

Presumably you didn't know that or you wouldn't have made such an extravagant claim. Not all hardware will work as well, if at all in a virtualised environment.

Virtualising operating systems is a superb tool and has its uses but has a way to go before being being as good as the "real" thing.

---

### Post by jamesisin on 2010-01-23
> **howefield said:**
> That is what I said.

I know; I was actually wondering what you meant by hardware limitations.  You really can't just say a two word phrase and leave it at that.  I am interested in what you mean when you say it.  You describe a little more in this last response, but I am still curious about further details.

---

### Post by jamesisin on 2010-01-23
> **rogue_0111 said:**
> Wow. My bad. I was just sharing.

Easy now.  Don't take my sarcasm too seriously.  But really wouldn't any corporate representative advocate for their own software?  How is this different from Gates saying "Windows is vital to the future of computing."; how is it any more credible?

---

