---
title: "UPDATED FOR CATA: Install World of Warcraft"
date: 2011-06-02
forum: Wine
---

### Post by cwwilson721 on 2011-06-02
*_NOTE: This was written while using Gnome 2 in 11.04. Things and changed a little, but not much. Will try to update later_*

I know this subject gets alot of reads, but there has not been an updated version for awhile (at least, not since before Cata came out).

I do NOT believe in using Play On Linux (POL), Crossover, or anything other than wine itself. Why add layers of complexity to a project that works in it's most basic form? (POL/Crossover, et. al., use wine as their base. So, I just use wine. Makes it easier).

If you have an issue, and anywhere in there you use POL or anything else except wine, DON'T post in here. If you use their products, and even worse PAY FOR THEM, go get help from them.

Now, for the preliminaries.

These are the basics you should do BEFORE you install WoW:

[COLOR="Red"]Note: wine 1.3.26 and above work fine now, with no mouse issues anymore[/COLOR]
[LIST]
[*]Activate your proprietary video drivers in System > Administration > Additional Drivers (Nvidia users: If 'nvidia-settings' works, then it IS activated, ATi/AMD: If card is not supported or no drivers available, good luck, and Intel probably won't work at all)
[*]Install wine 1.3 It's easiest to look in the stickies in this forum, and install the wine ppa.
[*]Create a wine install directory by running 'winecfg' in a terminal. If it wants you to install Gecko, do it, or your Launcher won't show news. Also, set the default install as XP for sound to work, and go to your Sound tab and set the sound driver to ALSA. 
[/LIST]
Recently, the *WoW* cursor issues while running in opengl mode have been fixed. There is NO need to 'patch' wine for now. 

That pretty much covers it. From here on out, it depends on how you install WoW.
[LIST]
[*]Install from the Client Download from Blizzard (This is how I have just installed WoW. The lower "costs" of download time for patches ALONE saved me almost 13GB of downloading. YES. 13GB!!)
[*]Install from DVD (If you have the Cata DVD, use that. No need to install all of them, just the most recent you have). What I do is mount the DVD with the correct options for 'unhiding' it, then I copy all the files to a folder in my .wine folder (makes it easier). Right click on 'Installer.exe', choose 'open with wine', and wait until it's done.
[*]Copy from an existing Windows install (Copy to ~/.wine/drive_c/Program Files/World of Warcraft. Using this method, you'll have to create your own launcher for WoW. Google for how to create a launcher in Ubuntu)
[/LIST]
For any of the above, when you get the chance after it installs, close the game. Then, do the following to avoid the common mistake of installing other programs into your WoW install:
[LIST]
[*] Rename your .wine folder to .wine-wow or whatever you wish.
[*]Edit you laucher command to run WoW from the new folder. EX: ```
env WINEPREFIX="/home/<USERNAME>/.wine-wow" wine "C:\Program Files\World of Warcraft\Launcher.exe" -opengl
``` Replace <USERNAME> with your Ubuntu username. This tells wine to run in the new wine-wow folder and run Launcher /WoW in opengl mode.
[*]Run the Launcher, and let it update patches/whatever until it's done (Note: If installed from DVD, the first patch alone is almost 8GB..then more patches. Be prepared)
[/LIST]

If you run an Nvidia card, this is ALL you need to run WoW in wine. ATi/AMD might need a registry tweak (Google for it), and Intel MIGHT work if you DON'T run it in opengl mode, but FPS will be low, and LOTS of video issues.

**** NOTE: After the 4.2 patch, I have had issues with Launcher.exe actually running the game (Windows users have also reported this same issue). To temporarily fix this, edit your command to launch WoW to: ```
env WINEPREFIX="/home/<USERNAME>/.wine-wow" wine "C:\Program Files\World of Warcraft\Wow.exe" -opengl
```
This will launch Wow.exe directly. I will edit this as Blizzard addresses this issue  ****

***Additional settings, etc (Raising FPS, Vent, Mangler)***

Now that WoW is running, it is time to address additional issues, like low FPS. A quick overview might be in order.

WoW, like most Windows games, prefers to use DirectX for 3D rendering. Direct3D (D3D), however, is closed source, and while there have been strides in the open source community to get D3D functionality in Wine, it STILL isn't fully implemented yet. Also, wine 'converts' D3D calls to OpenGL, so we can still use this. Also, WoW supports OpenGL. Kind of.

WoW OpenGL is NOT a full blown OpenGL game, however. Many effects that D3D handles, are NOT handled in OpenGL in WoW. Sunshafts and Shadows come to mind. Also, if you look in your Settings for Video, your slider might be stuck on the lowest setting.This is mostly due to a combination of WoW/OpenGL/wine not being FULLY supported.

So, why run in OpenGL? Because, as the 'native' mode of Linux, it is FAST. If you have the EXACT same settings in both Windows/WoW and wine/WoW, wine/wow can beat Windows/WoW in FPS (due to OpenGL and MUCH better/faster/more efficient networking. Less 'lag' = more FPS due to better communication with the servers.) But you have to trade 'eyecandy' for FPS. Personally, I would rather have the FPS advantage than all the pretty graphics.

Ignore the 'slider'. Really. Just set EVERYTHING to the lowest settings. ALL of the drop downs in Video and Advanced.

Try it out. If you don't like how it looks, you can improve the visuals by changing ONE setting at a time, and see how your FPS changes. View Distance is a big killer of FPS, as is Anti-Aliasing. Start at the lowest, and slowly increase, testing after each change, until you strike the balance you like between 'eyecandy' and FPS. There is no "magic setting" or tweak that does more to help FPS/Looks than you trying to get a balance. What I prefer may not be what you prefer. Just remember, just because you can run "Ultra" settings in Windows D3D does NOT mean the same card will not choke on the same settings in OpenGL/wine.

Now, for those who need Ventrilo (Vent): DON'T. Use Mangler instead. I have used the Vent client under wine, and got it to kind of work, almost, but always had SOME kind of issue with it, whether it was key-bindings, sound quality, or whatever. Then I tried Mangler. It has the same functionality as the Windows Vent client, but is a Native Linux program. Easy to install, and easy/fast to run. No fiddling with sound/environment variables, or any of that stuff. It JUST WORKS.

***Installing a Windows based accessory (Curse Client, etc...)***

Now, you will see why I install WoW into it's own wine folder. If you keep WoW in the basic '.wine' folder, and you install other Windows programs, those programs can, and do, add things to a perfectly fine WoW install, and may create havoc with WoW. While this is not a big deal for most Windows programs, imagine if you HAVE TO REINSTALL WOW FROM SCRATCH! Personally, I would rather have each Windows program in it's own folder/prefix/environment. That way, if any of them bork up for whatever reason, at the most I would lose is just that one program, and not ALL of the programs I use in wine.

Another reason for 'separate wine folders' is: Windows gets malware and viruses just by existing! By seperating all the programs into their own 'bottle', it reduces the chance of a complete meltdown/reinstall. The chance is STILL there, but greatly reduced. A good example is if you have 4 cars and only room in the garage for 3 cars. If the garage burns down, one car should still be ok. (It could still catch fire/be damaged, but the odds are reduced). Or a hail storm hits, and one car gets damaged, but the three in the garage are protected. Do you see the point I am trying to make?

A good example of this is the Curse Client. It needs to have IE6 installed for it to work properly, but wine/WoW/IE6 has issues. So, How do I setup a program separated from WoW, but can still access it, without messing up the WoW 'system files'? Easily.

To continue with the Curse Client example, we first need to get a couple of programs. You will need:
[LIST]
[*]The Curse Client for Windows (version 3 works best for me. Find it on the Ver 4 download page. It's there)
[*]winetricks (It may already be installed. If not, can be gotten from the repos)
[/LIST]

We are going to install everything into the default '.wine' folder first, then change/rename things to get it into it's own folder.
First, run winecfg. This will setup your wine folder for everything it needs. Next, run winetricks, install vcrun6, then dotnet2.0, and then install IE6 (there are a few versions of winetricks out there. You need to find how to install things through it). After this, install the Curse Client. (If you want to install ver 4 of the Curse client, you need to install IE8. Curse may fail on loading, but just exit, and try again)

Now, for the magic:
[LIST]
[*]Make sure you can run Curse, and login all the way. Don't worry about errors for "cannot find World of Warcraft files". We will fix in a moment)
[*]Exit curse, and rename the '.wine' folder to something like '.wine-curse'
[*]Edit the Curse launcher command to reflect the new name (env WINEPREFIX="/home/<USER>/.wine-curse" wine <PROGRAM>). Check and edit the command until Curse launches correctly.
[*]Create a link to your REAL World of Warcraft folder (i.e. : ~/.wine-wow/drive_c/Program Files/World of Warcraft). I usually just open the 'Program Files' folder, right click "World of Warcraft", and 'create link'. 
[*]Copy that link to where the 'Program Files' in your 'curse folder' (i.e. ~/.wine-curse/drive_c/Program Files) so it thinks WoW is there. Rename the link so it is called "World of Warcraft"
[/LIST]

What we have done up to now, is install Curse into it's own folder, but have linked WoW in such a way to NOT mess with the running enviornment/system files of WoW, but have allowed access to the files of WoW itself for Curse to do it's thing.

In this manner, if Curse gets messed up, all you have to do is delete the '.wine-curse' folder, reinstall curse like above, and your actual WoW game and all it's Gigabytes of data are still there and working.

Now, doesn't that make sense? If you need to install other programs, do it the same way:
[LIST]
[*]Install into the .wine folder crated when you run winecfg
[*]Tweak it until it runs. Add whatever support it need through winetricks or whatever.
[*]Rename the .wine folder to something else, and edit the launcher command to use that new folder i.e env WINEPREFIX="/home/<USER>/.wine-foo" wine "foo"
[*]Create links to other folders as needed.
[/LIST]

Happy Questing!

Please, constructive comments are appreciated. Try to keep things civil.

---

### Post by MissCrunk on 2011-06-02
Looking forward to see the information you post about increasing fps.  WOW is running nearly perfect on my computer, im not lagging, the  graphics arent choppy, the sound works great.. I watched the opening  cinematic at the beginning and it ran beautifully.. it didnt cut out or  lag one time. The ONLY problem Im having is a constantly super low FPS.  (Anywhere from 2-9, no higher.) Im using a  ATI Technologies Inc Radeon  R350 [Radeon 9800 Pro] video card.. ( i found that out by putting the  command 
lspci | grep VGA in terminal.

Im not very savvy when it comes to computer lingo, so Im having problems  understanding nearly all of what I read when it comes to ubuntu related  materials. I am using Ubuntu because my computer killed itself, and I  didn't have the money to get a new OS. Although I am enjoying trying to  figure all of this out (because i always love a challenge), after a few days, it is starting to wear me  out.. If you have any advice, PLEASE let me know. I would really  appreciate it! 

Additional info:

this is what I have added to my config.wtf file:
SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET M2UseShaders "0"


I have also gone to System > Administration > Additional drivers, and there's absolutely nothing in the window..

PS. In response to the comment you made about having not used the Client Download through the Blizzard Website (Battle.net), I'd like to say that its AWESOME. It's a straight shot download, you don't have to go through all the BS of having to continually open and close the launcher to get all the patches. I've been playing WoW since vanilla, and have downloaded the game on many different computers many different times, and I must say that it was a lot easier downloading it through the site rather than through the CDs.

---

### Post by cwwilson721 on 2011-06-02
I would like to do that myself, but I tend to just do the DVD...Even though (and I'll find out if it's true) a Client Download might be smaller overall than a DVD install (If it IS smaller, I might just do that. But I can research that after this install is done/running)

Yes, your videocard/chip is older and not supported by ATi/AMD in their proprietary drivers. THAT'S a HUGE reason I refuse to use ATi/AMD video. They make good products, but their Linux support (insert your own nasty word here). Nvidia, in contrast, still supports an old MX400 AGP card I have. Go figure.

About the only thing I can tell all of you that are in ATi/AMD limbo, or 'using' an Intel card/chip, is to set EVERYTHING on Low, not just the slider. Turn off AA, Sampling, Shadows, EVERYTHING either off or lowest settings. Then, raise ONE thing up at a time, ONE setting, see how it affects your setup. Actually, everybody pught to do this. It tells you a TON about what will work, and what won't. (View distance is a BIG FPS killer. But you need to find a happy medium.)

I will also post about things like the Curse Client (addon manager) and how to install it, without messing up your WoW install. Plus, installing a Vent Client that is a native Linux client.

More neat stuff coming.

I'll post more exact settings and other stuff, if/when this bloody time-killing-game ever gets done downloading. That way, I won't be working from my old, calcified brain memory.

---

### Post by cwwilson721 on 2011-06-03
Ok..Might be awhile, because I decided to do a full client download instead of patching the Cata DVD. (9.7 GB for D/L, as compared to at least 1 6.5 GB download patch, plus who knows how many more patches after that?)

Maybe this will be faster. We'll find out. Stay tuned...

---

### Post by cwwilson721 on 2011-06-04
One GREAT thing about using the Clint Download to install the game:
Since it's not an old patch (like 4.0-4.1), there are more peers to d/l it, and it downloads at least 3 times faster!

Will find out if it needs big patches after the d/l

---

### Post by Tweak42 on 2011-06-05
A suggestion regarding the older ATI video chips that official support was dropped. Adding in some sort of explanation/warning of where the line is that divides hardware of official ATI catalyst support and open source only support.  This is to abate the disappointment of the people that install Wow expecting they can get near the 3d performance as windows only to discover they are stuck using the open source drivers and get a slideshow for best performance.

Note: I don't want to advocate either Nvidia or AMD hardware, just inform the users what they are getting into.

---

### Post by cwwilson721 on 2011-06-05
I agree totally, BUT....Where IS the line?

ATi/AMD "support" is a moving target. From driver release to driver release, you never know if 'your card' is the next to get the "We don't care about your operating system" axe.

Thus, I DO WHOLEHEARTADELY  advocate Nvidia over ATi/AMD. They've had YEARS to improve their drivers and support, and the only 'improvement' is features for top-of-the-line or their newest cards. Nvidia, on the other hand, makes Linux drivers that are:
[LIST]
[*]Easy to install and update (even without Ubuntu's packaging)
[*]Still support ancient (AGP, even) videocards
[*]Cares about Linux, and even has releases of their drivers just for improvements to WoW (I could find the release I'm thinking of later, but right now am too tired, and need to get to WalMart before I get some sleep)
[/LIST]Put all of those together, and ATi/AMD is terrible. While Intel is just behind the times, and seemingly unable to follow standards and the reality of the desktop market by putting out under-powered '3D' capable chips that an old AGP or PCI slot card would leave in the dust (but they do render pretty video), ATi/AMD has horsepower/speed/standards galore, but seem to HATE Linux users. And anyone who doesn't shell out alot of money every 2 years will sooner rather than later be driverless. While opensource has been doing a fantastic job, 3D just won't be fast enough without the proprietary drivers for sometime to come.

Yep. Give me Nvidia. They care. They work. They just plain are the TOP in Linux.

Ooh..I think I just heard my 9600 GSO purr at me. Good Nvidia card. Good card.

[SIZE="1"]*[COLOR="Blue"]The preceding rant is the thoughts and opinions of the author. Who is old, and maybe senile. We think. We have caught him wandering around WalMart in his houseslippers holding a videocard in his arms like a cat, and muttering "We need electrons, or smelly Orcs to feed you...". Okay. DEFINITELY senile. The future may not bode well for this poor WoW freak...[/COLOR]*[/SIZE]

---

### Post by cwwilson721 on 2011-06-06
UPDATE:

Sorry this is taking so long to update the rest of the install for Cataclysm, but here is what is going on:

[LIST]
[*]I have a slow cable connection (just like most of the rest of the world, I can only afford the lowest speed my cable co. offers, so max speed is limited to 1.5 down, 256 up)
[*]My WoW box is also being used by my kids, since their own computers have finally given up the ghost. So, I have to log off my account I use for WoW, and login to theirs (otherwise, the poor 5200+ AMD would choke.)
[*]I have 4 other users/computers on my network, along with a Nintendo Wii that does Netflix. Combine all of this, and I have to dole out downloading time for WoW with the other users of my network (what can I say? I'm a nice guy)
[/LIST]Combining all of the factors above together, I am only 1/2 of the way to finishing my WoW download (so far). I'm hoping in 1-2 more days I may get done with that part of the install, and continue on to finishing the setup and the settings portion of this post.

Thank you for your patience. I know that MINE is getting a bit thin. I need my WoW fix...

---

### Post by Tweak42 on 2011-06-06
> **cwwilson721 said:**
> UPDATE:

Sorry this is taking so long to update the rest of the install for Cataclysm, but here is what is going on:

[LIST]
[*]I have a slow cable connection (just like most of the rest of the world, I can only afford the lowest speed my cable co. offers, so max speed is limited to 1.5 down, 256 up)
[*]My WoW box is also being used by my kids, since their own computers have finally given up the ghost. So, I have to log off my account I use for WoW, and login to theirs (otherwise, the poor 5200+ AMD would choke.)
[*]I have 4 other users/computers on my network, along with a Nintendo Wii that does Netflix. Combine all of this, and I have to dole out downloading time for WoW with the other users of my network (what can I say? I'm a nice guy)
[/LIST]

As much as I'm inclined to agree with your AMD qualms, they are heading in the right direction (albeit years behind Nvidia track record), and we need them to keep heading that way.  Linux is about choice and with AMD **competition** in the linux support market, Nvidia will have to take notice and make even better drivers than we have now. (see nvidia optimus)

I highly suggest to make a backup of all the install files / patches so you don't have to download all of them again.  Personally my current install uses a Cata DVD + a few gigs of 4.0x patch files, previous it was a Wrath DVD plus bunch of patches burned to dvdr.  Funny side note, my friends kept borrowing them for their hosed windows installs.

Also (if you're tinker inclined) getting a ddwrt or tomato firmware based router that can do QOS throttling and setting up profiles to load balance helps divvy up the bandwidth so everyone is happy.

---

### Post by cwwilson721 on 2011-06-06
> **Tweak42 said:**
> As much as I'm inclined to agree with your AMD qualms, they are heading in the right direction (albeit years behind Nvidia track record), and we need them to keep heading that way.  Linux is about choice and with AMD **competition** in the linux support market, Nvidia will have to take notice and make even better drivers than we have now. (see nvidia optimus)

[COLOR="Red"]I highly suggest to make a backup of all the install files / patches so you don't have to download all of them again.  Personally my current install uses a Cata DVD + a few gigs of 4.0x patch files, previous it was a Wrath DVD plus bunch of patches burned to dvdr.  Funny side note, my friends kept borrowing them for their hosed windows installs.[/COLOR]

[COLOR="blue"]Also (if you're tinker inclined) getting a ddwrt or tomato firmware based router that can do QOS throttling and setting up profiles to load balance helps divvy up the bandwidth so everyone is happy.[/COLOR]

[LIST]
[*]That's part of the issue. They HAVE had YEARS to improve, and instead of real improvements, they add eye-candy for Windows, and barely improve Linux install procedures at all, not to mention dropping whole generations of cards for 'support'..After years and years and years and years of this B.S., I gave up. So no more ATi/AMD, nor Intel (VERY poor performance and no intention of improving in a real sense of the word)
[*][COLOR="red"]I already do that. Makes it ALOT easier to do a reload. Only this time, I'm doing it from scratch on purpose, just so I'll know what issues can come up in the Cataclysm install, and try to address them in the first post in this HOWTO.[/COLOR]
[*][COLOR="Blue"]I already use a QoS throttling router, and as an aside, have been (until VERY recently) using a WRT54GL router that was running DDWRT (It dead. Smoke. Not good. Dead. Poof). But even with QoS, I'm a nice guy, and am not going to kill everybody else's 'Net access just for a game. (Even though it is WoW, it IS a game.)[/COLOR]
[/LIST]

---

### Post by cwwilson721 on 2011-06-29
UPDATE:

Do to many reasons, I only finished the download last night, and will start updating post #1 again later today.

Actually, it worked out pretty good, with patch 4.2 coming out yesterday. One download, 9GB, and done. I think the client IS the way to go.

---

### Post by cwwilson721 on 2011-07-02
Spoke too soon, had an additional 5.5GB patch...

[But post #1 is updated.]("http://ubuntuforums.org/showpost.php?p=10895545&postcount=1")

Sorry for the delay.

---

### Post by cwwilson721 on 2011-07-02
Now has examples of additions like the Curse Client

---

### Post by Tweak42 on 2011-07-05
> **cwwilson721 said:**
> Now has examples of additions like the Curse Client

FYI: something borked the v3 curse client around 6/28.
[LIST]
[*]It's recognizing out-of-date addon need updates
[*]But is failing to download addons updated after 6/28.  
[*]Old addons seem to download, but not the ones updated after 4.2 patch.
[/LIST]
If you are using the v3 client please file a [detailed ticket]("http://clientsupport.curse.com/") to show your support so hopefully curse notices us and fixes it.  Make sure you mention you are using the _v3 curse client_ or you will more than likely get a canned windows answer for the v4 client that we cannot use.

---

### Post by cwwilson721 on 2011-07-05
> **Tweak42 said:**
> FYI: something borked the v3 curse client around 6/28.
[LIST]
[*]It's recognizing out-of-date addon need updates
[*]But is failing to download addons updated after 6/28.  
[*]Old addons seem to download, but not the ones updated after 4.2 patch.
[/LIST]
If you are using the v3 client please file a [detailed ticket]("http://clientsupport.curse.com/") to show your support so hopefully curse notices us and fixes it.  Make sure you mention you are using the _v3 curse client_ or you will more than likely get a canned windows answer for the v4 client that we cannot use.

I've noticed that, and have added Ver 4 to the HOWTO

---

### Post by cwwilson721 on 2011-08-17
wine 1.3.26 and above work fine now, with no mouse issues anymore

---

### Post by Tweak42 on 2011-08-17
> **cwwilson721 said:**
> I've noticed that, and have added Ver 4 to the HOWTO

I forgot follow up: Curse Client v4 requires .NET to run and thus will not work on linux.  I've tried getting it working using various winetricks install, and using mono, but no luck so far.

Good news is that there was some sort of update in the curse server backend that pushed the fail date back around mid July so the v3 client can now download some addons updated post 4.2 patch.  The bad news however is addons updated after that point are still fail.  The v3 client can still tell which addons are out of date even if it can't download them.

My work around was to install curse client v4 in winXP virtual machine and share my wow folder for it to update.

---

### Post by cwwilson721 on 2011-08-19
> **Tweak42 said:**
> I forgot follow up: Curse Client v4 requires .NET to run and thus will not work on linux.  I've tried getting it working using various winetricks install, and using mono, but no luck so far.

Good news is that there was some sort of update in the curse server backend that pushed the fail date back around mid July so the v3 client can now download some addons updated post 4.2 patch.  The bad news however is addons updated after that point are still fail.  The v3 client can still tell which addons are out of date even if it can't download them.

My work around was to install curse client v4 in winXP virtual machine and share my wow folder for it to update.

While that works, both 'workarounds' are ridiculous. (I use the VM route myself)

Imagine this: You need gas in your car (Addons need to be updated on you Linux machine). You go to the gas station, but they decided that the old nozzles needed 'updating'(Curse v4), and they won't fit into your filler neck. And it's the ONLY place to buy gas in 329 miles. But, you can take your old 360 V8 Ford pickup truck (Windows) to the station instead, and because it has a tank mounted in the bed, the 'new nozzle' fits, and you can fill it up. Now you take the pickup to your car, and have to transfer the gas 8oz at a time, because all you have is a old paper Dixie cup (Reboot/reboot/reboot...). 

I forget the name offhand, but there IS another Addon site that actuall has a Linux Client...

---

### Post by Tweak42 on 2011-08-24
> **cwwilson721 said:**
> 

I forget the name offhand, but there IS another Addon site that actuall has a Linux Client...

[http://www.wowmatrix.com/](http://www.wowmatrix.com/) has a linux client and [http://minion.mmoui.com/](http://minion.mmoui.com/) has a java client that can run under linux

I got turned off from wowmatrix from the dust up they had with curse and wowinterface few years ago.
[http://wow.joystiq.com/2009/05/06/wowmatrix-responds-to-curse-and-wow-interface/#continued](http://wow.joystiq.com/2009/05/06/wowmatrix-responds-to-curse-and-wow-interface/#continued)

I tried mmo minion and it was a pain to install was buggy and kept getting old versions.  Development moves at snail pace since its been in beta since 2009.

---

### Post by krendar on 2012-01-24
I read this thread and I saw there was a problem with Curse Client but that was ½ year ago.

I have not been running WoW on linux since early WotLK and before I start installing I wonder if the situation has changed for Curse Client and if it works now?

Only use Windows for WoW so really hope it will work since Curse Client syncs about 50 addons on my install and it would be hell to update them manually.

If it doesn't work are there any alternatives? (I remember there used to be a python addon update script, but I suppose it doesn't work on Curse nowadays)

---

### Post by cwwilson721 on 2012-01-24
The issue with the Curse Client is that it "requires" IE8+ to be installed, plus a few "needed" things from other things.

I gave up on Curse a long time ago, and I use the Linux-native Addon Manager from Wowmatrix when I need to manage my addons in Linux.

However, I do have a dual-boot setup, just because of WoW. Sometimes, it is SO much easier to update/patch in Windows. (I either dual boot, or use a Windows VM. Since I'm not actually 'running' the game in the VM, speed/FPS/usability are secondary. I just want the freakin' patch to work!)

If you use a VM, Curse works fine, and in Windows in a dual-boot setup.

However, to manage in Linux, I use wowmatrix.

---

### Post by phibxr on 2012-01-24
> **krendar said:**
> I read this thread and I saw there was a problem with Curse Client but that was ½ year ago.

I have not been running WoW on linux since early WotLK and before I start installing I wonder if the situation has changed for Curse Client and if it works now?

Only use Windows for WoW so really hope it will work since Curse Client syncs about 50 addons on my install and it would be hell to update them manually.

If it doesn't work are there any alternatives? (I remember there used to be a python addon update script, but I suppose it doesn't work on Curse nowadays)

I use Wowmatrix under Windows. Haven't tried it under Ubuntu yet, since I don't really use more than Elvui, Skada, GTFO, NPCSCAN and Clique anymore.

Pretty easy to keep those updated the old fashioned way. :)

---

### Post by Tweak42 on 2012-01-24
> **krendar said:**
> I read this thread and I saw there was a problem with Curse Client but that was ½ year ago.

I have not been running WoW on linux since early WotLK and before I start installing I wonder if the situation has changed for Curse Client and if it works now?

Only use Windows for WoW so really hope it will work since Curse Client syncs about 50 addons on my install and it would be hell to update them manually.

If it doesn't work are there any alternatives? (I remember there used to be a python addon update script, but I suppose it doesn't work on Curse nowadays)

Curse Client 3.x is completely non functioning (on both wine and windows) last I tried.  The 4.x client requires a .NET function that isn't implemented on mono and doesn't work in wine (yet).

I'm currently using 4.x client on a WinXP instance running on virtual box.  It scans/updates my wow directory shared via the virtual box networking shared folder feature.

---

### Post by cwwilson721 on 2012-01-25
> **Tweak42 said:**
> Curse Client 3.x is completely non functioning (on both wine and windows) last I tried.  The 4.x client requires a .NET function that isn't implemented on mono and doesn't work in wine (yet).

I'm currently using 4.x client on a WinXP instance running on virtual box.  It scans/updates my wow directory shared via the virtual box networking shared folder feature.

EXACTLY why I keep an Windows install on my WoW box. Both a VM and a Boot Partition. My actual Windows Partition  is a separate hard drive, so if one fails, I can copy my WoW install from the other (either from Linux/wine to Windows, or Windows to Linux/wine)

As an aside, since I multiboot (Ubuntu 11.10, Slackware 13-ish, Windows 7 64bit Ultimate, and a few others), my actual Linux/wine/WoW is on a separate hard drive, too, so all my users (one at a time, tho), and all my Linux Distros installed on this box can access it. 

Why? I HATE downloading the WoW client, or patches...It's getting to be a ridiculous size to do so anymore, so the extra "belt and suspenders" approach gets me back to WoW in the shortest time following the inevitable hard drive failure (as if you never thought "Oh NO!! WoW was on there! And it's GONE!" Well, it has happened to me more than once, so I'm paranoid now). 

And, NO, I do not, nor will I EVER, allow Windows access to ANY Linux parttiion. I do allow all my Linux installs to access the Windows 7 install, however. That keeps my Linux partitions fairly safe, and allows me to fiddle with Windows with anything I need to.

The way I describe in the HOWTO in the first post is the way one of my VMs is setup for WoW/wine, so it DOES work. My actual WORKING install for Linux/wine/WoW is VERY much more 'complicated', but I try to keep my HOWTOs simple.

---

