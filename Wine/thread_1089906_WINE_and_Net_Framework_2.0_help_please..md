---
title: "WINE and Net Framework 2.0 help please."
date: 2009-03-07
forum: Wine
---

### Post by Mashuteichou on 2009-03-07
I recently started using Ubuntu, and I downloaded WINE last night. I also Downloaded 3 different installs of Net Framework 2.0. Neither worked, stopping at the same point of install. Basically, it starts configuring the installs, then it just pops up with an Microsoft Error Report. Like in Windows XP when a program freezes.

There is no code in the report, it just says whats being sent. I downloaded the 1.1 version, and that loaded fine I believe. It said it loaded fine, but we know how that works.

So, what do I do? I tried 3 different downloads with the same problem, and I need the 2.0 for the games I need. They won't load till Framework is loaded.

How do I do this?

---

### Post by cogadh on 2009-03-07
Use [winetricks]("http://wiki.winehq.org/winetricks") to install .NET.

---

### Post by Mashuteichou on 2009-03-07
I loaded Winetricks, started the dotnet20 download for the framework, but I accidently cancelled it.  Then I restarted into windows XP for something I forgot about, went back into Ubuntu, and now it won't load the file.  It keeps saying to rename it.  yet when I rename it, it can't find it.  

I assume that it partially downloaded and got corrupted.  How do I fix this?

---

### Post by Meow27 on 2009-03-08
the simplest solution is to delete your .wine folder and start everything you did on wine all over again (removing the package is unnecessary it the folder will come back when use use an .exe again)

just remember keep this as a last resort

or reinstall both wine and wine-tricks

---

### Post by Mashuteichou on 2009-03-08
> **Meow27 said:**
> the simplest solution is to delete your .wine folder and start everything you did on wine all over again (removing the package is unnecessary it the folder will come back when use use an .exe again)

just remember keep this as a last resort

or reinstall both wine and wine-tricks


Ok, first, where is the wine folder?   Sorry for the noob question, still getting used to Linux from Windows.   >_>  

I deleted Wine from the Add/Remove part, and it had 2 installs of my game, plus 2 installs of Framework 2.0, then 1 install of the other stuff I loaded.  When I tried to uninstall my game, it kept popping up "C+++ Library" or something.  Basically it couldn't find the file of the Framework.  Then I deleted the Net Framework, and I had to hit the same error message about 30 times before it deleted.  

I tried the Sudo Apt-get remove --purge winetricks, I believe thats how it was, but that didn't work.  So I deleted the winetricks cache file I believe in the Home folder.  Then I redownloaded Winetricks with the terminal because the site wouldn't work for me, and it loaded like the first time. 

Then, I did the downloads the site says, then I put in "sh winetricks dotnet20" in the terminal, and here's the summary:

----------------------------------
Setting Windows Version to Win2K

Executing wine regedit /home/phantom/.wine/drive_c/winetrickstmp/set-winver.reg

Executing cp -f /home/phantom/.winetrickscache/dotnet20/l.intl.nle /home/phantom/.wine/drive_c/windows/syystem32/

shalsum mismatch!  Rename /home/phantom/.winetrickscache/dotnet20/dotnetfx.exe and try again
 ----------------------------------

(I retyped it so if theres any mistakes, its my fault)

Then if stops the loading and the terminal goes back to normal, ready for a command.

When I go to the home folder, click on the wintrickcache and open in text editor, what do I change there, or do I change anything there?   Obviously its a file and not a folder, so I can't open the dotnet20 part and change the name of the exe file.  

So what do I do?   

I also downloaded 2 different downloads from Microsoft and they won't load.  They come up with runtime errors and library errors, etc.  Even after I reinstalled Wine.   Now, the funny thing is, I thought I would try the 1.1 Framework, and it ran fine.

---

### Post by cogadh on 2009-03-08
First off, you need to stop trying to solve this with a shotgun. You have done so many different things at the same time, that even if we can resolve your .NET issue, you will likely have other issues that you have now created. You need to do some cleanup to get things back to baseline state, so we can start fresh with .NET.

[list=1]

[*]Delete the .wine directory. This directory is a hidden directory in your home directory, so in order to see it in the file browser, you will need to press CTRL+H to show hidden files. Alternatively, you can delete it using the terminal by simply typing "rm -rf ~/.wine".

[*]Delete everything associated with winetricks, including the .winetrickscache directory (again, a hidden directory) and all of the MS downloads you have done. None of those files you downloaded manually from MS are going to install anyway, so don't bother with them again at all.

[*]After you have deleted everything, run winecfg to create a new .wine directory. DO NOT DO ANYTHING ELSE TO WINE AT THIS POINT.

[*]Download winetricks again and run "sh winetricks dotnet20"
[/list]
At this point, .NET should be installed properly. If you run into problems, rather than trying random solutions, post your questions here first. I can tell you that you will already likely have a problem with your menu shortcuts not appearing anymore. If that happens, there is a solution, but rather than muddy the process with this right now, lets work on getting the initial problem fixed first.

---

### Post by Mashuteichou on 2009-03-08
> **cogadh said:**
> First off, you need to stop trying to solve this with a shotgun. You have done so many different things at the same time, that even if we can resolve your .NET issue, you will likely have other issues that you have now created. You need to do some cleanup to get things back to baseline state, so we can start fresh with .NET.

[list=1]

[*]Delete the .wine directory. This directory is a hidden directory in your home directory, so in order to see it in the file browser, you will need to press CTRL+H to show hidden files. Alternatively, you can delete it using the terminal by simply typing "rm -rf ~/.wine".

[*]Delete everything associated with winetricks, including the .winetrickscache directory (again, a hidden directory) and all of the MS downloads you have done. None of those files you downloaded manually from MS are going to install anyway, so don't bother with them again at all.

[*]After you have deleted everything, run winecfg to create a new .wine directory. DO NOT DO ANYTHING ELSE TO WINE AT THIS POINT.

[*]Download winetricks again and run "sh winetricks dotnet20"
[/list]
At this point, .NET should be installed properly. If you run into problems, rather than trying random solutions, post your questions here first. I can tell you that you will already likely have a problem with your menu shortcuts not appearing anymore. If that happens, there is a solution, but rather than muddy the process with this right now, lets work on getting the initial problem fixed first.


Ok, I believe everything is running correctly now.  I tried deleting just winetricks, then reloading it, and it seemed to work.  I downloaded Framework 1.1 first, then loaded 2.0, and everything ran just fine.  

Then, I loaded my game, which is Fiesta from Outspark, and it loaded fine, till I opened the game.  The initial loader pops up, then looks slightly odd at the login section.  And a message that says, "errmsg" in a small window, then an "ok" button.  If I hit that, the loader closes.  

And I can't type anything in the login part, partly because of the error message, and partly because its not quite normal.  Part of it has a grey bar over it.  

So, now that the first problem is fixed, how do I fix this?  Or can I?

---

### Post by cogadh on 2009-03-08
I wish you had said something about the app you are trying to run sooner. Fiesta is not know to run in Wine at all:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=6483](http://appdb.winehq.org/objectManager.php?sClass=application&iId=6483)

However, it hasn't been tested recently, so if you want to experiment a little, you might have some success. Run the game from the terminal and post Wine's output here. Wine will produce a lot of error messages in the terminal which may explain what is happening. To run the game from the terminal, open a terminal, change directories to the game's install location, then "wine" it:
```
cd .wine/drive_c/Program\ Files/<path to game>
wine <game executable name>.exe
```

---

### Post by Mashuteichou on 2009-03-08
> **cogadh said:**
> I wish you had said something about the app you are trying to run sooner. Fiesta is not know to run in Wine at all:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=6483](http://appdb.winehq.org/objectManager.php?sClass=application&iId=6483)

However, it hasn't been tested recently, so if you want to experiment a little, you might have some success. Run the game from the terminal and post Wine's output here. Wine will produce a lot of error messages in the terminal which may explain what is happening. To run the game from the terminal, open a terminal, change directories to the game's install location, then "wine" it:
```
cd .wine/drive_c/Program\ Files/<path to game>
wine <game executable name>.exe
```

Im sorry, please bare with me, Linux is still new to me.

I know what you mean by path, but how do I find it?    

When I open my computer part, it comes up with all the partitions, just not labled with a drive letter.  I am pretty sure the Ubuntu files are under the one that says "Filesystem", but when I go there, theres no program files.

Which would then leave me to believe its in the XP folder, which is the only OS I have that has that folder, as far as I know.   

I know Im all over here, so when WINE loads a program, it goes to the XP partition by default?  Or am I reading that wrong?

When I typed in the file path, it said the file or directory isn't found.  I tried it different ways.  I even viewed the properties of the icon on the desktop, which led to the exe file, and that didn't work.   What am I doing wrong?

Here is the path:  

C:\Program Files\Outspark\SharpLauncher\OutsparkLauncher.exe

Thats what the shortcut says.   But in the Computer, its under disk1.  Does that matter?  

When I find it in the folder, the path is:

/media/disk-1/Program Files/Outspark/SharpLauncher

I tried both of these.  It is highly possible I am doing this wrong.  

Here is what I typed in the Terminal:

cd .wine/drive_c/Program\ Files/C:/Program Files/Outspark/SharpLauncher/OutsparkLauncher.exe

and  

cd .wine/drive_c/Program\ Files/media/disk-1/Program Files/Outspark/SharpLauncher

In short, they both said no such file or directory.

I tried different variations to these, and I just noticed you already typed part of it out.  Sorry.  So, it would be, 

.wine/drive_c/program files/Outspark/sharplauncher/outsparklauncher.exe. 

Which said no directory as well.  

Sorry for the long post and delay between them.   And thanks for the help.

---

### Post by Mashuteichou on 2009-03-08
Ok...well, I figured it out with one of the many different combinations I tried.  It was alot shorter then I thought it was supposed to be.   >_>

Ok, so now in the terminal, it says ~/.wine/drive_c/Program Files/Outspark/Fiesta$

What do I type for the exe?  Just Fiesta.exe doesnt work.  Do I need the path?

When I type in,  Wine Fiesta.exe, it says C:\\Windows\\system32\\Fiesta.exe : Module not found

---

### Post by Mashuteichou on 2009-03-08
I keep answering my own posts.   ^_^  I didn't think that capitals made a difference, but I guess it does.  I will be more careful from now on.

Ill post what came up in an edit.

fixme:virtual:NtAllocateVirtualMemory MEM_WRITE_WATCH type not supported
fixme: ole:CoGetContextToken stub
fixme:shell:URL_ParseUrl failed to parse L"System"
fixme:shell:URL_ParseUrl failed to parse L"System.Windows.Forms"
fixme:shell:URL_ParseUrl failed to parse L"System.Drawing"
fixme: ole:CoGetContextToken stub
fixme: ole:CoGetContextToken stub
fixme: ole:CoGetContextToken stub
fixme: ole:CoGetContextToken stub
fixme: ole:CoGetContextToken stub
fixme: ole:CoGetContextToken stub
fixme: ole:CoGetContextToken stub
fixme: ole:CoGetContextToken stub
fixme: ole:CoGetContextToken stub

(Space was because of happy face icons.)

---

### Post by CGANIERE on 2009-03-08
I didn't want to start a new thread. This is off topic.
I am using Ubuntu 7.10 I 
It won't let me install Wine for two reasons:
wine:
 Depends: libldap-2.4-2 (>=2.4.7) but it is not installable
  PreDepends: dpkg (>=1.14.12ubuntu3) but 1.14.5ubuntu16 is to be installed
Is there a way around this? 
I want to run Magic the Gathering Shandalar and other classic PC games from the 90s
If possible I'd like to run Revit Architecture 7.0 (by autodesk) under wine

---

### Post by cogadh on 2009-03-08
@CGANIERE
Start your own thread or find another where this is actually on-topic. Hijacking threads with unrelated problems is rude.

@Mashuteichou
I hate to say it, but you might be SOL on this. The "fixme" messages are developer notes about incomplete or unimplemented functions in Wine. Generally speaking, there is no way to correct them until Wine develops further or if you feel like coding a patch for Wine to address them. Most apps run with Wine will encounter a few of them and still work anyway, but unfortunately, the "fixme" messages you got would seem to indicate to me that Wine just can't do what Fiesta needs it to do.

---

### Post by bdws1975 on 2009-12-30
Hi all,

I'm having an issue as well with winetricks.

I've followed all the above steps and keep getting to the same end point.

I'm attaching a screenshot in hopes that someone can help.

My end goal is to install office 2007.

Thanks,
Brett

---

