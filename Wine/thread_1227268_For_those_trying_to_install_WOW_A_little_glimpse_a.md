---
title: "For those trying to install WOW: A little glimpse at the end result."
date: 2009-07-30
forum: Wine
---

### Post by dslreports_snakeoil on 2009-07-30
Here are two pictures of WOW on my ubuntu build.
The computer is a dual core AMD processor. 2 gigs of ram.
Nvidia 7500GT card.
Ubuntu 9.04 and wine 1.1.26 
The TV is a 42 inch 1080p. The game settings are maxed, and the resolution is 1920 x1080 .
So far, after running this setup for over a week, I have found no major problems. Just a few minor ones, that I think are equipment related, not software [for example wireless keyboard having to  short of a transmit range].

Anyhow, keep working at it, the end result is worth it.

---

### Post by castlefox on 2009-07-30
What is the frame rate difference?  

How did you set it up?

---

### Post by dslreports_snakeoil on 2009-07-30
On my windows box on a wired network I get about 60fps. The windows box has a 9500GT Nvidia card.

The linux box also hits close to 60fps.

I pretty much followed these instructions:
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

But I also looked for newer guides then that.
[http://www.sysadminwiki.net/wiki/index.php?title=How_to_install_and_configure_World_of_Warcraft_in_Ubuntu_9.04](http://www.sysadminwiki.net/wiki/index.php?title=How_to_install_and_configure_World_of_Warcraft_in_Ubuntu_9.04)

[http://forums.wow-europe.com/thread.html?topicId=9446365932&sid=1](http://forums.wow-europe.com/thread.html?topicId=9446365932&sid=1)

The only 3 things to remember is:
It's easier to download the files then try to figure out how to get the WOW install DVD to work. It takes longer, but it is easier.

The config.wtf file is not created until you log into WOW and have a char load on screen [all the way into the game]. I was able to actually move around a bit before the d3d started goofing up.

3] Take your time. If possible run things from terminal, as you'll get feedback when they fail. I had the famous "launcher crash after hitting play button".
All I did because I got tired of waiting for a replay was uninstall and reinstall wine and wow [hence you should copy all the wow files to a back up folder. That way you wont have to dl them again]

---

### Post by Ningamer on 2009-07-31
It took me a few days to install this properly. I had problems with the text, map (which I still haven't resolved) and lag. If you're installing from the cd, you have to enable hidden files/folders, as setup.exe and a lot of other files are hidden.

---

