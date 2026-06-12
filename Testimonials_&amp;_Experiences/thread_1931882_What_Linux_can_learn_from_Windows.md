---
title: "What Linux can learn from Windows"
date: 2012-02-26
forum: Testimonials &amp; Experiences
---

### Post by BertN45 on 2012-02-26
Using Ubuntu now for a couple of years, I have noticed that the system performs worse then Windows, when reaching the limits of the hardware it uses. I have noticed the following:
[LIST]
[*] As soon as the SWAP area is needed the system stalls in practice. Linux become very unresponsive and occasionally it takes minutes to select a menu entry of an active window. It is even hardly possible to close programs to free up memory. In strong contrast to e.g. Windows 7, that often has the same amount of memory swapped out as it has resident and remains responsive much longer.
[*] During high cpu loads Linux becomes unresponsive and it takes a long time before the system copes with the increase in load. Windows always boosts the priority of the process belonging to the active window and thus remains more responsive. Scheduling in Linux looks too complex and not very well suited for the desktop. It looks like they optimize for real time processes and batch jobs at the costs of the interactive processes and that is a pity. A batch process is something of the past and strong real time requirements are mainly caused by a poor design of the HW/SW interface.
[*] Note also that nowadays Ubuntu 11.10 uses the same amount of memory as Windows Vista!
[/LIST]

---

### Post by kevdog on 2012-02-26
Did you install a swp partition?  If not you know you can designate a portion of the file system as swap.  I too noticed a lot of lagging when the swp partition wasn't activated, however once activating my swp partition and making the appropriate changes in the fstab file, its really made a huge difference.

---

### Post by haqking on 2012-02-26
> **BertN45 said:**
> Using Ubuntu now for a couple of years, I have noticed that the system performs worse then Windows, when reaching the limits of the hardware it uses. I have noticed the following:
[LIST]
[*] As soon as the SWAP area is needed the system stalls in practice. Linux become very unresponsive and occasionally it takes minutes to select a menu entry of an active window. It is even hardly possible to close programs to free up memory. In strong contrast to e.g. Windows 7, that often has the same amount of memory swapped out as it has resident and remains responsive much longer.
[*] During high cpu loads Linux becomes unresponsive and it takes a long time before the system copes with the increase in load. Windows always boosts the priority of the process belonging to the active window and thus remains more responsive. Scheduling in Linux looks too complex and not very well suited for the desktop. It looks like they optimize for real time processes and batch jobs at the costs of the interactive processes and that is a pity. A batch process is something of the past and strong real time requirements are mainly caused by a poor design of the HW/SW interface.
[*] Note also that nowadays Ubuntu 11.10 uses the same amount of memory as Windows Vista!
[/LIST]

a broad sweeping statement relating to your own particular setup of course and not Linux/Ubuntu in general ;-)

---

### Post by aysiu on 2012-02-26
I don't even use a swap partition.

---

### Post by inobe on 2012-02-26
sounds like someone is running an old low end system with possible hardware malfunctions.

dude, did you get a dell?

---

### Post by BertN45 on 2012-02-26
> **kevdog said:**
> Did you install a swp partition?  If not you know you can designate a portion of the file system as swap.  I too noticed a lot of lagging when the swp partition wasn't activated, however once activating my swp partition and making the appropriate changes in the fstab file, its really made a huge difference.
Yes I do use a swap partition and that is used too.

---

### Post by darrenn on 2012-02-26
Isn't this a recurring discussion?

---

### Post by philinux on 2012-02-26
Moved to T&E.

---

### Post by rjbl on 2012-02-26
> **BertN45 said:**
> Using Ubuntu now for a couple of years, I have noticed that the system performs worse then Windows, when reaching the limits of the hardware it uses. I have noticed the following:
[LIST]
[*] As soon as the SWAP area is needed the system stalls in practice. Linux become very unresponsive and occasionally it takes minutes to select a menu entry of an active window. It is even hardly possible to close programs to free up memory. In strong contrast to e.g. Windows 7, that often has the same amount of memory swapped out as it has resident and remains responsive much longer.
[*] During high cpu loads Linux becomes unresponsive and it takes a long time before the system copes with the increase in load. Windows always boosts the priority of the process belonging to the active window and thus remains more responsive. Scheduling in Linux looks too complex and not very well suited for the desktop. It looks like they optimize for real time processes and batch jobs at the costs of the interactive processes and that is a pity. A batch process is something of the past and strong real time requirements are mainly caused by a poor design of the HW/SW interface.
[*] Note also that nowadays Ubuntu 11.10 uses the same amount of memory as Windows Vista!
[/LIST]


Hmm ...... you seem to have noticed things that no-one else, repeat no-one else, in the whole wide world has ever, repeat ever, noticed before since GNU/Linux first appeared nearly twenty years ago. Perhaps you are on your own in your opinions - even amongst MS fanboys.

rjbl

---

### Post by BertN45 on 2012-02-26
> **haqking said:**
> a broad sweeping statement relating to your own particular setup of course and not Linux/Ubuntu in general ;-)
My setup is the default setup of a 64-bits Ubuntu system. It is not  broad sweeping, because it is relatively precise for a post in the community cafe.

I did not say the Windows is better, I simply said that it behalves better in some circumstances.

---

### Post by gardnan on 2012-02-26
Two things:

You must realize that these are not widespread problems, as this is the first time I have heard anyone complain about the use of swap space. In addition, I have never experienced either of these problems, so if you could come up with an adequate test case, maybe someone will try and fix the problem.

And you must also realize that if Linux seems less responsive, it is because Linux is actually fairly GUI-agnostic, and will not grant the window manager any special priority or treatment, as it is just another process. This is what allows the wide variety of different window managers and GUI systems available on Linux.

---

### Post by BertN45 on 2012-02-26
> **inobe said:**
> sounds like someone is running an old low end system with possible hardware malfunctions.

dude, did you get a dell?

So Linux does not support old low end systems? You advice the people to go back to Windows, if they have system older then 4 years?

---

### Post by craig10x on 2012-02-26
Ubuntu 11.10 takes as much memory as windows?  That's a new one on me...
normally in my ubuntu 11.10 my system monitor shows about 700 mib (not even 3/4 of a gig) and at the highest (running stream radio, flash videos and even heavy memory taking java programs) i have seen it go is about say 930 mib...

Still way under 1 gig....even with all sorts of things going on...and this is with a 64 bit system (32 bit would use even less)...

Windows Vista takes a LOT more to run (with some of the applications i mentioned)...oh i know what microsoft says on their site...but i remember that in actual USE it took a lot more then the 1gb they claim it can run on...

---

### Post by inobe on 2012-02-26
> **BertN45 said:**
> So Linux does not support old low end systems? 

well you say linux now?

> Using **Ubuntu** now for a couple of years, I have noticed that the system performs worse then Windows

now since you confused linux with ubuntu, you switched things around we can go that way;)

there are hundreds of distributions, some of which can run on really low end hardware.

> You advice the people to go back to Windows, if they have system older then 4 years?

i have a few systems here that vista or 7 cannot operate on.

they are perfect candidates for these continuously updating distributions, giving me the latest and greatest software, they will always be useful to me on this platform!

you see everything wrong, open the eyes and mind, look around, you'd be amazed what can be found.

---

### Post by BertN45 on 2012-02-26
> **gardnan said:**
> Two things:

You must realize that these are not widespread problems, as this is the first time I have heard anyone complain about the use of swap space. In addition, I have never experienced either of these problems, so if you could come up with an adequate test case, maybe someone will try and fix the problem.

And you must also realize that if Linux seems less responsive, it is because Linux is actually fairly GUI-agnostic, and will not grant the window manager any special priority or treatment, as it is just another process. This is what allows the wide variety of different window managers and GUI systems available on Linux.


The second point was basically what I have said. The system is not optimized in any way for interactive use. On top of it the current Unity implementation with X, gnome, compiz and unity creates a lot of overhead (too many processes and too many process switches), maybe it gets better when Wayland is introduced. But the basic problem remains, the scheduler does not support/recognize interactive processes and more specifically the processes for the window I am working on at that moment in time. Probably it is more a desktop issue, they should boost the priority of the processes supporting the active Window.

---

### Post by inobe on 2012-02-26
running ubuntu on anything lower than a gig of memory footprint is like mounting a mustang front end on a ford pinto:P

---

### Post by DeathShot on 2012-02-26
> **rjbl said:**
> Hmm ...... you seem to have noticed things that no-one else, repeat no-one else, in the whole wide world has ever, repeat ever, noticed before since GNU/Linux first appeared nearly twenty years ago. Perhaps you are on your own in your opinions - even amongst MS fanboys.

rjbl
Actually I noticed this too, at least for me Windows 7 is faster and a lot more responsive. This could be due to the fact that it's built to take advantage of high end hardware as opposed to most Linux distros which are built to be small, and resource friendly. Also I noticed that Aero in Windows 7 has really good HWA and is optimized to not use *that* much more resources, unlike in Vista.

Also Ubuntu tends to take a lot more time to start up software then windows ever did. I notice the "starting so and so piece of software" for a few seconds before anything starts.

With that said, the fact that you can switch desktop environments with out even logging out and in sometimes, and the fact that one distro can cater to both high end and low end systems is something windows can't do, amongst other things. They both have theirs ups and downs, though Linux's biggest flaw is it's lack of corporate support. If Linux had a Multi-Billion dollar corporation which can throw Billions of dollars on a specific distro like MS or Apple can on their Operating Systems it would have greater support and more users.

---

### Post by BertN45 on 2012-02-26
> **craig10x said:**
> Ubuntu 11.10 takes as much memory as windows?  That's a new one on me...
normally in my ubuntu 11.10 my system monitor shows about 700 mib (not even 3/4 of a gig) and at the highest (running stream radio, flash videos and even heavy memory taking java programs) i have seen it go is about say 930 mib...


Well that proves my point. I bought the Dell with Vista and used it for some time for work. The original release was a disaster, but using it with Vista SP2, it needed close to 700Mb after booting:) The Windows 7 Beta, I tried, did need around 500MB after booting and Windows 8 is better again around 400MB. What it needs afterwards is almost completely dependent on the size of the application programs you use.

The improvement for Windows 7 came largely due to a change of the  paging philosophy. They succeeded to write another 200MB of OS to the page file without influencing the responsiveness.

---

### Post by BertN45 on 2012-02-26
> **inobe said:**
> running ubuntu on anything lower than a gig of memory footprint is like mounting a mustang front end on a ford pinto:P
You might not realize it, but most people in the world cannot afford a Ford Mustang. We do not all live in the USA.

---

### Post by cprofitt on 2012-02-26
It is odd that as soon as a person posts an observation that is somewhat negative about Linux people jump on them.

How about telling the person how to avoid the issue?

While the OP compares 11.10 to Vista it should be noted that Windows 7 is much more memory efficient.

When I boot Windows 7 it uses roughly 640mb of ram Ubuntu 11.10 takes about 720mb

I do not use swap very often, but if the fix is simple we should try to assist the OP.

---

### Post by MG&amp;TL on 2012-02-26
1GB is what I would call "a reasonable limit" for unity3d. Try unity2d, Xubuntu, Lubuntu. Don't even look at Kubuntu, unless you install that low-fat thing they were talking about.

---

### Post by Kevin McCready on 2012-02-26
> **inobe said:**
> running ubuntu on anything lower than a gig of memory footprint is like mounting a mustang front end on a ford pinto:P

I run Lubuntu on old laptop Toshiba TecraA5 1.73 GHz Intel Pentium M, 760 GB RAM   60 GB hard drive

It runs faster than any dumb cars and almost as fast as my 8.2 kg bicycle. I switched to linux because Windows7 was too slow on my laptop. 

I tried Linux in 2004 and gave up because support wasn't to the level of my needs. There is still a LONG way to go to help newbies, but at least I can muddle on now.

---

### Post by inobe on 2012-02-26
> **cprofitt said:**
> 

When I boot Windows 7 it uses roughly 640mb of ram Ubuntu 11.10 takes about 720mb

I do not use swap very often, but if the fix is simple we should try to assist the OP.


and here i'm trying to get the system to use all 8gigs, and can't get it to use just two:p

the problem for the op is that he/she hasn't recognized the minimum system requirements.

that in mind is bare minimum and not recommended, this means a slow usable system.

another is comparing linux to windows, this is like comparing apples to oranges.

---

### Post by BertN45 on 2012-02-26
> **inobe said:**
> and here i'm trying to get the system to use all 8gigs, and can't get it to use just two:p

the problem for the op is that he/she hasn't recognized the minimum system requirements.

another is comparing linux to windows, this is like comparing apples to oranges.

First of all my main system came with Vista installed and could run that OS relatively well, surely after SP2. As you can see it has 2GB and that should be enough for Ubuntu. So you are completely wrong talking about minimum system requirements.

Secondly you can solve any load problem by throwing HW at it. The point is, that we should expect a graceful degradation of performance at the moment we start hitting the limits of the HW we use. That is what I expect from a well designed system (Windows, Ubuntu or Linux). Remember swapping and scheduling is done by the kernel (Linux), but it can be influenced by the Desktop (Ubuntu). The desktop knows the active windows and could raise the priority for the processes supporting that active window, like Windows does.

If I cannot compare two desktop OSes, I cannot compare anything anymore.

If we never would discuss shortcomings and potential improvements, we all would be living still in a cage.

---

### Post by philinux on 2012-02-27
11.10 64 bit system here. Typical daily performance png attached.. Never goes over 1gig. Only time it has was when running virtualbox.

This is an older desktop from 2007 with 2 gig ram.

AMD Athlon(tm) 64 X2 Dual Core Processor 5200+ × 2 
nVidia GeForce 8600 GT

My Acer 1410 netbook runs win7 dual boot. 2 gig ram again but Ubuntu runs much better. I only use win7 for bskyb's SkyGo service.

---

### Post by kurt18947 on 2012-02-27
> **philinux said:**
> 11.10 64 bit system here. Typical daily performance png attached.. Never goes over 1gig. Only time it has was when running virtualbox.

This is an older desktop from 2007 with 2 gig ram.

AMD Athlon(tm) 64 X2 Dual Core Processor 5200+ × 2 
nVidia GeForce 8600 GT

My Acer 1410 netbook runs win7 dual boot. 2 gig ram again but Ubuntu runs much better. I only use win7 for bskyb's SkyGo service.

I have a similar processor w/ 4 Gb. RAM.  I started 11.10 **and** Win7 running in virtual box.  Still using < 1 Gb. RAM.

---

### Post by DeathShot on 2012-02-27
> **philinux said:**
> 11.10 64 bit system here. Typical daily performance png attached.. Never goes over 1gig. Only time it has was when running virtualbox.

This is an older desktop from 2007 with 2 gig ram.

AMD Athlon(tm) 64 X2 Dual Core Processor 5200+ × 2 
nVidia GeForce 8600 GT

My Acer 1410 netbook runs win7 dual boot. 2 gig ram again but Ubuntu runs much better. I only use win7 for bskyb's SkyGo service.

 Philinux, why do you have a 64bit system with only two gigs of ram? That's like having a race car with only 50HP. It makes no sense, if you have less then 4 gigs 64bits will just slow you down.

---

### Post by philinux on 2012-02-27
> **DeathShot said:**
> Philinux, why do you have a 64bit system with only two gigs of ram? That's like having a race car with only 50HP. It makes no sense, if you have less then 4 gigs 64bits will just slow you down.

Not slower at all. It's a 64 bit machine. Why would I run 32 bit.
 [http://tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

Lets not go down that debate. It's been done to death in recurring. 

Ok back on topic eh.

---

### Post by DeathShot on 2012-02-27
Fair enough

---

### Post by jmszr on 2012-02-28
BertN45,

About 3/4 of the way down SwapFaq: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) they discuss swappiness and how to adjust the swappiness value. Perhaps that might make a difference?

Hope that helps.

---

### Post by mastablasta on 2012-02-28
I noticed freezing and sometimes but rarely crashing on the old maschine. apparently it was swap fault (only 224MB ram). now this didn't happen in WinXP. computer would slow down there but would not freeze comepletelly as it did in Ubuntu.
 
anyway problem was solved by using lighter distro. so far no crashes, freezes, even slow down is rare.
 
one issue that was sort of mentioned here and that bothers me is that when for example running something fullscreen (especially in wine) the system keys and desktop in general still have priority over the programme. in windows as i know only ctrl+alt+del and occasioanlly alt+tab combos will do something. while all others will not interfere with programme.
 
same goes for taskbars (or whatever they are called now) they will dissapear (well actualyl i htink they are in the back) if you run something full screen.

---

### Post by BertN45 on 2012-02-28
> **jmszr said:**
> 
About 3/4 of the way down SwapFaq: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) they discuss swappiness and how to adjust the swappiness value. Perhaps that might make a difference?

I will try it, thank you. 

I have detected a number of problems; one with my system and the others with Ubuntu and/or Linux:
[LIST]
[*] Virtualbox and The latest 3.0.0.15/16 kernels seem to have an incompatibility. It slows down the LINUX Guests sometimes so much, that only after 10 minutes I see the Login screen. The advice in the VBOX forums is to re-install Ubuntu 11.10, since 3.0.0.12 does not seem to have that problem. I will wait for the Beta from Ubuntu 12.04.
[*] When running in the situation that my both cores are maxed out and run at 100%, the cpu frequency sometimes stays for 25 seconds on the lowest value in my case 800 mHz. As soon as there is a little bit time left, say at loads of 90% the cpu frequency is switched to the full 1800 mHz. I have noticed that the indicator frequency applet runs at nice priority, which is wrong, if it has to switch the frequency itself. I will find out, who is supposed to do the switching and at which priority that process or daemon runs.
[*] The on demand governor for the frequency switching is too conservative, by default it changes the frequency when the cpu-load is 95%. That means that it has been completely optimised for power and heat efficiency at the cost of response times. I think, it should boost the frequency at 33% or 50% to ensure low power consumption when feasible. However as soon the demand increases, it should give priority to response times. I changed those values in the kernel, but due to the other problems, it had no noticeable effect. For the moment I disabled frequency control in the BIOS.
[*] Remains the point that I still think that Ubuntu should raise the priority of the processes supporting the active window, at least, it would give me the change to kill a run-away process like Virtualbox somewhat faster. I do not like to wait 5 minutes before something happens.
[/LIST]

Currently I am rearranging the hardware, because I had a number of defect PCs, The one for the visitors (mostly children) broke down last weekend after 15 years of service, so I try to combine 2-3 defect PCs into one functioning one. Next week I continue with these issues.

---

### Post by doublemeat on 2012-02-29
> **rjbl said:**
> Hmm ...... you seem to have noticed things that no-one else, repeat no-one else, in the whole wide world has ever, repeat ever, noticed before since GNU/Linux first appeared nearly twenty years ago. Perhaps you are on your own in your opinions - even amongst MS fanboys.

rjbl

That is simply not true. I've run countless various Linux distros on a huge variety of hardware, ranging from original Pentium, to the latest Intel beasts; and with a huge variety of graphics, memory, and drive hardware capabilities. I run it in VMs with and without VT-x and VT-d/IOMMU, and natively.

The OP's post may be too general to adequately address, but this response is much more so. I can confirm his experiences at various times on a full spectrum of hardware; from configs that give Windows 2000 a hard time, to 8-core 16gb multi-SSD beasts. 

Usually Linux distros perform great when pushed to hardware limits, but it very often they do choke, stutter, and stall under heavy CPU, memory, and/or IO loads. Sometimes I've been able to figure out why (or at least do something to fix it...e.g. moving swap file or partition to SSD stripes), sometimes not. It all depends on the unique mix of hardware and drivers. Maybe it's the kernel's fault, maybe not. (I suspect it's usually issues with loadable modules.) 

It doesn't really matter, the point is that somewhere along the software stack (regardless of who owns it), resource pressure is not always dealt with optimally - where, say, Windows might have no problems with the same hardware. (OTOH I've seen many instances of the exact opposite; Windows chokes and Linux sails.) Maybe the hardware interfaces aren't exactly to spec and the driver code isn't as lenient as Windows; maybe there are hard-to-test bugs in the code under unusual conditions. Maybe the hardware itself has problems and the Linux code could do better at managing fringe cases. 

I don't know why it is, and really don't care. All I know is that it is absolutely true, fair, and accurate. The OP might or might not be correct in his suspected causes, but the observe symptoms ABSOLUTELY DO OCCUR UNDER SOME CONFIGURATIONS AND CIRCUMSTANCES. And again - maybe it's worse than Windows, maybe the other way around. My own subjective, anecdotal experience is that Linux experiences such slowdowns, stalls, glitches, and freezes more than Windows. (Which should really not be surprising - all fanboy prejudice aside - since Windows has had billions of dollars poured into it.) I am keenly aware that I could even be wrong about the balance of Windows vs. Linux glitches in my own experience, much less do I have basis to suggest which has more issues globally. 

I will say, the problems with either one, for me, have been rare and/or fixable enough to not be a big issue. But on occasion I have lost work (in both OSes) due to the system either crashing, becoming instantly unresponsive (either temporarily or permanently), and/or becoming gradually unresponsive for various reasons including runaway privileged execution, interrupts piling up, etc.

I submit that if you have never experienced such things, you either haven't used computers long enough, and/or enough computers, and/or haven't demanded enough of them. Furthermore if you don't know anyone who has experienced such things in Linux, ever, then you either don't know enough people, enough computer users, enough Linux users, and/or enough people with enough computers and experience and who demand enough from their computers.

So there: Now you cannot say you do not know anyone, ever, that has experienced such symptoms. :-)

And yeah, I'd also agree vehemently with the thread title that "Linux" can learn from "Windows". And also the other way around. This Linux vs. Windows vs. Mac OS X stuff is even more silly and pointless than the Ford vs. Chevy argument. (I once read a BSD fanboy that said in all seriousness, that BSD was so much more advanced than Windows, that it would uncover hardware flaws that Windows wasn't capable of reaching [that was his reasoning of why BSD was more unstable than Windows on a particular poster's PC]. What an absurd, flawed, and pointless assertion!)

---

### Post by mastablasta on 2012-02-29
Yes plenty servers chuckle and slow down to a crawl every day. especially google ... oh the slowdowns in their stacs....

remeber the reason windows performs nicer on more windows certified hardware is because manufacturers provide drivers for it. and they provide patches. while in linux. well you know how it is. as you said it maschine can work smooth or not. the question here is: is it OS fault or the lack of propper drivers fault?

i mean often drivers used here in linux are generic. and not tailored to specific hardware. and often times you end up using drivers that are for a similar but not really same chip.

---

### Post by BertN45 on 2012-02-29
> **doublemeat said:**
> The OP's post may be too general to adequately address, but this response is much more so. I can confirm his experiences at various times on a full spectrum of hardware; from configs that give Windows 2000 a hard time, to 8-core 16gb multi-SSD beasts. 


Thank you for the support. I started the post because, I hoped somebody could explain to me what caused the problem. From the past I know, that when you start to explain a problem, you suddenly see the light or a remark puts you on the right track. With a few exceptions nobody had any technical advice. It started to look more and more like a discussion between true believers.

Not counting the first incompatibility in my last post, I mention three points, which in my view would improve the experience of the Ubuntu/Linux users. I know operating systems and I am familiar with the internals of a kernel, but Linux is (not yet) part of that knowledge. I could use some help, but then you have to react based on the technical ideas I expressed. Discussion will improve or invalidate those ideas.

I intend to file some bug reports or change requests. At least two of the issues should be simple to solve.

---

### Post by cwklinuxguy on 2012-02-29
I once tried to run Ubuntu 11.04 on a netbook in a virtual machine, and the VM had about half my RAM or a little more (probably between 500 and 700 MB). Yeah...it was a TERRIBLE experience. Trying to run Unity on low end hardware doesn't work well. It's just how it is. Unity is simply too heavy for running on less than a gig of RAM. Now, LXDE, XFCE, ***maybe*** MATE (fork of Gnome 2)...fine, you should have better luck. But not Unity. Trying to run Unity on super low-end hardware isn't much better than driving a big rig through mud. XFCE or LXDE should give you better performance in that regard, I think :)

---

