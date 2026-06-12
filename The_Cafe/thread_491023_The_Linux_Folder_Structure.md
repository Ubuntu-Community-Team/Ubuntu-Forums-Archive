---
title: "The Linux Folder Structure"
date: 2007-07-03
forum: The Cafe
---

### Post by Praill on 2007-07-03
I have a long unanswered question that has been refreshed in my mind by a different question in the forum.

What is the reason behind the continued use of the old unix folder structure?

When someone installs a package its contents are scattered throughout the folder structure. The executables are installed in /bin, /usr/bin, /usr/local/bin, /usr/share, ~/<program name>, etc. The modules are installed in /usr/lib, /lib/, /usr/local/lib. The man files, the help files, etc, are the same story. God forbid you install a program that doesnt make a menu entry. Most of the time you can execute the programs name in a terminal (not very user friendly) but if it installs in /usr/local or ~/ then you have to search for it. Also, a program like EasyCam installs the executable by the name of lauchcam2 (no thats not a typo). The only way for me to find this program after installation was through exhaustive google searching.

Furthermore, say I decide to create a program called lauchcam2 (not knowing one exists). We are going to overwrite eachother. It just doesn't make any sense. Why not do like windows and install in a program files directory? This makes everything not only easier to find, but it makes your system (and what's installed on it) easier to navigate.

Hopefully someone can explain this to me because I just don't see the logic behind the way linux does this.

---

### Post by Tundro Walker on 2007-07-03
I think it has to do with keeping a set area where files install to, that way new files can look for necessary code modules in /bin, usr/bin, etc.  I can kinda understand it, but I find it annoying sometimes, too.  You install something, and half the time there's no menu entry.  So, you're digging in the CLI & folders for it.  And you start typing the CLI name you think works for it, and it turns out to be totally different.  (9 times out of 10, I end up having to look at the Synaptic file specs for the package I d/l'ed to figure out what the executable is for these types of things.)

That's been one of my (very few) annoyances with Linux.  In Windows, I liked how I could install a program where ever I wanted, but I didn't like how it tossed all kinds of crap in the registry.  Also, sometimes Windows programs end up tossing files in all kinds of other folders, like the System folder and what-not.  There were times I would spring-clean my computer, and find folders, files, and registry entries for crap I had uninstalled 6 months ago.

At least with Linux, there's a semi-set way programs are installed, so programmers / developers can anticipate where certain programs will be that their program may require.  In Windows, the System & Program Files folders attempted to do this, but you'd always see programs install with duplicate .dll files and what-not, because the programmer was paranoid that your MS Windows computer didn't have them installed (or path'ed correctly).

---

### Post by PaulFr on 2007-07-03
Well, one point against having a self-contained package structure: Each and every package will have to have its own copy of the libraries it uses, implying huge waste of disk space. Unix has always had library versioning right in the library name (the developer needs to make use of this properly :-).

Now, to your point regarding the difficulty of finding **launchcam2**, the Ubuntu/Debian packaging scheme maintains the  metadata for all installed packages - so an easy way to find out what was installed in a package is in Synaptic Package Manager - just select any package, and right-click, then select Properties menu. One of the tabs in the resulting dialog is Installed Files which shows which files went where.

**Question:** One question I have is that is there a way to query this metadata in the reverse ? i.e. given a full path like /usr/bin/smbd, can I find which package installed this file ? That would be very helpful.

Now regarding your comment about a second launchcam2, this has already been considered in Ubuntu/Debian (please see **update-alternatives** for a description of how two commands with identical names are handled). Of course, I think this needs some effort on the part of the package creator (does it ? I am not sure of this).

As an actual example, the **git** command refers to a source code management tool as well as the  GNU Interactive Tools File Manager. When both are installed, the user is warned about the alternatives and a update-alternatives command is shown as part of the warning, so that the user can select the appropriate command for use.

My $0.02.

---

### Post by Praill on 2007-07-03
> Well, one point against having a self-contained package structure: Each and every package will have to have its own copy of the libraries it uses, implying huge waste of disk space. Unix has always had library versioning right in the library name (the developer needs to make use of this properly .
Well, just like in windows, modules (dll's) of the standard, or latter added, api need to be in a centralized location... but program files really don't need to be.
> Now, to your point regarding the difficulty of finding launchcam2, the Ubuntu/Debian packaging scheme maintains the metadata for all installed packages - so an easy way to find out what was installed in a package is in Synaptic Package Manager - just select any package, and right-click, then select Properties menu.
Very, very nice to know. Im instantly glad I asked after learning this very valuable peice of information. One suggestion might be to make this information a little easier to find though. Perhaps putting a "installed files" button on the "install completed" window after a package installs. Maybe i'll make an [IDEA] post re: that.
> ...update-alternatives...
Good to know as well. I figured something like this had to exist.

---

### Post by ynnhoj on 2007-07-03
you might be interested in gobo linux; it has a different filesystem hierarchy.  link: [gobo linux at a glance](http://www.gobolinux.org/?page=at_a_glance).

---

### Post by saulgoode on 2007-07-03
> **Praill said:**
> Well, just like in windows, modules (dll's) of the standard, or latter added, api need to be in a centralized location... but program files really don't need to be.

That's not really true for Linux. Many programs rely on the existence of other programs and need to know where to find them. A GUI CD-burner such GnomeBaker or K3B might work by specifying command-line arguments to 'cdrecord' or other cdrtools (this is how they used to work, I am not sure if they still rely on CLI programs). Many media convertors rely on the FFMPEG, MENCODER, and MPLAYER commands. Under the Unix philosophy of many small programs working together, the distinction between a program and library of shared functions becomes quite gray.

---

### Post by Praill on 2007-07-03
> **ynnhoj said:**
> you might be interested in gobo linux; it has a different filesystem hierarchy.  link: [gobo linux at a glance](http://www.gobolinux.org/?page=at_a_glance).
This looks great. They even maintain the old-school unix directory structure as sym links so that any program can find another program it needs. This is exactly the type of system ubuntu should approach.. for its user friendlyness alone.

---

### Post by az on 2007-07-03
> **Praill said:**
> I have a long unanswered question that has been refreshed in my mind by a different question in the forum.

What is the reason behind the continued use of the old unix folder structure?

When someone installs a package its contents are scattered throughout the folder structure. The executables are installed in /bin, /usr/bin, /usr/local/bin, /usr/share, ~/<program name>, etc. The modules are installed in /usr/lib, /lib/, /usr/local/lib. The man files, the help files, etc, are the same story. God forbid you install a program that doesnt make a menu entry. Most of the time you can execute the programs name in a terminal (not very user friendly) but if it installs in /usr/local or ~/ then you have to search for it. Also, a program like EasyCam installs the executable by the name of lauchcam2 (no thats not a typo). The only way for me to find this program after installation was through exhaustive google searching.

Furthermore, say I decide to create a program called lauchcam2 (not knowing one exists). We are going to overwrite eachother. It just doesn't make any sense. Why not do like windows and install in a program files directory? This makes everything not only easier to find, but it makes your system (and what's installed on it) easier to navigate.

Hopefully someone can explain this to me because I just don't see the logic behind the way linux does this.

Obviously, it's not meant to be that way.

There are a few sets of guidelines.  In the linux filesystem hiearchy, certain things go in certain places.  In debian and debian derivatives, the package manager is in charge of the filesystem, with the exception of your home folder.  There are strict packaging rules that determine where the files go.  No official deb package will ever put anything in /usr/local.  If you have stuff there, they were put there by a third-party and I would frankly stay away from such third-party binaries if I could.

Any supported Ubuntu desktop package has a menu entry.  Since Debian uses a different menu than Ubuntu, deb packages that are not officially supported by Ubuntu may or may not have the Ubuntu-type menu.

Also, it is presumed that since the package manager is charged with dealing with the rest of your filesystem, if you want to create your own application, you either keep it  in your home drive, or you know what you are doing so that you do not overwrite anything useful.

---

### Post by Jucato on 2007-07-03
> What is the reason behind the continued use of the old unix folder structure?

Simple answer. Linux is meant to be like UNIX. And in order for it to keep that identity, it needs to comply with certain standards, one of which is the filesystem hierarchy. Now, if Linux stopped using that, even just "under the hood", it wouldn't really be Linux, would it?

>  When someone installs a package its contents are scattered throughout the folder structure. The executables are installed in /bin, /usr/bin, /usr/local/bin, /usr/share, ~/<program name>, etc. The modules are installed in /usr/lib, /lib/, /usr/local/lib. The man files, the help files, etc, are the same story. 

UNIX/Linux groups files according to purpose, not according to package/program (like in Windows). This makes it easier to share resources, and also makes it a lot easier to put a certain directory in another partition, without disturbing the whole system. (In fact, Linux only sees one single filesystem. It doesn't know/care whether directories are mounted in other places).

> God forbid you install a program that doesnt make a menu entry. Most of the time you can execute the programs name in a terminal (not very user friendly) but if it installs in /usr/local or ~/ then you have to search for it. Also, a program like EasyCam installs the executable by the name of lauchcam2 (no thats not a typo). The only way for me to find this program after installation was through exhaustive google searching.

This is what a filesystem standard is for. This is also what distributions are for. The standard locations for an executable will always be in a bin/ directory, and by default, it should be in /usr or /usr/local. At least you'd know where to look. (Some Windows programs don't actually install in the Program Files directory).  Distributions also take most of the load off your shoulders, by building packages in a way that the correct files are put in the correct directory. Also, it's the responsibility of the programmer who created the software to install set it up to install in the correct places. If it doesn't you should file it as a bug.

Also, not all apps have menu entries, most specially command line apps. If a GUI app that should have a menu entry doesn't have one, it's most probably a bug.

> Furthermore, say I decide to create a program called lauchcam2 (not knowing one exists). We are going to overwrite eachother. It just doesn't make any sense. Why not do like windows and install in a program files directory? This makes everything not only easier to find, but it makes your system (and what's installed on it) easier to navigate.

It depends. Generally, you don't want to install your own programs in, say, the system directories like /usr. You'd install in /usr/local or in /opt. Not only do you lessen the risk of clashing with existing files, you also make it easier to maintain your own program in your own way.

You have to consider where Linux is coming from and what Linux is to be able to understand why we do things this way. Linux takes its inspiration from UNIX. What this means is that there is a bit of a focus on:
- multi-user: if I remember correctly, UNIX was the first truly multitasking, multi-user operating system. The directory structure makes it very easy to manage multiple users and resources
- resource sharing: UNIX is big on this. This is one of the reasons why everything with the same purpose is placed in the same place.
- flexibility: it is so easy to put different parts of the filesystem in different partitions/disks, without affecting the system. In fact, advanced users probably put /var, /etc and others in different partitions.
- administration: let's face it. Until recently, Linux has been the realm of geeks, programmers and administrators. dumping all config files in a single directory makes it easier to manage them.

So why does Linux still use the UNIX filesystem hierarchy? Because it still works.

Of course, it's not perfect, specially on the end-user end of things (like "migrating" a certain app to another installation). I myself have wrestled with the difficulties brought about by splitting config files and app data. I don't know if Gobolinux presents a good, viable solution to that. Whatever the solution may be, I don't think changing away from the UNIX structure will be beneficial in the long run.

EDIT: Oops! forgot to give some links:
Some slightly technical reading:
[http://www.tldp.org/LDP/sag/html/fs-background.html](http://www.tldp.org/LDP/sag/html/fs-background.html)
[http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/foreward.html](http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/foreward.html)

---

### Post by Tomosaur on 2007-07-03
How about this for an idea?

A minor alteration to the installation process (and it would even be possible to download a 'converter' so that your current system could benefit):
When you install a package, the package contains all of the information about where to place the various files. There are certain standards which are usually adhered to, such as binaries in /usr/bin, documentation in /usr/share/doc, and so on. Now, what I propose is that we add a little function to dpkg so that some soft links are created in some other directory (/software for example), while the actual files are stored in the usual place. For example, lets say we have a package which has the following files and their target directories:
```

convertor ---> /usr/bin/convertor
conv_lib.so ---> /usr/lib/conv_lib.so
README ---> /usr/share/doc/convertor/README
COPYING ---> /usr/share/doc/convertor/COPYING
convertor-logo.png ---> /usr/share/pixmaps/convertor-logo.png

```

Why can't we keep this structure, but ALSO create a software directory which only contains LINKS to files, but uses the package's name? For example, the structure of the software folder would look like this:

```

/software
||||||/convertor (the root of the package's directory would contain a soft-link to the binary)
||||||||||/doc (this directory would contain a soft-link to the various documentation files)
||||||||||/lib (this directory would contain a soft-link to the various libraries required by the software)
||||||||||/data (this directory contains miscellaneous stuff like images, sound files, videos etc)

```

Now granted, given the nature of free software, programs tend to share stuff, which is why the current system is so beneficial. Theoretically, this new system is a 'waste of space', even though we wouldn't actually have multiple copies of the files, we'd just have multiple links to the files. Even though we're wasting space, we're wasting a very, very minimal amount. This method also means that compatability isn't an issue. Developers don't need to worry about the new software folder, because everything is sorted out by dpkg.

At the end of the day, the current system is fine for me, but I think that we should have the CHOICE of a different system. As I've just shown, there's no reason why we need to get rid of the current system, or even why this should be a difficult task to accomplish (because it really isnt, it wouldn't take much work at all). Obviously, the current system is not ideal for some people, and if they've only used Windows in the past, then it's pretty obvious that they may be thrown off by the directory structure which Linux uses. I see no reason why a secondary 'fake' directory structure couldn't be included as an option when first using your new Ubuntu machine. For the hard-core efficiancy junkies, they can just leave the feature turned off, but for those who like a more centralised structure, they can enable it and then be satisfied. 

If something like this were to be adopted, however, we would still need to keep the new directory structure outside of the home folders, otherwise we'd have as many duplicates as there are users, which is just pointless. Anyone wishing to edit stuff inside the new software directories would still need to use root priveleges.

---

### Post by fyllekajan on 2007-07-03
> **Praill said:**
> This is exactly the type of system ubuntu should approach.. for its user friendlyness alone.

No that's insane. There's no need for Ubuntu or any other Linux distro to prostitute itself for Windows users. Adding a kernel patch and a billion hidden symlinks to Ubuntu would make a fine mess. When talking about user friendliness the Windows way is NOT always the most intuitive way to do things - now this may come as a surprise to some users here with their definition of user friendliness screwed up. :)

Ubuntu should improve it's user friendliness for sure, but the user shouldn't need to deal with those things the package management system can do for them. And experienced users already knows how the filesystem works anyway. But if you still want to mess with these things there's always Gobo. Or maybe you could take this question to the devs, and then post the reply here. I mean this discussion is just as stupid as the one about removing the CLI. :)

---

### Post by dca on 2007-07-03
I don't know, this may help:
 
[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

---

### Post by Tomosaur on 2007-07-03
I agree that the GoboLinux solution is completely backwards. In the solution I proposed, it's kind of the 'inverse' of the GoboLinux one. The old UNIX structure is still the primary directory structure, and is what users will actually be changing if they mess about in the /software directory. The /software directory is just one big clump of symlinks/

Fyllekajan: I agree with the sentiment, but I see no reason why people shouldn't have the **option** of a more centralised directory structure. The one I proposed would be completely optional, and have no impact on the system other than the illusion of a centralised structure in which software is organised. It's true that the Windows way is not always 'the best way', but then, your phone is not necessarily the BEST phone, and my band may not be the BEST band. People have different tastes and opinions. I say, if it can be done, and it will help Linux and the various communities as a whole, then why shouldn't we do it? This thread isn't the first about this topic, so it seems to me that enough people want it to warrant at least the OPTION of using such a structure.

---

### Post by justin whitaker on 2007-07-03
> **fyllekajan said:**
> No that's insane. There's no need for Ubuntu or any other Linux distro to prostitute itself for Windows users. 

It's this sort of rhetoric that really shows a high level of ignorance and elitism in the Linux Community. The man is floating ideas, and you call it "prostitution"?

Exactly where are we going to get new users if not for ex-Windows users? Do Linux Gurus sprout fully formed out of the ether?

Revisiting old ideas and seeing if they are still valid is quite constructive. 

Personally, I like Gobo's approach, because it lets you compile multiple versions of an application against multiple versions of a library-so if you somehow screw up something, you can use the older version of the application. It's not easy to do, but its still useful. 

But with a good search engine, or a database like file system, it's really not necessary.

---

### Post by saulgoode on 2007-07-03
> **Tomosaur said:**
> I agree that the GoboLinux solution is completely backwards. In the solution I proposed, it's kind of the 'inverse' of the GoboLinux one. The old UNIX structure is still the primary directory structure, and is what users will actually be changing if they mess about in the /software directory. The /software directory is just one big clump of symlinks/

But what purpose does that big clump of symlinks serve? Sure, it allows the user to look at what is installed (don't the Debian package managers have such a function?); but if you delete a symlink from this proposed /software directory, nothing has changed. The system still looks for (and finds) the original programs and libraries.

---

### Post by fyllekajan on 2007-07-03
Tomosaur, don't get me wrong here I'm not against options as long as they don't mess with the system - I skipped over some posts (yours included) when first reading the thread. Sure some centralised directory structure would be useful to SOME users and they should have it. Some people may wish to view the whole directory structure in 3d as in fsv and they should have it too. But I fail to see how it would add to the user friendliness when the new Ubuntu user is to poke around in the filesystem directories when s/he shouldn't need to. Then again it's just a point of view. I'm sure the devs know best what to do here.

justin whitaker, call it whatever you like the point stands. Those ideas from the OP has been floating and discussed for so long time it seems more like trolling to me. Point is that Ubuntu should attract ex-Windows users by being a superior and more user friendly OS and not by imitating Windows in every way it can. And I believe there's a good reason this hasn't been implemented in Ubuntu. ;)

---

### Post by igknighted on 2007-07-03
> **Praill said:**
> I have a long unanswered question that has been refreshed in my mind by a different question in the forum.

What is the reason behind the continued use of the old unix folder structure?

When someone installs a package its contents are scattered throughout the folder structure. The executables are installed in /bin, /usr/bin, /usr/local/bin, /usr/share, ~/<program name>, etc. The modules are installed in /usr/lib, /lib/, /usr/local/lib. The man files, the help files, etc, are the same story. God forbid you install a program that doesnt make a menu entry. Most of the time you can execute the programs name in a terminal (not very user friendly) but if it installs in /usr/local or ~/ then you have to search for it. Also, a program like EasyCam installs the executable by the name of lauchcam2 (no thats not a typo). The only way for me to find this program after installation was through exhaustive google searching.

Furthermore, say I decide to create a program called lauchcam2 (not knowing one exists). We are going to overwrite eachother. It just doesn't make any sense. Why not do like windows and install in a program files directory? This makes everything not only easier to find, but it makes your system (and what's installed on it) easier to navigate.

Hopefully someone can explain this to me because I just don't see the logic behind the way linux does this.

The issues you are running into are not due to the file structure, but rather due to sloppy programing/packaging.  If protocol is followed, it makes perfect sense.  /bin is only for system binaries.  /usr/bin is for most applications.  /usr/local/bin really isn't used much anymore.  /opt is a place where many large precompiled programs install.  Sun's Java, the mozilla products (if you install from mozilla's installers not the repo), Songbird, etc.  all install here.  These install into their own self sustained folder, so it is windows like (hence why only bigger projects who don't want to worry about dependency issues use it).  To install to any of those locations you need to be root.  Anything you install as your user will be in ~/.

There are guidelines for where things go.  If packagers are sloppy there can be issues, but this is no different than windows.  Try installing obscure stuff from CNET then figuring out how to run it.  If you install from places other than the repos, expect to have some issues to work around.

If you are installing from the repo, synaptic tells you exactly where everything is going so you can look up the command there.  Many linux apps are CLI only, so why would they get a menu entry?  You should get in the habit of checking what the command to run an app is after you install it, it'll make your life easier down the road.

---

### Post by a12ctic on 2007-07-03
Hmm tbh, I've always found the linux folder structure a LOT simpler than windows. In windows stuff gets lost in the massive Program Files, and sometimes if you delete a shortcut or something youll never be able to find a new .exe to remake the shortcut, especialy with the terrible search capabilities of WinXP. In linux you always know that the bin will be in a bin folder, you know that the configuration files will be in /etc, etc. I guess its always made sense to me...

---

### Post by forrestcupp on 2007-07-03
The Linux file hierarchy is WAY different than Windows, and you have to learn how it works.  But inexperienced Windows users have to put time into learning Windows file structure, too.  You had to learn that programs are placed in Program Files.  You also had to learn that when you install things on Windows, it also puts files in other places too, like Windows\System, etc.  When you install things, it also puts several entries in the registry.  These things are why you can't just find an application's folder in Program Files and delete it, unless you want headaches.

Windows is not as clean as just making a folder in Program Files.  I haven't always felt this way, but I personally would rather have the Linux file structure, than to have the headache of filtering through an unreadable registry.

Edit:
I do have a question, though.  If usr doesn't stand for user, what is it?  And what does etc stand for?

---

### Post by a12ctic on 2007-07-03
> **forrestcupp said:**
> The Linux file hierarchy is WAY different than Windows, and you have to learn how it works.  But inexperienced Windows users have to put time into learning Windows file structure, too.  You had to learn that programs are placed in Program Files.  You also had to learn that when you install things on Windows, it also puts files in other places too, like Windows\System, etc.  When you install things, it also puts several entries in the registry.  These things are why you can't just find an application's folder in Program Files and delete it, unless you want headaches.

Windows is not as clean as just making a folder in Program Files.  I haven't always felt this way, but I personally would rather have the Linux file structure, than to have the headache of filtering through an unreadable registry.

Edit:
I do have a question, though.  If usr doesn't stand for user, what is it?  And what does etc stand for?

usr does stand for user. etc stands for etcetera (or however its spelled).

---

### Post by saulgoode on 2007-07-03
> **a12ctic said:**
> usr does stand for user. etc stands for etcetera (or however its spelled).

Actually, 'etc' stands for Editable Text Configuration.

---

### Post by bapoumba on 2007-07-03
> **saulgoode said:**
> Actually, 'etc' stands for Editable Text Configuration.
Sorry, I'm going to be completely out of the thread topic here. But I cannot resist... Here is one of my [favorite threads on Slashdot ]("http://ask.slashdot.org/askslashdot/07/03/03/028258.shtml") ^^ (quite old, but still makes me laugh).
/me goes out. Back on topic now :)

---

### Post by az on 2007-07-03
> **a12ctic said:**
> Hmm tbh, I've always found the linux folder structure a LOT simpler than windows. In windows stuff gets lost in the massive Program Files, and sometimes if you delete a shortcut or something youll never be able to find a new .exe to remake the shortcut, especialy with the terrible search capabilities of WinXP. In linux you always know that the bin will be in a bin folder, you know that the configuration files will be in /etc, etc. I guess its always made sense to me...

Well, that's the Unix heritage of building an OS as individual pieces that talk to each other rather than big single-purpose applications.  That's why Unix tools are by-and-large mostly the same whther you are running Linux, Solaris or BSD.

It's set up to be efficient at sharing.  I really don't think this sort of "under the hood" stuff is of any significance to the end-user.  Unless you are developing code, you have no business complaining how the filesystem is structured.

Sure there have beed lots of projects like appdirs, klik and autopackage to help with binary-only package installation.  The fact is, the strenght of the software is in it's open source development.  The more you try to make something binary-compatible ( or in this case, try to arrange the binaries esthetically, like a bouquet) the harder you make it for the developer.  I find it hard to make that compromise.

If there is any problem here, it's that some third-parties are providing sub-standard binaries.  If the distro itself was the problem, then it would be an easy fix.

The situation is clear to me:  If you wanna install some binary-only package from some non-official source, do it at your own risk.  Don't go blaming how the distro is organised for the shortcomings of some wierd package or two.

---

### Post by runningwithscissors on 2007-07-03
I've actually replaced a f*cked root partition and all installed programs continued to work like nothing had happened.

Besides, users who don't know anything about the filesystem should not be poking around it. :)

---

### Post by igknighted on 2007-07-03
> **a12ctic said:**
> usr does stand for user. etc stands for etcetera (or however its spelled).

/usr = Unix System Resources, yes?

EDIT: I've seen a few variations, but this is what I have seen from the most credible sources

---

### Post by runningwithscissors on 2007-07-03
> **igknighted said:**
> /usr = Unix System Resources, yes?

EDIT: I've seen a few variations, but this is what I have seen from the most credible sourcesThat's a backronym. Originally it stood for user.

---

### Post by Tomosaur on 2007-07-03
A centralised file structure would alleviate the problems of missing menu items, and binaries with different names to the actual package. With a /software folder, the directories inside that would be the actual PACKAGE names, and inside those would the binaries, documentation, data etc. It doesn't serve any 'purpose' aside from making things easier to find really. The problems that users commonly report could be solved easily by a simple dpkg -L package-name, but unfortunately the kinds of people who get lost are the kinds of people who don't know that they can do that in the first place.

---

### Post by BoyOfDestiny on 2007-07-03
> **runningwithscissors said:**
> I've actually replaced a f*cked root partition and all installed programs continued to work like nothing had happened.

Besides, users who don't know anything about the filesystem should not be poking around it. :)

I would have to agree with this sentiment. But I believe a user shouldn't "HAVE TO" deal with it. As is, for me and users I've switched to Ubuntu, we all stick to /home. 

The only time I've ever had to deal with it is during the testing Ubuntu releases (I get bored, so I'm running Gutsy Gibbon). This is the only time where I've had to deal with something outside of /home, i.e. to make a symbolic link if something changed.

The thought of trudging through ANY filesystems hunting for things seems a waste. If you are a power user, type man which or man whereis. Don't waste your time.

With new standardization from groups like LSB, and continuing refinement of the Filesystem Hierarchy Standard, it will be easier for package managers, front-ends, and what have you to handle things.

[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

If I wanted to manually manage all my 3rd party apps, move installs around, I'd be using Windows... :P

It seems the issue gets touched upon time and again, and I'm feeling some Deja Vu with my response here. I like to compile apps, grab it from cvs, svn, mercurial, git, etc. I like to add a repo rather than manually go through double clicking with gdebi (plus side, gdebi works from CLI...)

I've never once had to mess with anything outside of /home. I rather let the apps do it. I can wipe /, and with /home intact have a fresh install up to my liking within 20minutes. I can't say the same about any other OS's I've used.

I love easy. If you want the filesystem easier, I'd argue add a layer of abstraction rather than tweak something in this fashion.

Time for beagle and tracker. Time for more GUI front ends.

EDIT: Figured I'd add a link to freedesktop, I see in Gutsy some more standards are showing up, so to speak (xdg dirs etc.)

[http://www.freedesktop.org/](http://www.freedesktop.org/)

---

### Post by WinterWeaver on 2007-07-03
Personally I think that, for the system to be user friendly .... you should not have to touch the filesystem at all... except for you home folder. Of course you can still do that if you need to.

I've come to love the Debian/Ubuntu/Linux way of handling programs with the packages. I install a package, and I know that the package manager will sort out where it needs to go, and I dont have to worry about it. I dont think I've ever had to touch any program's folder (except for Screenlets when I had to delete a file, but that was in the home folder..... oh yes... and Zope/Plone for my web development)

For me, I'm quite happy to know where my home folder is, where my extra drives are mounted... and that's it. I prefer not to poke around other places... and so far I'm very happy for that ^_^

I believe that long time windows users feel that they need to understand the dir structure, because they were so used to NEEDING to know where everything is, for maintenance etc. (I'm prob wrong :P)

I for one am happy to not know what is going on lol...

have fun 

WW

---

### Post by forrestcupp on 2007-07-03
It's good to be able to back up my /home directory and reinstall my system.  But the only problem with that is having to redownload all of the programs I installed.  If I could backup all of the debs that I downloaded, that would help.  So is there a centralized place that it puts all of the debs you download through apt?  And if I backed that up, reinstalled my system, and put those files back on my hard drive, could I reinstall those programs using apt without having to download them again?

---

### Post by jasay on 2007-07-03
> **forrestcupp said:**
> It's good to be able to back up my /home directory and reinstall my system.  But the only problem with that is having to redownload all of the programs I installed.  If I could backup all of the debs that I downloaded, that would help.  So is there a centralized place that it puts all of the debs you download through apt?  And if I backed that up, reinstalled my system, and put those files back on my hard drive, could I reinstall those programs using apt without having to download them again?

Assuming you haven't done an "apt-get clean" the debs should still be here: ```
 /var/cache/apt/archives
```

---

### Post by Tundro Walker on 2007-07-03
I'm gonna read between the lines on the OP's post.

I think the reason folks new to Linux complain about the filesystem is because they have a pretty awkward introduction to it.  The start up Ubuntu, and smile happily seeing a GUI with a "start" menu thingy, they mess around with customization of the GUI...all is great.  They go to "Add/Remove" or Synaptic, and are amazed at all the free goodies they can just download.  So, they pick one, it installs, then they go to their "start" menu thingy and don't see an icon.  So, they open up Nautilus and browse the folder/filesystem, and see this totally foreign terrain.  I mean, it's a "folder structure", but not one they're used to from Windows.  They dig through things called "bin", "etc", "usr", usually not knowing what holds what or where their program can be, and eventually come here to complain about how "bad" the filesystem is in Linux.

Personally, I don't think the filesystem in Linux needs to change (unless something totally spectacular comes along, and as of yet, nothing really has, which is why folks are really splitting hairs and things.)  I think the Linux filesystem does its job well, and it's pretty user-friendly for advanced users who want to dig around in it.  But, for "noobs" or "average Windows users" migrating to Ubuntu, I think some user-friendliness could be focused on avoiding ever exposing them to the filesystem much, unless it's their home directory, where they'd make their own folders and such.

And, actually, Ubuntu's repo Master of the Universe folks have done a pretty good job of this.  They've taken some programs, which usually just install without any clue where it's gone, and tweaked it to provide a "start" menu shortcut and such.

Computers are complex things, and I think a lot of folks have gotten so used to them being dumbed-down interface-wise, that they kinda freak out when they're exposed to the guts of the operation.  I mean, on your iPod, you're not exposed to really bizarre directories or such when you're trying to find the music you just tossed on it.  Folks take that mentality, and bring it over to their computer, and it's just not being fair.  Your iPod plays some tunes...your computer can theoretically help you take over the world...

---

### Post by FreeFog on 2012-08-12
The Linux Hierarchies are designed to solve problems, they are the result of long earned communal experience, understanding their purposes will ease your life.

In Dept Explanation:
[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/c23.html]("http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/c23.html")

Skip the technical details and try to get the essence of each directory branch.

---

### Post by nothingspecial on 2012-08-13
[IMG]http://img845.imageshack.us/img845/6976/necro2.png[/IMG]

---

