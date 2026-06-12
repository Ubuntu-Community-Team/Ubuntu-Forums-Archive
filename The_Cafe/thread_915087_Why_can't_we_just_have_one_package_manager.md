---
title: "Why can't we just have one package manager?"
date: 2008-09-09
forum: The Cafe
---

### Post by anotherdisciple on 2008-09-09
It would be nice if we found an alternative to .deb and .rpm. Some Package manager that every distro used. 

Would that make it easier to make programs install on multiple distros? I would think so... but I've never put together a .deb or .rpm... so I don't fully understand the concepts behind them.

Would we need their commands and filesystems to be more closely related also?

---

### Post by swisscow on 2008-09-09
Not sure if I agree as you can  convert easily enough from rpm to deb using alien (don't know about the other way) and binaries can be compiled and installed without too much hassle (cough)

I hear what you say but personally I'd rather all those really clever programming type people out there spent their time filling the "gaps", i.e. where linux is a bit thin, such as video editing .

That's my 2 cents worth

---

### Post by insane_alien on 2008-09-09
source always works...

---

### Post by LaRoza on 2008-09-09
> **anotherdisciple said:**
> It would be nice if we found an alternative to .deb and .rpm. Some Package manager that every distro used. 

Would that make it easier to make programs install on multiple distros? I would think so... but I've never put together a .deb or .rpm... so I don't fully understand the concepts behind them.


What can't Windows have a unified packaging system? Look into it. It isn't as unified and actually much more random than anything Linux has.

There is a universal packaging system for all OS's (even non-Linux's). It is called source.

---

### Post by anotherdisciple on 2008-09-09
> **LaRoza said:**
> What can't Windows have a unified packaging system? Look into it. It isn't as unified and actually much more random than anything Linux has.

There is a universal packaging system for all OS's (even non-Linux's). It is called source.

True... I just like the ease of .deb ... It would be nice to have all the distros use one package manager.

---

### Post by cardinals_fan on 2008-09-09
> **anotherdisciple said:**
> True... I just like the ease of .deb ... It would be nice to have all the distros use one package manager.
...and .deb is not a package manager.

---

### Post by starcannon on 2008-09-09
> **anotherdisciple said:**
> It would be nice if we found an alternative to .deb and .rpm. Some Package manager that every distro used. 

Would that make it easier to make programs install on multiple distros? I would think so... but I've never put together a .deb or .rpm... so I don't fully understand the concepts behind them.

Would we need their commands and filesystems to be more closely related also?

The answer is.... drum roll please....

For the same reason we can't have just one flavor of ice-cream.

not being trollish or smart*strik, there are many people that prefer package management system x over package management system y. Its all about choice.
Occasionally someone will put out a .bin(ary) with scripts that let it install on most flavors of linux, nvidia drivers for instance, thats about as close as you going to get though, and even it is comiling from source so it kinda fits LaRoza's version of the once size fits all.

---

### Post by y@w on 2008-09-09
> **starcannon said:**
> The answer is.... drum roll please....

For the same reason we can't have just one flavor of ice-cream.

not being trollish or smart*strik, there are many people that prefer package management system x over package management system y. Its all about choice.

Also the same reason we have more than one political party :)

But for real, there's also lots of choices in distros. All have their advantages and disadvantages, just a matter of preference.

---

### Post by toupeiro on 2008-09-09
> **LaRoza said:**
> What can't Windows have a unified packaging system? Look into it. It isn't as unified and actually much more random than anything Linux has.

There is a universal packaging system for all OS's (even non-Linux's). It is called source.

+10,000

/signed: a former Windows software packager!

Installshield
Wise
Nullsoft
Acronis
SMS
ScriptLogic
BigFix
MSI
MST
MSP
Pre-compiled EXE
Batch
VBS
file extraction from zips or cabs
and many more....

ugh, windows is WORSE in so many ways...


and quite frankly, by unification you mean you want to be able to install redhat packages, you can actually install RPM on your ubuntu system... (sudo apt-get install rpm)  Mileage may vary, but whatever.

---

### Post by Polygon on 2008-09-09
becuase linux is source compatible not binary compatible.

---

### Post by chris4585 on 2008-09-10
> **toupeiro said:**
> +10,000

/signed: a former Windows software packager!

Installshield
Wise
Nullsoft
Acronis
SMS
ScriptLogic
BigFix
MSI
MST
MSP
Pre-compiled EXE
Batch
VBS
file extraction from zips or cabs
and many more....

ugh, windows is WORSE in so many ways...


and quite frankly, by unification you mean you want to be able to install redhat packages, you can actually install RPM on your ubuntu system... (sudo apt-get install rpm)  Mileage may vary, but whatever.

not bashing linux, but truthfully don't all of those installers work on more versions of windows than any one type of package manager would for linux?  I mean who cares is it all works.

---

### Post by SomeGuyDude on 2008-09-10
I think the OP meant it'd be nice if there was a way (aside from compiling from source) that all installation of software could be done on every Linux distro. It really is one of the reasons that people get annoyed with the OS who aren't comfortable with too much CLI and dependency-hunting.

It's a big reason I stick with Ubuntu, frankly.

---

### Post by loell on 2008-09-10
people always mixed up package management from a package manager.. ;) sigh.. :)

---

### Post by irrdev on 2008-09-10
It would be easier if all the distros chose either deb or rpm, there is no need for *another* package format (there are several though!). That goal isn't realistic, however. There are over 1000 linux distros available, and while Ubuntu as #1 uses deb, both openSUSE as #2 and Fedora as #3 use rpm. That said, openSUSE and Fedora rpms are not compatible with each other, due to modifications in openSUSE's new zypper package manager. It's too bad, since package management is both the strong and weak point of linux. For distros such as Ubuntu, enough packages are made available by the community. However, smaller distros starting up have a hard time of making it, due to the small userbase at the beginning. That is why I applaud direct Ubuntu spinoffs such as Linux Mint, which make full use of the Ubuntu repositories. If more distros in the future follow suit, this will be the best step forwards to unifying package management. As for openSUSE, Fedora and Red Hat linux, they are simply to entrenched as rpm-based distros to make the switch. Likewise, Ubuntu and Debian can't afford drop the deb format. It's too bad, but I think you have to accept it as part of Linux. As somebody already mentioned above, Source code is the only cross-platform package format on Linux, or on any operating system for that matter! :grin:

---

### Post by klange on 2008-09-10
Consider this:
When it comes to package format, RPM is considered the "one". But RPM sucks. Before we can have one package management system, we need one package format, and as that one format has already been set and it's one that is inferior, we'll never see the day when Deb (etc.) users succumb.

@"Source = Unified": And how do I compile it? make && make install? ./configure first? autotools? Source isn't truly universal. (There's also -dev package names and such that are hard to trace.)

---

### Post by geoken on 2008-09-10
There should be one package format/manager with clearly indicated and updated listing of what versions of specific libraries are current. This way, if a dev uses a new version of a library (because it has some features they needs), they'll know they need to supply the library themselves. Right now they need to look out into the Distro soup and try to figure out which distros have the correct library in their repositories and which don't.

---

### Post by billgoldberg on 2008-09-10
> **anotherdisciple said:**
> It would be nice if we found an alternative to .deb and .rpm. Some Package manager that every distro used. 

Would that make it easier to make programs install on multiple distros? I would think so... but I've never put together a .deb or .rpm... so I don't fully understand the concepts behind them.

Would we need their commands and filesystems to be more closely related also?

I hardly come across a .rpm package these days.

Sites like getdeb.net are useful and the repos have most things anyway.

You can always compile from source if there isn't a .deb package available.

--

The package manager in Ubuntu is apt, not dpkg (.deb).

---

### Post by anotherdisciple on 2008-09-10
> **cardinals_fan said:**
> ...and .deb is not a package manager.

Yes, I know... I mean I like how easy it is to work with .deb packages.

---

### Post by qazwsx on 2008-09-10
You just can not  grab deb and install it. Try out some old stable debian packages and you may have a problem. 

Third party deb packages may contain some scripts which can seriously harm your system.

I mean packages are not necesseraly compatible with your system.


Besides apt can use rpm repos ;) And for example with KPackage frontend  you can even install rpm packages (if you really want some troubles).

---

### Post by anotherdisciple on 2008-09-10
> **SomeGuyDude said:**
> I think the OP meant it'd be nice if there was a way (aside from compiling from source) that all installation of software could be done on every Linux distro. It really is one of the reasons that people get annoyed with the OS who aren't comfortable with too much CLI and dependency-hunting.

It's a big reason I stick with Ubuntu, frankly.

YES! That's exactly what I'm trying to say!

---

### Post by toupeiro on 2008-09-10
> **chris4585 said:**
> not bashing linux, but truthfully don't all of those installers work on more versions of windows than any one type of package manager would for linux?  I mean who cares is it all works.

yes and no.

Script logic installers will only install with a scriptlogic client service, yet scriptlogic is a very prominent enterprise packager

SMS packages are deployed with a Microsoft SMS client

MSI packages are only installable with a Microsoft Windows installer service, and that is also version specific.

MST files can only be used as overlays to MSI Files IF you have Windows installer service 2.0 or better.  Not that they didn't exist before that, they just didn't work.

MSP are package files that can only be used to patch installations that were originally MSI installations done with windows installer service 3.0 or better.  Not that didn't exist before that, they just didn't work.

Installshield logs proprietary installation GUIDS in the registry outside of the typical HKLM/Software/Microsoft/Windows/CurrentVersion/Uninstall area, and if you are ever unfortunate enough to blow up an installshield installation, it will corrupt your installation database and many times you are NEVER able to install anything packaged with installshield again.

Bigfix uses a completely proprietary packaging script language and deployment methodology, yet is also highly prominent in the enterprise.

VBS will only work on versions of windows with a cscript or wscript interpreter.  

Batch and traditional file extractor installations usually always work unless you run into DLL version conflict or need to do anything advanced which is why they are not always used, however **all of them** use different methodologies for packaging, compiling the package, or executing the installation if file copies, as well as handling pre and post execution processes.

man, I almost forgot, a few years ago, Intuit got into the packaging game, creating yet another proprietary packaging methodology for their widely used IT management software package, Track-IT.

Do they all work?  Maybe to the laymen, yes, but if you take a closer look, or eventually get some software in a package format you don't have an interpreter service for, its a horrible disgusting mess, far worse than linux.  Installing Windows installer or using a bigfix client is no different than needing rpm installed on my machine to install rpm packages.


What windows DOESN'T have is a tool that can take a SMS package and convert it into one or several different packages.  Why?  Because No vendor in the package management business on windows wants you to.  In their minds, they think their way is superior, and want your money, so the odds of you seeing anything as innovative as alien for windows packages and remaining legal to use is practically 0.

I'm not bashing windows, a lot of these methods aren't even Microsoft applications, but they are all Microsoft endorsed. If you're trying to make a comparison between windows and linux on package management/managers (an irrelevant semantic IMO) saying windows is superior, you've obviously never done any packaging for windows. :)  If your complaint is that an rpm won't execute by default on a debian system, then just install the RPM debian package, or use alien to convert it to deb, or get the source for rpm, and use the rpm switches to simply extract the files and scripts...  You have so many options.  In windows, you have very, very few outside of what you are given.

EDIT:

What it boils down to is that Microsoft controls every aspect of windows, and vendors mold their software to fit the shape of windows while trying to remain unique and innovative.  Linux based operating systems sacrifice the "one entity determines master design" philosophy to allow for diverse and talented user communities to mold the shape of the OS.  If you want one entity telling you how to use your computer, that is very easy to do, stick with windows, or stick with ONE Linux distribution.  In my opinion, the root cause to the perceived package management situation is likely the very same thing you'd praise linux for in another thread, and I'm sorry, but you can't have it both ways as it suits you unless you take the initiative to learn how to make the packages work in places they weren't designed to, or convert them, or get them by another means.  The truth of the matter is that its not that you CAN'T use RPM's in a debian based OS, its that you can't do it quite as easily as you can in a redhat based OS...

:-({|=

my lengthy .02

---

### Post by anotherdisciple on 2008-09-10
Holy smokes toupeiro! That's a lot of reply! haha... but I understand your side. It's just a bummer that it can't work both ways. Linux is very innovative... it's nearly impossible to make innovation work only one way!

---

### Post by quinnten83 on 2008-09-10
> **SomeGuyDude said:**
> I think the OP meant it'd be nice if there was a way (aside from compiling from source) that all installation of software could be done on every Linux distro. It really is one of the reasons that people get annoyed with the OS who aren't comfortable with too much CLI and dependency-hunting.

It's a big reason I stick with Ubuntu, frankly.
Amen!
and running .sh files or .run files, requires using command line and personally I don't feel like touching source, because i don't want the hassle.
The only time i use source is for my wacom tablet, and even then I wait until someone has created a detailed howto.

I wish all distro's would use debian package manager though. I kinda think that Yum sucks and yast is not much better.

EDIT: i don't like to use source because I am always scared I will break something so badly my entire system no longer will function.

---

### Post by Swarms on 2008-09-10
From an user who is tired of compiling, running .sh scripts etc.

I must say taht SomeGuyDude hits the nail.

---

### Post by 2cute4u on 2008-09-10
> **billgoldberg said:**
> 
You can always compile from source if there isn't a .deb package available.


No, YOU can always compile from source, but 95 percent of computer users can't.   As long as people like you keep stating things like that,  then people will always think "Linux is just for Geeks", and from your other posts it seems that you want it that way.

What we need isn't to only have one package manager, what we need an easy to use package manager that is capable of installing packages in all formats. It also needs to be able to be able to install both from repositories and local files.    If synaptic package manager had alien built into it, and a local "repository" folder, where we can  drag and drop any kind of package; that would do the job nicely.

---

### Post by NTolerance on 2008-09-10
[http://www.packagekit.org/pk-intro.html](http://www.packagekit.org/pk-intro.html)

---

### Post by dasunst3r on 2008-09-10
No matter what package manager you use, just remember that you're better off than Windows.  Every time I start up Windows, so many things pop up and asks you whether you want to update.  Sometimes, it drives you to your knees begging, "PLEEEEEEEEEEASE!  I just want to use my computer!"  In most distributions, this is not so -- the only update notification I get is a dinky little icon on the panel that I can click whenever I want.

---

### Post by mips on 2008-09-10
Well if we had to have only one could it please be [pacman]("http://en.wikipedia.org/wiki/Pacman_%28package_manager%29")?!

---

### Post by smartboyathome on 2008-09-10
I agree with mips, I like pacman. But that just shows that people like different package managers, as well as everything else. If you remove that, then people will start fighting over what features should and should not be in that one package manager, leading again to fragmentation of package management and package managers.

---

### Post by toupeiro on 2008-09-10
> **smartboyathome said:**
> I agree with mips, I like pacman. But that just shows that people like different package managers, as well as everything else. If you remove that, then people will start fighting over what features should and should not be in that one package manager, leading again to fragmentation of package management and package managers.

Well said.

I really just wish that people would treat Linux Operating systems as primary colors and not shades of grey.  What I mean is, Embrace the fact that each is different, with a lot of time, thought and development going into each one, and very strong reasons for implementing the things they did, and choose the one which works best for you!  You could virtually argue this point on so many things:

SELinux versus AppArmor, Sudo versus RBAC, Gnome versus KDE... the list could go on virtually forever...

I used to take the stance very firmly about package management consolidation.  I felt Linux needed it to succeed, but as time went on, my opinion about that began to change, as I started to realize what would be compromised in doing something like that.  

How many things in RPM do you really come across that do not have a debian alternative, or vice versa?  If neither, how many of them have a nice, easy installer?  Such as: NVidia drivers and citrix ICA, or google-earth as examples?  I just don't run into it at all anymore...  It seems that the worst case scenario is that you have a choice.  Imagine if you didn't?

If you say there should be one way to fetch packages, imagine that this was chosen for you, and it was YaST, or heck even more fun, the OpenSolaris Pkg-get or whatever its called.  Well, now you have one uniform way of getting your apps.  All development on yum, yast, aptitude and all the others die out because pkg-get is now the universal package manager.  Do you really think that its better that this decision was made for you, or do you think its better the way it is now, that you can choose a linux distro that will run your linux apps and provide a set of different tools for you to choose from and let YOU decide which is a better fit for your needs?

I do not believe that there is enough value anymore in standardizing on package management, if you consider what we have to lose in doing so.  Thats just my opinion.

---

### Post by Polygon on 2008-09-10
it doesnt matter.


even if we do have one package manager, we would still need debs or rpms or whatever for each distro, as linux is not binary compatible, it would have to be compiled separately for each distro. it wont solve any problems really, since developers do not have access to every single distro to make a package for.

---

