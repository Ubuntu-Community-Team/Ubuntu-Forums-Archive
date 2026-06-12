---
title: "What Is Installed On Ubuntu?"
date: 2009-01-23
forum: Ubuntu Brainstorm
---

### Post by arvevans on 2009-01-23
After several years of using Ubuntu-Gnome I have added a plethora of software beyond the basic Ubuntu Installed package.  Fact is that I have lost track of what has been added, and thus might be available for my use.  Pull-down menus don't help resolve this because much of the added software does not automatically appear on menus.  I find myself frequently accessing Synaptic Package Manager just to see what is installed and available.

This brings me to the suggestion that we may need a new "What Is Installed (wii)" software application which shows the name of installed software, along with a short textual description of what each package is used for.

I don't know if this would be part of the Menu Editor, or a stand-alone application.  For one-off locally developed software (I do a lot of shell-script and java-script programming for specific purposes), this new tool would probably need an interface which lets the user add his/her own list of Installed Software and allows editing of the "what it is used for" field.

A starting place might be a scan tool which finds the name of all executable software in any */bin file and builds a database of these executables.  Then the "Purpose" field of the database could be populated by doing a 'man' on each command and extracting only the "NAME" line from that data.

Once such a database were automatically populated it could be reviewed by the user and suitable corrections made to the "Purpose" field.  

A third field in the database might contain the full-path location for each executable.  The fourth field might be the permissions, and the last field might be ownership for each executable.  

Arv - K7HKL

---

### Post by felker2 on 2009-01-23
Run

```
dpkg --get-selections
```

to see what's installed.

---

### Post by Merk42 on 2009-01-23
If you prefer a GUI solution:

Applications > Add / Remove...
Then at the top next to Show: change to "Installed Applications Only"

or

System > Administration > Synaptic Package Manager
Then on the bottom left click "Status", then up above it, "Installed"

---

### Post by arvevans on 2009-01-24
Good suggestions, but those don't find and don't show the other applications that I have added outside of Synaptics Package Manager, and don't find the executables that I have added to /usr/local/bin.  The [dpkg --get-selections] method does not show anything about the applications...just a lists them by name.    Seems what is needed is a "bin-walker" that finds all executable programs and attempts to guess what they might be used for.

In playing a bit with a shell-script to do some of what I wanted, it also became apparent that most methods do not know of and do not find windows applications which have been installed by downloading the .exe programs and then using wine to install them.

On thinking about this a bit more, maybe we need a tool to walk the whole file system looking for executables.  The database populated by such a program could then be shared with Ubuntu developers to show just what programs users are installing, and what they are used for.

Arv
_._

---

### Post by lithorus on 2009-01-24
> **arvevans said:**
> Good suggestions, but those don't find and don't show the other applications that I have added outside of Synaptics Package Manager, and don't find the executables that I have added to /usr/local/bin.  The [dpkg --get-selections] method does not show anything about the applications...just a lists them by name.    Seems what is needed is a "bin-walker" that finds all executable programs and attempts to guess what they might be used for.

In playing a bit with a shell-script to do some of what I wanted, it also became apparent that most methods do not know of and do not find windows applications which have been installed by downloading the .exe programs and then using wine to install them.

On thinking about this a bit more, maybe we need a tool to walk the whole file system looking for executables.  The database populated by such a program could then be shared with Ubuntu developers to show just what programs users are installing, and what they are used for.

Arv
_._

If you have installed things without using .deb's (synaptic/apt-get) you pretty much ignored the reason they are there in the first place. To keep track of what is installed and where. This is why it's very much discouraged to install anything not using .deb's. If you have to install something with a "make install" there is always the program checkinstall which will make a "make install" into a .deb package.

In the case of wine installed programs I don't think there can be any good solution. But maybe you should look at wine-doors ([http://www.wine-doors.org](http://www.wine-doors.org)) which is much like apt in terms of wine programs. There is a .deb package of that btw. :)

---

### Post by Slug71 on 2009-01-24
I would have to agree with the OPs point. Linux just seems very 'messy' and to a newb i think that can be a major drawback and scary.

This is a C/P from a threadi just posted in, in Jaunty Testing and Discussion which i think is also very appropriate for this one.

> For a newb i think the biggest draw back to Linux and could be quite scary is the Filesystem in Places-Computer-Filesystem.
I hate comparing Windows to Linux but i really think Linux needs to 'clean' up a bit like Windows in that area. The amount of folders there can be quite overwhelming for a new user and a lot of them have the same name.

Lets say newb wants to install Google earth or Adobe flash 64bit or anything which only comes as a tar or bin file.
A lot of them you cannot download to the desktop and extract and install from there or else you end up with a folder on your desktop which you cant move.
They can be moved but now newb has to go search how to. Then when he figures out how to move it he now needs to go through those folders to find out where.
Just too complicated and unnecessary IMO.

---

### Post by lithorus on 2009-01-24
> **Slug71 said:**
> I would have to agree with the OPs point. Linux just seems very 'messy' and to a newb i think that can be a major drawback and scary.

This is a C/P from a threadi just posted in, in Jaunty Testing and Discussion which i think is also very appropriate for this one.

I agree with you that it can be a little confusing to new users that you cannot just download X program and install. But we also have to be careful not copying Windows on that regard. Rather I would suggest that there is set up a system to wrap binary .tar.gz installs much like checkinstall does for "make installs". For instance it could put things in an "Applications" folder in the users directory, do "ldd" checks if the system is missing packages and perhaps help install those.

IMHO it's much better to sort/fix things at install time rather than try and sort/fix them afterwards.

---

### Post by Slug71 on 2009-01-24
> **lithorus said:**
> I agree with you that it can be a little confusing to new users that you cannot just download X program and install. But we also have to be careful not copying Windows on that regard. Rather I would suggest that there is set up a system to wrap binary .tar.gz installs much like checkinstall does for "make installs". For instance it could put things in an "Applications" folder in the users directory, do "ldd" checks if the system is missing packages and perhaps help install those.

IMHO it's much better to sort/fix things at install time rather than try and sort/fix them afterwards.

While i do agree with you and it could be a good approach i still think something needs to be done about all those folders. 
Like i said, I would hate to copy Windows or for that matter take the usability of Linux away from Linux vets but im sure something can be done to achieve both.

The way i see it is, there is a much higher percentage of computer users that just want the thing to work than for a lot of us that dont mind tweaking or breaking stuff.
They just dont have the time or interest to mess around learning or tweaking with a new OS which can almost seem like learning to use a computer all over again.

You dont want a complete noob or someone that hates Microsoft or Apple for whatever reason to feel that they want to stick with Linux to prove a point or because they dont want to give those companies any of their money again and just for those reasons alone. No enjoyment benefits.

They should want to do it for those reasons and the security benefits of using Linux but then once they use it be like 'wow, i cant believe i never did this sooner'.

So you want that but also keep the usability there for the more advanced users.

---

### Post by arvevans on 2009-01-25
Part of the problem is that some of the .deb installables don't adhere to standards for where things should be installed, and some don't include hooks for adding themselves to the menu system ("which menu system" is part of the problem here).

Also, being primarily a script-language programmer, I have written numerous special application programs which I use for my own work (and have installed similiar purpose-built scripts written by others).  After 20+ years of doing this, it would be nice if I could track which of these I have installed on my Ubuntu Linux system, and where they are installed.  Guess this makes my idea a selfish one because it was intended to resolve my own view of what is needed, but I suspect than many others have similar situations.

Windows does have a similar problem in that some software installs in weird places and some does not automatically add itself to menu lists.  I'm not saying that we should emulate windows...just that we need to know where things are installed, and what things are installed inside our Linux OS computing platforms.

This is not a complaint about Linux or Ubuntu.  It is just a suggestion for making it a bit friendlier and possibly easier for newbies and experts alike to make more effective use of their computers.

Arv
_._

---

### Post by lithorus on 2009-01-26
The problem with a script that searches the system for executables is just that it won't show the status of the programs and I don't even think that you can rely on a filename for identifying the program. It won't show the version of the program either. However these are things that a package manager does, and will also avoid programs from conflicting with eachother. Which is why it should always be encouraged to use the package manager to install things and not make programs to accommodate when installed without using a package manager.

A good example is Envy.

It started out as alot of scripts which needed to be tweaked for each release and would almost certainly break upon upgrade of Ubuntu. Although it was necessary because the nvidia packages at that time were not always the latest and did not support the latest cards etc. Then the project evolved and got to use the package manager properly (and through dkms) and in the end got integrated into Ubuntu itself and therefor got more or less obsolete.

My point is that this was a project which started out as being a script/program outside the package manager, but to not break the system upon upgrade it had to become part of the package system. This is something which should always be encouraged. If you have problems making .deb packages the solution would be to make it easier for people to make .deb packages and not for making it easier for people to work around them.

> While i do agree with you and it could be a good approach i still think something needs to be done about all those folders.
Like i said, I would hate to copy Windows or for that matter take the usability of Linux away from Linux vets but im sure something can be done to achieve both.
What do you mean by "All those folders"? Do you mean the folders in "/"? Preferably the normal user should not have to browse through the "Filesystem" item at any time. Also it's not something that can just be changed.

---

### Post by Slug71 on 2009-01-26
> **lithorus said:**
> 
What do you mean by "All those folders"? Do you mean the folders in "/"? Preferably the normal user should not have to browse through the "Filesystem" item at any time. Also it's not something that can just be changed.


Yeh the folders in. /- Filebrowser.

No it isnt something that can just be changed but i think it does need to be addressed.
Linux is becoming ever more popular now and like i said, some people dont want to spend time looking for how-to's etc and spend lots of time on it simply because they dont have the time or interest to do so.

Take adobe 64bit flash which i installed yesterday. It only comes in a tar.gz.
A newb or MS/Apple hater switches to Linux for whatever reason, they dont know any codes, they have an app which they need installed. They look in there. Now they are completely lost.

Or some apps which need to be downloaded then made executable. They do this on their desktop because they dont know where else to put it.
Install it and then end up with a folder/file that cannot be moved on their desktop.(It can but they dont know this)

---

### Post by smartboyathome on 2009-01-26
> **Slug71 said:**
> Take adobe 64bit flash which i installed yesterday. It only comes in a tar.gz.
A newb or MS/Apple hater switches to Linux for whatever reason, they dont know any codes, they have an app which they need installed. They look in there. Now they are completely lost.

Not Ubuntu's fault, it is Adobe because they chose not to release it as open source and didn't package it for Ubuntu like its 32bit counterpart.

> **Slug71 said:**
> Or some apps which need to be downloaded then made executable. They do this on their desktop because they dont know where else to put it.
Install it and then end up with a folder/file that cannot be moved on their desktop.(It can but they dont know this)

Well, shall Ubuntu start searching Launchpad then? I think that could solve many of these compiling issues.

---

### Post by Slug71 on 2009-01-26
Im not saying its anybody's fault.

Adobe was just a example. There are plenty of apps out there that are only available as a bin or a tar.gz.

All im saying is that things can be made a little easier by having a dedicated folder where all installed apps go.

---

### Post by lithorus on 2009-01-27
First of all the 64-bit flash is still in alpha stage so people messing around with it should know a little about their system or two. If if was released for Windows it would probably be in a zip file and the user would be in the exact same position. Also the mentioned .tgz file still doesn't have much to do with '/' at all. People can install firefox plugins in their home folder.

Anyway Adobe does release their release versions as .deb packages.

Sorry, but it was a bad example :)

> Or some apps which need to be downloaded then made executable. They do this on their desktop because they dont know where else to put it.
Install it and then end up with a folder/file that cannot be moved on their desktop.(It can but they dont know this)
Then people should 'package' it in a .tgz file which can retain these kind of information. Preferably they should package it in a .deb package like I've always said. I think the exact same thing happens in Windows/OSX when people download an .exe/.app file with no installer. Is it also Windows/OSX to blame there?

---

### Post by Slug71 on 2009-01-27
> **lithorus said:**
> First of all the 64-bit flash is still in alpha stage so people messing around with it should know a little about their system or two. If if was released for Windows it would probably be in a zip file and the user would be in the exact same position. Also the mentioned .tgz file still doesn't have much to do with '/' at all. People can install firefox plugins in their home folder.

No they wouldnt be.
You can choose the destination during install on windows via the installer GUI after extraction. Program Files being default.

Yes you can install it in the home folder but its hidden.

The 64bit is not a bad example.
How about Google Earth then?

> **lithorus said:**
> Then people should 'package' it in a .tgz file which can retain these kind of information. Preferably they should package it in a .deb package like I've always said. I think the exact same thing happens in Windows/OSX when people download an .exe/.app file with no installer. Is it also Windows/OSX to blame there?

Well sadly not everything is packaged in a .deb package. More and more are though.
How many .exe's are there with no installer today?

---

### Post by lithorus on 2009-01-27
> **Slug71 said:**
> No they wouldnt be.
You can choose the destination during install on windows via the installer GUI after extraction. Program Files being default.

Yes you can install it in the home folder but its hidden.

The 64bit is not a bad example.
How about Google Earth then?



Well sadly not everything is packaged in a .deb package. More and more are though.
How many .exe's are there with no installer today?

AFAIK there is no 64-bit flash for Windows at the moment. So you cannot really compare the alpha version for linux with the release version of Windows. The release version of 64-bit flash for Linux will ofcourse come as a .deb package.

Google earth comes with an installer which put it in /opt and makes a symlink to your home folders bin directory. To execute it I have to right click the installer file and select "Allow executing file as program" under permission. Don't have to know anything about where to put files. Again this could have been avoided if they had packaged it inside a .tgz file.

---

