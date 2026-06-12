---
title: "Suggestions to appeal Windows (and/or lazy) users"
date: 2005-08-27
forum: The Cafe
---

### Post by tseliot on 2005-08-27
Hi, I am a satisfied Ubuntu user and I love it but I've read many posts (I do not refer only to this forum) in which newbies coming from Windows complain about the unfriendlyness of Linux (not of a distro in particular) and of its command line.

Now, I like the command line and I think (i.e. I'm sure) it's fundamental to Linux. But there are some newbies who don't want to have anything to do with it unless it's strictly necessary. This is NOT my case as I miss the lack of a functional command line in Windows Xp (I know what's DOS) when I have to fix my father's computer (I don't use Windows any more).

I think something could be done for these people who either don't want or don't have the time to learn how to use the command line (although I think it's easy). For this reason I've thought of some applications which could make those people's life easier and which could prevent them to switch back to Windows.

I can't program so my suggestions could be impossible or very hard to make but I've thought they could be integrated in GNOME or in KDE so as to prevent the use of the command line.

I would like to know:
a) whether it's possible or not to made them (and include them in a future release of the OS) 
b) your opinion about my ideas 

P.S. Ok, perhaps point 3 and 4 are very hard to made.


1) a GUI to Xorg featuring the following functions:
selection of your graphic board (e.g. if you want to switch from your 1st card to your 2nd one)
resolution
refresh rate
Monitor

A user could either select what s/he needs or fill in the text field (e.g. the desired resolution or refresh rate)

2) a GUI to install single .deb files (which runs sudo dpkg -i name_of the file  automatically, with warning messages in windows) by doing a drag & drop of the file into an area of the desktop 

OR (the easiest thing to make) an "install" option available with a right click on the desired .deb file

3) A simplified and eye candy GUI to kernel compilator (menuconfig, etc.) with the following functions:
A button which installs all the packages which are required to compile a kerne

The following sections in which you only have to put a tick if you need it (a matter of mouse clicks)
DMA (to enable in the kernel)
Architecture (i386, amd64,etc.)
RAM Amount of (more than 1gb)
Filesystem support (ext3.etc.)
Framebuffer for Nvidia (in order to disable it)

A button to download the latest stable kernel source from Ubuntu and Kernel.org

A button to use your previous kernel settings to the new kernel (i.e. "sudo make oldconfig")

A section in which you can type the name of the new kernel

OPTIONAL (because it could be hard) The possibility to recompile the modules for the new kernel (nvidia, etc.) 

A button to Compile the kernel image and headers (which stands for the command sudo make-kpkg --initrd &#8211;append-to-version=-name_of_the_kernel kernel_image kernel_headers)

A button to install the new kernel and update GRUB

4) I know this should be up to the developers of the drivers: 
A better integration with the scripts of nvidia ati installers: some automated script which does everything for you  Then you can choose to use the installed driver by using the application I've dealth with in Point 1.

OR an application (with a GUI) which compiles the modules (e.g. nvidia or ati) for your current kernel

---

### Post by xequence on 2005-08-27
And maybe someone who has never used windows and has used linux will complain about things about windows ;) Just what you are famaliar too...

> OR (the easiest thing to make) an "install" option available with a right click on the desired .deb file 

They have that on mepis.

Other then that request, which I also would like, I dont much understand the other ones and I still get along well using ubuntu. XP PRO gives me real trouble  ](*,)

---

### Post by Kyral on 2005-08-27
I actually like the idea of an "Idiot Proof" way to compile a kernel. Its a bitch when you just wanna compile in a module

---

### Post by drizek on 2005-08-27
If you want those features, use a distro like suse or mepis or xandros or linspire etc. 

they all have those capabilities. as for recompiling the kernel, i dont think that is something that most users want to do. if they screw it up, it will kill their computer. making it idiot-proof means we will have more idiots recompiling kernels, and more problems as a result. instead, the ubuntu kernels should support more hardware by default. that way, people wont have to bother recompiling the kernel at all.

---

### Post by aysiu on 2005-08-27
I second the motion. Mepis has almost all of those features (except the kernel recompiling). I love Ubuntu, but if people want that stuff, they should use Mepis.

---

### Post by Paul Bramscher on 2005-08-27
[QUOTE=tseliot]Hi, I am a satisfied Ubuntu user and I love it but I've read many posts (I do not refer only to this forum) in which newbies coming from Windows complain about the unfriendlyness of Linux (not of a distro in particular) and of its command line.[/QUOTE]

In my case, I originally come from an Apple // and MS-DOS background, using linux since the late 1990's.  I'm not afraid of command-line, but I'm married, couple kids, mortgage, full-time job, etc. now.  I don't have a lot of spare time.

The sheer brilliance of linux is that you can set up all different sorts of purposed boxes today -- and you can do it totally command-line if that's your thing.  Or almost totally GUI.

What's nice is that the GUI's are generally just front-ends over some conf file.  So you have an arrangement that pretty much caters to your style.  What's missing is that some of the more complex tasks (goofing with xorg.conf, apache conf, php.ini, my.cnf, sshd.conf, etc. are still lacking GUI interfaces.  But these aren't trivial anyway, and you better know what you're doing when you make adjustments.

So in my opinion, it should ideally be possible to set up a desktop-class box for a newbie without ever touching a command prompt.  I think we're basically there already, multiple distros have been there for awhile.

---

### Post by drizek on 2005-08-27
there already are GUI frontends to config files.

i cant remember the name off the top of my head, but i do remember there was a poll on a kde site once asking if users wanted to include it with kde or continue using config files. config files won by a small margin, so it was never implemented.

Edit: i also read on a kubuntu feature plan thing that they might take the mepis os config utility and bring it to kubuntu. that would be very cool IMO.

---

### Post by mstlyevil on 2005-08-27
I just wouldn't worry about appealing to Windows users who are too lazy to switch. Linux is not windows nor should it be. My brother thinks I am crazy for using Linux. He told me straight up he would not switch because he is used to the way Windows works and he is used to the way IE works and does not want to relearn a new OS.  You just cannot appeal to these people no matter what you do. I know people that will not switch from 98 or 2000 to XP because some things are different. They will not switch till they have to.  So I think trying to appeal to lazy Windows users is a waste of time. Now on the other hand I think there are plenty of things that might appeal to Windows users that are fed up with the garbage they put up with using M$.  Outside of Gaming, you can do everything a windows machine can do if you are willing to take the time to learn. You also get many applications in Linux for free that does not come with a paid copy of windows. All we need to do is get the information out there that Linux is a viable alternative to windows.

---

### Post by Stormy Eyes on 2005-08-27
Ignore Windows users. If they want something better badly enough, they'll get off their lazy asses and switch. Until then, they're not worthy of time or concern, and will probably resent efforts to persuade them that there are better options available.

---

### Post by aysiu on 2005-08-27
Trying to convince a Windows user to switch to Linux is like trying to convince a city dweller to suddenly move out to rural farm country. Sometimes, city dwellers will complain about pollution, noise, violent crime, homelessness, etc., but ultimately, they like the convenience of a major metropolitan area.

That doesn't mean there shouldn't be some distros that appeal to those who do suddenly decide, "Hey, I think I'll give Linux a shot." Not *every* Linux distro has to do that, but I am glad that Linspire and Mepis are around to fill that niche. I'm also glad that Ubuntu doesn't really, but it's still simple enough for non-programmer people like me to use.

---

### Post by drizek on 2005-08-27
[QUOTE=aysiu]Trying to convince a Windows user to switch to Linux is like trying to convince a city dweller to suddenly move out to rural farm country. Sometimes, city dwellers will complain about pollution, noise, violent crime, homelessness, etc., but ultimately, they like the convenience of a major metropolitan area.

That doesn't mean there shouldn't be some distros that appeal to those who do suddenly decide, "Hey, I think I'll give Linux a shot." Not *every* Linux distro has to do that, but I am glad that Linspire and Mepis are around to fill that niche. I'm also glad that Ubuntu doesn't really, but it's still simple enough for non-programmer people like me to use.[/QUOTE]
 thats not true. the country sucks, and they are polluting more than cities with their fertilizer runoff and pesticides and cow shit.

linux is not like the country. switching to linux is like moving from LA to london. its better, but you have to give some things up and get used to a whole new system, but its a better system.

---

### Post by aysiu on 2005-08-27
[QUOTE=drizek]thats not true. the country sucks, and they are polluting more than cities with their fertilizer runoff and pesticides and cow shit.

linux is not like the country. switching to linux is like moving from LA to london. its better, but you have to give some things up and get used to a whole new system, but its a better system.[/QUOTE] Okay. So my analogy wasn't perfect. The idea is that you can't convince anyone to switch.

---

### Post by occy8 on 2005-08-27
> Ignore Windows users. If they want something better badly enough, they'll get off their lazy asses and switch. Until then, they're not worthy of time or concern, and will probably resent efforts to persuade them that there are better options available. 

thats a harsh comment. But looking at your location it explains something :wink: 
Not every windows user has got the time to learn all that linux stuff. I must say I don't have a problem with installing software using the command line, that doesn't take much time to learn and a lot is being installed by synaptec anyway.
A problem is if your hardware is not supported or where its difficult to get it working, thats a real pain in the bum if you are new to linux install it and then the screen's black, modem doesn't work or printer.
I like to see  a website where a script checks your hardware and tells your if there will be a problem or not.

---

### Post by skoal on 2005-08-27
[QUOTE=drizek]thats not true. **the country sucks**, and they are polluting more than cities with their fertilizer runoff and pesticides and cow shit.[/QUOTE]
pfft! you city slickers...

I was born and bred a bumpkin, along the vast countryside stretches of Texas.  Yeehaw! and Yippie kay yay, mutha crunkers!  

......now, can any of you fellers do _this_ in the city?

Toss sun dried cow shit over to your buddy like it were a frisbey? Throw a match on said frisbey, making things _really_ interesting with your buddy? Distil your own moonshine whisky, made from taters and the choicest rat droppings? Stand outside your front porch stark naked, spelling out your name in the dirt while taking a wiz?  Watch some twister pick up your neighbours house, waving to him as he circles and flails about aimlessly next to it, "Hey Superman! who's laughing now at my storm shelter?!"?  Or just walk over to a pond, get in a boat, and go fishin' with a 12 gauge Winchester?

Now THAT's living, brother. Aysiu was correct!...partially, I think...who knows...I digress anyways...

As for your pollution "analysis", I only see a grey haze when I drive my John Deere _into_ Dallas, not the other way around...

Just to seem somewhat on topic here, Windows users are not lazy.  That is all.

\\//_

---

### Post by drizek on 2005-08-27
i installed kubuntu for my little brother and he is using it just fine. he can use synaptic to install software(mostly games), he set up his ipod, set up a p2p app, and he even set up an hp printer. he never had to use the command line for anything or even read a guide for anything and his system works great. his install of windows xp was hopeless. full of spyware and other crap and his computer was soooo slooooooow.

---

### Post by Wolki on 2005-08-27
> **tseliot]Hi, I am a satisfied Ubuntu user and I love it but I've read many posts (I do not refer only to this forum) in which newbies coming from Windows complain about the unfriendlyness of Linux (not of a distro in particular) and of its command line.[/quote]

Yeah, but make it easier and they will still complain. Many people do not really give Linux a chance, when they try it they only want to confirm their own prejudices. Copying Windows is a bad idea - lure them into thinking "Hey, this is just like Windows" and they will stumble even more over the things that are different - and some things **have** to be different, because frankly, from a user interface perspective, Windows sucks. Prepare people that things will be different, and if possible explain why, and they might accept it - at least imho.


That said, there is absolutely nothing wrong with making things easier - every minute spent doing trivial stuff is a minute that's not used for more interesting stuff, and that does not mean one is lazy (though I am  said:**
> 
1) a GUI to Xorg featuring the following functions:
selection of your graphic board (e.g. if you want to switch from your 1st card to your 2nd one)
resolution
refresh rate
Monitor

Well, xorg.conf is a config text file. That's harder to edit automatically than something like gconf, but by no means impossible. A spec on everything that the apps should be able to do would be needed (just look at the additional features possible for nvidia cards, you can't support everything), and it needs to stay maintained since the xorg guys are constantly adding new features. Not easy, probably with the devil in the details due to the huge number of possible configurations.

And it probably wouldn't change that a user has to know the refresh/sync rates of his monitor, which often is the difficult part of editing xorg.conf. Having such a program would be useful, but imho not that much (how often do you edit your configuration?). The time used to develop is is maybe better used fixing some bugs right now, or useful features in programs used more often. But I'm sure such a thing is planned for the future.

> 2) a GUI to install single .deb files (which runs sudo dpkg -i name_of the file  automatically, with warning messages in windows) by doing a drag & drop of the file into an area of the desktop 


That sounds like a bad idea. Dropping something on the desktop puts it there (or if you drop it onto an Icon it sends it to that folder, application, or whatever type of icon it is). Maybe desklets-style, but I still don't see that as a particularly useable solution. Not to forget that it would use space on the desktop, and Ubuntu's philosophy is that the desktop is for the user to organize  as he wishes. That's why there's nothing on it after you install Ubuntu.

> 
OR (the easiest thing to make) an "install" option available with a right click on the desired .deb file

Easy. There already are nautilus scripts that do just that. It should also be really easy to program something that puts the Output into a window (I can't remember exacly how it is implemented, didn't install the scripts again after my HDD crashed)

It becomes difficult if you want automatic dependency resolution. The you would have to worry about conflicts and everything.

If Ubuntu doesn't include something like that, it might be because normal users are not supposed to install random debs - they are not tested by the Ubuntu team, and would be a great way to spread spyware and viruses. 


> 
3) A simplified and eye candy GUI to kernel compilator (menuconfig, etc.) with the following functions:

If xconfig is not good enough, this will be hard. Kernel compiling is a hard thing, do it wrong and you'll end up with something that won't work. And usually, users don't (and shouldn't) have to recompile their kernel. I'd say leave that to the people who know what they're doing.


> 4) I know this should be up to the developers of the drivers: 
A better integration with the scripts of nvidia ati installers: some automated script which does everything for you  Then you can choose to use the installed driver by using the application I've dealth with in Point 1.

Would really be better on the driver side. Using the packaged Ubuntu versions is good enough for me, and for lots of other people too I'd guess. Sure, you'll have to wait a little, but whan you get it it'll be easy to install and completely tested. I like having a stable system I don't have to fiddle with. Having everything as the latest and greatest is fun, but a broken system isn't, especially when you have work to do (and things always break then, as old Murphy told us:) )

Just my opinion. YMMV.

---

### Post by drizek on 2005-08-27
[QUOTE=skoal]pfft! you city slickers...
As for your pollution "analysis", I only see a grey haze when I drive my John Deere _into_ Dallas, not the other way around...
\\//_[/QUOTE]

there are other types of pollution ,not just smog. that cowshit that you light on fire contains a lot of methane(which is why it burns so well), and that methane is released into the atmosphere. methane is a greenhouse gas and cow shit is the leading cause of methane pollution. 

and then you have farmers using excess fertilizer due to shitty farming methods and excess water due to shitty irrigation, and then that water washes off all the fertilizer into a river(do you have those in texas?), which increases the amount of algea, and eventually kills all the fish.

anyway...

---

### Post by tseliot on 2005-08-28
Thanks for the answers guys. I like Ubuntu as it is but I would also like to decrease the percentage of Windows users. Ok there are distros like Mepis, etc. but I wanted Ubuntu to offer both the easy and the normal (with command line) way to users. I think this would make a better learning curve.Of course the command line would be used for more advanced purposes. I would keep on using only the command line though.

And about kernel compilation and Xorg GUI: ok they should be used by people who know what they are doing and the system is supposed to work out of the box (I refer to the kernel now). But what if your hardware is not supported or correctly detected? Ok, there's always the Community but I think a front-end to set for example the right resolution or to change the refresh rate wouldn't bad at all.

The kernel compilation application could be simplified even more: by using the settings of your previous kernel by default and by cracking down the number of options you can chose (e.g. DMA, Architecture and filesystem options only). this would solve little problems which can make you go nuts (I refer to DMA).

I'm not trying to make Ubuntu look or work like Windows but I would also like to make Microsoft monopoly end. It's only an idea, and perhaps it is a bad one, only time will tell (let's keep an eye on Mepis and PClinuxOS).

Alberto

---

### Post by Brunellus on 2005-08-28
General comment:  Simply making things easy won't bring the masses to desktop linux any more than the masses came to the old MacOS or are going to OSX.  To paraphrase Grand Moff Tarkin:  "Fear will keep the users in line."   Remember that MS-DOS and later Windows only gained prominence because businesses bought the computers that ran them in huge numbers--once that market had gone Intel/Microsoft, the home user market followed.  So shall it be with Linux:  no matter how warm & fuzzy you make it for the home user, it'll be industry that decides if or when a major migration happens.

Even if large corps migrate en masse to Linux, that might not mean much for Linux at home, which is what we all seem to mean when we say "desktop."  Corporate IT departments are unlikely to deploy thousands of computers and give their wage serfs root on *all* of them--that would be boneheaded to the extreme!  Thus, most users will just be that--users--and won't even get into anything that requires superuser privileges (the things we're always complaining about:  installation, etc).

On to specific comments.

> **tseliot]
I would like to know:
a) whether it's possible or not to made them (and include them in a future release of the OS) 
b) your opinion about my ideas 

P.S. Ok, perhaps point 3 and 4 are very hard to made.


1) a GUI to Xorg featuring the following functions:
selection of your graphic board (e.g. if you want to switch from your 1st card to your 2nd one)
resolution
refresh rate
Monitor[/QUOTE]

This already exists in SuSE as SaX.  This is super-nifty, and now that they're opening up fully, I anticipate some of their work in this regard to trickle out to other distributions, like our own beloved Ubuntu...



> 2) a GUI to install single .deb files (which runs sudo dpkg -i name_of the file  automatically, with warning messages in windows) by doing a drag & drop of the file into an area of the desktop 

OR (the easiest thing to make) an "install" option available with a right click on the desired .deb file

MEPIS already does this said:**
> 3) A simplified and eye candy GUI to kernel compilator (menuconfig, etc.) with the following functions:
A button which installs all the packages which are required to compile a kerne

The following sections in which you only have to put a tick if you need it (a matter of mouse clicks)
DMA (to enable in the kernel)
Architecture (i386, amd64,etc.)
RAM Amount of (more than 1gb)
Filesystem support (ext3.etc.)
Framebuffer for Nvidia (in order to disable it)

A button to download the latest stable kernel source from Ubuntu and Kernel.org

A button to use your previous kernel settings to the new kernel (i.e. "sudo make oldconfig")

A section in which you can type the name of the new kernel

OPTIONAL (because it could be hard) The possibility to recompile the modules for the new kernel (nvidia, etc.) 

A button to Compile the kernel image and headers (which stands for the command sudo make-kpkg --initrd –append-to-version=-name_of_the_kernel kernel_image kernel_headers)

A button to install the new kernel and update GRUB



Easy, tiger.  For 95% of Windows users, a kernel is the quantum of popcorn.  This should not be a priority--all those users who want to tune their kernel already have, or can gain, the requisite skills.  The user your'e worrying about couldn't tell you the difference between an OS and application software, or AOL and the Internet.  A kernelconfig GUI would be a waste of time at this point.

> 
4) I know this should be up to the developers of the drivers: 
A better integration with the scripts of nvidia ati installers: some automated script which does everything for you  Then you can choose to use the installed driver by using the application I've dealth with in Point 1.

OR an application (with a GUI) which compiles the modules (e.g. nvidia or ati) for your current kernel

Unlikely to happen in Ubuntu, because those drivers are nonfree.

---

### Post by tseliot on 2005-08-28
[QUOTE=Brunellus]Easy, tiger.  For 95% of Windows users, a kernel is the quantum of popcorn.  This should not be a priority--all those users who want to tune their kernel already have, or can gain, the requisite skills.  The user your'e worrying about couldn't tell you the difference between an OS and application software, or AOL and the Internet.  A kernelconfig GUI would be a waste of time at this point.



Unlikely to happen in Ubuntu, because those drivers are nonfree.[/QUOTE]
I've just found out this feature in Open Suse beta3. I haven't tried it yet but I've found the information while reading a review.

QUOTE:
...
They have given OpenOffice.org a new splash image that looks really nice. Also included are many nice backgrounds for the desktop as well. Some are of a nature motiff featuring animals, fauna or landscapes. Others are SUSE specific.[COLOR=Red] I had the installer install the nvidia drivers and Microsoft fonts during the "check for online updates" this time and that was wonderful. [/COLOR]I didn't have to fiddle with anything at all to obtain 3d acceleration. That's a really nice feature. ...


I think s/he is talking about Yast. Isn't it great? Could it be done in Ubuntu too?

It's not a personal request as I have no problem at all with installing Nvidia drivers from the command line (actually I've made a HOWTO about this). 


Here's the link to the review, please have a look:

[http://www.tuxmachines.org/node/2372](http://www.tuxmachines.org/node/2372)

---

### Post by tseliot on 2005-08-28
And I've found another thing about SUSE:

You can enable DMA from a GUI, AMAZING!

Here's the link to a screenshot:

[http://osdir.com/screenshots/index.php?directory=yast&currentPic=29](http://osdir.com/screenshots/index.php?directory=yast&currentPic=29)

---

### Post by poofyhairguy on 2005-08-28
[QUOTE=tseliot]
1) a GUI to Xorg featuring the following functions:
selection of your graphic board (e.g. if you want to switch from your 1st card to your 2nd one)
resolution
refresh rate
Monitor[/QUOTE]

So an xorg.conf GUI tool. I wan that too.

> 
2) a GUI to install single .deb files (which runs sudo dpkg -i name_of the file  automatically, with warning messages in windows) by doing a drag & drop of the file into an area of the desktop 

OR (the easiest thing to make) an "install" option available with a right click on the desired .deb file

The OR is more possible, and I want that too.

> 
3) A simplified and eye candy GUI to kernel compilator (menuconfig, etc.) with the following functions:
A button which installs all the packages which are required to compile a kerne

The following sections in which you only have to put a tick if you need it (a matter of mouse clicks)
DMA (to enable in the kernel)
Architecture (i386, amd64,etc.)
RAM Amount of (more than 1gb)
Filesystem support (ext3.etc.)
Framebuffer for Nvidia (in order to disable it)

A button to download the latest stable kernel source from Ubuntu and Kernel.org

A button to use your previous kernel settings to the new kernel (i.e. "sudo make oldconfig")

A section in which you can type the name of the new kernel

OPTIONAL (because it could be hard) The possibility to recompile the modules for the new kernel (nvidia, etc.) 

A button to Compile the kernel image and headers (which stands for the command sudo make-kpkg --initrd –append-to-version=-name_of_the_kernel kernel_image kernel_headers)

A button to install the new kernel and update GRUB

Could be possible (libranet has one) but will never be in Ubuntu. Ubuntu's development is aimed at the easiest of stuff. Kernel compelation will never be made easy enough, so a tool for it won't be included. Of course this is just my opinion, but I am the guy that reads more about Ubuntu than almost anyone.

> 
4) I know this should be up to the developers of the drivers: 
A better integration with the scripts of nvidia ati installers: some automated script which does everything for you  Then you can choose to use the installed driver by using the application I've dealth with in Point 1.

OR an application (with a GUI) which compiles the modules (e.g. nvidia or ati) for your current kernel


These drivers will always come from synaptic. Those that need the latest and greatest will have to mess with the junk. The repo drivers work great, so this is not really a problem.

So you were right. In my opinion, yes on the first two, no on the second two.

---

### Post by poofyhairguy on 2005-08-28
[QUOTE=skoal]
Toss sun dried cow shit over to your buddy like it were a frisbey? Throw a match on said frisbey, making things _really_ interesting with your buddy? Distil your own moonshine whisky, made from taters and the choicest rat droppings? Stand outside your front porch stark naked, spelling out your name in the dirt while taking a wiz?  Watch some twister pick up your neighbours house, waving to him as he circles and flails about aimlessly next to it, "Hey Superman! who's laughing now at my storm shelter?!"?  Or just walk over to a pond, get in a boat, and go fishin' with a 12 gauge Winchester?
[/QUOTE]

Skoal, sometimes its fun to play with stereotypes, but no one is going to beleive we have twisters that bad in Texas. This is not Kansas. 

That said, we do hunt fish with guns.....

---

### Post by poofyhairguy on 2005-08-28
[QUOTE=occy8]
I like to see  a website where a script checks your hardware and tells your if there will be a problem or not.[/QUOTE]

Good idea...but it would be hard to do.

---

### Post by occy8 on 2005-08-28
[QUOTE=poofyhairguy]Good idea...but it would be hard to do.[/QUOTE]

Hard but not impossible
You guys@ubuntu collect that sort of data in your hardware feedback thingy the mandriva people have someting where you can search for supported hardware ... there is a website for printers...
It just needs to be coordinated and since you want to attract windows people the script would have to read the hardware through windows

---

### Post by drizek on 2005-08-28
[QUOTE=tseliot]And I've found another thing about SUSE:

You can enable DMA from a GUI, AMAZING!

Here's the link to a screenshot:

[http://osdir.com/screenshots/index.php?directory=yast&currentPic=29](http://osdir.com/screenshots/index.php?directory=yast&currentPic=29)[/QUOTE]
 yes, suse and yast kick ass. 

its difficult to port yast to another distro though cause it has a lot of suse-specific things in it. that is why no distros adopted it after it went opensource a few months ago.

also, yast is Qt so the ubuntu devs would probably prefer something gtk.

---

### Post by npaladin2000 on 2005-08-28
The thought of making it "easy" to compile a new kernel for end users makes me shudder.  That's an advanced function and should be left to advanced users...kinda like messing with the registry in Windows.

Now, I MIGHT agree with making some sort of easy way to compile kernel modules against one's current kernel headers.  This way some of the more esoteric driver modules can be compiled and added in, without screwing with a kernel.  It'd take a lot less time anyway. ;)

I can agree with an xOrg configurator...Sax2 is nice.  Double-click install for debs is a good idea, and many have suggested it. 

As far as something for the NVIDIA and ATI drivers...they're not open-source and not likely to become so, so they can't be compiled.  (I disagree with saying they're "not free."  They're free and can be had without paying; they're just not open-source. Usually when people say "not free" for some reason they mean "Non-FOSS" which would be more accurate.     Anyway, right now Ubuntu does the same thing Microsoft does: installs a home-grown driver that comes with the OS, and doesn't support very much. If you want better driver support, you have to install the manufacturer's driver.  There's just no way around that...and those who have used these cards in Windows too will likely be used to that fact.

---

### Post by tseliot on 2005-08-29
[QUOTE=npaladin2000]...
As far as something for the NVIDIA and ATI drivers...they're not open-source and not likely to become so, so they can't be compiled.  (I disagree with saying they're "not free."  They're free and can be had without paying; they're just not open-source. Usually when people say "not free" for some reason they mean "Non-FOSS" which would be more accurate.     Anyway, right now Ubuntu does the same thing Microsoft does: installs a home-grown driver that comes with the OS, and doesn't support very much. If you want better driver support, you have to install the manufacturer's driver.  There's just no way around that...and those who have used these cards in Windows too will likely be used to that fact.[/QUOTE]
Yes, but in beta 3 of Open Suse you the update application asks you if you want to install nvidia drivers, if you answer yes they are installed. I wonder how SUSE can do such a thing.

I'll try SUSE as soon as I get my computer back from Compaq.

---

### Post by Brunellus on 2005-08-29
[QUOTE=npaladin2000]The thought of making it "easy" to compile a new kernel for end users makes me shudder.  That's an advanced function and should be left to advanced users...kinda like messing with the registry in Windows.

Now, I MIGHT agree with making some sort of easy way to compile kernel modules against one's current kernel headers.  This way some of the more esoteric driver modules can be compiled and added in, without screwing with a kernel.  It'd take a lot less time anyway. ;)

I can agree with an xOrg configurator...Sax2 is nice.  Double-click install for debs is a good idea, and many have suggested it. 

As far as something for the NVIDIA and ATI drivers...they're not open-source and not likely to become so, so they can't be compiled.  (I disagree with saying they're "not free."  They're free and can be had without paying; they're just not open-source. Usually when people say "not free" for some reason they mean "Non-FOSS" which would be more accurate.     Anyway, right now Ubuntu does the same thing Microsoft does: installs a home-grown driver that comes with the OS, and doesn't support very much. If you want better driver support, you have to install the manufacturer's driver.  There's just no way around that...and those who have used these cards in Windows too will likely be used to that fact.[/QUOTE]
 they're free in the sense of "gratis," but certainly not free in the sense of "libre."  Vanilla Ubuntu, for philosophical and legal reasons, must be both gratis and libre.  Dig?

---

### Post by Brunellus on 2005-08-29
a license?

---

### Post by Kvark on 2005-08-29
[QUOTE=npaladin2000]I disagree with saying they're "not free."  They're free and can be had without paying; they're just not open-source. Usually when people say "not free" for some reason they mean "Non-FOSS" which would be more accurate.[/QUOTE]
You got confused over a flaw in the English language, it uses the word free when refering to two entirely different things, both to freedom (libre) and to lack of cost (gratis).

To live in a prison is free as in gratis, you don't have to buy a prison cell or pay any rent. But it is not free as in libre, you can't do what you want to, come and go as you wish or repaint your cell.

To live in a house is free as in libre, you can do what you want in your house, come and go as you wish and make any changes you see fit to your house. But it is not free as in gratis, you had to pay for the house.

You are right in that the drivers don't cost anything and thus it would be wrong to say that they are not free as in gratis. But there is a restrictive licence agreement that dictates what you are and are not allowed to do with the drivers and you can't make any changes to them. Thats why people say that they are not free as in libre.

---

### Post by npaladin2000 on 2005-08-29
[QUOTE=Brunellus]they're free in the sense of "gratis," but certainly not free in the sense of "libre."  Vanilla Ubuntu, for philosophical and legal reasons, must be both gratis and libre.  Dig?[/QUOTE]

If you mean "free" as in "the pursuit of life, liberty, and the pursuit of happieness" then it's impossible for an inanimate object to be "free" in the sense of "libre," meaning "freedom." (People say "libre" translates to 'free" but it's more accurate to say it translates to "liberty" or "freedom.")  

Maybe open-source software means more freedom, but for the people who use the code, not the code itself.  Code just sits there. ;)  Libre is the state of having freedom, which is really limited to living, animate things. Code can't "have freedom," though the coder or the user can have freedom associated with what they do with the code.  However, the code itself must (usually) be open source in order for the person to have freedom to do whatever they do with it. The free part describes the state the person is in, not the code.  Code doesn't have the right to bear arms, or the right to trial by jury.     

That's why it's more accurare to say FOSS, because you're describing the software (the last S).  The F, for free, is the "as in beer" part.  The OS, for Open Source, is the part that provides the person "libre" or liberty, because the code is open source.  Please don't re-write the English language to fit one's own needs.  There's too many megalomaniacs out there trying to as it is. ;)

And now I'm getting into semantics.  But then again, some people are alwau\ys up for some antics.  :grin:    Anyway, remember, the person is free as in libre.  The software is open.

---

### Post by Stormy Eyes on 2005-08-29
[QUOTE=drizek]...and then that water washes off all the fertilizer into a river(do you have those in texas?)...[/QUOTE]

The Rio Grande forms a fair amount of Texas' southern border with Mexico.

---

### Post by Knome_fan on 2005-08-29
[QUOTE=npaladin2000] A pile of uninformed drivel[/QUOTE]
[http://en.wikipedia.org/wiki/Free_software](http://en.wikipedia.org/wiki/Free_software)
[http://en.wikipedia.org/wiki/Open_source_vs._free_software](http://en.wikipedia.org/wiki/Open_source_vs._free_software)
[http://www.gnu.org/philosophy/free-sw.html](http://www.gnu.org/philosophy/free-sw.html)

Just to get you started.

---

### Post by npaladin2000 on 2005-08-29
[QUOTE=Knome_fan][http://en.wikipedia.org/wiki/Free_software](http://en.wikipedia.org/wiki/Free_software)
[http://en.wikipedia.org/wiki/Open_source_vs._free_software](http://en.wikipedia.org/wiki/Open_source_vs._free_software)
[http://www.gnu.org/philosophy/free-sw.html](http://www.gnu.org/philosophy/free-sw.html)

Just to get you started.[/QUOTE]
 Knomey, calling it a pile of uninformed drivel, besides not making any sense whatsoever, does not help your point (quite frankly it makes the appearance of immaturity).   And most of those articles illustrate the same thing I did: the semantic problems with the definitions.  Free as in freedom doesn't make sense when applied to software; it's not free to do anything. Quite frankly it's only supposed to do what it's told, which is the polar opposite of freedom.

Software isn't free; the person is free.  The software enables the person to be free.  The software is open-source.  The open-ness is what makes it free. You know what group of people who want software to have freedom to do whatever it wants? Spyware authors and Microsoft. ;)

Incidentally, an overly-restrictive license that says you can see the code but not compile or modify it is not open-source, because it's not completely open..as in to use and modification.

"religious zealousism" and such attitudes that cause someone to refer to a reasoned explanation as a "pile of uninformed drivel" are exactly what drive people from Linux and Linux communities.  Keep in mind, freedom also means freedom for people to think as THEY choose, not freedom to think as YOU choose.  You can disagree, no problem.  But the phrase "pile of uninformed drivel" is not disagreement, it's insult, and nothing more.

I'm a major proponent of freedom. It's the most wonderful thing in the world.  But the term should be applied properly.

---

### Post by az on 2005-08-29
> **npaladin2000]If you mean "free" as in "the pursuit of life, liberty, and the pursuit of happieness" then it's impossible for an inanimate object to be "free" in the sense of "libre," meaning "freedom." (People say "libre" translates to 'free" but it's more accurate to say it translates to "liberty" or "freedom.")  [/QUOTE]

Actually, it means that it is not property.  So, it does pertain to inanimate objects.


[QUOTE=npaladin2000]Maybe open-source software means more freedom, but for the people who use the code, not the code itself.  Code just sits there.  said:**
> 

Bear arms?  I am so glad I do not live in the US.


[QUOTE=npaladin2000]That's why it's more accurare to say FOSS, because you're describing the software (the last S).  The F, for free, is the "as in beer" part.  The OS, for Open Source, is the part that provides the person "libre" or liberty, because the code is open source.  Please don't re-write the English language to fit one's own needs.  There's too many megalomaniacs out there trying to as it is. ;).
No.  Something can be open source and still be proprietary.  That means that you have the code, but you are not allowed to add to it, redistribute it, or copy it.  Being able to read the source code is only one small benefit of FLOSS.

Free Libre Open Source Software properly describes the concept which is opposite to proprietary software.



[QUOTE=npaladin2000]And now I'm getting into semantics.  But then again, some people are alwau\ys up for some antics.  :grin:    Anyway, remember, the person is free as in libre.  The software is open.[/QUOTE]

People are people and why should it be
That you and I should get along so 
awkwardly. - Depeche Mode.

Software is either Free-Libre-open-source or proprietary.

---

### Post by Knome_fan on 2005-08-29
> **npaladin2000]Knomey, calling it a pile of uninformed drivel, besides not making any sense whatsoever, does not help your point (quite frankly it makes the appearance of immaturity).
[/quote]
Ehm, my point was that it was uninformed drivel, so how does spelling it out not make my point?

[QUOTE=npaladin2000]
And most of those articles illustrate the same thing I did: the semantic problems with the definitions.  Free as in freedom doesn't make sense when applied to software said:**
> 
Jesue, if you had actually read the articles, you would by now have realized that freedom when it comes to software does not mean the software is free to what it wants, but that you or whoever uses it is free to do with it whatever he wants. That's not to hard to understand, is it?

[QUOTE=npaladin2000]
"religious zealousism" and such attitudes that cause someone to refer to a reasoned explanation as a "pile of uninformed drivel" are exactly what drive people from Linux and Linux communities.

Ah, I can't remember how many times I read this kind of bs on /. and the like if people don't have any arguments left. Rest assured, neither do I represent the linux community, whatever that may be, nor am I so important that my behaviour on some linux forum will drive people away from Linux.
And why pointing out that you don't know what you are talking about is "religious zealousism" is beyond me... (Btw., are you sure zealousism is even a word?)

[QUOTE=npaladin2000]
Keep in mind, freedom also means freedom for people to think as THEY choose, not freedom to think as YOU choose.  You can disagree, no problem.  But the phrase "pile of uninformed drivel" is not disagreement, it's insult, and nothing more.
[/quote]
No, it's an accurate description of what you wrote. You don't know what you are talking about, you don't know the least about what free software and open source mean and how they are related, yet you chose to write an awful lot about it.

[QUOTE=npaladin2000]
I'm a major proponent of freedom. It's the most wonderful thing in the world.  But the term should be applied properly.[/QUOTE]
And it is.

---

### Post by Wolki on 2005-08-29
[QUOTE=npaladin2000]That's why it's more accurare to say FOSS, because you're describing the software (the last S).  The F, for free, is the "as in beer" part.  The OS, for Open Source, is the part that provides the person "libre" or liberty, because the code is open source.[/QUOTE]

That's simply wrong. You can have source code that's open but still restricted in terms of 'freedom'. And you can have Free software that costs money.

Open Source is a term invented because it's more reassuring to companies.

---

### Post by Kvark on 2005-08-29
[QUOTE=npaladin2000]Incidentally, an overly-restrictive license that says you can see the code but not compile or modify it is not open-source, because it's not completely open..as in to use and modification.[/QUOTE]
It is open source if the code is available in a human readable form, period. The important difference between open source and close source is that you can check under the hood to confirm that the program doesn't have any hidden trojans or such. Propriarity software vs whatever the opposite should be called is an entirely different matter. A program can very well come with both open source code and a propriarity licence at the same time.

So... it is propriarity if it comes with a licence/EULA/patent that restricts what you are allowed to do with it. What would you call software that you are allowed to use for any purpose, share with anyone you want and modify in any way you want?

---

### Post by npaladin2000 on 2005-08-29
[QUOTE=Kvark]It is open source if the code is available in a human readable form, period. The important difference between open source and close source is that you can check under the hood to confirm that the program doesn't have any hidden trojans or such. Propriarity software vs whatever the opposite should be called is an entirely different matter. A program can very well come with both open source code and a propriarity licence at the same time.

So... it is propriarity if it comes with a licence/EULA/patent that restricts what you are allowed to do with it. What would you call software that you are allowed to use for any purpose, share with anyone you want and modify in any way you want?[/QUOTE]

I'd call it open.  If it comes with a proprietary license but the source is still available then a: it's a rather dumb thing to do because people are going to learn from it and use it anyway.  And b: not really 100% open source anyway.  Closer to closed...people can look in the window but not come in the house. But looking in the window still means you can "borrow"/steal some of the design ideas and use them in your own house. 

You know what code that some are allowed to look at but not modify or redistribute is?  Shared source.  See Microsoft. You might not like them, but they already defined a term for "open to some, but restricted in what you can do with it."

Just using the term "free" invites confusion.  Why do you think there's so much written up about it?  Of course, i think there are some out there who use the term to intentionally create confusion, but I'm a conspiracy theorist. ;)

---

### Post by npaladin2000 on 2005-08-29
[QUOTE=Wolki]That's simply wrong. You can have source code that's open but still restricted in terms of 'freedom'. And you can have Free software that costs money.

Open Source is a term invented because it's more reassuring to companies.[/QUOTE]

If you want to get technical, the GPL is restricted in terms of "freedom" too. Probably the most freedom-producing licensing out there is the BSD-style license.

---

### Post by Knome_fan on 2005-08-29
[QUOTE=npaladin2000]If you want to get technical, the GPL is restricted in terms of "freedom" too. Probably the most freedom-producing licensing out there is the BSD-style license.[/QUOTE]

Well, if you want to get technical about it proponents of the GPL argue that it is the freest license, as it is the license that protects freedom, contrary to the BSD license for example. (You would of course have found that out already had you bothered reading up on the subject before writing about it...)

---

### Post by npaladin2000 on 2005-08-29
[QUOTE=Knome_fan]Well, if you want to get technical about it proponents of the GPL argue that it is the freest license, as it is the license that protects freedom, contrary to the BSD license for example. (You would of course have found that out already had you bothered reading up on the subject before writing about it...)[/QUOTE]

The biggest difference between the two is the freedom/restriction one:  Where the BSD license allows you to use the source to compile and release a closed-source application provided you give credit to the original author, the GPL prevents you from doing so by specifiying that all code based/derived from a piece of GPL code must always be GPL.  That's less freedom for everyone but the author(s).  Proponents argue in favor of it because it helps out their freedom.  Opponents argue against it because it impedes their freedom.  

I can understand the reasoning for writing the GPL that way, because some coders might not want to see someone use their code in that way.  But that means the author is telling you what you can and can't do with the code. Technically the BSD-style license does that too, but it's less restrictive. 

I'm probably going to ignore you soon if you keep trying to use the little snide comments.  I'm only here for intelligent discussion.

---

### Post by Knome_fan on 2005-08-29
Again, the argument the GPL proponents are making is that it is in fact freer, as it presevers freedom. 

And the point is not that the authors get more freedom with the GPL, but that everyone who uses the code in the long run will have the same freedom  as the one who got it under the GPL in the first place. 

Though you threaten to ignore me for comments like this, the GNU site I linked to really has a lot on this very subject.

Now you can of course disagree with this assessment, but please, for the sake of an intelligent discussion, at least try to inform yourself about the subject at hand before engaging in a discussion. 

P.S.:
Don't you think it's a little bit inconsistent that you are now arguing about which license is freer, while only a short while ago you informed us there wasn't something like free software anyway?

---

### Post by Wolki on 2005-08-29
[QUOTE=npaladin2000]If you want to get technical, the GPL is restricted in terms of "freedom" too. Probably the most freedom-producing licensing out there is the BSD-style license.[/QUOTE]

If you want to get technical, software under the GPL is free software by definition. Stallman defined the term, based on four kinds of freedom. You can, of course, argue whether it is really free. I doubt, however, that a productive discussion will come from it.

---

### Post by npaladin2000 on 2005-08-29
[QUOTE=Knome_fan]P.S.:
Don't you think it's a little bit inconsistent that you are now arguing about which license is freer, while only a short while ago you informed us there wasn't something like free software anyway?[/QUOTE]

Actually, I'm discussing which license provides more freedom and to whom, if you'll read carefully. ;)  

Am I free to take a piece of GPL code, compile it along with some code I wrote and distribute it without revealing my own source code?  Nope.  I am required to open my source as well; I have no choice. Those are the terms of the license. 

That doesn't quite preserve freedom, as it dictates (quite exactly) what you're allowed to do with the code.  It DOES, however, preserve the ideal of open-sourcing software allowing everyone to see and tweak source code (so long as they agree to the restriction that they MUST pass it along the same way and are not free to do anything else).  That's certainly not a bad thing (to most people anyway).  But why not call a fish a fish?

---

### Post by Knome_fan on 2005-08-29
It preserves the freedom of the code.

Person A creats GPL software.
Person B gets the software and the code from person A.
Person B is now free to do with it whatever the hell he wants.
Now if Person B decides to either gives the unchanged software, or software incorporating the work form person A to person C, he has to grant person C the same rights he received from person A.
Person C is now free to do with the software and the code whatever he wants.

The freedom is preserved. 

Btw., how can a software license provide freedom, while according to you software can't be free anyway?

---

### Post by poofyhairguy on 2005-08-29
Yall are confusing me a lot. Please no BSD vs GPL flame war here. We all know that the GPL puts a priority on freedom for the USER and the BSD License puts priority on freedom for the DEVELOPER. No need to argue anything, that is obvious.

---

### Post by npaladin2000 on 2005-08-29
[QUOTE=Knome_fan]Btw., how can a software license provide freedom, while according to you software can't be free anyway?[/QUOTE]

Software and it's license provide freedom to a person.  A piece of inanimate code can't be free as in libre; the person in posession of it can, and, in fact, is the only entity associated with this whole thing that is able to excercise any freedom.  That was my original point, remember?  The fact that semantically, saying "free software" meaning "libre" is incorrect.  The person who has the code is free.  The software is open.  

Just wanted to re-iterate that before I go to bed. I realize there are some out there who WANT "free software" to be the common term, and there's a reason for that: PR.  If something's associated with increased freedom it's seen as better. "Promoting open-ness" doesn't sound as dramatic, even though technically, that's EXACTLY what the GPL does.  I believe in promoting open-ness; it's a great thing.  I just insist on calling it exactly what it is.   I also believe in promoting freedom, but I think it should be done for the right reasons, not because it's the latest en-vogue catch-phrase associated with some bandwagon.   One should never blindly hop on a bandwagon; one should always think about their position before they accept it as their own.   

And now it's sleepy time; I have to work tonight.

---

### Post by npaladin2000 on 2005-08-29
[QUOTE=poofyhairguy]Yall are confusing me a lot. Please no BSD vs GPL flame war here. We all know that the GPL puts a priority on freedom for the USER and the BSD License puts priority on freedom for the DEVELOPER. No need to argue anything, that is obvious.[/QUOTE]

Uhh...you sure it isn't the other way around?

---

### Post by neighborlee on 2005-08-29
[QUOTE=mstlyevil]I just wouldn't worry about appealing to Windows users who are too lazy to switch. Linux is not windows nor should it be. My brother thinks I am crazy for using Linux. He told me straight up he would not switch because he is used to the way Windows works and he is used to the way IE works and does not want to relearn a new OS.  You just cannot appeal to these people no matter what you do. I know people that will not switch from 98 or 2000 to XP because some things are different. They will not switch till they have to.  So I think trying to appeal to lazy Windows users is a waste of time. Now on the other hand I think there are plenty of things that might appeal to Windows users that are fed up with the garbage they put up with using M$.  Outside of Gaming, you can do everything a windows machine can do if you are willing to take the time to learn. You also get many applications in Linux for free that does not come with a paid copy of windows. All we need to do is get the information out there that Linux is a viable alternative to windows.[/QUOTE]

its only a 'viable' alternative if its easy to use just like windows or macOSX.  You will not help gain market share for linux withhout that mentality I guarnatee it.

Linspire is doing a decent job and they sure have a easy to use system with clear drawbacks ( not free either OS wize or CNR wize though you can argue merits of CNR if you want).  Suse and mandrake are easy to use and are at the top at distrowatch although both clealry have their drawbacks. Mepis ( although I dont like the author at all ) is near the top  due to advertising and of course having a easy to use DE along with features that mean , once installed you do NOTHING to surf and listen to music and watch DVD's, plus the author I admit was smart for designing , out of the box, a livecd/installer and all of it on one CD.  My only complaint there is the use of kde for which I can't abide due to qt not living up to the standards of gtk. That is my philosophy meaning if your a cooporate user , you can still use gtk and not pay for the priviledge ( yes I know about bsd vs gtk but I prefer the open source arguement more than the developer arguement ).

I chose ubuntu as I liked the community, but this easy to use attack and forget windows users bashing has me rethinking that decision frankly, as I have not seen too many 'counter arguements' to these ignorant claims.


united we stand and divided we go splat-.

[http://www.newsforge.com/article.pl?sid=03/08/13/1424212](http://www.newsforge.com/article.pl?sid=03/08/13/1424212) < interesting little article and id say very worthy of a read.

cheers
nl

---

### Post by poofyhairguy on 2005-08-29
[QUOTE=npaladin2000]
Just wanted to re-iterate that before I go to bed. I realize there are some out there who WANT "free software" to be the common term, and there's a reason for that: PR.  If something's associated with increased freedom it's seen as better. "Promoting open-ness" doesn't sound as dramatic, even though technically, that's EXACTLY what the GPL does.  I believe in promoting open-ness; it's a great thing.  I just insist on calling it exactly what it is.   I also believe in promoting freedom, but I think it should be done for the right reasons, not because it's the latest en-vogue catch-phrase associated with some bandwagon.   One should never blindly hop on a bandwagon; one should always think about their position before they accept it as their own.   
[/QUOTE]

I think the best term is Libre software.

---

### Post by poofyhairguy on 2005-08-29
[QUOTE=npaladin2000]Uhh...you sure it isn't the other way around?[/QUOTE]

Positive. The GPL forces developers that use GPL code to release the source code for everything under the GPL. This is great for users, because that means they can always get the newest GPL code for free (beer kind), and all code that messes with it is opened up for their use. Its less good for developers, because they cannot USE the newest GPL for free (again as in beer) without opening their code. This mislabeled "virus" effect. It simply makes it harder to sell GPL software and make money. It better for users.

With BSD, the developer can use the newest released code in any of their own projects without having to open the product's code. Users can use the new BSD code all they want (like GPL), but they don't get to have free (beer) use of code that uses this BSD code then sells it in a closed product.  No "virus" effect to liberate users from the cost of software. Its better for developers. 

There are some exceptions, but considering how most of the software market is today, this is the truth.

---

### Post by poofyhairguy on 2005-08-29
[QUOTE=neighborlee]its only a 'viable' alternative if its easy to use just like windows or macOSX.  You will not help gain market share for linux withhout that mentality I guarnatee it.[/QUOTE]

False. Very false. Ubuntu can (and does focus) on the MOST OF THE WORLD that lacks a Computer right now, and grow to double digit marketshare completely with this part of the market.....not a single Windows user needs to be converted to make this happen.

The honest truth is that Linux (TODAY) is easier to use than Max OSX or Windows. My sister has less trouble with her cell phone (runs Linux) and her Tivo (runs Linux) than her Powerbook (OSX) and Sony Viao (with XP). 

But for the wasteland that is IBM compatible x86 world (I like to call them "Dells") Linux will never be the easiest. Why? Because it will always lack drivers. Even with enough marketshare, some companies no longer exist (only XP drivers there). Some companies can't make good Windows drivers, so there is little hope that they will make good Linux ones.

Apple gets around this by selling OSX only on their boxes. Makes driver problems go away. MS depends on the manufacturers to make drivers, and often they don't do a good job. Driver problems witll not go away. Everytime Linux catches up (802.11b, USB drive support, etc.) the new wave of computer hardware hits that won't work with Linux (802.11g, Webcams with chat software, etc.). Its an endless cycle.

I avoid problems by buying hardware that works with Linux. It costs me my time (to research) and my money (to replace non compatible stuff). I call that "the real cost of Linux." It does not bug me, I like Linux more. But many users won't agree. And Desktop Linux won't be for them. It will invade their life through Tivo's, Playstations, Cell Phones, Cars, etc.

> , once installed you do NOTHING to surf and listen to music and watch DVD's, plus the author I admit was smart for designing , out of the box, a livecd/installer and all of it on one CD.  

Its nice Mepis can do all of that out of the box. The creator of Mepis decided it was worth the legal risk (seeing how he lives in the U.S.) to include these things, even though that is against U.S. law (for some, risks a lawsuit for others). He is playing the odds, going on the fact that almost no one has been suied for distributing these things. Ubuntu runs on the assumption that when Desktop Linux gets popular enough, the legal problems WILL come, so don't do anything illegal. I'm glad both exist.

> 
I chose ubuntu as I liked the community, but this easy to use attack and forget windows users bashing has me rethinking that decision frankly, as I have not seen too many 'counter arguements' to these ignorant claims.

You probably don't know the context. For some reason, this month, this is like the 10th editiorial we have had in here about how "Ubuntu needs to change things, and copy Windows on these things" to get popular. Despite the fact that everytime I (or someone) tells them that "the only official channel to the developers is bugzilla, posting this here only gives people things to argue about." So people are just tired of it. We have hit both sides so many times recently its boring. So we are just copying and pasting responses (not this one). 

I would just close the threads, but then people will say "we are trying to hide something." If I let them go people like yourself coming in halfway will think we are mean (when we are not). So its a lose-lose situation. Can't win. I don't try. No one does.

Pick your OS for its technical merits. Thats what matters. I like the techinical merits of Ubuntu. Don't let the community sway you- we have no way to police our fellow members besides moderation....everyone is welcome.


> 
united we stand and divided we go splat-.


Gnu is a divided landscape. Almost nothing can bring it together. We are lucky there is only one kernel,  one major xserver and two big DEs.

---

### Post by mstlyevil on 2005-08-29
> its only a 'viable' alternative if its easy to use just like windows or macOSX. You will not help gain market share for linux withhout that mentality I guarnatee it. 

  I sure in the hell didn't find windows easy to use when I first started using it. People are just used to windows because that is all they know. I could care less if they adopt Linux. If they are too lazy to try it out because it is different, that is their problem, not mine.  I haven't had one virus or one instance of adware, spyware, or malware since switching.  I have a lot easier time setting up Linux then I ever did XP. I can have Ubunu installed and fully runnig in about 2 hours. It takes me 5 or 6 hours to have XP up and running. ubuntu is by far easier to set up and run once you get used it. different does not make something harder.

---

### Post by neighborlee on 2005-08-29
[QUOTE=mstlyevil]I sure in the hell didn't find windows easy to use when I first started using it. People are just used to windows because that is all they know. I could care less if they adopt Linux. If they are too lazy to try it out because it is different, that is their problem, not mine.  I haven't had one virus or one instance of adware, spyware, or malware since switching.  I have a lot easier time setting up Linux then I ever did XP. I can have Ubunu installed and fully runnig in about 2 hours. It takes me 5 or 6 hours to have XP up and running. ubuntu is by far easier to set up and run once you get used it. different does not make something harder.[/QUOTE]

 I guess this is your version of 'this is why you should use linux 101: first RTFM' ?

thats part of the problem is that kind of attitude, and to THINK I thought it only exited in debianland.  oh wait..I AM in debianland..sorry for a while I forgot that.

...

---

### Post by mstlyevil on 2005-08-29
[QUOTE=neighborlee]I guess this is your version of 'this is why you should use linux 101: first RTFM' ?

thats part of the problem is that kind of attitude, and to THINK I thought it only exited in debianland.  oh wait..I AM in debianland..sorry for a while I forgot that.

...[/QUOTE]
  My opinion by no means reflects the entire Linux community. (Disclaimer)

 What part of I could care less if you use Linux or not do you not understand. I think you really believe I care that the whole world embraces Linux. I like and use Ubuntu because it works for me. If some one expresses an interest and wants to try Ubuntu/Linux, I am more than willing to help them get started.  I am 36 years old and life is too short to be caring about what everyone thinks about the choices I made in my life including my OS. I am new to Linux and am having a positive experience. I do not need morons like you telling me how horrible something is and then you want me to say oh I'm sorry for my attitude when you are the one with the problem. What do ypu want me to do? Sing the praises of Microsoft? Windows has it's good points but the bad is far weighter than the good. It is people who are fed up with the BUGS in windows and the constant crashes, viruses,spyware,driver conflicts,lack of programs for a OS you PAID $300 dollars for. It is these people as I run across them that I will hand them a live CD of Ubuntu to try and let them decide for THEMSELVES if Ubuntu is right for them.

---

### Post by occy8 on 2005-08-29
[QUOTE=poofyhairguy]
But for the wasteland that is IBM compatible x86 world (I like to call them "Dells") Linux will never be the easiest. Why? Because it will always lack drivers. Even with enough marketshare, some companies no longer exist (only XP drivers there). Some companies can't make good Windows drivers, so there is little hope that they will make good Linux ones.

Apple gets around this by selling OSX only on their boxes. Makes driver problems go away. MS depends on the manufacturers to make drivers, and often they don't do a good job. Driver problems witll not go away. Everytime Linux catches up (802.11b, USB drive support, etc.) the new wave of computer hardware hits that won't work with Linux (802.11g, Webcams with chat software, etc.). Its an endless cycle.

I avoid problems by buying hardware that works with Linux. It costs me my time (to research) and my money (to replace non compatible stuff). I call that "the real cost of Linux." It does not bug me, I like Linux more. But many users won't agree. And Desktop Linux won't be for them. It will invade their life through Tivo's, Playstations, Cell Phones, Cars, etc.
[/QUOTE]

Thats how the Microsoft Wintel cycle works, buy new hardware and you have to upgrade your Windows, or when you buy new Windows you need new hardware

At least in Linux you can get most things running, if you are prepared to invest a lot of time, or you are really smart :wink: 

It can be cheaper too if you build a new system and for better support you don't use the latest hardware. A couple of days ago I talked about a hardware database. I couldn't remember this one I think it's the best by design [http://hardware.linuxfaqs.de/](http://hardware.linuxfaqs.de/)

---

### Post by neighborlee on 2005-08-29
[QUOTE=poofyhairguy]

I would just close the threads, but then people will say "we are trying to hide something." If I let them go people like yourself coming in halfway will think we are mean (when we are not). So its a lose-lose situation. Can't win. I don't try. No one does.

Gnu is a divided landscape. Almost nothing can bring it together. We are lucky there is only one kernel,  one major xserver and two big DEs.[/QUOTE]]


coming in halfway ?..no actually I read entire thread before weighing in. ;-)

I dont need to be reminded of a given mindset with certain unplesantness, so lets get beyond that point .  My point throughout was simply that things need to be practical and efficient to use ,  not unlike other OS's with proven track records at least up till now .  I reiterate that arklinux CC is sweet albeit those might label it a total clone and maybe so, but its very well done and pleasing to look at.  It would be nice to know what the intended fix is for our CC and what it might look like, and be able to weigh in on the process before its gold.

thx
nl

---

