---
title: "Wine crashing when I log into WoW?"
date: 2010-06-04
forum: Wine
---

### Post by bwisdom on 2010-06-04
Ok so I recently figured out why my 3d wasnt working (had something to do with my fix so I could dual monitor, but I found another fix that keeps my 3d working). Now I can log into wow and all that good stuff, but as soon as I log in there is a program error and I have to force quit wow. I must note that both the log in screen and character selection screen are choppy but I can login and use them.

I am victim of the dreaded Intel 8280 chipset and my graphics card is ATI Inc M71 [Mobility Radeon X2100]. Also, here is a screenshot of the error and why i think it is wine. I went to the appdb place but couldnt find anything on the error.

[http://img97.imageshack.us/img97/6441/screenshot1dv.png]("http://img97.imageshack.us/img97/6441/screenshot1dv.png")

---

### Post by asdfoo on 2010-06-04
terminal output?

[http://wiki.winehq.org/FAQ#get_log](http://wiki.winehq.org/FAQ#get_log)

---

### Post by pedro_orange on 2010-06-04
While also supplying the log / terminal information.
Please check the WoW on Ubuntu wiki page and ensure you have a similar WoW config file.
Finally please check that you have turned down desktop effects in the GNOME session, as this uses some graphics resources.

---

### Post by bwisdom on 2010-06-04
Ok so here is the error log: [http://www.filefront.com/16647061/wowerrlog]("http://www.filefront.com/16647061/wowerrlog") If you would rather have me just post the whole thing in this forum I can do that, I just did it this way cause it was kinda long

As far as the config goes. I had it working before I upgraded to 10.04, but I did check it again just to make sure. What is interesting is if I remove the "SET gxApi "OpenGL"" line from my config file it works great, but I dont have any character models I just see the glows from enchants and gear.

---

### Post by pedro_orange on 2010-06-04
You can use pastebin to post massive outputs from the terminal.

From your output I can't actually see what is going on. Could you please post the whole thing from your "wine /path/to/wow.exe -opengl -nosound" line?

I used to run it with the flags -opengl and -nosound cause I found pulseaudio never really worked with anything in wine and caused silly problems. Also killing pulseaudio is usually a good idea with wine applications.
You should be able to run it in OpenGL mode if you used to.

---

### Post by bwisdom on 2010-06-04
Ill try that when I can get back to it and Ill use pastebin this time. It probably wont be until tomorrow morning until I can get to it though.

---

### Post by bwisdom on 2010-06-05
Ok so this is what I got, about line 58, 59 is where the error box popped up:

[http://pastebin.com/k7d2ErQP]("http://pastebin.com/k7d2ErQP")

Ive done a little looking around and its not looking too great, but maybe yall find better news.

---

### Post by david.burlingame on 2010-06-05
I am having a similar error which I believe is related to the follow lines from the terminal:
System information:
Radeon Mobility x1400  - using the working open-source driver
Ubuntu 9.10 Karmic
Wine1.2
No library overrides
Registry added: 
  HKEY_CURRENT_USER >Software >Wine > Opengl
       Key> DisabledExtensions - value GL_ARB_vertex_buffer_object

56. failed to open C:/Program Files/World of Warcraft/Data/Interface/Icons
57. failed to open C:/Program Files/World of Warcraft/Interface/Icons


I'm not sure if this is something which failed on install or perhaps was "not" applied with a patch.  I examined an older drive which had WoW 3.2.x installed on it.  There was no "Icons" directory in either location.  A search on both installations reveals no such directory or file.  

Q:  Does anyone with a working 3.3.3 install have these directories?  
Q  part 2: if so - how were they created?


On a different thread from wineHQ there was a post from another user with this issue.  His solution was to add a registry entry for the video device and type.  There was no registry location or syntax listed on that thread.

[http://bugs.winehq.org/show_bug.cgi?id=22854](http://bugs.winehq.org/show_bug.cgi?id=22854)

---

### Post by pedro_orange on 2010-06-06
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154)

A guy on here had the same problem. Disabling / uninstalling pulseaudio seemed to sort it. Did you try this as I suggested earlier? :)

> Q: Does anyone with a working 3.3.3 install have these directories?
Q part 2: if so - how were they created?

No they do not exist

---

### Post by bwisdom on 2010-06-06
Yea, if ya look at the pastebin the command I used to start wow included the -nosound tag. It still came up with the same problem.

---

### Post by asdfoo on 2010-06-06
does anything change if you cd to the install directory before running it?

---

### Post by bwisdom on 2010-06-07
Hey, cd'ing to the directory didnt change anything. Still the same error. It is interesting though, I did some fiddling and I got it to work. What I did was get rid of the SET gxApi "opengl" line and it works, kinda now. It doesnt crash. I do have a slight issue though:

[http://img180.imageshack.us/img180/5986/screenshoteo.png]("http://img180.imageshack.us/img180/5986/screenshoteo.png")

Neither one of those is me (I think I ended up under the Tauren when I took this pic, lol), but all other players have no textures except their shoulders/helm/weapons. All the NPCs and me have all of our textures. Its kinda strange to say the least, lol.

EDIT: I felt like I should edit this in. In its current state, the game is just about unplayable. If anything starts to happen around you you start lagging. That could just be a problem with my chipset/video card or it could be my wine config. I will have to do further tweaking to make it work.

---

### Post by Darasen on 2010-06-08
I had the exact same issue , I use ATI video as well, and was able to resolve it with the help of wow wiki. 

[http://www.wowwiki.com/Wine_troubleshooting](http://www.wowwiki.com/Wine_troubleshooting)

I installed winetricks and updated the library as indicated in the guide then edited the xorg config file as also indicated. After that I have been able to play using the FGLRX drivers. 

I hope this information helps.

---

### Post by pedro_orange on 2010-06-08
> **bwisdom said:**
> Yea, if ya look at the pastebin the command I used to start wow included the -nosound tag. It still came up with the same problem.

Try killing the pulseaudio process before starting wine. This is not the same as just telling WoW to not use sound, as wine will still try to.

---

