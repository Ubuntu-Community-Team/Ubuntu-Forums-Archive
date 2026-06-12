---
title: "Why is it that Installing Software is So Compicated under Linux?"
date: 2008-11-25
forum: The Cafe
---

### Post by Ubuntist on 2008-11-25
I mean, I don't get it.  Under Windows, I can often download a package from any old website (at some risk, of course), click on it and--bingo--it installs itself, although I may have to run the package as an administrator.

Under Linux, it's easy enough to install something from the repositories, but otherwise it's much more complicated than under Windows.  Why?  I'd have thought that without Windows' registry (not that I understand what the registry does, but I've heard lots of bad things about it), it would be, if anything, even easier.

---

### Post by Skripka on 2008-11-25
How is that?


You look for precompiled .deb packages first--download and click on it, and you're done.  This works most of the time/

Sometimes you have to compile, but that is usually a rare thing.


Windows apps are somewhat "simpler" because they are ALWAYS precompiled, and you almost never get to see the source, or what the program will do to your OS.

---

### Post by SunnyRabbiera on 2008-11-25
Well it depends on what you need to do, most applications are under source code for many good reasons:
For one a binary would not always be the best idea, a binary made for a i386 processor type is different then one made for a AMD64.
Two there are many flavors of linux with different installers, tar.gz, .deb, .rpm etc, and not all of them have the same stuff preloaded, in some ways this is good as no one is forcing everyone to use the same format to install things like in OSX or windows (though yes windows acually does have more formats of installing things under its skin, there are not just windows .exe's there are .msi and others out there too so dont think linux is alone)

Some applications just dont want to work, I have seen it happen but thats under both windows and linux.
Look if you stick to the repositories you will be fine for the most part and if you do find a package that is source code there are ways around that too, its all about diversity.

---

### Post by geoken on 2008-11-25
Because linux users believe the replication of a 20kb library 3 or 4 times == the end of the world.

Say for example you have a video converter based of ffmpeg. In windows you could install 5 different video converters and they'd all install ffmpeg into their local folder in program files. In linux, all 5 of those apps will look for the ffmpeg libraries in predefined folders. The app itself wont have ffmpeg bundled with it (even though it's dependent on ffmpeg). It becomes even more complicated when the apps are looking for different versions of ffmpeg. Ideally, you could get the newest version and everything would be fine but sometimes the newer version breaks some features so you have to have both installed. Then you get into the situation where the library itself can't be installed through your package manager so you have to install it manually and deal with it's dependencies which leads to the situation often called 'dependency hell'.

---

### Post by wahoobob on 2008-11-25
The repository programs have been tested and will (for the most part) work as advertised.  Usually, I find that there are at least 50+ titles ready to work for any task I take on. Any of the untested packages are not for the faint of heart, like me.  I try to spend as little time as possible being a test subject and repairing my computer when it is screwed by untested software.  So, be thankful for the thousands of useful and free programs in the repositories and wait for the techies to test them and make them ready for the masses.

---

### Post by SunnyRabbiera on 2008-11-25
> **geoken said:**
> Because linux users believe the replication of a 20kb library 3 or 4 times == the end of the world.

Say for example you have a video converter based of ffmpeg. In windows you could install 5 different video converters and they'd all install ffmpeg into their local folder in program files. In linux, all 5 of those apps will look for the ffmpeg libraries in predefined folders. The app itself wont have ffmpeg bundled with it (even though it's dependent on ffmpeg). It becomes even more complicated when the apps are looking for different versions of ffmpeg. Ideally, you could get the newest version and everything would be fine but sometimes the newer version breaks some features so you have to have both installed. Then you get into the situation where the library itself can't be installed through your package manager so you have to install it manually and deal with it's dependencies which leads to the situation often called 'dependency hell'.


yeh but to be honest I have not had to deal with as much "dependency hell" with debian based systems on a personal level.
Now with a RPM system yes, though some are better then others (Mandriva is definitely top of the class there)

---

### Post by geoken on 2008-11-25
> **wahoobob said:**
>  So, be thankful for the thousands of useful and free programs in the repositories and wait for the techies to test them and make them ready for the masses.

Be thankful for what you get and wait patiently until we decide to give you more. That's really fulfilling the spirit of freedom and choice Linux is based on. /sarcasm

---

### Post by Simian Man on 2008-11-25
As someone who has compiled many applications meant for Linux on Windows systems, I have to disagree with you.

If an application is distributed for a particular system (Windows or Linux), it is always easy to install.  If an application is mainly distributed for Windows it is usually still fairly easy to get running on Linux.  If an application is distributed primarily for Linux it is usually a *BITCH* to get working on Windows.

---

### Post by geoken on 2008-11-25
> **SunnyRabbiera said:**
> yeh but to be honest I have not had to deal with as much "dependency hell" with debian based systems on a personal level.
Now with a RPM system yes, though some are better then others (Mandriva is definitely top of the class there)

I had to when I was trying to install the 2 main Buzz clones. It was at this time that I became really angered with the library management in Linux. I had to track down a 2kb library so I could install a 6kb library so I could finally install the app (actually I had to do this 4 times for each of the dependencies, which were all under 10kb). In the end I spent about 2 days to install 50kb of libraries which will very, very likely never be used for another app as they are extremely specific to the app I was trying to install (they were actually written by the same guys who wrote the app).

---

### Post by oedipuss on 2008-11-25
> **geoken said:**
> Because linux users believe the replication of a 20kb library 3 or 4 times == the end of the world.

Say for example you have a video converter based of ffmpeg. In windows you could install 5 different video converters and they'd all install ffmpeg into their local folder in program files. In linux, all 5 of those apps will look for the ffmpeg libraries in predefined folders. The app itself wont have ffmpeg bundled with it (even though it's dependent on ffmpeg). It becomes even more complicated when the apps are looking for different versions of ffmpeg. Ideally, you could get the newest version and everything would be fine but sometimes the newer version breaks some features so you have to have both installed. Then you get into the situation where the library itself can't be installed through your package manager so you have to install it manually and deal with it's dependencies which leads to the situation often called 'dependency hell'.

I think that's the main reason windows installations deteriorate over time, and the source of other problems as well.

---

### Post by SunnyRabbiera on 2008-11-25
> **geoken said:**
> I had to when I was trying to install the 2 main Buzz clones. It was at this time that I became really angered with the library management in Linux. I had to track down a 2kb library so I could install a 6kb library so I could finally install the app (actually I had to do this 4 times for each of the dependencies, which were all under 10kb). In the end I spent about 2 days to install 50kb of libraries which will very, very likely never be used for another app as they are extremely specific to the app I was trying to install (they were actually written by the same guys who wrote the app).

yes but then again its better in some ways then to have installers that take up a crap load of room.
We dont have the benefit of that many executable installers, in a way its good because when you download windows .exe files from third parties it can screw your system up but in a way its bad as you wind up having to compile sometimes.
But I rather like the linux approach in a way, it keeps the packages from being too large but it also keeps all the installers in one place.
But I do think there should be a dependency free installer in the future.

---

### Post by Skripka on 2008-11-25
> **geoken said:**
> I had to when I was trying to install the 2 main Buzz clones. It was at this time that I became really angered with the library management in Linux. I had to track down a 2kb library so I could install a 6kb library so I could finally install the app (actually I had to do this 4 times for each of the dependencies, which were all under 10kb). In the end I spent about 2 days to install 50kb of libraries which will very, very likely never be used for another app as they are extremely specific to the app I was trying to install (they were actually written by the same guys who wrote the app).

I sense you're making rules out of exceptional exceptions.

---

### Post by geoken on 2008-11-25
> **Skripka said:**
> I sense you're making rules out of exceptional exceptions.

I've never had to manually compile something (which is usually a direct bi-product of requiring a feature in the newest version of an app) and been able to find all, or even the majority, of required libs in the repos.

As for exceptions to the rule, both examples I've used actually happened to me. The first example (where I was talking about ffmpeg) actually happen with a ffmpeg front end I was using that broke when ffmpeg was updated. I had to modify the majority of an XML file used to send commands to ffmpeg because ffmpeg arbitrarily changed the shorthand names for many of it's codecs in the video codec switch.

---

### Post by SunnyRabbiera on 2008-11-25
> **geoken said:**
> I've never had to manually compile something (which is usually a direct bi-product of requiring a feature in the newest version of an app) and been able to find all, or even the majority, of required libs in the repos.

As for exceptions to the rule, both examples I've used actually happened to me. The first example 9where I was talking about ffmpeg) actually happen with a ffmpeg front end I was using that broke when ffmpeg was updated.

Me I have yet to encounter any major dependency hell so I guess I am lucky :D

---

### Post by Skripka on 2008-11-25
> **geoken said:**
> I've never had to manually compile something (which is usually a direct bi-product of requiring a feature in the newest version of an app) and been able to find all, or even the majority, of required libs in the repos.

As for exceptions to the rule, both examples I've used actually happened to me. The first example (where I was talking about ffmpeg) actually happen with a ffmpeg front end I was using that broke when ffmpeg was updated. I had to modify the majority of an XML file used to send commands to ffmpeg because ffmpeg arbitrarily changed the shorthand names for many of it's codecs in the video codec switch.

My experience has been the exact opposite.  I call you case exceptional because I've never gotten a situation like that-nor do I know anyone personally who has.  Everytime I've had to compile something-I've been able to find and install  the dependencies as easy as they are in the readme.  YMMV.  The exceptions to that have been a few Plasma widgets, where cmake doesn't want to compile---but with those After I've nosed around more I find debs easily available with no need to compile myself.

---

### Post by geoken on 2008-11-25
I think a problem here is that a lot of people think this is a problem of distributing source vs distributing binary packages. It isn't. It's an issue of library replication. If it became customary to include the required libraries with the source and link to them locally during compiling then their would be no issue whatsoever. We could have a system like PC-BSD's pbi where all apps install into their own folder with their own libs but the package itself still contains sources.

---

### Post by geoken on 2008-11-25
> **Skripka said:**
> My experience has been the exact opposite.  I call you case exceptional because I've never gotten a situation like that-nor do I know anyone personally who has.  Everytime I've had to compile something-I've been able to find and install  the dependencies as easy as they are in the readme.  YMMV.  The exceptions to that have been a few Plasma widgets, where cmake doesn't want to compile---but with those After I've nosed around more I find debs easily available with no need to compile myself.

Either way, I think a pbi style package willmake people a lot happier. 

I'd argue that a lot of people who haven't had this problem may have simply been scared off when they downloaded an app that they couldn't find in the repos, uncompressed the archive and find a bunch of unknown files. I know this has happened to my daughter several times. Upon realizing the file she downloaded isn't a .deb, she deletes the archive rather than even attempt to compile.

---

### Post by SunnyRabbiera on 2008-11-25
> **geoken said:**
> I think a problem here is that a lot of people think this is a problem of distributing source vs distributing binary packages. It isn't. It's an issue of library replication. If it became customary to include the required libraries with the source and link to them locally during compiling then their would be no issue whatsoever. We could have a system like PC-BSD's pbi where all apps install into their own folder with their own libs but the package itself still contains sources.

There I agree, the BSD .pbi is a really cool concept and wish it was ported over to linux.

---

### Post by Pogeymanz on 2008-11-25
> **Ubuntist said:**
> I mean, I don't get it.  Under Windows, I can often download a package from any old website (at some risk, of course), click on it and--bingo--it installs itself, although I may have to run the package as an administrator.

Under Linux, it's easy enough to install something from the repositories, but otherwise it's much more complicated than under Windows.  Why?  I'd have thought that without Windows' registry (not that I understand what the registry does, but I've heard lots of bad things about it), it would be, if anything, even easier.

Most programs are either in the repos or already compiled for you as a .deb. So, usually it is easier in Linux to install things.

However, not all Linux distros use .deb packages, so less popular programs will just give the source code so that anyone can install it. And usually they have instructions, so what's the big deal?

---

### Post by Archmage on 2008-11-25
> **Ubuntist said:**
> I mean, I don't get it.  Under Windows, I can often download a package from any old website (at some risk, of course), click on it and--bingo--it installs itself, although I may have to run the package as an administrator.

I did try this with Vista and ten programs:

Two didn't start.
Two didn't finish the install.
Three did work with flaws
Two did work
One did destry my system and I would need to install Vista again

I'm not impressed.

---

### Post by Mr. Picklesworth on 2008-11-25
> **geoken said:**
> Because linux users believe the replication of a 20kb library 3 or 4 times == the end of the world.

Say for example you have a video converter based of ffmpeg. In windows you could install 5 different video converters and they'd all install ffmpeg into their local folder in program files. In linux, all 5 of those apps will look for the ffmpeg libraries in predefined folders. The app itself wont have ffmpeg bundled with it (even though it's dependent on ffmpeg). It becomes even more complicated when the apps are looking for different versions of ffmpeg. Ideally, you could get the newest version and everything would be fine but sometimes the newer version breaks some features so you have to have both installed. Then you get into the situation where the library itself can't be installed through your package manager so you have to install it manually and deal with it's dependencies which leads to the situation often called 'dependency hell'.

In fact, duplication *is* the end of the world for dynamically linked libraries. A wonderful bonus we get here, which people don't often observe, is the ability to update a single dynamic library one time and have the benefit of that update seen across the desktop. It means better security and it means more room for rapid development of new features. It means that the developers of the *applications* don't need to keep their eyes open for updates to the libraries they depend on. On the other hand, in Windows land, *each application* has to handle those updates itself, which gets a lot more redundant and a lot more troublesome than 200 kB of hard drive space.

Some libraries, on the other hand, were always meant to be statically linked, or were poorly designed to begin with.
Debian has always been built with the Unix design philosophies at heart, one of which is that a distinct application should do a single thing well and leave the rest to other applications. This includes dynamic libraries. Regrettably, numerous developers have completely ignored the value of that advice. If 'do one thing well' *was* the case with these things, the packages would likely be more stable and we would have far less trouble with version differences since the dependencies then become a more understandable selection of required features.

I have noticed a trend with package uninstall scripts failing, leading to unremovable packages. (Not unlike the myriad of programs in Windows that simply cannot uninstall themselves without a major fight). So Debian definitely isn't bullet proof. Thankfully, upstream is always working on it.

---

### Post by jomiolto on 2008-11-25
> **geoken said:**
> Because linux users believe the replication of a 20kb library 3 or 4 times == the end of the world.

I wish things were as simple as that, but alas they're not; including all the libraries with every app you install brings a whole slew of other problems. For example if a security hole (or even a simple bug) was found in one of the libraries, it would mean upgrading every single app on your system that uses that library! There might also be problems with licensing -- I'm not an expert on the matter, but I believe distributing libraries with an application has some implications on licensing of the application itself.

And, besides, many libraries are much larger than "20kb" and bigger applications can use dozens of libraries. I wouldn't mind downloading a bit of extra every time I install an application, but if even simple applications were multiple megabytes, I would be somewhat annoyed.

Also, I quite disagree with the original poster; one of the best things about Linux (IMO) is how *easy* it is to install software -- I just pick and choose all the things I want from the package manager and click "install" (or whatever the button says). That way I can quickly install all the software I use regularly (dozens of programs with hundreds of dependencies) in just a couple of minutes -- downloading all that stuff takes hours, but I don't need to sit on the computer during that, and I can do something else. It's quite rare for me not to find something in the repositories and in most of those cases there is a .deb available somewhere.

Admittedly, programs that are not available as suitable packages can be problematic, and sometimes I do wish that there was some universal package format that worked on all distributions without problems...

---

### Post by geoken on 2008-11-25
> **Mr. Picklesworth said:**
> In fact, duplication *is* the end of the world for dynamically linked libraries. A wonderful bonus we get here, which people don't often observe, is the ability to update a single dynamic library one time and have the benefit of that update seen across the desktop.

What you call a benefit I call a broken video converter because a new version of ffmpeg decided to change the naming convention for codecs. As a developer, I don't want to rely on libraries that can arbitrarily change breaking my apps core functionality. You're making it sound like relying on ever changing external libraries falls more in line with the practice of 'set it and forget it' than having libraries which don't change. As a developer, I'd be a lot more worried about relying on an externally linked ffmpeg than I would be relying on a statically linked, heavily tested version of ffmpeg.

---

### Post by Mr. Picklesworth on 2008-11-25
There are more stable libraries which try to abstract these things. For example, [GStreamer]("http://gstreamer.freedesktop.org/") has been quite successful and talks with ffmpeg from time to time. This way that bother (and I have heard of ffmpeg dependency problems before) is left to a single other entity instead of to every single person who deals with video encoding.

You can always distribute ffmpeg *with* your application, by the way. I don't believe there is anything stopping anyone from doing that, but it just isn't recommended or appreciated most of the time ;)

FFmpeg, being a crazy thing without any releases (just svn checkout at any time), has never struck me as something one could possibly trust to be stable, whether they say they try or not. Frankly, I don't blame anyone but the person who *selected* ffmpeg if it turns out to be unmaintainable for them.

This is definitely a different method of organizing software. Not necessarily worse, or better; just better suited to certain things. One must adapt to it. Learn its strengths and its weaknesses and build on them instead of trying to make Debian and RPM something they are not.

---

### Post by geoken on 2008-11-25
IMO, if developers had something they could target (like .pbi) then we'd at least have a choice between statically linked and larger file sizes and dynamically linked. For some statically linked isn't an issue at all. 

The current system I'm on is running XP SP3. It's a 3+yr old install and there about 50 apps in the program files folder. The entire system has less than 800mb of .dll's on it (that includes the core windows dll's). I think a lot of people would consider this completely irrelevant (both in terms of storage space and bandwidth to download) if it meant a greater library of applications available to them.

---

### Post by aysiu on 2008-11-25
The reason installing software is "so complicated" in Linux is the same reason it's "so simple" in Linux.

It's just a completely different approach that has its own benefits and drawbacks.

It's simple because almost everything or everything you need is hosted in secure and trustworthy repositories, and those can be installed with a simple click or two, and they will be automatically upgraded with every new release.

It's complicated because for some people, not every application they want is in the repositories.

So if many things you want (clearly the OP's case) is outside the repositories, then, yes, it's complicated. But if everything you want (in my case, for example) is in the repositories, then, it's simple.

---

### Post by Magneto on 2008-11-25
How else would they drive away end-users?

:grin:

I don't think that stereotype holds true anymore. When was the last time you installed Windows and had an application that provided a way to install whatever type of app(yes not totally inclusive of everything one might need)you may need from word processor to media player?

I think being a windows user has corrupted your thought process. I don't believe it can be honestly construed as easier to accomplish a task that requires more steps and time to complete than another.

Compare

Windows -
 search for a website or application using a browser 
find free software that fits your needs or purchase it online or in a store
install it

Linux (depending on distro and applications used)
open a terminal/synaptic and search for a keyword in the application's name
install it

For less common or more specialized software one may need to search more or configure more etc but I think that's comparable to windows. Since the user base is smaller for Linux there aren't as many people developing software for it as Windows so you may not have 40-400,000 different apps available to choose between for a specific program need. I don't think the question is about installation processes as much as it is about software availability. More popular apps require less user interaction such as compilation from source- because their larger user base allows people to compile for a broad range of environments, test accordingly and include in pkg mgmt systems or easily downloadable binaries.

---

### Post by cmay on 2008-11-25
i do not think its fun to compile from source on windows.
but the two other procedures i cant see how click on debian-package and let gdebi install in one click is harder than click ok next click where to install click next click i agree to license click next click ok .

audacity i compiled from source on windows. i also compiled a operative system that should be installed on a single floppy disk on windows. i do not remember never have needed compiled anything under linux other for the fun of it. last time i did  i think it was supertux :)

---

### Post by Dragonbite on 2008-11-25
> **Ubuntist said:**
> I mean, I don't get it.  Under Windows, I can often download a package from any old website (at some risk, of course), click on it and--bingo--it installs itself, although I may have to run the package as an administrator.

Under Linux, it's easy enough to install something from the repositories, but otherwise it's much more complicated than under Windows.  Why?  I'd have thought that without Windows' registry (not that I understand what the registry does, but I've heard lots of bad things about it), it would be, if anything, even easier.

The key to that is can often download PRECOMPILED EXE FILES FOR WINDOWS from any old website .... What about when it is an application that doesn't have a Windows EXE?

Windows has always had to make it easy for downloading anything and running the installation (for better or worse) because they never had a centralized repository of application to access.

Linux has built a strong community and ecosystem around the centralized repository because this every-file-for-itself method had significant stability, security and maintainability issues.

Also, if the application grows enough in popularity then it may find its way into the repository and then you don't even need to go to the website to download it.

I have been pleasantly surprised by double-clicking on a .deb file and having it install itself without any issues. And I'm not sure if it is still true but wasn't it not all that long ago that .rpm files were more common than .deb?

How about Mac users which have even fewer download applications than Windows yet doesn't have the repositories of Linux to fall back on?

---

### Post by phrostbyte on 2008-11-25
In Linux distributions like Ubuntu, software is downloaded using the package manager. If you find software which is not part of the repository but can be, this is a bug in Ubuntu. And it should be reported.

---

### Post by phrostbyte on 2008-11-25
> **aysiu said:**
> The reason installing software is "so complicated" in Linux is the same reason it's "so simple" in Linux.

It's just a completely different approach that has its own benefits and drawbacks.

It's simple because almost everything or everything you need is hosted in secure and trustworthy repositories, and those can be installed with a simple click or two, and they will be automatically upgraded with every new release.

It's complicated because for some people, not every application they want is in the repositories.

So if many things you want (clearly the OP's case) is outside the repositories, then, yes, it's complicated. But if everything you want (in my case, for example) is in the repositories, then, it's simple.

Actually that is true, the way Windows distributes software is also one of it's biggest flaws, everytime you install something in Windows, you are trusting your machine to a possibly unknown third party. An install can do anything from installing a program, to stealing your credit card information and passwords. And installers may (and do) often do both. This is a huge flaw in Windows and is a big part of it's security failures stem from this.

So if Ubuntu decided to adopt Microsoft's model for software distribution, it will come with it's own very huge drawbacks. Personally I prefer the repository model. It's far more secure, and if the repository is complete, it is far more usable too.

---

### Post by handy on 2008-11-25
Installing software using Arch is as simple as the following command:

***yaourt -S** <package_name package_name package_name>*

Upgrading the entire system is as easy as using the following command:

***yaourt -Syu***

Which will sync the machine with the repository database then download & install the latest version of everything in the system.  

The downloads are binaries so the process is quite quick, if you run this command daily there is only a few minutes a day (on average) required to keep your system on the cutting edge.  

Apart from hardware failure, there is no longer any need to install an upgraded version as you can do it every day.

I think that is the simplest software installation system I have ever seen.

---

### Post by Dragonbite on 2008-11-25
> **handy said:**
> Installing software using Arch is as simple as the following command:

***yaourt -S** <package_name package_name package_name>*

Upgrading the entire system is as easy as using the following command:

***yaourt -Syu***

Which will sync the machine with the repository database then download & install the latest version of everything in the system.  

The downloads are binaries so the process is quite quick, if you run this command daily there is only a few minutes a day (on average) required to keep your system on the cutting edge.  

Apart from hardware failure, there is no longer any need to install an upgraded version as you can do it every day.

I think that is the simplest software installation system I have ever seen.

doesn't look that much different than

yum install <package> <package> <package>
(to install one or more packages)

and 

yum update    
(to update the repository list)

and 

yum upgrade <optional package>      
(if you list a package it will update just that package, otherwise updates the whole system)

---

### Post by Compucore on 2008-11-25
I don't mind whether I install drivers or apps for my linux laptop if it is in ther terminal or through deb. If there is something missing I would usually check out what was missing.befoer I had installed it. When I installed my laserprinter from I made sure I read the instructions carefully so it would install and compile on my boxes. Sometimes I don't read the instructions in the beginning. Nowadays I read them literally to make sure I have a good install on my drivers or apps over here. As if they were like the ten commandments written in stone. :)

Compucore

---

### Post by Eisenwinter on 2008-11-25
Installing software on Linux is not complicated at all, depending on the circumstances.

Many times people confuse "complication" with "dependency hell".

Sure, I've been stuck at DH for minutes at a time, but eventually succeeded with the installation of 99% of the programs I tried to install.

The only reason I haven't succeeded to install some program from source, so far, is if it's **so old**, that I can't even find it's dependencies anymore.

---

### Post by handy on 2008-11-25
> **Dragonbite said:**
> doesn't look that much different than

yum install <package> <package> <package>
(to install one or more packages)

and 

yum update    
(to update the repository list)

and 

yum upgrade <optional package>      
(if you list a package it will update just that package, otherwise updates the whole system)

Yep, I haven't used yum, but it looks like another nice simple rolling release system.

I wonder if the powers that be will ever decide that Ubuntu should have a rolling release system?  It could have repo's covering the range from stable to unstable so users as they became more familiar with the system could uncomment the unstable if they desired.

That would make Ubuntu so much less of a hassle for those that upgrade every 6 months.

---

### Post by spupy on 2008-11-25
Complicated? Have tried compiling gimp or pidgin in windows? You haven't, because it's more complicated that on Linux! Tadaaa!:)

Seriously now. Aren't most windows programs statically linked? Also, i read somewhere that windows ships with most of the libraries, so programmers don't need to bother with dependencies, since everything they need is already included in the OS. Can someone confirm this?

---

### Post by doorknob60 on 2008-11-25
> **handy said:**
> Installing software using Arch is as simple as the following command:

***yaourt -S** <package_name package_name package_name>*

Upgrading the entire system is as easy as using the following command:

***yaourt -Syu***

Which will sync the machine with the repository database then download & install the latest version of everything in the system.  

The downloads are binaries so the process is quite quick, if you run this command daily there is only a few minutes a day (on average) required to keep your system on the cutting edge.  

Apart from hardware failure, there is no longer any need to install an upgraded version as you can do it every day.

I think that is the simplest software installation system I have ever seen.

+1, although I use yaourt -Syu --aur to update my AUR packages as well. Yaourt, Pacman, and the rolling release system is the reason I like Arch so much, it just works so well. My system kliked doing weird things updating Ubuntu, but updating things gradually like this always seems rto work better and it isn't time consuming, and you're not usually wishing "I wish I had version [number] of [application]" If you do, you can use yaourt -Sb [application], edit the PKGBUILD to the newest version, and that will usually download and compile the application for you. Arch is just amazing :) But installing apps in any Linux distro (for the most part) is less complicated than in Windows. I don't have to go hunt for the exe, download it, run it. I just type a simple terminal command, or even a GUI for it.

---

### Post by kikoman on 2008-11-25
You only install software 0.1% of time you use your computer over in all.

And if 3rd party supports it, they will provide .deb like flash for a one step installation.

And that ease of installation is the hole of windows why it has a major problem regarding virus/spywares.

my newbie pov cents

---

### Post by LuisAugusto on 2008-11-25
I won't read the whole thread, but how clicking install in the Add/Remove dialog is complicated :/

Ubuntu: Add/Remove or Synaptic
OpenSUSE: 1 click install 

And most distros have a package manager, backend by apt, zypper, yum, whatever. Far easier than in Windows :/

---

### Post by doas777 on 2008-11-25
now that I'm used to apt, installation is easier in ubuntu than XP.

in linux:
```

click to open terminal
type 'sudo apt-get install <package>'
type in passwd
press enter (Y/n):
wait while ubuntu does it all.
configure as needed.

```

in XP:
```

open browser
google app
select result link
select download
allow site in noscript (cuz their bastards and js linking)
download file
scan file for viri
dclick to start install
wait while kaspersky classifies install
allow application to run 
click next
click i agree
click next
click custom
unccheck spyware
uncheck crapware
click next
click no i don;t want you to spy on me, even if it's supposedly anymous.
click next
allow app to copy files (my IDS is set to ask about almost everything. I love kaspeersky) 
wait while kaspersky classifies install
allow app to access network
configure as needed

```

that says it all for me.

---

### Post by loell on 2008-11-25
I don't want **yaourt**, **apt**, **yum** or even **gnome-appinstall**(add/remove) , heck i don't even want the unified **packagekit**.. they are too complicated!

I want something simple, like when you think of the program, and presto it's there!  :KS

keep your two to three click tools to yourselves.. :popcorn:

---

### Post by geoken on 2008-11-25
> **loell said:**
> I don't want **yaourt**, **apt**, **yum** or even **gnome-appinstall**(add/remove) , heck i don't even want the unified **packagekit**.. they are too complicated!

I want something simple, like when you think of the program, and presto it's there!  :KS

keep your two to three click tools to yourselves.. :popcorn:

What's the point of the sarcastic comments? The OP is obviously talking about apps that aren't in the repo's, you probably would have realized that if you read the post.

---

### Post by LuisAugusto on 2008-11-25
> **doas777 said:**
> now that I'm used to apt, installation is easier in ubuntu than XP.

in linux:
```

click to open terminal
type 'sudo apt-get install <package>'
type in passwd
press enter (Y/n):
wait while ubuntu does it all.
configure as needed.

```

No, no, wrong approach, normal users don't want a terminal, It should be:

> [LIST=1]
[*]Click on Applications menu
[*]Select Add/Remove
[*]Select the desire application(s)
[*]Click Install
[*]Type your password
[/LIST]

Success!

---

### Post by loell on 2008-11-25
> **geoken said:**
> What's the point of the sarcastic comments? The OP is obviously talking about apps that aren't in the repo's, you probably would have realized that if you read the post.

yes pbi fan ;), i've read the OP before posting, just so you know, the comment was directed to posts before my post. and besides why  would it concern you anyway? ;)

---

### Post by geoken on 2008-11-25
> **doas777 said:**
> 

that says it all for me.

1) "g inkscape" in start menu (alias for launching default browser with google search)
2) don't even go to inkscapes site, just select download link from the google results
3) let app download and double click the file in Firefox's download manager to initiate installation
4)wait while windows does it all
5)configure as needed

---

### Post by geoken on 2008-11-25
> **loell said:**
> yes pbi fan ;), i've read the OP before posting, just so you know, the comment was directed to posts before my post. and besides why  would it concern you anyway? ;)

Because it's frustrating when I see legitimate questions get addressed with unfounded tongue in cheek sarcasm. You were addressing the posts before you which were also drenched in sarcasm by making the OP seem lazy because he thought package managers are too hard, even though he clearly stated he was referring to apps outside of the repos.

---

### Post by loell on 2008-11-25
> **geoken said:**
>  even though he clearly stated he was referring to apps outside of the repos.

which is already been addressed by stating there are deb packages around. i'm fully aware by what you mean, its "deviation by sarcasm" right? which i don't intend to continue, lets just say i want to comment , you want to comment, lets leave it at that. :) / now, this is not a sarcastic smiley so just relax/ :D

---

### Post by LuisAugusto on 2008-11-25
First, you can probably find repositories for apps outside the "official" repos.

For application without any kind of repositories:

[Get deb]("http://www.getdeb.net/")

It still doesn't look hard to me...

---

### Post by handy on 2008-11-26
> **LuisAugusto said:**
> First, you can probably find repositories for apps outside the "official" repos.

For application without any kind of repositories:

[Get deb]("http://www.getdeb.net/")

It still doesn't look hard to me...

Things are hardest at the beginning, it probably takes most windows users a couple of months of using a distro' before they feel so at home that thoughts of how you do it in windows don't occur anymore.

If I look at a windows screen these days it looks so alien to me, which is pretty wild after long days in windows for 10 years. :lolflag:

---

### Post by Ubuntist on 2008-11-26
Thanks for the replies; I think I (the OP) am getting some idea of what makes installing non-repository packages more complex than just executing an installer.  And let me emphasize, as geoken kindly does, that it's non-repository packages that I'm asking about; there's nothing complicated about installing with apt-get or Synaptic.

An example is GNU R, a statistical package: [http://www.stats.bris.ac.uk/R/](http://www.stats.bris.ac.uk/R/).  If I'm happy to use version 2.7.1, than I can simply install from repos.  But if I want 2.8.0, then under *nix I've got to wade through this: [http://www.stats.bris.ac.uk/R/doc/manuals/R-admin.html#Installing-R-under-Unix_002dalikes](http://www.stats.bris.ac.uk/R/doc/manuals/R-admin.html#Installing-R-under-Unix_002dalikes).  If I were installing under Windows, on the other hand, all I have to do is execute [http://www.stats.bris.ac.uk/R/bin/windows/base/R-2.8.0-win32.exe](http://www.stats.bris.ac.uk/R/bin/windows/base/R-2.8.0-win32.exe) .

If I installed things like 2.8.0 frequently, it wouldn't be a big deal, because I would remember how to do it.  Since I can get most of what I need from the repos, though, I only do non-repo installs once in a while.  That makes it a nuisance, since by the time I do the next install I've forgotten how I did it the last time.

---

### Post by bruce89 on 2008-11-26
> **Ubuntist said:**
> An example is GNU R, a statistical package: [http://www.stats.bris.ac.uk/R/](http://www.stats.bris.ac.uk/R/).  If I'm happy to use version 2.7.1, than I can simply install from repos.  But if I want 2.8.0, then under *nix I've got to wade through this: [http://www.stats.bris.ac.uk/R/doc/manuals/R-admin.html#Installing-R-under-Unix_002dalikes](http://www.stats.bris.ac.uk/R/doc/manuals/R-admin.html#Installing-R-under-Unix_002dalikes).  If I were installing under Windows, on the other hand, all I have to do is execute [http://www.stats.bris.ac.uk/R/bin/windows/base/R-2.8.0-win32.exe](http://www.stats.bris.ac.uk/R/bin/windows/base/R-2.8.0-win32.exe) .

If I installed things like 2.8.0 frequently, it wouldn't be a big deal, because I would remember how to do it.  Since I can get most of what I need from the repos, though, I only do non-repo installs once in a while.  That makes it a nuisance, since by the time I do the next install I've forgotten how I did it the last time.

Try getting all distros to use the same toolchain and the same versions of all libraries.

---

### Post by handy on 2008-11-26
> **Ubuntist said:**
> Thanks for the replies; I think I (the OP) am getting some idea of what makes installing non-repository packages more complex than just executing an installer.  And let me emphasize, as geoken kindly does, that it's non-repository packages that I'm asking about; there's nothing complicated about installing with apt-get or Synaptic.

An example is GNU R, a statistical package: [http://www.stats.bris.ac.uk/R/](http://www.stats.bris.ac.uk/R/).  If I'm happy to use version 2.7.1, than I can simply install from repos.  But if I want 2.8.0, then under *nix I've got to wade through this: [http://www.stats.bris.ac.uk/R/doc/manuals/R-admin.html#Installing-R-under-Unix_002dalikes](http://www.stats.bris.ac.uk/R/doc/manuals/R-admin.html#Installing-R-under-Unix_002dalikes).  If I were installing under Windows, on the other hand, all I have to do is execute [http://www.stats.bris.ac.uk/R/bin/windows/base/R-2.8.0-win32.exe](http://www.stats.bris.ac.uk/R/bin/windows/base/R-2.8.0-win32.exe) .

If I installed things like 2.8.0 frequently, it wouldn't be a big deal, because I would remember how to do it.  Since I can get most of what I need from the repos, though, I only do non-repo installs once in a while.  That makes it a nuisance, since by the time I do the next install I've forgotten how I did it the last time.

I have many Bookmarks to refer to in the future, to help me when I have to do something again, as my memory is not what it once was.  

Occasionally I have written a wiki article, which gives others the benefit of the research I had to do to accomplish something.  

These abilities that the internet has afforded us, allow us to help each other not have to reinvent the wheel quite so often. :-)  

As you say, some things under windows may be easier than under Linux, though the big difference is the amount of genuine support that truly exists in the Linux community.

---

### Post by Dragonbite on 2008-11-26
When I first became in charge of the Linux special interest group here Firefox 2 was just released.

Somebody, obviously new, went straight to the Firefox website and tried to download and install it just was he would for Windows.

I had to describe to him how the package manager for his distribution (openSUSE) works because he didn't even understand the concept at the time.

The only downside with the repository method is having to wait (c'mon, I want it now Now NOW!).  When things like Firefox or Flash or Reader comes out usually there is a Windows .exe file available because that is Window's method of distribution.

With repositories we have to wait, or install it ourselves from source usually.

It would be nice if these vendors offered, say, a .exe, .dmg (is that what Macs take?), .deb and .rpm at the same time, kudos if the .deb and .rpm can be generic enough it doesn't matter if it is Debian or Ubuntu (.deb) or Red Hat/CentOS, Fedora, openSUSE or PCLinuxOS (.rpm).

---

### Post by handy on 2008-11-26
> **Dragonbite said:**
> 
It would be nice if these vendors offered, say, a .exe, .dmg (is that what Macs take?), .deb and .rpm at the same time, kudos if the .deb and .rpm can be generic enough it doesn't matter if it is Debian or Ubuntu (.deb) or Red Hat/CentOS, Fedora, openSUSE or PCLinuxOS (.rpm).

Yes .dmg is Mac for disk image I reckon.

I agree, it would be nice.

---

### Post by Dragonbite on 2008-11-26
The other option, though, which may not be as useful for Mozilla but maybe for Adobe would be to host their own repository that they maintain.

That way updates can be pushed through automatically and they could add new applications (Photoshop for Linux? Flash for Linux?).

Kinda like how Mono has their own repositories for Novell SUSE/openSUSE and Red Hat (CentOS).  For dapper there used to be a repository for all things Mono but I don't know if they've kept it up (or what it does to conflicts).

---

### Post by jimi_hendrix on 2008-11-26
compiling from source...1 list of commands

tar xvzf (or zvjf if its a .bz2) && cd <root name of package> && ./configure && make && make install && make clean

---

### Post by LinuxGuy1234 on 2008-11-26
> **Ubuntist said:**
> I mean, I don't get it.  Under Windows, I can often download a package from any old website (at some risk, of course), click on it and--bingo--it installs itself, although I may have to run the package as an administrator.

Under Linux, it's easy enough to install something from the repositories, but otherwise it's much more complicated than under Windows.  Why?  I'd have thought that without Windows' registry (not that I understand what the registry does, but I've heard lots of bad things about it), it would be, if anything, even easier.

I think it is:
Windows:confused::
Click Download
Click Save File
Open file
Click
Click
Click OK
Click
Click
Click
Appeal over a long EULA
Push I agree
Click
Let installer install the software
Done.
Linux:KS:
Applications->Add/Remove
Pick Program
Apply changes
Type root password
Let apt do work
Be happy

The Windoze Registry:
Stores about 100% of your settings crap

Now see? :mad:

---

### Post by Magneto on 2008-11-26
> **jimi_hendrix said:**
> compiling from source...1 list of commands

tar xvzf (or zvjf if its a .bz2) && cd <root name of package> && ./configure && make && make install && make clean
pretty much
the original poster's use of the word complicated only refers to n00bs and it isn't as if people new to Windows don't find it "complicated" too
As far as I'm concerned that complicated bs is just a stereotype.

---

### Post by SunnyRabbiera on 2008-11-26
> **LinuxGuy1234 said:**
> I think it is:
Windows:
Click Download
Click Save File
Open file
Click
Click
Click OK
Click
Click
Click
Appeal over a long EULA
Push I agree
Click
Let installer install the software
Done.
Linux:KS:
Applications->Add/Remove
Pick Program
Apply changes
Type root password
Let apt do work
Be happy

The Windoze Registry:
Stores about 100% of your settings crap

Now see? :mad:


Yup I agree

---

### Post by pp. on 2008-11-26
> **LinuxGuy1234 said:**
> I think it is:
Windows:confused::
Click Download
Click Save File
Open file
Click
Click
Click OK
Click
Click
Click
Appeal over a long EULA
Push I agree
Click
Let installer install the software
Done.
Linux:KS:
Applications->Add/Remove
Pick Program
Apply changes
Type root password
Let apt do work
Be happy

The Windoze Registry:
Stores about 100% of your settings crap

Now see? :mad:

You forgot to enter the 20 character license key (printed in a font which won't let you tell 1 from l or I, 0 from O, B from 8, Y from V and so on)

---

### Post by LinuxGuy1234 on 2008-11-26
> **pp. said:**
> You forgot to enter the 20 character license key (printed in a font which won't let you tell 1 from l or I, 0 from O, B from 8, Y from V and so on)

Nope... but WHATEVER.

---

### Post by Namtabmai on 2008-11-26
> **Ubuntist said:**
> Thanks for the replies; I think I (the OP) am getting some idea of what makes installing non-repository packages more complex than just executing an installer.  And let me emphasize, as geoken kindly does, that it's non-repository packages that I'm asking about; there's nothing complicated about installing with apt-get or Synaptic.


Precisely, if you are comparing installing supported on Windows verses supported software on Ubuntu, Ubuntu wins by a small margin (in that you install through Synaptic instead of finding/going to a website and downloading manual).

The trouble is your comparison is flawed, you are trying to compare installing a supported pre built Windows version against building the source manually on Ubuntu.

If you want to really compare this, you have to compare building/installing a Windows application from source against the same on Ubuntu.

Try this (something I had to do recently at work);

Grab the 0.5 source of bzr-svn, [http://people.samba.org/bzr/jelmer/bzr-svn/0.5/](http://people.samba.org/bzr/jelmer/bzr-svn/0.5/), and try building/installing it on Ubuntu then on Windows.

For me it took 10 minutes to build/install on Ubuntu, then I went on to do the same with Windows. It took hours of finding and installing other software that the build process required, not to mention a little googling for information as well as a small fix to the build process.

In conclusion comparing installing software on Windows vs Ubuntu.

**_Supported pre-compiled software (exe vs deb)_**

Close, but Ubuntu is marginally better as 90% of the time it's available in Synaptic, if not the process is similar to windows.

**_Compiling software on Ubuntu vs Windows_**

Ubuntu wins hands down, Windows isn't even the same ball park when it comes to this.

Of course, the real question I think you're asking is "Why doesn't software X provide Ubuntu debs?", and really that a question you'd be better off asking the developers.

---

### Post by Ubuntist on 2008-11-27
> **jimi_hendrix said:**
> compiling from source...1 list of commands
tar xvzf (or zvjf if its a .bz2) && cd <root name of package> && ./configure && make && make install && make clean

I'm sure this all seems very simple to most of the people participating in this thread.  It would probably seem simple to me if I knew what each of the commands did.

The tar I get.

As far as cd <root name of package>, this raises the question of *where* to install.  What's the right place for something like this?  /usr/local?  /usr/opt?

What does configure do?

I know what make is and have even used it in building programs.  But what's the point of running make without an argument?  What does make install actually do?  (I think I can guess what make clean does.)

Finally, would this sequence of commands work under any Linux (or other *nix?) distro, or only under a Debian-based one?

---

### Post by Ubuntist on 2008-11-27
> **Namtabmai said:**
> Precisely, if you are comparing installing supported on Windows verses supported software on Ubuntu, Ubuntu wins by a small margin (in that you install through Synaptic instead of finding/going to a website and downloading manual).

The trouble is your comparison is flawed, you are trying to compare installing a supported pre built Windows version against building the source manually on Ubuntu.

If you want to really compare this, you have to compare building/installing a Windows application from source against the same on Ubuntu.


Sorry, I made my plaintive question seem more general than it was meant to be.  It's just that the particular non-repo packages that I have needed have been easier for me in Windows than in Ubuntu. Just my own experience. I still much prefer Ubuntu to Windows, for all kinds of reasons.

> 
Of course, the real question I think you're asking is "Why doesn't software X provide Ubuntu debs?", and really that a question you'd be better off asking the developers.

Yeah, I guess that's it, although as I ask in my reply. What I'm taking away from this discussion is that simple installer packages are perfectly possible in Ubuntu, but for various reasons they are not provided as often as installers for Windows.  I'm sure it's just a matter of market share.

---

### Post by Skripka on 2008-11-27
> **Ubuntist said:**
> I'm sure this all seems very simple to most of the people participating in this thread.  It would probably seem simple to me if I knew what each of the commands did.

The tar I get.

As far as cd <root name of package>, this raises the question of *where* to install.  What's the right place for something like this?  /usr/local?  /usr/opt?

What does configure do?

I know what make is and have even used it in building programs.  But what's the point of running make without an argument?  What does make install actually do?  (I think I can guess what make clean does.)

Finally, would this sequence of commands work under any Linux (or other *nix?) distro, or only under a Debian-based one?

I've never had to tell a source tar where to install itself....if you ever actually need to, odds are it ought to be in the readme.  If not, and in doubt, /usr/src.

```
make install
```
installs the program to your system

---

### Post by tsali on 2008-11-27
To Namtabmai = +1

---

### Post by LinuxGuy1234 on 2009-02-02
I think that every single problem can be solved by creating a "Universal Package Management" specification, and implement it in every OS out there.

---

### Post by Johnsie on 2009-02-02
If you only use stuff from the repositories you will mostly like have outdated software. You're also letting a company control what applications/versions you use. If you don't let Cannonical control your software then you run a risk of installing something dangerous.


With Windows many programs have automatic updaters, but with Linux you're almost expected to wait until the repository maintainer decides for you. Getdeb and external deb packages good if legit but they will break your package database. They can also be unsafe because you need to give them root access to install themselves. Giving a deb root gives it the power to do anything it wants to your system, even bad stuff.

I have had to go through long tutorials just to install simple things on Linux but that is gradually improving.

---

### Post by handy on 2009-02-03
Has someone said how easy it is under Arch yet?

Total system upgrades aren't much more difficult or time consuming, for that matter.

---

### Post by billgoldberg on 2009-02-03
> **handy said:**
> Has someone said how easy it is under Arch yet?

Total system upgrades aren't much more difficult or time consuming, for that matter.

I don't think much "newbies" will think installing apps in Arch is easy. No GUI and all.

Yaourt makes it a bit easier.

---

### Post by igknighted on 2009-02-03
> **geoken said:**
> What you call a benefit I call a broken video converter because a new version of ffmpeg decided to change the naming convention for codecs. As a developer, I don't want to rely on libraries that can arbitrarily change breaking my apps core functionality. You're making it sound like relying on ever changing external libraries falls more in line with the practice of 'set it and forget it' than having libraries which don't change. As a developer, I'd be a lot more worried about relying on an externally linked ffmpeg than I would be relying on a statically linked, heavily tested version of ffmpeg.

This is why projects like Phonon exist.  Phonon is a layer between end user apps (like your video converter) and the ffmpeg libraries.  Phonon keeps a stable API for your app to interface to, and ffmpeg interfaces with phonon to provide the functionality.

This allows us to use the technologically superior dynamically linked libraries, but keep a stable API for app developers.

---

### Post by handy on 2009-02-03
> **billgoldberg said:**
> I don't think much "newbies" will think installing apps in Arch is easy. No GUI and all.

Yaourt makes it a bit easier.

Is pacman/yaourt really that hard to use?  It takes a few minutes of reading the Beginners Guide when you are doing your initial Arch install to get started & then the Arch Wiki Pacman page or man pacman to cover far more than most will ever need.

Hmm, so you reckon people are that attached to their mouses eh!?

---

### Post by andrew.46 on 2009-02-03
Hi LuisAugusto,

> **LuisAugusto said:**
> No, no, wrong approach, normal users don't want a terminal

Hmmmm..... how would you define a 'normal user' and would you really want to deprive this person of the most powerful aspect of Linux?

Andrew

---

