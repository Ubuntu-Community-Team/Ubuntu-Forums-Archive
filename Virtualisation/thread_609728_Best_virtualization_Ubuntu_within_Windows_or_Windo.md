---
title: "Best virtualization: Ubuntu within Windows or Windows within Ubuntu?"
date: 2007-11-11
forum: Virtualisation
---

### Post by the8thstar on 2007-11-11
Hello,

After several attempts at running XP (and soon Vista) with VMWare and VirtualBox within Ubuntu, I'm now wondering if the reverse option could be a more appropriate solution. I would like your opinion on this. Either way, I want to virtualize an existing partition into the other (raw disk if you prefer).

**Virtual Ubuntu in Vista - Ultimate Flexibility**

Pros: all the drivers load, all the media play and I have several thousands Linux programs to choose from (Ubuntu) in a native directX friendly environment where Office 2007 runs fine (Vista).

Cons: is the security as good in Vista as it is in Ubuntu, even with programs like Norton, RegCleaner, etc. ? Will the ports be open or closed like in Ubuntu? What about permissions? 

**Virtual Vista in Ubuntu - Ultimate Security**

Pros: Compiz fest for everyone if the seamless mode works one day, best threat protection for Vista based programs thanks to Ubuntu hosting/craddling

Cons: no sound in Vista with VMWare and Vbox, no support for my webcam (MS VX-6000) for Skype, no 3D accel feature in Vista

Additional question: will I have enough memory with only 1Gb to run both systems?

Your comments are welcome.

---

### Post by Depressed Man on 2007-11-11
For situation 1) Security won't be as good as natively running Ubuntu (though to be fair it all boils down to the user). But it's easier to break into a Windows machine since it has a bigger market share. Ports would be controlled by the Windows firewall (or whatever firewall you choose to install which would usually deactive the windows one). Permissions, what do you mean? In Vista they're controlled by the UAC and in Ubuntu..well if it was running virtualized Ubuntu would apply its permissions to its own file system.

And with 1 GB? I doubt it. Perhaps if you weren't running any memory hogging programs (e.g. Firefox, Open Office, Thunderbird). But my 1 GB desktop with its current load of screenlets, firefox, thunderbird, pidgin, and Open Office running is around 800 MBs of usage). Virtualization requires a nice bit of RAM, then the RAM used by the virtualized OS itself.

My laptop has Ubuntu with a virtualized XP. It uses about 1.5 GBs of RAM (with the programs running in Ubuntu) + 512 MBs of RAM for the stripped down XP I run. Vista requires alot more I think judging by its normal use on my laptop.

---

### Post by the8thstar on 2007-11-11
Thanks for your reply, **Depressed Man**. My Ubuntu 7.10 + Virtual XP MCE 2005 ran smooth and nice together with only 1Gb of RAM, even with Office 2007 open in XP and Firefox 2 in Gutsy. I guess the processor speed and the material conf also play their part in the deal.

I will try with 1Gb... if it doesn't work, I guess I'll buy some more RAM or ReadyBoost my flashstick.

---

### Post by P4man on 2007-11-12
I guess it makes sense to select the OS you prefer/use most as host. I agree with the above poster though, that 1 GB is going to be extremely tight, especially for Vista. Vista by itself requires 1GB to function decently. If you are going to virtualize windows though, I see no reason to use Vista. Use XP.

---

### Post by Depressed Man on 2007-11-12
> **the8thstar said:**
> Thanks for your reply, **Depressed Man**. My Ubuntu 7.10 + Virtual XP MCE 2005 ran smooth and nice together with only 1Gb of RAM, even with Office 2007 open in XP and Firefox 2 in Gutsy. I guess the processor speed and the material conf also play their part in the deal.

I will try with 1Gb... if it doesn't work, I guess I'll buy some more RAM or ReadyBoost my flashstick.

I don't think Office 2007 eats up as much RAM as Open Office (I can always test it out myself later though). And yeah, processing speed will help out alot. Both my PCs are dual cores (but my laptop sports a new Intel Core 2 Duo compared to my desktop's AMD Opteron). 

I would think ReadyBoost would only work if Vista was the host and Ubuntu was being virtualized. And Vista does use up more RAM then XP so keep that in mind (never tried the MCE version of XP). Don't know the specific amount though..

---

### Post by the8thstar on 2007-11-12
Hopefully I should get my Vista copy in a few days, so we'll know pretty soon which config is the best.

---

### Post by ericesque on 2007-11-13
I've had some trouble with XP in VirtualBox.  Then again, I'm trying to us MS Money installed on a virtual machine to access data on a physical partition through a samba share that is being shared from Ubuntu-- which is installed on a loopback mounted virtual partition.

LOL. I deserve.

---

### Post by jsmithy on 2007-11-14
Hello, :)

I'm a nooby to Linux and Ubuntu.

I have installed Dapper x64 in a machine with dual cores and it runs extremely good.

I installed VMware Workstation 6.0.2 (the latest build) and I created a Windows XP x32 as a guest.  It is running on the default 256MB memory allocation and I works as good as a real installation I have running in a similar hardware.

I figured out that having a 64x host to run x86 guests was the way to go.

It turns out that after a long time of testing, this setup is much much safer than any Windows setup alone.

Just a hint:  I have installed Firehol in the host to make it more secure and make security easier that to have to deal with iptables directly.  The guests are running the same firewall I was using on my real installations.

Since the guests are running with two net interfaces each, multiplexed both, guest traffic is not controlled by the host and as such there is not interference by the host at all.

Security tests of both the host and the guests have concluded that  all ports on both are secured.

I can conclude that for me, this is the best setup.

I hope this helps you.

Peace for all :)

---

### Post by dpj23 on 2007-11-15
My current on configurations using VM workstation is as follows:

XP Pro SP2 = 512mb
Vista Enterprise = 640mb

Note that Vista does experience slow downs due to the limits I put on it with only 640mb RAM...  If I had to make a suggestion it would be to run Vista with 768mb RAM...

---

### Post by tomot on 2007-11-16
Offering my 2 cents:

I don't care about rotating cubes in Ubuntu,
(and they don't work under VM in anyway event)
and I definitely dont care to do 3d desktops in Vista that requires 
even more memory.

I do care that I can use my Dual Monitors which have different
resolutions, with an extented Desktop across both monitors.

I can only do that with XP as host and Ubuntu as guest,
because the ATI/amd windows drivers are a lot better
at this time than their Linux counterparts.

AND, Ubuntu/Gutsy does not crash anymore since I
virtualised it using the ATI  XP video drivers. 

cheers!

---

### Post by veloce on 2007-11-17
> **tomot said:**
> 
I do care that I can use my Dual Monitors which have different
resolutions, with an extented Desktop across both monitors.

I can only do that with XP as host and Ubuntu as guest,
because the ATI/amd windows drivers are a lot better
at this time than their Linux counterparts.
cheers!

dual monitors with different resolutions with an extended desktop across both monitors is certainly possible under Ubuntu. (Been there, done that).  Yes it is harder than under windows - but not impossible.

Ubuntu's memory management and smp are more than worth the one time hassle of getting the screens working.

---

### Post by Hobo2021 on 2007-11-17
I think it really depends on what you use your system for the most. I would prefer to run Ubuntu with Windows as a virtual machine, but for me, I've learned, it's just not in the cards. I use Adobe products heavily, and running it in a VM limits the amount of RAM I can use, and I was never successful in getting my Wacom to work within it. Additionally, I have an X-Fi and that's just (probably) never going to work with the way Creative is not releasing drivers.

I pretty much use my Ubuntu VM for development, and Windows for everything else. Also, running Windows in VM used a ridiculous amount of memory and CPU (okay, not ridiculous, but you'd know it was running)..but so far running Ubuntu as VM it's using 20 MB of RAM and 0% CPU utilization. Even with a few programs running the usage doesn't climb significantly.

---

### Post by Victory on 2007-11-18
I'm assuming you want to use vmware to run a physical installation of Windows? My experience with that hasn't been too good.

Purely from a perspective which looks at sustainability booting into Windows natively and running Ubuntu withing that is the best option. First of all let me clarify that opinion is only considering sustainability, you can form your own view in regards to flexibility and security.

I have both ran Windows natively and booted into Ubuntu, as well as ran Ubuntu natively an vmwared Windows. First of all I found Windows a hell of a lot more difficult to setup with all guides recommending the use of vmware toolboxes scsi drivers when they were not required at all for IDE drives, this caused (and still causes many people) several sleepless nights trying to sort out the problem. However once configuration is done you wouldn't think that there's be a sustainability problem in running this configuration, but alas there is... the existence of Microsoft's WGA program.

My intention was to use Ubuntu as the primary operating system however with my private server community (lets leave the legality of this for another thread) I still need to develop things using windows utilities etc etc which I planned to use vmware for. However I would occasionally need to boot into Windows natively to testrun the game clients as vmware at this stage is not very good for gaming (and neither seems any other solution for 3d direct 9). 

How WGA comes into play. Once you've got vmware running Windows it'll prompt you to activate your copy of windows within the next 3 days. No problem, just activate online and away we go. Once doing all my developing and configuring the time comes to boot into windows natively and try out my changes on the game clients. Upon native booting Windows finds that it has had too many hardware changes once again, and requires activation. The use of separate configured hardware profiles does not fix this and so you will find yourself continually activating windows..

There are workarounds to this problem perhaps but I wanted a no fuss solution so in my situation I've had to get rid of Ubuntu for that particular computer.

---

### Post by veloce on 2007-11-19
Whereas my experience of using a windows vm under ubuntu has been excellent. The key point of difference is that I don't need 3d in windows.  This means I only had to reactivate windows once and it's sorted.

The key advantage for me is that I have far less cr@p installed in my virtual windows and it actually runs *faster* than natively! Plus, Ubuntu handles memory and smp so much better. 

So my experience has been:
[LIST]
[*]A 512Mb windows XP machine in a 1Gb Ubuntu physical machine works well.  
[*]A 512Mb Ubuntu vm in a 1Gb Windows XP physical machine was a dog.
[/LIST]

So, as per usual, selection of the best tool is dependent on the job you want to do with it.

---

### Post by the8thstar on 2007-11-21
Thank you guys for all your feedback and replies. At this point, I'm going to leave the two systems separate. Both are excellent in their respective domains and they are nice complements to each other.

With only 1Gb of RAM, it seems too difficult to run both at the same time. Also, I understand Ubuntu becomes a resource hog under Vista and Vista doesn't like to run under Ubuntu. Then, there is the activation bit and the Microsoft EULA that deter me from wasting my time on this.

My only real interest at running the two systems together was to allow Office 2007 to run. From what I understand, Office can run on Windows 2000 as well; the nice part is that there is no activation required for that OS.

So... I'm gonna try and find a copy of Windows 2000 on eBay and run it under VMWare or VirtualBox, with Office 2007 installed in it.

In the meantime, I have made sure that all my files can be found in the same spot for Vista and Ubuntu. This way, I don't have to worry about looking for them forever on end. I have patched Vista to recognize ext2/ext3 partitions, so all is good.

---

