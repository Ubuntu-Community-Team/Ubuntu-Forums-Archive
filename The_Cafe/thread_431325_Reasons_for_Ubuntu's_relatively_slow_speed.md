---
title: "Reasons for Ubuntu's relatively slow speed"
date: 2007-05-02
forum: The Cafe
---

### Post by maniacmusician on 2007-05-02
I'm curious as to what these really are. Ubuntu and it's derivatives are most certainly slower than other distros that I've tried, and I'm wondering why. Some people have cited the generic kernel as a cause, saying that since the Ubuntu kernel isn't optimized to  your system, you take a hit. While this may be true, I don't quite think it's the entire reason. While browsing around on another forum, I found this post by another user:
> Do an lsmod and you'll find three screens full of modules that it loads "just in case", rather than auto-detecting your hardware and only loading modules it needs.
This was quite interesting. I'm not sure if it's complete BS or not, but if it's true, then what's the reasoning behind it? If other distros have the technology to load only needed modules, why do we not? Is the module system flexible enough to load modules selectively at boot depending on what hardware is running at that time? 

I'm really just curious about this, so keep the silliness and flames out of this thread, or I'll just have it closed and you'll have succeeded in wasting my time and the time of others who wanted to read this thread.

---

### Post by BLTicklemonster on 2007-05-02
I get laptop battery monitoring stuff, and I'm on a desktop. I have some wacom tablet thing, and I didn't even know wacom texas made tablets. HP printer stuff, and I don't have a printer hooked up? Tons of stuff loads up or appears to anyway, that I have no need for. I see the reasoning behind that comment, MM.

How ya doin'? Long time.

---

### Post by maniacmusician on 2007-05-02
yeah, I get a lot of stuff that I don't use either...but the questions is why? If other distros have selective module loading why don't we? The comment does make sense, but on the other hand, you have to say to yourself, that this is a pretty obvious thing. Ubuntu devs must certainly be aware of it, and they must have all those modules enabled for a reason. So what's their reason? Is it worth taking a hit in performance for? How much performance will we gain by resolving this issue?

---

### Post by Xzallion on 2007-05-03
I have an idea why they do this, but this is just my speculation, no proof or research before my pondering.

Since Canonical tries to make Ubuntu work on the widest selection of machines and to make it as easy to install as possible, making sure certain modules are loaded by default helps.  Like the Wacom Tablet thing, when someone buys a Wacom Tablet, they want to plug it in and see it start working.  If that module isn't loaded then they would (i believe) have to reboot after installing this since I think it is covered in the xorg.conf file.  But more then that, maybe some applications are used to working with certain modules, or some such.

The other thing, if you rely on an autodetection script to determine what modules to load, you create another chance for failure.  If it detects something wrong, you have to disable the autodetect and fix the problem yourself.  With such a wide range of computer hardware and devices,  I wouldn't trust an auto detection program to determine what modules to load.

Hopefully someone that understand this better and has some research/facts will post, but until then you have my own ponderings.

---

### Post by reyfer on 2007-05-03
> **Xzallion said:**
> I have an idea why they do this, but this is just my speculation, no proof or research before my pondering.

Since Canonical tries to make Ubuntu work on the widest selection of machines and to make it as easy to install as possible, making sure certain modules are loaded by default helps.  Like the Wacom Tablet thing, when someone buys a Wacom Tablet, they want to plug it in and see it start working.  If that module isn't loaded then they would (i believe) have to reboot after installing this since I think it is covered in the xorg.conf file.  But more then that, maybe some applications are used to working with certain modules, or some such.

The other thing, if you rely on an autodetection script to determine what modules to load, you create another chance for failure.  If it detects something wrong, you have to disable the autodetect and fix the problem yourself.  With such a wide range of computer hardware and devices,  I wouldn't trust an auto detection program to determine what modules to load.

Hopefully someone that understand this better and has some research/facts will post, but until then you have my own ponderings.

I completely agree with you on the first part of your post. But on the part about the autodetection script, the question remains: how come it is working on other distros?

---

### Post by Tomosaur on 2007-05-03
The short and shrift of it is that Ubuntu loads tons of crap onto your system which you don't need. This is why it's so successful at 'just working' for so many people. Many other distributions provide you with the bare minimum, then you have to optimise it for your system. Ubuntu goes in the other direction - it provides you with everything, and you have to clean out all of the stuff you don't need.

I think a tool to do this automatically would be useful, or an online installer which detected your hardware and only installed what is necessary - this could go some way to improving speed, and it could also remove some incompatibility issues and conflicts, too, I suppose.

But it's a moot point for me, anyway - a brand new Ubuntu install on my machine is still a few times faster than XP ever was, even when I re-installed XP brand new. It's performance doesn't degrade over time, and it always feels like new.

---

### Post by maniacmusician on 2007-05-03
> **Tomosaur said:**
> The short and shrift of it is that Ubuntu loads tons of crap onto your system which you don't need. This is why it's so successful at 'just working' for so many people. Many other distributions provide you with the bare minimum, then you have to optimise it for your system. Ubuntu goes in the other direction - it provides you with everything, and you have to clean out all of the stuff you don't need.

I think a tool to do this automatically would be useful, or an online installer which detected your hardware and only installed what is necessary - this could go some way to improving speed, and it could also remove some incompatibility issues and conflicts, too, I suppose.

But it's a moot point for me, anyway - a brand new Ubuntu install on my machine is still a few times faster than XP ever was, even when I re-installed XP brand new. It's performance doesn't degrade over time, and it always feels like new.
that's certainly true, but in the interest of not wasting cpu power, I'd love to be able to cut down on the stuff I don't need. So how do you tell which modules are unnecessary? and how do you permanently remove modules? (Isn't modprobe -r only temporary?) there should at least be a comprehensive resource that helps us with this (there probably is, I guess).

What else can we cut down on besides modules and services?

---

### Post by prizrak on 2007-05-03
I think it really varies by hardware for me OpenSuSE and FC/RedHat are pretty slow. Ubuntu on the other hand is pretty quick.

---

### Post by maniacmusician on 2007-05-03
> **prizrak said:**
> I think it really varies by hardware for me OpenSuSE and FC/RedHat are pretty slow. Ubuntu on the other hand is pretty quick.
openSuSe has always been slow, I think. at least the few times that I've tried it. Ubuntu is certainly not slow, but it's **relatively** slow compared to systems like Sabayon and Gentoo, Slack, etc.

---

### Post by Fitzy_oz on 2007-05-03
> **maniacmusician said:**
> openSuSe has always been slow, I think. at least the few times that I've tried it. Ubuntu is certainly not slow, but it's **relatively** slow compared to systems like Sabayon and Gentoo, Slack, etc.

Couldn't agree more - Perhaps a Module Document with a short definition for what each loaded module is and if and how it can be safely removed or disabled or a gui tool to do both?

---

### Post by Steve H on 2007-05-03
I'd like to know which modules to unload to streamline my system as well. I does bug me that there are modules sitting in memory doing nothing, and will never do nothing because I don't have the hardware. When I used XP there was a site run by Black Viper that used to list the various services and whether the were system critical or not. It was great i streamlined XP by about 80 - 100Mb in memory(which for XP was a miracle).

I could do with a similar site listing all the system critical stuff, so I can ditch the rest that i don't want or need!

:)

---

### Post by Sunflower1970 on 2007-05-03
> **Steve H said:**
> I'd like to know which modules to unload to streamline my system as well. I does bug me that there are modules sitting in memory doing nothing, and will never do nothing because I don't have the hardware. When I used XP there was a site run by Black Viper that used to list the various services and whether the were system critical or not. It was great i streamlined XP by about 80 - 100Mb in memory(which for XP was a miracle).

I could do with a similar site listing all the system critical stuff, so I can ditch the rest that i don't want or need!

:)

Black Viper's back. (I found something on Digg about him about a month or two ago..Wish I had known about him and his site a few years ago)

I'd like to know what I can disable, too. Would be a fun project to dig a bit deeper...and knowing my luck break my system (lol!)

---

### Post by Tomosaur on 2007-05-03
I remember there's a command line tool I used to wean out all of the unnecessary stuff, it provided a description with each item. I don't currently have access to my machine as I'm at my parents house, but I'll take a look later tonight and see if I can find out it's name again.

---

### Post by reacocard on 2007-05-03
> **Tomosaur said:**
> I remember there's a command line tool I used to wean out all of the unnecessary stuff, it provided a description with each item. I don't currently have access to my machine as I'm at my parents house, but I'll take a look later tonight and see if I can find out it's name again.

I think you mean debfoster. It's a great tool, but it's limited to packages. You can use sysv-rc-conf to adjust services. I don't know of any tools for adjusting kernel modules though.

---

### Post by Tomosaur on 2007-05-03
> **reacocard said:**
> I think you mean debfoster. It's a great tool, but it's limited to packages. You can use sysv-rc-conf to adjust services. I don't know of any tools for adjusting kernel modules though.

No it was something else. It scanned for the various modules on your system, their status etc. It was kind of similar to msconfig on Windows.

---

### Post by Hendrixski on 2007-05-03
> **maniacmusician said:**
> openSuSe has always been slow, I think. at least the few times that I've tried it. Ubuntu is certainly not slow, but it's **relatively** slow compared to systems like Sabayon and Gentoo, Slack, etc.

Everything runs slow compared to Gentoo... then again... everything is faster to install in non-Gentoo distributions.

I think it's a fair trade off to have everything work out of the box if it works bit slower rather than have it potentially crash out of the box just to get a few miliseconds of speed when loading an app.  It's not really noticeable.

---

### Post by jdong on 2007-05-03
> **maniacmusician said:**
> I'm curious as to what these really are. Ubuntu and it's derivatives are most certainly slower than other distros that I've tried, and I'm wondering why. Some people have cited the generic kernel as a cause, saying that since the Ubuntu kernel isn't optimized to  your system, you take a hit. While this may be true, I don't quite think it's the entire reason. While browsing around on another forum, I found this post by another user:

This was quite interesting. I'm not sure if it's complete BS or not, but if it's true, then what's the reasoning behind it? If other distros have the technology to load only needed modules, why do we not? Is the module system flexible enough to load modules selectively at boot depending on what hardware is running at that time?\

All of these statements are false.

(1) You would be surprised at how LITTLE kernel optimization does. Changing CFLAGS on the kernel does not yield any spectacular or most of the times even _noticeable_ benefits. This also applies to most applications on the system... maybe when we have a more sophisticated optimization framework standard in GCC, this will change, but for now, CFLAGS are just simply not significant in the performance they gain. Where it is important, Ubuntu's build scripts do indeed apply optimizing CFLAGS.

(2) The modules claim is total BS too. Module loading is all automatically handled by the udev/events system, which is fully dynamic. It does not randomly try to probe every single module. Ubuntu's kernel builds everything as a module so only the bare minimum has to stay in memory for your system to work. Other distros build in a lot of the modules that Ubuntu has listed under lsmod. This also doesn't really have much of a performance impact, just a nominal (a few MB) RAM usage impact.

(3) Unloading modules or deleting unused packages will NOT make your system faster. The former will make bootup slower because you're spending this time unload modules :D

The most likely reason it is slow is because of developer tradeoffs. For example, adding full RTL/LTR font rendering support in Firefox slows it down a good amount, but at the same time it adds support for many languages. There are probably many many examples of this that I am incapable of listing. A lot of the distros you named stick with very vanilla setups that trade some automation and convenience for a faster bootup with fewer worries.



Out of curiousity, exactly what is slow? I've found Feisty Fawn to be very competitive in performance with other distros.

---

### Post by DoctorMO on 2007-05-03
I second the above post, I was going to point out that udev handles loading usb kernel modules and that pci modules are loaded by udev on boot. you could check /etc/modules to see what is loading by default without udev but most of the time it's small if not empty list.

On saying that you can also be running a lot of system daemons which will eat up small amounts of cpu each.

---

### Post by EdThaSlayer on 2007-05-03
Maybe that module detecting software can't detect all of the pcs hardware 100% so just to be sure that no people complain they just enable all modules by defaust. Hope I didn't say the same thing as someone else.

---

### Post by Steve H on 2007-05-03
I guess I'm presuming that the modules were much like services in XP. I know I got some performance gain (not to mention more free memory) by shutting down/disabling services in XP.

Is this a misconception where Linux is concerned? Would it not be of a benefit to at least free up some more memory for the system?

Maybe its the geek inside that just wants the most efficient install and module tradeoff possible.

:)

---

### Post by jdong on 2007-05-03
> **EdThaSlayer said:**
> Maybe that module detecting software can't detect all of the pcs hardware 100% so just to be sure that no people complain they just enable all modules by defaust. Hope I didn't say the same thing as someone else.

No, that is not true. Ubuntu purely uses dynamic detection and it is highly discouraged to include drivers that require any sort of manual or brute-force probing techniques.

---

### Post by jdong on 2007-05-03
> **Steve H said:**
> I guess I'm presuming that the modules were much like services in XP. I know I got some performance gain (not to mention more free memory) by shutting down/disabling services in XP.

Is this a misconception where Linux is concerned? Would it not be of a benefit to at least free up some more memory for the system?

Maybe its the geek inside that just wants the most efficient install and module tradeoff possible.

:)

No, modules are like Windows drivers (.sys, .vxd). Go around Device Manager and look at the Show Details tab for each listed device, then tell me how many "modules" are loaded. You don't disable modules unless you don't want the associated device to function -- which is usually not the case. Disabling a kernel module saves you about 16KB of RAM, which is just enough to display 1/4 of the star smilie in the edit page, so umm... it's not terribly useful ;-)

Services are like... umm... services. They are loaded in /etc/rcS.d or /etc/rc2.d, and by default, Ubuntu only does the BARE MINIMUM for a fully functioning Ubuntu system. You can disable services using the configuration tool, or by hand-manipulating these two directories, but of course disabling the wrong services, JUST LIKE Windows, can lead to a mysterious loss of some functionality, which can be difficult to diagnose.

---

### Post by Steve H on 2007-05-03
> **jdong said:**
> No, modules are like Windows drivers (.sys, .vxd). Go around Device Manager and look at the Show Details tab for each listed device, then tell me how many "modules" are loaded. You don't disable modules unless you don't want the associated device to function -- which is usually not the case. Disabling a kernel module saves you about 16KB of RAM, which is just enough to display 1/4 of the star smilie in the edit page, so umm... it's not terribly useful ;-)

Services are like... umm... services. They are loaded in /etc/rcS.d or /etc/rc2.d, and by default, Ubuntu only does the BARE MINIMUM for a fully functioning Ubuntu system. You can disable services using the configuration tool, or by hand-manipulating these two directories, but of course disabling the wrong services, JUST LIKE Windows, can lead to a mysterious loss of some functionality, which can be difficult to diagnose.

That makes a lot more sense to me now. Thanks for that, jdong. i guess there is not much to regain from tatting around with modules, services etc. then?!

:)

---

### Post by jerrylamos on 2007-05-03
Well with Feisty Fawn and now early Gutsy Gibbon, on my several computers Ubuntu runs crisp and fast, certainly compared to the Windoze dual booted on the same system.  Now I'm an "ordinary desktop computer user" so I do internet, internet mail, internet videos, internet searching, Office word & spreadsheets, digital photo cropping & printing, LAN file sharing, and of course testing prerelease Ubuntu (also some X and a little K), occasional competitive Linux comparisons, etc.  I don't do games and 3D, I'm not into eye candy.  I'm into applications.

From my standpoint, for example, Feisty is nice and fast on a 1 gHz Pentium, 512 mb, old 4G hard drive and 1280x1024 LCD.  I'd like to see Vista on that system (no, I really wouldn't). 

Cheers, Jerry:)

---

### Post by Miguel on 2007-05-03
As said by Jdong, you won't gain much from disabling modules. On my system, there are a few modules marked as unused by lsmod which I don't know what they do or support but at most it would save me, what?, 500kb? You gain more by disabling some gnome applets.

You can gain more (not much) if you modify the startup services and some programs run by gnome on startup.  For example, why load all those wacom and nvidia things if you don't own  their hardware? Logical Volume Manager? I didn't know the live installer supported that. EVMS? The same. But when you start changing these things, you're on your own. Most obviously, don't disable anything you don't know what it does. On the gnome side, I usually disable updates notification (I'll aptitude update, thanks) and also disable restricted managers (read my sig). However, the most noticeable gain is that I feel better.

In short: did Arch run faster on my laptop? Yes. Did it take longer to configure? You can be sure.

---

### Post by prizrak on 2007-05-03
Nevermind

---

### Post by prizrak on 2007-05-03
> **Steve H said:**
> I guess I'm presuming that the modules were much like services in XP. I know I got some performance gain (not to mention more free memory) by shutting down/disabling services in XP.

Is this a misconception where Linux is concerned? Would it not be of a benefit to at least free up some more memory for the system?

Maybe its the geek inside that just wants the most efficient install and module tradeoff possible.

:)

Yeah I used to do that on XP as well. There is a trade off, the system gets noticeably less stable. Especially SP2 would have hidden dependancies.

---

### Post by jdong on 2007-05-03
0 used != unnecessary module. It just means nothing is currently actively using it, or that the module does not mind being removed (i.e. it has a mechanism for disconnecting from userspace apps that use the device)

I'm not saying that Ubuntu doesn't have room for improvement... if we can find some app that is performing particularly badly, then profile it to figure out where it is doing worse than our competition, then we can fix it :)

---

### Post by Gargamella on 2007-05-03
> **maniacmusician said:**
> yeah, I get a lot of stuff that I don't use either...but the questions is why? If other distros have selective module loading why don't we? The comment does make sense, but on the other hand, you have to say to yourself, that this is a pretty obvious thing. Ubuntu devs must certainly be aware of it, and they must have all those modules enabled for a reason. So what's their reason? Is it worth taking a hit in performance for? How much performance will we gain by resolving this issue?

yes,I know that's important, but it is slower than my xp, and I would like at least to be able to make it lighter on boot...anyway I hope there will be a change of attitude in this argument

---

### Post by B0rsuk on 2007-05-03
> **maniacmusician said:**
> yeah, I get a lot of stuff that I don't use either...but the questions is why? If other distros have selective module loading why don't we? The comment does make sense, but on the other hand, you have to say to yourself, that this is a pretty obvious thing. Ubuntu devs must certainly be aware of it, and they must have all those modules enabled for a reason. So what's their reason? Is it worth taking a hit in performance for? How much performance will we gain by resolving this issue?

The same reason why Ubuntu installs so many packages by default and offers no choice during installation. To make it as newbie-proof as possible. Ubuntu is targeted at users who can't be bothered to set something up manually. (72 percent of Ubuntu users never used Linux before) That's why they made everything work in a preemptive way.
Also, Ubuntu forces some choices upon you. I use KDE and Ubuntu Edgy updated from Dapper and earlier from Breezy. I had to install KDE metapackage, and with it I get a lot of programs I don't want, because I use only 1 kind of image viewer etc. You can't remove unneed stuff because kde metapackage depends on them.

You'll find yourself thinking more and more about Debian. Debian installs only minimal system by default and allows much more customizing. It doesn't force stuff down your throat. And since Ubuntu is based on Debian, switching 'back to roots' isn't a big deal.

---

### Post by reacocard on 2007-05-03
> **B0rsuk said:**
> The same reason why Ubuntu installs so many packages by default and offers no choice during installation. To make it as newbie-proof as possible. Ubuntu is targeted at users who can't be bothered to set something up manually. (72 percent of Ubuntu users never used Linux before) That's why they made everything work in a preemptive way.
Also, Ubuntu forces some choices upon you. I use KDE and Ubuntu Edgy updated from Dapper and earlier from Breezy. I had to install KDE metapackage, and with it I get a lot of programs I don't want, because I use only 1 kind of image viewer etc. You can't remove unneed stuff because kde metapackage depends on them.

You'll find yourself thinking more and more about Debian. Debian installs only minimal system by default and allows much more customizing. It doesn't force stuff down your throat. And since Ubuntu is based on Debian, switching 'back to roots' isn't a big deal.

You can just remove the kde/gnome/xfce metapackage you know. It's not needed to run the desktop, it's main purpose it simply to ensure smooth dist-upgrades between releases, but it's not hard to do that manually without the metapackage.

---

### Post by jdong on 2007-05-03
Again, **Ubuntu does use fully dynamic module probing like most other modern distros, and does NOT load any modules for hardware/capability that your computer does not have**. The reason that you see more modules listed is that Ubuntu builds almost everything it can as a module, while many other distros will build in the core IDE or AGP systems statically with the kernel, so they do not show up on lsmod. The usage count on lsmod does NOT show whether or not the device is in use -- it only shows whether or not anything else in the kernel is holding a lock on the device.

There is no "waste", no "loss of performance" from what you are seeing -- at most you are losing a few KB of RAM, which is quite insignificant unless you are doing embedded systems (which you would not use stock Ubuntu for anyway)

---

### Post by maniacmusician on 2007-05-03
> **jdong said:**
> Again, **Ubuntu does use fully dynamic module probing like most other modern distros, and does NOT load any modules for hardware/capability that your computer does not have**. The reason that you see more modules listed is that Ubuntu builds almost everything it can as a module, while many other distros will build in the core IDE or AGP systems statically with the kernel, so they do not show up on lsmod. The usage count on lsmod does NOT show whether or not the device is in use -- it only shows whether or not anything else in the kernel is holding a lock on the device.

There is no "waste", no "loss of performance" from what you are seeing -- at most you are losing a few KB of RAM, which is quite insignificant unless you are doing embedded systems (which you would not use stock Ubuntu for anyway)
okay, I understand that, thanks for all your explanations. It still stands true that Ubuntu is kind of slower than other distros, but at least you cleared up the stuff about the modules. Ubuntu and Kubuntu run fine on my modern machines. With specs that high, I don't really notice little things like this.

However, my concern is more with older machines. In my experience, Ubuntu is a good amount slower on older machines. Same goes for Kubuntu. That's a bit unfortunate. But it's not that big a deal; I guess I'll just use something else on older machines. I just hope we can improve performance on Ubuntu in the coming years.

---

### Post by thk on 2007-05-03
Sorry, without hard data, this discussion is meaningless. Individual perception of speed is rarely accurate in my experience.

---

### Post by jdong on 2007-05-03
> **maniacmusician said:**
> okay, I understand that, thanks for all your explanations. It still stands true that Ubuntu is kind of slower than other distros, but at least you cleared up the stuff about the modules. Ubuntu and Kubuntu run fine on my modern machines. With specs that high, I don't really notice little things like this.

However, my concern is more with older machines. In my experience, Ubuntu is a good amount slower on older machines. Same goes for Kubuntu. That's a bit unfortunate. But it's not that big a deal; I guess I'll just use something else on older machines. I just hope we can improve performance on Ubuntu in the coming years.

That may be true, but let's try to figure out why. I don't think any of us have actually profiled the system and tried to identify exactly why it's slow. I would have to say from experience that it has little to do with "zomgz no cflags generic optimizationz1!!!!!!" and more to do with differences at the source or design level...

---

### Post by kleeman on 2007-05-03
Can you be a bit more specific about Ubuntu being slower?

For example:

What machine are you using and what memory is there?
Which desktop are you using?
What exactly is slower (with times)?
Which distros are you comparing Ubuntu to?
What apps have you open when you make the comparison?

All of the factors I listed above can affect speed so generalized statements about slowness need context....

---

### Post by maniacmusician on 2007-05-03
> **jdong said:**
> That may be true, but let's try to figure out why. I don't think any of us have actually profiled the system and tried to identify exactly why it's slow. I would have to say from experience that it has little to do with "zomgz no cflags generic optimizationz1!!!!!!" and more to do with differences at the source or design level...
Right, I didn't think that either. As I stated in my first post, I didn't think that kernel optimization really had that big of an effect. Instead, I was asking **why**, the same way you are. I would also like to know why Ubuntu is generally slower. I'm not blaming it on the modules or on the kernel optimizations. The whole time, my post was a question. I wanted to know if the modules thing was true and if not, what the true reason behind it was. You answered that the modules excuse was BS, so now we need to discover the real cause of it.
> **kleeman said:**
> Can you be a bit more specific about Ubuntu being slower?

For example:

What machine are you using and what memory is there?
Which desktop are you using?
What exactly is slower (with times)?
Which distros are you comparing Ubuntu to?
What apps have you open when you make the comparison?

All of the factors I listed above can affect speed so generalized statements about slowness need context....

I understand what you're saying but it doesn't really apply here. Anyone that's tried various distros will be able to say that Ubuntu is not among the fastest of them. There's a certain spec threshold, above which it's hard to tell if a system is slower or not. So for example, on Core 2 Duo systems with lots of RAM and fast drives, most systems will operate pretty fast, regardless of differences in actual performance. But on lower specced systems, performance hits are more obvious. So indeed, a generalized statement is more appropriate  here.

---

### Post by macogw on 2007-05-04
I find it much faster than any other distro I've tried, except Damn Small Linux.  OpenSuSE & Fedora run okay for normal stuff, but the package managers are unbearable.  Sabayon has a 3 minute boot for me, and then it's not very responsive once it gets going.  It takes a few seconds to open up an application.

---

### Post by kleeman on 2007-05-04
> **maniacmusician said:**
> Right, I didn't think that either. As I stated in my first post, I didn't think that kernel optimization really had that big of an effect. Instead, I was asking **why**, the same way you are. I would also like to know why Ubuntu is generally slower. I'm not blaming it on the modules or on the kernel optimizations. The whole time, my post was a question. I wanted to know if the modules thing was true and if not, what the true reason behind it was. You answered that the modules excuse was BS, so now we need to discover the real cause of it.


I understand what you're saying but it doesn't really apply here. Anyone that's tried various distros will be able to say that Ubuntu is not among the fastest of them. There's a certain spec threshold, above which it's hard to tell if a system is slower or not. So for example, on Core 2 Duo systems with lots of RAM and fast drives, most systems will operate pretty fast, regardless of differences in actual performance. But on lower specced systems, performance hits are more obvious. So indeed, a generalized statement is more appropriate  here.

Well I have tried a range of distros on older hardware and find Ubuntu competitive so we have different experiences. If you are interested in nailing why you feel it is slower for you you need to be specific i.e. run a controlled benchmark on a specific app or desktop startup. If you don't we are reduced to me saying this is my experience and you saying what yours was i.e. a waste of time......

---

### Post by John.Michael.Kane on 2007-05-04
Why not just profile your system maniacmusician using OProfile which is in the repo's, and get the hard data you need. As well as an explanation of what is causing your "slowness".

---

### Post by FFred on 2007-05-06
> **jdong said:**
> Out of curiousity, exactly what is slow? I've found Feisty Fawn to be very competitive in performance with other distros.

For me it's starting apps. In KDE, with a kde konsole terminal already open, opening a new one takes 2 1/2 seconds. I get more or less similar results with all KDE applications. Once they've started, performance is normal.

This is on a machine with 2GiB of RAM and a decent dual core intel CPU so it's not a hardware limitation.
uname -a :
Linux neverwhere 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux

---

### Post by drdabbles on 2007-05-08
There doesn't seem to be any followup on this. Here's my $0.02 USD.

Without hard data- oprofile data, times, etc.- it is impossible to know what "slow" or "fast" mean. You can say that with faster processors comes faster performance. That is true with regard to time. However, the same instructions need to be executed for both machines. So, if you submit hard data that developers can look at, your problems can be addressed.

The problem here is the placebo effect. The system appears slow to you, whereas the system is performing the same functions at the same rate in both scenarios. Without using the scientific method, we can not resolve any issues people may or may not be having. If there are issues, we need to address them now so they can make it into the next release.

I can profile my system. I'd be glad to submit data if someone wants to look. I have a three or four servers, two desktops, and a laptop. All of these are a few years old, and the processors range from Core2 Duo to Celeron. I can also bootlog my systems. Some of them are base installs, whereas others have many extras loaded. Anybody want the data?

---

### Post by Blondie on 2007-05-08
> **maniacmusician said:**
> openSuSe has always been slow, I think. at least the few times that I've tried it. Ubuntu is certainly not slow, but it's **relatively** slow compared to systems like Sabayon and Gentoo, Slack, etc.

IMO the latest OpenSUSE is slower than Feisty, but Debian Etch is faster than Feisty. Haven't tried other distros recently enough to usefully comment.

---

### Post by BLTicklemonster on 2007-05-08
XP, from grub, is at the login menu in 18 seconds flat.

Ubuntu, from grub, is at the login menu in over twice as much time.

Using firefox in ubuntu, I'm used to the wait before it comes up. Earlier this evening, I was ripping a new Barbie DVD we'd gotten for my daughter (so she'd destroy the copy, not the original), and had to go online to find something, and BAM, firefox was online in no time (comparatively speaking). 


Maybe not exactly what this thread is about, but these two things are glaring examples of where Ubuntu needs to be looking in terms of fickle people who will judge an OS solely on how fast ... it is, whether booting, or bringing up a web browser. If I were a sheep, I'd have stuck with Windows, trust me. Look, to the outside observer sheep, Ubuntu is just an interesting curiosity, nothing more. It needs to be something that grabs them by the back of the head and slams them into the wall, and lets them know that, "hey, this is IT". 

Quantative information? No, but there's no doubt xp loads faster for the majority of the people who use ubuntu. I keep my XP clean, nothing running in the background, no garbage loading up that I don't need. Now how can I, or why can't I do this to Ubuntu?

Am I willing to boot to windows and time firefox opening, then boot to ubuntu and time firefox opening, and posting the results? Heck no, ubuntu takes forever to close, and forever to boot. (comparatively speaking)

---

### Post by steven8 on 2007-05-09
I have said nothing but how faster Feisty is for me than Dapper and XP was.  Boot time, shutdown time, OO opens faster, Firefox opens faster.  I love it!

---

### Post by kingkookie on 2007-05-09
As far as the Kernel goes, here is my suggestion:

Have a strong combination of Kernels pre-compiled on Ubuntu's setup disc.  Then during the setup, don't be afraid to ask what Make and Model of computer the user is using.  You can have a list of major Brand Name, with a sublist of models they make.  Do you have a HP Pavilion ZE4500?  No problem, just go under HP and select your model, from there, Ubuntu can tell what hardware you have and can select and Kernel that is pretty much pre-compiled for your system.  Perhaps even have a program to automatically check what system you have.

For custom built machines, you could choose custom machine and begin defining what your system has.

Of course, that might not be logical, but from my perspective, I'm sure that thinning out the Kernel and Modules to only what is needed would improve performance even if it is very slight.  For older machines, like mine, it could make a drastic improvement.  For now, I'm going through the learning experience of building my own kernel.  Hopefully I will succeed.

---

### Post by jdong on 2007-05-09
> **BLTicklemonster said:**
> XP, from grub, is at the login menu in 18 seconds flat.

Ubuntu, from grub, is at the login menu in over twice as much time.


Ah, and we arrive at Truth #7 about booting:

Microsoft has done **A LOT** to optimize the bootup procedure of XP, including:

Fully dynamic service dependency tracking
Early GUI/login-screen presentation
On the fly self-reprofiling, and self-defragmentation to speed up future boots.....


XP does boot up faster than most stock Linux distributions, and that gets more and more true as there are more and more things to track during bootup. It is indeed an area that Linux needs to work on in order to appeal to desktop users. Traditionally *nix was not optimized for quick startup/shutdown, but to be started up once and used for MONTHS between reboots. This area of daily startup/shutdown is a very new area for *nix, and it'll take time before the OS is tuned for such workloads.




And once again..... **Removing modules from the kernel will NOT** significantly affect bootup speed. Module loading does not hold much significance in bootup time. It's simply not the bottleneck, and not the reason the system is slow. I don't know where people get the idea that having a modular kernel with a broad range of loadable modules makes the system slower, but it is false. It is not "bloat" in any way, so stop suggesting it as such.

---

### Post by darkworld on 2007-05-09
i just read the beginning on this and being a newbie I only have limited knowledge. My question maybe a foolish one but then not as foolish as the question that isnt asked! 

Once your machine is booted and running fine. Why cant the kernel be intelligent enough to drop the unused modules? Sort of 

Kernal to user dialog: Everything ok?........... yes.......Should I drop the unused modules y/n ?........ Y

---

### Post by jdong on 2007-05-09
> **darkworld said:**
> i just read the beginning on this and being a newbie I only have limited knowledge. My question maybe a foolish one but then not as foolish as the question that isnt asked! 

Once your machine is booted and running fine. Why cant the kernel be intelligent enough to drop the unused modules? Sort of 

Kernal to user dialog: Everything ok?........... yes.......Should I drop the unused modules y/n ?........ Y

Once again, **slowness has NOTHING AT ALL to do with kernel modules**. Why don't you take that tissue box out of your car? It's making it go slower! I mean, I was in this other car the other day, and it accelerated so fast compare to yours -- it must be because you have two tissue boxes in your car and he only has the travel-size mini pack!


Ubuntu uses a **fully dynamic** modules probing system and does not load modules because "it feels like it" -- all modules are loaded because they are either necessary or provide a highly useful service. There's no "unused" modules, unless you consider your network card unused when you are not actively downloading :)

---

### Post by Linuturk on 2007-05-09
As a laptop users, I half agree and disagree with this thread.

I shutdown and startup my computer at work everyday, around the same time as my desktop at work. My Ubuntu laptop boots up faster than I can login to my XP machine. This is mostly due to some group policy we've enabled here at work. Shutdown time for my Ubuntu laptop is great. It seems to kick right off, just like an old Mac I used to have.

On the other side of the fence, things could be faster. If this was a vanilla XP install, it would fly onto the desktop before Ubuntu could present the login screen. There is a reason for this, of course.

Your ubuntu box is doing a lot more "out of the box" than your Windows XP machine. A full range of applications and services are already installed. Match the application base you have installed in Ubuntu to your Vanilla XP machine (and add antivirus) and see which reaches the desktop from the login menu faster.

An even better comparison would be booting up a Windows server with many services to booting up your Ubuntu box. I bet you a pretty pony that the Ubuntu machine will load faster than that Windows Server, and it will be more stable.

---

### Post by Compucore on 2007-05-09
I remember at one point with red hat that they had a way for optimizing the kernel itself which was to load a program tha actually went into the kernel itseld and you told it for a particular machine. That it had this, that, and the other thing after it installed completely onto the hard drive. So that the other drivers that were not required to load did not get loaded into memory. I have it here from a book that I have. I think it was called Linux for dummies. It was one of their earlier books where Red hat 5.0 or 6 was burnt onto the cdrom and you could load their version of red onto a computer. and go from there with it. I think it might be handy to have something like this aailable for lubuntu where you could go in and do what you needed to do with it and do a reboot afterwards. 

Compucore

---

### Post by jdong on 2007-05-09
> **Compucore said:**
> I remember at one point with red hat that they had a way for optimizing the kernel itself which was to load a program tha actually went into the kernel itseld and you told it for a particular machine. That it had this, that, and the other thing after it installed completely onto the hard drive. So that the other drivers that were not required to load did not get loaded into memory. I have it here from a book that I have. I think it was called Linux for dummies. It was one of their earlier books where Red hat 5.0 or 6 was burnt onto the cdrom and you could load their version of red onto a computer. and go from there with it. I think it might be handy to have something like this aailable for lubuntu where you could go in and do what you needed to do with it and do a reboot afterwards. 

Compucore

Umm... you're thinking of statically linked kernel drivers.... which are worse than kernel loadable modules. The memory requirements of the two and the resource usage is identical, but a kernel loadable module system can only probe the modules that apply to a particular system, instead of loading everything that someone decided to build into your kernel.

---

### Post by getlost on 2007-05-13
Ok,
  I have some details that maybe can add to this problem. Since I upgraded to edgy from dapper I have had a problem with the generic kernel. That problem continues with feisty.

 Here is the strange part: If I unplug my laptop and run on battery the speed returns to normal. So it appears to be related to acpi possibly.

  I have tried removing powernowd and using speedstep but there is still no difference. I have tried both Gnome and Kde and it makes no difference either. This happens on a fresh install. I have done an lsmod of both the generic kernel and the i386 kernel and all the same modules are loaded. This is on a Sony Vaio VGN-FJ270 laptop with Centrino and 2gigs of ram. If anyone has any ideas please let me know.

I would also be curious if this is the same issue with others complaining about speed.

Also, I'm willing to try any tests and post results because I would like to fix this. From what I read the i386 kernel only access 1gig of ram. Perhaps someone can confirm this.

---

### Post by Visceral Monkey on 2007-05-13
I love how some people insist that if there is no way to measure a "slow down" it just doesn't exist for them. I can agree on the perception bit, but there has to be something causing that perception of slowness. Personally, I find Fiesty to be slower than previous versions and other linx distros. It's now also slower than xp to boot and more importantly, feels slugish in performance. The how are the why don't effect the end result for me, which is that it's slower, slugish and becoming annoying.

---

### Post by jdong on 2007-05-13
We're not saying it doesn't exist or can't be measured, we say that it should be measured and characterized in a fashion that aids in fixing it. Of course we are all extremely interested in finding performance bottlenecks with Ubuntu and resolving them ,but not being able to identify the problematic areas really hinders progress.

---

### Post by getlost on 2007-05-13
IMPORTANT UPDATE:
   Ok. I've done some testing and I imagine this is reproducible.

   On booting up using generic kernel (recovery) the boot sequence gets to a point where it says: Running /scripts/init-bottom ... then it says done almost immediately. THEN there is a long pause (about 10 seconds) before it starts running rcS.d scripts. The scripts are then running very slow. I actually messed with the scripts and made the first script to just echo Debug... SO THE PROBLEM IS DURING initrd init.

  Now if I disconnect the power and run from battery it goes right through the Running /scripts/init-bottom ... into the rcS.d scripts WITH NO DELAY and the script run at normal speed.

  Finally, If I use i386 kernel no problem.
  
Again, this is on a Sony Vaio using a Centrino (not core duo) chip.

Any ideas will be nice.

---

### Post by PatrickMay16 on 2007-05-13
Perhaps a reason for ubuntu's slow speed is the amount of memory it uses. These days ubuntu is very bloated, taking almost 200MB of RAM after booting and logging in with Edgy. I suggest that people try Debian Etch, which is much faster.

---

### Post by getlost on 2007-05-14
I'm trying to be helpful here but seem to be being ignored...

Anyway. Further to my investigation I have found that there is definitely a problem with the generic kernel and the ACPI modules. If I start with acpi=off then the problem goes away that I described above. I pulled apart the initrd.img-2.6.20-15-generic kernel and dropped the acpi drivers from the initrd.img-2.6.20.15-i386 and started in recovery mode and there is no delay as I described. However, when I start in normal mode (without quiet or splash) although there is no delay during start up, once kde is loaded the slow down begins again. (popups and various messages appear in slow motion). I believe (although am not sure) this is do to a reloading of the acpi modules from the kernel.

Since it appears that this is beyond the purpose of this thread (which seem to be simply to complain) I'll let you know once I fix it. ;) If someone helpful should read this, I'd appreciate your input as I believe this might be a source of peoples complaints on performance. NOTE: This does not occur on my desktop.

---

### Post by jdong on 2007-05-14
Sounds like an ACPI bug or race condition of some sort. You should file a bug against the linux-soruce-2.6.17 package, and/or go to #ubuntu-kernel on IRC and try to get that diagnosed.

I've seen ACPI probing cause delays on some systems before, but that certianly doesn't account for every type of slowness people are referring to.

---

### Post by maniacmusician on 2007-05-14
> **getlost said:**
> 
Since it appears that this is beyond the purpose of this thread (which seem to be simply to complain)
Actually, this thread was just of an inquisitive nature. I wasn't complaining that Ubuntu is slow (because on my machine, it runs quite fast. My computer is pretty high specced), but I was wondering why it slower than some other distros on my older computers.

But I'm glad that you found something valuable. Though it seems to be only laptop/acpi related, it is still a bug. Hope you clear it up.

---

### Post by FFred on 2007-05-31
Except you can't use XP for a few minutes after you got to the desktop because it hasn't actually finished booting...

I don't really care about booting speed anyway, I only boot every now and then so it's completely irrelevant.

---

### Post by bruce89 on 2007-05-31
Slow?  Gnumeric takes 4 seconds to start from cold. (even with a 7 year old HD)

The only slow things are OpenOffice.org and Firefox (and by proxy Epiphany's loading is slow, runs alright when it has started), but that's because they are bloated rubbish.

---

### Post by forrestcupp on 2007-05-31
Ok, so despite what some people say, what if you do want to remove some of the services?  I use Feisty from a clean install, and there were some services that I can do without.  Maybe it doesn't make any difference, but if you do want to remove them, below is a good link that explains how to do it, and it explains somewhat what the purposes of the different services are.  Some of the ones you can't figure out, you can google the name and get an explanation.  The how-to is mainly for versions older than 6.10, but it works the same way, and I found a few that I removed.

Again, I can't say whether or not it actually makes any difference.

[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

---

### Post by FFred on 2007-05-31
OK, replying to myself. 
The reason a terminal (konsole) or pretty much anything takes ages to open is that it scans each and every font on the system prior to displaying a window (thanks for strace). Why it does this is  a mystery. 

I've had machines with as many fonts as I currently have (running Mandrake and Gentoo) but no such speed problems. From what I remember they were using xfs (the x font server), which may or may not be an issue...

---

### Post by DrMega on 2007-05-31
I suspect any performance issues are more to do with general Linux hardware support than anything else. Certainly on my machines, there are things which run many times faster than their Windoze counterpart, but certain processes are much, much slower. In particular I find reading/writing CDs and DVDs torturously slow when compared to Windows, and I suspect that is because the manufacturer of the drive couldn't be bothered to write Linux drivers for it and so I'm stuck with generic ones.

---

### Post by ricardisimo on 2007-06-27
I'm chiming in a tad late, but yes, Firefox and Thunderbird are more than just slow, they are hogs that freeze up my system for 15-30 seconds at a time, not just opening new tabs, but loading new pages or new emails. In fairness, *most of the time* I can still work with other apps that are already open. OOo is, of course, slow quite often, but this is less of a surprise a) because it is, in fact, a beast, and b) it's always been this way. T-Bird and FF, on the other hand, became hogs after the last kernel upgrade a few weeks or a month ago - coincidence or not I don't know. I'd greatly appreciate any ideas on how to fix this, or even a link to an existing report in launchpad. Thanks.

---

### Post by Yfrwlf on 2007-11-18
> **BLTicklemonster said:**
> XP, from grub, is at the login menu in 18 seconds flat.

Ubuntu, from grub, is at the login menu in over twice as much time.

Like has been already pointed out, XP comes up with the login screen before a lot of the system services start up, while Linux loads all the basic system stuff before you finally get to a login screen.  To compare the two, you'd need to time it from Grub to being fully onto the desktop and by automatically skipping the manual login part (since it's inclusion can screw up your test, since sometimes some things continue to load while sitting at the login screen).

Even that though isn't a fair comparison, since each system loads different utilities that do different things (but of course the majority do roughly the same things).

Regardless, any way in which code can be optimized and ways which will speed up program and OS loading times though is certainly ALWAYS good to go after!

Also, I must point out that there is much more auto-detection taking place during the Live CD boot than the OS boot it seems like, so the Live CD tries a lot harder to see what you have, but after installation it strips a lot of that out it seems.  I could be wrong, and I know booting from the CD is a lot slower, but it still seems to be doing a lot more behind the scenes detection stuff on the Live CD.  So, I think there is SOME effort going into installing more of the things your machine needs on it, but perhaps it could go further.

---

### Post by Yfrwlf on 2007-11-18
> **ricardisimo said:**
> I'm chiming in a tad late, but yes, Firefox and Thunderbird are more than just slow, they are hogs that freeze up my system for 15-30 seconds at a time, not just opening new tabs, but loading new pages or new emails. In fairness, *most of the time* I can still work with other apps that are already open. OOo is, of course, slow quite often, but this is less of a surprise a) because it is, in fact, a beast, and b) it's always been this way. T-Bird and FF, on the other hand, became hogs after the last kernel upgrade a few weeks or a month ago - coincidence or not I don't know. I'd greatly appreciate any ideas on how to fix this, or even a link to an existing report in launchpad. Thanks.

One way that doesn't have to do with code optimizations is to have an "agent" or "manager" or whatnot load up during boot, so that part of the program could be loaded and loading the rest wouldn't take as long.  That is what Windows does with IE I do believe, is part of it loads on bootup, and you can do it with OOo too, and I think that there are agents for one or both OOo and FF for Windows.  Implementing this would, of course, slow your system down and take up space when you don't want to use these programs, but perhaps someone could make an "agent" so that if you wanted these programs in memory you could have.  Or, you could just load the program and keep it open. ;)  Firefoxy is always running on my machines any way, so opening new windows is no problem, and on faster systems even from a cold start, Firefox only takes about 2 seconds to load.

---

### Post by FFred on 2007-11-18
> **ricardisimo said:**
> I'm chiming in a tad late, but yes, Firefox and Thunderbird are more than just slow, they are hogs that freeze up my system for 15-30 seconds at a time, not just opening new tabs, but loading new pages or new emails. In fairness, *most of the time* I can still work with other apps that are already open.
It seems to me as well that something has gotten wrong with the latest iteration of Firefox. Loading a new page (especially a long one, very noticeable on things like slashdot) freezes the app. Firefox really should be threaded. 
It has no impact on the rest of the system though although I expect it could have on a box with little RAM to spare.

---

### Post by ffi on 2007-11-18
> **BLTicklemonster said:**
> XP, from grub, is at the login menu in 18 seconds flat.

Ubuntu, from grub, is at the login menu in over twice as much time.


On my system XP is dead slow it takes ages to get a responsive desktop, unlike Linux, granted the desktop is there but I can't do anything for a long time and the only things starting up are my firewall (comodo) and antivirus (nod). Ubuntu boots up slower than Mandriva though, it always seems to hang a bit while setting op the lvm (what is that anyway?).

Prelinking speeds things up a bit too but ever since gutsy it takes ages to run, so I disabled it because updating/installing/removing software took ages...

another useful thing is mounting drives with the noatime option

---

### Post by tdrusk on 2007-11-18
> **FFred said:**
> It seems to me as well that something has gotten wrong with the latest iteration of Firefox. Loading a new page (especially a long one, very noticeable on things like slashdot) freezes the app. Firefox really should be threaded. 
It has no impact on the rest of the system though although I expect it could have on a box with little RAM to spare.
Try Opera. It runs a lot smoother on my system.

---

### Post by Dimitriid on 2007-11-18
Ive been comparing Ubuntu with Arch. Now I used Ubuntu and Xubuntu 32 bit Feisty,

My desk system specs are: Sempron 2800+ ( socket 939 ), 7682mb ddr 333 ram, BFG nvidia 7600GT, run of the mill 80gb 7200rpm hdd.

Now I tried Feisty on the desktop then I tried Arch. I noticed quite a dramatic improvement. Arch as you know is very minimalist, does not even installs a desktop environment or even xorg. You have to pick your modules, install them, and add all the daemons you might need ( in my case it was only HAL, FAM and GDM I beliebe ). After that Arch gives you a Gnome install which is pretty basic. The speed improvement is definitely noticeable. Boot up takes 3 or 4 seconds less, applications open at least 1 second early, memory consumption has gone down a bit. Everything is slightly improved in response times, like going from Ubuntu to Xubuntu. 

Now there are several reasons why this might be happening so maybe the more knowledgeable folks can pinpoint it better. But what I think it is might be either the barebones version of gnome ( all those little things like update manager, network manager, etc. ).
It might be the way Arch is build which optimizes specifically for x86 and x86 only ( although ive seen many laugh at that notion ). It might be the way the kernell is build for arch. Or it might be the rolling release system ( I never tried Gutsy on the desktop but Arch has mosts packages I use on equal or better versions than Gutsy and keeps updating everything everyday, there is no wait for a whole new release. )

But there IS a speed difference and on my hardware its definitely noticeable. Thoughts?

---

### Post by jdong on 2007-11-18
The difference is most likely related to what patches Arch has on top of the mentioned apps versus Ubuntu. Compiler optimizations and kernel configuration cannot make such a pronounced difference.

---

### Post by FFred on 2007-11-18
> **tdrusk said:**
> Try Opera. It runs a lot smoother on my system.
Unfortunately I really dislike the Opera interface nowadays... 
I just make do with Firefox and sometimes Konqueror. I just wish it would be better :)
Opera is still an impressive piece of work though. It's true that it runs quite fast on pretty much anything.

---

### Post by tdrusk on 2007-11-18
> **FFred said:**
> Unfortunately I really dislike the Opera interface nowadays... 
I just make do with Firefox and sometimes Konqueror. I just wish it would be better :)
Opera is still an impressive piece of work though. It's true that it runs quite fast on pretty much anything.

yeah. The MAIN reason I run it is because it crashes significantly less than firefox and konqueror with flash.

---

