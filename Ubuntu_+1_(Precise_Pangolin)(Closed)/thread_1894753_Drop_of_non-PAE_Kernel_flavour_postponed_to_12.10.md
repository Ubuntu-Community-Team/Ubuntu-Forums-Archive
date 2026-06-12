---
title: "Drop of non-PAE Kernel flavour postponed to 12.10"
date: 2011-12-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2011-12-13
As this is a major source of FUD, this news might bring some inner peace to some.

> 
Chair: Martin Pitt Attendees: Kees Cook, Stephane Graber, Matt Zimmerman, Colin Watson, Soren Hansen Guests: Tim Gardner, Steve Langasek, Jonathan Carter Full log: [http://ubottu.com/meetingology/logs/ubuntu-meeting/2011/ubuntu-meeting.2011-12-12-21.01.moin.txt](http://ubottu.com/meetingology/logs/ubuntu-meeting/2011/ubuntu-meeting.2011-12-12-21.01.moin.txt)  Action review:  * pitti: document brainstorm review activity &#8594; carried over  * kees: perform brainstorm review &#8594; carried  Edubuntu LTS application  * Still blocked on Kubuntu LTS application  * [https://wiki.ubuntu.com/Edubuntu/12.04/LTS-Proposal](https://wiki.ubuntu.com/Edubuntu/12.04/LTS-Proposal) has the list of affected applications, will still be tuned a bit to drop Java dependencies**  Non-PAE kernel disposition  * Kernel team would like to drop non-PAE kernel soon  * TB members generally feel that (1) dropping the current default kernel is too much of a step, and (2) there is still a significant number of users which have non-PAE systems, based on Launchpad bug report data and an ubuntu-devel@ strawpoll  * Maintaining the extra flavour is not much extra work, and not comparable to e. g. the -ti-omap4 kernel which is an entirely separate source tree  * We need a way to prevent upgrades for non-PAE systems. Some options were mentioned:   * Add update-manager check to not offer the upgrade if PAE is not available   * Add libc6/linux preinst to abort the upgrade early if PAE is not available; that's not the best failure mode, but will prevent a safety net for users of `apt-get dist-upgrade`  * '''Agreements''':   * Switch precise over to PAE kernel by default on i386; we retain the option to revert if it causes too much fallout (Colin)   * [COLOR=Red]_Drop non-PAE flavour in 12.10; this will give non-PAE systems another 5 years of life time, which is considered enough_[/COLOR]   *** Further discuss upgrade strategy/checks  Micro release Exception for Nova, Swift, Glance, and Keystone  * [https://lists.ubuntu.com/archives/technical-board/2011-November/001142.html](https://lists.ubuntu.com/archives/technical-board/2011-November/001142.html)  * deferred to discussion by email, as we ran out of time 

---

### Post by keithpeter on 2011-12-13
Hello All

One up for Ubuntu vs Scientific Linux/CentOS 6.xx. Good decision I think.

Non pae hardware owners can now be pointed at an LTS release with support for 5 years and so well beyond the lifetime of the hardware.

PS: Centrino based laptops like the Thinkpad T40/T41/T42 were non PAE. There is quite a lot of that kit still around.

---

### Post by teh603 on 2011-12-13
So, for those of us who haven't been paying attention to the FUD, what exactly is this all about?

---

### Post by effenberg0x0 on 2011-12-13
A PC with a 32-Bit Operating System cannot use more than 3 to 4GB of RAM. Search for the "3GB Limit". Why would one want to run with more than 4GB? Many reasons. In my case: I run Windows Virtual Machines with 8GB of Virtual RAM each. So I use Ubuntu 64-bit with 16GB of RAM. I would benefit from 64 or 128 of RAM, but desktop motherboards generally have only 4 memory slots. And I don't like using server motherboards in desktops. This is just one example, other people might show you other needs. But generally, in development, you come across situations in which you need more and more RAM. Another situation is in servers - you need a lot of RAM to handle many simultaneous users and sessions.

If you want to use more than 4GB of RAM (and many of us do) you have to:

**1)** Use a 64-Bit Operating System. That's it. To use it, you need a **post-2005** (Celeron Prescott) Intel CPU or a **post-2004** (Athlon) AMD CPU.** (EDIT: **To be clear: Forget about PAE/NON-PAE. Just use the default Ubuntu)

**2)** Use **PAE** (Physical Address Extension), which is a CPU feature that allows a 32-bit CPU to handle more than 3GB of memory. But you will need all of the following: 
- A PAE-Enabled OS (that is, one with a PAE-Enabled Kernel) **EDIT:** If it is not clear, Ubuntu 32-bit **does support** PAE (automatically).
- A PAE-Enabled CPU
- A PAE-Capable Motherboard 
- A PAE-Configurable BIOS. 

This would mean a **post-1995** (Pentium-Pro) Intel CPU or a **post-1995** (Athlon) AMD CPU. **A 16-years PC.**

This is the theory. Now, in real life, few are the cases in which all these needed requirements are available to the user. Generally he has the CPU but his motherboard can't handle it. Or even if it can, the BIOS don't have a place to activate it ("Memory Hole Remapping"), etc. Large-OEM notebooks like Dell/HP, for example, are known to have very few customization options in the BIOS generally.

If they had dropped **NON-PAE Kernel** support, it would mean that people with PCs older than 16 years (...) would not be able to use newer kernels. They would not benefit from the cutting-edge of technology in their 17-years (!?) PCs. Yeah, it makes no sense. Why do they even care about newer kernel releases?

So these are the technical **facts**. Let me explain you the **FUD** now. 

Unfortunately, there are people that feel entitled to slow down technology advancement, the personal development of others and freely take charge of the time of developers, just so they can eat at McDonald 6 times a week instead of buying any PC (a used one would do) which is newer than **16 years** (14 years old would do). The more time they waste with this hardware, the transition to 64-bit will be slower. Developers will have to continue coding with memory limitations in mind, consider the 32-bit platform users, there's the need for 32-bit compatibility layers development (ia32), etc. Basically we all loose, except for this minority. 

So, in order to run lubuntu or some other lighter version of Ubuntu, to access Facebook in an almost dying-slow speed and post here that Unity is too heavy on "everyone's" hardware, they disseminated the idea that dropping **NON-PAE-Kernel** would somehow affect all users, which is simply not true. **It makes no difference at all for people with hardware newer than 16 years.** Only people that are using a 16-more year old PC as a paper-weight (because clearly no one can be using a 16-year old PC for any serious/professional use - a potato would be more productive) would be affected (they would not be able to use cutting-edge kernel releases - go figure). You can recognise people with 20-year old hardware, that do not use the PC for anything serious, by the FUD they disseminate at every thread. It has become usual at general help and even here at PP+1. People behind kernel and Ubuntu development are technical and serious. They wouldn't just make a change that affects everyone in a bad way. Every time your hear stuff like that, you know it's a lie. But sometimes new users, less experienced ones, get desperate. 

**OBS:** This is intentionally a large explanation. Hopefully other forum users will read it too, to understand what all the fuzz is about.

---

### Post by kaldor on 2011-12-13
This is a very good decision seeing as this is an LTS release.

---

### Post by teh603 on 2011-12-13
S'ok, that's the kind of explanation I've been needing.

I do actually have a 16-year old computer lying around; its an ancient Tanzania- board Mac that the parents used to use and has the only remaining copy of a certain letter to a certain person that dad needs to keep from now until the End Times. Although should he need it, we're just going to give him the computer and say "Its in here somewhere, see if you can dig it out." Its still running MacOS 8, and that's the best it'll ever run.

The oldest computer I've got that still works is only 9, but its got some kind of screwball legacy BIOS. I keep it around to show off to people how old hardware isn't totally dead. When the cutoff time comes, I guess I'll try it out and see, but I wouldn't be surprised if it wasn't PAE-compliant. Damn thing can't even boot from USB.

Guess it might be time to finally replace the old monster?

---

### Post by grahammechanical on 2011-12-13
@effenburg0x0

Thanks. Can I make just one tiny point? You write:

> If they had dropped PAE-Kernel support,

Should that not say NON PAE-Kernel support? At least it shows I was reading what you wrote carefully.

Regards.

---

### Post by jbicha on 2011-12-13
effenberg, your explanation is a bit off. PAE is automatically used if you install 32-bit Ubuntu on a system with more than 3GB of RAM. [Source]("https://help.ubuntu.com/community/EnablingPAE#Ubuntu_10.04_LTS_.28Lucid_Lynx.29").

Also, you're mixing up the question about dropping non-PAE support with dropping 32-bit support. There are still lots of netbooks being sold today with non-64-bit-capable Intel Atom chips, like this [chip]("http://ark.intel.com/products/55663/Intel-Atom-Processor-Z670-%28512K-Cache-1_50-GHz%29").

---

### Post by effenberg0x0 on 2011-12-13
> **kaldor said:**
> This is a very good decision seeing as this is an LTS release.

Why? 

> **teh603 said:**
> S'ok, that's the kind of explanation I've been needing.

I do actually have a 16-year old computer lying around; its an ancient Tanzania- board Mac that the parents used to use and has the only remaining copy of a certain letter to a certain person that dad needs to keep from now until the End Times. Although should he need it, we're just going to give him the computer and say "Its in here somewhere, see if you can dig it out." Its still running MacOS 8, and that's the best it'll ever run.

The oldest computer I've got that still works is only 9, but its got some kind of screwball legacy BIOS. I keep it around to show off to people how old hardware isn't totally dead. When the cutoff time comes, I guess I'll try it out and see, but I wouldn't be surprised if it wasn't PAE-compliant. Damn thing can't even boot from USB.

Guess it might be time to finally replace the old monster?

I like old PCs. I have an old XT stuck somewhere. It's great to collect old IT, of course, since it has a special meaning to us. Your 9-year PC most likely has a PAE-Capable CPU, but as I said, it's a lottery to  also have a motherboard and a BIOS that can handle it. I had that luck only once. Maybe you're luckier than me :)

> **grahammechanical said:**
> @effenburg0x0

Thanks. Can I make just one tiny point? You write:
Should that not say NON PAE-Kernel support? At least it shows I was reading what you wrote carefully.
Regards.
You're absolutely right, I was multitasking heavily when typing that. It was a mistake. Thanks for pointing out :)

> **jbicha said:**
> effenberg, your explanation is a bit off. PAE is automatically used if you install 32-bit Ubuntu on a system with more than 3GB of RAM. [Source]("https://help.ubuntu.com/community/EnablingPAE#Ubuntu_10.04_LTS_.28Lucid_Lynx.29").
Can you please point out where I explicitly said that it didn't? I think I expressed myself badly somewhere, it was not my intention to say that if I did. I mean, of course it is activated, but only in hardware that is capable of it: CPU (newer than 16 years), MB and BIOS. We bought 200 Dell notebooks and guess what, none of them supports PAE (BIOS/MB). So we had to install 64-bit OS to use the RAM (6GB). That's my point: Although we have kernel and CPU support, MB/BIOS matching the hardware is lottery.  

> **jbicha said:**
> 
Also, you're mixing up the question about dropping non-PAE support with dropping 32-bit support. There are still lots of netbooks being sold today with non-64-bit-capable Intel Atom chips, like this [chip]("http://ark.intel.com/products/55663/Intel-Atom-Processor-Z670-%28512K-Cache-1_50-GHz%29").
Hey Jbicha :) Being 100% honest with you: I just **hate** going into this sort of discussion, with links to prove points, etc. I've done that repeatedly for too many years. You probably expect me to say "Oh, ok, so show me some statistics on sales and market share of SKUs with no 64 support", and the thing goes on and on. This is lame and I really don't enjoy it. So, please don't take that bad but I'm going to respectfully avoid it, ok? But, for all effects, I'm wrong and you're absolutely right when you say that this particular SKU has no support for Intel64. If you feel like it, please fix/remove my OP to match the information you have as correct. Thanks.

---

### Post by teh603 on 2011-12-14
> **effenberg0x0 said:**
> Can you please point out where I explicitly said that it didn't? I think I expressed myself badly somewhere, it was not my intention to say that if I did. I mean, of course it is activated, but only in hardware that is capable of it: CPU (newer than 16 years), MB and BIOS. We bought 200 Dell notebooks and guess what, none of them supports PAE (BIOS/MB). So we had to install 64-bit OS to use the RAM (6GB). That's my point: Although we have kernel and CPU support, MB/BIOS matching the hardware is lottery.Given how the hardware manufacturers are bundling 64-bit Win7 onto almost everything these days, I wouldn't be surprised if they felt that PAE was useless. After all, they only intend for it to run a 64-bit OS, so why include 32-bit compatibility layers?

I've also heard arguments that PAE is simply a kludge to prevent 64-bit systems from "properly taking over," the way a couple of the larger ISPs are rejecting IPv6.

---

### Post by keithpeter on 2011-12-14
> **effenberg0x0 said:**
> If they had dropped **NON-PAE Kernel** support, it would mean that people with PCs older than 16 years (...) would not be able to use newer kernels. They would not benefit from the cutting-edge of technology in their 17-years (!?) PCs. Yeah, it makes no sense. Why do they even care about newer kernel releases?

Hello effenberg0x0

When I booted the old reliable T42 thinkpad (about 6 years old) from a Scientific Linux 6 live CD I got the one line 'non-PAE kernel, can't boot' type error from grub. The machine has 1GB RAM. [I'm not the only one according to Google]("http://www.kernelcrash.com/blog/openvz-and-asterisk-and-pae/2009/02/03/")

What are we doing wrong?

I don't have that laptop any more but just interested.

---

### Post by effenberg0x0 on 2011-12-14
> **keithpeter said:**
> Hello effenberg0x0

When I booted the old reliable T42 thinkpad (about 6 years old) from a Scientific Linux 6 live CD I got the one line 'non-PAE kernel, can't boot' type error from grub. The machine has 1GB RAM. [I'm not the only one according to Google]("http://www.kernelcrash.com/blog/openvz-and-asterisk-and-pae/2009/02/03/")

What are we doing wrong?

I don't have that laptop any more but just interested.

It's hard to say as it seems the T42 had submodels, each with a different CPU. And I have never used Scientific Linux. So I would need more information than that to even star thinking about it. 

However, no offense (it seems you liked this PC), but I hated every minute of the couple months I had to work with one of this older Thinkpads. All I can remember are all the problems, incompatibilities and issues, everything was specific, had a catch, etc. Linux was not wonderful in 2003 as it is today, sure, but people with cheap laptops could install all of its drivers, use all its features correctly and we had like 50 IT guys that couldn't make a modem work: It was embarrassing. A friend actually put his on a bench in the subway and stood some meters away waiting for it to get stolen. 

So, if I had to bet, completely in the blind for info here, I'd guess it's more  likely that you hit some kernel release that had problems with T42 than  really a PAE/Non-PAE issue.
]

---

### Post by jbicha on 2011-12-14
> **effenberg0x0 said:**
> 
We bought 200 Dell notebooks and guess what, none of them supports PAE (BIOS/MB). So we had to install 64-bit OS to use the RAM (6GB). That's my point: Although we have kernel and CPU support, MB/BIOS matching the hardware is lottery.

There are computers than can run 64-bit but not 32-bit PAE? Wow.

> **effenberg0x0 said:**
> 
Hey Jbicha :) Being 100% honest with you: I just **hate** going into this sort of discussion, with links to prove points, etc. I've done that repeatedly for too many years. You probably expect me to say "Oh, ok, so show me some statistics on sales and market share of SKUs with no 64 support", and the thing goes on and on. This is lame and I really don't enjoy it. So, please don't take that bad but I'm going to respectfully avoid it, ok? But, for all effects, I'm wrong and you're absolutely right when you say that this particular SKU has no support for Intel64. If you feel like it, please fix/remove my OP to match the information you have as correct. Thanks.

I'm not a moderator so I can't edit posts, nor do I think it's needed here. The Intel Atom thing makes ever dropping 32-bit support a far-off dream which is too bad. :( I wasn't trying to start an argument so I'm glad you're not wanting to start one either. :)

---

### Post by dino99 on 2011-12-14
I have some old hardware too, running "-generic" kernel only and not able to use 64 bits system anyway; so i'm sure that some alternative like ppa will propose kernels compatible with these pure 32 bits machines.

---

### Post by keithpeter on 2011-12-15
> **effenberg0x0 said:**
> So, if I had to bet, completely in the blind for info here, I'd guess it's more  likely that you hit some kernel release that had problems with T42 than  really a PAE/Non-PAE issue.
]

Hello effenberg0x0

> You should be pretty safe assuming PAE for any Pentium II or Athlon or newer, although some Pentium M's (marketed as Centrino)--namely, those with a 400 MHz bus--do not support PAE.

[http://serverfault.com/questions/85980/what-processors-do-do-not-support-pae](http://serverfault.com/questions/85980/what-processors-do-do-not-support-pae)

I suspect its the Centrino chips used in the T41, T42 machines. These models are available in the UK for very cheap and make a good basic laptop as their batteries seem to hold up as well (I got nearly three hours of the old T42). 

The only point I'm making here is that the decision to put a non-PAE kernel in the LTS release means that these old doorstops can be used until they finally break.

I have a thing about not putting old laptops into the landfill, but getting them used.

---

### Post by effenberg0x0 on 2011-12-15
> **jbicha said:**
> There are computers than can run 64-bit but not 32-bit PAE? Wow.

They do boot the PAE-Kernel, but there's no way to make them see the additional RAM. If you cat cpuinfo | grep pae you see the CPU has it. But you're stuck at 3.something GB and Dell stripped BIOS doesn't have an option for it (generally should be something like "Memory Hole Remapping", but can have other names. Dell account manager never heard of PAE or any memory hole thing lol. We had to install 64-Bit because the old machines were replaced for these exactly because people demanded more RAM...
> **jbicha said:**
> 
I'm not a moderator so I can't edit posts, nor do I think it's needed here. The Intel Atom thing makes ever dropping 32-bit support a far-off dream which is too bad. :( I wasn't trying to start an argument so I'm glad you're not wanting to start one either. :)

A question: I haven't looked at the huge list of Intel/AMD cpus to see what's PAE/No-PAE 64/No-64.  But aren't this atoms with no 64-bit instr. set support targeted only at embedded platforms? I haven't seen notebooks with this atom yet (again, haven't really looked at that).

---

### Post by effenberg0x0 on 2011-12-15
> **keithpeter said:**
> Hello effenberg0x0

[http://serverfault.com/questions/85980/what-processors-do-do-not-support-pae](http://serverfault.com/questions/85980/what-processors-do-do-not-support-pae)

I suspect its the Centrino chips used in the T41, T42 machines. These models are available in the UK for very cheap and make a good basic laptop as their batteries seem to hold up as well (I got nearly three hours of the old T42). 

The only point I'm making here is that the decision to put a non-PAE kernel in the LTS release means that these old doorstops can be used until they finally break.

You're probably right. These "exceptions" in cpu lines do exist. 
> **keithpeter said:**
> 
I have a thing about not putting old laptops into the landfill, but getting them used.

Or donate them. I've seen laptops considered to be useless for corporate users get into hands of children and unprivileged ones. While more than a half will not make any proper use of the hardware (because no one teaches them what to do with it), eventually you find a guy whose life will change with the machine. I know one specific case of a person who had never used a computer and got a used one with a C2D T5670 cpu. Someone installed mIRC in the donated laptop. Somehow the guy clicked on it and started lurking on some channels. Within a year, the guy was using Cygwin/Mingw and some IDE to code C+Win32API. An amazing accomplishment for someone that had never used a touchpad in the entire life... This is the gifted and rare exception, that turns into a case, of course.

---

### Post by keithpeter on 2011-12-15
> **effenberg0x0 said:**
> Within a year, the guy was using Cygwin/Mingw and some IDE to code C+Win32API. An amazing accomplishment for someone that had never used a touchpad in the entire life... This is the gifted and rare exception, that turns into a case, of course.

That's the idea, google 'zero dollar laptop' for some further examples.

Back on thread: Ubuntu supports older hardware and increases secure access to online world to more groups in each economy. Something to shout about I think. Turn the decision to support non-PAE kernels during the first (desktop) 5 year LTS into a *positive *message.

---

### Post by teh603 on 2011-12-15
> **effenberg0x0 said:**
> A question: I haven't looked at the huge list of Intel/AMD cpus to see what's PAE/No-PAE 64/No-64.  But aren't this atoms with no 64-bit instr. set support targeted only at embedded platforms? I haven't seen notebooks with this atom yet (again, haven't really looked at that).Dell's Inspiron Duo netbooks are Atom- powered, and 64-bit. And top out at two gigs of memory, but all the 64-bit Atom processors seem to top out at two gigs.

Supposedly they're so 64- bit that some won't boot an i386 kernel. :lolflag:

---

### Post by jbicha on 2011-12-15
> **effenberg0x0 said:**
> A question: I haven't looked at the huge list of Intel/AMD cpus to see what's PAE/No-PAE 64/No-64.  But aren't this atoms with no 64-bit instr. set support targeted only at embedded platforms? I haven't seen notebooks with this atom yet (again, haven't really looked at that).

The vast majority of netbooks were running Atom chips. This year, there are 64-bit Atom in addition to the 32-bit chips; AMD Neo & Fusion chips (all of which are 64-bit); and ARM.

---

### Post by 67GTA on 2011-12-18
We have two thin clients at work that I boot my external drive (Lubuntu) on. Opensuse gives me a 'non-PAE kernel, can't boot' message now. I guess 12.04 won't work on them either then?

---

### Post by effenberg0x0 on 2011-12-18
> **67GTA said:**
> We have two thin clients at work that I boot my external drive (Lubuntu) on. Opensuse gives me a 'non-PAE kernel, can't boot' message now. I guess 12.04 won't work on them either then?

Any idea about the thin client cpu?

---

### Post by jerrylamos on 2012-01-13
non-PAE dropped already in precise pangolin 20120110.
  
CD image wouldn't boot on IBM Thinkpad T40 1.5 gHz Pentium M.  
Message said kernel wouldn't run on that pc.

The T40 has been running Unity-2D 12.04 just fine, as well as Lubuntu 12.04 both updated frequently.

I'll download today's oversized image to see if its kernel will or won't run on the T40.  The image won't fit on a CD so I'll can copy the .iso onto the T40's hard drive and boot directly off the .iso.

Jerry

---

### Post by cariboo on 2012-01-13
The non-pae kernel is still available here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2.1-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2.1-precise/)

jerrylamos, please get your facts straight, instead of creating FUD.

---

### Post by keithpeter on 2012-01-13
> **jerrylamos said:**
> non-PAE dropped already in precise pangolin 20120110.
  
CD image wouldn't boot on IBM Thinkpad T40 1.5 gHz Pentium M.  
Message said kernel wouldn't run on that pc.

The T40 has been running Unity-2D 12.04 just fine, as well as Lubuntu 12.04 both updated frequently.

I'll download today's oversized image to see if its kernel will or won't run on the T40.  The image won't fit on a CD so I'll can copy the .iso onto the T40's hard drive and boot directly off the .iso.

Jerry

Hello jerrylamos and all

That error is what I used to see when I tried to boot CentOS or Fedora on my old T42. Centrino based laptops (e.g. 'Dothian' processors) have no PAE support, see earlier in thread

Hope this is a passing packaging issue or that the non-PAE kernel will be available on alternative CD. This LTS could see that generation of laptops safely into recycling...

Edit: just seen Carribou's post, so non-PAE still available.

---

### Post by jerrylamos on 2012-01-13
> **cariboo907 said:**
> The non-pae kernel is still available here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2.1-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2.1-precise/)

jerrylamos, please get your facts straight, instead of creating FUD.

Did a zsync on today's daily build which runs O.K. on the T40.

Jerry

---

### Post by bubbajunk on 2012-02-07
> **jerrylamos said:**
> Did a zsync on today's daily build which runs O.K. on the T40.

Jerry

Jerry, I came across your post while researching why the daily build iso file of 12.04 would not boot on my Thinkpad T42. Like you, my Thinkpad has a Pentium M that does not support PAE. The Thinkpad runs 11.10 perfectly fine. I wanted to start testing 12.04, but ran into the PAE support issue. 

Sounds like you figured out how to incorporate the non-PAE kernel into the daily build iso file using zsync. I'm not familiar with this tool or how to use it. Can you help me?

Would you be able to provide some guidance on the steps you used to incorporate / zsync the non-PAE kernel from the link above into the daily build iso? Your help would be much appreciated.

---

### Post by lucazade on 2012-02-07
> **bubbajunk said:**
> Jerry, I came across your post while researching why the daily build iso file of 12.04 would not boot on my Thinkpad T42. Like you, my Thinkpad has a Pentium M that does not support PAE. The Thinkpad runs 11.10 perfectly fine. I wanted to start testing 12.04, but ran into the PAE support issue. 

Sounds like you figured out how to incorporate the non-PAE kernel into the daily build iso file using zsync. I'm not familiar with this tool or how to use it. Can you help me?

Would you be able to provide some guidance on the steps you used to incorporate / zsync the non-PAE kernel from the link above into the daily build iso? Your help would be much appreciated.

Install UCK and customize your iso adding a non-pae kernel (self compiled or from other repositories)
[http://uck.sourceforge.net/](http://uck.sourceforge.net/)

it is available in the repo and quite easy to use.. there are also other alternatives but require more work.

---

### Post by jerrylamos on 2012-02-07
bubbajunk,

I just did a zsync on today's daily build 20120207 and booted the .iso file directly from the hard drive.  This is it running on the T40.  Looking below, the kernels are stated as pae: 

lubuntu@lubuntu:~$ ls /boot
abi-3.2.0-14-generic-pae     grub            memtest86+_multiboot.bin
config-3.2.0-14-generic-pae  memtest86+.bin  System.map-3.2.0-14-generic-pae

Now this is a:
model name	: Intel(R) Pentium(R) M processor 1500MHz
running just fine.

I'll try burning a CD to see if it will boot also?

My guess, there was a bug fix on the pae which is running O.K. today.  No clue for tomorrow....

Jerry

---

### Post by xyzzyman on 2012-02-07
> **jerrylamos said:**
> bubbajunk,

I just did a zsync on today's daily build 20120207 and booted the .iso file directly from the hard drive.  This is it running on the T40.  Looking below, the kernels are stated as pae: 

lubuntu@lubuntu:~$ ls /boot
abi-3.2.0-14-generic-pae     grub            memtest86+_multiboot.bin
config-3.2.0-14-generic-pae  memtest86+.bin  System.map-3.2.0-14-generic-pae

Now this is a:
model name	: Intel(R) Pentium(R) M processor 1500MHz
running just fine.

I'll try burning a CD to see if it will boot also?

My guess, there was a bug fix on the pae which is running O.K. today.  No clue for tomorrow....

Jerry

When you do a uname -a what does it show?

---

### Post by bubbajunk on 2012-02-07
> **jerrylamos said:**
> 

I just did a zsync on today's daily build 20120207 and booted the .iso file directly from the hard drive.  This is it running on the T40.  Looking below, the kernels are stated as pae: 

lubuntu@lubuntu:~$ ls /boot
abi-3.2.0-14-generic-pae     grub            memtest86+_multiboot.bin
config-3.2.0-14-generic-pae  memtest86+.bin  System.map-3.2.0-14-generic-pae

Now this is a:
model name	: Intel(R) Pentium(R) M processor 1500MHz
running just fine.

I'll try burning a CD to see if it will boot also?

My guess, there was a bug fix on the pae which is running O.K. today.  No clue for tomorrow....

Jerry

Jerry,
I just downloaded a fresh copy of today's daily build. I flashed to a USB and tried to boot. I received the same error as before about the cpu not supporting the kernel. I downloaded from the following link: [http://cdimage.ubuntu.com/daily-live/20120207/precise-desktop-i386.iso](http://cdimage.ubuntu.com/daily-live/20120207/precise-desktop-i386.iso)

I'm not sure what you are doing differently than me, but somehow we are getting different results. You stated that you are able to boot from the the iso on your hard drive. I've never done that. I've always burned the iso to a disc or flashed to a USB. Have you tried burning the iso to a cd and booting? I'm booting from the USB drive I created using UNetbootin and the fresh iso I downloaded today. 

Another thing that is different is that you indicated that you updated your iso using zsync. Can you confirm the link you are used for your original iso and the link you used for the zsync process? Did you start from a fresh download of precise-desktop-i386.iso at one point? Or did you start from an oneiric iso and update it using zsync? Or are you using the "alternate cd" build found here: [http://cdimage.ubuntu.com/daily/20120207/precise-alternate-i386.iso?](http://cdimage.ubuntu.com/daily/20120207/precise-alternate-i386.iso?)

Sorry for so many questions, but maybe I can figure out what I'm doing differently.

---

### Post by xyzzyman on 2012-02-07
> **bubbajunk said:**
> Jerry,
I just downloaded a fresh copy of today's daily build. I flashed to a USB and tried to boot. I received the same error as before about the cpu not supporting the kernel. I downloaded from the following link: [http://cdimage.ubuntu.com/daily-live/20120207/precise-desktop-i386.iso](http://cdimage.ubuntu.com/daily-live/20120207/precise-desktop-i386.iso)

I'm not sure what you are doing differently than me, but somehow we are getting different results. You stated that you are able to boot from the the iso on your hard drive. I've never done that. I've always burned the iso to a disc or flashed to a USB. Have you tried burning the iso to a cd and booting? I'm booting from the USB drive I created using UNetbootin and the fresh iso I downloaded today. 

Another thing that is different is that you indicated that you updated your iso using zsync. Can you confirm the link you are used for your original iso and the link you used for the zsync process? Did you start from a fresh download of precise-desktop-i386.iso at one point? Or did you start from an oneiric iso and update it using zsync? Or are you using the "alternate cd" build found here: [http://cdimage.ubuntu.com/daily/20120207/precise-alternate-i386.iso?](http://cdimage.ubuntu.com/daily/20120207/precise-alternate-i386.iso?)

Sorry for so many questions, but maybe I can figure out what I'm doing differently.

It may be that he used lubuntu, and you used Ubuntu. I have a feeling that lubuntu has dropped back to non-pae for their release.

---

### Post by nm_geo on 2012-02-07
> **xyzzyman said:**
> It may be that he used lubuntu, and you used Ubuntu. I have a feeling that lubuntu has dropped back to non-pae for their release.
  
I got both daily isos running live on flash drives tested today and both are PAE kernels Ubuntu and Lubuntu. Both of my regular installs are PAE kernels as well.

---

### Post by xyzzyman on 2012-02-08
> **nm_geo said:**
> I got both daily isos running live on flash drives tested today and both are PAE kernels Ubuntu and Lubuntu. Both of my regular installs are PAE kernels as well.

Just to test I'm pulling down the lubuntu daily right now, and I'll try it in a virtualbox with PAE disabled to see if it'll error.

---

### Post by prusswan on 2012-02-08
On the windows side of things, it will depend how long the flagship 32 bit product (XP) will survive, last I checked it still commands a larger share than the latest 7. Actually most users don't need a 64 bit setup, and their 32 bit hardware might not be that old (it is "new" but just doesn't support 64 bit) so PAE will come in handy. That said I don't feel those who have no need for PAE should be compelled to upgrade, the PAE thing is just a bonus when it comes to common usage.

---

