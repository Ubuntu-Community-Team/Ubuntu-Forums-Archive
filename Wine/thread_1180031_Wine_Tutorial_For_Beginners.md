---
title: "Wine Tutorial For Beginners"
date: 2009-06-06
forum: Wine
---

### Post by NightwishFan on 2009-06-06
Some Tips On Using Wine In Ubuntu:


To those who do not know, Wine is software to allow you run 16 and 32-bit Windows binaries natively on Unix-Like systems. Wine is available from the Ubuntu repositories, and runs on AMD64 as well, using 32-bit libraries. The 64-bit version drops support for old 16-bit applications.

[http://en.wikipedia.org/wiki/Wine_(software](http://en.wikipedia.org/wiki/Wine_(software))

Wine functions as a wrapper on common Windows functions (such as the NT kernel) and uses Linux equivalents to fulfill them. Wine is not based on Windows, and does need a Windows license to be used.

Performance and stability in applications can vary widely, however many programs work quite well, and may even perform better than when used on Windows. There is a web page where Windows applications are reviewed, and their functionality is rated.

[http://appdb.winehq.org/](http://appdb.winehq.org/)

The version of Wine in the repositories is somewhat out of date, though it is quite fine to use. For those wishing for a more up to date version of Wine can follow this tutorial to manually add a third party repository. This will allow you to stay current with the Wine development and utilize new technology. However, if all of your programs work as expected, I suggest you utilize the older, more stable Wine in the Ubuntu repositories.

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

When you have Wine installed, the first step is always to configure Wine to your specifics. Press alt+f2 and type the following command.

```
winecfg
```

The first tab has the Windows version you want to utilize. It is a safe default to use 'Windows Xp'. (Do not worry! It will not install Windows Xp!).

Next, go to the tab labeled drives. (This is important) Click the Autodetect button to set up acceptable defaults. If you use .iso images of software, then you might want to add a special entry.

An easy way to use .iso images in Wine is as following:

1.	Open up a terminal window.
2.	Type the following command to install Gmount-Iso, which is a utility to mount iso images. ```
sudo apt-get install gmountiso
```
3.	Create a directory to mount .iso images in. In the terminal window type: ```
sudo mkdir /media/virtual
```
4.	In winecfg under the drives tab, click add and name the device: ```
/media/virtual
```
5.	Simply mount any .iso images in Gmount-Iso to /media/virtual, and Wine will detect them as an inserted CD/DVD device.

The last essential task to set up Wine is to visit the audio tab. It will take a short while to initialize, which is normal. Just hit 'ok' when a popup window opens. Wine should default to using ALSA. If you want to change any settings here, feel free.

The Graphics tab allows you to set up advanced settings such as Pixel Shading, for which the defaults should be fine. You can also choose whether or not Wine applications obey your Window manager, which is personal taste.

DO NOT RUN WINE WITH COMPIZ OR KWIN ENABLED! Performance will suffer.

**UPDATE**
DIRECTX:

Wine already has directX support. Do not install DirectX. Wine's own implementation is far better than installing standard DirectX. Check your program or game through the Wine App Database and scroll down to see if any tweaks are necessary. At the most you may enable a native Windows DLL.


To run any applications, simply click the .exe file in your chosen file manager. If the executable opens in another type of application, such as an archiver, then you need to set up Wine as the software to manage .exe files. Using GNOME simply right click the file and choose properties. Go to the open with tab and click the bullet to use Wine Windows Program Loader. It should be a similar process for KDE and XFCE.

Note: If you manually add Wine as the program to

To run a windows application from the command line (and passive Windows command line options to the program):

```

cd /path/to/
wine application.exe -command1 -command2

```

Just replace my /path and the -commands with your own. Note that the windows command line parameters are optional, I am just noting they do work. Example:

```
wine arcanum.exe -no3d -fullscreen
```

IMPORTANT: When using the command line to run applications sometimes you NEED to change to the program’s directory using the 'cd' command. Otherwise the application may fail to run. 

Using Regedit:

This is very useful! Using the regedit command to edit the registry is needed for some games.

On Gnome or KDE, simply press alt+f2 and type: regedit
Push enter, and the registry will appear. Here is a list of useful keys.

[http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys)

•  In a terminal, type wine regedit and hit enter 
•  Open the tree on the left to the section where you need to add it (e.g., HKEY_CURRENT_USER\Software\Wine) 
•  Select the section you are going to add the new key to (e.g., Wine) 
•  Right click and select New->Key 
•  Type the name of the new key (taken from the list below) 
•  Hit enter
Keys I change (mostly for Starcraft)
HKCU/Software/Wine/Direct3D: 
DirectDrawRenderer (set to: opengl)
RenderTargetLockMode (set to: readtex)

This improves Starcraft performance to playability, I can achieve 180+ APM since the game does not lag.

Hopefully writing this will be of some use to newcomers that are trying Linux. Wine is a great piece of software and works on all the software from Windows I am used to. I am all for using open source alternatives, including games, but there is no harm in making use of the old software I purchased in the past.

These work nearly flawlessly:

•	Starcraft: Brood War
•	Morrowind
•	Arcanum Of Steamworks And Magick Obscura (Odd to install, if you like this game and want to run it, PM me and I will explain how, if enough need this tutorial, I will post another thread about it.)
•	Battle For Middle Earth
•	RPG Maker 2003 (no midi)

---

### Post by Kaideane on 2009-06-06
This is exactly what I was looking for, and worked a treat with no errors along the way.
I was able to mount my .iso files and have them working perfectly in less than 5 minutes.

Thank you NightwishFan!

---

### Post by mister_playboy on 2009-06-06
Great tutorial.  Thank you.

---

### Post by Sealbhach on 2009-06-07
Hi, very useful info about mounting .iso files. What's the best way to get them off a CD or DVD? I've seen people say to use something like:

dd if= /media/cdrom of= /whatever/directory/yournew.iso

Would that work for video games?

.

---

### Post by NightwishFan on 2009-06-08
Are you trying to create a .iso image from a CD/DVD? If so, I would just use Brasero or K3b to do so. Just copy the CD to an image.

Also, for this tutorial, if anyone has any questions please ask. I merely stated some tips I use that might not be common knowledge.

I will post some game individual tweaks as well.

I WILL EDIT THE ORIGINALLY POST WITH UPDATES. They will be marked with *** UPDATE ***

---

### Post by hapkidoin on 2010-01-05
I'm a complete newbie to Linux, let alone ubuntu, so please forgive my ignorance.  I want to get away from M$, but I have written a *lot* of custom-software for my employer in VB.NET and I want to know if there's a way to run it without installing Windows on every machine that I want to run these programs on if we switch over to ubuntu.

Can this be done using Wine?  Is that a stupid question?  I have no idea...  Thanks for your patience.

---

### Post by Chame_Wizard on 2010-03-23
This is good for me.:lolflag:

---

