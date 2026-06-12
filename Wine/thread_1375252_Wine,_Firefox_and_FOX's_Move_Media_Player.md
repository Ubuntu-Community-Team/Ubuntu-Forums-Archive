---
title: "Wine, Firefox and FOX's Move Media Player"
date: 2010-01-07
forum: Wine
---

### Post by webpilot on 2010-01-07
&#8195;Over the past year, I've occasionally been able to watch FOX TV on my Hardy Heron machine. It is one of the few things that I found works brainlessly on µSoft OSes but is a real pain in the butt for Ubuntu.

&#8195;Since I first got it to work, upgrading wine has usually broken it.  Sporadically, it works from time to time.  I decided to spend some time and do a little wine version *regression* to make it work again.

&#8195;Now the following method isn't pretty, but it does work for me on Ubuntu Hardy Heron (8.04).

[LIST=1]
[*]if you have a previous installation of the Move Player, click Applications-Wine-Uninstall wine software and choose Move Media Player to be removed.
[*]uninstall your present wine installation using Synaptic (wine versions 1.1.35 &  1.0.0 do not work; I never tried 0.9.59).
[*]go to [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html) and download **[Wine 1.1.20 i386]("http://wine.budgetdedicated.com/archive/ubuntu/hardy/wine_1.1.20%7Ewinehq0%7Eubuntu%7E8.04-0ubuntu1_i386.deb")**, for Ubuntu Hardy (8.04).  Remember where you saved this file.
[*]I had a prior installation of Firefox version 2.0.0.20, but it can still be downloaded from the Internet (e.g. [http://www.freewarefiles.com/Mozilla-Firefox_program_23305.html](http://www.freewarefiles.com/Mozilla-Firefox_program_23305.html)   ) I found Firefox 3.x too buggy for this application.
[*]Find the downloaded Wine 1.1.20 file with Nautilus, right mouse click and choose _O_pen with "GDebi package manager". Install the program.
[*]Open another instance of Nautilus and move to the ~/.wine/drive_c directory.  Move your Firefox Setup 2.0.0.20.exe file there, rmc the file and lmc Open with "Wine Windows Program Loader".  The program will install.
[*]If all goes well you should be able to now select from the desktop's top bar, Applications - Wine - Programs - Mozilla Firefox - Mozilla Firefox.  Do it.
[*]In the firefox address bar, cut copy paste [http://www.fox.com/](http://www.fox.com/) and choose some episode to watch of some series.  My favs are 24 and Fringe.
[*]You will be eventually prompted to download their Move player.  Download the file to your desktop.  Move the file to ~/.wine/drive_c directory.  Close Firefox.   Rmc the file and lmc Open with "Wine Windows Program Loader".  The move player install program (MoveMediaPlayerWin_071503000010.exe) will install.
[*]Launch Firefox, go back to the FOX website, and chose again the episode you wish to watch.  A commercial will play first.  You will hear it, but not see the video.  As soon as the episode begins to play, watch to the right/center of the screen, just before the Advertisement window and look for the Full Screen button. Left mouse click (lmc) that button. The desktop will go blank, don't panic, press the escape key and voila video!
[/LIST]
&#8195;The buttons (e.g. sound slider likes to go to zero when you move the mouse over it) are a little buggy, but I watched a lot of 24 episodes last year.

[IMG]http://i913.photobucket.com/albums/ac336/web_pilot/misc/Fringe.jpg[/IMG]

---

### Post by Lepodo on 2010-01-07
Followed this tutorial and it works like a charm. Well, after all the installation and muckiong around stuff. Still, it is great to be able to watch shows like 24.

Cheers,
Lepodo

---

### Post by Treepwood on 2010-01-08
Are you able to play the video in fullscreen? I have tried using this guide on NFL Gamepass, and I get fine video and audio in windowed mode, but when I try to go fullscreen, the screen turns black and I am left with audio only. When I exit fullscren, the picture returns.

---

### Post by seandiggity on 2010-01-19
After trying all kinds of stuff (see my frustrated post at [http://forums.virtualbox.org/viewtopic.php?f=2&t=12472&p=120415#p118723](http://forums.virtualbox.org/viewtopic.php?f=2&t=12472&p=120415#p118723)), I ended up getting Move Media Player to work in Wine on Jaunty.  I'd like to post my solution to another thread since it's the first one that shows in Google: [http://ubuntuforums.org/showthread.php?t=474321](http://ubuntuforums.org/showthread.php?t=474321)
...but I can't for some reason, maybe because it's old.  Anyway, i'm posting my solution here, which is a lot like the one by webpilot above.

**I GOT MOVE MEDIA PLAYER TO WORK IN WINE**

Ubuntu version: 9.04 x86
Wine version: 1.01
Firefox version: 2.0.0.20
Flash player version: 9.0
Move Media Player version: 071706000001

**1.** Install Wine.  In Ubuntu/Debian:
```
sudo apt-get install wine
```

**2.** Download Firefox 2 and install it in Wine.  I grabbed ffox 2 from here: [http://download.oldapps.com/Firefox/Firefox%20Setup%202.0.0.20.exe](http://download.oldapps.com/Firefox/Firefox%20Setup%202.0.0.20.exe)
If you save the file on your Desktop, the command to install it would be:
```
wine ~/Desktop/Firefox*.exe
```
...you should also be able to run the .exe in wine just by opening it in Nautilus (e.g. double-clicking on the .exe).

**3.** Download Adobe Flash Player and install it in Wine. Download link: [http://fpdownload.adobe.com/get/flashplayer/current/install_flash_player.exe](http://fpdownload.adobe.com/get/flashplayer/current/install_flash_player.exe)
Install it just like the .exe in step 2; example:
```
wine ~/Desktop/install_flash_player.exe
```

**4.** Download the Move Media Player and install it in Wine. I grabbed it from here: [http://player.movenetworks.com/pub/BBB87026/MoveMediaPlayer_071303000006.exe](http://player.movenetworks.com/pub/BBB87026/MoveMediaPlayer_071303000006.exe)
Install it just like the other .exe files; example:
```
wine ~/Desktop/MoveMediaPlayer*.exe
```

***NOTE*:** I'm not sure this is a necessary step, as we will install the latest Move Media Player in step 6. I just don't want to screw with my setup to find out :P
Also, the Move Media Player version will likely change in the future, so finding a version that works in Wine and the website you wanna view (in my case, ESPN360) could be more difficult down the line.  That is, step 6 only works right now (January 2010) but no guarantees about later.

**5.** Install the User Agent Switcher addon for Firefox from here: [https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)
Restart Firefox and add the user agent string for Firefox 2 in Windows XP.  There are two ways of doing this:

**Option 1.** Add the string yourself via Tools > Add-ons > Extensions > User Agent Switcher > Options > New > New User Agent.  The string to paste in is ```
Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.8.1) Gecko/20061010 Firefox/2.0
```

**Option 2.** Grab an XML file to import the string (and many others) into User Agent Switcher here: [http://qainsight.net/content/binary/AgentStrings20070304.xml](http://qainsight.net/content/binary/AgentStrings20070304.xml)
Save the file and import it via Tools > Add-ons > Extensions > User Agent Switcher > Options > Import

**6.** With the user agent string set to Firefox 2 in Windows XP (Tools > Default User Agent), browse to [http://www.movenetworks.com/install-move-player](http://www.movenetworks.com/install-move-player)
Follow the instructions there to update your player. If your browser freezes, just close it and start it again, restoring the previous session.

**7.** Browse to the site you want to view, and you should be all set!  Just make sure your user agent string is still set to Firefox 2 in Windows XP.

---

### Post by DouglasAWh on 2010-01-20
couldn't delete...

---

### Post by DouglasAWh on 2010-01-20
> **seandiggity said:**
> 

Ubuntu version: 9.04 x86
Wine version: 1.01
Firefox version: 2.0.0.20
Flash player version: 9.0
Move Media Player version: 071706000001

Did you try in Karmic? I've only got Karmic and Lucid machines at home, though I suppose I could fix that if I had to...

It looks like I have everything except Jaunty and it doesn't work.  I don't understand why that would matter if we have the same version of wine...

Disregard my previous post. I see now it's x86. I might just go back and delete it if I can.

---

### Post by Virus666 on 2010-01-25
Finally I found an absolute way to run **Move Media Player** in Ubuntu.

What we have needed:

- Wine
- PlayOnLinux
- Firefox 2.0.0.20
- Flash Player
- Move Media Player


[COLOR=Navy]**[SIZE=3]1)[/SIZE]**[/COLOR] First, we need to install **Wine** via terminal or Synaptic.

```
sudo apt-get install wine
```[SIZE=3][COLOR=Navy][B]

2)[/B][/COLOR][/SIZE] **PlayOnLinux** will allow us to select different versions of Wine for multiple installations. And it seem that with the help of it, Windows applications work smoother than simple Wine method.

[http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html)

Repository installaton is recommended.

**[SIZE=3][COLOR=Navy]3)[/COLOR][/SIZE]** Download **Firefox 2.0.0.20**.

[ftp://ftp.mozilla.org/pub/firefox/releases/2.0.0.20/win32/en-US/Firefox%20Setup%202.0.0.20.exe](ftp://ftp.mozilla.org/pub/firefox/releases/2.0.0.20/win32/en-US/Firefox%20Setup%202.0.0.20.exe)
[ftp://ftp.mozilla.org/pub/firefox/releases/2.0.0.20/win32/](ftp://ftp.mozilla.org/pub/firefox/releases/2.0.0.20/win32/) (localizations)

[SIZE=3][COLOR=Navy]**4)**[/COLOR][/SIZE] Install Firefox 2.0.0.20


[LIST]
[*] PlayOnLinux
[*]Install
[*]Install a .pol package or unsupported application
[*]Manual intallation install a program in a new prefix
[*]Firefox 2
[*]Assign a wine version to a programm
[*]1.1.29
[*](We will move Firefox 2 setup exe to that location: "/home/username/.playonlinux/wineprefix/firefox 2/drive_c")
[*]Select Firefox Setup 2.0.0.20.exe and install
[*]Select firefox.exe as a shortcut in "/home/kullan&#305;c&#305; ad&#305;/.playonlinux/wineprefix/firefox 2/drive_c/program files/mozilla firefox" folder.
[/LIST]
 
**[SIZE=3][COLOR=Navy]5)[/COLOR][/SIZE]** Download Flash Player

[http://fpdownload.adobe.com/get/flashplayer/current/install_flash_player.exe](http://fpdownload.adobe.com/get/flashplayer/current/install_flash_player.exe)[SIZE=3][COLOR=Navy][B]

6)[/B][/COLOR][/SIZE] Install Flash Player


[LIST]
[*]PlayOnLinux
[*]Install
[*]Install a .pol package or unsupported application
[*]Edit an application already installed
[*]Firefox 2
[*]Assign a wine viersion to a programm
[*]1.1.29
[*](We will move Flash Player setup exe to that location: "/home/username/.playonlinux/wineprefix/firefox 2/drive_c")
[*]Install the Flash Player and do not make a shortcut.
[/LIST]

[SIZE=3][COLOR=Navy]**7)**[/COLOR][/SIZE] Download Move Media Player

Open Firefox 2 and download Move Media Player.

[http://www.movenetworks.com/install-move-player](http://www.movenetworks.com/install-move-player)[B][SIZE=3][COLOR=Navy]

8 )[/COLOR][/SIZE][/B] Install Move Media Player

Same method in 6.


That's all. Now, the websites which need Move Media Player should work on Firefox 2. I tried that method in **Jaunty** and I'm sure that Hardy and above versions will have the same result...:popcorn:

**edit:** You'll need to open Firefox 2 in PlayOnLinux window, otherwise it will always ask you to install Flash Player and Move Media Player.

---

### Post by webpilot on 2010-01-26
&#8195;[SIZE=4]**MAINTENANCE**[/SIZE]

&#8195;With **24** starting up again last week, I just knew this would happen: the Move Player flickers, showing the upper half of the flic for a while and then showing the bottom erratically.   It's watchable, but ...

&#8195;I spent some time *fiddling*, but to no avail.  Another piece of software mysteriously now will not launch no matter what I tried.  So, two programs work properly, one erratically, and another not at all.   I came to the conclusion it's time to [COLOR=Red]**reconfigure**[/COLOR] wine.

&#8195;The following is an on going work in progress.  I put this together from ideas I read all over the web.

[LIST=1]
[*]type at the command line ```
$ wine --version
``` responds with wine-1.1.20
[*]rename the hidden .wine folder in $HOME directory to .wine.backup using NAUTILUS.  I did this so I could always have a 'fall back' option.
[*]now recreate the wine configuration directory by typing ```
$ winecfg
``` I now have a very clean ~/.wine/drive_c directory .  However there are very few programs to run.  Notepad.exe is one I recognized.  None of my prior installed programs exist here anymore.
[*]I download all my desired software into one directory on my hard drive, named *downloads*.  I made a link here for my desired program installer using Nautilus and moved the link to the ~/.wine/drive_c directory .  From there I rmc'ed it and lmc'ed *Open with "Wine Windows Program Loader"*.  The installer ran without a glitch and my previously "broken" program now runs again.
[/LIST]
&#8195;Now, it's just a matter of repeating the above for installation of Firefox and and the Move Player.  Hopefully, nothing breaks.  I'll post my findings.

---

