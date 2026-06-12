---
title: "Age of Mythology Freeze"
date: 2009-03-18
forum: Wine
---

### Post by Xhip on 2009-03-18
Hello!

I'm running Xubuntu here and the following stuff that I'm going to describe happens in any version of Wine.

The game in question is Age of Mythology. I tried the game in Wine and everything works great, aside from some minor graphical strange events. But at a random time the game completely freezes. The mouse will still be usable and the music continues on playing, but the game and anything else is completely frozen. This can happen either when I'm playing or either when I'm in the menus... 

When I'm talking about freezing, it's a complete FREEZE. I mean, Linux hangs completely, I can't do anything! Only solution is unplug my portable from the current source and restart the system...

Anyone can help on this please? Any idea?

Regards!

---

### Post by Xhip on 2009-03-19
bump

---

### Post by Xhip on 2009-03-20
C'mon, no one plays Mythology??

I think this is related with my 3D acceleration in Wine, but I don't know the mecanics of it, I don't know if it is related with 3D acceleration of Linux itself or the 3D acceleration Wine gets from DirectX, don't know how this stuff works... Only thing I know is that I have a Mobility Radeon M6 LY working with default 'radeon' driver and I have enabled 3d acceleration correctly by working on 'xorg.conf'...

No one can help please?

---

### Post by Xhip on 2009-03-22
bump

---

### Post by Altay_H on 2009-05-14
I'm having the same problem in Intrepid Ibex. Age of Mythology will freeze after playing for a little while. However, the entire system doesn't freeze. Switching screens doesn't work, but pressing Ctrl+Alt+F1 will take me to a virtual terminal where I can reboot the computer. In Jaunty Jackalope Age of Mythology won't even run because Ubuntu logs out once the video sequence is over. The video sequence plays correctly in both though.

---

### Post by WolfRage on 2009-10-22
I am trying to bring several players of this game together to come up with a best play unified solution so please post back with any updates you have for getting AOM to play.
 
I know it has been awhile sine you were looking into this issue. But I too am now trying to tackle the issue of getting this game to run and run well. SO I will post agian when I have more luck.
 
What I have found to work so far:
1: Copy pidgen.dll from AOM_D1 to C:/windows/system32/
2: Download MFC42.dll (I believe that is the correct name.) and copy that to C:/windows/system32/
3: Install the game.
4: Install MSMXMLenu.msi from AOM_D2.
5: Install the version 1 to version 1.10 patch.
6: Start the game in safe video mode.
 
Alternatives: I tried installing the game using POL (Play On Linux) but this resulted in a problem with MSMXML not being detected.
So the next plan is to install the game normally but apply the patch using POL by importing the game using the POL Plugin.
I am also thinking about installing Directx off the AOM CD before launching the game, but I am not sure if Directx will even install or if it is used in the WINE enviroment.

---

### Post by Altay_H on 2009-10-22
Back when I first switched to Ubuntu and installed Age of Mythology using whatever version was the most recent stable everything worked perfectly. The only aspects that differed from Windows were that there was no Online multiplayer, due to the necessity of a cracked executable and that LAN multiplayer would not work across systems.

If you only care about getting Age of Mythology to work, I'd suggest trying Ubuntu 8.04 (Hardy Heron) with whatever version of Wine was stable in the summer of 2008 (I think it was version 0.9.something).

---

### Post by WolfRage on 2009-10-22
Yes but unfortunately I want to play via LAN. I have the atuall install disks, but I am thinking I may have to revert to an older version of Wine to make it work.

---

### Post by Altay_H on 2009-10-22
As long as all the players are using the same operating system you should be able to play LAN games without any problem. Just install Linux on all the computers and LAN multiplayer works. If installing Linux on all the computers is not an option, then you'll need Windows. I don't think there's any way around this currently.

---

### Post by u235sentinel on 2009-10-22
I wonder if playing it in a window would help things here.

I have AOM and haven't tried getting it working yet.

Some games seem to run better when I switch it over to a window.  Something to try at least.

---

### Post by WolfRage on 2009-10-23
I think that the real problem is my setup. One I am using Ubuntu 9.10 which is still beta for a few more days. But I also noticed that my graphics card is not being utilized. It is a older ATI Radeon 9300X.

---

### Post by WolfRage on 2009-10-27
I actually posted in correctly the card is a 9600 xt and the solution wound up being a reversion to 8.04 and using Envy, now Age Of Mythology works most of the time...
 
For any one searching for Information relating to a ATI 9600 XT All-In-Wonder I found that your options are as follows: The current best solution is Envy which is aviable in the Ubuntu repositores, this appplication will match up the propritary drivers with your version of Ubuntu, your Kernel and the x-org-server version. 
The next reall good option is to regress to Ubuntu 8.04 Hardy Herron or 8.10 Intrepid.
Although the regression is not ideal it offered me the best solution when coupled with Envy to support the legacy hardware of my older desktop, with out breaking the system with future updates.
Best pages to help you:
This page will give you help with installing drivers on versions of Ubuntu 8.10 and older.
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) 
This page will tell you how to regress your version of Ubuntu with out reinistalling an older version of Ubuntu.
[http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)
This is the Envy NG home page, which will help to automagicly update your propritary drivers to your system.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

