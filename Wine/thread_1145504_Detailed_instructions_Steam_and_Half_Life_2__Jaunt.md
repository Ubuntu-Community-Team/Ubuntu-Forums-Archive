---
title: "Detailed instructions: Steam and Half Life 2  Jaunty 9.04"
date: 2009-05-01
forum: Wine
---

### Post by fletchoid on 2009-05-01
Installing Steam with WINE and then Half Life 2 on new 9.04 upgrade

This information is spread out in little bits all over the forums and various other sites.  I thought it might be useful to put it all together, considering the number of posts on this topic.
**What this works with:**  Ubuntu 9.04 64 bit;kernel 2.6.28.11 generic; AMD64X2 6000; ATI 4870 Graphics card; ATI proprietary fglrx driver; WINE 1.0.1 Compiz 3D effects turned OFF with Compiz Fusion Icon. Most sites recommend that you use the newest WINE version.  I was a bit reluctant to mess with the WINE package included in Ubuntu 9.04, so I just used that.  Best to research WINE a bit before you install it.  I won't cover that here.  Also, make sure your graphics drivers are working perfectly before you get into this mess.  I had some initial problems with the upgrade from 8.10.  Don't try any of this until your system is tested and stable.
Once Wine is installed, copy all of the Windows fonts either from your real copy of Windows (in C:/Windows/Fonts/) into your WINE windows directory  (in  ~/.wine/drive_c/windows/fonts/ ) or, alternatively you can download some of the more common ones from the internet.  (eg.  from [http://thepemberton.com/posts/downloads/fonts.7z](http://thepemberton.com/posts/downloads/fonts.7z)  You can install the 7Z unzipping program from Synaptic Package Manager.)  If you don't install Windows fonts into the ** ~/.wine/drive_c/windows/fonts** directory, Steam will have NO TEXT!  I found that the real Windows fonts were better.  You need Tahoma fonts for half life 2.  Its best to have them all for future use.
  
Download and run the SteamInstall.exe file (NOT the SteamInstall.msi that’s on their download page)
From a terminal:  (I am using * as a bullet; don't put that in the terminal)
          *  **cd ~/Desktop**
          *  **wget [http://store.steampowered.com/download/SteamInstall.exe](http://store.steampowered.com/download/SteamInstall.exe)**

or whatever SteamInstall.exe source works. I just googled SteamInstall.exe and downloaded it from somewhere.
Once the file is downloaded, copy it into the **~/.wine/drive_c/windows/system32** folder
Go to the applications menu and select WINE, Browse c:\drive
Go into windows/system32 folder and paste the SteamInstall.exe file there.
In the terminal type:
          *  **cd ~/.wine/drive_c/windows/system32**
          *  [B]wine SteamInstall.exe -dxlevel 81 -novid
[/B]
 I actually just went into the **~/.wine/drive_c/windows/system32** folder and right clicked SteamInstall.exe that I just moved there, and selected  "Open with Wine Windows Program Loader"  So I had to put the -novid and -dxlevel commands into the launcher programs for the games I installed.  For half life 2, I had to set the DirectX level to 81 (dxlevel 81).  Don't worry too much about this.  You can change the DirectX level later in the command that you use to launch Steam.  If you have different programs that need different DirectX levels, you just write them into the launch commands.  The dxlevel in the Steam command should be the same as in the game command or the Steam settings will override the game settings.  More on that later.
           
The Steam installer will guide you through a small install process. Once completed, edit the shortcut (or create one if one wasn’t automatically created for you):

Right-click on Applications menu -> Edit Menus -> Wine -> Programs -> Steam -> Steam, right-click “Steam” and change the properties “command” to ONE of the following command lines:

   *  **wine “C:/Program Files/Steam/steam.exe” -dxlevel 81 -novid -width 1024 -height 768 -heapsize 512000**
 
OR, alternatively:

   *  **env WINEPREFIX="/home/*yourusername*/.wine" wine "C:\Program Files\Valve\Steam\steam.exe" -dxlevel 81 -novid -windowed -width 1024 -height 768 -heapsize 512000**

The first wine line opens Steam on the desktop, and sets DirectX to 81, cancels opening videos, makes the window smaller, and does something to the heapsize, whatever the hell that is.

The Second alternate line does the same, except it opens a WINE window that is separate from your normal desktop.  In my case, I found that this second line was better.  Especially when loading games.  Don't be a bozo like me and leave the *yourusername* in the command and then wonder why it wasn't working.  Duh, oh yeah, change it to the "user name" !! Hyuck!

Notice that the location of Steam is different in the first wine command and the second.  The first one I found in a forum and assumes the Steam.exe is in  C:/Program Files/Steam/steam.exe,  but when I installed Steam, the Steam.exe went to C:\Program Files\Valve\Steam\steam.exe  Check where yours goes, and adjust accordingly.

Now you can run Steam, and use Steam to install any games you already have in your game list, purchase new games online, or install using CDs or DVDs. If you are going to install from disks, research the forums for hints.  It is a bit more complicated.  I just installed games I already own from my Steam account.  Haven't tried installing from disks, or from the Steam store, so I can't help you.

To get Half Life 2 to work I had to edit the command line in the menu (see instructions above) to the following:

  *   [B]env WINEPREFIX="/home/*yourusername*/.wine" wine "C:\Program Files\Valve\Steam\steam.exe" -applaunch 220 -dxlevel 81 -novid -windowed -width 1024 -height 768 -heapsize 512000
[/B]
Notice that it only differs from the one that starts Steam, by having -applaunch 220 in addition to the other commands.  This just loads Steam, and then immediately the game.  I found that half life 2 flickered and had graphics problems, unless I ran it with this launch command.  It runs inside a WINE window, and runs fairly well.  Once again, don't be a bozo and leave "*yourusername*" in the command line instead of your ACTUAL username..... yes,  i  did it twice.... duh!

Enjoy.

---

### Post by asdfoo on 2009-05-01
[http://wiki.winehq.org/FAQ#head-8b4fbbe473bd0d51d936bcf298f5b7f0e8d25f2e](http://wiki.winehq.org/FAQ#head-8b4fbbe473bd0d51d936bcf298f5b7f0e8d25f2e)

---

### Post by Bios Element on 2009-05-01
> **asdfoo said:**
> [http://wiki.winehq.org/FAQ#head-8b4fbbe473bd0d51d936bcf298f5b7f0e8d25f2e](http://wiki.winehq.org/FAQ#head-8b4fbbe473bd0d51d936bcf298f5b7f0e8d25f2e)

When your having a general discussion with people who don't know what "Wine" is, typing it in caps makes it easy to distinguish from the drink wine.

---

### Post by fletchoid on 2009-05-02
asdfoo

Thanks for the link to WINE wiki.  Makes this thread more complete.

---

### Post by fletchoid on 2009-05-02
DOH!!  I spent several hours reading randomly scattered bits and pieces that helped me install Steam and HL2.  That's why I decided to write it all down, and share with the community.  So, today I was looking for the applaunch ## that loads the original Half Life, and Blue Shift, and came across this EXCELLENT page that explains everything.  I wish I had found this earlier.  Anyway, this thread now has everything you need to install and run the whole Half Life series.

Check the link:
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam)

---

### Post by olaboy- on 2009-05-02
Well, I tried your advice since I've been having trouble getting HL2 engine working (team fortress 2 specifically). I couldn't find a steaminstall.exe that would update the client (your link downloads a 200ish byte file). My system is built similarly: Jaunty 64, Radeon 4870 but with ATI Catalyst&#8482; 9.4 Proprietary Linux x86 Display Drivers.

Everything installs smoothly and after I start the game, it'll play the Valve intro video but then goes to a black screen. I can hear the menu music but can't see or interact with anything. Back to looking for a solution :(


EDIT: Nevermind works perfectly now using the default propriety ATI drivers.

---

### Post by sandy8925 on 2009-05-03
Errr.......Steam and Half-Life 2 are displayed as working flawlessly out of the box on the Wine Appdb website(although of course on the latest "beta" versions). I've tried them and they work fine for me too. I'd recommend that you go right ahead and install the latest Wine version because a lot of games work a lot better and faster. Plus if you have an Nvidia card you can enjoy the benefits of the new and faster drivers too !

---

### Post by sandy8925 on 2009-05-03
By the way how well do Windows games work on Wine uing ATI cards ? I ask because many poeple seem to think that ATI cards don't perform well in Linux and seem to prefer Nvidia. Also how is the general performance of ATI cards in Linux? (like in Compiz for example)

---

### Post by fletchoid on 2009-05-03
> **sandy8925 said:**
> By the way how well do Windows games work on Wine uing ATI cards ? I ask because many poeple seem to think that ATI cards don't perform well in Linux and seem to prefer Nvidia. Also how is the general performance of ATI cards in Linux? (like in Compiz for example)

My ATI 4870 now works flawlessly with Compiz, plays video without any sputtering (even on the face of a desktop shere, while rotating), and works well with Prey and Half Life 2.  That being said, it did break when I upgraded to 9.04 ([https://bugs.launchpad.net/ubuntu/+bug/366529](https://bugs.launchpad.net/ubuntu/+bug/366529)).  After a bit of fiddling it is working perfectly again.  I think the only problem now is that a lot of the solutions you find on the forums mention NVidia specific things, and you have to dig a bit further to find the ATI specific solutions.  The only other minor problem I how have is that the games detect my ATI card, and decide that I can play in superhighwowwyzowwy graphics mode with antialiasing etc. but actually, I have to go in and manually turn some of the settings down to get good fps.  This is really only a pain because you have to do it EVERY time you go into the game.  I wish I could figure out how to access the configuration files of the game, and set the settings permanently.
However, in that other OS whose name I shall not mention, I get fabulous fps in Oblivion, maxed out with about 100 mods, super high graphics, etc.  Also, can play Crysis, Far Cry 2, etc. fast as hell.  Like being in a frikkin movie.  If we could just get there in Ubuntu....... sigh....

---

### Post by Bad Boy Bubby on 2009-05-03
Hi

I have followed the instructions and got steam installed but I am having trouble getting CS Source to run.

ubuntu 9.04
Wine 1.0.1
Nvidia Driver 1.80

It loaded so I ran the video stress test and it was ultra slow like 1 frame every 20 secs or something.

I have tried setting the -directx 81 switch on the steam start icon but CSS still reports that it is running in DX 9 in video options.  When I exit CSS it crashes the box and goes back to logon screen.

So I just tried launching the game and loaded a map just to run round on and the game just crashed back to desktop leaving desktop res 800 x 600.

short cut launch command is
env WINEPREFIX="/home/simon/.wine" wine "C:\Program Files\Steam\Steam.exe" -dxlevel 81

Any Ideas ?

Just installed HL2 and it seems to work ok

got CSS working now too had to set the dxlevel 81 in the launch options within the steam games menu all working fine now thx

---

### Post by u235sentinel on 2009-05-04
Has anyone tried getting the Mic to work with WINE and TF2?

I've been struggling with this for some time.  Seems it's a problem everywhere even on the winehq comments.  

Thought I'd ask here in case someone got it working :D

Oh and if you have it working, let me know which sound card you are using.  I have an SB Live which works great just not in the game :/

Thanks!

---

### Post by nerooo on 2009-06-07
When steam is done installing it pops up with a window and says Checking for Steam Updates... and it's been like that for 30 minutes.

It says Error Connecting to Steam Server after and just closes.

---

### Post by VoltRabbit on 2009-06-17
Some great info here. I hope this ends up stickied

---

### Post by VoltRabbit on 2009-06-18
I did a bunch of searching and reading trying to get ready to tackle installing my Half Life 2 from a 5 disc set.  I wanted to know what to do to prepare, as I am fair new with ubuntu, and brand new to WINE. In the end I didn't have to do anything specail. No terminal, no font downloads, nothing but point and click goodness.  The only hassle is waiting for the downloads.

I already had WINE installed and was ready to get my hands dirty.
First I tried installing from the first disk but hit a snag when it would not allow me to eject the disk to insert the second. Some one has since posted how to fix that but I'll save that for a later date.

So I decided to just try installing Steam and then HL2 from there.  It went almost perfectly, I didn't even have to install the Tahoma fonts as ( I was going to but then said f#ckit because I could not find the link to the font download right away, sometimes not being willing to wait is a virtue) I had read about. So I just opened WINE, went to Steams website, downloaded Steam, then installed/downloaded HL2, rebooted, WIN.  Now hear me that the performance is not good, but it is playable.  I did this just before bed last night so I have yet to really tweak settings or try the very latest WINE version.  With all settings on high the game slugs.  

I'd like to thank everyone in this thread making a effort to help the rest of us. We really need to get together and form a One-Stop-Shop document for WINE + Steam games (I don't mean links to other places).  What we have here is a really great start though.

---

### Post by neglect on 2009-07-04
I just installed ubuntu, all is well, I miss nothing except my CSS so thanks for a very neat instruction. 

I run into a problem right after installing steam. It updates fine, and after the 99% mark its just closes and is gone. If I then try to run it from the terminal (with this command wine "C:\steam\Steam.exe" -dxlevel 81 -novid -windowed -width 1024 -height 768 -heapsize 512000) i get the following output:

CellID: Fetching server list from CSDS. . .
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
fixme:urlmon:CoInternetSetFeatureEnabled 5, 0x00000002, 1, stub
fixme:urlmon:CoInternetSetFeatureEnabled 10, 0x00000002, 1, stub
CellID: CSDS returned 172 servers.
CellID: Connecting to 58.120.225.167:27031. . .
CellID: Connect to 58.120.225.167:27031 took 336 MS
CellID: Nothing beat our old best time of 12 MS
^Cschelehond@ubuntu:~/.wine/drive_c/steam$ Deleting active MRSW lock (0x114e24), expect failure


And that's it. After that nothing happens. Anybody here have the same problem? Any advice on how to fix it?

---

