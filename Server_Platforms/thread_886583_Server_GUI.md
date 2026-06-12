---
title: "Server GUI ?"
date: 2008-08-11
forum: Server Platforms
---

### Post by skooter1121 on 2008-08-11
I'm brand new to Ubuntu Server. (Although I'm using and familiar with  Ubuntu desktop) Just D/L it and Installed on PC. Found manual area on Web, great.

Is there a graphical interface? So far it's difficult to remember all settings. Too  many slips of paper. Usually take screen shots with GUI.

-Skooter-

---

### Post by pparks1 on 2008-08-11
Create a folder on your network or someplace else accessible.   With a text editor, be sure to write down steps that you take.  If nothing else than for change control type purposes.   It's amazing how often you forget something that you used to know really well simply because you haven't used it in awhile.

As far a GUI goes...my suggestion would be to load something like Webmin ([www.webmin.com](www.webmin.com)).   Gives you a nice admin GUI from a web browser on another machine.

---

### Post by tuxxy on 2008-08-11
If your having trouble setting up from the CLI, you could also just install Hardy as usual and then add all the server packages and remove the uneeded files.  

Atleast this way you will have GNOME from install and the end OS would be just the same as server if you get the right packages.

---

### Post by netztier on 2008-08-11
> **skooter1121 said:**
> 
Is there a graphical interface? So far it's difficult to remember all settings. Too  many slips of paper. Usually take screen shots with GUI.


Aside from the usual (un)recommended option to install the package **ubuntu-desktop** on your server (dragging along a whole lot of unneeded things like Firefox, Network Manager, OpenOffice and the likes), and aside from the other usual suggestion to install some lightweight desktop environment (xubuntu-desktop), the **[Ubuntu Server Guide]("https://help.ubuntu.com/8.04/serverguide/C/index.html")** suggests using **eBox**:

[https://help.ubuntu.com/8.04/serverguide/C/ebox.html](https://help.ubuntu.com/8.04/serverguide/C/ebox.html)

Judging from what it looks, it's probably similar to Webmin as suggested in this thread. 

regards

Marc

---

### Post by skooter1121 on 2008-08-11
Thanx.

I'm D/L the Webmin now. Looks good.

In the DOS dayze I had some TSR's that would load that would allow me to copy / paste text screens with hotkeys. Anything like that available for Ubuntu ?

I guess I could create a small DOS boot partition which could load the TSR, then go to Ubuntu ? Since this server is a new install I have a lot of flexibility. Any recommendations for a boot manager for a partition setup: DOS / Ubuntu Server / Swap ?

-Skooter-

---

### Post by timcredible on 2008-08-11
install gnome or kde, whichever you prefer.  don't listen to anybody that says you should manage a server with cli - there's no reason not to use a window manager.  both are in the repos, so it's easy to install - ```
sudo apt-get update
sudo apt-get install gnome
``` should get you gnome. you can also access gnome or kde remotely and it'll behave exactly as it does when you're on the system locally, check my sig link for a how-to.

---

### Post by pparks1 on 2008-08-11
I don't think anybody here said that you should NOT manage a server with a GUI.   However, by default it doesn't come with a GUI and we are providing some options.

I personally don't choose to have a GUI because it's just more packages to update, more resources consumed and more potential security vulnerabilities.   I prefer to just use a command line for my tasks and webmin for those things that I do or other admins do that are simply not convenient in a CLI.

---

### Post by skooter1121 on 2008-08-11
Thanx all:

Since this is a testing environment I'd like to use a GUI and I am already familiar with gnome. So I'll like to try [COLOR="DarkOrange"]timcredible[/COLOR]'s suggestion.

I've:
sudo apt-get update (OK)
sudo apt-get install gnome
result: Some packages could not be installed. The following packages have unmet dependencies: gnome
E: Broken packages

Next step?

-SKOOTER-

---

### Post by hyper_ch on 2008-08-11
a normal gui won't give you any benefit as it is the same to edit a config file in a gui text editor or cli based one.

webmin can help you but if you have no clue you should start with command line to get the basic understanding on how all those daemons run.

---

### Post by windependence on 2008-08-11
> **skooter1121 said:**
> Thanx.

I'm D/L the Webmin now. Looks good.

In the DOS dayze I had some TSR's that would load that would allow me to copy / paste text screens with hotkeys. Anything like that available for Ubuntu ?

I guess I could create a small DOS boot partition which could load the TSR, then go to Ubuntu ? Since this server is a new install I have a lot of flexibility. Any recommendations for a boot manager for a partition setup: DOS / Ubuntu Server / Swap ?

-Skooter-

If you're worried about cutting and pasting from the terminal, I would suggest not working on your server from the console. Use another PC, can be linux, Windoze or Mac and ssh in to your box. You can also use screen at the terminal console or in an ssh session. There are many tools like this for server admin from the CLI without resorting to a crutch like the GUI. Most servers are remotely managed anyway.

-Tim

---

