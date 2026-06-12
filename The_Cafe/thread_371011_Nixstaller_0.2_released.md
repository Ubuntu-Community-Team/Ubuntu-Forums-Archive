---
title: "Nixstaller 0.2 released"
date: 2007-02-26
forum: The Cafe
---

### Post by -Rick- on 2007-02-26
I hope noone minds a little bit of advertizing my project ... :KS 

Nixstaller is a Open Source software project that makes it possible to create installers that work on many different UNIX like systems.

Some of the features are:
[LIST]
[*]Lua support for configuring and programming the installer
[*]A ncurses and FLTK frontend (GTK2 and Qt are planned).
[*]Can be fully translated
[*]gzip, bzip2 and lzma compression
[*]Very few dependencies (about nothing for the end user)
[*]Runs on Linux, FreeBSD, NetBSD, OpenBSD, Solaris (and Nexenta).
[/LIST]

The homepage is at berlios: [http://nixstaller.berlios.de]("http://nixstaller.berlios.de").
An example installer for Vim 7: [link]("http://prdownload.berlios.de/nixstaller/vim70.sh").

I've attached a screenshot showing the FLTK frontend. The installation screen is created through a Lua script.

EDIT: 0.3 has been released, see [this post]("http://ubuntuforums.org/showpost.php?p=3578580&postcount=16").

---

### Post by H.E. Pennypacker on 2007-02-26
Looks promising.

---

### Post by matthew on 2007-02-26
This sort of advertising is quite welcome.

---

### Post by Adamant1988 on 2007-02-26
I don't know if bumps are allowed, but I think this thread deserves one.  I like what you're doing!

---

### Post by H.E. Pennypacker on 2007-02-27
I've always been interested in having installers much like those in Windows on Linux, but thinking of .debs, it may not make that much sense.  I may be missing something though.  I still fully support the project.

---

### Post by Adamant1988 on 2007-02-27
I think that any installable package that's free of a package manager needs to include all of it's dependencies, and it needs to only install what's needed instead of replacing a lot of stuff.

---

### Post by Polygon on 2007-02-27
well debs are fine, if your using a certain distro.. I mean ubuntu .debs and debian .debs are not 100% compatable, and if you use a distro that uses RPMs or something else, debs are useless.

It would be really cool if this project in the future could include dependencies for programs, and maybe even add a entry into synaptic or whatever package manager being used on the system. That would simply be awesome.

---

### Post by Adamant1988 on 2007-02-27
> **Polygon said:**
> well debs are fine, if your using a certain distro.. I mean ubuntu .debs and debian .debs are not 100% compatable, and if you use a distro that uses RPMs or something else, debs are useless.

It would be really cool if this project in the future could include dependencies for programs, and maybe even add a entry into synaptic or whatever package manager being used on the system. That would simply be awesome.

Yeah, a smart installer that can learn what it's dealing with and adjust it's installs accordingly would be amazing.

---

### Post by -Rick- on 2007-02-28
I'm still thinking about dependencies. Basicly there are 2 ways (as mentioned already):

1) Include all or atleast uncommon libraries
2) Work with the local package manager

The good thing about nr 1 is that it will likely work on the user's system and is less work than nr 2. The bad thing is that it can make the install package much bigger and few dependencies cannot be included originating from another system.

Number 2 doesn't add up size but requires lots of work since;
[LIST]
[*]code has to be written for every package manager,
[*]maintainence because internals of the package manager may change,
[*]maintainence because dependent packages may be removed or renamed from the package repository.
[/LIST]

Ofcourse combinations or less featured possibilities are possible;
[LIST][*]Download dependencies. Drawback is the need of a internet connection.[*]Check for dependencies but instead of doing all the magic to install them ask the user to do so.
[/LIST]

As for 'making an entry in synaptic', this basicly means that the installer has to make a .deb file and install it. This is obviously good for upgrading and uninstalling, but also requires a lot of work and maintainence.

I'm thinking about starting with "Check for dependencies but instead of doing all the magic to install them ask the user to do so." and when that works make some sort of plugin system so that dependencies can, or atleast tried to, be installed via the local package manager. This system may be later extended to creating packages for the local package manager.

Ofcourse any suggestions are welcome :KS

---

### Post by Adamant1988 on 2007-02-28
I just hope it will work cross distribution, yet with a single interface.  This could be a big deal, you should definitely make as much noise about it as possible... Digg anyone?

---

### Post by red_Marvin on 2007-03-01
This is a welcome project for sure! :)

Som thoughts on the needs of package manager integeration:
- Even if you include all dependencies, and then install only those who aren't already installed, you'd need to communicate with the local package manager to tell it which files were installed, since elsewise when you, with the package manager, install program xyz which has the same dependencies as the installed program, some packages will be added/overwritten. (Since the package manager wasn't told they were already there.) No harm there, if you're not unlucky. But problems will arise when you uninstall xyz and clean the dependencies, so that the files are removed (Again since noone told the package manager that there were more programs dependent on them), and then - bang!

The nicest solution I can think of is by having the nixstaller packages include a dependency list for common package managers, or something like that...

---

### Post by -Rick- on 2007-03-01
> **red_Marvin said:**
> This is a welcome project for sure! :)

Som thoughts on the needs of package manager integeration:
- Even if you include all dependencies, and then install only those who aren't already installed, you'd need to communicate with the local package manager to tell it which files were installed, since elsewise when you, with the package manager, install program xyz which has the same dependencies as the installed program, some packages will be added/overwritten. (Since the package manager wasn't told they were already there.) No harm there, if you're not unlucky. But problems will arise when you uninstall xyz and clean the dependencies, so that the files are removed (Again since noone told the package manager that there were more programs dependent on them), and then - bang!

The nicest solution I can think of is by having the nixstaller packages include a dependency list for common package managers, or something like that...
I forgot to mention that the idea was to keep all the dependencies in a seperate directory. This way it doesn't disturbe the package manager as you descibed and updates won't break the package.

---

### Post by maniacmusician on 2007-03-01
The seperate directory thing is a pretty good idea. I think it would be really cool if you started coding for direct communication with the default package manager in the system. For example, apt in Debian based systems. Eventually, this would make for really clean integration, while the seperate directory thing would be a nice safe fallback.

Of course that's a hell of a lot of work :)

I understand the need for different distros to have different package management systems...what I don't understand is why they don't set some better standards for communication  between the package managers? That would make it easier for more than one type of package manager to co-exist on the same system, or make it easier for cross-distro installers like this one to function as well.`

---

### Post by -Rick- on 2007-03-05
> **Adamant1988 said:**
> Digg anyone?

It is now ... ;)
[http://digg.com/software/Nixstaller_0_2_released]("http://digg.com/software/Nixstaller_0_2_released")

---

### Post by bash on 2007-03-05
Or the other crazy extreme would be that you code a package managing system yourself, that can replace the existing ones (like apt) with one unified one, which can still handle the current packages, but since its you developed it, it also has seamless integration with your installer. So something that on the one hand works like apt/synaptic but also works with your installer.

---

### Post by -Rick- on 2007-10-20
Hello all

Just wanted to inform that a new major release has been out today. New features are:
 - A new frontend powered by GTK+2.
 - More Lua scripting functionality, such as tracking widget data, locking a screen and 5 new widgets.
 - A more easy and automated way to create new project directories via a script.
 - Support for OpenBSD 4.1, NetBSD 4.X (tested on RC2) and the latest Solaris 10 (10-4).
 - Several other features such as the user being able to create a directory as root, an updated FLTK frontend, (customizable) logo support, a redesigned ncurses frontend and a way to include additional run time files. The full changelog can be seen [here]("http://nixstaller.berlios.de/manual/0.3/nixstaller_1.html#SEC4").

The attached screenshot shows the new GTK2 frontend. Files (including Vim 7.1 demo) can be downloaded [here]("http://developer.berlios.de/project/showfiles.php?group_id=4863").

The next release is probably focused on package integration (automaticly creating system native packages).

---

### Post by Acglaphotis on 2007-10-20
> **-Rick- said:**
> It is now ... ;)
[http://digg.com/software/Nixstaller_0_2_released]("http://digg.com/software/Nixstaller_0_2_released")

Dude, with that title you aren't gonna get much help from diggers. Use something like:

'Universal installer for linux coming soo?'

Or something that would caught some eyes. Nixstaller 0.2 released it's a little boring AND doesn't give much information for people who don't know the projetc.

---

### Post by bobbocanfly on 2007-10-20
Every go and digg [http://digg.com/linux_unix/Universal_Installer_For_Linux_Coming_Soon](http://digg.com/linux_unix/Universal_Installer_For_Linux_Coming_Soon)

This project is a brilliant idea, hope it really takes off.

---

### Post by Kimm on 2007-10-20
Not to be the bearer of bad news or anything. But this has allredy been done (and is somewhat wide-spread, even has a software management tool (kinda like Synaptic, for uninstalling only)): [http://www.autopackage.org/](http://www.autopackage.org/)

Or am I missing something?

---

### Post by 23meg on 2007-10-20
Just a comment on the name: for some it may fall short of instilling trust (Nix-*staller*).

---

### Post by -Rick- on 2007-10-20
> **Acglaphotis said:**
> Dude, with that title you aren't gonna get much help from diggers. Use something like:

'Universal installer for linux coming soo?'

Or something that would caught some eyes. Nixstaller 0.2 released it's a little boring AND doesn't give much information for people who don't know the projetc.
Maybe, but that was posted a long time ago (see post date).

> 

Not to be the bearer of bad news or anything. But this has allredy been done (and is somewhat wide-spread, even has a software management tool (kinda like Synaptic, for uninstalling only)): [http://www.autopackage.org/](http://www.autopackage.org/)

Or am I missing something?
Autopackage does it's thing in a different way and works AFAIK only on Linux. I'm not sure about it's current state either (main developer left, got a real bunch of critics). Still choice is good, and if both projects have different goals I don't see a problem (it's pretty common in the OS world right?).

Thanks for the comments so far :)

---

### Post by Acglaphotis on 2007-10-20
W00T It's on the front page!

---

### Post by bobbocanfly on 2007-10-20
238 diggs in 11 hours, not bad going for something like this :D.

---

