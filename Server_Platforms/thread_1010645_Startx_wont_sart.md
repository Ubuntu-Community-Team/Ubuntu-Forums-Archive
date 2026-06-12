---
title: "Startx wont sart"
date: 2008-12-14
forum: Server Platforms
---

### Post by wlraider70 on 2008-12-14
I just installed ubuntu server form an install disk.
As far as i can tell the GUI isn't loaded.
Ive tried "startx" and i get a message about the package being refereed to as x11-common. ??

There was some wierdness when i installed from the CD is it possible that the GUI didnt install or that it was not on the CD.

I've tried the apt-get but im not online yet, i have a wireless card.

So im looking for any of the following.

1. what other commands minght start the GUI
2. how can I install off the CD if it didn't already?
3. how can i download a GUI.


please be keystroke specific with commands i'm now at the command line.

---

### Post by dantrevino on 2008-12-14
The server install does not install a gui.  If you want to add a gui to your server install, make sure your repositories are updated, and

```
sudo apt-get install ubuntu-desktop
```or 

```
sudo apt-get install kubuntu-desktop
```whichever you prefer.

---

### Post by wlraider70 on 2008-12-14
how exactly would i Update my repositories ?

I'm assuming I will have to be connected to the internet, if i plug in an Ethernet will I have to configure or is it automatic?

---

### Post by gTinker on 2008-12-14
wlraider70,

Judging by the title of your post and your comments, it seems that you didn't really want the "server" edition, as poster dantrevino mentioned, the server edition doesn't install a GUI. Servers are meant to be configured at the command line, don't need X.

If you have trouble using the command line and don't understand the commands posters are giving you to add the GUI stuff that you want, it might be easier for you to download the regular edition which will install a GUI for you. However it is your choice, what poster dantrevino wrote out for you would get you the GUI but if you aren't comfortable with the commands, it will probably take quite a bit of time and some question-and-answer activity here in the forum to lead you through it. If you had the normal edition that people use, it would be a live CD and you could use it to test Ubuntu on your system before installing.

If you choose to continue from this point, ask specific questions and someone will try to help. Do not expect automagic configuration for a server edition.

---

