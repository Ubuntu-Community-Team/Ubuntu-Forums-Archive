---
title: "Workaround for running Xvfb and Ktorrent as a service in Jaunty"
date: 2009-05-11
forum: Server Platforms
---

### Post by Mythbuster1848 on 2009-05-11
Hello Everyone,

These forums have been enormously helpful in my switch from Fedora to Jaunty. To express my gratitude, here's a little "pay it forward":

When I was running Fedora, I ran Xvfb as a service, so I could run Ktorrent headless and interact only with the webUI. Fedora installed Xvfb as a service by default. Jaunty does not. Here's a workaround (it may not be elegant, but it works on Jaunty 9.04):

Instead of playing around with init scripts, you can use the start-stop-daemon command from within the /etc/rc.local script. First make sure rc.local is executible with:

```
sudo chmod +x /etc/rc.local
```Then open rc.local with an appropriate editor (you'll have to sudo it) and add the following lines:

```
start-stop-daemon --start --name xvfb --background --startas /usr/bin/Xvfb -- :100 -ac
start-stop-daemon --start --name ktorrent --background --user [username] --startas /usr/bin/ktorrent --chuid [groupname:username] -- --display :100
```where [username] is the user you configured the ktorrent webUI under. Xvfb might get a bit upset about missing fonts, but it still seems to run for me. I was never able to figure out why xvfb-run doesn't seem to work.

This should get Xvfb running with a virtual display on :100 at startup and then start Ktorrent with [username]'s configuration on the virtual display. You will of course have to enable the webUI plugin for Ktorrent when you have it open as [username] on a real display first. If anyone has a more elegant way to get this functionality working, I'm happy to hear it.

---

### Post by kironnk on 2009-08-05
I am getting the below error while trying to run Xvfb. I also see that /usr/X11R6/lib directory doesn't exist. Can you please help me out.

(WW) Could not open RGB file "/usr/X11R6/lib/X11/rgb.txt"; will use built-in copy.
error opening security policy file /usr/X11R6/lib/X11/xserver/SecurityPolicy
Could not init font path element /usr/X11R6/lib/X11/fonts/misc/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/TTF/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Speedo/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/CID/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/75dpi/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/100dpi/, removing from list!

Fatal server error:
could not open default font 'fixed'

---

### Post by andrevanzuydam on 2009-08-05
It may not be the best solution but installing all the xfonts worked for me

apt-get install xfonts*

---

### Post by chronniff on 2009-11-14
I'm running karmic know, but when I was running jaunty I always used the command:
        DISPLAY=:0 ktorrent
to start ktorrent on a remote server that was actually running gnome, You still had the graphical interface, but you could launch it remotely from ssh without having to forward X, and essentially use the webui to control it.....Well, this may be slightly off topic, but all of a sudden with the release of karmic, this age old command I have been using for years and years and years just decided not to do anything....It doesn't even give me the dignity of throwing an error, its just as if it is executing, except it isn't. and no ktorrent ever launches.....I guess I was just wondering if anyone has any knowledge of why this is, or how to fix it.....I doesn't look to be a bug since I can't find anything about it via google.....I am going to try out the workaround in this thread though thanks for the idea!

---

