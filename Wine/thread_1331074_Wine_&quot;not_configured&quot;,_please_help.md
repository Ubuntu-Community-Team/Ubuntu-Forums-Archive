---
title: "Wine &quot;not configured&quot;, please help"
date: 2009-11-18
forum: Wine
---

### Post by id10twork on 2009-11-18
I figured out my problem with WoW install, but now I do not know how to fix it. I have installed the latest version of Wine from Synaptic. I try to open a program (e.g. WoW), and it tells me "there is no Windows program configured to open this type of file". When I try to do a Wine update in Terminal, it blatantly says that it's not going to install the file. Please help. Thank you.

---

### Post by lisati on 2009-11-18
I'm not a regular user of Wine, but if memory serves correctly, there is this command from the terminal:
```
winecfg
```
If someone else comes up with a better suggestion, I'll defer to their wisdom.

---

### Post by Xog on 2009-11-19
> **lisati said:**
> I'm not a regular user of Wine, but if memory serves correctly, there is this command from the terminal:
```
winecfg
```
If someone else comes up with a better suggestion, I'll defer to their wisdom.


I haven't used winecfg in a while, I usually just click on Apps -> Wine -> Configure Wine..

I was bored and waiting on a response to another thread, so i decided to look at my wine configuration by using "winecfg"

i got this!
err:wineboot:pendingRename couldn't get file attributes (2)

and the winecfg still opened.

---

### Post by id10twork on 2009-11-19
Thank you for the responses, but when I go into "configure wine" a lot comes up and it seems configured. When I type "winecfg" it says "cannot allocate memory". This is so frustrating!

---

### Post by Xog on 2009-11-19
id10twork, open a terminal and type
```
wine --version
```
tell me what it says

---

### Post by id10twork on 2009-11-19
> **Xog said:**
> id10twork, open a terminal and type
```
wine --version
```
tell me what it says

Ok well I did that, and very odd, it says 1.1.33... but I already downloaded 1.2...???

---

### Post by Xog on 2009-11-19
> **id10twork said:**
> Ok well I did that, and very odd, it says 1.1.33... but I already downloaded 1.2...???

you have the newest version of wine.. i wish i could solve my problem.. it should be working for you.

Also, have you tried changing the current OS from "Windows XP" to "Windows 2000" in winecfg ?

---

### Post by id10twork on 2009-11-19
> **Xog said:**
> you have the newest version of wine.. i wish i could solve my problem.. it should be working for you.

Also, have you tried changing the current OS from "Windows XP" to "Windows 2000" in winecfg ?

I just did that, but no change. What should other things in Wine be set to though? This is my only my 2nd experience trying to use a Windows program...

---

### Post by Xog on 2009-11-19
go into ubuntu software center and search "wine"

There should be two results. Open up the first one, and tell me if it says "Install" or "Remove" (DO NOT CLICK JUST LOOK)
Regardless of what it says, go back, and click on the 2nd result (Beta Release) and tell me if it says "Install" or "Remove"

It may seem pointless to you but I'm trying to figure out my problem as well as help you

---

### Post by id10twork on 2009-11-19
I don't understand where you are telling me to go. If I go to Synaptic it tells me 1.2 is installed. Is this what you mean?

---

### Post by Xog on 2009-11-19
> **id10twork said:**
> I don't understand where you are telling me to go. If I go to Synaptic it tells me 1.2 is installed. Is this what you mean?

Genius! I didn't think of using Synaptic to see if I can find my version of wine.. you just solved my problem! Finally installing the correct version of wine!

As for your problem.. Sorry :(

What I meant was click on Applications, and on the bottom should be Ubuntu Software Center..

what version of ubuntu u running?

---

### Post by id10twork on 2009-11-19
I don't know where this "wine 1.2" is coming from... if I try to download from the site though (binary) it fails :(

---

### Post by id10twork on 2009-11-19
> **Xog said:**
> Genius! I didn't think of using Synaptic to see if I can find my version of wine.. you just solved my problem! Finally installing the correct version of wine!

As for your problem.. Sorry :(

What I meant was click on Applications, and on the bottom should be Ubuntu Software Center..

what version of ubuntu u running?

I have 9.1... But I don't have Software Center anywhere

---

### Post by Xog on 2009-11-19
9.10 "Karmic Koala" ?

I don't know why you wouldn't have this.. When you click "Applications" what is on the list that drops down?

---

### Post by id10twork on 2009-11-19
accessories, games, graphics, internet, office, programming, sound & video, system tools, wine

---

### Post by Alatar1 on 2009-11-19
So the installer wont run? which installation method are you using? and also this is kinda a simple thing but try right clicking the installer and selecting "run with wine windows program loader"

---

### Post by Xog on 2009-11-19
That's weird!

[http://img29.imageshack.us/img29/8150/screenshotpes.png](http://img29.imageshack.us/img29/8150/screenshotpes.png)

And yes, I did just bring up the WoW installer to tease you :P no hard feelings! I really don't know what the problem is.

---

### Post by id10twork on 2009-11-19
When I try to run it in Wine, it tells me Wine is not configured.

---

### Post by Xog on 2009-11-19
try completely uninstalling wine, then do this

```
rm -rf $HOME/.wine
rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.xpm

```

when that's done, type "wine --version" and tell me what it says. I hope you don't have a ghost like i did :(

---

### Post by Alatar1 on 2009-11-19
Xog, from what i read on the other thread you posted on, those rm commands didnt work out too well, try walking him thru removing them with synaptic

---

### Post by Xog on 2009-11-19
> **Alatar1 said:**
> Xog, from what i read on the other thread you posted on, those rm commands didnt work out too well, try walking him thru removing them with synaptic
the rm commands worked perfectly, it's just that another version of wine was installed in another directory that i didn't even know about.

the "ghost" wine ;)

those instructions should work fine.

---

### Post by id10twork on 2009-11-19
> **Xog said:**
> try completely uninstalling wine, then do this

```
rm -rf $HOME/.wine
rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.xpm

```

when that's done, type "wine --version" and tell me what it says. I hope you don't have a ghost like i did :(
"command not found"

---

### Post by Xog on 2009-11-19
> **id10twork said:**
> How do I uninstall Wine? I know I sound like a total n00b...

[http://wiki.winehq.org/FAQ#head-2e99ab665e3b15d1880eff2bcbb640b2d5839586](http://wiki.winehq.org/FAQ#head-2e99ab665e3b15d1880eff2bcbb640b2d5839586)

:popcorn:

if that confuses you, just how exactly did you install wine in the first place? You claim you don't have an "Ubuntu Software Center"

on that note. run this in a terminal and tell me what it says:
```
cat /etc/issue
```

---

### Post by id10twork on 2009-11-19
it says Ubuntu 9.10 \n \l

---

### Post by Alatar1 on 2009-11-19
did you try and run those rm commands all at once? if you did it could be causing the "command not found"

---

### Post by Xog on 2009-11-19
> **id10twork said:**
> it says Ubuntu 9.10 \n \l

Click on System -> Admininstrator -> Update Manager

Let it run, then click "Install Updates" if it's available.

Then click "Check" after it's done again, and install again if anything else was found. I always double check even if it's not necessary

> did you try and run those rm commands all at once? if you did it could be causing the "command not found"

Indeed, you must run each line as a separate command.

```
rm -rf $HOME/.wine 
```
PRESS ENTER
```
rm -f $HOME/.config/menus/applications-merged/wine* 
```
PRESS ENTER
```
rm -rf $HOME/.local/share/applications/wine 
```
PRESS ENTER
```
rm -f $HOME/.local/share/desktop-directories/wine* 
```
PRESS ENTER
```
rm -f $HOME/.local/share/icons/????_*.xpm 
```
PRESS ENTER

---

### Post by Alatar1 on 2009-11-19
Why are you having him check for OS updates? the problem is obciously with WoW and wine..I dont understand...

---

### Post by Xog on 2009-11-19
> **Alatar1 said:**
> Why are you having him check for OS updates? the problem is obciously with WoW and wine..I dont understand...

Because under Applications, he does not have "Ubuntu Software Center" and he is indeed running 9.10 Karmic

[http://ubuntuforums.org/showpost.php?p=8346288&postcount=15](http://ubuntuforums.org/showpost.php?p=8346288&postcount=15)


id10twork, does Software Center happen to be in "System Tools" ?

---

### Post by id10twork on 2009-11-19
> **Xog said:**
> Click on System -> Admininstrator -> Update Manager

Let it run, then click "Install Updates" if it's available.

Then click "Check" after it's done again, and install again if anything else was found. I always double check even if it's not necessary



Indeed, you must run each line as a separate command.

```
rm -rf $HOME/.wine 
```
PRESS ENTER
```
rm -f $HOME/.config/menus/applications-merged/wine* 
```
PRESS ENTER
```
rm -rf $HOME/.local/share/applications/wine 
```
PRESS ENTER
```
rm -f $HOME/.local/share/desktop-directories/wine* 
```
PRESS ENTER
```
rm -f $HOME/.local/share/icons/????_*.xpm 
```
PRESS ENTER

It downloaded some updates. I don't think I can do those commands again because I think earlier you had me uninstall Wine. I don't know how to get it back other than Synaptic, but that doesn't seem to be doing anything. This is a very odd problem...

---

### Post by Xog on 2009-11-19
> **id10twork said:**
> It downloaded some updates. I don't think I can do those commands again because I think earlier you had me uninstall Wine. I don't know how to get it back other than Synaptic, but that doesn't seem to be doing anything. This is a very odd problem...

You're not confirming if you've been doing anything we're telling you. What have you done that we told you to do so far?  I need to know what step you're at.

Is wine currently installed? 
Did you run those commands I mentioned? (This uninstalls wine)
Did you install all the updated with the Update manager?
Is Ubuntu Software Manager now under Applications? It should be at the bottom. Check "System Tools" under Applications to see if it's in there.
How did you install wine from the beginning?

---

### Post by Alatar1 on 2009-11-19
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) 
do it how it says to there... should ensure its up to date, installing wine right off the bat with synaptic is no bueno

---

### Post by id10twork on 2009-11-19
> **Xog said:**
> You're not confirming if you've been doing anything we're telling you. What have you done that we told you to do so far?  I need to know what step you're at.

Is wine currently installed? 
Did you run those commands I mentioned? (This uninstalls wine)
Did you install all the updated with the Update manager?
Is Ubuntu Software Manager now under Applications? It should be at the bottom. Check "System Tools" under Applications to see if it's in there.
How did you install wine from the beginning?

1. no, it is gone, as I was told to do
2. yes, I did
3. yes, I updated
4. no, Software Manager is still not there. All I have under System tools is Ubuntu Tweak, Sun Java 6, and XScreensaver setup
5. I originally installed Wine through Synaptic

Also, as I said before, when I try to download Wine the way their site tells me to it says that I have unmet dependencies and the package will not be installed.

---

### Post by Xog on 2009-11-19
> **id10twork said:**
> 1. no, it is gone, as I was told to do
2. yes, I did
3. yes, I updated
4. no, Software Manager is still not there. All I have under System tools is Ubuntu Tweak, Sun Java 6, and XScreensaver setup
5. I originally installed Wine through Synaptic

Also, as I said before, when I try to download Wine the way their site tells me to it says that I have unmet dependencies and the package will not be installed.

I'm at work and can't see the ubuntu screens so bear with me.

Go into Synaptic and do a search for "wine"

There should be about 10-20 results if you have uninstalled it. If there is anything with a GREEN BOX before it, right click on ALL the green boxes, and select "Mark for COMPLETE REMOVAL"

When you're done doing that, click the "Apply" button. Then click Close, and follow any directions it says regarding updates, etc.
*If you uninstalled wine correctly, there shouldn't be ANY green boxes. If there are none, proceed to the next step.

-------

Go to [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)
Scroll down past the screen shot of "Software Sources" to where it says "Installing Wine:"

You should see: "Click close to finish, and then reload the package information when prompted. If you have Wine installed, the system's update manager will now inform you of the latest Wine beta release and prompt you to upgrade. If you haven't installed Wine yet, go to Applications->Add/Remove and search for Wine or just click this link."
Click on "Click this link." and select Run (i believe "aptget something" would be selected on a list (shouldn't be anything else but that on the list), then select Install.

Let me know if it gives you an error.


*If you receive an error before another step (such as clicking "close" in Synaptic and the update gives you an error), reply here without continuing on to the next steps.

---

### Post by id10twork on 2009-11-19
Thank you. I have done all that... except... I just noticed that my "add/remove" is missing... It was there before the upgrade...

---

### Post by Xog on 2009-11-19
> **id10twork said:**
> Thank you. I have done all that... except... I just noticed that my "add/remove" is missing... It was there before the upgrade...

One problem at a time. We'll get to that.

Open terminal, input this:

```
wine --version
```

If it gives you a version, try running your WoW installer (right click on it, select Windows Emulator blah blah)

---

### Post by id10twork on 2009-11-19
The program 'wine' can be found in the following packages:
 * wine
 * wine1.2
Try: sudo apt-get install <selected package>
wine: command not found

---

### Post by Xog on 2009-11-19
> **id10twork said:**
> The program 'wine' can be found in the following packages:
 * wine
 * wine1.2
Try: sudo apt-get install <selected package>
wine: command not found

Go to Update Manager in System => Administration and check for updates. Assuming you've done the steps to get the most recent version of wine before all this mess, it should update your wine package.

---

### Post by id10twork on 2009-11-19
checked, no updates

---

### Post by Xog on 2009-11-19
> **id10twork said:**
> checked, no updates

Go to System->Administration->Software Sources

Then select the Third Party Software (or Other Software, should be 2nd tab on the top) tab and click Add.

enter this in the promt after clicking "add":
```
ppa:ubuntu-wine/ppa
```
Click "Add Source"
Click close to finish, and then reload the package information when prompted. If you have Wine installed, the system's update manager will now inform you of the latest Wine beta release and prompt you to upgrade.

If it gives you an error, enter this into your terminal
```
sudo apt-get install wine1.2
```

After that's done, go back to Update Manager and check for updates.

As a side note, did you happen to upgrade to 9.10 from 9.04?

---

### Post by id10twork on 2009-11-19
I did upgrade, yes. I only did it a few days ago, though because of my bad experience with Jaunty I was nervous. Terminal finally decided to install Wine (thanks). No updates though.

---

### Post by Xog on 2009-11-19
> **id10twork said:**
> Ok, I've done that. No update. Wine was removed though, remember? I can't get it installed again.

doing sudo apt-get install wine1.2 should have installed version 1.2. in terminal type "wine --version" without quotes

---

### Post by Xog on 2009-11-19
As for Ubuntu Software Center,

[http://allmyapps.com/app/ubuntu-9.10/software-center-ubuntu-software-center](http://allmyapps.com/app/ubuntu-9.10/software-center-ubuntu-software-center)

Near the top, there should be an orange button that says "Free" and when you hover your cursor over it, it changes to "Install"

Click on it.

---

### Post by id10twork on 2009-11-19
> **id10twork said:**
> I did upgrade, yes. I only did it a few days ago, though because of my bad experience with Jaunty I was nervous. Terminal finally decided to install Wine (thanks). No updates though.

Also, I don't know if I was supposed to try again, but if I was, it still tells me there is no Windows program configured.

---

### Post by Xog on 2009-11-19
> **id10twork said:**
> Also, I don't know if I was supposed to try again, but if I was, it still tells me there is no Windows program configured.

terminal:
```
winecfg
```

This configures Wine. When the program opens up, click on Drives, then click Audio.. it should be detecting everything you have.

After you do this, click Apply / OK. You SHOULD be ALL set!

PS: I know you were confused last night / thismorning when you were mentioning 1.1.33 and 1.2.. for clarification, 1.1.33 IS version 1.2.

---

### Post by id10twork on 2009-11-19
It still tells me the same thing, even after those steps. Do you know what my configuration should say?

---

### Post by Xog on 2009-11-19
> **id10twork said:**
> It still tells me the same thing, even after those steps. Do you know what my configuration should say?

what does it say when you type ```
winecfg
```

what does it say when you type ```
wine --version
```

---

### Post by id10twork on 2009-11-19
winecfg brings up the config screen. wine --version says 1.1.33

---

### Post by Xog on 2009-11-19
> **id10twork said:**
> winecfg brings up the config screen. wine --version says 1.1.33

Is wine an option under Applications?

If so, close out the terminal and close out the winecfg if you have it open. Go to Applications -> Wine -> Configure Wine

if it works then it's working

---

### Post by id10twork on 2009-11-19
it brings up the Wine configuration screen

---

### Post by Xog on 2009-11-19
> **id10twork said:**
> it brings up the Wine configuration screen

okay your problem is solved. go to your wow installer, right click and open with wine

---

### Post by id10twork on 2009-11-19
> **Xog said:**
> okay your problem is solved. go to your wow installer, right click and open with wine

Same error still

---

### Post by Alatar1 on 2009-11-19
Tell me, if you go to Applications>wine>configure wine and click on the "drives" tab is there anything in there?

---

### Post by Xog on 2009-11-19
> **Alatar1 said:**
> Tell me, if you go to Applications>wine>configure wine and click on the "drives" tab is there anything in there?

Him and I are sending PM's to eachother. When he tries to run the WoW installer, it says:
[quote=id10twork]
It says what I've been typing if you look back through. It says "there is no Windows program configured to open this type of file"[/quote]

I think another important question to ask here is..

What installer are you running? Did you download the installer from worldofwarcraft.com or are you trying to use the CD?

---

### Post by id10twork on 2009-11-19
I'm sorry, what do you mean by what installer?

---

### Post by Xog on 2009-11-19
> **id10twork said:**
> I'm sorry, what do you mean by what installer?

The World of Warcraft installer. You've been trying to install world of warcraft right?

[http://ubuntuforums.org/showthread.php?t=1330965](http://ubuntuforums.org/showthread.php?t=1330965)

---

### Post by id10twork on 2009-11-19
I have this feeling that I just drug you guys around in circles for no reason... I have no idea what a WoW installer is.

---

### Post by Xog on 2009-11-19
> **id10twork said:**
> I have this feeling that I just drug you guys around in circles for no reason... I have no idea what a WoW installer is.

[http://www.worldofwarcraft.com/downloads/wowclient-download.html](http://www.worldofwarcraft.com/downloads/wowclient-download.html)

Click on "Download for PC"

"WoW Installer" = "World of Warcraft Installer"
Description: This installs the game World of Warcraft.

---

### Post by id10twork on 2009-11-19
I can't use my discs to download?

---

### Post by Xog on 2009-11-19
> **id10twork said:**
> I can't use my discs to download?

You can but there's many steps involved and its complicated.

It's best to just download the installer from the link I mentioned. All you have to do is open it and it will install.

---

### Post by id10twork on 2009-11-19
Thanks again. I'll respond in a few hours, I'm at work right now.

---

### Post by id10twork on 2009-11-20
Well, it is going much, much further. I haven't seen if it's playable yet, but it is downloading. Sorry for that trouble earlier, I had no idea that downloading from the discs and downloading from the installer were 2 different things

---

### Post by Xog on 2009-11-20
> **id10twork said:**
> Well, it is going much, much further. I haven't seen if it's playable yet, but it is downloading. Sorry for that trouble earlier, I had no idea that downloading from the discs and downloading from the installer were 2 different things

No problem. Also,

Some computers might experience low FPS , while trying to run WoW in opengl mode . In that case , removing Config.wtf file ( it is localised in WTF folder ) , running WoW to generate that file again , and then making changes ( to opengl mode ) might help. Make sure , to give read/write access to WTF folder ( otherwise WoW will crash ). Add this line to your Config.wtf file using your favorite text editor: 

SET gxAPI "OpenGL"

Just add that to the bottom of the Config.wtf file, located in the WTF folder.

Also, after every patch, you have to go to your C:/Program Files/ for wine (Applications -> Wine -> Browse C:\) and set permissions for Create and Delete Files on the World of Warcraft folder. To do so, right click on the World of Warcraft folder and go to Properties. Set the permissions on all three, and click Enable Permissions, then click OK.

*You must do that after every patch, otherwise WoW will lock you out every time and it won't run until you do that.

If you somehow come across another problem, read this: [http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine](http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine)

it's not too long and will inform you of any problems you might discover, so no reason to ask :-P

---

### Post by blkdrmz on 2012-06-17
> **Xog said:**
> try completely uninstalling wine, then do this

```
rm -rf $HOME/.wine
rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.xpm

```when that's done, type "wine --version" and tell me what it says. I hope you don't have a ghost like i did :(

Thanks Xog I most definitely had a "ghost" wine installation kudos for you.

---

