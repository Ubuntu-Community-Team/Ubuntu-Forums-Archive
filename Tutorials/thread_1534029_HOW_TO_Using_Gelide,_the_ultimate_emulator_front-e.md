---
title: "HOW TO: Using Gelide, the ultimate emulator front-end"
date: 2010-07-18
forum: Tutorials
---

### Post by Mike_IronFist on 2010-07-18
I'm a huge fan of emulation on Ubuntu. However, there seems to be a common misconception that it's hard to get a good multi-emulator setup on Ubuntu. The truth is, things actually keep getting easier! Just recently, I discovered a fantastic emulator front-end called Gelide. This tutorial will show you how to use it and take advantage of its (awesome) features.

**_Sections_**:
-**Introduction To Gelide**
-**Downlading Gelide**
-**Getting Started**
*--Part I : Getting started with a clean slate*
*--Part II: Adding Game systems*
*--Part III: Adding ROMs*
*--Part IV: Adding Emulators*
-**Running Your Games**
-**The Sky's The Limit!**
-**Other, Important Stuff**

**Introduction to Gelide**
Gelide is a simple, but powerful, universal front-end for emulators on Linux. It basically supports any emulator, although there might be some exceptions. For more info about Gelide, go here:
_[http://gelide.sourceforge.net/index.php?sect=home&lang=en]("http://gelide.sourceforge.net/index.php?sect=home&lang=en")_

**Downloading Gelide**
_[32-bit version from Dropbox]("http://dl.dropbox.com/u/34318743/Installers/Linux/Emulator%20Frontends/gelide_0.1.5-1~getdeb1_i386.deb")_
^ Download and install this version if you're running a 32-bit version of Ubuntu (if you're unsure, most likely you are running 32-bit).

_[64-bit version from Dropbox]("http://dl.dropbox.com/u/34318743/Installers/Linux/Emulator%20Frontends/gelide_0.1.5-1~getdeb1_amd64.deb")_
^ Download and install this version if you're running a 64-bit version of Ubuntu.

**Getting Started**
*Part I: Getting started with a clean slate*
Let's get going! Open up Gelide. (in GNOME, it's located in the "Games" menu)
Upon opening Gelide for the first time, you may be surprised to find that, not only is it preconfigured, but there's a huge number of systems and emulators set up. Most users will find this rather annoying, as some of the settings are for emulators that are pretty dated, and lots of the settings are for video game systems you've never heard of. The way to start with a clean slate, however, is simple.

First, click "Edit -> Preferences" from the Gelide menu and uncheck "Load default systems at boot". Then, close Gelide, and open your Home folder. Press **[FONT="Courier New"]ctrl+H[/FONT]** to show the hidden folders, and open **[FONT="Courier New"].gelide[/FONT]** . Delete EVERTHING inside this folder, and you're done. Go back to your Home folder and press **[FONT="Courier New"]ctrl+H[/FONT]** again to hide your hidden folders. Remember, only delete the contents of your Gelide folder. Do NOT, I repeat, do NOT, delete any folders or anything else.

As a bonus, you can hide the filter pane unless you REALLY need to use it. It takes up rather unnecessary screen space. Hide it by clicking "View" from the menu and unchecking "Filters".

*Part II: Adding Game Systems*
Now that you've got a clean slate, let's try adding some systems you'll be emulating. In this example, I've installed Mednafen from the Ubuntu Software Center and I want to use it to play some NES games.

The first thing we will do is right-click the blank pane that's under  **Games Library** click "add". This will open a simple little two-tab dialog. For "name", you can call it whatever you want, but I will call this new system entry "NES" (without the quotes). You don't have to put anything for description, nor do you have to give it an icon file, dat file, or bios file, but I highly recommend giving it some kind of icon. Just click the generic gear icon under "icon" and a dialog will open to select one. I recommend clicking "Filesystem" in the dialog, going to "/usr/share/gelide/pixmaps" and picking an icon for the system you're emulating, as Gelide actually comes with some nice icons for those.

*Part III: Adding ROMs*
(Note: I'm not gonna provide you with any copyrighted ROMs in this tutorial. See bottom of post for more info.)
Now that our system has a name and (optionally) an icon, we can click the second tab, which is labeled "Directories". We really only need to add a ROMs folder, so click "open" under "Roms directory", locate and select the folder containing your NES ROMs, click "OK" and you're done.

Now we will refresh our ROMs list for the NES. Right-click the newly-made NES icon and click "Refresh". The pane on the right should now be filled with the ROMs you specified in your ROM folder. Sweet! Now all we need is to specify an emulator to run these ROMs with.

*Part IV: Adding Emulators*
Now that we're nearly done, I'm gonna take a moment to talk about the only empty pane left in the Gelide main window. This pane is the Emulators pane. Depending on what system you have currently selected, it only displays the emulators for that particular system. If you have an emulator that you will be using for more than one system (for example, using Mednafen for both NES and Gameboy Color) you will have to set it up for each system, rather than setting it up once. This might seem tedious, but it's actually very nice, because it allows versatility - for example, you might always want your NES ROMs to run in fullscreen, but you might also want your Gameboy ROMs to run in a window since they're very low resolution and look blocky when blown up to huge resolutions. Separating how each system uses Emulators allows us to do this.

Now on to adding Emulators!
With the NES selected under "Games Library", right-click the Emulators pane and click "add".
Adding a name for the Emulator is important, so I'll just be simple and put in "Mednafen" as the name. You don't have to specify the version, original author, or website - those are unimportant details. Once you've put in a name, click the button next to "Binary:".
This opens another "Select a File" dialog that you can use to locate your binaries. Most emulators that you can install with .debs or through the Software Center will be located under "/usr/games/" , although occasionally they might be installed under "/usr/bin/" . In the case of Mednafen, it's in "/usr/games", so we click "Filesystem", "usr", "games", and then we select "mednafen" and click "Open". We have our binary!

Now click the box under the "Binary" section. It's time to add some parameters, or as Gelide shortens them, "params". Parameters are what a program is told to do when it opens. With emulators, the parameters always include the name of the ROM file, and sometimes contain other things. Here's what I put in my "params" field for Mednafen:
```
-fs 0 "$gf"
```
Mednafen has a parameter to prevent it from opening in full screen. With [FONT="Courier New"]**-fs 0**[/FONT] added to the params field, I know that every NES ROM I open with Mednafen will not open full screen.
The more important part of this, though, is [FONT="Courier New"]**"$gf"**[/FONT] , (quotes should be included). [FONT="Courier New"]**"$gf"**[/FONT] is a variable that will be replaced with whatever ROM you select from your Game's library, so it's extremely important to always include it at the end of the "params" field. Without it, Gelide can't tell your emulator to open the ROM file.

Now this was a very simple example, but you might choose to add a lot more parameters or, possibly even less. Lots of emulators, like snes9x-gtk, can be configured without usage of the command-line at all, so you would only need [FONT="Courier New"]**"$gf"**[/FONT] as a parameter in that situation. It depends on what emulator you're using. In this case, Mednafen's command-line only. Configuring Mednafen is actually quite easy, but this is obviously not a Mednafen tutorial, so I'll leave it at that. Click "OK" when you're done and you're ready to go.

**Running your Games**
Now for the simple part. Once you have your emulator set up, all you have to do is double-click a game from the ROMs list and play! Gelide will not respond to user input until the emulator that it launched is closed, so don't freak out that it turns gray and ignores your mouse clicks. You can just minimize it after your ROM is launched if it's annoying you. Once you close the emulator you were running, Gelide becomes active again, allowing you to pick another ROM, System, Emulator, etc.

**The Sky's The Limit!**
So now that you know how to use Gelide, take advantage of it! You can use Gelide with just about any Emulator, be it Mednafen, SNES9x, Hu-Go!, Gens, or MAME. Configuring it for MAME is as simple as locating your MAME ROMs folder (which is in /home/user/.mame/roms/") and adding whatever command-line parameters you see fit. Once you refresh your ROMs list, you're good to go.

I currently use Gelide with some of the following emulators and systems on my Ubuntu 10.04 laptop:
MAME - Multiple Arcade Machine Emulator
Hu-Go! - Turbografx-16 Emulator
Mednafen - Multi-system Emulator, for NES, Gameboy, GBC, GBA, and more
Kega Fusion - Sega Genesis/Megadrive, Master System, 32x, CD, and Gamegear Emulator
prboom - Engine for playing games like Doom, Doom II, and Chex Quest.

Try out whatever emulators you like with Gelide - more often than not, you'll find it super convenient to find all of your retro games in one place.

**Other, Important Stuff**
-I will NOT tell you where to find copyrighted ROMs online. However, there are plenty of public domain ROMs for use with your emulator(s).
_[http://www.pdroms.de/files/]("http://www.pdroms.de/files/")_
Aside from those, if you want to find yourself some ROMs, Google it.

-I used Mednafen as an example in this tutorial, but obviously you can use whatever emulator you like.

-I'm not going to answer questions explaining how to use Mednafen in this thread - however, if enough users are interested, I could also put together a Mednafen tutorial.

-I'm more than willing to help if you have a question about Gelide that I didn't address in this tutorial, but I don't care if you think "Gelide sucks" or anything like that. If you don't want to use Gelide, you don't need this tutorial, so leave the space for users who actually want to use it so they can ask questions.

-If you are interested in getting any of the emulators I use, but you just can't figure out where to find them, send me a PM, and I'll put up a link for you at the bottom of this post.

---

### Post by tauresule on 2011-12-16
Great tutorial! Got me through the process perfectly and I am now playing Dragon Warrior as I should be.
If you're still active in the forums, a Mednafen tutorial would be great still, though I Google around every once in a while for them.

---

### Post by Mike_IronFist on 2011-12-16
> **tauresule said:**
> Great tutorial! Got me through the process perfectly and I am now playing Dragon Warrior as I should be.
If you're still active in the forums, a Mednafen tutorial would be great still, though I Google around every once in a while for them.

Glad to hear that the tutorial was helpful!

It's true that while Mednafen's probably one of the best emulators on Linux (and Mac OS X and UNIX), it's REALLY poorly documented outside of the developers' own docs.

I guess I could put together a Mednafen tutorial sometime soon next week.

---

