---
title: "Booting Ubuntu in five seconds"
date: 2008-09-26
forum: Ubuntu Brainstorm
---

### Post by gny on 2008-09-26
Ok, I know that the link is subscribers only content, so sorry about that.

"At the Linux Plumbers Conference Thursday, Arjan van de Ven, Linux developer at Intel and author of PowerTOP, and Auke Kok, another Linux developer at Intel's Open Source Technology Center, demonstrated a Linux system booting in five seconds. The hardware was an Asus EEE PC, which has solid-state storage, and the two developers beat the five second mark with two software loads: one modified Fedora and one modified Moblin. They had to hold up the EEE PC for the audience, since the time required to finish booting was less than the time needed for the projector to sync."

[http://lwn.net/Articles/299483/](http://lwn.net/Articles/299483/)


So it can be done!

No more "But we boot faster then Windows so why bother" crap. Now we know that it can be done. So what are we going to do about it?

(Actually I have no idea what I could do about it, I am not that good.)

I for one would like to be a proud owner of a laptop booting in 5 seconds. Who needs power suspend or hibernate then?

---

### Post by GeneralZod on 2008-09-26
Maybe this is made clear in the subscribers-only portion of the text, but are these "linux systems" booting to GUIs, or just to command prompts?

---

### Post by UbuWu on 2008-09-26
This will be a focus of the next Ubuntu release, Jaunty. Several Ubuntu developers also attended that talk. It will never be 5 seconds though, because they also skipped things like new hardware detection.

---

### Post by gny on 2008-09-26
They booted in to xfce but skipped gdm.
And yes, they have disabled a few things as hotplug and udev.

So maybe 5 seconds is a bit far fetched with a more "normal" setup, but it proves that great things can be done for boot speed. If my laptop booted in say 10 ~ 15 seconds that would be totally freaking awesome.

---

### Post by gnomeuser on 2008-09-27
> **GeneralZod said:**
> Maybe this is made clear in the subscribers-only portion of the text, but are these "linux systems" booting to GUIs, or just to command prompts?

The modified readahead in a special way, did their own custom kernel without initrd, removed services like avahi and cups (so no printing support - not critical we can start it on demand later but that would really be cheating). The kernel itself boots in 1 sec on the machine in question, ½ a second with current upstream kernel due to a bugfix in the USB stack.

It's a scraped experience but not by much, however rejoice many of the easy changes are already in Fedora and Ubuntu following a little hackfest after the talk. There are also some additional improvements on going in terms of cleverly reading from ext3/4 filesystems. All in all we should be able to boot a standard distribution much faster than we do, it does require some hard decisions though.

This work is sexy, it's bold, but ultimately it's most useful for embedded devices, netbooks and the likes. For a full desktop you need it to be supportable, you need wide hardware support, you want good defaults - it's not to say we can't do vastly better than we currently do.

Now playing devil advocate, on a desktop setup, single user. If you are going to do autologin, would it not be a better idea to focus on making suspend to ram (or something akin to Vista' Hybrid suspend) work better. What way not only do you get startup in seconds but you also gain the ability to return directly to the place where you left off instead of the clean sheet state of a cold boot.

Don't get me wrong, I believe we shold do both but I see the second as more useful for your average user.

---

### Post by gny on 2008-09-27
I agree. My desktop is most of the time happily humming away watts quietly playing music anyway. So, no I don't "really" need the insane boot speed on that one, but then I didn't "really" need a bigger monitor either. ;)

I only really "suffer" from the booting speed when I am booting my laptop away from home. I don't suspend to ram much, I never know how long I will leave it in that state and don't want to drain batteries. And I am seeing forward to all the OOoohs and AAaaaahs when people see the INSANEOORZ boot speed of my SUPERIORZ OS :) hehe

It's great news that people are working on it. They all have my big thanks for their effort. I would liked to have been there at the presentation with all that great people with big sexy brains. mmmmmmmm ... braiiiiiins.

Is there some forum or mailing list where people are discussing this? It would be fun and interesting to read about the progress.

---

### Post by gny on 2008-09-27
Oh, I forgot. Will we see some of this changes in time for Intrepid, or is that impossible due to the code freeze?

---

### Post by UbuWu on 2008-09-27
Most of it will happen in Jaunty. One small improvement that was already made a few days ago was the way modprobe was compiled, making it much slower on Ubuntu than other distro's like Fedora. But this saves at most some seconds.

---

### Post by gnomeuser on 2008-09-27
> **gny said:**
> Oh, I forgot. Will we see some of this changes in time for Intrepid, or is that impossible due to the code freeze?

Some of the work has come for free with kernel 2.6.27 and some easy changes like modprobe optimization you will get in Intrepid, other stuff requires more intrusive work and you are unlikely to see it before Jaunty and beyond.

This is an active area of research, you should expect improvements in the coming cycles as work consolidates upstream. There are efforts e.g. to wind down the many early userspace solutions to just one, which will make optimization easy. The same with udev rules and certain other areas. 

Another thing we might see is an option to enable bootchart with automated data collection by default in the development cycle. That would give developers a means to get massive direct feedback on a number of different configurations, thus giving us a way to spot regressions quickly.

As the wise Fredrico says, to fix a performance issue, one must first know there is a performance issue so metrics will be very helpful in identifying bottlenecks and areas upon which to focus.

---

### Post by sdowney717 on 2008-09-29
it should be able to boot fast.
It should be off, not using any power when not being used.
This is very green.
It could be done with a suspended image to non volatile ram.
Which when starting up again, the image is simply there.

At least once it is all configured most users wont be needing to re auto detect hardware every time it comes on.

I can imagine this could be done. I can also imagine it could cause problems.

---

### Post by signifer123 on 2008-09-29
> **sdowney717 said:**
> it should be able to boot fast.
It should be off, not using any power when not being used.
This is very green.
It could be done with a suspended image to non volatile ram.
Which when starting up again, the image is simply there.

At least once it is all configured most users wont be needing to re auto detect hardware every time it comes on.

I can imagine this could be done. I can also imagine it could cause problems.

I think most people here have volatile ram though.

So suspend to disk would be more useful. As harddisks and flash memory are non volatile. 
At least until NVRAM balances out it's speed and cost to match that of volatile RAM.

---

### Post by sdowney717 on 2008-09-29
I bet the future is headed towards non voltile ram.
Think of the energy saving, machines would simply go off, use zero power and instantly restart.
This energy saving would add up to a lot of power if all computers did this.

---

### Post by forger on 2008-09-29
> **gny said:**
> Now we know that it can be done. So what are we going to do about it?

(Actually I have no idea what I could do about it, I am not that good.)

I for one would like to be a proud owner of a laptop booting in 5 seconds. Who needs power suspend or hibernate then?

As they said, it's modified and especially made for eee pc.
Ubuntu is made to be an all-around desktop solution, not a slimmed-down per-user-and-per-computer-that-needs-two-drivers solution.
No one stops *you* from slimming down and removing any unnecessary parts/drivers/kernel modules :)

---

### Post by gnomeuser on 2008-09-29
> **sdowney717 said:**
> it should be able to boot fast.
It should be off, not using any power when not being used.
This is very green.
It could be done with a suspended image to non volatile ram.
Which when starting up again, the image is simply there.

At least once it is all configured most users wont be needing to re auto detect hardware every time it comes on.

I can imagine this could be done. I can also imagine it could cause problems.


[If only the whole suspend to disk thing wasn't terminally broken by design](http://mirror.linux.org.au/pub/linux.conf.au/2008/Fri/mel8-139.ogg) (links to huge ogg theora - you are warned).

Yes if magically we could get non volatile sources like flash that were fast and didn't burn out in a year of this kind of use then that would be a fine solution. 

I imagine we can do a kind of suspend that would quickly suspend while idle for more than 100ms or so, then resume. The OLPC XO machine does something like this. You could also do a hybrid suspend where if you have been suspend for a long time, you write out to disk and thus use no power what so ever. All of this is being worked on, but it is a huge job.

Fast booting does not grant the same things a resume does, e.g. with a fast boot I don't get my machine back in the exact state I was in when I left it. They are two different things entirely.

---

### Post by UbuWu on 2008-09-29
Here is an interesting blog post about what things Mandriva did to decrease the boot time:

[http://blog.crozat.net/2008/09/improving-boot-time-on-general-linux.html](http://blog.crozat.net/2008/09/improving-boot-time-on-general-linux.html)

(It is hard to tell which things apply to Ubuntu as well, it is quite technical)

---

### Post by Ub1476 on 2008-10-02
My laptop boots in something between 20-25 seconds from the entire begining to a complete Gnome desktop. I can imagine it being faster though, as I use a SSD and the new Centrino 2 proccesor. I'm hopeing the Jaunty release will be laptops users paradice. :D

---

### Post by GSMX on 2008-10-03
My laptop boots in 61 seconds to GDM, which I think is too damn long... I have tried all available tips on The Internets to speed it up, but it's just not working... 5 seconds boottime would be freakin' awesome!!! I know they have some shortcuts, but I don't bother most of them ( how often would hardware of a laptop change??? )

---

### Post by gnomeuser on 2008-10-03
> **GSMX said:**
> My laptop boots in 61 seconds to GDM, which I think is too damn long... I have tried all available tips on The Internets to speed it up, but it's just not working... 5 seconds boottime would be freakin' awesome!!! I know they have some shortcuts, but I don't bother most of them ( how often would hardware of a laptop change??? )

They killed some rather useful things.. I would be rather upset if I couldn't print (cups is one of things that had to go). 

We can do better but in the end we will have to offer a full experience, this doesn't not. Finding ways to be fast and have all the functionality required by our users is a compromise (certain things just can't be made fast and we already agreed that deferring work was cheating).

Aside that this was done on SSD, a regular hd will be much slower for this purpose. We will not see Ubuntu boot in 5 secs for all users, we probably won't see it for most people but we can make things a lot faster. What we need to do is set a limit like Arjan did of 5 secs but maybe say 20 secs from grub to complete autologin in GNOME on regular hardware. That would be a reasonable start.

---

### Post by gnomeuser on 2008-10-03
Here's a video demoing it for those interested
[http://www.youtube.com/watch?v=s7NxCM8ryF8](http://www.youtube.com/watch?v=s7NxCM8ryF8)

---

### Post by UbuWu on 2008-10-03
> **gnomeuser said:**
> They killed some rather useful things.. I would be rather upset if I couldn't print (cups is one of things that had to go).

A big part of it could probably be loaded on demand only when a document is printed or only when a printer is detected. Not so long ago hplip was started at every boot and now it is only used when something is printed to a hp printer.

---

### Post by olskar on 2008-10-03
Of course I do appreciate a fastbooting system but I certainly can spend some 15 more seconds to have a better/faster/more stable system when it is started.

---

### Post by gnomeuser on 2008-10-03
> **UbuWu said:**
> A big part of it could probably be loaded on demand only when a document is printed or only when a printer is detected. Not so long ago hplip was started at every boot and now it is only used when something is printed to a hp printer.

And how then do you propose that we detect networked printers. For this we currently need cups running (one could conceive avahi bringing it that up when needed but.. avahi was removed as well).

The world is not so simple as to let us rely on plugging in new hardware and having it detected in this networked world.

Another case might be bluetooth, you need to run the service, you can't detect a bluetooth device without it, without that detection no pairing. Without pairing no joy and I for one really want to sync my phone with my laptop. Sure we can check for bluetooth support in the machine or react to hardware being plugged in but then how do we determine when to start the service.. at boot, at the user session (and btw. how does this differ from defering work which was already established as cheating).

There are many cases where we need this kind of thing, removing support removes functionality that is needed. We can be smarter about enabling support only on machines that have the hardware or when the hardware is plugged in but there will always be cases we can't handle like this.

---

### Post by KimmoHop on 2008-10-08
If fast booting does not make system slower, why not implement it? Not everyone boots every year, some boot few times a day.

I think that the problem is two-folded:
1. Optimization that works for all users, like readahead and not scanning hardware in every boot. In my opinion, how convenient detecting new HW is, in most cases it can be started manually after changing HW configuration. If the boot is stuck (HW for a driver not found), scanning or probing can be started. It's the same as with my FAT32 and NTFS partitions, I don't want linux to scan those every N boots :)

2. Optimization that is user and/or HW dependant (and user initiated), like compiling (possibly automatically without guesswork) all and only needed drivers in kernel and deciding what services to use. With services I don't mean individual daemons, but higher-level systems. If there are no network printers, then CUPS can be started when printing is needed, if there are no shared resources, those need not be started.

I remember once compiling my own kernel, and boy, did I know what I should select and what not! (Also I may have compiled uCLinux kernel for Motorola Coldfire, but that was luckily preconfigured and I didn't have to guess) That process really could benefit probing HW and selecting what drivers are needed. Sorry if such mechanism already exists.
 

What I'm saying (in 5 seconds, can you?) is: Fast universal Ubuntu, optimized for my HW in no time.

I have tried MachBoot (not for me), and it was up in impressive 9 seconds from CD. 10-15 seconds for Ubuntu is OK from HD. Actually 8.04 boots to usable state way faster than my XP (maybe it's time for reformat and reinstall) on my XP2100 processor.
Yes, we use XP too, that's why boot time has meaning to me :) Maybe I'll get rid of it someday (when printing is as good and Wine runs Incredimail...) or run it virtually inside linux.

I could also use 5 second linux with just firefox and multimediaplayers, but BIOS and GRUB would make blow it. Maybe I'll get Asus ExpressGate motherboard someday ;)

Sorry for long first post,
BR, Kimmo:)

---

### Post by michaeljt on 2008-10-17
> **KimmoHop said:**
> 2. Optimization that is user and/or HW dependant (and user initiated), like compiling (possibly automatically without guesswork) all and only needed drivers in kernel and deciding what services to use. With services I don't mean individual daemons, but higher-level systems. If there are no network printers, then CUPS can be started when printing is needed, if there are no shared resources, those need not be started.

+1.  Can't Ubuntu reconfigure itself after booting to boot fast on the current hardware, and to boot more slowly but still successfully if there is a hardware change?  And similarly do profiling of what services the user tends to use, so that those are started up automatically, and others on demand?  Re Avahi and network printing - I don't know much about Avahi, but is possible to have it do a minimal startup which is just enough to detect the presence of services and to load more completely if services are found?  (Or to load completely straight away if the user uses network services a lot, see "profiling" above).

---

### Post by chris062689 on 2008-10-17
What I never understood was, couldn't Ubuntu compile it's own optimized kernel when it first installs / first boots?
Removing support for hardware that isn't needed, and stuff like that?  I know that wouldn't be a good solution for some business solutions, but for the home user, I don't think it would be a bad idea, plus there could always be a menu option to "recompile" the kernel...

---

### Post by gnomeuser on 2008-10-17
> **chris062689 said:**
> What I never understood was, couldn't Ubuntu compile it's own optimized kernel when it first installs / first boots?
Removing support for hardware that isn't needed, and stuff like that?  I know that wouldn't be a good solution for some business solutions, but for the home user, I don't think it would be a bad idea, plus there could always be a menu option to "recompile" the kernel...

That would basically create.. 8 million different kernels to support also if you extend your computer say with some kind of USB gadget you would, potentially but likely, not have it be detected.. major bummer.

It would be a support nightmare, total insanity at near zero gain. 

What you can do to gain a speedier boot is compile more modules into the kernel, which, surprisingly is what Arjan did to get the kernel to boot in a second (amongst other things - many other things but this is a big win). This is not without problems either and one would have to weight out if the gain is worth the cost.

---

### Post by michaeljt on 2008-10-20
You might want to offer a few different kernels though, with the bits compiled in adjusted to suit common configurations (and everything else as modules in all cases of course).

---

### Post by b3n87 on 2008-10-21
What ever your thoughts, I think we can all agree that Ubuntu needs some boot tweaks asap.

---

### Post by gnomeuser on 2008-10-21
> **b3n87 said:**
> What ever your thoughts, I think we can all agree that Ubuntu needs some boot tweaks asap.

That's a bit like saying "we can all agree it should be faster".. sure but it's idealistic to believe we can just do that without making trade-offs.

One way to get to a speedier boot could be by installing bootchart by default on the development branch then hooking it up to smolt ([http://smolts.org/](http://smolts.org/)), this way we get collation between hardware and boot time, across changes done. Knowing where the problem is cannot be underestimated, measuring the effect of a change neither so. We need to make sure we are aware of our problems and we need to know when we introduce regressions as well as improvements. We can also get a good wide look at where we are encountering problems this way, what kernels fails to boot for which setups, side benefits which can be of great use. 

Readahead schemes might also buy us some time, but to do this right we would need to have online defragging capabilities (to arrange blocks that need reading at boot in the optimal order - I believe ext4 will support this in the future, btrfs definitely will, ext3 does not currently so here a technology upgrade is required), as well as naturally some kind of metric for judging which blocks needs to be read ahead. How do we recalibrate the read ahead settings as the file system changes say as a result of a package upgrade (e.g. vital files gets moved, the block we needed is no longer known nor optimally placed - only a reboot for recalibration would do this properly I suspect, which also then means we will have slow boots still)

We would also need to check our assumptions, what modules e.g. are not compiled in but loaded on the majority of machines regardless. Can we find a smarter way to handle modules, so on.. where can we be smarter, where are we currently stupid? What wrong assumptions do we make about the system and what is the impact of these.

Big project, just saying "make it faster" is unhelpful in identifying problems, trade offs and potential solutions.

The one situation where it is easy would be in a specific deployment, you know all the hardware, you control the upgrades, you know everything. You can pick hardware to suit the requirement of a fast read (SSD e.g.). For a general OS like Ubuntu though, that needs to work in a multitude of deployments, across diverse hardware, in multiple languages, with a wide range of use cases.. hard job but step one is figuring out where it hurts and what we can do about it.

---

### Post by vuco on 2008-10-22
> **KimmoHop said:**
> If fast booting does not make system slower, why not implement it? Not everyone boots every year, some boot few times a day.

I think that the problem is two-folded:
1. Optimization that works for all users, like readahead and not scanning hardware in every boot. In my opinion, how convenient detecting new HW is, in most cases it can be started manually after changing HW configuration. If the boot is stuck (HW for a driver not found), scanning or probing can be started. It's the same as with my FAT32 and NTFS partitions, I don't want linux to scan those every N boots :)

2. Optimization that is user and/or HW dependant (and user initiated), like compiling (possibly automatically without guesswork) all and only needed drivers in kernel and deciding what services to use. With services I don't mean individual daemons, but higher-level systems. If there are no network printers, then CUPS can be started when printing is needed, if there are no shared resources, those need not be started.

I remember once compiling my own kernel, and boy, did I know what I should select and what not! (Also I may have compiled uCLinux kernel for Motorola Coldfire, but that was luckily preconfigured and I didn't have to guess) That process really could benefit probing HW and selecting what drivers are needed. Sorry if such mechanism already exists.
 

What I'm saying (in 5 seconds, can you?) is: Fast universal Ubuntu, optimized for my HW in no time.



I think that compiling is not needed. Only linking.
I will explain:

Divide the kernel package in dozens of modules packages each containing
just one module, already compiled (the object file).

At instalation time, the system checks dmesg (or whatever) to see what 
were detected and creates a metapackage which requires the packages
that contain the kernel modules needed by the specific machine. This
automatically created package doesn't install anything by itself, but
starts the linking phase of the kernel object files and installs the
resultant kernel.

Grub boots by default this customized kernel. But a new grub option
would be added: the "hardware detection option" which will boot kernel
with all the modules/initrd/detections stuff as we have today and will
start in another runlevel. In this runlevel, will be started a service
that will recreate the kernel metapackage (updating the requirements
for the kernel objects packages needed by the new hardware configuration)
and install it. On the next boot, the new customized kernel will take place.

Additionally, we could have a GUI in the system/administration menu 
which could be ran to force some detections or inserting some HW
support even if it wasn't detected and, again, generate the kernel 
metapackage...

Please don't flame me too much if I said something wrong...

Best Regards
Luis Otávio de Colla Furquim

---

### Post by gnomeuser on 2008-10-22
> **vuco said:**
> I think that compiling is not needed. Only linking.
I will explain:

Divide the kernel package in dozens of modules packages each containing
just one module, already compiled (the object file).

At instalation time, the system checks dmesg (or whatever) to see what 
were detected and creates a metapackage which requires the packages
that contain the kernel modules needed by the specific machine. This
automatically created package doesn't install anything by itself, but
starts the linking phase of the kernel object files and installs the
resultant kernel.

Grub boots by default this customized kernel. But a new grub option
would be added: the "hardware detection option" which will boot kernel
with all the modules/initrd/detections stuff as we have today and will
start in another runlevel. In this runlevel, will be started a service
that will recreate the kernel metapackage (updating the requirements
for the kernel objects packages needed by the new hardware configuration)
and install it. On the next boot, the new customized kernel will take place.

Additionally, we could have a GUI in the system/administration menu 
which could be ran to force some detections or inserting some HW
support even if it wasn't detected and, again, generate the kernel 
metapackage...

Please don't flame me too much if I said something wrong...

Best Regards
Luis Otávio de Colla Furquim

Modules which are not loaded are just "wasted space" sorta speak. If a given driver is a module you are not needing it won't be loaded at all, making this whole scheme wrong from the inception if I understand the idea correctly.

What takes time with regards to modules is primarily module insertion and loading. This is most of what initrd (early userspace) does for us, all the detection, scanning of busses and such will be done regardless and needs to be done, you can't get around that (well you could but then you would need to be in a world where everything was static at all times.. say like a TV - no no not far fetched.. these run Linux trust me, Sony e.g. have been doing embedded Linux on their TVs since 2002).

Arjan recently posted a bunch of patches to parallalize many of these scans so already we should see speedups there when we adopt and enable the work (should be in 2.6.28 or in Ubuntu speak Jaunty timeframe). 

We can get around the loading of modules simply by discarding the initrd stage and compiling everything into the kernel.. not a pretty solution or a very neat one but Arjen wagers we can get coverage of 95% of all desktop systems this way and the rest can have the "alternative" initrd way.. I doubt this will really work long term, but experiments will probably reveal the true state of this suggestion on a wide scale.

---

### Post by vuco on 2008-10-22
> **gnomeuser said:**
> Modules which are not loaded are just "wasted space" sorta speak. If a given driver is a module you are not needing it won't be loaded at all, making this whole scheme wrong from the inception if I understand the idea correctly.

What takes time with regards to modules is primarily module insertion and loading. This is most of what initrd (early userspace) does for us, all the detection, scanning of busses and such will be done regardless and needs to be done, you can't get around that (well you could but then you would need to be in a world where everything was static at all times.. say like a TV - no no not far fetched.. these run Linux trust me, Sony e.g. have been doing embedded Linux on their TVs since 2002).

Arjan recently posted a bunch of patches to parallalize many of these scans so already we should see speedups there when we adopt and enable the work (should be in 2.6.28 or in Ubuntu speak Jaunty timeframe). 

We can get around the loading of modules simply by discarding the initrd stage and compiling everything into the kernel.. not a pretty solution or a very neat one but Arjen wagers we can get coverage of 95% of all desktop systems this way and the rest can have the "alternative" initrd way.. I doubt this will really work long term, but experiments will probably reveal the true state of this suggestion on a wide scale.

I'm not really sure if what proposed was exactly understood. I mean my
suggestion on doing customized kernels wasn't just about saving space. I
didn't clearly said that the packages containing each one an object 
file of a single kernel module would be compiled to be statically linked
in the kernel (except for the ones who can't be compiled to be statically
linked). So no insmoding (at most situations) and, perhaps, no initrd.
So, everything (or most of it) would be compiled into the kernel and the
coverage wouldn't be 95%, but 100%! Everything without recompiling, just
linking. The packages with kernel pieces would be object files, not source
files.

Best Regards

---

### Post by gnomeuser on 2008-10-22
> **vuco said:**
> I'm not really sure if what proposed was exactly understood. I mean my
suggestion on doing customized kernels wasn't just about saving space. I
didn't clearly said that the packages containing each one an object 
file of a single kernel module would be compiled to be statically linked
in the kernel (except for the ones who can't be compiled to be statically
linked). So no insmoding (at most situations) and, perhaps, no initrd.
So, everything (or most of it) would be compiled into the kernel and the
coverage wouldn't be 95%, but 100%! Everything without recompiling, just
linking. The packages with kernel pieces would be object files, not source
files.


If the object is trying to avoid module insertion as much as possible, then the solution would likely not be this complicated and hard to implement+support scheme, but rather compiling as many modules into the kernel as possible. The potential performance hit of doing that would be minimal and you would avoid losing functionality. As Arjan estimates this would get us to coverage of 95% of all machines. The rest would then be forced back on the "properly designed early userspace method - because calling this legacy mode would be backwards :)". 

That would be easier to maintain, and easier to support plus it would not require complicated implementation and design to make work. 

For the record I don't really believe that module insertion would be the first choice on my list of targets. I don't believe it will gain us much by following any of the current proposals and the risk of regressions is some what frightening but I would love to be proven wrong.

---

