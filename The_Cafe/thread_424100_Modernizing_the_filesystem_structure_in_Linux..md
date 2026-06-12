---
title: "Modernizing the filesystem structure in Linux."
date: 2007-04-26
forum: The Cafe
---

### Post by moma on 2007-04-26
After reading the blueprint of filsystem structure changes in Ubuntu, 
( see: [https://blueprints.launchpad.net/ubuntu/+spec/hide-filesystem-structure/](https://blueprints.launchpad.net/ubuntu/+spec/hide-filesystem-structure/) )

I decided to write my own proposal to radically lift the the old Unix alike Filesystem Hierarchy Standard ( FHS) to a modern age.  

The current, ancient path structure has fixed locations and weird, nerd'ish names such as /etc, /usr and  /srv. The naming was accidentally created tens of years ago and is for servers only, it's not for an average joe Desktop user to understand !

**So here is a proposal for a new File Hierarcy Standard (FHS) for Linux/Unix alike operating systems -- for both Server and Desktop purposes.**

(I haven't mentioned all possible sub directories)
```
/

/sys
	/boot
	/os 
	/setup
		/init 
		/network
	/bin 
	/sbin
	/lib
	/include
	/gui
		/gnome
		/kde
	/temp
	/var 
	/dev 
	/proc 	

/media
	/cdrom
	/dvd	
	/floppy
	/zip
	/windows

/programs
	/share
		/pixmap
		/background
		/sound
		/manual 	
	/gimp
	/scribus
	/openoffice
	/mozilla
		/thunderbird
		/firefox		

/home
	/root 
		/temp

	/anna      ( anna is a normal Ubuntu user)
		/desktop
		/programs
		/documents
			/pictures
		/music
		/temp
		/.setup
			/gimp
			/thunderbird
			/firefox

	michael   ( michael is also a normal Ubuntu user)
		/desktop
		/programs
		/documents
			/pictures
		/music
		/temp
		/.setup
```

**A common FHS library routines**
==========================
We need a library that knows everything about path names and locations and how to handle them.
Let's call this library for pathinfo.so.

Here are some values this library should comprise.

// ---- pathinfo.h ----------
// Table:

```
Path name     	      Default value 	  Meaning in the current (old) Linux-distributions

SYSTEM_BIN            /sys/bin            # /bin and /usr/bin, /usr/local/bin
SYSTEM_SBIN           /sys/sbin           # /sbin/
SYSTEM_SETUP          /sys/setup          # /etc					      Cannot be shared
SYSTEM_OS             /sys/os		  # /sys 					      Not sharerable
SYSTEM_PROC 	      /sys/proc           # /proc					      Virtual, not sharable
SYSTEM_LIB    	      /sys/lib		  # /lib, /usr/X11/lib, /usr/local/lib 
SYSTEM_INCLUDE	      /sys/include	  # /include, /usr/local/include 
SYSTEM_BOOT	      /sys/boot	          # /boot
SYSTEM_TEMP	      /sys/temp           # /tmp 					      Cannot be shared
SYSTEM_GUI	      /sys/gui            # currently scattered in many places	
SYSTEM_VAR	      /sys/var            # /var 					      Cannot be shared	
SYSTEM_DEV 	      /sys/dev            # /dev					      Cannot be shared
SYSTEM_PROGRAMS	      /programs           # /usr/, /usr/local, /opt 

SYSTEM_ADMIN          /home/root 	  # /root

USER_BASE             /home		  # /user or /home depending on system (Unix/Linux).
USER_HOME             $HOME	          # User's $HOME, normally /home/<username>
USER_TEMP             /home/temp	  # $HOME/tmp
USER_SETUP            /home/.setup	  # scattered in numerous hidden files under $HOME
USER_DOCUMENT         /home/documents	  # $HOME/*
...etc...
```

Programs should never use fixed, constant path names, instead they should ask this common library what the locations are. Here is a sample Python script (a model of such) that queries some important locations.

# Import FHS (Filesystem Hierarchy Standard) library.
import fhs      # Maybe pathinfo is better name for this library.

# returns /sys/temp 
global_tmp = fhs.query_path(SYSTEM_TEMP);

# returns /sys/setup
global_setup = fhs.query_path(SYSTEM_SETUP);

# returns /sys/var/log 
global_setup = fhs.query_path(SYSTEM_LOG);

# returns /home
user_home = fhs.query_path(USER_HOME);

# returns $HOME/.setup
user_setup = fhs.query_path(USER_SETUP);
-------------------------------------------------------------

**Command line utility **
=================
We can also create a tiny command line utility (fhs) to be used from CLI.
$ fhs SYSTEM_SETUP 
/sys/setup 

# Eg. this command would list all standard path names.
$ fhs -l 
/sys
/sys/boot
/sys/os 
...etc...


**Configuration:**
=============
Its merit is simplicity and beauty.

The default values of the path names are defined in the above table.
But I propose that the system administrator (root) could re-define all or some of the locations by assigning a new name into /.fhs.conf file.   

Here is an example of such /.fhs.conf file.
```
# ---- /.fhs.conf ----
# Use this file to re-assign system and user path names.
# If no /.fhs.conf is present then default values are used.
#
# Operating system will automatically send a PATH-CHANGED signal 
# to all processes and programs after changes.
#
# For more information, see: man fhs

# Set old fashioned root account
SYSTEM_ADMIN=/root

# Testing some MYSQL settings in a temporary /test/setup directory. 
SYSTEM_SETUP=/test/setup 

SYSTEM_LOG={USER_HOME}/log

# I want to test the latest KDE
SYSTEM_GUI=/test/gui

# Override /media
SYSTEM_MEDIA=/mnt 
```

Can you see how flexible this would be. 
Eg. Let's say you want to test some new settings for MySQL engine. For that, you could re-assign /sys/setup (which is now known as /etc) to a new location ( /test/setup ).

**Caveats:**
In the current Linux world, some directories must have a fixed location.
Eg. the boot process is dependent on /bin, /sbin, /dev and /etc directories. 
These must be on the same file system during the start (and cannot be mounted or re-mounted)

Huge amount of software must be rewritten to use the new FHS library. It's not so many lines of code pr. application but still...a job to do.

**Important questions:**
What directories can be shared between
	- several login users?
	- several instances of operating systems?

Can we re-place the /boot directory or must it be strictly under the root file system?

Can we improve the boot-process so /bin, /etc, /dev and /sbin can have variable locations?
EDIT: One solution is to statically compile and link those applications (such as bash and mkdir) that are needed by boot-process.

**Implementation:**
The above mentioned FHS library and /.fhs.conf file allows easy and step-by-step transition from old FHS to new structure.

The new FHS mechanism should be baked into Freedesktop.org and LSB standards.

**Security and logability:**
No doubt, this new FHS will make Linux operating system much more saleable, streamlined and easier to learn than the old one.
Directory names and their function will be self-explanatory. No more cryptical names like /etc and /usr/local/bin and all that chaos.

But does this new FHS introduce new security aspects?  and
                   + should we introduce a directory content snapshot mechanism which allows users to rollback directory content and installations.
                   + should it include a file accounting and logging mechanism to improve the security and reporting. What directories and files was changed? Rollback or commit !

**Target platform:**
Gutsy Gibbon + 1

**Related documents:**
[https://wiki.ubuntu.com/HideFilesystemStructure](https://wiki.ubuntu.com/HideFilesystemStructure)

[https://blueprints.launchpad.net/ubuntu/+spec/userfriendly-filesystem-structure]("https://blueprints.launchpad.net/ubuntu/+spec/userfriendly-filesystem-structure")

The current Linux FHS spesification: [http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

BSD Unix FHS: [http://www.freebsd.org/cgi/man.cgi?query=hier]("http://www.freebsd.org/cgi/man.cgi?query=hier")

xdg-user-dirs:  [http://freedesktop.org/wiki/Software_2fxdg_2duser_2ddirs](http://freedesktop.org/wiki/Software_2fxdg_2duser_2ddirs)

Xdg-utils: [http://portland.freedesktop.org/wiki/XdgUtils](http://portland.freedesktop.org/wiki/XdgUtils)
(must be amended...)
------------------------------------------

Your comments welcomed.

Sincerealy
   // moma

---

### Post by Sunnz on 2007-04-26
First thing comes to mind is that Ubuntu wouldn't be such a good platform for the purpose of 'learning UNIX'... e.g. my school's lab uses Kubuntu so large organisation like those might have to switch back to Debian when 6.06 LTS ends...

But I guess we'll see what others think first.

---

### Post by bonzodog on 2007-04-26
Using a new file system structure would create major problems in cross compatibility between the other 100 odd distros, and prevent backwards compatibility to enable us to push bug fixes upstream to source or just to debian main. 

I don't think somehow that debian would accept any of this without it becoming de-facto from the kernel downwards, meaning that it would then flood to each and every distro as and when they changed kernel. 

This change would have to be carried out by the Kernel devs themselves, on direct instruction from Linus himself.

It would also mean that most current software would not currently compile on the new system with out paths being passed to the configure script. No-one on ubuntu at the moment would be able to pull a clean vanilla source off sourceforge and just compile the program, without knowing the path changes, or forcing automake to re-write the configure script for each program in compilation. 
Gobolinux got around this by leaving an old directory structure in place, but encouraged all its users to learn how to build programs from source and pass options to the compilers.

I dunno, I am happy with the 30 year old Unix dir tree, it works. I really think this is a case of "If it isn't broke, don't fix it".

---

### Post by Crashmaxx on 2007-04-26
Gobo Linux is already doing this sort of thing with their distro. In order to keep it working with existing apps, they have hidden hard links that simulte what the programs expect to see. It is pretty neat, and their real goal, is to convince devs to make their apps so that they can be installed in any location the user sees fit and have nothing 'hard coded' to point to a specific location.

There is a big thread about it here:
[http://ubuntuforums.org/showthread.php?t=295071](http://ubuntuforums.org/showthread.php?t=295071)

---

### Post by forrestcupp on 2007-04-26
I know it isn't feasible to change the filesystem, but that is my biggest complaint about Linux.  For instance, I installed the Commodore emulator called VICE.  It took me forever to track down all the different directories that this package was installed.  The binary was installed in /usr/bin like normal, but then I had to figure out where to install the kernel ROMs.  It's just a pain sometimes to figure out where everything goes.

But it would be a very major thing to try to change something like that.  That's probably a bigger change than switching everyone over from 32 bit to 64 bit.

---

### Post by Zuph on 2007-04-26
The problem is that the current filesystem structure is GOOD and it works and it makes a whole lot of sense to anyone that has used it for a while.  Giving something more intuitive names or subdividing things further will not help anything.  And making the Linux filesystem more "Windows-like" defeats the purpose of it being a different OS.  Linux isn't better because it's like windows but free, it's better because of differences like the filesystem layout.

---

### Post by ViRMiN on 2007-04-26
Is it broke?

---

### Post by Roberticus on 2007-04-26
I say yay to this kind of change. Takes ages to learn where everything is...
Easier for new users (such as me) to find stuff =)

---

### Post by wmcbrine on 2007-04-26
> **Zuph said:**
> The problem is that the current filesystem structure is GOOD and it works and it makes a whole lot of sense to anyone that has used it for a while.Agreed. I strongly reject this proposal.

I even reject the much more modest proposal linked at the top, about ".hidden". Heck, the first thing I do on a Windows system is turn off the awful hiding of extensions and system files. I'd hate to see Ubuntu go down that road.

But if you really want to do this, you might first study what Apple's done with OS X. It  has a lot of "nonstandard" (from a Unix perspective), "user friendly" directories in its layout, but also manages to hold on to traditional Unix functionality fairly well (though not as well as Ubuntu or other Linux distros).

---

### Post by tbroderick on 2007-04-26
> **forrestcupp said:**
> For instance, I installed the Commodore emulator called VICE.  It took me forever to track down all the different directories that this package was installed.  The binary was installed in /usr/bin like normal, but then I had to figure out where to install the kernel ROMs.  It's just a pain sometimes to figure out where everything goes.


Maybe VICE needs better documentation.

---

### Post by Nils Olav on 2007-04-26
> **ViRMiN said:**
> Is it broke?

It's imperfect.

---

### Post by karellen on 2007-04-26
even if I can't say I'm pro or against this (as the current structure is ok for me but I wouldn't mind if it would be a new one) I must say that you've put some work into this proposal. nice :)

---

### Post by aysiu on 2007-04-26
> **wmcbrine said:**
> 
I even reject the much more modest proposal linked at the top, about ".hidden". Heck, the first thing I do on a Windows system is turn off the awful hiding of extensions and system files. I'd hate to see Ubuntu go down that road. It already went down that road on Kubuntu Edgy, which hid all the system folders defined in /etc/kubuntu-default-settings/

That confused a lot of people.

---

### Post by forrestcupp on 2007-04-26
> **tbroderick said:**
> Maybe VICE needs better documentation.

When I found the directory that had the documentation, It wasn't bad.  The problem was finding where the documentation was.  This was just one example.  When you install things from the repos, it's not easy to find things.  I know the binaries are usually in /usr/bin or /usr/games, but the one binary file is only a small part of a software package.

---

### Post by tehkain on 2007-04-26
Well first off, if you need to go out of your home folder you should already know the file hierarchy. If you don't then you should probably stick to not messing with those files. Beginners going around in the system messing with files is not something we should be encouraging with a simple file structure. They are sure to end up with a broken system.

Now to the gobolinux link system. From what I heard the files are still in the normal spots but they hide and hardlink the files to these 'fake' folders. The only reason that makes sense for then is that they use the drag and drop install method. 

The issue I have with this is that it encourages people with little to no knowledge to mess with files they shouldn't even touch. Since they can easily find them.

I am however a strong believer in a modular install system in the far far future. Where every program will be contained in a special folder that is more of a container so that you can smoothly add and remove modules and not leave anything behind. Like lets say gedit will be one file that has many other inside it. So if 'bob' wants to use my gedit versions all he needs to do delete his and slide my file in.

---

### Post by tbroderick on 2007-04-26
Well, you could go to packages.ubuntu.com and look up vice. If you click on 'list of files' it will display where everything is. I think synaptic has that feature too. Another option would be to use (s)(r)(l)ocate. Just run sudo updatedb and then you could search for vice. But most applications install their the docs in a standard location, /usr/share/doc/name_of_program. Which would be the first place you should look.

---

### Post by bobbybobington on 2007-04-26
Perhaps we could have a middle of the road solution, kinda what apple does. Just give nautilus the ability to toggle between two "modes". a "default" that displays the folders with more logical names, and an "advanced" that shows the regular unix folder names that are under the hood. This way, you wouldn't need to change the filesystem structure, and would make new users lives a lot easier.

---

### Post by timpino on 2007-04-26
> **bobbybobington said:**
> Perhaps we could have a middle of the road solution, kinda what apple does. Just give nautilus the ability to toggle between two "modes". a "default" that displays the folders with more logical names, and an "advanced" that shows the regular unix folder names that are under the hood. This way, you wouldn't need to change the filesystem structure, and would make new users lives a lot easier.

A good idea IMO, give them tags or something that can be displayed instead of the names. when I first started with linux I had no idea etc is where you configure stuff. Displaying it as "Configurations (/etc)" would be great for beginners who don't follow instructions by copy and paste.

---

### Post by jpatton on 2007-04-26
Certainly very well thought out, and many of the folks commenting have some valid points as well, seems to me if you had the right amount of development experience, that you could implement this as a new distro, perhaps using the LFS as the basic groundwork.

While I don't know if I agree on the need, I certainly applaud the detail and lucidity of your argument.

Good work!

---

### Post by ssodhi on 2007-04-26
> **ViRMiN said:**
> Is it broke?

Nope.

Might I interject with the 'so don't fix it'? 

-Sanjay Sodhi

---

### Post by igknighted on 2007-04-26
> **Zuph said:**
> The problem is that the current filesystem structure is GOOD and it works and it makes a whole lot of sense to anyone that has used it for a while.  Giving something more intuitive names or subdividing things further will not help anything.  And making the Linux filesystem more "Windows-like" defeats the purpose of it being a different OS.  Linux isn't better because it's like windows but free, it's better because of differences like the filesystem layout.

Agreed.  I wish people would take the time to learn the file system instead of fighting it, it is such a large part of why linux is great.

---

### Post by Polygon on 2007-04-27
i noticed that a lot of your directories are assuming that the user uses a certain program (aka your gnome,kde, gimp, and etc subdirectories)

and i also dont see the need to change it. The only downside of the hfs that linux uses is that the files for programs get spread out across the filesystem, but that is counteracted by packages like .deb files which keep track of where everything is, and stuff like the gnome menu that lists all programs that are set up correctly and place the correct .desktop file in the correct directory when you install it.

---

### Post by Sunnz on 2007-04-27
The only thing that I think should change is the installation of 3rd party apps should be in their own directory, this includes everything you install from Synaptic or preinstalled during installation... basically any thing besides the 'base' system.

So say if you install mysql (or preinstalled from Ubuntu Server) it should be installed in /usr/mysql/ (or /usr/local/mysql/) and have its config in a etc or config directory under it.

I mean, stuffing all the configuration files under /etc is not a good idea. Mysql has a config file called... what? my.ini!!! How can they ensure that no body else on the other side of the planet would never ever ever use the same file name for their config file!!

Otherwise, I say keep it as it is. I know a lot of people here are more used to the GUI side of things... but remember there are people who use Ubuntu as server and there are certainly a lot of people using other distros. A great advantage of the structure as we know today is **efficiency** on the _command line_. Try compare how to get into someone's home folder on nix and Windows:
Linux:
cd /home/user/
Windows:
cd \\c\documents and settings\user\

And if you want to change Mozilla settings:
Linux:
vi /home/user/.mozilla/.profile/cookie.txt
Windows:
notepad.exe  \\c\documents and settings\user\Application and support\mozilla\.profile/cookies.txt

I hope you get what I mean now. Make things neater, but don't overdo it!!!

---

### Post by BoyOfDestiny on 2007-04-27
> **tbroderick said:**
> Maybe VICE needs better documentation.

No, it doesn't need better documentation. It's actually excellent.

[http://www.viceteam.org/vice_4.html#SEC23](http://www.viceteam.org/vice_4.html#SEC23)

It's in there... However this "issue" is due to the fact the ubuntu package. doesn't include the kernal (for c64 yes it's kernal with an a...). 

Now where does Ubuntu say this, in the VICE description in synaptic:

"This package does not contain the various ROM images needed to actually use the emulators; they are available separately from other locations (see the README.ROMs file).  A corporation in the
Netherlands called Tulip holds the copyrights to the ROM images, and redistribution is not permitted, but VICE itself is unencumbered."

Users need to read the documentation, changing file structures doesn't seem the way to go about this. If you need to find where an app is installed via synaptic, right click on the package, properties, installed files.

From terminal
for example will show the vice c64 emu...
whereis x64

One can only imagine documentation being incorrect and outofdate with variations on the filesystem heirarchy. If it encourages people to poke around instead of reading the readme... I'd say this is bad all around. 

Keep the file system as is, tweak it with soft links if need be...

EDIT: I wonder if my response was too harsh. For new users (as I was one just a few years back) need an introduction to using man, and an easier way to navigate to relevant documentation. Ideally no config would be needed (pretty much everything I've installed from Ubuntu's add/remove) Anyway, I still think these changes would be some layer abstraction, not tweaking of the file system organization.

---

### Post by ViRMiN on 2007-04-27
That was what I was hinting at Sanjay :)

To be honest, if it changed radically, I'd change distros.  Maybe it's the ex-Windows users who need to change rather than make Unix/Linux look like what they're familair with... 2p credit used.

---

### Post by Tomosaur on 2007-04-27
Yeah, I'm against change. Linux has used this filesystem forever now - it's good, and it does actually make sense after a while. Besides, changing anything now would quite simply break a lot of programs, cause every tutorial site out there to become defunct, and cause hell for those businesses who have actually invested in Linux.

I just don't think there's any need to change, to be blunt. I don't see the directory structure as 'old' - if anything, it makes FAR more sense, and is actually more intuitive than, say, the Windows dir structure. It just takes a little time to adjust to, but it wasn't exactly brain surgery.

---

### Post by yota on 2007-04-27
> **forrestcupp said:**
> I know it isn't feasible to change the filesystem, but that is my biggest complaint about Linux.  For instance, I installed the Commodore emulator called VICE.  It took me forever to track down all the different directories that this package was installed.  The binary was installed in /usr/bin like normal, but then I had to figure out where to install the kernel ROMs.  It's just a pain sometimes to figure out where everything goes.

dpkg is able not only to tell where are stored all the files of a package (and the same information is available under the synaptic package manager, just look under the properties of an installed package)
> 
yota@linbook:~$ dpkg -L vim
/.
/usr
/usr/bin
/usr/bin/vim.basic
/usr/share
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/vim
/usr/share/doc
/usr/share/doc/vim

it can inform also the package that owns every single file you have on your box
> 
yota@linbook:~$ dpkg -S /usr/share/lintian/overrides/vim
vim: /usr/share/lintian/overrides/vim


I see more and more discussions about a complete change in the fs hierarchy, so here are my two cents.
Maybe the FSH is a bit daunting at first, but there are lots of good reason for it to stay as it is.
IMHO one above all is that it's really rational and flexible and the same structure can be used on a small desktop as well as on a large datacenter server.
If someone looks only at the single particular applications many things can get overlooked; what we have now is already the result of more than 10 years of natural evolution, surely it still can be improved more, but a complete rework would only mean to waste lot of good work already done.
Moreover if the point is to have an easier and comfortable environment for the new user, a presentation layer can be added on top of the existing structure without screwing it up.

In the end just one word about gobolinux: symlinks are not infallible. If someone who thinks that gobo "symlink compatibility layer" is really a smart idea and wants to discover some glitches here and there I suggest to try and see for yourself: just boot with the live cd, mount your root partition, rename every folder as you like and make symlinks to provide older names (like /home -> /Docs and Setts).
Welcome to the "it mostly works, but not always" world.
Aside the hardlinks can be really really dangerous when used on a large scale (and cannot be used across different partitions).

---

### Post by r.k.maroon on 2007-04-27
I'd like to suggest alternate or multiple file-view systems.  There really isn't a problem (that I know of) letting the OS display different views of the same files; the underlying structure is dependent the filesystem and the likes anyhow.  Being able to choose how the filestructure is presented would be awesome.  So linux-buffs get their /var directories and I get my /sys directory. 

Correctly done, this would preserve legacy compatibility and the likes.  To clarify, I'm talking about virtualizing the filesystem and presenting a view-layer that's separate from the actual files on disk.  The underlying structure could be chosen according to whatever scheme seems optimal.  

I really, really like the idea of a /sys directory, because it somehow reminds me of the olden days and my amiga.

I really, really DON'T like the idea of a .hidden file.  Ugly, ugly, ugleeey!  Don't obfuscate the otherwise so clear and transparent nature of . naming.  Configure programs to do this, don't mess with /

---

### Post by timpino on 2007-04-27
I think a complete remodel of the filesystem is going over the top, but having a virtualization layer and/or discriptive tags along side the directory names is a good option for teaching new users the filesystem. For a new user the directory names don't mean jack schitt except for maybe /home.

For instance: a person has a problem with his/her resolution
the cure: go to /etc/X11 and edit xorg.conf to add your desired resolution (and/or edit refresh rates on your monitor). This is a one shot fix, the user might know the next time this problem arrises what to do. But if instead he/she sees it as going into /system/configurations or just /Configurations (/etc) and then going into X11 the person will know that not only does /etc store configurations for X11 but most likely for any other application he or she has installed on his or hers computer.

In short I think it will help new users get used to the old filesystem and grow to like it faster than otherwise.

EDIT: Typo

EDIT2: Also this would remove some of the need to study the filesystem of *nix before trying to use it.

---

### Post by stimpack on 2007-04-27
GoboLinux file system is very nice, OS X file system is nice. The way OS X handles Applications (the .app, read up on it) is simply beautiful.

Linux filesytem is very bad. It suited the times, but the times were quite a long time ago now, we need something that wasn't designed by Doug McClure, spear in hand.

---

### Post by samjh on 2007-04-27
If Ubuntu changes its file system structure, every distro had better do the same, otherwise compatibility will suffer.  Linux being incompatible with Linux is not acceptable, IMHO.

Linux is also seen as a cousin to Unix, and used for teaching Unix.  It will lose that value too, if its file system changes.

What Linux distros need is better documentation, rather than a complete overhaul of the file system.  Perhaps a brief "Welcome to Linux" interactive tutorial might be a good idea.

---

### Post by Nils Olav on 2007-04-28
> **samjh said:**
> If Ubuntu changes its file system structure, every distro had better do the same, otherwise compatibility will suffer.  Linux being incompatible with Linux is not acceptable, IMHO.

Linux is also seen as a cousin to Unix, and used for teaching Unix.  It will lose that value too, if its file system changes.

What Linux distros need is better documentation, rather than a complete overhaul of the file system.  Perhaps a brief "Welcome to Linux" interactive tutorial might be a good idea.

It would be 100% compatible with the FHS. Nothing would brake.

---

### Post by jrusso2 on 2007-04-29
There is no reason to change the world just because people won't learn it.  The file system has been working fine a long time.

---

### Post by DoktorSeven on 2007-04-29
I've seen this silly argument many, many times, and have said the same thing each and every time:

those who think the file structure is "confusing" or "needs modernizing" do not understand the Linux filesystem.  Take the time to understand it and they'll find that it makes more sense than what they're trying to change it to.

---

### Post by dspari1 on 2007-04-29
The vast majority of the people against the idea are justifying against the change by claiming that standard programs will no longer compile under a new system. GoboLinux already proves that this isn't the case, so that argument is moot.

With that covered, lets have a conversation on WHY the current system is better than the proposed one. The common middle ground is to just have two different view modes; Basic and Advanced; thus the directories will be categorized in a laymen language by hot-linking the directories without actually changing the filesystem.

---

### Post by dspari1 on 2007-04-29
> **DoktorSeven said:**
> I've seen this silly argument many, many times, and have said the same thing each and every time:

those who think the file structure is "confusing" or "needs modernizing" do not understand the Linux filesystem.  Take the time to understand it and they'll find that it makes more sense than what they're trying to change it to.

First of all, the original poster seems very knowledgeable in what he is talking about, so discrediting him by saying he doesn't even understand the filesystem is unjustified.

Trust me, Joe Shmoe and John Doe don't want to or even care to learn the Linux filesystem. They do not care to know that /usr/sbin is for administrative tools and that /usr/bin are the normal applications, or that /usr/games are for games. They do not want to know that /usr/share are where the config files for these apps are located. 

For example, epsxe is in /usr/bin; however, I have to go to /usr/bin/share/epsxe/ to be able to install graphical plugins. The normal user will think "why o why do I have to go to a bazillion different places to find what I'm looking for?"

The only thing they want is a system that is easy to use and figure out without having to spend time reading documentation.

---

### Post by Kvark on 2007-04-29
Having an abstraction layer with 2 different modes would confuse me to no end. Let's say in nautilus I go to /settings/graphics/screen.conf and mess up my resolution so I am stuck with command line only. When I try to change it back using bash I can't find any /settings/ directory. Where did the file I edited 5 minutes ago go?? Oh now it is called /etc/X11/xorg.conf . How was I supposed to know that this time the file I edited before has moved to an entirely different file?

Please just pick one filesystem structure I don't care which. Just stick to it so the files always stay at the same place I found them at before.

It is confusing enough that files beginning with a "." are sometimes visible sometimes hidden. I wish they would make up their mind if they exist or not. If the files where neatly organized in the right places then there would be no mess that needs to be hidden. For example move all the hidden files in /home/user/ to /home/user/settings/ and then you don't need to hide them anymore because they are not in the way anymore. But maybe even that one change would be enough to cause a huge compatibility mess.

---

### Post by hakimaki on 2007-05-27
> **jpatton said:**
> Certainly very well thought out, and many of the folks commenting have some valid points as well, seems to me if you had the right amount of development experience, that you could implement this as a new distro, perhaps using the LFS as the basic groundwork.

While I don't know if I agree on the need, I certainly applaud the detail and lucidity of your argument.

Good work!


I agree, why not undertake this as a project for himself.  Im sure he would be proud of his accomplishment in making it work.  Also, put it out there for others to try.  Even if it never goes anywhere, it would be interesting to see it can be done.

---

### Post by Carlos Santiago on 2007-06-30
Yes! I also think that the filesystem structure needs to be modernized.

For a new user, a directory named  /etc looks like a directory of non important stuff ... and if he was running out of space, he would probably try to delete !

I also like the proposal tree!

Good work!

---

### Post by slimdog360 on 2007-06-30
one thing which annoys me is that if I want to have more then one distro on the same hard drive using the same  /home partition. If I want to use the same user name I have to use the same /home/myusername folder. Now if the two distros use different window managers, things stuff up.

---

### Post by macogw on 2007-06-30
> **slimdog360 said:**
> one thing which annoys me is that if I want to have more then one distro on the same hard drive using the same  /home partition. If I want to use the same user name I have to use the same /home/myusername folder. Now if the two distros use different window managers, things stuff up.

How so?  In one distro, it'll be KDE and in the other GNOME or whatever.  The settings for whichever WM/DE you're using at the time would load.  If you don't want to share settings (I do like to share settings since I can then avoid rearranging all my menus on both of them), let them each put /home in the same partition as root, and make a /media/data partition with a symlink from /home/~username to /media/data called, for instance "stuff" so then you can go /home/~username/stuff and it'll take you to /media/data from either distro while the config in /home/~username would be kept separate of each of them.

I'm not a fan of changing it.  It'd be too confusing to switch distros.  It's already too confusing since most of them don't conform strictly to the standard, so things are often moved confusingly elsewhere.  What we need is for all of the distros to agree to do it the same way, and then stick with that.  I do agree with whomever said that things-installed-after-system-install should go elsewhere.  I'm pretty sure that's the purpose of /opt which seems to go rather unused.

---

