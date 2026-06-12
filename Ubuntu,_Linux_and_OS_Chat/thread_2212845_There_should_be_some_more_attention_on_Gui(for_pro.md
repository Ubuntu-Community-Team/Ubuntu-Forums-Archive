---
title: "There should be some more attention on Gui(for programs and games that are out of ub)"
date: 2014-03-23
forum: Ubuntu, Linux and OS Chat
---

### Post by Cerberus90 on 2014-03-23
For example, you want to install some game. And you download it on official site, and they get game in run file... Here should be by default some ubuntu program to install/uninstalll, it without terminal (coz not all linux users are Unix geeks)... Or even better there should be question when Ubuntu is Installed, of two VERSION of OS. One for advanced terminal users, and other for GUI users only with some basic terminal possible commands, like just run game from terminal for check of errors etc ... 
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
I will be honest, i am sick of using terminal... i want Gui program by default for Uninstall/install programs, like Ubuntu soft.Centre does do, and even better, coz for example i am unistall Wine with USC and still have Notepad avaible from Nautilus...

---

### Post by deadflowr on 2014-03-23
Wouldn't it be better to get those game/whatever developers to make debian packages(which are easily installable through the software center, et al), than to force Ubuntu/debian to comform to those developers ways?

Also, how would you run notepad without something like wine?
notepad is a windows app, not a linux app.

---

### Post by Cerberus90 on 2014-03-23
Installed wine in USF, uninstalled same way and nautilus still have (right click/open with) nautilus, but nothing happens coz wine is uninstalled... thats how great USC are for managing programs... It left program leftovers, and now you will tell me to use some terminal commands, thats what i talking about. Btw Ubuntu Tweak is good app but do not remove notepad ... I think that synaptic manager is better coz it have remo and remove all, something like that options... but is not default by ubuntu...

---

### Post by deadflowr on 2014-03-23
Unfortunately, for better or worse, Ubuntu's package manager doesn't like touching configuration files and other stuff inside the home folder.
So the apps for wine are still there.
Open nautilus press ctrl +h, or menu > view > show hidden files and folders, look for the .wine folder.
Notepad should be in here.
Or simply delete the wine folder entirely.

Does that make sense.

---

### Post by buzzingrobot on 2014-03-23
You can download Windows software from most any random site and click to install because its developers built that package to conform to the Windows installation standards created by Microsoft.  Those standards are enforced by the obvious desire of developers to be sure their products install on Windows.

You can download Ubuntu software and click to install it if those developers have followed Ubuntu standards. Ubuntu, however, also provides the convenience of collecting thousands and thousands of these packages for easy point-and-click installation, and avoidance of dubious software from untrustworthy sites.

In both cases, the ability to point and click to install software did not happen by accident.

If you want a Windows program installed in Ubuntu, then its developers need to make a version for Ubuntu.

---

### Post by slooksterpsv on 2014-03-23
It's not that hard to package apps either. My app I've made, comes in a nice neat DEB package, any files it uses are created in /tmp so they're removed whenever the system is rebooted. You need to contact the developer regarding this issue and ask them for a debian package. If it's more the CLI utilities that you want in GUI form, what ones? I could see if there is a GUI version or make a quick GUI version.

---

### Post by Cerberus90 on 2014-03-23
> **deadflowr said:**
> Unfortunately, for better or worse, Ubuntu's package manager doesn't like touching configuration files and other stuff inside the home folder.
So the apps for wine are still there.
Open nautilus press ctrl +h, or menu > view > show hidden files and folders, look for the .wine folder.
Notepad should be in here.
Or simply delete the wine folder entirely.

Does that make sense.

I was done manual delete after removed it from USC, AND UBU.TWEA... a month ago and here it is still here...
@[**[COLOR=#000000]buzzingrobot[/COLOR]**]("http://ubuntuforums.org/member.php?u=1488460"), [**[COLOR=#000000]slooksterpsv[/COLOR]**]("http://ubuntuforums.org/member.php?u=38762") 
                        Yea, i could but like they would make my wishes come true, maybe if we all ask in some form, forum etc... Anyway thx for     respond !
Btw, [http://www.playdeb.net](http://www.playdeb.net) do packing in deb, and thats great thing... Do they break licence etc if they packed closed source games ... ?

---

### Post by deadflowr on 2014-03-23
> **Cerberus90 said:**
> 
Btw, [http://www.playdeb.net](http://www.playdeb.net) do packing in deb, and thats great thing... Do they break licence etc if they packed closed source games ... ?

That would depend on the terms of the license.
Unlike open source licenses like gpl, there is no across the board license for closed source apps.
To each his own, in that regard.

---

### Post by buzzingrobot on 2014-03-23
> **Cerberus90 said:**
> I was done manual delete after removed it from USC, AND UBU.TWEA... a month ago and here it is still here...
@[**[COLOR=#000000]buzzingrobot[/COLOR]**]("http://ubuntuforums.org/member.php?u=1488460"), [**[COLOR=#000000]slooksterpsv[/COLOR]**]("http://ubuntuforums.org/member.php?u=38762") 
                        Yea, i could but like they would make my wishes come true, maybe if we all ask in some form, forum etc... Anyway thx for     respond !
Btw, [http://www.playdeb.net](http://www.playdeb.net) do packing in deb, and thats great thing... Do they break licence etc if they packed closed source games ... ?

Removing a file or a folder is an either-or proposition:  Either you removed it correctly or you didn't. I.e., if you tried to remove the .wine folder but it is still there, then you did not correctly remove the .wine folder.

Most Windows developers create software to *sell*.  Pleading with them on forums, etc. (which they are unlikely to even read) is not going to convince any of them to start writing software for Linux. For better or worse, it seems to be widely believed that the cost of porting a Windows application or game to Linux would exceed any profit derived from selling it. If they could make more money writing for Linux, why wouldn't they already be doing that?

When you use Linux, you need to put aside some of the habits you acquired with Windows.  That includes downloading random software from random sites.  That only works in Windows due to Windows' dominance. (Who would deliberately create Windows software that cannot install in Windows?) Besdies, you would not download an OS X or Linux package and expect to install it on Windows.


In Linux, you should confine your software choices to those packages available in your distribution's repositories, or, with care, to packages on other sites that are explicitly prepared to install in youor distribution.

---

### Post by mastablasta on 2014-03-24
and furthermore there are many better ediotrs availabel in Ubuntu why would you use notepad?!? :-O avoid Widnows porgrams if possible - there are os many good linux alternatives. open source or even closed source. i mean just for text editing you have excelent gedit and kate for GUI,  nano and vim for CLI. then there is more such as sublime text (i think this one is closed source), or oyu can use an IDE such as Geany or KDevelop for even more more advanced editing and development... soem programes have a lot of choices and a lot better alternatives. some have poorer alternative and some have none. only for those with no or insuficient alternatives use wine or virtualbox. otherwise use native applicaitons.

Computer janitor is a GUI clean up tool. use with care!

---

### Post by monkeybrain20122 on 2014-03-24
> **Cerberus90 said:**
> For example, you want to install some game. And you download it on official site, and they get game in run file... Here should be by default some ubuntu program to install/uninstalll, it without terminal ..

A .run file in this case is just an install script. You can usually run it by just clicking, without the terminal. 

But you need to do two things first 1) right click the .run file, choose Properties > Permission and check the box "allow to be excuted.." (Geeks would tell you to fire up the terminal and chmod+x path/to/file :)) 2) Open Nautilus, go to Files > Preferences > Behaviour and choose "Ask each time" for Executable text files (the default of display is stupid, many gnome defaults don't make any sense :)) 'Files" is on left corner of the top panel when Nautilus is open. You only have to do 2) once after you set up Ubuntu, but you have to do 1) for every .run file (in case this is not obvious enough :))

Then when you click the .run file a window would pop up asking you if you want to run or display it, just click run.

---

### Post by monkeybrain20122 on 2014-03-24
> **mastablasta said:**
> 
Computer janitor is a GUI clean up tool. use with care!

Use bleachbit instead. The computer janitor is dangerous.

---

### Post by buzzingrobot on 2014-03-25
> **monkeybrain20122 said:**
> A .run file in this case is just an install script. You can usually run it by just clicking, without the terminal. 



The thing to keep in mind when installing via this and similar methods is that the package and all the files it installs will be invisible to the system that handles updating and automatic dependency resolution.  The user will need to rely on the vendor to provide updates and security fixes, and the user will be responsible for instaling them correctly. Even if, for example, there is a severe security issue in an Ubuntu library that Ubuntu patches via an update, if a "foreign" application has installed an identical duplicate library for its own use -- as is often done in Windows -- that library will not be patched by Ubuntu's update.

---

### Post by monkeybrain20122 on 2014-03-25
> **buzzingrobot said:**
> The thing to keep in mind when installing via this and similar methods is that the package and all the files it installs will be invisible to the system that handles updating and automatic dependency resolution.  The user will need to rely on the vendor to provide updates and security fixes, and the user will be responsible for instaling them correctly. Even if, for example, there is a severe security issue in an Ubuntu library that Ubuntu patches via an update, if a "foreign" application has installed an identical duplicate library for its own use -- as is often done in Windows -- that library will not be patched by Ubuntu's update.

That's is true. That's why I only install such programs in my home and symlink to /usr/local or /opt when needed.

---

### Post by cariboo on 2014-03-26
For removing packages completely, including configuration files, I use synaptic package manager, it's available in the repositories. One other thing to make sure of, is to check if the program/package is running, as some parts won't be removed if it is.

---

