---
title: "Should I try Ubuntu Studio?"
date: 2017-03-02
forum: Ubuntu Studio
---

### Post by norafaithrainbow on 2017-03-02
I am new to ubuntu and I have it installed on my current computer. I want to know if I should give ubuntu studio a shot. Can someone tell me the pros and cons of ubuntu studio? Is the gui like the default ubuntu gui? (I think it is gnome, correct me if I am wrong.) I am sorry if someone has already posted this. I did not find a post about this.

---

### Post by howefield on 2017-03-02
Have a browse at [http://ubuntustudio.org/](http://ubuntustudio.org/) and take the feature tour.. then ask questions on anything you don't understand.

The desktop environment is xfce so quite unlike the default Ubuntu Unity interface.

---

### Post by norafaithrainbow on 2017-03-03
I decided to just go with it. I do wish I could move that top bar to the bottom but other than that, it's okay. That isn't really why I got it though. I got it because it is a creative suite, and has a bunch of freeware tools that won't have annoying logos and I can just use them forever.

---

### Post by howefield on 2017-03-03
> **norafaithrainbow said:**
> I decided to just go with it. I do wish I could move that top bar to the bottom but other than that, it's okay..

You should be able to move the panel in Ubuntu Studio. 

Can't quite remember but it might be right click on an empty part of the panel, select panel properties > unlock and then grab the left edge of the panel and drag it down. If I got that wrong I'm sure someone will come along and correct it but in any event I'm sure it is doable.

---

### Post by Mike_Whell on 2017-03-03
Ubuntu Studio is my daily driver for music playback.  However, remember that the default kernel is optimized for real time music production.  That optimization might not be perfect for other applications.  You can, alternatively, opt for the standard Ubuntu kernel at boot time.

---

### Post by yoshii on 2017-03-03
I have tried a wide variety of Linux systems and I keep coming back to Ubuntu Studio.  
The main interface is very similar to Xubuntu and has some of the same programs and features and dependencies.  
The only real complaint I have with Ubuntu Studio is that it comes with way too many fonts, but those can be gradually deleted with much effort.  
On a previous version of Ubuntu Studio, the font manager crashed on some buggy fonts until they were manually disabled.  I don't know if that's been fixed yet.  

Xubuntu has nearly the exact same stuff with less bloat, and then you can manually install the low-latency kernel if you have a good internet connection.  And then after that, manually pick and choose which multimedia programs and codecs you want to add to Xubuntu.  That would make it very much like Ubuntu Studio without the extra bloat.  

The Xubuntu install .ISO is significantly smaller than the Ubuntu Studio .ISO which comes with a lot of stuff, including Linux instruments.  
As long as you install Synaptic Package Manager, gDebi, and maybe even Ubuntu Software Center, you can download pretty much everything you need.  Apt-get is there of course.  

Personally, I like XFCE alot for the desktop environment.  I do usually also install PCmanFM also, as a file manager to use occasionally though.  It's a nice extra that doesn't fight with XFCE's Thunar.  It comes with Lubuntu, but you don't need to install Lubuntu just to use it.  Other than that, I find that Xubuntu's and Ubuntu Studio's XFCE style interface is really nice and convenient and doesn't leave anything out.  For setting the system configuration, it seems a lot easier than some of the others.  And for customizations, it's still versatile without slowing things down too much.  

The other good thing about Ubuntu Studio is that it comes with video and image editing and conversion gear as well as ISO and DVD/CD management tools.  And of course you can play videos too.  It's easier to use VLC Media Player for some formats, and that's available too, so it's not really a problem.  I found that Parole crashed on previous versions, so I stopped using it entirely and just use VLC Media Player instead.  For some simple edits, you can use the 32-bit Windows version of AVIdeMux and it runs OK in Linux over Wine.  

It's worth getting the more up to date version of Wine from [http://winehq.org](http://winehq.org)
I find the "wine-devel" version most stable and up to date.  I haven't used "wine-staging".  Ubuntu's wine is usually out of date.  
If you use "wine-devel", just be sure to make note of where it gets installed (in /opt/) and modify connections and triggers as needed for wine and winecfg and Mono and Gecko.  

The Ubuntu Studio webpage has some out of date info too.  So realise that some stuff is currently better than it was.  
However, always read the Release Notes for Known Issues and any bugs or significant compatibility stuff or changes.  

If you do that, you shouldn't have any problems.  
Also, it's worth reading up on how to do an offline install of .DEB files via Synaptic Package Manager and/or apt-get.  
If you always have a good strong internet connection you probably won't need that, but if you don't always have your own personal wifi or ethernet internet connection, that's useful for downloading to USB drive on somebody else's system.  

Here's the main link I made here for some tips on getting a faster-resonding Ubuntu Studio if you want to compose music.  
The main tips of PulseAudio configuration make PulseAudio useful for pro audio with a USB Class Compliant audio hardware soundcard and MIDI controller.  
[https://ubuntuforums.org/showthread.php?t=2309922](https://ubuntuforums.org/showthread.php?t=2309922)

Good luck.  
These are good days to be using Linux.  
Peace be with you.

---

### Post by norafaithrainbow on 2017-03-04
> **howefield said:**
> You should be able to move the panel in Ubuntu Studio. 

Can't quite remember but it might be right click on an empty part of the panel, select panel properties > unlock and then grab the left edge of the panel and drag it down. If I got that wrong I'm sure someone will come along and correct it but in any event I'm sure it is doable.

I will have to try that. I recently had to reinstall ubuntu because I tried installing windows (If I could avoid it I would) and the windows installer glitched and wiped my data (I didn't have that much on my computer so it's no big deal. That was the first and last time I didn't make a special ntfs partition for windows). I will be reinstalling ubuntu studio.

---

### Post by norafaithrainbow on 2017-03-04
I've tried installing wine. It just doesn't launch.

---

### Post by yoshii on 2017-03-05
> **norafaithrainbow said:**
> I've tried installing wine. It just doesn't launch.

it takes wine a long time to run during the first launch since install or boot.  give it time and watch the drive's activity light.  
also, when you select an EXE to run, you have to first choose "Wine Program Loader" to set it to run EXEs.  And MSIs need to be run via $ wine start "thisprogram.exe".  

Also, a detail which is often left out:

When you need to select something to run, do [show all files] as well as [show hidden files].  And after you select the EXE to run, make sure that the .desktop file's command syntax looks like this:  wine "thisprogram.exe"

The tricky thing, is when you first browse for an EXE to run, Linux doesn't show them because they aren't Linux executables.  So you have to toggle the menu at the bottom right of the file browser to show ALL FILES.  After that, EXEs will show up in the list for that session and you can select them.  But be sure to edit the command syntax as follows...  Quotation marks are needed every time, especially if there's a space or wierd character in the file name or folder path.  

If you edit thisprogram.desktop, it should look something like this:  
```

[Desktop Entry]
Version=1.0
Type=Application
Name=thisprogram
Comment=thisprogram
Exec=wine "/home/yourusername/.wine/drive_c/Program Files (x86)/thisprogramfolder/thisprogram.exe"
Icon=agave
Path=
Terminal=false
StartupNotify=true

```

Be sure to include the double quotation marks and delete any single quotation marks unless they are literally in the folder or file name.  
I hope this helps.  

Not all Windows programs work with Wine.  But [http://winehq.org](http://winehq.org) is the place to get the best support for wine, not from here.  WineHQ is where the makers of wine hang out and provide support and documentation.  

Also, Wine functionality depends upon which version you install and if it's compatible with whichever version of Linux you installed.  The specifications matter.  
Good luck.

---

### Post by norafaithrainbow on 2017-03-15
> **yoshii said:**
> it takes wine a long time to run during the first launch since install or boot.  give it time and watch the drive's activity light.  
also, when you select an EXE to run, you have to first choose "Wine Program Loader" to set it to run EXEs.  And MSIs need to be run via $ wine start "thisprogram.exe".  

Also, a detail which is often left out:

When you need to select something to run, do [show all files] as well as [show hidden files].  And after you select the EXE to run, make sure that the .desktop file's command syntax looks like this:  wine "thisprogram.exe"

The tricky thing, is when you first browse for an EXE to run, Linux doesn't show them because they aren't Linux executables.  So you have to toggle the menu at the bottom right of the file browser to show ALL FILES.  After that, EXEs will show up in the list for that session and you can select them.  But be sure to edit the command syntax as follows...  Quotation marks are needed every time, especially if there's a space or wierd character in the file name or folder path.  

If you edit thisprogram.desktop, it should look something like this:  
```

[Desktop Entry]
Version=1.0
Type=Application
Name=thisprogram
Comment=thisprogram
Exec=wine "/home/yourusername/.wine/drive_c/Program Files (x86)/thisprogramfolder/thisprogram.exe"
Icon=agave
Path=
Terminal=false
StartupNotify=true

```

Be sure to include the double quotation marks and delete any single quotation marks unless they are literally in the folder or file name.  
I hope this helps.  

Not all Windows programs work with Wine.  But [http://winehq.org](http://winehq.org) is the place to get the best support for wine, not from here.  WineHQ is where the makers of wine hang out and provide support and documentation.  

Also, Wine functionality depends upon which version you install and if it's compatible with whichever version of Linux you installed.  The specifications matter.  
Good luck.

I am going to have to try this. Thank you, I have been dying to try it, but I always came across that same problem.

---

### Post by gbk2 on 2017-03-19
I used Mint 17 for about 3 years. I have a big trouble after upgrading blender to 2.78c - it crashes after RMB - very often used click. The problem doesn't occur with either blender 2.69 nor 2.75. I tried to upgrade drivers for Radeon HD 6730M but it crashed completely x-server. So I consider to replace Mint 17.3 with Ubuntu Studio 16 with blender as one of flag graphic tools. Which version of blender is on-board there? May I expect the same problem with blender upgrading? I use laptop with integrated Radeon - not excellent but not bad up to now - not going to change.
Any help or guidelines appreciated.
Greg

---

### Post by Jay_Bowles on 2017-03-25
> **norafaithrainbow said:**
> I will have to try that. I recently had to reinstall ubuntu because I tried installing windows (If I could avoid it I would) and the windows installer glitched and wiped my data (I didn't have that much on my computer so it's no big deal. That was the first and last time I didn't make a special ntfs partition for windows). I will be reinstalling ubuntu studio.  It is usually best to install Windows first when you want to "dual boot" as Windows doesn't play nicely and does'nt recognise Linux. Make sure you turn Hibernation off and quick boot in windows and repartition your drive within windows to provide space for Ubuntu studio. Then install away!!  Actually I dual boot with Windows as there is software I use a lot that is only available for that platform. By the way if you are into digital art you must check out Krita; it's an awesome raster painting program.

---

