---
title: "Warcraft 3 Messes up my screenlets"
date: 2009-07-11
forum: Wine
---

### Post by mrblaineng on 2009-07-11
Hey guys so I recently got WINE working :popcorn: and I've been impressed now I don't have to restart my computer back to windows every time I want to play games. So I was trying out warcraft 3 and I didn't really like how it was in windows mode so I added the -opengl in the command. It worked like a charm and was no longer in windows mode, but after I exited the game all my screenlets were stacked on top of each other. I was wondering if anyone else is getting this problem and if there is a fix for this because it's kind of troublesome to drag back all the screenlets into the right spots. Thanks!

---

### Post by khelben1979 on 2009-07-11
As a temporary solution you can always start a second x server where you start your Windows game within Wine,

```
startx -- :2
```
gives you a second x server which you'll find by pressing ```
ctrl + alt + f8
```

Other than that you can always restart your x server after you have quit the game and if your desktop is saved as saving your session, all your windows and the way you have placed them out on the screen should be shown just the way they were before your exited the x server.

---

### Post by renbla on 2009-07-11
Maybe you want to try out playonlinux to play warcraft :)  [http://www.playonlinux.com/en/](http://www.playonlinux.com/en/), instead of playing it from wine directly

---

### Post by mrblaineng on 2009-07-11
I have tried opening a second x server but when I try to run the game it tells me that it couldn't find the drivers or something along those lines.

---

### Post by ackanao on 2009-07-11
Use cogadh's script to run game in it's own X-Server:

[http://gwos.org/doku.php/wine:winestuff#advanced_stuff]("http://gwos.org/doku.php/wine:winestuff#advanced_stuff")

---

### Post by mrblaineng on 2009-07-11
I tried the launcher thing and I got the same error message

Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
E: client-conf-x11.c: XOpenDisplay() failed
E: client-conf-x11.c: XOpenDisplay() failed
E: client-conf-x11.c: XOpenDisplay() failed

---

### Post by ackanao on 2009-07-11
It looks like you need to configure your X-Server properly - for Nvidia graphic cards type **sudo nvidia-settings** and save changes you made to xorg.conf. Don't know for Ati or other graphic cards.

---

### Post by mrblaineng on 2009-07-11
I typed sudo nvida-settings into my terminal and the settings came up but I have no idea what to do next. I have a 8600GTS Nvidia Graphics card.

---

### Post by ackanao on 2009-07-11
When you're done configuring your graphic adapter goto "**X Server Display Configuration**" and click on "**Save to X Configuration File**"; Check "**Merge with existing file**" option and click on "**Save**"

There's an important note in "Advanced Stuff" section:

> 
NOTE - You can avoid having to modify the script by editing the Xwrapper.config file to allow normal users X access. Open the /etc/X11/Xwrapper.config file in a text editor using sudo, then change the &#8220;allowed_users=console&#8221; entry to &#8220;allowed_users=anybody&#8221;.


---

### Post by mrblaineng on 2009-07-12
I saved with the check mark on the "Merge with exisiting file" option and I also changed the Xwrapper.config file to allow anybody but I still seem to get the same error message.

---

### Post by khelben1979 on 2009-07-12
What happens if you do it the other way around. Running your wine games on the first x server and then doing other things on the second x server?

---

### Post by Freezing on 2009-07-12
What should i change here then i dont get it 
Btw am having Ati Radeon 9200SE family edition.

Copy the text below and paste it into the terminal with either the middle mouse button or by clicking on Edit&#8594;Paste. Take out the nVidia settings portion if you don't have an nVidia card and modify the application paths to match your game.

#!/bin/sh
#uncomment if launching from console session
#sudo /etc/init.d/gdm stop
#KDE use this instead
#sudo /etc/init.d/kdm stop

# Launches a new X session on display 3. If you don't have an Nvidia card
# take out the "& nvidia-settings --load-config-only" part
X :3 -ac -terminate & nvidia-settings --load-config-only

# Goto game dir (modify as needed)
cd "$HOME/.wine/drive_c/Program Files/Game/Directory/"

# Forces the system to have a break for 2 seconds, X doesn't launch instantly 
sleep 2

# Launches game (modify as needed)
DISPLAY=:3 WINEDEBUG=-all wine "C:/Program Files/Game/Directory/game.exe"

---

### Post by Freezing on 2009-07-12
hey am getting this error 

X: user not authorized to run the X server, aborting.
cd: 12: can't cd to /home/agathodaimon/.wine/drive_c/Program Files/Game/Directory/
sleep: missing operand
Try `sleep --help' for more information.
wine: cannot find 'C:/Program Files/Game/Directory/game.exe'

---

### Post by mrblaineng on 2009-07-13
Alright so when I try to start a new X windows I get this message now.

X: warning; process set to priority 1 instead of requested priority 0.

Fatal server error:
Server is already active for display 0
 If this server is no longer running, remove /tmp/.X0-lock
 and start again.

---

### Post by mrblaineng on 2009-07-14
I seem to have found the solution to my problem. If anyone else is having this sort of trouble this is what I did.

I went to the registry and changed the display settings there and now the game doesn't mess up my screenlets. Luckily Warcraft 3 has the display settings in the registry.

Anyway thanks for all the help everyone!

---

