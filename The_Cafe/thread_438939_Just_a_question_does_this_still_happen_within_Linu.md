---
title: "Just a question: does this still happen within Linux?"
date: 2007-05-10
forum: The Cafe
---

### Post by Lucifiel on 2007-05-10
Okay, was talking with someone who had quite a lot of experience with Linux for over 1 year: he spent his time working on different installations and configurations of Linux for IBM.

Anyways, he was telling me that in Linux, there was this issue of GUI and command-line not synching. As in: you enabled an option via the GUI but the changes did not occur. Then, you checked through Terminal or some other command line interface mode and found out that the enabled options were not reflected there. 

So, does this still happen within Linux? Or even Ubuntu?


Just asking. :)

---

### Post by Tomosaur on 2007-05-10
> **Lucifiel said:**
> Okay, was talking with someone who had quite a lot of experience with Linux for over 1 year: he spent his time working on different installations and configurations of Linux for IBM.

Anyways, he was telling me that in Linux, there was this issue of GUI and command-line not synching. As in: you enabled an option via the GUI but the changes did not occur. Then, you checked through Terminal or some other command line interface mode and found out that the enabled options were not reflected there. 

So, does this still happen within Linux? Or even Ubuntu?


Just asking. :)
Can't say I've ever encountered this problem before...

---

### Post by B. Gates on 2007-05-10
...

What? Give us an example, that was WAY too broad.

---

### Post by Lucifiel on 2007-05-10
Oh sorry, here's what he said:

> my experience is that the gui doesn't work very well to change settings
yeah, we would change settings via the gui
and nothing would change
we found the cfg file for that and saw that it had not changed
check the permissions out, and no issue there
changed the settings in the cfg file and things changed

---

### Post by rai4shu2 on 2007-05-10
I only ever see that with VLC. It's damn annoying sometimes.

---

### Post by Tux Aubrey on 2007-05-10
Generally not, as far as I know.

It **HAS** happened to me with some third-party GUIs (yes, I'm looking at you nVidia Settings!)

I'm guessing it has to do with packages installing themselves on menus without the option of running them with administrative privileges (ie as root user).  In the case I'm familiar with, the Nvidia Settings GUI offers to make changes to a file (xorg.cof) that requires root privileges to edit.  It doesn't ask for a password and gives no error messages.  When I check xorg.conf, the changes are not there.  Just a bit of faulty programming I guess.  Its easy enough to make the changes manually, but very confusing if you don't know the issue.

In the case of official packages (those that come with or are endorsed by Ubuntu) I have never had this problem.

---

### Post by Rui Pais on 2007-05-10
> my experience is that the gui doesn't work very well ...
there is not **a** gui, but GUIs for this or that app. 

If a gui don't actualize the config file that are suppose to act upon, thats a GUI bug. 
It has nothing to do with Linux or Ubuntu.

---

### Post by prizrak on 2007-05-10
I think it would have to do with the way GUI is made. If it doesn't properly modify the file and restart the daemon (chances are it needs to be restarted) then it won't work. Not so much a Linux problem as a GUI problem. I've actually encountered that bug in Windows a couple of times.

---

### Post by shavenlunatic on 2007-05-10
> **Tux Aubrey said:**
> Generally not, as far as I know.

It **HAS** happened to me with some third-party GUIs (yes, I'm looking at you nVidia Settings!)

I'm guessing it has to do with packages installing themselves on menus without the option of running them with administrative privileges (ie as root user).  In the case I'm familiar with, the Nvidia Settings GUI offers to make changes to a file (xorg.cof) that requires root privileges to edit.  It doesn't ask for a password and gives no error messages.  When I check xorg.conf, the changes are not there.  Just a bit of faulty programming I guess.  Its easy enough to make the changes manually, but very confusing if you don't know the issue.

In the case of official packages (those that come with or are endorsed by Ubuntu) I have never had this problem.

erm, just edit the launcher to have **gksu** at the beginning, it will prompt for a password on running it, and any changes you make to xorg (aslong as you click apply and ALSO click to save to .conf file!!!) will be saved fine :)

---

### Post by brim4brim on 2007-05-10
I've only had it happen with VLC.  It also happens with VLC in windows though so its just something stupid they did I guess, putting buttons in that don't modify the config file.

---

### Post by tgalati4 on 2007-05-10
You can make changes to your screen resolution and they won't take place until you restart the xserver.  There are perhaps other desktop settings that require an xstart restart otherwise they won't take effect.  You can load modules in the kernel and sometimes (rarely though) a reboot is required for the new module to work properly.  I've experience this with some video and sound modules.  

So if you are running in single user mode and make changes via the command line interface then startx the new settings will take effect.  If you use a gui to make changes and the xserver is not restarted then yes, I can see a situation where it appears that you made the changes but they don't stick.

Some servers, such as Samba, require tweaking of the configuration file to get it to work the way you want.  Using the "Share Folders" gui will give you basic functionality, but if you need more advanced configuration, you need to get into the configuration file and edit it by hand.  This is a case of the gui handling general and simple cases, but the real power in many servers is contained in the configuration files.  As the servers gain in functionality and complexity, often the gui's don't keep up.

Perhaps the story by the OP was a serious issue at the time, but Linux distros are maturing all the time so those observations may be outdated.

I remember Redhat 6.3 being difficult to install.  That is not the case anymore with Live CD's and better hardware detection routines.  Sure there are edge cases with brand new hardware and oddball or non-standards compliant hardware, but overall Linux installs are much easier.  We don't have "Install Fests" anymore because they aren't needed.  Now we can exchange distro CD's and check the forums when something doesn't work.  It's a new world.

---

