---
title: "New applet: Desktop Drawers"
date: 2008-09-03
forum: Ubuntu Dev Link Forum
---

### Post by ratl3 on 2008-09-03
Hello, I have created a gnome panel applet to solve an issue that has bugged me for a while now.  I was wanting to know if anyone else would like to use it or has any input.

It is an extension of the show desktop applet with some added features. It is a drop down menu that includes the ability to show the desktop, show the contents of the desktop, change desktop to a different folder, add a new desktop, and manage current desktops. 

My current drawers drop down looks like this:
[LIST]
[*]Show Desktop
[*]Contents >
[*]-------------
[*]Desktop Drawers
[*]Kids
[*]Temp
[*]Website
[*]----------
[*]Add Desktop
[*]Manage Desktops
[/LIST]

I created this because I noticed that I was using the desktop for the projects I was currently working on.  I needed a way to change the files on the desktop according to the project being worked on and originally would just link the desktop folder to a project folder.  I created this panel applet to automate this process. 

(Update)
NEW IN 0.4:
Addition of multiple new features and bug fixes.  The desktop is now changed using the ~/.config/user-dirs.dirs file instead of symlinking the Desktop dir to the folder.  This fixes Recent Document displays in user programs as well as allowing copy and paste between desktops.  Recent Documents Desktop added to the list.  This allows one to have the recently accessed documents show up on their desktop.  Also, a Preferences window has been added to allow one to customize Drawers to their liking.

I have created a launchpad page and a PPA for this project at:

[https://launchpad.net/desktopdrawers](https://launchpad.net/desktopdrawers)
[https://launchpad.net/~ryanhjefferson/+archive](https://launchpad.net/~ryanhjefferson/+archive)

To add this to the list of apt repositories add the following entry to your /etc/apt/sources.list file:

```
deb http://ppa.launchpad.net/ryanhjefferson/ubuntu hardy main
```

After this has been added to the sources.list file and everything has been updated one can just apt-get install desktopdrawers to install Desktop Drawers. 

Please leave a message if you use Desktop Drawers.

Thanks

---

### Post by mujambee on 2008-09-05
I like the concept. May I have a look at it?

---

### Post by ratl3 on 2008-09-05
I have attached two files that are needed to run Drawers, drawers.py and desktop_drawers.server.txt.  The python file needs to be copied to the /usr/local/bin directory and the desktop_drawers.server.txt needs to be renamed to desktop_drawers.server and copied to the /usr/lib/bonobo/servers/ directory.  One will also need to install some software to run this applet.  The requirements for Drawers are python, wmctrl, and xmacroplay.  All of these are in the ubuntu repositories. If it seems like I am receiving any more interest I will set up a launchpad account with a deb repository for Drawers.  I hope you find this as useful as I do.

---

### Post by ratl3 on 2008-09-05
I should give a warning before anyone uses this applet.  When it is first run it will move your current desktop to the folder ~/.Desktops/Original Desktop and link ~/Desktop to that folder.  One should back up their current Desktop directory just in case something goes wrong.

---

### Post by ratl3 on 2008-09-11
I have created a PPA for this project at:

[https://launchpad.net/~ryanhjefferson/+archive](https://launchpad.net/~ryanhjefferson/+archive)

To add this to the list of apt repositories add the following entry to your /etc/apt/sources.list file:

```
deb http://ppa.launchpad.net/ryanhjefferson/ubuntu hardy main
```

After this has been added to the sources.list file and everything has been updated one can just apt-get install desktopdrawers to install Desktop Drawers. 

In the PPA as of this moment is release 0.3a which includes a default home folder switcher, showing of windows after desktop has been shown, and fixing of a bug where folders that have been switched to can not be selected.

Please leave a message if you use Desktop Drawers.

---

### Post by izm81 on 2008-10-02
Hi, Ryan! I’ve tried out “Desktop Drawers” for a day and it is interesting! Nice little project. :) I’ve filed a few bugs on the project page. ;)

I think it’s a great start! But in general, I think the most compelling use-case is not made clear enough, neither through the UI nor the documentation / description:

[LIST=1]
[*]Install the Desktop Drawers applet on your panel.
[*]Select Manage Desktops to open the ~/.Desktops directory in Nautilus.
[*]In this folder, create folders for different “workspaces,” (”Project 1&#8243;, “Project 2&#8243;, etc)
[*]Then create links to related folders and files in each of these workspaces.
[*]Projects/Workspaces can now be switched between using the applet.
[/LIST]

Although it’s not quite addressing the issues that I wanted to with the “Intelligent Desktop,” (from my [blog]("http://www.stevenbrown.ca/blog/archives/384")) I’m going to continue using Desktop Drawers for a while more, I think. :) Thanks!

---

### Post by zhocchao on 2008-11-17
hi
it's interesting.  What about shortcuts. As I am switching workspaces with crl + alt + left/right i could switch desktops with ctr + alt + up/down.
greetings
z

---

