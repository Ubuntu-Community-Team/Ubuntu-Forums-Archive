---
title: "Please help me find my VST with Reaper"
date: 2010-04-17
forum: Ubuntu Studio
---

### Post by lordofmiscreation on 2010-04-17
----If anyone has experience with this particular installer would be GREATLY, GREATLY appreciated.  The short of it is I can find the folder my VST is installed in, I can see it, I just can't get Reaper to recognize it.

----I recently upgraded to UbuntuStudio 9.10 and I previously had gotten almost all of my VST's up and going in Linux Mint, Puppy Linux, and Ubuntu 9.04, including the executable's under wine. I know I can get the easy one's, the plain ol .dll's up and running seconds by creating a folder in the .local/reaper, but I always have to spend 20 hours trying to locate the applications you have to install with wine. I've tried 20 different things with 20 different directories.

----First off I know LinReaper installs everything in your .local file, including the .wine file your preference's will automatically point to when you click add directory. (FYI for anyone who has not found it, if you need to install a custom theme, lame mp3 codec, you'll need to do so in "Reapers Home File" which is the .local folder) I've tried that and it didn't work, I've tried using the (z: directory and listing the entire pathway to regular wine directory

z:home/testprofile/.wine/dosdevices/c:/Program Files

----and the c:/Program Files

z:/home/testprofile/.local/reaper/.wine/drive_c/Program Files

----which is the .wine in the . local...lol and the c:/Program Files in that folder

----Something so simple, lol, is there a command I can write to create a link between reaper and the the VST .dll stored in the .confic file, I did try several variations of creating that pathway as well (.config is where LinReaper can install the vst application and stores the .dll by default for anyone whoe needs to find it)

/home/testprofile/.config/reaper/vst

----How do I create the symbolic link inside of LinReaper's VST folder to any existing VST collection and have Reaper automatically recognize it so that I can have a consistent method of running these applications when it's time to upgrade my OSX?  I guess I should clarify, I was sure to direct Reaper preferences to the exact location I installed the VST, but that elusive son of a bitch just would not show up.

I posted this question under a wine forum, but I thought I would put one here because of this one is dedicated to my operating system I promise I'll modify or delete so as not to overload the server, thanks

---

### Post by sgx on 2010-04-17
from my wine based Reaper,

Hi, you are the boss in linux, you put your vsts where you want them, and you want them here:

/home/username/.wine/drive_c/Program Files/Steinberg/VstPlugins

so create those folders, most installers will put the .dll files in VstPlugins,
and support/data folders nearby, according to their own whims.

The path I mention is required by some (not all) plugins, and their installers.
Installers may put things in different places, as they are designed, but that path has the locations in place for installers to find them.
You&#314;l find Zebra, Native Instruments, and IK Multimedia at various places on that path, if you install their products.

Remember to install wineasio, and run

regsvr32 wineasio.dll

wineasio can then be chosen in Reapers preferences -> device panel

scanning is imperfect in reaper, sometimes you will need several
attempts to complete the scan, some vsts can stop it in it´s tracks, so
you need to start reaper again, to finish scanning, be prepared to be flexible.

any voids in a wine commandline nead to be filled with a *
as in cd /home/you/drive_c/Program*Files

many installers have a few such voids to fill in.

Don´t put extra collections of vsts where you need to have root access,
a filemmanager set up in 2 windows, or dual pane, like konqueror, nautilus, pcmanfm, dolphin etc has the options of move, copy, or link,
when you drag that VstPlugins folder somewhere where you have full read-write access, just choose the link option. I put that VstPlugins link in 
/home/username to ease maintenance, and for other vsthosts like Cantabile, that don´t require ´scanning´ for vsts like Reaper does.

You can´t mix-and-match root-user with normal-user, so all wine related things should be done as normal user, Reaper being one of them. Or, if
certain critical audio things only work  as root, you can install wine again as root, and run your whole session as root, some security warnings do apply in that scenario. Don´t be doing shady downloads yada yada yada

Dual-booters with XP, can use linux ntfs-3g to have read/write/ access to their windows partition vsts, linking them to their linux equivalents. This can save lots of disk space, since many popular apps, like Wusikstation and Kontact come with vast libraries of samples.

Hope some of this helps.
Cheers

also, some plugins that fail to scan in Reaper, work in Cantabile, EnergyXT2 or MU Lab, so I put them, and duplicates of my smaller my goto-plugins in /home/username, since hard-disk space is cheaper than time and labor!

---

### Post by lordofmiscreation on 2010-04-17
Thank you sir
Just to let you know your efforts were not wasted, I am writing up some step by step instructions should I ever need a reference, complete with hard copies, I really appreciate your response.  

I figured out where I was making my mistake and it involves how LinReaper installs Reaper.  It isolates the entire application in the .local file, including and instance of .wine which by all appearances is completely independent of the wine application which appears in your ubuntu menu. 

My mistake was not using the LinReaper script to install my commercial VST's, which from what I can tell is the only way to create a relationship between Reaper and your app.  In Mint and Puppy I used an inconsistent method of installing them, and if I remember right I just right clicked  the window the .dll was located, opened the properties, and copied the locating into Reaper preferences.  Somehow it worked and I don't know why.  So this time I tried the same thing and when I installed them, I tried quite a few locations with nothing doing, most of them in the normal .wine, the .config, and .local/reaper/vst (the hidden folders in the home file directory).  The trouble is Reaper just doesn't understand these pathways, I think because it can't find the data files associated with the .dll.  

A consistent method
1.Navigate your way through the main menu to multimedia and open LinReaper options.  
2.Go to plug ins, use the options "Install a new plug in using windows installer", load the file and hit execute 
3.It should start the wizard, and accept installation in the default location, which in this case is C:\Program Files\Stringer.  When you open the Reaper preferences, this is the C drive Reaper can see.  The actual location of this file in your linux system is 

/home/****your user name goes here****/.local/reaper/.wine/drive_c/Program Files.  

You need to know this because since Reaper is isolated, there is no way to uninstall an application should you need to, in fact I've had a hard time with upgrades because they can't find home.  I believe if you need to, you can simply delete these files and re-install them, however you may need to edit the registry before you do so.

For my future reference, when it asks where you want the data installed, accept the default location.  If it asks you where you want to install the .dll, open notepad and copy the location.  LinReaper should then create a happy marriage between the two files and everything should be up and going in minutes.

C:\windows\profiles\****your user name goes here****\My Documents\.config\reaper\vst

The actual directory in your linux system is

/home/****your user name goes here****/.local/reaper/.wine/drive_c/windows/profiles/****your user name goes here****/My Documents/.config/reaper/vst

Sorry for the trouble, after all day of trying I just needed a little sleep and a moment of clarity for it all to come together.  I'll do my best to contribute to this forum and operating system and I thank everyone because Ubuntu Studio is exactly what I have been looking for.

---

### Post by lordofmiscreation on 2010-04-17
I'm going to start a quick thread about the Behringer UCG102 if anyone knows about this device

---

