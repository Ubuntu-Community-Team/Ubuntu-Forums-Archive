---
title: "How do Linux users deal with Windows preinstalled on preferred laptops"
date: 2022-12-12
forum: Ubuntu, Linux and OS Chat
---

### Post by smith73 on 2022-12-12
I am searching for a new Lenovo Thinkpad laptop and it's very difficult to find them supplied
without Windows 10-11 preinstalled. On my current laptop I use Ubuntu and so far
there wasn't any urgent need in Windows on bare metal and semiconductors, except 
for recovering ntfs file system on my portable hard drive.
I have a Windows 8 installed on a Linux Oracle virtual machine and used it for some 
minor tasks.

Now there are options, when a good Thinkpad laptop, new or refurbished,
comes only with Windows preinstalled and I was thinking about installing
Ubuntu in dual boot. But then there would be some hustle with partitioning,
if I do not use Windows too much and much space under it will stay unused.
Or if something goes wrong on a 1TB SSD in Windows in dual boot, like:

> Please note that in the following circumstances the Ubuntu 22.04  installation option &#8220;Install Ubuntu alongside Windows 10&#8221; may be  missing, if your Windows 10 installation: **is not correctly shutdown or is hibernating**, has **corrupted partition which needs repair**, **partition has not enough free disk space left for resizing**, uses **Dynamic Disk** or the file system contains **uncontrollable file fragmentation**

[[1]("https://linuxconfig.org/how-to-install-ubuntu-22-04-alongside-windows-10")]

so that it will affect Ubuntu in dual boot.

Now I need to find enough reasons to keep Windows in dual boot, especially 
with regard to some Windows software.

I am interested in CAD software, maybe some audio, graphics processing,
various programming stuff and there is enough of it for Linux. 
[B]Are there substantial differences in results a (CAD) software for Windows
would produce that are essentially unachievable with relevant software 
for Linux?[/B]

There are mentions on google about better "user experience" on Windows, but it seems
too subjective as a variable. There also are mentions that there are better and more
games for Windows, but this conclusion seems too superficial.
[B]Is there anything a software running in Windows guest on a Linux virtual machine host 
would perform differently in comparison with the same software running on Windows using
bare metal and semiconductors?[/B]

---

### Post by TheFu on 2022-12-13
I pull the original HDD/SSD and put it on a shelf before I ever boot the system.
Then I install a new HDD/SSD and install my desired Linux.

In the old days, vendors could refuse to perform warranty work if the original OS wasn't still there, unmolested, so I got into that habit.  Since Linux needs hardly any storage - 64G SSD is more than sufficient and less than $30 these days.  Heck, I've seen a 256GB SSD for under $20 this week and 1TB for $55.  For a laptop, I just don't need/want that much storage.  

My main desktop has 40GB. It runs inside a VM for flexibility. I can put that VM onto any laptop in about 10 minutes and have "my computer" ready to go or access it over the internet (via x2go or and ssh) when I don't want to risk taking any sensitive information on travel.

---

### Post by ian-weisser on 2022-12-13
If you are as yet unsure of the software or the user experience, then  maybe you should play with WSL2 a bit, or Ubuntu in a Windows VM, until  you are satisfied.

I purchase only from vendors with a generous return policy.

I use the installer's "Try Ubuntu" environment to test ALL hardware before committing to an install: Network, printing, audio, camera. Streaming a movie covers a lot of hardware. Over both wired and wireless connections.

If the hardware fails the test, I can return it. If it passes the test, I can wipe Windows. I stopped dual-booting a decade ago when Virtual Machines became good enough and the hardware became fast enough.

---

### Post by TheFu on 2022-12-13
> **ian-weisser said:**
>  
I use the installer's "Try Ubuntu" environment to test ALL hardware before committing to an install: Network, printing, audio, camera. Streaming a movie covers a lot of hardware. Over both wired and wireless connections.
 

Lots of people, including me, have done this expecting things like networking to "just work" post-install, but been disappointed when drivers in the installation that worked, don't work, once installed.  Perhaps is was just bad luck, but it has happened to me a few times with realtek NICs.

---

### Post by zebra2 on 2022-12-13
All of my Linux software runs on both Windows and Linux.  I bought a Windows 11 system with an integrated SSD for $145 for my limited Windiws OS needs.  Dual boot misery days are over. My Linux machines are Lenovo Laptops with a Windows license.

---

### Post by TheFu on 2022-12-13
> **zebra2 said:**
>  My Linux machines are Lenovo Laptops with a Windows license.

How many Linux licenses do you have?  ;)

---

### Post by DuckHook on 2022-12-13
> **TheFu said:**
> Lots of people, including me, have done this expecting things like networking to "just work" post-install, but been disappointed when drivers in the installation that worked, don't work, once installed.  Perhaps is was just bad luck, but it has happened to me a few times with realtek NICs.
Yup. This happens for a number of reasons, but one with which I have some sympathy is that some drivers contain binary blobs that are not FOSS and would therefore taint the kernel if they were installed on bare metal. The driver is available on the LiveUSB but won't get installed for that reason.

Starting with an untainted kernel is important to many, including me, so I understand why the devs make the decisions that they do.

It does cause no end of frustration and hassle for new users though, or for those who don't care if their kernel is tainted.

---

### Post by TheFu on 2022-12-13
> **DuckHook said:**
> Yup. This happens for a number of reasons, but one with which I have some sympathy is that some drivers contain binary blobs that are not FOSS and would therefore taint the kernel if they were installed on bare metal. The driver is available on the LiveUSB but won't get installed for that reason.

I'd prefer an untainted kernel, but only if it still worked.  If I want 100% F/LOSS, then Ubuntu isn't the choice. I'd use Debian.  I'm practical.  Something that works and is consistent between the install and the installer would be better for most.  What they are doing now is a bait -n- switch.  You think your hardware is all supported, because it works pre-install, but do the install only to discover that things don't work that did before.  No bueno. Feels like a used car salesmen tactic.

---

### Post by DuckHook on 2022-12-14
Sometimes, I find that Canonical causes their users distress unintentionally and certainly not because they are trying to hoodwink them, but because they don't adequately explain the possible drawbacks. If the LiveUSB process were more sophisticated and alerted the user that proprietary drivers have been loaded and these won't be loaded on a default install, then it would alleviate some misunderstanding.

I suspect that the reason for such lapses is the limited resources that Canonical has. Microsoft's catering budget alone probably exceeds Canonical's entire operating budget.

---

### Post by zebra2 on 2022-12-14
> **TheFu said:**
> How many Linux licenses do you have?  ;)


Haven't actually identified a Linux license yet but I know that there is a implied condition of use involved. I do have Linux software with a proprietary license.  Software that I purchased and have a registration code. Actually, If I like something and have a day to day need for it I don't mind paying for someone  else's product. 

Regarding the Windows license's I have always registered them on my MS account even if I didn't need the installed OS.

---

### Post by Tadaen_Sylvermane on 2022-12-14
> **DuckHook said:**
> Sometimes, I find that Canonical causes their users distress unintentionally and certainly not because they are trying to hoodwink them, but because they don't adequately explain the possible drawbacks. If the LiveUSB process were more sophisticated and alerted the user that proprietary drivers have been loaded and these won't be loaded on a default install, then it would alleviate some misunderstanding.

I suspect that the reason for such lapses is the limited resources that Canonical has. Microsoft's catering budget alone probably exceeds Canonical's entire operating budget.

I don't understand the dislike of closed source. I prefer open yes. But it's near impossible to buy open hardware. How can people worry about the software so much when the hardware is 99.9% likely to have closed stuff in it. Then you are just buying something so you can only use 50% of it. 
The average person these days doesn't give a damn about open / closed. All that matters is can they do their email and facebook. Maybe do some libreoffice stuff. You need to be educated to know the difference and it isn't worth most folks time I imagine.

---

### Post by DuckHook on 2022-12-14
> **Tadaen_Sylvermane said:**
> I don't understand the dislike of closed source.
Maybe my paranoia is rising to the top again, but the short answer to your observation is:

I don't trust it.

In the same way that I don't trust Star Chambers, or Closed Courts, or Secret Societies. In my experience, opacity nurtures scoundrels whereas transparency promotes honesty and integrity.

I'm not saying that all closed source is bad or malicious. But we can't tell, can we, and that's the problem.

The FOSS movement is often criticized, perhaps deservedly, as being tedious, idealistic, condescending and unrealistic. But what is lost in such criticism is recognition that there is also a practical side to FOSS: when a bright light is shone on code, the cockroaches scurry off to the shadows. I would add that those shadows are invariably closed source.

The fact that HW is almost all closed source may be a reality, but that doesn't mean we should resign ourselves to things getting even worse. If I can keep my SW FOSS, then at least I'm defending the fort.

---

### Post by TheFu on 2022-12-14
> **zebra2 said:**
>  Regarding the Windows license's I have always registered them on my MS account even if I didn't need the installed OS.

When MS tried to get people to MS accounts, I ran away and haven't returned.  Sure, I could give them a new, only-MSFT, email address, but I shouldn't have to.  I'll never use their cloudy stuff, having been burned far too many times by that company over the decades.  People have short memories.  Look, Squirrel!

I worked for over a decade being paid for my software. None was open source. Half was under ITAR export control.  Very few people have the skills to review software for bugs, much less security issues.  The expertise needed is usually specific to a program.

Most people just want code that works and doesn't cost too much.  The great thing about F/LOSS is that even if I don't have the expertise, I can hire someone else to make changes ... either within the project team or by forking.  

That's a huge deal for corporations where it is less about the price and more about the capability needed to make their processes more efficient.  I've seen companies pay $500K for an interface to be added to a single software product, then pay 15% of that annually to "maintain" the interface (i.e., keep it working).  When an interface can save 25K employees 10 minutes an hour, almost any price is a bargain for the added efficiency.  Watch a UPS driver some time.  Every little detail they do has been trained to be optimized from the daily route they drive to how they handle the vehicle keys when they are delivering.

Typical SW annual maintenance costs make the Apple and Google app store 30% overhead charges seem like robbery in comparison.

---

### Post by smith73 on 2022-12-14
There were 2 cases when I urgently needed Windows on bare semiconductors:
1) to repair an ntfs file system on a portable ssd
2) to run an Epson scanner driver, as Epson provided only an app for WIndows, and 
Windows VM guest on an Ubuntu host didn't recognize the scanner via USB.

But now it seems actually not so bad to have a Windows license key installed on a
laptop hardware and run Ubuntu or dual boot on it, as it's just a string of numbers
and maybe letters.

[B]Can someone recommend which Thinkpad is better - T470-80 series or
a newer E14-15 series (or L)? [/B](apart from CPU and its cores)
I read in several reviews that battery life in E series is worse than in T series,
and the modifications in casing material in E series do not provide any essential
 improvements in durability.

It seems rather idiotic from a laptop manufacturer to make users chase any new 
release and swap their laptops every 2 years.

---

### Post by TheFu on 2022-12-14
What is "better" is highly subjective.  You need to make a priority list of what is important to you.
For example, I didn't care about laptop battery life before 2012.  I'd never use a laptop that wasn't plugged in for more than a few minutes before that time, so it didn't matter.  Then life changed and I'd find myself in a shared space, working for hours, without access to power.  Still, the battery life didn't need to be 10+ hours.  To me, the screen size and weight top the list.  Next is having a good keyboard, then CPU and RAM, finally external connectors (USB3 and USB-c).  An SDHC/microSD slot is nice, but not mandatory.

An external HDMI connector is required. It can be microHDMI. When doing presentations, HDMI projectors are the standard IME.

I don't really care about great wifi. It isn't important to me. Most of the time, it will be using a USB-to-GigE ethernet plug.

I need 8G or more RAM.  4G isn't enough. I've had laptops with 2G and 4G of RAM and had to compromise too much.  4000+ passmarks for CPU performance. I'd like to be able to run a few virtual machines.

I don't game, so I prefer the integrated GPU and don't want an added GPU that just eats power.
For years, Intel laptops handled sipping battery better than AMD, so only Intel-based laptops were considered.  I don't know if that is still the situation or not.

See how that story leads to pick a laptop?  What's your story? What's important to you?

---

### Post by SeijiSensei on 2022-12-14
I recently bought a Dell laptop with Windows 11 preinstalled.

In Windows, I resized the Windows partition to about half its original size. Then I created a new partition in the freed-up space and installed Kubuntu 22.04 from a USB stick there. I don't often using dual booting and prefer VMs. On Windows I have a VirtualBox VM that runs 22.04, and on Linux I have a KVM that runs Windows 11.

---

### Post by zebra2 on 2022-12-14
> **TheFu said:**
> When MS tried to get people to MS accounts, I ran away and haven't returned.  Sure, I could give them a new, only-MSFT, email address, but I shouldn't have to. 

The reason I register my Windows license(s) is because an unregistered license can be activated by anyone.  I had that happen and I lost my ability to install Windows on one of my laptops. If the license is activated it can't be stolen. It is just good sense.  I agree though with the multi email address thing. I have a few of them with MS.

---

### Post by DuckHook on 2022-12-14
> **TheFu said:**
> When MS tried to get people to MS accounts, I ran away and haven't returned.  Sure, I could give them a new, only-MSFT, email address, but I shouldn't have to.  I'll never use their cloudy stuff, having been burned far too many times by that company over the decades.  People have short memories.  Look, Squirrel!
It's the lack of choice that bothers me. After installing W10 in a VM, I expected W11 to go pretty much the same way. I understood that I would have to install TPM as a virtual device, but I was already resigned to that. However, I was surprised and dismayed when the install process hung at the network stage. It insists on the user connecting to a Microsoft account. If you don't have one, you *have* to create one. Big Brother, anyone?

I tried to work around this by disconnecting the virtual NIC, but the install process would just choke and refuse to go any further.

Those who are technically knowledgeable can bypass this requirement by invoking a power shell, setting a register entry, then rebooting, but this is well beyond the scope of the average user's abilities. So, in essence, users have no choice but to be herded into the Microsoft feedlot.

This is a really really big problem. If MS were not so dominant, it wouldn't be such a problem, but it's their very dominance that makes lock&#8209;ins like this so toxic. This just shows that the leopard has not changed its spots: MS today is no different than the MS of yesteryear.

---

### Post by TheFu on 2022-12-15
At some point, I'll be forced to choose to run a newer MS-Windows version or not be able to completely my taxes without using a cloudy service.  

Hopefully, the IRS will make filing using their website directly available for non-trivial tax forms.  Last month, at least 1 popular tax software vendor here was found to be selling tax information to google and bookface without approval.  I was happy that I'd been printing my tax forms and using snail mail the last 10 yrs, even though I use their fat-program on Windows yearly.  In the 1990s, the only real competitor was caught installing root-kits with their software, so they are never going to see any of my money again.  I have a long memory.

I used to like to get the "deals" on tax software the week prior to the deadline, but can't do that anymore since I don't have a supported version of MS-Windows anymore.

I should point out that I stopped all patching of Win7 when MSFT tried to force a new EULA onto everyone.  I read the new forced agreement and decided I couldn't agree.  My Win7 VM hasn't been patched since around 2015 (I think), because accepting patches means I accept the terms of the EULA, which I do not.  Changing an agreement without approval by both sides is illegal, but I can't sue MSFT outside small claims court and only for the price of the license ... er ... which MSFT gave away (free) at the Win7 launch party. ;)  I do have a Win10 license, but it is tied to a laptop that has never booted Win10.  The HDD containing it was wiped years ago to hold something useful.  

Never forget what companies have done that you don't like. If possible, don't give them another penny. That's the only way to let them feel your displeasure with their actions.  We don't have to accept the terms offered.  It is a choice.

---

### Post by lammert-nijhof on 2022-12-15
I stopped dual booting in 2009, since that time I only run Windows in a Virtualbox VM. 
My first VM was Windows XP Home and I installed and activated it in March 2010. I still use the same VM a few times per week and it survived 3 desktops and 4 CPUs :)    I also use that XP-VM with a simple 3D CAD program Google SketchUp, I used it for 2D drawings and a kind of 3D animations of our house and that works fine.  You can turn and re-center that 3D animation. 
I also run Windows 11 Pro with a Microsoft email account, that I only use for the purpose of logging in. For true email I use other accounts, one gmail for family and friends and another hotmail for the unavoidable commercial stuff. 

Since Virtualbox 7, Virtualbox also supports IOMMU for e.g. using a 2nd physical GPU or iGPU in e.g a Windows Gaming VM. You very probably don't have a 2nd GPU, so you have to use the 3D acceleration provided by Virtualbox since many years.  That is fine for the standard Linux games like SuperTuxKart and Extreme Tux Racer.  They run at 1080p 60Hz with a 75% load on my Vega-8 iGPU in the Ryzen 3 2200G.
I also use DOSBOX to run DOS games like good old Wolfenstein-3D :)

---

### Post by smith73 on 2022-12-15
> **zebra2 said:**
> The reason I register my Windows license(s) is because an unregistered license can be activated by anyone.
But you can as well register the Windows license in the Windows virtual machine guest running on Ubuntu host?
In case the Windows initially preinstalled in a laptop should be removed.

---

### Post by TheFu on 2022-12-15
> **smith73 said:**
> But you can as well register the Windows license in the Windows virtual machine guest running on Ubuntu host?
In case the Windows initially preinstalled in a laptop should be removed.

Nobody here is **your** lawyer.  

I suspect pre-installed licenses are single install/use, directly on hardware.  Retail licenses are single install, either on hardware or in a VM, but not both.

I vaguely remember reading that MSFT would sell VM-only licenses.

---

### Post by smith73 on 2022-12-15
> **TheFu said:**
> What's important to you?

Previously I thought that the full price of Windows was included in the final price of a laptop and it seemed sort of not suitable, if I am not a Windows user.
Then several vendors told, that for laptop manufacturers a Windows costs ~5-10$ per laptop and essentially does not affect the final price.

Right now I'm like 98% oriented towards Thinkpad E14 gen2 AMD Ryzen3 4300U 4 cores (1, 2) due to backlit keyboard, aluminum casing (sort of mil-tested), IPS
FHD display (which I hope to have at least 250 nits of brightness), no PWM flickering and USB-C charging port. 16GB RAM and 512gb or 1T SSD.

For the following months I may not need heavy use of battery alone, but I'd like to take preemptive measure to ensure good power supply.
I asked at the local electronics store and they told that if a laptop supports charging via USB-C port, a LiPo external powerbank (30000mAh 65W with
 PD3.0 QC3.0 4xUSB + USB C) BASEUS can be use for rechargeable power delivery. And it costs basically the same as an external battery for older
Thinkpad series T470 or so (~90euros).

I am basically planning to undertake various programming stuff, but would like to also try Blender Python CLI, as well as try some CAD and 3d modelling software
for Windows, as the laptops comes with WIndows - beginner to intermediate level. But now I see that Blender requires 2GB GPU, and this E14 has shared (dynamic) memory
for graphics. Also I'd like to try various ML stuff on it, and don't know in advance how compute intensive they will be. Can you advise whether the integrated 
graphics card with shared dynamic memory can be sufficient at16GB RAM for this kind of tasks (beginner to intermediate level)?

[[1]("https://psref.lenovo.com/syspool/Sys/PDF/ThinkPad/ThinkPad_E14_Gen_2_AMD/ThinkPad_E14_Gen_2_AMD_Spec.PDF")], [[2]("https://psref.lenovo.com/syspool/Sys/PDF/datasheet/ThinkPad_E14_Gen_2_(AMD)_datasheet_EN.pdf")]

There is another version of E15 with Dos, but there  may be no backlit keyboard, and if I place the luminescent keyboard stickers, I suppose the light they'd
be constantly emitting may in the ling run damage the screen with the lid closed.

---

### Post by TheFu on 2022-12-15
Blacklit keys aren't need after you learn to touch type.  Spend 2 weeks, practicing for 1 hr a day and you'll never need blacklit keys again. There are lots of free typing trainers. ... or be limited over something frivolous, IMHO, the rest of your life.  I have a blacklit mechanical keyboard. I didn't want it, but find the lights too bright when I'm working, even turned all the way down.

For CAD and other engineering things, you'll want a better CPU and more RAM.  For CAD, you'll probably want a CAD-specific GPU too.  Gaming GPUs and CAD GPUs are different animals.  [https://www.nvidia.com/en-us/drivers/graphics-for-solidworks/](https://www.nvidia.com/en-us/drivers/graphics-for-solidworks/) is an example. Typically, I wanted to see "Quadro" in the GPU name last time I looked.  [https://www.nvidia.com/en-us/studio/compare-gpus/](https://www.nvidia.com/en-us/studio/compare-gpus/)  has the new models and which workloads they are designed to handle.  Looks like only workstation GPUs are for 4K resolutions, not laptops.

I've never used a laptop for anything "serious", expect remote access into real computers that have real power or for webapp programming, which I did on a 2GB RAM chromebook just fine.  I wasn't doing Java.  Java programmers, especially if they are building GUIs or Android, know that 64GB and a fast Core i9 isn't enough. That's the curse of Java. Most other general purpose languages don't need much.  When I was coding those web apps, there were times I had to compromise.  A few years later, I replaced that chromebook with a much, much, nicer chromebook that was 2x the price, faster CPU, more RAM (4G), higher resolution screen, longer battery life AND lighter.  I'd still be using it today, had the keyboard not worn out and replacement been as costly as the machine was worth.  The next laptop was over $100 less, but had 2x the CPU, 2x the RAM, 2x the storage and retained 1080p and 10hrs of battery. It was much heavier and had a larger screen, which I found cumbersome. After 3 yrs, the keyboard wore out on that box too and again, it would cost more to replace than the laptop value.  I've been without a real laptop for a few years, but with COVID, it hasn't been any issue.  

I won't ever think that any laptop can be a desktop replacement.  Laptops are so limiting and expensive when compared to well-selected desktops, even boot-box sized "desktops" are a deal.  Going much smaller and prices rise again as flexibility is lost.  It is amazing what $300 in a desktop can get these days using a microATX motherboard and $110 CPU/GPU/APU.  Saw one with nearly 20,000 passmarks last week for that price.  I think the best compromise is to get a cheap, used, laptop and build a power-house desktop.  Both can be had for less than an average laptop price, assuming you don't go crazy on the GPU.  Ah ... but you need a good workstation GPU.  IDK what you should do, just know that a GPU like that will cut the battery from 10 hrs to 2 hrs. That's the trade-off.

Having reasonable expectations is the starting point to avoid disappointment.  If you are buying professional software, you'll want hardware to go with that software.  If you are going with F/LOSS, only you can try it, see what it can and cannot do, then decide if that is sufficient for YOUR expectations.

---

### Post by smith73 on 2022-12-15
> **TheFu said:**
> Blacklit keys aren't need after you learn to touch type.  Spend 2 weeks, practicing for 1 hr a day and you'll never need blacklit keys again.

That's a good idea. Though I can imagine some situations when I may not want to maintain the necessary muscle tone for such muscle memory. 2 weeks of training would be good a month ago, and now I hope to get some black Friday discounts, even if none, I may buy it with 1T ssd and backlit keys just because I am already tired to spend whole days in reading reviews and specs. Ideally a red kb backlight would be better for eyehealth than just white led, I saw it on some more expensive gaming Lenovo laptops. 

> **TheFu said:**
> For CAD and other engineering things, you'll want a better CPU and more RAM.  For CAD, you'll probably want a CAD-specific GPU too.  Gaming GPUs and CAD GPUs are different animals.  [https://www.nvidia.com/en-us/drivers/graphics-for-solidworks/](https://www.nvidia.com/en-us/drivers/graphics-for-solidworks/) is an example. Typically, I wanted to see "Quadro" in the GPU name last time I looked.  [https://www.nvidia.com/en-us/studio/compare-gpus/](https://www.nvidia.com/en-us/studio/compare-gpus/)  has the new models and which workloads they are designed to handle.

The highest available option for this E14 thinkpad is 16GB RAM and 1T SSD, and it has integrated AMD Radeon Graphics with DirectX® 12 with shared (dynamic) memory. Wouldn't
16GB RAM be suitable for beginner level to just try out the Blender Python CLI (and maybe load it with external Python libraries)?  Though for Blender some site on google recommends "Graphics card: Any GPU card operating on OpenGL 3.3 GPU with 2 GB RAM", apart from 8 GB RAM. And IT SSD can also provide enough space for virtual memory.

> **TheFu said:**
> Having reasonable expectations is the starting point to avoid disappointment.  If you are buying professional software, you'll want hardware to go with that software.  If you are going with F/LOSS, only you can try it, see what it can and cannot do, then decide if that is sufficient for YOUR expectations.

I definitely won't be buying all professional software, and especially the one for Windows, to just try it out and learn to use it. I audited some courses on Pluralsight about 3D and
engineering type modelling during their free weeks, and apart from Blender they seem to use all proprietary software, like AutoCAD and others. That's one of somewhat artificial reasons for me to leave Windows in dual boot. Though of course while successfully enough running Ubuntu for years I'd first try using FreeCAD and Blender etc. 
[SIZE=1]It seems that comparing their functionality [SIZE=1]and reverse engineering[/SIZE] of GUI btw closed and open source is a good task for ChatGPT, as this ML already can write Linux kernels and OSes on integrated VMs and React apps for some users.[/SIZE]

It seems that I don't have some special expectations, as I just want to learn new software, and if it computes just slower on a non-dedicated vRAM GPU, that's ok, 
I'd be grateful if it works at all on such thinkpad.

---

### Post by DuckHook on 2022-12-15
> **TheFu said:**
> At some point, I'll be forced to choose to run a newer MS-Windows version or not be able to completely my taxes without using a cloudy service…We don't have to accept the terms offered.  It is a choice.
I agree with most everything you've said, but not this.

As a Linux enthusiast, I get what you are saying, but in the larger picture, it's not a choice. I get this excuse from a lot of my friends and family who think I'm too hard on the proprietary jailware vendors and it drives me nuts: "you don't have to use Windows, you know…"

We are *forced* to use MS—if not directly, then indirectly—every time we (among so many other things) do our banking, go to our doctor, file our taxes or service our car. All of these services can operate only by running Windows. It is ubiquitous, unavoidable and so deeply ingrained in our modern lives that it is in every sense a utility: like electricity, running water and the sewer system.

Anyone who tells me that I have a choice to not use Windows may as well say that I have a choice to not use electricity, clean water or sanitation services. There is no choice in the matter—not in the real world anyway—and this is the reason that MS cannot be treated as "just another company". They cannot be allowed to leverage their dominance to further diminish our lives. They wanted this dominance: well, they got it (in highly unsavoury ways I might add); but one of the consequences of attaining such dominance must be a commensurate restriction on their ability to exploit us.

Because we recognize the importance of this principle, we impose such restrictions on all the basic utilities: electricity, natural gas and telecoms, but, for crazy reasons, we don't impose such restrictions on Microsoft. It's nuts.

---

### Post by grahammechanical on 2022-12-15
Give Microsoft some credit. If it was not for Windows becoming bloated with code over time and every new version of Windows requiring ever more powerful hardware we would all still be running machines barely capable of running a command line OS. Microsoft Windows and computer games created a consumer demand for ever more powerful hardware. Or, is that a conspiracy theory put about by the hardware manufacturers to hide their planned obsolescence sale module? :)

Regards

---

### Post by TheFu on 2022-12-15
I had X/Windows running under Linux in 1994 on a i486/33 w/8MB of RAM.  X/Windows is painful over 14.4Kbps dialup. ;)

Had a grayscale SPARC with just 16MB of RAM around that time at work, until my Alpha workstation (64-bit in 1994!) arrived.

---

