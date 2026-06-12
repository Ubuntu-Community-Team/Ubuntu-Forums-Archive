---
title: "Package Management Idea..."
date: 2007-11-15
forum: The Cafe
---

### Post by jclmusic on 2007-11-15
could someone with more experience of coding please tell me how easy this would be?:

The install packages would be a series of directories (like deb files) and a text file with instructions to basically copy all those files into the directory. Each install package would also contain a shortcut which would be placed in an "Applications" folder, linking to the program (menus could also possibly be created from this folder). The install packages would also contain all dependencies needed for the program. If the system it was being installed on already had some of the dependencies, these would be automatically ignored, or perhaps automatically overwritten (that would however be a virus risk).

---

### Post by DoctorMO on 2007-11-15
I don't understand what your asking for is a poor version of deb/debian install packages.

---

### Post by igknighted on 2007-11-15
If I understand you right, the point of this is to always a menu entry and to have a single known folder for applications, correct?  If this is indeed what your are suggesting, then you are merely describing almost the exact way it is already.

First, all .deb's should have a .desktop file and set up their own menu entry.  If they don't, they are poorly built packages or the developer got lazy.  Either way, switching to a new design wont change anything, people will still make bad packages or get lazy and not write a .desktop.

Second, there are a couple folders for programs to be installed to.  But this is OK, because it's just like sorting them by their purpose.  There are some oddballs in there of course, but the basics are /bin, /usr/bin, /usr/local/bin, and ~/bin.  /bin is system stuff (often needed for boot... /bin cannot be on a partition other than /).  /usr/bin is for almost all programs.  /usr/local/bin is typcally unused folder, but sometimes apps install here.  ~/bin is in your home directory and exists so you can add your own programs without needing to be root to add them to one of the other folders.

The easiest way to check what folders your system is using for binaries is to use the echo command to look at the variable $PATH (a system variable that defines where to look when you type a command).  Here is mine, for example: [CODE][[dfitzg@localhost ~]$ echo $PATH
/usr/bin:/bin:/usr/local/bin:/usr/X11R6/bin/:/usr/games:/usr/lib/qt3//bin:/home/dfitzg/bin:/usr/lib/qt3//bin
/CODE]
To understand this better, lets say you try to run the command "ls".  This program is located in /bin.  But the computer will check the folders named in $PATH in order, so it will look in /usr/bin first.  When it doesn't find ls, it will check /bin.  Be wary, because if you write or install a program called ls and put it in /usr/bin, it will take precedence over the real ls.  Now lets say you have writen a program called laserprint, which prints a file to your laser printer (idk why, but lets say you did).  You would probably put this in ~/bin.  When you ran this command, the system would check every folder until it got to ~/bin and found it.

The point of this is that the things you (seem) to be asking for are very much already there.  I hope the examples and such I gave are helpful to see how it is working underneath.  If I just babbled stuff at you that you already knew I am very sorry.

---

### Post by jclmusic on 2007-11-15
yes, but what about including all dependencies in the install package instead of seperately? 

and links to the programs in the apps folder, not just the /bin and /usr/bin folders themselves, so that a newbie could open a folder which would be either on the desktop, or linked to from the desktop where they could access shortcuts to all installed applications. could also create a menu from this folder.

---

### Post by igknighted on 2007-11-15
> **jclmusic said:**
> yes, but what about including all dependencies in the install package instead of seperately? 

and links to the programs in the apps folder, not just the /bin and /usr/bin folders themselves, so that a newbie could open a folder which would be either on the desktop, or linked to from the desktop where they could access shortcuts to all installed applications. could also create a menu from this folder.

1) Dependencies cannot be included.  Think about it... what about the dependencies of the dependencies?  And the dependencies of the dependencies of the dependencies?  Your files would be enormous, and most of it wouldn't be needed.

2) Check out this folder: /usr/share/applications.  It holds the .desktop files if the programs were packaged properly.  You can launch apps from here.

---

### Post by DoctorMO on 2007-11-15
> yes, but what about including all dependencies in the install package instead of seperately?

This is the wrong way to go about solving a problem that has been solved.

> and links to the programs in the apps folder, not just the /bin and /usr/bin folders themselves, so that a newbie could open a folder which would be either on the desktop, or linked to from the desktop where they could access shortcuts to all installed applications. could also create a menu from this folder.

Your trying to make the Ubuntu/Debian package system work like MacOSX and/or windows; We're not here to copy their ideas and until you can present a use case currently not covered by the deb package system then there isn't much need to discuss your ideas.

---

### Post by igknighted on 2007-11-15
> **DoctorMO said:**
> This is the wrong way to go about solving a problem that has been solved.



Your trying to make the Ubuntu/Debian package system work like MacOSX and/or windows; We're not here to copy their ideas and until you can present a use case currently not covered by the deb package system then there isn't much need to discuss your ideas.

While I agree that the linux solution is more elegant, and while it's not necessarily easy for new user to get the hang of, there is no need to shoot them down harshly.  He/She is only trying to help, so lets help back so everyone learns.

---

### Post by salsafyren on 2007-11-15
> **DoctorMO said:**
> This is the wrong way to go about solving a problem that has been solved.



Your trying to make the Ubuntu/Debian package system work like MacOSX and/or windows; We're not here to copy their ideas and until you can present a use case currently not covered by the deb package system then there isn't much need to discuss your ideas.

Use case:

Install firefox1, firefox2, firefox3 on the same system using debs.

Is not easily done.

Could easily be done with eg. Zeroinstall. Debs are not the answer for everything.

---

### Post by jclmusic on 2007-11-15
i am not a newbie, and i'm perfectly proficient with deb files. but im thinking of making something for newbies.

salsafyren hits the nail on the head. this is exactly what i plan. that every program will have one install file. i beleive autopackage also does this?

and as for making linux like osx, this is not the case. i am actually thinking of doing something similar to what gobolinux does, where both filesyststems can be used side by side with the use of links (may also include a button to switch between them). but here i am talking specicically about package management.

> This is the wrong way to go about solving a problem that has been solved.

then what is the right way? and solved how?

---

### Post by frup on 2007-11-15
The solution is for distro developers to make sure they have all common dependencies in distros and and for app developers to not stray to much with out need.

---

### Post by Fri13 on 2007-11-19
> **jclmusic said:**
> i am not a newbie, and i'm perfectly proficient with deb files. but im thinking of making something for newbies.

salsafyren hits the nail on the head. this is exactly what i plan. that every program will have one install file. i beleive autopackage also does this?

and as for making linux like osx, this is not the case.


First, it would be prefer to teach these newbies to use package manager. It is not more than select application what they want and package manager will take care of others. There is no need for one package.
If you already has all depencies, it would take more data to be downloaded (+n1) everytime and then throw away data what is not needed or overwrite what you already has.

Problem is that then we would have DLL hell on GNU/Linux. Currently only one maintainer is needed to keep one library or application up to date. If this data is changed, disto package maintainers takes this and repackages it for reposity. So when new application needs new version, developer dont need to include it to own package because he knows it will be found by distro.

There would be big problems by that older application install older library over newer and all newer applications dont work anymore because needed library is older. User should then reinstall applications to get them work.
And MacOSX does this samekind thing but little different way. It still install all files to /usr, /etc and /bin locations, just like all *nix systems. But it just shows user that there is one file. 
Autopackage does this same, but those files are big to install. You first need to install autopackage itself and still, it isnt' so powerfull than current package management.

When you install something trought autopackage, those installed apps cant be updated by distro package management. You just add other (broken) package manager to system what already has one, very powerfull one.
So if application maker wants to have own application be available for every distro, there are help available how to do that. First it needs littlebit time and effort to notify distro developers that there is new application what would be good for distro users. Then allow them to get account to source where they can get it and package it when updates comes. And then, appliction developer only need to focus to own application same way as with autopackage and distro packagers takes care, that application is updated to all distro users when package comes.

One way is too, user makes own reposity (not so nice because we then had hundreds of them) for distro.
Working together is not so hard and after all, everyone can enjoy from easy up-to-date system + apps and install/remove management.
There is never reason to break working system just because we want few new users. 

It's like we should forget user account because new users only wants to use computer and they need to be root because they hate it when they dont have easy access to all files on their machine.

---

