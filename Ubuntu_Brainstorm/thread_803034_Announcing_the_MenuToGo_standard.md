---
title: "Announcing the MenuToGo standard"
date: 2008-05-21
forum: Ubuntu Brainstorm
---

### Post by andrewluecke on 2008-05-21
Introducing the first Milestone of MenuToGo. 

**Introduction**
Menutogo is a way for developers to add a list of available actions to their archives so that users only need to deal with relevant files. Unlike RPM's or DEB's, it doesn't require files to be packaged in a special way to use, and the MenuToGo menu-file can simply be dropped into repositories. Its not designed as a replacement for proper packaging, but it makes it very easy when no packaging exists. 

If there is enough interest, I will continue with the project and build up a working group for it. I intend to try to get it integrated into Intrepid ipex, and all other distro's & operating systems, as it helps act as the missing link to bridge where packaging systems cant reach. Please let me know what you honestly think guys. If its a crappy idea, I wont pursue it for Ubuntu any longer (I'll try other distributions first). Also, note its not a replacement for DEB's either. Its a supplement. 


An example menu for a source archive may be:
- Read the release notes. 
- Install dependencies via APT (if apt is detected)
- Compile Program
- Compile and Install Program
- Uninstall program

Its more user friendly then seeing: autogen.sh, README, xga.c, xga.h,automake.in,src,makefile,COPYING,includes. Newbies wont know how to compile that program or use it! Menutogo solves that!


**Links**
[- Screenshots (one showing the advantages) are available here.]("http://sourceforge.net/project/screenshots.php?group_id=226716") 
[- Click here for Project Page]("http://sourceforge.net/projects/menutogo/")


[MenuToGo is a prototype of brainstorm idea 7167]("http://brainstorm.ubuntu.com/idea/7167/"). 

Please vote for it on: [http://brainstorm.ubuntu.com/idea/8904](http://brainstorm.ubuntu.com/idea/8904) . 

And of course its open source, cross platform, and uses XML menu files.

---

### Post by smartboyathome on 2008-05-22
Perhaps you can make this into a binary so that it can be run from within the directory of the program; no need to install it. It could have the rules file (for lack of a better name) hidden in the same folder as the binary. I think this may go somewhere. :)

---

### Post by andrewluecke on 2008-05-22
> **smartboyathome said:**
> Perhaps you can make this into a binary so that it can be run from within the directory of the program; no need to install it. It could have the rules file (for lack of a better name) hidden in the same folder as the binary. I think this may go somewhere. :)

Actually, I was thinking that before, and it will happen for Milestone2. But now its been suggested, I'll add it now to the SVN (its a 5 min job, that only requires a few lines of code). 

For now there is a way it can be done anyway easily. You simply include the binary, the menutogo menu file, and create a shellscript that is "./Menutogo menu.menutogo". Done. 



MenuToGo has been also designed in a way, that the options XML file follows EXACTLY the same format as the standard menu XML files.  Anything that you have in the defaults, can be added to, or changed with the programs menutogo file. So this behavior could also be exploited if required for your idea. It was actually one idea I had before, to slowly overtake microsoft's autorun format

---

### Post by andrewluecke on 2008-05-22
Milestone 1.1 (revision 71 on the SVN) has this feature implemented now smartboyathome. I probably wont remake the packages though until I have tested OSX support first. But it can be pulled directly off the SVN. You simply need a file called menu.menutogo in the same directory as the binary, and it will run it

---

### Post by smartboyathome on 2008-05-22
Can you change the menu's name to .menu.menutogo? That way the user doesn't have to be concerned with it. Also, what about making it spit out the commands from the last commands with a log (perhaps named .log.menutogo)? For example, if you run ./configure, you might have a missing dependancy, and thus you would want to look at the output.

---

### Post by CrazyGuy123 on 2008-05-23
Hi,

Nice program.

For acceptance around the Ubuntu community I think you'll find you need to focus on applications where the menu is used for other uses OTHER than direct application installation.  For example, the menutogo link could\should run a script to package an application (without sudo access) and then install the package directly via dpkg with sudo.

There are many other uses of menutogo which don't include application installation, and it would be good to highlight these.

The reason I say this is at the moment installing things from source is only done by developers, and they understand the risks, whereas if large numbers of users start using easy menus to install directly from source, compatibility problems could result (since apt-get won't be able to do dependancy checking), and files could be overwritten.  Application removal is also much less reliable as the uninstall script may not be kept in sync with the install script.

As a lightweight menu I really like it.  Have you considered adding rendering options so the menu can be styled, a bit like [HTA applications]("http://en.wikipedia.org/wiki/HTML_Application"). - I guess that'd be a pretty big code change though, so maybe not worth it.

---

