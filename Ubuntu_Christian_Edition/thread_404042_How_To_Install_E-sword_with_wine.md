---
title: "How To Install E-sword with wine"
date: 2007-04-07
forum: Ubuntu Christian Edition
---

### Post by david_kt on 2007-04-07
[COLOR="Red"]WARNING: DO NOT run below installer with sudo or as root[/COLOR]
[B][U]
Installation[/U][/B]
**1. Install Wine**
First, use wine stable (1.0.1) as some users reported latest wine is not compatible with e-Sword 9.6.0. You could upgrade wine after installation is completed.

**2. Install cabextract**
```
sudo apt-get install cabextract
```
**3. Download [e-Sword_installer_301011.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=205873&stc=1&d=1319983063") and then extract it. Double click on e-Sword_installer extracted to run it.**

If it fail to execute, make sure it is executable (right click on the extracted file (e-Sword_installer) >> click properties >> click permision tab >> and then tick on the execute (allow executing file as program).

**4. Install other addon **
If the addon you want to install is not in the installer, please download from windows file first. After that, run the e-Sword_installer and tick manual option (no. 4 from the top). It will open a browser for you to locate your addon, select that file and click ok to install.
[B]
5. Font Smoothing[/B]
As fedback and tested by David Devonshire, I added font smoothing script.[LIST]
[*]Download [font_smoothing_050409.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=108759&stc=1&d=1238927243") and extract it.[*]Double click on the extracted file (font_smoothing) and choose **_RUN IN TERMINAL_**. [*]Select option 2, 3, or 4 and then <ok>. [*]Launch e-Sword and see the different.[*] Play with option 2,3, or 4 until you like it best
[/LIST]

That's it, very simple. **You do not have to read further**, unless you want to install e-Sword Portable, refine your installation, or study the script.
===========================================================================
**e-Sword Portable**
I have added e-sword portable. After you install e-sword using this instruction or installer, and you have satisfied with the result, you could make e-sword portable:
1. Download [e-sword_portable251008.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=89577&d=1224921664").
2. Extract it and you will have 3 scripts.
3. Copy those 3 scripts to root folder of any usb.
4. double click "create_e-Sword_Wine_portable" on the usb and choose "run in terminal", it will open menu. You could choose to create e-Sword portable only, but now there is a choice to create wine-1.0 portable to your usb.

=======================================================================
[COLOR="Red"]WARNING:
1. You have to run "sudo apt-get build-dep wine" before you could install wine-1.0 portable.
2. Creating wine-1.0 portable takes about 45 minutes, depending on your computer speed.
3. Wine-1.0 portable is not required for e-Sword portable, it is just an option.[/COLOR]
========================================================================
Now you have two launcher:
1. "e-Sword_portable_launcher", for host with wine installed, and
2. "e-Sword_portable_wine_launcher",for host without wine installed.

To run e-sword on any linux desktop, run "e-Sword_portable_launcher" on the root folder of your usb. If it complains there is no wine, you could try to run "e-Sword_portable_wine_launcher" utilizing wine-1.0 on your usb. If wine-1.0 dependencies are satisfied on that computer, it would run without wine installed.

It has been tested using host computer with wine 0.59 and wine 1.0. It should be able to run on any wine version above 0.59. 
The portable wine has been tested with wine removed (but dependencies not removed).

========================================================================================

Changelog:
- Add option to choose stable or release candidate e-sword ( 30/10/11 )
- Add back manual install for executable ( 30/08/11 )
- Bug fixed for search function ( 18/05/11 )
- Has to include www for wget, otherwise it fails to download ( 29/04/11 )
- Change layout of download page for addons ( 26/02/11 )
- Change layout of download page in e-Sword ( 03/01/11 )
- Now will download latest version of e-Sword, not hard-coded to any version ( 10/10/10 )
- Update to e-Sword 9.6.0 ( 24/04/10 )
- Include support for other languages OS and ensure there is desktop launcher ( 12/11/09 )
- Update to e-Sword 9.5.1 ( 11/09/09 )
- Enable multiple manual and added addons ( 13/08/09 ) 
- Update to e-Sword 9.0.3, bug fixed to upgrade from old e-Sword but almost all modules could NOT be converted, update wine to wine 1.1.23. ( 07/06/09 )
- Bug fixed for manual option to execute from directory name with space in it ( 12/05/09 )
- Add Day-By-Day By Grace (Bob Hoekstra) ( 11/05/09 )
- Change main program to e-Sword 9.0.1 ( 07/05/09 )
- bug fixed for download progress bar and add font smoothing ( 05/04/09 )
- Add Treasury of Scripture Knowledge (TSK) ( 12/01/09 )
- Change main program and updater to e-Sword 8.0.6. Add Indonesian and Vietnamese Bible. ( 02/01/09 )
- Check for wine 1.1.7 and offer a choice to terminate program or to continue if find other wine version. ( 23/11/08 ) 
- Change main program to e-Sword 8.0.5, add updater to update from old e-Sword, and add new feature "localizer". Separate "add desktop launcher" script as recent wines could create desktop launcher. So, this script might not required by some of you. (21/11/08 )
- added gui progress bar for wine-1.0 portable installer and bug fixed to run on puppy linux live cd
- added uninstaller and progress bar GUI for e-Sword installer, remove beta version as it disappears from the web. ( 12/10/08 )
- wine-10 portable to accompany e-Sword portable. (10/10/08 )
- automatic backup and restore is available on installer. (06/10/08 )
=============================================================================

**Explanation of the Installation Script**

Lukeelliot reported that addons would only show blue screen ON KUBUNTU/KDE (and I can confirm that), but what you have to do is just press enter until it completes installation. If you run it in terminal, it will inform that the installation of addon completed. Anyhow, it is still working as normal in ubuntu/gnome.

Ng Oon-Ee reported that on Intrepid RC he experience blue screen problem as well (not confirmed by me yet as I am still runnning hardy). But it could be solved by just press enter until it complete installation or disable compiz to make the addons installer run as normal.

The installer attached would do the following:
1. Download and install latest e-Sword 
2. Copy riched20 to correct location
3. Download msls31.dll from Microsoft website
4. Set dlloverrides for riched20 and oleaut32
5. Download mfc42.dll from Microsoft website
6. Install additional bibles and classical bible map, of your choice
7. Install other addon already downloaded (tick manual option), it will open a browser for you to locate your addon, select that exe file and click ok to install. It also could be used to run e-Sword update, if e-sword installed using below instruction or using this installer.

All are done in special prefix (.wine_Esword).

You have to install cabextract for this installer to work:

```
sudo apt-get install cabextract
```

After that, download Esword_installer.tar.gz and then extract it.
Double click on Esword_installer to run it. If it fail to execute, make sure it is executable (right click on the extracted file (Esword_installer) >> click properties >> click permision tab >> and then tick on the execute (allow executing file as program).

To install other addons, tick/select manual on the menu pop up when you run esword_installer and navigate to the downloaded addon. If you want your favourite addon to be included for automatic installation, please let me know.

You could use this instruction and installer theoretically in any distro running wine, not just ubuntu. Some users have tried it successfully on Mepis and Puppy linux as well.

After successfully install e-Sword and addons, you should continue reading "Change icon on installer" section onward on manual instruction below to learn how to get full benefits of e-sword running on wine.

===============================================================

**Alternative installation (manual installation)**
(you could choose to install it automatically by downloading and running the attached installer. Below instruction is only needed if you want to do it manually and you can skip to "Change icon on installer" section and please read further to learn how to get a full benefit of e-sword running on wine)
 

**You could download the program and other addons here:**

[http://www.e-sword.net/downloads.html]("http://www.e-sword.net/downloads.html")

**Create "wineprefix" for Esword (for newer wine you could skip this step):**

```
wineprefixcreate --prefix .wine_Esword 
```

**Install the program:**

Make sure the setup951.exe is in you home folder. Otherwise, you should cd to the location first, for example "cd Desktop" if the setup903.exe is on your Desktop.

```
 env WINEPREFIX=~/.wine_Esword wine setup951.exe
```

_Download msls31.dll_ to your ~/.wine_Esword/drive_c/windows/system32 from here:

[http://www.dlldump.com]("http://www.dlldump.com")

(Search msls31.dll and download it. If you download it somewhere else, you need to copy it to  ~/.wine_Esword/drive_c/windows/system32)

[COLOR="Red"]Note: the automatic installer download msls31.dll from microsoft, which is much safer.[/COLOR]

[U]
Copy riched20.dll[/U] from ~/.wine_Esword/drive_c/Program Files/e-Sword to  ~/.wine_Esword/drive_c/windows/system32


```
 cp ~/.wine_Esword/drive_c/Program\ Files/e-Sword/riched20.dll ~/.wine_Esword/drive_c/windows/system32

```

Make sure all the above dlls in lower case. If they are in upper case, rename them to lower case.

In winecfg set riched20.dll and oleaut32.dll to native. IMPORTANT: _Do not run winecfg from menu_, as it would run default winecfg. Please use terminal to run winecfg for this bottle:

```
env WINEPREFIX=~/.wine_Esword winecfg
```

Press the Libraries tab > type riched20.dll > press add > press edit > choose Native (windows).
Do the same for oleaut32.dll.

Use winetricks to install mfc42, otherwise, e-Sword 951 would not run.

Type: 

```
 env WINEPREFIX=~/.wine_Esword wine "C:\Program Files\e-Sword\e-Sword.exe"

```

to run it. Or, you could use the launcher (if successfully created) on desktop.

**To install addons, run in terminal:**

Make sure the bbe.exe is in you home folder. Otherwise, you should cd to the location first, for example "cd Desktop" if the bbe.exe is on your Desktop.

```
 env WINEPREFIX=~/.wine_Esword wine bbe.exe
```

If it shows only blue screen, press [alt+tab] to switch to installation windows. You may need to press [alt+tab] again every time after you press next. In KDE, it might show only blue screen, just press enter and enter until it is completed.

The above example is to install bbe.exe. You could install other addons using above overrides, just replace bbe.exe.


**Change Icon on Launcher.**
The launcher created already use e-Sword icon. But if you want to use other icon, follow below step:
Right click the launcher and choose properties.
After that click on the wine icon, it will open a windows.
Navigates to the icon file you want.
If the icon you want did not appear in the navigation windows, change the extension to png.
You could download and use attached 2 icons as well (original e-sword icons) if you like.

[B]
Add more fonts[/B]
To add more fonts, copy whatever fonts you have to ~/.wine_Esword/drive_c/windows/Fonts or ~/.wine_Esword/drive_c/windows/fonts.

(Please check whether the fonts directory is with capital F or lower case f(i.e. ~/.wine_Esword/drive_c/windows/Fonts or ~/.wine_Esword/drive_c/windows/fonts. Some version of wine use Fonts and some use fonts, not sure which is which).

If it still not appear in e-sword, it might be due to file permission problem. What you have to do is to open terminal (application>accesories>terminal), and then issue below command:

```
chmod 777 -R ~/.wine_Esword/drive_c/windows/Fonts or
chmod 777 -R ~/.wine_Esword/drive_c/windows/fonts 
```


The fonts should now available for E-sword to use.

**Increase font size for E-sword menu**
If you find e-Sword application font itself (ie. the font for "menu, edit, format, etc")  is too small, what you can do is:

Open terminal (Application>Accesories>Terminal)
Open wine configuration editor from terminal:

```
 env WINEPREFIX=~/.wine_Esword winecfg
```

Click graphics tab.

At below, there is a screen resolution slider, the default is 96 dpi. Slide the slider to higher dpi. Be carefull though to use too big value as GlennW reported the winecfg become to big to fit to the screen when he use maximum value (120 dpi). Click apply and then ok. 

Open your e-sword, if it is too big, you could repeat the above steps, adjusting the slider to whatever number (between 96 to 120).

**Troubleshooting**
If you encounter a weird problem, possibly there are some wine processes in the memory. To get rid of these processes, you could
1. reboot your computer,
 or
2. kill wine related processes using system monitor:
From menu: system >> Sytem monitor >> click "processes" tab.
Kill all processes related to wine, including all exe processes.
 or
3. Open terminal, and run below command (one at a time):
```
killall wine
killall wineserver
killall wine-preloader
```

If there is no launcher in the desktop:

1. Normally it is still avialable from the menu. Go to menu:

Application> Wine> Program > e-Sword > e-Sword (right click on this menu and select "add this launcher to desktop"

2. Add manually. One way to make the launcher work is to use absolute path in the command:
```
env WINEPREFIX="/home/Your_User_Name/.wine_Esword" wine "C:\Program Files\e-Sword\e-Sword.exe"
```
Replace Your_User_Name with actual user name you are using.
And after that you could use the icon attached.

3. Use attached "Create_Desktop_Launhcer" sript, the easiest way.

**Backup and restore E-sword**

**Note: The installer could do below job automatically for you.**

This instruction is to backup your e-Sword installation in case your box crashed or you want to reinstall your operating system. By following this instruction, it would save you the hassle of re-installing e-Sword and you would not lose your setting or whatever work you have done on e-sword. It could also be done to replicate your e-Sword from one box to another, without the need to manually install it.

What you need to do is just copy the files and folder in the .wine_Esword folder, EXCEPT DOSDEVICES folder. i.e. you need to copy:
```

drive_c folder
user.reg
userdef.reg
system.reg
```

You also need to copy e-sword folder in your home directory:

```
~/username/e-sword
```

In addition to that, you could copy the Desktop Launcher as well.

To restore/install in new computer, what you have to do is:

Install wine (sudo apt-get install wine)

Create special bottle:

```
wineprefixcreate --prefix .wine_Esword
```

and then copy:

```
drive_c folder
user.reg
userdef.reg
system.reg
```

to .wine_Esword directory.

After that you need to create/copy the launcher. If you copy the launcher, please make sure you edit the path.

Please let me know if this instruction does not work for you.

DK

---

### Post by ardchoille42 on 2007-04-07
You could also just 
```

sudo apt-get install gnome-sword

```
to get a nice bible app in gnome

or

```

sudo apt-get install bibletime

```
to get a nice bible app in KDE.

---

### Post by david_kt on 2007-04-08
> **ardchoille42 said:**
> You could also just 
```

sudo apt-get install gnome-sword

```
to get a nice bible app in gnome
.

I tried above code:
```

sudo apt-get install gnome-sword
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gnome-sword
```

May be what you meant was: sudo apt-get install gnomesword ?

I tried it but it install very basic bible, much inferior to E-sword. Or did I miss something? Have you compared it to E-sword?

DK

---

### Post by Jinto.Lin on 2007-11-29
I've used e-sword for a long time now, and just moved to Ubuntu Studio (fully, no dual booting!) BibleTime is ok, but it does not compare to e-sword. No copy function (copy specific verses), it is buggy (crashes when you change some options) and it has no true parallel reading (you can have more than one Bible open, but they can not link.)

Thanks for the info! I'll post again when I get it to work. (Am downloading Wine now, just re-installed Ubuntu.)

~Jinto.Lin

---

### Post by Dov on 2007-11-30
I'm a pretty dedicated open-source user, but I must say that e-sword absolutely leaves for dead anything in the Linux world. Fortunately it runs flawlessly under Wine! 

The GPL would seem to fit the license requirements set by the developer of e-sword, so perhaps he could be persuaded to GPL the code?

---

### Post by GlennW on 2007-12-03
> **Jinto.Lin said:**
> I've used e-sword for a long time now, and just moved to Ubuntu Studio (fully, no dual booting!) BibleTime is ok, but it does not compare to e-sword. No copy function (copy specific verses), it is buggy (crashes when you change some options) and it has no true parallel reading (you can have more than one Bible open, but they can not link.)

Thanks for the info! I'll post again when I get it to work. (Am downloading Wine now, just re-installed Ubuntu.)

~Jinto.Lin

Indeed like a lot of people, I found, and came to love e-Sword under XP. Now that I've migrated to Gutsy, I'm interested in e-Sword running with Wine on Gutsy. I'm quite the noob so take that into consideration.  I'm very interested in knowing how you, if you were successful, got e-Sword up and running.

---

### Post by cafluegg on 2007-12-14
I got e-Sword running by following this tutorial. It works flawlessly.

---

### Post by jonathonblake on 2007-12-16
> **ardchoille42 said:**
> You could also just ...to get a nice bible app in .... 

*The Sword Project* is distinctly lacking in resources when compared to *e-Sword*. If one has built up a solid collection of e-Sword resources, then migration to another Bible Study Program is not a viable option.

*e-Sword* has a slight edge, in functionality, over *The Sword Project*. When it comes to tools for creating new resources, *e-Sword* blows *The Sword Project* away.

> **Dov said:**
> The GPL would seem to fit the license requirements set by the developer of e-sword, 

The GNU GPL violates the major premise of the e-Sword license --- distribution must be gratis. (Consider, and examine the difference between "gift economies" and "market economies", before pointing to the exceptions.)

xan

jonathon

---

### Post by cafluegg on 2007-12-22
Just thought that I would mention that this tutorial helped me to install e-Sword on churchpup (A puppy linux derivative) as well.

---

### Post by ggaines1 on 2007-12-26
trying to install esword in ubuntu 7:10,  keeps hanging on install have tried debian packag e and allows me to load all modules but wont configure, tried wine install instructions and when I get to this point /home/gregory/.wine/drive_c/windows/system32/setup785.exe
 
It hangs saying looking for location for files but box hangs and can get no farther.
any advice would be apreciated, 

I am very much a beginner to ubuntu

thanks

---

### Post by aggiedvm on 2007-12-28
I have copied the dll files and executed the E_sword program.  The program comes up but it does not have any bibles or other programs.  I have tried installing the add-ons with the following command:

root@aggiedvm-laptop:/home/aggiedvm# env WINEPREFIX=/.wine_Esword WINEDLLOVERRIDES="riched20=n" WINEDLLOVERRIDES="riched32=n" wine barnes.exe

The program then hangs with a mesage box sayihng "preparing wizard please wait"  and then nothing happens.

Any help would be appreciated.

Aggiedvm

---

### Post by jgt157 on 2007-12-31
I was able to successfully install e-Sword with your instructions from above, but when I try to set the dll's to native, the button that says add is grayed out.  I'm running wine version wine-0.9.46.  Can someone help with this?

Thanks,

Jim T

---

### Post by rgroff on 2008-01-02
I too am trying to install e-Sword with wine-0.9.46. but all I get is blank pages with no text.  I have followed the instructions carefully but to no avail.  I would like to install Ubuntu on my wife's computer but without e-Sword Ubuntu will not be used.

Please any help would be appreciated.

Ray

---

### Post by david_kt on 2008-01-26
Sorry I have not tried this installation using latest wine, but my e-sword is still working fine with latest wine.

Once I got back home I will try it using latest wine and update the instalation instruction as neccesary to suit to latest wine.

DK

---

### Post by jonathonblake on 2008-01-26
One potential issue in installing e-Sword, is that e-sword.net has been redesigned to drop/reject connections from bots, scripts, and the like.

xan

jonathon.

---

### Post by david_kt on 2008-01-26
I have checked using latest e-sword (794) and wine 0.9.53, e-sword still install without problem. In order to view it, you must make sure to add dll overrides in  winecfg as mentioned.

To add dll overrides, you need to type riched20, and then press add. If you have not typed anything yet, offcourse the add button is not active.

But I have not able to install addon as well using ubuntustudio gutsy gibbon, I will check further how to overcome this issue.

I will come back as soon as I got some solution for this other than copying the addon from windows box.

DK

---

### Post by david_kt on 2008-01-26
> **rgroff said:**
> I too am trying to install e-Sword with wine-0.9.46. but all I get is blank pages with no text.  I have followed the instructions carefully but to no avail.  I would like to install Ubuntu on my wife's computer but without e-Sword Ubuntu will not be used.

Please any help would be appreciated.

Ray

Please run 

```
env WINEPREFIX=~/.wine_Esword winecfg
```

and on library set riched20.dll and oleaut32.dll to native for e-sword.exe.
That would solve your problem. But I still could not install addon yet using gutsy.

DK

---

### Post by david_kt on 2008-01-28
sorry, double post

---

### Post by david_kt on 2008-01-28
I have edited this "how to" to solve recent problem of installing addons. The problem lies in the source of dll download. As I am not sure whether or not I could share dll legally, I have looked for a new source of dll, which I have tested it could be used.

Please refer to my first post in this thread and let me know if any of you still face some problems. You should be able to use latest wine, latest e-sword, and all addons. And you could use this how to theoritically in any distro that could run wine.

DK

---

### Post by david_kt on 2008-01-28
> **ggaines1 said:**
> trying to install esword in ubuntu 7:10,  keeps hanging on install have tried debian packag e and allows me to load all modules but wont configure, tried wine install instructions and when I get to this point /home/gregory/.wine/drive_c/windows/system32/setup785.exe
 
It hangs saying looking for location for files but box hangs and can get no farther.
any advice would be apreciated, 

I am very much a beginner to ubuntu

thanks


Ithink you use debian package in ubuntu christian. This how to does not require that package, just follow exactly as written. Oh, I forgot, you should install wine first:

```
sudo apt-get install wine
```

If it said there is no wine package, add the repository or follow below instrcution:

```
http://www.winehq.org/site/download-deb
```

DK

---

### Post by father_je on 2008-02-01
error message (Module not found msis31.dll) pls help, what will i do next, thank you very much

---

### Post by david_kt on 2008-02-01
> **father_je said:**
> error message (Module not found msis31.dll) pls help, what will i do next, thank you very much

Are sure it is msis31.dll? I thought it is supposed to be msls31.dll. Could you let me know in which step throw that error (copy and paste your terminal output if you could, including the command issued).

Make sure  you have downloaded msls31.dll from:

[http://www.dlldump.com/cgi-bin/testwrap/downloadcounts.cgi?rt=count&path=dllfiles/M/msls31.dll]("http://www.dlldump.com/cgi-bin/testwrap/downloadcounts.cgi?rt=count&path=dllfiles/M/msls31.dll") 

And copy it to ~/.wine_Esword /drive_c/windows/system32 

If you downloaded it in your home directory, open terminal and copy and paste below command:

```
cp msls31.dll ~/.wine_Esword /drive_c/windows/system32 
```

If you downloaded it on your Desktop, then you should go to Desktop first before issuing above command (cd Desktop).

After that rerun the command that give you error. Make sure other dlls are also copied to ~/.wine_Esword /drive_c/windows/system32 

Please let me know if you still have problem.

DK

---

### Post by father_je on 2008-02-01
Thank you very much, e-Sword is now running fine in our computer, to everybody who helped, thank you very very much, God Bless you all

---

### Post by david_kt on 2008-02-01
> **father_je said:**
> Thank you very much, e-Sword is now running fine in our computer, to everybody who helped, thank you very very much, God Bless you all

How do you make it run? Is it using this "generic how to" or using the deb installer? Are you able to install all modules as well?

DK

---

### Post by ChrisNZ on 2008-02-03
> **david_kt said:**
> [B]

Or you could go to direct link below:
Riched20:
[http://www.dlldump.com/cgi-bin/testwrap/downloadcounts.cgi?rt=count&path=dllfiles/R/RICHED20.DLL]("http://www.dlldump.com/cgi-bin/testwrap/downloadcounts.cgi?rt=count&path=dllfiles/R/RICHED20.DLL")

Riched32:
[http://www.dlldump.com/cgi-bin/testwrap/downloadcounts.cgi?rt=count&path=dllfiles/R/riched32.dll]("http://www.dlldump.com/cgi-bin/testwrap/downloadcounts.cgi?rt=count&path=dllfiles/R/riched32.dll")

oleaut32:
[URL="http://www.dlldump.com/cgi-bin/testwrap/downloadcounts.cgi?rt=count&path=dllfiles/O/OLEAUT32.DLL"http://www.dlldump.com/cgi-bin/testwrap/downloadcounts.cgi?rt=count&path=dllfiles/O/OLEAUT32.DLL[/URL]


Download msls31.dll to your ~/.wine_Esword/drive_c/windows/system32 from here:

[http://www.dlldump.com/]("http://www.dlldump.com/")


DK

File Links have changed... Try these

Riched20:
Version: 5.30.23.12212
Link may have changed to...
[http://www.dlldump.com/cgi-bin/testwrap/downloadcounts.cgi?rt=count&path=dllfiles/R/RICHED20.DLL](http://www.dlldump.com/cgi-bin/testwrap/downloadcounts.cgi?rt=count&path=dllfiles/R/RICHED20.DLL)

Filename: riched32.dll
Version: 5.1.2600.0
[http://www.dlldump.com/cgi-bin/testwrap/downloadcounts.cgi?rt=count&path=dllfiles/R/riched32.dll](http://www.dlldump.com/cgi-bin/testwrap/downloadcounts.cgi?rt=count&path=dllfiles/R/riched32.dll)

Filename: OLEAUT32.DLL
Version: 5.1.2600.2180
[http://www.dlldump.com/cgi-bin/testwrap/downloadcounts.cgi?rt=count&path=dllfiles/O/OLEAUT32.DLL](http://www.dlldump.com/cgi-bin/testwrap/downloadcounts.cgi?rt=count&path=dllfiles/O/OLEAUT32.DLL)

Filename: msls31.dll
Version: 3.10.349.0
[http://www.dlldump.com/cgi-bin/testwrap/downloadcounts.cgi?rt=count&path=dllfiles/M/msls31.dll](http://www.dlldump.com/cgi-bin/testwrap/downloadcounts.cgi?rt=count&path=dllfiles/M/msls31.dll)

Hope this helps everyone... will let you know how I get on

---

### Post by ChrisNZ on 2008-02-03
Hi from a "convert" to Linux, thanks for all your help.

Chris

---

### Post by cjm5229 on 2008-02-03
I have wine 0.95.4 installed, Installed eSword 795, got it working perfectly, but when I try to install the modules,  it brings up the "preparing Wizard" dialog and goes no further. I have this in the terminal "" WINEDLLOVERRIDES="riched32=n" wine barnes.exe
fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
"  Any ideas?
God Bless you, Carl

---

### Post by Wuzzle on 2008-02-04
Downloaded a few modules, and started experimenting.   Found that adding riched20.dll, riched32.dll, oleaut32.dll, msls31.dll, and setting to win98, to the default settings of the e-sword bottle under winecfg created earlier from the directions above allowed all modules to install flawlessly.

Used this example command line for each of the modules from the terminal.

env WINEPREFIX=~/.wine_Esword wine esv.exe
env WINEPREFIX=~/.wine_Esword wine drb.exe  

Hope this helps. :)

---

### Post by david_kt on 2008-02-05
> **cjm5229 said:**
> I have wine 0.95.4 installed, Installed eSword 795, got it working perfectly, but when I try to install the modules,  it brings up the "preparing Wizard" dialog and goes no further. I have this in the terminal "" WINEDLLOVERRIDES="riched32=n" wine barnes.exe
fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
"  Any ideas?
God Bless you, Carl

Hi Carl,

The command is not correct, you should put riched20 in overrides as well:

```
env WINEPREFIX=~/.wine_Esword WINEDLLOVERRIDES="riched20=n" WINEDLLOVERRIDES="riched32=n" wine bbe.exe
```

Please let me know if you still have problem after issuing the above command.

DK

---

### Post by cjm5229 on 2008-02-08
david_kt
I figured it out, I didn't get one of the dll files installed correctly, I removed them all and reinstalled them and it is working now. Thank You. 
Carl
PS
It works in Hardy also!

---

### Post by Ninefold on 2008-02-10
I was getting a "Preparing to Install..." message with the addons but I figured out the problem I was having. I used the .dll's from my Windows install rather than downloading them. Once I replaced those .dll's with the downloadable ones the addons installation worked.

Also, with the addons I had to alt+tab to the installation screen each step because it defaulted to just a the blue install screen. For a split second it was confusing.

In the end it worked great. Thanks for the great instructions! Would have been lost without them.

---

### Post by th1bill on 2008-02-19
I have a fresh Gutsy install.  I have managed to get the text for the KJV but I am getting the msls error and when I try to install the asv.exe module I recive the message tellimg me the directory does not exist.  I'm lost.

---

### Post by th1bill on 2008-02-19
And then there is this problem;

th1bill@workgroup:~$ cd desktop
bash: cd: desktop: No such file or directory
th1bill@workgroup:~$ cd Desktop
th1bill@workgroup:~/Desktop$ cp msls31.dll ~/.wine_Esword /drive_c/windows/system32
cp: target `/drive_c/windows/system32' is not a directory
th1bill@workgroup:~/Desktop$

---

### Post by david_kt on 2008-02-19
> **th1bill said:**
> And then there is this problem;
th1bill@workgroup:~$ cd Desktop
th1bill@workgroup:~/Desktop$ cp msls31.dll ~/.wine_Esword /drive_c/windows/system32
cp: target `/drive_c/windows/system32' is not a directory
th1bill@workgroup:~/Desktop$

Hi Bill,

There is a mistake in the instruction, please remove the space between ~/.wine_Esword and /drive_c.... So, it should be

```
cp msls31.dll ~/.wine_Esword/drive_c/windows/system32
```

I have amended the instruction as well. Thanks for the feedback and please let me know if you have ther problems after successfully copying the msls31.dll into place.

DK

---

### Post by th1bill on 2008-02-19
> **david_kt said:**
> Hi Bill,

There is a mistake in the instruction, please remove the space between ~/.wine_Esword and /drive_c.... So, it should be

```
cp msls31.dll ~/.wine_Esword/drive_c/windows/system32
```

I have amended the instruction as well. Thanks for the feedback and please let me know if you have ther problems after successfully copying the msls31.dll into place.

DK

.. I copied and pasted the code and it executed.  When I bring up e-Sword and my cursor touches the linked strongs numbers the msls not found message pops up and when I click OK I get a never-eding series of empty squares as I move the cursor around the window.
.. I do not know if it matters but I installed the setup795 through the download manager of Foxfire.  Then, my modules, ie. asv.exe, are located in Downloads and even if I cd to Downloads the Terminal tells me it cannot install the module because it cannot find it.
.. Thanks for the help David.  I have already given up on this once but there just is nothing available for the laborer in Linux right now that a person on a limited, fixed income can afford.  e-Sword really is all there is.

---

### Post by th1bill on 2008-02-19
David, I just clicked Places and went Home>.wine_Esword>drive_c:>windows>system32 and the msls.dll is there.

---

### Post by th1bill on 2008-02-19
I copied asv.exe and pasted a copy to my desktop anrd to my Home folder.  I then got the following results fro the terminal;

th1bill@workgroup:~$ env WINEPREFIX=~/.wine_Esword WINEDLLOVERRIDES="riched20=n" WINEDLLOVERRIDES="riched32=n" wine asv.exe

and the message came up, "Preparing Wizard, please wait," and it froze.

---

### Post by david_kt on 2008-02-20
> **th1bill said:**
> I copied asv.exe and pasted a copy to my desktop anrd to my Home folder.  I then got the following results fro the terminal;

th1bill@workgroup:~$ env WINEPREFIX=~/.wine_Esword WINEDLLOVERRIDES="riched20=n" WINEDLLOVERRIDES="riched32=n" wine asv.exe

and the message came up, "Preparing Wizard, please wait," and it froze.

Looks like the dll is not downloaded correctly. Could you try to download the dll again. And please take note that there is some problem in the instruction (it did not appear for unknown reason), you should download oleaut32.dll as well. I try to repair the instruction shortly.

DK

---

### Post by th1bill on 2008-02-20
> **david_kt said:**
> Looks like the dll is not downloaded correctly. Could you try to download the dll again. And please take note that there is some problem in the instruction (it did not appear for unknown reason), you should download oleaut32.dll as well. I try to repair the instruction shortly.

DK

Thank you, I'll do as you suggested and get back to this in about 8 hours.  Once again, I really appreciate your help.  With Rick Meyers consent I make up CD's and give them away.  I am now promoting Ubuntu at my church and the issue will certainly come up there also and I will keep the notes on the install process to help others.

---

### Post by th1bill on 2008-02-20
Okay, I downloaded the new copies of riched20.dll and msls.dll, renamed RICHED20.DLL to same but lower case and pasted them in the system32 folder.  I have exactly the same result as before.  These files were downloaded from dlldump.com.

I also still get the install wizard preparoiong to setup message and it freezes.

---

### Post by david_kt on 2008-02-20
> **th1bill said:**
> Okay, I downloaded the new copies of riched20.dll and msls.dll, renamed RICHED20.DLL to same but lower case and pasted them in the system32 folder.  I have exactly the same result as before.  These files were downloaded from dlldump.com.

I also still get the install wizard preparoiong to setup message and it freezes.

No, you must download 4 dlls: riched20.dll, riched32.dll, oleaut32.dll, and msls31.dll 
And after that, make sure you also set riched20.dll and oleaut32.dll to native:

```
env WINEPREFIX=~/.wine_Esword winecfg
```

Wine configuration window will pop up, click library tab, type riched20.dll, click add, edit to set it to native. Do the same for oleaut32.dll. And then try again.

 Please post here the out put in the terminal.

DK

---

### Post by th1bill on 2008-02-21
I'm sorry David, I downloaded all four .dll files and dragged and dropped, answering yes when asked if I wanted to replace them and so I do not have a terminal output to copy this time.  To set the riched20.dll and the oleaut32.dll to native I used the GUI at Applications>Wine>Wine Configure.  I still receive the msls not found and I am still unable to install any other Bibles.  If you need a terminal output give a command to issue and I will publish the output.  The files are located at ~/.wine_Esword/drive_c:/windows/system32.

---

### Post by david_kt on 2008-02-21
> **th1bill said:**
> I'm sorry David, I downloaded all four .dll files and dragged and dropped, answering yes when asked if I wanted to replace them and so I do not have a terminal output to copy this time.  To set the riched20.dll and the oleaut32.dll to native I used the GUI at Applications>Wine>Wine Configure.  I still receive the msls not found and I am still unable to install any other Bibles.  If you need a terminal output give a command to issue and I will publish the output.  The files are located at ~/.wine_Esword/drive_c:/windows/system32.

First of all, make sure it is no " : " in the folder name. It should be:

```
~/.wine_Esword/drive_c/windows/system32.
```

Instead of 
```
~/.wine_Esword/drive_c:/windows/system32.
```


See if that is the mistake. You must make sure you only have one folder "drive_c", not two folders "drive_c" and "drive_c:"

After that try again if it is ok.

And what I mean by terminal output is open terminal and issue below command:

```
 env WINEPREFIX=~/.wine_Esword wine "C:\Program Files\e-Sword\e-Sword.exe"
```

```
env WINEPREFIX=~/.wine_Esword WINEDLLOVERRIDES="riched20=n" WINEDLLOVERRIDES="riched32=n" wine bbe.exe
```

DK

---

### Post by th1bill on 2008-02-21
> th1bill@workgroup:~$  env WINEPREFIX=~/.wine_Esword wine "C:\Program Files\e-Sword\e-Sword.exe"
wine: cannot find 'C:\Program Files\e-Sword\e-Sword.exe'
th1bill@workgroup:~$ 

The output will come in two posts, iy goes crazy next.

---

### Post by david_kt on 2008-02-21
Bill,

Looks like you make some mistakes when following this instruction (or it might be due to the mistake I make earlier) as the wine could not even find the e-Sword.exe. Could you do me a favor by doing below steps:

1.  delete the .wine_Esword folder.
2. reboot your computer
3. repeat the instruction in the beginning of this thread carefully

If after that still unsuccessful, I will tell you the next step. Please be patient, I am sure I could guide you through this process.

DK

---

### Post by th1bill on 2008-02-21
Sorry, you'll know why so long in a second.
> fixme:richedit;RichedEditWndProc-common EM_FOR_MATRANGE:stub  When I put the second command in to the Terminal I writes thousands of lines of this code.  The only way to stop it is to force a shut down with the Restart button on the front of the machine.

---

### Post by th1bill on 2008-02-21
> **david_kt said:**
> Bill,

Looks like you make some mistakes when following this instruction (or it might be due to the mistake I make earlier) as the wine could not even find the e-Sword.exe. Could you do me a favor by doing below steps:

1.  delete the .wine_Esword folder.
2. reboot your computer
3. repeat the instruction in the beginning of this thread carefully

If after that still unsuccessful, I will tell you the next step. Please be patient, I am sure I could guide you through this process.

DK

Alright and thank you for you patience with a sometimes loud mouth Wibndows convert.

---

### Post by th1bill on 2008-02-21
I followed the instructions with the exception that the downloaded e-Sword read setup797.exe.   I made the change and it installed without hitch but when I typed the copied and pasted the run command it came up with no text and the Terminal went wild once more.  This time it did allow me to click the "x" button and shut it down so no read out to post.  I'm about to reboot and bring up the esword from the desktop icon.  BRB

---

### Post by th1bill on 2008-02-21
I've rebooted and I get the frames but no text when I click the icon.

---

### Post by david_kt on 2008-02-21
Give me about 8 hours from now, I will try E-sword 797 version once I arrive home and inform you the result. Please let me know also your wine version, open terminal and issue below command:

```
wine --version
```

DK

---

### Post by Tru on 2008-02-22
I was just using Ubuntu Ultimate Edition and it has something called Wine-doors.  It seems to take Wine past a basic install and comes pre-tweaked and ready to install a lot more Windows apps then just a base install of Wine.  Like I said I just looked at it and will play with it more over the weekend and will see how it handles installing e-sword and see if it takes some of the headache out of installing it.  If anyone wants to check it out to here is a [link ]("http://www.wine-doors.org/")

---

### Post by th1bill on 2008-02-22
> th1bill@workgroup:~$ wine --version
wine-0.9.46
th1bill@workgroup:~$ 

Alright.  I tried all 16 possible combinations for the settings on the two DLLs and none of them worked.  I went to my other machine and wrote everything from the esword4linux file from the deb installation there and put it in the ~/usr/local/apps file but when I click the start icon for it it tells me my permissions are incorrect so you are my last hope.

---

### Post by th1bill on 2008-02-22
Thanks Tru for the suggestion but having just migrated from being a Windows dummie I have no idea, as of this time, what to do with all of that code.

---

### Post by david_kt on 2008-02-22
Hi Bill,

I have tried it using wine 0.9.55 and e-sword 797. Could you upgrade your wine to 0.9.55 to be sure? Please follow the instruction on the first post carefully. It should run without any problem, including all the addons.

DK

---

### Post by th1bill on 2008-02-22
Okey, I'll run synaptic and see if I can find the upgrade and let you know.

---

### Post by th1bill on 2008-02-22
I tried the reinstall but I am stil running v. 946.  I'll need to figure this one out.

---

### Post by th1bill on 2008-02-22
I found [http://www.tuxmind.org/en/2008/02/09/wine-0955/](http://www.tuxmind.org/en/2008/02/09/wine-0955/) but I have no idea of where to find the public key so the command lines means nothing to me.  Sorry.

---

### Post by th1bill on 2008-02-22
I found Winehq and installed the 955 deb package.  I verified the two files were set to Native and still have no text.  If your tired I'll stop bugging you.

---

### Post by th1bill on 2008-02-22
David,
.. I'm going to delete the work we have done because I just reinstalled the deb package at whatwouldjesusdownload and with the new version of Wine it runs like a top.  Thank you for your efforts but I'll have to recommend that folks running Gutsy do the wine upgrade at Winehq and that they then install the esword4linux package.  nothing to set and you can download the modules you wish to use with one click GUI ease.
.. Once more, thank you.

---

### Post by david_kt on 2008-02-22
I am glad that finally you are able to run it. Please lock your wine as sometimes the wine upgrade might kill e-sword. To lock it:

System->Administration->Synaptic Package Manager -> and search for wine ->  select "wine" in the list -> click Package->Lock Version -> apply

This is very important as I saw some people complain that e-sword broke after wine upgrade if e-swrod installed using deb package.

 But for e-sword installed using this instruction, if followed corretly, so far it could work for any wine version and I do not see the neccesity to lock wine.

DK

---

### Post by th1bill on 2008-02-22
> **david_kt said:**
> I am glad that finally you are able to run it. Please lock your wine as sometimes the wine upgrade might kill e-sword. To lock it:

System->Administration->Synaptic Package Manager -> and search for wine ->  select "wine" in the list -> click Package->Lock Version -> apply

This is very important as I saw some people complain that e-sword broke after wine upgrade if e-swrod installed using deb package.

 But for e-sword installed using this instruction, if followed corretly, so far it could work for any wine version and I do not see the neccesity to lock wine.

DK

Thank you for that tip.  I've done so.

---

### Post by GlennW on 2008-03-06
Hi David, thanks for all the work that you and your associates have done regarding e-Sword and its installation. I have used e-Sword for years and now that I have migrated to linux I'd like to be able to use it here too. I'm quite the linux newb and so I'll tell you what I've done thus far and see what kind of advise the forum comes up with. 

I pretty much removed everything from my XP partition, wanting to free up as much space as possible for my growing gutsy partition. I therefore zipped up e-Sword (bibles, commentaries, dictionaries, everything) and have it sitting unzipped in /home/e-Sword.

I am confused by some of david_kt's code seems, to my very uneducated linux thinking, to be running e-Sword from windows! That's not my intent. Is there a way to run in with wine from a folder in gutsy?

blessings...
Glenn

---

### Post by david_kt on 2008-03-06
GlennW,

The instruction is to run e-sword from linux. No MS windows required.

Please follow the steps carefully and you will be able to run e-sword on linux (not only ubuntu).

As for the addons, you just need to copy from your /home/e-Sword to .wine_Esword.

Please let me know if you have any questions.

DK

---

### Post by GlennW on 2008-03-08
> **david_kt said:**
> GlennW,

The instruction is to run e-sword from linux. No MS windows required.

Please follow the steps carefully and you will be able to run e-sword on linux (not only ubuntu).

As for the addons, you just need to copy from your /home/e-Sword to .wine_Esword.

Please let me know if you have any questions.

DK

Thanks David, everything went relatively smooth as far as installs go. After a bit of fiddling around, I managed to get e-Sword to work. All of the addons work just fine. 

I have a question. How can I get this icon to replace the wine icon?

---

### Post by david_kt on 2008-03-09
> **GlennW said:**
> 
I have a question. How can I get this icon to replace the wine icon?

Right click the launcher and choose properties. After that click on the wine icon, it will open a windows. Navigates to the icon file you want. If the icon you want did not appear in the navigation windows, change the extension to png.

DK

---

### Post by GlennW on 2008-03-09
David, it worked like a charm!! Thanks.

Another issue has popped up. I attempted to add some fonts since the font displayed is terrible! I found the folder where the e-Sword fonts are located and there were just some Georgia fonts there. I added a bunch, nothing crazy. After I restarted e-Sword, the Edit and Format menu options were unavailable. I went back to the fonts folder to find out that all the fonts had a little "lock" on the one corner of the icon. I've never seen that before. 

How can I "unlock" these fonts? Are these considered addons too?

Thanks.

PS. I hope your pastor's sermon was a good as my pastor's sermon...

---

### Post by david_kt on 2008-03-09
Hi Glenn,

If the fonts has a lock in it, that means there is some file permission issue.

What you can do is right click in the file, and click the permission tab, and then click on the execute, read, write for the appropriate user. You could safely click all the options I think.

But if there are too many files, it could be very trouble some to change the file permission one by one.

What you could do is to open terminal (application>accesories>terminal), 

and then issue below command:

```
chmod 777 -R ~/.wine_Esword/drive_c/windows/fonts
```

you could change 777 to 700, and it should be ok as well. But to be sure, I suggest to use 777.

After that, reload the fonts page in nautilus, all the locks should be disappear. The above command is to give full right for every body to use all files at the fonts folder.

Please let me know if you still have some issue.

DK

---

### Post by GlennW on 2008-03-09
Thanks David for your help, it's been invaluable. I unlocked the fonts as you directed and I now have access to them in e-Sword. I can change all of the fonts (bible, commentary, dictionary, etc.) except the e-Sword application font itself (ie. the font for "menu, edit, format, etc"). It is very small and pixelated. All other fonts are clear and sharp as they should be. If that can't be fixed, I can live with that. I'm just so happy that e-Sword is up and running again.

Thanks again!

---

### Post by david_kt on 2008-03-10
> **GlennW said:**
> except the e-Sword application font itself (ie. the font for "menu, edit, format, etc"). It is very small and pixelated. 

For Esword application fonts, you could increase it using below method:

Open terminal (Application>Accesories>Terminal)

Open wine configuration edito from terminalr:

```
 env WINEPREFIX=~/.wine_Esword winecfg

```

Click graphics tab.

At below, there is a screen resolution slider, the default is 96 dpi. Slide the slider to maximum (120 dpi). Click apply and then ok.

Open your e-sword, if it is too big, you could repeat below steps, adjusting the slider to whatever number (between 96 to 120).

DK

---

### Post by alaaji on 2008-03-11
I can confirm that this works on Hardy Heron with the updated version of esword (setup798.exe).  Thanks so much for your work David!

---

### Post by XanderTM on 2008-03-11
Hi, David!

I, also, am very noobish to Linux, and I'm trying to get E-Sword on my laptop, and it won't let me! I followed all that you said, and when it came to actually installing it, it won't work! It keeps giving me this:

And this is what I put in:

env WINEPREFIX=~/.wine_Esword wine setup798.exe

And this is what it responds with:

wine: could not load L"C:\\windows\\system32\\setup798.exe": Module not found

Now, I changed the number on the setup.exe because I have the new version of e-Sword.

Anyways, any help that could be given would be GREATLY appreciated.

Xan

---

### Post by david_kt on 2008-03-11
> **XanderTM said:**
> 

env WINEPREFIX=~/.wine_Esword wine setup798.exe

And this is what it responds with:

wine: could not load L"C:\\windows\\system32\\setup798.exe": Module not found


That is because the setup file (setup798.exe) is not in your home folder. When you open terminal, the default is your home folder. Where do you put/donwload the setup file? If you put it on your desktop, then you should change location to Desktop first after you open terminal (Applications>Accessories>terminal):

```
cd Desktop
```

and then only you could execute the file:

```
env WINEPREFIX=~/.wine_Esword wine setup798.exe
```

Please let me know if it is still not clear.

DK

---

### Post by XanderTM on 2008-03-12
ha! well, it got installed! And it runs! but...when I opened it, it said "Module not found (msls31.dll)."
So, whenever I hover over a Strong's numbering, it comes up as garbled mess. And it won't switch to other scriptures unless I double click that scripture, exit out, open it back up, and there's what I clicked.

And I've already checked to see if it was in the System32 folder, and it is! It's all lowercase and everything. Do I need to set it to native, too?

---

### Post by david_kt on 2008-03-12
> **XanderTM said:**
> ha! well, it got installed! And it runs! but...when I opened it, it said "Module not found (msls31.dll)."
So, whenever I hover over a Strong's numbering, it comes up as garbled mess. And it won't switch to other scriptures unless I double click that scripture, exit out, open it back up, and there's what I clicked.

And I've already checked to see if it was in the System32 folder, and it is! It's all lowercase and everything. Do I need to set it to native, too?

Could you explain more detail:

1. How did you put msls31.dll?
2. How did you run the e-sword?

DK

---

### Post by XanderTM on 2008-03-13
Well, I put msls31.dll into the system32 file just by clicking and dragging it into there, with all of the other files. And I opened e-Sword just by double clicking it. When I open it, it gives the regular tip like always, then when I exit the tip, it comes up with a window that says "Module not found (msls31.dll)" with an "OK" button. That's all.

Oh, and if I minimize then bring it back up, all of the windows with scripture and stuff in them are black.:(

So, yeah, umm...I think that's about it. I don't need to make that dll native?

Thanks for the help!

---

### Post by david_kt on 2008-03-13
> **XanderTM said:**
> Well, I put msls31.dll into the system32 file just by clicking and dragging it into there, with all of the other files. And I opened e-Sword just by double clicking it. When I open it, it gives the regular tip like always, then when I exit the tip, it comes up with a window that says "Module not found (msls31.dll)" with an "OK" button. That's all.

Oh, and if I minimize then bring it back up, all of the windows with scripture and stuff in them are black.:(

So, yeah, umm...I think that's about it. I don't need to make that dll native?

Thanks for the help!

For msls31.dll you do not need to make it native. When you drag and drop it, make sure the location is:

/home/YourUserName/.wine_Esword/drive_c/windows/system32

**_not_** /home/YourUserName/.wine/drive_c/windows/system32

If that is correct, the only problem is may be you double click on e-Sword.exe, which will run the default wine.

You should double click the launcher created in the Desktop instead,
 or 
open terminal (Application>Accessories>terminal) and run with this command:

```
env WINEPREFIX=~/.wine_Esword wine "C:\Program Files\e-Sword\e-Sword.exe"
```

DK

---

### Post by Berean on 2008-03-22
I've had an absolute nightmare trying to install this!  I run Logos Scholar Gold in VMware but really wanted to get eSword running in Ubuntu so have followed your thread and playing around a little: VMware take a while to load, so only open it when writing papers.  Essentially, I installed the .dll files as you suggested but set the "system" as Windoze 98.  I also downloaded the modules to the desktop by "Save to disk" and not "Open with wine" (for some peculiar reason it wouldn't work by "open with wine"), then right clicked and selected "Open with Wine windows emulator".  When the blue screen appeared I followed the prompts and then when it went completely blue I Alt. and tabbed to move to the desired screen.  This completely set it up and it's running fantastically!  Thanks to those who have already posted and whose advice I have picked and chosen to get me where I am now.  Blessings.

---

### Post by kneewax on 2008-03-25
Hey Guys,

I followed the instructions in the first posts in this thread and they worked just fine.  However the fonts e-sword is displays through WINE are really poor, and almost unreadable.  Does anyone any know a way of improving the font display?

Thanks

Kneewax

---

### Post by david_kt on 2008-03-26
> **kneewax said:**
> Hey Guys,

I followed the instructions in the first posts in this thread and they worked just fine.  However the fonts e-sword is displays through WINE are really poor, and almost unreadable.  Does anyone any know a way of improving the font display?

Thanks

Kneewax

It is already included in the tutorial, here I copy again for you:

_Add more fonts_
To add more fonts, copy whatever fonts you have to ~/.wine_Esword/drive_c/windows/fonts.
If it still not appear in e-sword, it might be due to file permission problem. What you have to do is to open terminal (application>accesories>terminal), and then issue below command:
```
chmod 777 -R ~/.wine_Esword/drive_c/windows/fonts
```

The fonts should now available for E-sword to use.
[U]
Increase font size for E-sword menu[/U]
If you find e-Sword application font itself (ie. the font for "menu, edit, format, etc") is too small, what you can do is:

Open terminal (Application>Accesories>Terminal)
Open wine configuration editor from terminal:
```
env WINEPREFIX=~/.wine_Esword winecfg
```

Click graphics tab.

At below, there is a screen resolution slider, the default is 96 dpi. Slide the slider to maximum (120 dpi). Click apply and then ok.

Open your e-sword, if it is too big, you could repeat below steps, adjusting the slider to whatever number (between 96 to 120).

---

### Post by kneewax on 2008-03-26
Thanks guys, I had already added the dll files to the libraies tab, and made them Native - but for some reason the settings hadn't saved.

I now have a new problem, I upped the dpi setting and the fonts are improved but now a bit too big - the problem now is that because of the increased size the Wine config window is too big to fit on the screen and I can't get to the slider to adjust it.  Does anyone know a command I can use to reset it?

Cheers

Kneewax

---

### Post by david_kt on 2008-03-26
> **kneewax said:**
> Thanks guys, I had already added the dll files to the libraies tab, and made them Native - but for some reason the settings hadn't saved.

I now have a new problem, I upped the dpi setting and the fonts are improved but now a bit too big - the problem now is that because of the increased size the Wine config window is too big to fit on the screen and I can't get to the slider to adjust it.  Does anyone know a command I can use to reset it?

Cheers

Kneewax

For winecfg, have you click apply button? May be that is the problem. And remember to click ok as well. It should be saved.

As for the fonts, what I mean is font files, not dll. You could copy it from C:/Windows/fonts folder in MS windows, or download it from internet.

Which dpi you adjusted? Is it in winecfg or gnome? But if you could not see the slider, cou could right click the tab below for the wine config windows, and choose move. After that move your mouse until you could see the slider.

DK

---

### Post by kneewax on 2008-03-26
[QUOTE=david_kt;4588990
Which dpi you adjusted? Is it in winecfg or gnome? 
DK[/QUOTE]

Sorry, not being very coherent am I? 

I did apply the fonts as you suggested and that was a great improvement - all looks good now within individual Bibles.  Thanks!

I ALSO tried to increase the E-Sword menu fonts as you suggested using the WINEcfg panel.  This is what I can not now get back to.  The winecfg window displays but the slider etc are all off the bottom of my screen I cannot scroll down or resize the window.  Interestingly if I access the general Wine Configuration menu (not the one for the e-sword bottle) then it displays just fine within the perimeters of my desktop resolution.

Sorry not trying to be obtuse :)

Kneewax

---

### Post by david_kt on 2008-03-26
> **kneewax said:**
> 
I ALSO tried to increase the E-Sword menu fonts as you suggested using the WINEcfg panel.  This is what I can not now get back to.  The winecfg window displays but the slider etc are all off the bottom of my screen I cannot scroll down or resize the window.  Interestingly if I access the general Wine Configuration menu (not the one for the e-sword bottle) then it displays just fine within the perimeters of my desktop resolution.


What you should do (as I mention before), right click on the tab of winecfg window at bottom panel, and choose move. After that , you should be able to move the winecfg window just by moving the mouse, until you could see the slider.

DK

---

### Post by kneewax on 2008-03-26
sorry, thought I'd said, but didn't (got distracted by a small person)  it still won't move beyond the boundaries of the desktop. and that is not enough to reach the slider.  Never mind, I will work around it for now.  Thanks for all you help on this  DK - and the work you have put in getting us working with e-sword.

Kneewax.

---

### Post by david_kt on 2008-03-26
> **kneewax said:**
> sorry, thought I'd said, but didn't (got distracted by a small person)  it still won't move beyond the boundaries of the desktop. and that is not enough to reach the slider.  Never mind, I will work around it for now.  Thanks for all you help on this  DK - and the work you have put in getting us working with e-sword.

Kneewax.

In that case, just copy system, user, and userdef files from your ~/.wine folder to ~/.wine_Esword folder.

You need to run winecfg again to set the dll override, and also might need to run the setup.exe again in case e-sword could not launch.

DK

---

### Post by Eutaw on 2008-03-27
When I got Gutsy running, before I knew about this forum, I clicked on esword installer from accessories. It will open, but without any text in any of the windows. I followed the instructions after the fact (the .dll files etc), still no joy. do I need to delete and re-install, or is there some other way to get it going?
Thanks.

---

### Post by Eutaw on 2008-03-27
Oops! I installed it with Feisty, upgraded to Gutsy, no text either place.

---

### Post by kneewax on 2008-03-27
EUTAW,  I assume from your post you are using Ubuntu CE?  I tried the Installer that ships with Ubuntu CE and got nowhere (although I added it separately as I am not keen on the CE version).  I would remove it and follow the instructions from the original message in this thread.  

This may not be the only way to get it working - but it will work.

Kneewax

---

### Post by david_kt on 2008-03-27
> **Eutaw said:**
> When I got Gutsy running, before I knew about this forum, I clicked on esword installer from accessories. It will open, but without any text in any of the windows. I followed the instructions after the fact (the .dll files etc), still no joy. do I need to delete and re-install, or is there some other way to get it going?
Thanks.

The esword installer from accesories is different from this instruction. Please try to follow this instruction from start, and let me know if you still could not make it run.

DK

---

### Post by JFonseka88 on 2008-03-27
~/.wine_Esword/drive_c/windows/system32

How do I access that ?
I don't think it even exists, but I do have wine installed, i'm 100% sure.
I'm running Ubuntu - Christian edition, and my wine is updated

---

### Post by david_kt on 2008-03-27
> **JFonseka88 said:**
> ~/.wine_Esword/drive_c/windows/system32

How do I access that ?
I don't think it even exists, but I do have wine installed, i'm 100% sure.
I'm running Ubuntu - Christian edition, and my wine is updated

That folder is created by the special command:

```
wineprefixcreate --prefix .wine_Esword
```

Please follow the instruction from the beginning. If cou still could not find it, may be you need to show hidden folder:

Open home folder (Places >> Home folder)
Show hidden folder (View >> Show Hidden Folder)

and you will see folders with dot in front.

DK

---

### Post by love2learn on 2008-03-29
i am so new i dont know how to rename a file i suppose.  I think because the DLL is in caps I cant rename it? I have renamed the others from caps but the DLL in the other 3 names werent caps? I have successfully mv'd the others over but not this one. Please help?

---@laptop:~/Desktop$ sudo rename riched20.DLL riched20.dll
[sudo] password for ----:
Bareword "riched20" not allowed while "strict subs" in use at (eval 1) line 1.
Bareword "DLL" not allowed while "strict subs" in use at (eval 1) line 1.
----@laptop:~/Desktop$

---

### Post by david_kt on 2008-03-29
> **love2learn said:**
> i am so new i dont know how to rename a file i suppose.  I think because the DLL is in caps I cant rename it? I have renamed the others from caps but the DLL in the other 3 names werent caps? I have successfully mv'd the others over but not this one. Please help?

---@laptop:~/Desktop$ sudo rename riched20.DLL riched20.dll
[sudo] password for ----:
Bareword "riched20" not allowed while "strict subs" in use at (eval 1) line 1.
Bareword "DLL" not allowed while "strict subs" in use at (eval 1) line 1.
----@laptop:~/Desktop$

Sudo is not required, and rename is to rename multiple files with syntax:
rename [ -v ] [ -n ] [ -f ] perlexpr [ files ]

To rename a single file, try mv instead:

```
mv -i riched20.DLL riched20.dll
```

Remember to move all dlls from your Desktop  to ~/.wine_Esword/drive_c/windows/system32

DK

---

### Post by ag65151 on 2008-03-29
I got e-sword working great following the instructions above. thank you for that. 

However, I can not install any add-ons. When I use the
```

env WINEPREFIX=~/.wine_Esword WINEDLLOVERRIDES="riched20=n" WINEDLLOVERRIDES="riched32=n" wine bbe.exe

```

I get the pop-up window that says it is preparing to install and then in the terminal I entered the above command I get and endless repeat of 

```

fixme:richedit:RichEditWndProc_common EM_FORMATRANGE: stub

```

Just to be specific: all of the add-on files I want are on my Desktop. I cd to ~/Desktop and run the above command. I copied it directly and only changed the exe to the one I was trying to install. I have tried it with 3 different add-ons and have the same results.

Thanks again for you help.

---

### Post by david_kt on 2008-03-30
> **ag65151 said:**
> 
```

fixme:richedit:RichEditWndProc_common EM_FORMATRANGE: stub

```

Just to be specific: all of the add-on files I want are on my Desktop. I cd to ~/Desktop and run the above command. I copied it directly and only changed the exe to the one I was trying to install. I have tried it with 3 different add-ons and have the same results.


Looks like the dll is the problem, Could you redownload the dll or look for dll from other places

and let me know the result.

DK

---

### Post by love2learn on 2008-03-30
incredible! I made the switch to Ubuntu less than a week ago. I couldn't even rename a file. Buy following these simple instructions e-sword works flawlessly on Ubuntu. If I can do it anyone can. Your instructions worked with wine-0.9.46 and setup798.exe. shear genius!

Thanks for your time and effort

---

### Post by ag65151 on 2008-03-30
Thanks for the dll's. I now have e-sword up, running, and full of resources. 

Thanks for this how-to. The lack of a strong Bible tool has been the shortfall of Linux in general for some time. With this how-to and e-sword, there should be no reason for anyone to donate to the Gates' pockets any longer.


Thanks again.

---

### Post by KingdomKid on 2008-04-08
Hey Guys...

Quick question...I have a dual boot system (XP and Kubuntu), I have E-sword installed on my XP side. Considering, does this make any difference in following the instructions in this post to get it install on my linux (Kubuntu) side?

Thank You in advance.

---

### Post by Eutaw on 2008-04-08
I dual boot with Vista. It made no difference in the instructions.

---

### Post by KingdomKid on 2008-04-08
> **Eutaw said:**
> I dual boot with Vista. It made no difference in the instructions.

Did you already have E-sword installed on the Vista side?

The reason I ask is, in my research, I have found here in the forum, some that say, it's simpler, if you already have e-sword installed in windows that you could just copy (the files in esword) over into wine in your linux side. ???

I would not know how to do that???

Before I did the instructions in this post, which looks like the best I have found on the subject, I thought I would explore the options and verify with some who has experience in doing "any" of the above.

---

### Post by david_kt on 2008-04-08
> **KingdomKid said:**
> Did you already have E-sword installed on the Vista side?

The reason I ask is, in my research, I have found here in the forum, some that say, it's simpler, if you already have e-sword installed in windows that you could just copy (the files in esword) over into wine in your linux side. ???

I would not know how to do that???

Before I did the instructions in this post, which looks like the best I have found on the subject, I thought I would explore the options and verify with some who has experience in doing "any" of the above.

The problem with e-sword in linux is to install addon. If you already have e-sword on your windows (regardless XP or Vista), it would be easier to install addon (just copy the addon from C:/program files/e-Sword folder from windows to ~/.wineEsword/drive_c/ Program Files/e-Sword in linux, or wherever you install it).

If you could follow the instruction here to install addons, there is no need to have it install on the windows side. But if you have installed all addons on windows, it is much faster to just copy and paste the whole folder from windows to linux to install all addons.

DK

---

### Post by Eutaw on 2008-04-08
What I found was that the various Bibles and commentaries I already had were referenced in Ubuntu. I still had to follow the instructions to activate and use them, but I didn't have to download them from the main site. When I clicked on the e-Sword module manager, they were there. I had to copy them to Desktop and do the cut and paste thing with the Wine instructions, but that was easy once I found them.

---

### Post by KingdomKid on 2008-04-08
Hey Guys...

Thanks for the input and help. I got it up and running.

I have 1 issue I need help on. The launcher on the desktop has a bad path for some reason. When I try launch I get an err message:

The file or folder **file:///mnt/winc//Program Files/e-Sword/e-Sword.exe** does not exist.

I can and it (e_Sword) will launch from the terminal.

Any suggestions??

---

### Post by david_kt on 2008-04-08
> **KingdomKid said:**
> Hey Guys...

Thanks for the input and help. I got it up and running.

I have 1 issue I need help on. The launcher on the desktop has a bad path for some reason. When I try launch I get an err message:

The file or folder **file:///mnt/winc//Program Files/e-Sword/e-Sword.exe** does not exist.

I can and it (e_Sword) will launch from the terminal.

Any suggestions??


What you could do is to right click on the launcher >> click properties >> choose launcher tab >> replace the command with the one you use it in terminal.

The launcher should be working now.


By the way, could you tell me which wine version you are using? Open terminal and type:

```
wine --version
```

DK

---

### Post by KingdomKid on 2008-04-08
> **david_kt said:**
> What you could do is to right click on the launcher >> click properties >> choose launcher tab >> replace the command with the one you use it in terminal.

The launcher should be working now.


By the way, could you tell me which wine version you are using? Open terminal and type:

```
wine --version
```

DK

DK...thanks for the info.
I got to the properties...I have 4 tabs (General | Permissions | Meta Info | Preview ) I don't see where I can change the command path. Can you direct me a little more?

The version of wine is: wine-0.9.33

---

### Post by david_kt on 2008-04-08
> **KingdomKid said:**
> DK...thanks for the info.
I got to the properties...I have 4 tabs (General | Permissions | Meta Info | Preview ) I don't see where I can change the command path. Can you direct me a little more?

The version of wine is: wine-0.9.33

Looks like it is a different launcher, not sure what happen. Then just create a new launcher:

Right click on desktop (on blank area) >> choose create launcher>> on command, put the one you use it in terminal successfully.

You could fill other information as you wish, but at least fill up the name as well. You could also add icon to this launcher, preferably original e-sword icon.

Please let me know if you still have problem.

DK

---

### Post by KingdomKid on 2008-04-08
> **david_kt said:**
> Looks like it is a different launcher, not sure what happen. Then just create a new launcher:

Right click on desktop (on blank area) >> choose create launcher>> on command, put the one you use it in terminal successfully.

You could fill other information as you wish, but at least fill up the name as well. You could also add icon to this launcher, preferably original e-sword icon.

Please let me know if you still have problem.

DK

DK...I tried creating a new launcher, didn't work. Not sure why???
I put in the command that works in terminal, nope. Then I tried using the "browse" button and following it to the command. That didn't work either.

Also...since you asked about my wine version, I noticed that mine is older version. Is that a big deal?

Thanks

---

### Post by david_kt on 2008-04-08
> **KingdomKid said:**
> DK...I tried creating a new launcher, didn't work. Not sure why???
I put in the command that works in terminal, nope. Then I tried using the "browse" button and following it to the command. That didn't work either.

Also...since you asked about my wine version, I noticed that mine is older version. Is that a big deal?

Thanks

Could you elaborate in detail what you do to create launcher, and how it failed (The browse button would not work as you have not make a script to launch e-sword).

Older wine version should not be a problem, as you has reported that it could run from terminal. 

DK

---

### Post by KingdomKid on 2008-04-09
> **david_kt said:**
> Could you elaborate in detail what you do to create launcher, and how it failed (The browse button would not work as you have not make a script to launch e-sword).

Older wine version should not be a problem, as you has reported that it could run from terminal. 

DK

FYI...I am using Kubutu 7.04

I right click on desktop> click on create new> click on new link to application>

From that point I get a box with the 4 tabs:
General | Permissions | Application | Preview

click on application tab > from here I get a box to fill in the properties. Those are:

Description:
Comment:
Command:
Work Path:

I put this, which works from terminal, in the "command" space:
 
[env WINEPREFIX=~/.wine_Esword wine "C:\Program Files\e-Sword\e-Sword.exe"]

click ok

Icon was created. clicked on it for test. It ran for about 5 seconds, like it was going to work, then nothing. Nothing happened, no error, no nothing.

---

### Post by david_kt on 2008-04-09
> **KingdomKid said:**
> FYI...I am using Kubutu 7.04

Well, I am not sure about kde. I will try to install one and inform you later. Could you subscribe to this thread so that you will receive email notification when I have studied the kde launcher. All this while I am only using gnome, so, I need to study first in order to be able to solve your problem. I hope somebody here have experience in making launcher in kubuntu so that you could get the answer quicker.

DK

---

### Post by KingdomKid on 2008-04-09
> **david_kt said:**
> Well, I am not sure about kde. I will try to install one and inform you later. Could you subscribe to this thread so that you will receive email notification when I have studied the kde launcher. All this while I am only using gnome, so, I need to study first in order to be able to solve your problem. I hope somebody here have experience in making launcher in kubuntu so that you could get the answer quicker.

DK

DK, thanks for all you help!!!:)

These instructions have been a great help! I have e-Sword running and I just got some new fonts put in.
I'll also see what I can come up with as far as the launcher. Until then I can use the terminal. 
I am subscribed to the thread...

Thank again!

---

### Post by david_kt on 2008-04-10
> **KingdomKid said:**
> DK, thanks for all you help!!!:)

These instructions have been a great help! I have e-Sword running and I just got some new fonts put in.
I'll also see what I can come up with as far as the launcher. Until then I can use the terminal. 
I am subscribed to the thread...

Thank again!

I have tried to run E-sword using KUBUNTU 6.06, wine version 0.9.43 today.

The launcher could run as normal.

What you could do is to open the launcher using text editor ( right click on the launcher>> open with>>utility>>kate), and make sure it has below lines:

```

[Desktop Entry]
Name=e-Sword
Exec=env WINEPREFIX="/home/your_user_name/.wine_Esword" wine "C:\\Program Files\\e-Sword\\e-Sword.exe" 
Type=Application
StartupWMClass=Wine
Path=/home/your_user_name/.wine_Esword/dosdevices/c:/Program Files/e-Sword/
Icon=/Path/to/the/icon/you/want

```

your_user_name should be change to what you use as user name.

After that, try to launch it again and see if this help.

Otherwise, you could upgrade your wine to higher version (0.9.43 for example), and then try to reinstall e-sword. If it still does not work, try to remove the whole folder (.wine_Esword folder) and install it from scratch again.

DK

---

### Post by KingdomKid on 2008-04-10
> **david_kt said:**
> I have tried to run E-sword using KUBUNTU 6.06, wine version 0.9.43 today.

The launcher could run as normal.

What you could do is to open the launcher using text editor ( right click on the launcher>> open with>>utility>>kate), and make sure it has below lines:

```

[Desktop Entry]
Name=e-Sword
Exec=env WINEPREFIX="/home/your_user_name/.wine_Esword" wine "C:\\Program Files\\e-Sword\\e-Sword.exe" 
Type=Application
StartupWMClass=Wine
Path=/home/your_user_name/.wine_Esword/dosdevices/c:/Program Files/e-Sword/
Icon=/Path/to/the/icon/you/want

```

your_user_name should be change to what you use as user name.

After that, try to launch it again and see if this help.


DK

DK...Thanks for the help.

I tried the above but could not get it to work. I did however, through trial and error and some of your suggested codes, get a launcher to work with the following steps.

Right click on Desktop > create new > link to application > application tab

Enter following code in command space= env WINEPREFIX="/home/your_user_name/.wine_Esword" wine "C:\\Program Files\\e-Sword\\e-Sword.exe"

Enter following code in "work path" space= /home/your_user_name/.wine_Esword/dosdevices/c:/Program Files/e-Sword/

( Im not sure if the above code in "work path" really makes a difference, yet, I did it anyway???)

Click on General tab, changed name to e-Sword
Click on Icon, choose icon you want
Click OK

Tested and it worked. All is well. 
Thank You DK, I appreciate your help. :popcorn:

---

### Post by gusjones on 2008-04-12
> **david_kt said:**
> 
```
 env WINEPREFIX=~/.wine_Esword WINEDLLOVERRIDES="riched20=n" WINEDLLOVERRIDES="riched32=n" wine bbe.exe
```If it shows only blue screen, press [alt+tab] to switch to installation windows. You may need to press [alt+tab] again every time after you press next.


Hi David, I am trying this install out on Hardy Heron Beta, not sure if that's relevant, anyway thanks for your howto for esword, which I have installed without any problems, however when I try to install the various addons I get the following repeated console error:

-------
err:module:import_dll Library RICHED20.dll (which is needed by L"C:\\windows\\system32\\RICHED32.DLL") not found
------
 Can anyone help me out here? Does the capitlising of the dlls in the error message have anything to do with the problem??

---

### Post by gusjones on 2008-04-12
Problem solved! Maybe this will help someone else, 

Go to ~/.wine_Esword/drive_c/program files/e-sword/ and copy riched20.dll.

cd to ~/.wine_Esword/drive_c/windows/system32/ and paste riched20.dll to here (rename old riched20.dll to be on the safe side).

I then found that the installer worked fine.

---

### Post by david_kt on 2008-04-12
> **gusjones said:**
> Problem solved! Maybe this will help someone else, 

Go to ~/.wine_Esword/drive_c/program files/e-sword/ and copy riched20.dll.

cd to ~/.wine_Esword/drive_c/windows/system32/ and paste riched20.dll to here (rename old riched20.dll to be on the safe side).

I then found that the installer worked fine.

You should download another 3 dlls ( riched32, oleaut32.dll, and msls31.dll) and placed it to ~/.wine_Esword/drive_c/windows/system32/ as well, if you have not done that.

DK

---

### Post by gusjones on 2008-04-12
> **david_kt said:**
> You should download another 3 dlls ( riched32, oleaut32.dll, and msls31.dll) and placed it to ~/.wine_Esword/drive_c/windows/system32/ as well, if you have not done that.

DK

I can't understand this, I had originally copied riched20 and the other 3 dlls to /system32, why then did I need a new riched20 installed by esword itself?

Anyway I'm glad to have esword working with modules, IMHO it is far better than gnomesword and the other alternatives.

---

### Post by david_kt on 2008-04-12
> **gusjones said:**
> I can't understand this, I had originally copied riched20 and the other 3 dlls to /system32, why then did I need a new riched20 installed by esword itself?

Anyway I'm glad to have esword working with modules, IMHO it is far better than gnomesword and the other alternatives.

That is because the riched20.dll you downloaded either corrupted or different version. May be I should change the "how to" to use the riched20.dll in e-sword and see whether or not it is consistently good.

DK

---

### Post by Eutaw on 2008-04-12
> **gusjones said:**
> Hi David, I am trying this install out on Hardy Heron Beta, not sure if that's relevant, anyway thanks for your howto for esword, which I have installed without any problems, however when I try to install the various addons I get the following repeated console error:

-------
err:module:import_dll Library RICHED20.dll (which is needed by L"C:\\windows\\system32\\RICHED32.DLL") not found
------
 Can anyone help me out here? Does the capitlising of the dlls in the error message have anything to do with the problem??

Case sensitive problem, appears to me.

---

### Post by k51 on 2008-04-18
Hi, e-Sword installed fine thanks to your tutorial, but now I'm just wondering how to get the modules I install working?
I installed a lot of modules from within module manager, but I don't see how to get them into the e-sword app, e.g. still only have default KJV bible in bible view.

I have no file called bbe.exe on my computer, should of it been created next to e-Sword.exe?

Please advise, thanks.

---

### Post by Eutaw on 2008-04-18
Hi k51,
bbe.exe is one of the modules. He used it as an example. To install the modules, go to your module manager where you installed the modules. You need to copy those to Desktop, then follow the instructions, inserting each module at the "bbe.exe" point in the command line.
Rick

---

### Post by david_kt on 2008-04-18
> **k51 said:**
> Hi, e-Sword installed fine thanks to your tutorial, but now I'm just wondering how to get the modules I install working?
I installed a lot of modules from within module manager, but I don't see how to get them into the e-sword app, e.g. still only have default KJV bible in bible view.

I have no file called bbe.exe on my computer, should of it been created next to e-Sword.exe?

Please advise, thanks.

This tutorial is not related to module manager. What you need to do is to 
search the exe file downloaded by the module manager ( for example bbe.exe and other exe file), and run it as the instruction. If you could not find the exe files downloaded by the module manager, you have to download them again from:

[http://www.e-sword.net/downloads.html](http://www.e-sword.net/downloads.html)

Choose whatever module category from the drop down box , and then choose whatever module from there. After it is downloaded, remember the location of the file, and open terminal, navigate to that folder, and execute the command as the instruction stated (copy and paste the command).

DK

---

### Post by bishoptf on 2008-04-20
Hey david_kt thanks much for the instructions, I have it running on hardy with the latest wine ver and e-sword, looks like it works.  I am trying to add as many items that were in ubuntu CE on my on, I have never done much with wine so this was a big help :) I am wanting to set up some PC's in our youth area to let them do stuff and I am trying to add as many items from CE.  One that I was looking at was The Word, but I can't find any specific installation instructions, do you know of any or have you installed it?  Also, what other Bible based apps would be good for a youth group?  Thanks....

---

### Post by david_kt on 2008-04-21
> **bishoptf said:**
>  One that I was looking at was The Word, but I can't find any specific installation instructions, do you know of any or have you installed it?  Also, what other Bible based apps would be good for a youth group?  Thanks....

Is the link below contain the software you want to install?

[http://www.theword.gr/en/index.php/w/download](http://www.theword.gr/en/index.php/w/download)


If yes, I would try to install it first and then write the instruction. Otherwise, please give me a link to the software you want to install.

As for other software, I really do not have any idea. But if you find windows software you want to run in linux, just let me know in case I could manage to make it work.

DK

---

### Post by david_kt on 2008-04-21
I have just downloaded and install the word from :

[http://www.theword.gr/en/index.php/w/download](http://www.theword.gr/en/index.php/w/download)

It install without any problem at all in Hardy, wine version 0.9.59.
Just donwloaded the exe file, double click on it.

 If it did not run, right click on the exe file, choose "open with other application", look for "wine windows emulator".

 Please let me know if you still have problem.

DK

---

### Post by canadianbaptist on 2008-04-26
I could use some help in installing esword on 7.10 I followed this tutorial and it worked once. Now it opens but there is no Bible. If I search I can see bible but cannot see it in the pane.

I have changed the dll's into lower case and have changed them to native (windows) I have uninstalled esword twice and wine once. I think a lot was left on.....

How can I start over from scratch or fix this problem. Any help would be great!

**Update** I think I messed up something when I tried to copy my modulles from my pc and into my home folder in esword......

I think the application is not reading the modules I have. Is there a terminal command to rebuild this???

---

### Post by david_kt on 2008-04-27
> **canadianbaptist said:**
> 
**Update** I think I messed up something when I tried to copy my modulles from my pc and into my home folder in esword......

I think the application is not reading the modules I have. Is there a terminal command to rebuild this???

Let me understand this issue:
You could not see any text at all or you just not seeing the modules?

DK

---

### Post by canadianbaptist on 2008-04-27
> **david_kt said:**
> Let me understand this issue:
You could not see any text at all or you just not seeing the modules?

DK

Thanks for the reply! I can't see any text in the Bible section. I first installed it and was VERY happy. I then copied my favorite commentary into the esword folder in my home folder. From that time on I can't see any Bibles.

Now if I do a search in the search pane I can see scripture with the results of the search, I think esword "looks" to a particular folder and I broke it. I either need to rebuild something or reinstall.

If I uninstall esword and wine it is still left behind in applications - wine

I think if I can completely wipe out what I did and start over... it would work.

I need this to work. Thanks for your help

---

### Post by david_kt on 2008-04-27
> **canadianbaptist said:**
> Thanks for the reply! I can't see any text in the Bible section. I first installed it and was VERY happy. I then copied my favorite commentary into the esword folder in my home folder. From that time on I can't see any Bibles.

Now if I do a search in the search pane I can see scripture with the results of the search, I think esword "looks" to a particular folder and I broke it. I either need to rebuild something or reinstall.

If I uninstall esword and wine it is still left behind in applications - wine

I think if I can completely wipe out what I did and start over... it would work.

I need this to work. Thanks for your help

I dont really understand the problem, but to reinstall is very easy. Just delete the ~/.wine_Esword folder, and start the installation from the begining. Another option is to copy the drive_c, system.reg, user.reg, and userdef.reg from ~/.wine_Esword folder in gutys Gutsy to ~/.wine_Esword in Hardy, it would work without any reinstallation. Please let me know if you need further help.

DK

---

### Post by canadianbaptist on 2008-04-27
> **david_kt said:**
> I dont really understand the problem, but to reinstall is very easy. Just delete the ~/.wine_Esword folder, and start the installation from the begining. Please let me know if you need further help.

DK

I have done this for about 3 hours last night. It is leaving stuff behind because I don't have to put the dll's into the system 32 folder again.

I am using the instructions here :[http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

Can you see any problems? Is there a way to remove the "bottle" and  wine?

---

### Post by david_kt on 2008-04-27
> **canadianbaptist said:**
> I have done this for about 3 hours last night. It is leaving stuff behind because I don't have to put the dll's into the system 32 folder again.

I am using the instructions here :[http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

Can you see any problems? Is there a way to remove the "bottle" and  wine?

I think you will need to restart your computer to clean programs stuck in memory. I have not tried it myself with hardy without putting the dll into system 32 folder, but if it still work after restart, may be the built in dll somehow could work already. But to be on the safe side, please put the downloaded dll to system32.

To make it easy, if after installation it did not work, you could try to copy three folders from gutsy to hardy, see my previous post a few minutes ago.

DK

---

### Post by canadianbaptist on 2008-04-27
> **david_kt said:**
> I think you will need to restart your computer to clean programs stuck in memory. I have not tried it myself with hardy without putting the dll into system 32 folder, but if it still work after restart, may be the built in dll somehow could work already. But to be on the safe side, please put the downloaded dll to system32.

To make it easy, if after installation it did not work, you could try to copy three folders from gutsy to hardy, see my previous post a few minutes ago.

DK


Ok, I have started over. I have reinstalled ubuntu (no more dual booting) I am going to install esword in a bit but I want some advice how a few things

1. The wine I am using is the up to date one... is it ok

2. The dll's should be in lower case right? 2 of them are in upper case but just in the ".dll" part. Does this matter? I was changing them to lower case anyways

3. When I paste into system 32 folder the first time it said something about ONE of the dll's being there already. I think I just replaced. Is this what messed it up?

= I want to "redo" it but I want input first. ... **Anybody??**

---

### Post by david_kt on 2008-04-27
> **canadianbaptist said:**
> Ok, I have started over. I have reinstalled ubuntu (no more dual booting) I am going to install esword in a bit but I want some advice how a few things

1. The wine I am using is the up to date one... is it ok

2. The dll's should be in lower case right? 2 of them are in upper case but just in the ".dll" part. Does this matter? I was changing them to lower case anyways

3. When I paste into system 32 folder the first time it said something about ONE of the dll's being there already. I think I just replaced. Is this what messed it up?

= I want to "redo" it but I want input first. ... **Anybody??**

1. Latest wine should be ok ( I am running latest wine in Hardy without any problem)
2. Change all dll to lowercase.
3. Yes, just replace it. You could always get the original dll by making new wine bottle.

DK

---

### Post by canadianbaptist on 2008-04-28
> **david_kt said:**
> 1. Latest wine should be ok ( I am running latest wine in Hardy without any problem)
2. Change all dll to lowercase.
3. Yes, just replace it. You could always get the original dll by making new wine bottle.

DK


Thank you sooooo much for your help. I have figured it out! I totally uninstalled ubuntu and reinstalled. I then had the same problem. I researched wine a bit and found you MUST run the wine config from terminal as opposed to manually. I did it from terminal and it works great!

It turned out good because I learned so much trying to figure it out!

---

### Post by david_kt on 2008-04-28
> **canadianbaptist said:**
> Thank you sooooo much for your help. I have figured it out! I totally uninstalled ubuntu and reinstalled. I then had the same problem. I researched wine a bit and found you MUST run the wine config from terminal as opposed to manually. I did it from terminal and it works great!

It turned out good because I learned so much trying to figure it out!

Now I understand the problem. The wine config has to be run from terminal, as in the instruction. May be I should edit the instruction to make it clear.

If you run from the menu, wine config configure the default wine. Whereas this instruction is to use special bottle for e-sword, to avoid conflict with other program you might want to run with wine .

Also, if you double click on the eSword.exe file for example (not the launcher), it would run in the default wine and it won't work, unless you configure the default wine as well to suit esword.

DK

---

### Post by kneewax on 2008-04-30
Hi Guys,  I had some problems with WINE so I removed it and the installed apps and have done a fresh install.  I reinstalled esword as per instructions, except that I used the latest release 7.9.8 (I was using 7.9.7).  Now I have a strange problem, if I try to use the scripture reference lookup the moment I hit enter to navigate to my chosen passage e-sword closes.  I get no error message, it just shuts itself down.

Any one got any ideas on this?

Cheers
Kneewax

---

### Post by pistos on 2008-05-01
> **kneewax said:**
> Hi Guys,  I had some problems with WINE so I removed it and the installed apps and have done a fresh install.  I reinstalled esword as per instructions, except that I used the latest release 7.9.8 (I was using 7.9.7).  Now I have a strange problem, if I try to use the scripture reference lookup the moment I hit enter to navigate to my chosen passage e-sword closes.  I get no error message, it just shuts itself down.

I have the same problem with eSword. But, I don't think it has to do with the version of eSword you are running. I think it has to do with WINE, because I am running eSword 7.9.5. A friend of mine has the same problem too, but he is running 7.9.8. We both have the latest version of WINE installed.

---

### Post by kneewax on 2008-05-01
> **pistos said:**
>  We both have the latest version of WINE installed.

Ah-ha the plot thickens! I think Hardy (Which I am using) has the latest version of Wine, and I suspect the Gusty installation I was using e-sword with before was using the previous or an older version, where this worked...

Does anyone know if this DOES work on older versions of Wine?

---

### Post by Eutaw on 2008-05-01
One of the bits of advice somewhere in this forum suggested that we LOCK wine once we got it working, because sometimes when the next version or update comes through it quits working right. I had e-Sword working under Gutsy, and just did the upgrade without unlocking wine. It's working fine for me, so you should probably go back a version on wine and then lock it.

---

### Post by pistos on 2008-05-03
Good news... the newest version of WINE has fixed the bug in eSword. Update WINE and you will be golden again.  :)

---

### Post by krash182 on 2008-05-09
Thank you,  I had to reinstall the .dll's four times and edit the library from the application, not with terminal for it to work but it is now working well after only two weeks of playing with wine.  only with your help could I get it to work at all.  Ernie

---

### Post by mtcycler on 2008-05-09
I am running the latest version of wine and e-sword, but it doesn't work right, if I run the bible search it closes e-sword, and it tells me that it can't find module msls31.dll when I try to scroll from verse to verse. msls31.dll is in the proper file (I have downloaded it and put it there several times and replaced it I know it is there). If I don't put the mouse over the text part of e-sword  (like over the task bar or menu bar) it will not give me the error, and I can read what is on the screen but if I try to move the scroller it gives me the error.

I am still new at this so keep it simple.

Thanks

---

### Post by david_kt on 2008-05-10
> **mtcycler said:**
> I am running the latest version of wine and e-sword, but it doesn't work right, if I run the bible search it closes e-sword, and it tells me that it can't find module msls31.dll when I try to scroll from verse to verse. msls31.dll is in the proper file (I have downloaded it and put it there several times and replaced it I know it is there). If I don't put the mouse over the text part of e-sword  (like over the task bar or menu bar) it will not give me the error, and I can read what is on the screen but if I try to move the scroller it gives me the error.

I am still new at this so keep it simple.

Thanks

I am running Hardy, wine 0.9.59, and latest e-sword without any problem. Offcourse I update the e-sword instead of fresh install.

Could you confirm:
1. where you put your msls31.dll
2. how you run the  and also how you run the setup798.exe

Please write the above two as detail as possbible for to understand the problem.

DK

---

### Post by jerrallan on 2008-05-17
Hello, I have installed wine 9.59 and followed the instructions to install e-sword 7.9.8. I am using Ubuntu 8.04. I dual boot and have e-Sword installed in Windows XP.
 
All of the 4 dll files seem to be properly installed in the wine_esword directory and the cases are all lower case.

I can run the basic e-Sword with no problems. I am unable to install the modules.  I am trying to install esv.exe  right now.

Using the env WINEPREFIX=~/.wine_Esword wine "C:\Program Files\e-Sword\esv.exe" , I get
preloader: Warning: failed to reserve range 00000000-60000000
wine: cannot find 'C:\Program Files\e-Sword\esv.exe'
 
Using the env WINEPREFIX=~/.wine_Esword WINEDLLOVERRIDES="riched20=n" WINEDLLOVERRIDES="riched32=n" wine bbe.exe [substituting esv.exe for bbe.exe]
the install wizard comes up and it freezes. 

The esv.exe is in the Places>Home Folder. I am operating from name@name-desktop.

I have read through the threads but can't find a solution.

Help!  And Thanks.

---

### Post by david_kt on 2008-05-17
> **jerrallan said:**
> 
Using the env WINEPREFIX=~/.wine_Esword wine "C:\Program Files\e-Sword\esv.exe" , I get
preloader: Warning: failed to reserve range 00000000-60000000
wine: cannot find 'C:\Program Files\e-Sword\esv.exe'
 
Using the env WINEPREFIX=~/.wine_Esword WINEDLLOVERRIDES="riched20=n" WINEDLLOVERRIDES="riched32=n" wine bbe.exe [substituting esv.exe for bbe.exe]
the install wizard comes up and it freezes. 

The esv.exe is in the Places>Home Folder. I am operating from name@name-desktop.

I have read through the threads but can't find a solution.

Help!  And Thanks.

The correct code is 
```
env WINEPREFIX=~/.wine_Esword WINEDLLOVERRIDES="riched20=n" WINEDLLOVERRIDES="riched32=n" wine esv.exe
```

NOT

```
env WINEPREFIX=~/.wine_Esword wine "C:\Program Files\e-Sword\esv.exe"
```

And the installer freeze due to some error (or different version) in one of the downloaded dll. You could try to copy the 4 dll from you windows partition to:

~/.wine_Esword/drive_c/windows/system32

DK

---

### Post by jerrallan on 2008-05-17
David, reinstalled the dll's and the other routine.  Got a lot of errors, but it worked.

Thanks. Now I can use this great program on Ubuntu.

---

### Post by david_kt on 2008-05-18
I have updated the instruction to suit wine-1.0-rc1. Only need to download msls31.dll and copy riched20.dll from e-Sword folder.

Another improvement on wine is there is no need to do dlloverrides anymore to install module.

Please check updated instruction on my first post in this thread. I have checked it work perfectly, including able to see graphic viewer (as before) but with less dll to download. This is due to the improvement wine has made so far.


Further thought, I am not sure why msls31.dll is still non-existent in wine, or is there any other way to deal with it except to use original msls31.dll?

DK

---

### Post by jesse100 on 2008-05-22
I am still working through the issue of internet access so I can't download anything. I installed esword via wine. Great except I have no Bible or content. 

I then tried installing modules as per instructions. The setup wizard hangs up every time. 

What could be the problem? 

Thanks,

Jesse

---

### Post by david_kt on 2008-05-22
> **jesse100 said:**
> I installed esword via wine. Great except I have no Bible or content. 

I then tried installing modules as per instructions. The setup wizard hangs up every time. 

What could be the problem? 

Thanks,

Jesse

What is the wine version you are using? And what do you mean by "no bible or content"?

If you mean you did not see any text at all after installing e-Sword, I guess you need to copy the riched20.dll and set the dlloverrides. Please check again whether or not you have done this correctly.

DK

---

### Post by jesse100 on 2008-05-23
DK,

The esword has no bible or anything. I just downloaded the UCE today so it would be the latest I guess. I will have to check that on that machine. 

The dll to copy and the dll overrides you mentioned... is that covered in this thread? 

I am a newbie so bear with me. 

Thanks,

Jesse

---

### Post by david_kt on 2008-05-23
> **jesse100 said:**
> DK,

The esword has no bible or anything. I just downloaded the UCE today so it would be the latest I guess. I will have to check that on that machine. 

The dll to copy and the dll overrides you mentioned... is that covered in this thread? 

I am a newbie so bear with me. 

Thanks,

Jesse

Oh IC. You are using deb in ubuntu CE. This thread is a general guidelines, could be used on any distro, including UCE offcourse. Please check the first post of this thread, and follow it carefully. You would have e-Sword fully running. By the way, this  instruction is for wine RC 1, so, please check your wine version. If you have older wine, you still could tried it, and I will post you older instruction if it did not work.

DK

---

### Post by jesse100 on 2008-05-23
Thanks DK. I am very new at this so I am slowly going through what your first post says to do. I am curious. What distro would you recommend to me (taking into account I am a newbie). I like the ubuntu so far. I have tried freespire, openGEU and UCE. Any advice?

Jesse

---

### Post by david_kt on 2008-05-23
> **jesse100 said:**
> Thanks DK. I am very new at this so I am slowly going through what your first post says to do. I am curious. What distro would you recommend to me (taking into account I am a newbie). I like the ubuntu so far. I have tried freespire, openGEU and UCE. Any advice?

Jesse

I guess you should use original ubuntu (as I use it as well). The reason is it is easier to get support from ubuntu forums. One thing very important for newbie is support.

Linux mint is another candidate for you to try. It is ubuntu with some tweak to run most of the function you need. But it has not release the hardy heron based yet.

DK

---

### Post by jesse100 on 2008-05-28
Thanks DK for the advice. I bought the "Official" Ubuntu book with the dvd and installed it on my laptop. I have since gotten the modem to work and I am up and running. I have installed eSword and all is right with the world. You are so right. Although I found others "slicker" looking and maybe a little easier to get around in the best supported one is the way to go. Ubuntu is.

Now if I can just get my ATT aircard to work with it...

Agape,

Jesse
[www.alfphc.com](www.alfphc.com)
[jesserolandministries.tripod.com](jesserolandministries.tripod.com)

---

### Post by david_kt on 2008-05-28
> **jesse100 said:**
> 

Now if I can just get my ATT aircard to work with it...

Agape,

Jesse
[www.alfphc.com](www.alfphc.com)
[jesserolandministries.tripod.com](jesserolandministries.tripod.com)

You could post your problem to other forum, may be beginner forum, hardware and laptop, networking and wireless, or other appropriate forum in ubuntu.
This thread may give some help for you:

 [AT&T aircard 875 help]("http://ubuntuforums.org/showthread.php?p=3952335")

DK

---

### Post by jesse100 on 2008-05-30
Thank you I am working on it. The ATT site has some instructions to. Lots of confusing stuff but I will keep at it. 

Another question... is a firewall and virus scanner necessary for linux? 

Which ones?

Jesse

---

### Post by david_kt on 2008-05-30
> **jesse100 said:**
> 

Another question... is a firewall and virus scanner necessary for linux? 

Which ones?

Jesse

I have been using it for more than 1 year without firewall and virus scanner, and so far there is no problem. I suggest you just leave firewall and virus scanner for later part, after you have nothing else to tweak to make you box/laptop running fully.

DK

---

### Post by brambling21 on 2008-05-31
I found it easier to install e-Sword using Crossover than using Wine, maybe try downloading a trial version of the software and see if you can install it with that.

[http://farm3.static.flickr.com/2402/2540033166_c7efe08444_o.png](http://farm3.static.flickr.com/2402/2540033166_c7efe08444_o.png)

A fully working free trial version can be downloaded from:

[http://www.codeweavers.com/products/](http://www.codeweavers.com/products/)

---

### Post by Holzster on 2008-06-15
I got E-Sword installed fine - but I looked for 3 hours here how do I install the bibles - everyone say to copy from windows - I do not have windows.  I tries installing the exe's through wine but it just hangs

thanks

---

### Post by jonathonblake on 2008-06-15
> **Holzster said:**
> everyone say to copy from windows - I do not have windows.

* Are you installing resources from e-Sword.net and eStudySource, or user created resources?
* What happens when you use the e-Sword Resource Installer, pointing it to resources on your hard drive/DVD?

xan

jonathon

---

### Post by Holzster on 2008-06-15
What is the e-Sword Resource Installer?

I am downloading the exe's from esword then using wine.  But it times out or gives me an error that I must have esword version 6 or newer - I am using version 7.9.8

thanks

---

### Post by jonathonblake on 2008-06-15
> **Holzster said:**
> What is the e-Sword Resource Installer?

It is a utility included in Ubuntu Christian Edition 3.x, that installs resources for e-Sword.  

Download the files from e-sword.net manually.   Then point it at the download location, to install them for you.

xan

jonathon

---

### Post by david_kt on 2008-06-15
> **Holzster said:**
> What is the e-Sword Resource Installer?

I am downloading the exe's from esword then using wine.  But it times out or gives me an error that I must have esword version 6 or newer - I am using version 7.9.8

thanks

1. Which wine version are you using?
2. Did you follow the instruction at the beginning of this thread? 

DK

---

### Post by greatnw on 2008-06-25
Used the instructions provided to install E-Sword on my IBM T41 running Mandriva 2008.1. Mandriva is by far the simplest and best working distro on my machine. 

Simple instructions, up and running right away. I did notice that while I had Compiz running when installing modules the system would crash after the fourth of fifth install. Turned off Compiz, completed all the modules and turned Compiz back on. Flawless!

Works better than when I had E-Sword running on an older Toshiba with Ubuntu 7.1. 

Thanks so much. E-Sword, Quicken, TopoUSA and other mapping software keep me tied to XP more than I care for. I dual boot but prefer Linux. 

E-Sword is the best bible software going.

---

### Post by gpxfactor on 2008-06-25
> **david_kt said:**
> Please run 

```
env WINEPREFIX=~/.wine_Esword winecfg
```

and on library set riched20.dll and oleaut32.dll to native for e-sword.exe.
That would solve your problem. But I still could not install addon yet using gutsy.

DK

I figure that this was proably solved (seeing that there are 17 pages on it) but this is how I solved it anyways:
1. After install and copy they dll files (riched20.dll and msls31.dll , note text case) then I open the winecfg ("configure wine" in the menu).
2. I then added e-sword.exe (locate it in the wine drive "~/.wine/c_drive/Program Files/e-Sword/e-Sword.exe".
3. Go to the libraries tab and add two overrides riched20.dll and oleaut32.dll. Set both to native.

That should work for you. Start up e-Sword and try.

---

### Post by mtcycler on 2008-06-29
dk
mtcycler again, I am on a different computer and have put the msls31.dll in the correct spot I am sure, but e-Sword does not see it, any ideas?
Thanks

---

### Post by david_kt on 2008-06-29
> **mtcycler said:**
> dk
mtcycler again, I am on a different computer and have put the msls31.dll in the correct spot I am sure, but e-Sword does not see it, any ideas?
Thanks

Either you need to restart your computer, or the e-sword you install in the wrong spot.

Please check how you install e-sword, was it in the special bottle or default bottle. And then, put the msls31.dll to the same bottle of your esword.

DK

---

### Post by jerrallan on 2008-07-07
This is a great guide.  I had to reinstall Ubuntu because of a crash. Reinstalled wine and e-sword flawlessly in about ten minutes.

I did do some drag and drop of the dll files into windows 32.

Great howto here and E-Sword is one terrific application for the money. It beats the $200 programs too.

---

### Post by rcdeacon on 2008-07-15
I looked with great interest at this thread but after doing a fresh install of Hardy and the latest wine from the repos's and E-sword I get error messages when starting E-sword. These messages have to do with files like markup.ovl and study.not. Apparently they cannot be found or are in the wrong place. When I installed wine from the repos I simply clicked on setup798.exe and went with the flow. (I had already taken care of the rich20 and oleaut files) After a string of error messages e-sword comes up and works fine. I would like to know how can I get rid of these errors?

---

### Post by david_kt on 2008-07-15
> **rcdeacon said:**
> I looked with great interest at this thread but after doing a fresh install of Hardy and the latest wine from the repos's and E-sword I get error messages when starting E-sword. These messages have to do with files like markup.ovl and study.not. Apparently they cannot be found or are in the wrong place. When I installed wine from the repos I simply clicked on setup798.exe and went with the flow. (I had already taken care of the rich20 and oleaut files) After a string of error messages e-sword comes up and works fine. I would like to know how can I get rid of these errors?

If you just clicked on setup798.exe, you should do all the tweak in the default wine as well. Instead of running

```
env WINEPREFIX=~/.wine_Esword winecfg

```
run:

```
winecfg
```

and add the dll overrides.

And instead of

```
cp ~/.wine_Esword/drive_c/Program\ Files/e-Sword/riched20.dll ~/.wine_Esword/drive_c/windows/system32
```

run

```
cp ~/.wine/drive_c/Program\ Files/e-Sword/riched20.dll ~/.wine/drive_c/windows/system32
```

And to install addon, just click on the exe file.

After that, all should be ok. Please let me know if you still have problem. I am running wine 1.1.1 now and it is still running well.

DK

---

### Post by rcdeacon on 2008-07-15
OK, thanks but let me see if I understand properly. Although I DID "add" the rich20.dll and the oleaut.dll file they need to be copied to a different directory? (cp is the command to copy I think) I also added another file to the system32 directory (msls31?)

---

### Post by rcdeacon on 2008-07-15
I had to post back with the exact error message. This may make sense to someone who can steer me in the right direction. The error message is as follows;

"The Microsoft Jet Database engine cannot open the file C:\windows\profiles\bob\My Documents\e-sword\markup.ovl. It is already opened exclusively by another user, or you need permission to view its data. 3051"

There are other errors similar in context where it is looking for the file study.not. I'm not sure if I need to uninstall and start again with e-sword or not.

---

### Post by david_kt on 2008-07-15
> **rcdeacon said:**
> I had to post back with the exact error message. This may make sense to someone who can steer me in the right direction. The error message is as follows;

"The Microsoft Jet Database engine cannot open the file C:\windows\profiles\bob\My Documents\e-sword\markup.ovl. It is already opened exclusively by another user, or you need permission to view its data. 3051"

There are other errors similar in context where it is looking for the file study.not. I'm not sure if I need to uninstall and start again with e-sword or not.

Looks like you have installed other things or ever install other thing in the default wine. That is why I make the instruction in the beginning of this thread to use special bottle, used for e-sword only. This is to avoid this kind of problem.

Could you try to install e-sword using the instruction at the beginning of this thread, and let me know the result. Also please let me know you wine version.

DK

---

### Post by rcdeacon on 2008-07-15
Thanks DK I will try to reinstall. I have not installed anything else in wine but e-sword but I did not use the method outlined in this thread either. So I will remove wine, remove e-sword and start from scratch. Thanks. I have wine 1.0 installed BTW.

---

### Post by rcdeacon on 2008-07-15
No joy! I removed wine, I removed e-sword. Then I followed the instructions but the same problem persists. E-sword will run but I have to go through a series of error messages first.

---

### Post by rcdeacon on 2008-07-15
OK. Not sure what happened but I logged out to do some work as root and when I logged back in and started e-sword it worked without the error messages.

---

### Post by david_kt on 2008-07-15
> **rcdeacon said:**
> OK. Not sure what happened but I logged out to do some work as root and when I logged back in and started e-sword it worked without the error messages.

Ah, I forgot to inform you. Sometime wine stuck and you need to reboot. Or, if you do not want to reboot, open terminal and run (one at a time):

```
killall wine
killall wineserver
killalll wine-preloader

```

This is to make sure all wine processes are removed from the memory, which could prevent wine from working properly. I have added more detail instruction on troubleshooting section in the first post of this thread.

DK

---

### Post by rcdeacon on 2008-07-16
DK thanks for all the help. It is very appreciated.

---

### Post by rcdeacon on 2008-07-16
Had to do the same thing for my Dell Dimension desktop. Worked great! Thanks.

---

### Post by seuzy13 on 2008-07-24
I am still getting an error when I try to install addons.

It freezes on the "Preparing wizard, please wait" screen, and I get this error in the terminal:
"fixme:richedit:RichEditWndProc_common EM_FORMATRANGE: stub"
which proceeds to repeat itself over and over.

I did add riched20, riched32, and oleaut32 as overrides in wine config. However, strangely when I run this command: WINEDLLOVERRIDES="riched20=n" WINEDLLOVERRIDES="riched32=n" wine asv.exe
I do not get any errors, but it still freezes at the same screen. When I throw oleaut32=n into the mix, the errors come back.

Help would be appreciated. Thanks.

---

### Post by david_kt on 2008-07-24
> **seuzy13 said:**
> 

I did add riched20, riched32, and oleaut32 as overrides in wine config. However, strangely when I run this command: WINEDLLOVERRIDES="riched20=n" WINEDLLOVERRIDES="riched32=n" wine asv.exe
I do not get any errors, but it still freezes at the same screen. When I throw oleaut32=n into the mix, the errors come back.

Help would be appreciated. Thanks.

First of all, only 2 overrides are needed, we do not need riched32 overrides (please check the first post on this part):

In winecfg set riched20.dll and oleaut32.dll to native. IMPORTANT: Do not run winecfg from menu, as it would run default winecfg. 

Could you try again (killall wine process first) without riched32 overrides?

By the way, is the main program (e-sword) running as normal and you are only unable to install addon? And what is your wine version?

DK

---

### Post by seuzy13 on 2008-07-25
Okay, I tried without riched32, and I get this error:
wine: Call from 0x7ee055ba to unimplemented function riched20.dll.RichEdit10ANSIWndProc, aborting
wine: Call from 0x7ee055ba to unimplemented function riched20.dll.RichEdit10ANSIWndProc, aborting

eSword by itself is working perfectly. I am using wine 1.0.

---

### Post by david_kt on 2008-07-25
> **seuzy13 said:**
> Okay, I tried without riched32, and I get this error:
wine: Call from 0x7ee055ba to unimplemented function riched20.dll.RichEdit10ANSIWndProc, aborting
wine: Call from 0x7ee055ba to unimplemented function riched20.dll.RichEdit10ANSIWndProc, aborting

eSword by itself is working perfectly. I am using wine 1.0.

I guess you are using old instruction, i.e. you download 4 dlls. For later wine (not sure since which version), those dlls will cause the addon could not run.

So, could you please repeat your installation, using the updated instruction (only download 1 dll i.e. msls31.dll). And one more dll is riched20.dll, copy it from e-sword folder, do not download. Please refer the the first post of this thread for the details, including the troubleshooting section.

DK

---

### Post by seuzy13 on 2008-07-25
That did it. Thanks!

---

### Post by rcdeacon on 2008-07-26
I have installed with these instruction before and all went well but that is not the case this time. The only way I can get e-sword to start is with the command line. There was NO icon placed on the desktop other than the e-sword.lnk icon which does not work. The usual icon was not placed. I tried a custom launcher and that would not work either. Not sure what to do at this point.

---

### Post by david_kt on 2008-07-27
> **rcdeacon said:**
> I have installed with these instruction before and all went well but that is not the case this time. The only way I can get e-sword to start is with the command line. There was NO icon placed on the desktop other than the e-sword.lnk icon which does not work. The usual icon was not placed. I tried a custom launcher and that would not work either. Not sure what to do at this point.

There are 3 things you could try:

1. Normally it is still avialable from the menu. Go to menu:

Application> Wine> Program > e-Sword > e-Sword (right click on this menu and select "add this launcher to desktop"

2. Add manually. One way to make the launcher work is to use absolute path in the command:
```
env WINEPREFIX="/home/Your_User_Name/.wine_Esword" wine "C:\Program Files\e-Sword\e-Sword.exe"
```
Replace Your_User_Name with actual user name you are using.
And after that you could use the icon attached on the first post of this thread.

3. Try to re-install e-Sword again, make sure you kill all processes related to wine before re-install.

DK

---

### Post by Dr Small on 2008-07-27
I am trying to install the kjvr.exe addon, but when I run:
```
env WINEPREFIX=~/.wine_Esword wine kjvr.exe
```

I get:
```
err:module:import_dll Library riched20.dll (which is needed by L"C:\\windows\\system32\\riched32.dll") not found
```

I have followed your guide every step of the way, and have e-sword working flawlessly, except for this one thing.


Edit, Fixed.
I was copying riched20.dll to the wrong system32/

Dr Small

---

### Post by rcdeacon on 2008-07-27
David_kt,
I finally got an icon by doing a "repair" of the installation. I do however get an error regarding the "markup.ovl" file but that is not a real showstopper. At least I can start up e-sword from the desktop now. Thanks.

---

### Post by mtcycler on 2008-08-07
I have E-Sword working... sort of...
I can open E-Sword and read the "Tip of the Day" but there is no bible and I can't install asv.exe

I have wine 1.0
E-Sword 7.9.8

---

### Post by david_kt on 2008-08-07
> **mtcycler said:**
> I have E-Sword working... sort of...
I can open E-Sword and read the "Tip of the Day" but there is no bible and I can't install asv.exe

I have wine 1.0
E-Sword 7.9.8

Did you follow the updated instruction in the first post? If yes, there are two possible mistake:

1. You did not copy riched20.dll from e-sword folder to the right place (system32 directory at the right "bottle").
2. The dll overrides for riched20.dll is not in the correct bottle

DK

---

### Post by david_kt on 2008-08-08
I have added instruction to backup E-sword istallation in case your box crashed or you want to reinstall your operating system. By following this instruction, it would save you the hassle of re-installing e-sword and you would not lose your setting or whatever work you have done on e-sword. It could also be done to replicate your e-sword from one box to another, without the need to manually install it.

Please check the first post of this thread, right at the end of that post. And please feed back to me if you face any problem.

DK

---

### Post by brambling21 on 2008-08-24
e-Sword does run under Ubuntu, I got it running under Xubuntu 8.04 with very few problems, however, and very sadly, I need to use Windows to install the modules on a Win32 install of e-Sword, then copy the modules over to the Linux folder where e-Sword is installed, Codeweavers Crossover seems to be a bit better than Wine at this point, but not really all that much better.

Hopefully things will improve in the future.

---

### Post by david_kt on 2008-08-25
> **brambling21 said:**
> e-Sword does run under Ubuntu, I got it running under Xubuntu 8.04 with very few problems, however, and very sadly, I need to use Windows to install the modules on a Win32 install of e-Sword, then copy the modules over to the Linux folder where e-Sword is installed, Codeweavers Crossover seems to be a bit better than Wine at this point, but not really all that much better.

Hopefully things will improve in the future.

Could you let me know 
1. Which wine version are you using? 
2. Did you follow the latest instruction on the first post (only use 1 downloaded dll i.e. msls31.dll)?

DK

---

### Post by david_kt on 2008-09-01
Update:
I have added automatic installer that would:
1. Download and install E-sword 798
2. Copy riched20 to correct location
3. Download msls31.dll
4. Set dlloverrides for riched20 and oleaut32

All are done in special bottle (.wine_Esword).
Download Esword_installer.tar.gz  from the first post of this thread and then extract it.
Make sure it is executable (right click on the extracted file (Esword_installer) >> click properties >> click permision tab >> and then tick on the execute (Allow executing file as program).
Double click on Esword_installer to run it

It has been tested using wine-1.0 and e-Sword Version 7.9.8. It run without any problem on ubuntu 8.04 (Hardy Heron).
You could use this how to theoritically in any distro running wine, not just ubuntu.

---

### Post by david_kt on 2008-09-01
I have included selected addons in the installer. If your favourite addon is not there, please let me know so that I could include it in the installer.

DK

---

### Post by Ecna on 2008-09-02
Dude. The windows version needs a script like this, so I don't have to download all addon installers manually. Great work david_kt.

As for requests for selected addons, I'd love to see the HOT+, and the Wescott Hort version of the greek NT. As well as Thayer's dictionary. 

Also, after installing addons manually, the script exits silently. It would be nice if there was a simple "Installation Complete" message, so I know it hasn't crashed before finishing up.

---

### Post by david_kt on 2008-09-03
> **Ecna said:**
> Dude. The windows version needs a script like this, so I don't have to download all addon installers manually. Great work david_kt.

As for requests for selected addons, I'd love to see the HOT+, and the Wescott Hort version of the greek NT. As well as Thayer's dictionary. 

Also, after installing addons manually, the script exits silently. It would be nice if there was a simple "Installation Complete" message, so I know it hasn't crashed before finishing up.

I have added HOT+, Wescott Hort version of the greek NT, and Thayer's dictionary. Please download again the installer in the first post of this thread.

But for manual install, I still do not how to pop up a message, even in terminal, to inform installation is completed. Because I am just using winefile to run the program. I will learn again to improve it in near future, but no promise as I am not a programmer. I just copy and paste all the codes, with some modification.

DK

---

### Post by david_kt on 2008-09-03
> **Ecna said:**
> Also, after installing addons manually, the script exits silently. It would be nice if there was a simple "Installation Complete" message, so I know it hasn't crashed before finishing up.

After studying for a couple of hours, now I have inlcuded your suggestion in installing addons manually i.e. it would give a pop up message the program crash (regardless you run it in terminal or not) or inform "Install of manual done" in terminal if the program completed without error (provided you run it in terminal).

DK

---

### Post by Shabakthanai on 2008-09-03
> **ggaines1 said:**
> trying to install esword in ubuntu 7:10,  keeps hanging on install have tried debian packag e and allows me to load all modules but wont configure, tried wine install instructions and when I get to this point /home/gregory/.wine/drive_c/windows/system32/setup785.exe
 
It hangs saying looking for location for files but box hangs and can get no farther.
any advice would be apreciated, 

I am very much a beginner to ubuntu

thanks
I am old with poor retention, so I will try to explain.  I am also self taught in using a computer and never had much help.  Before I read your post, I already  attempted to install e-Sword, also Wine.  I used Adept Package Manager 3.5.9.  My OS is Kubuntu 8.04.  The installation failed.  When I read your instructions they seemed to be written as though neither Wine or e-Swore were installed.  Because I had installed them, I attempted to add your instructions that were missing.  Unfortunately this installation failed too.  I installed Wine using Adept, but not e-Sword.  I attemmpted to download e-Sword using the Wine program.

My question is this. Should I uninstall e-Sword and Wine over then apply your instructions; what do you advise?  I have a small ministry where I am counciling people on spiritual matters, who can not see very well.  Because e-Sword has the capability to increase the font, I am sure my laptop will help them.

I have e-Sword on my desktop using the same OS and Desktop, however it took me about a year to get it installed and I can't remember what I did that finally made it work.  If I knew what files to transfer, I suppose I could copy them on my thumb drive and paste them into the laptop, but this wouldn't make the original installation work, would it?  I am sorry to trouble you with my problems; I have no  one willing or able to help me here.  Thanks if you are willing.  In CHRIST, Steven

---

### Post by david_kt on 2008-09-03
> **Shabakthanai said:**
>  I used Adept Package Manager 3.5.9.  My OS is Kubuntu 8.04.  The installation failed.  When I read your instructions they seemed to be written as though neither Wine or e-Swore were installed. 

My question is this. Should I uninstall e-Sword and Wine over then apply your instructions; what do you advise?  

I have e-Sword on my desktop using the same OS and Desktop, however it took me about a year to get it installed and I can't remember what I did that finally made it work.  If I knew what files to transfer, I suppose I could copy them on my thumb drive and paste them into the laptop, but this wouldn't make the original installation work, would it? 

Hi Steven,

Wine must be installed before following the instruction. I suggest you use wine 1.0 as higher wine cause problem during installation. 

So to make sure it is wine 1,0. please remove wine:

```
sudo apt-get remove wine
```

After that, download wine 1.0 from below link:

[http://wine.budgetdedicated.com/archive/ubuntu/hardy/wine_1.0.0~winehq0~ubuntu~8.04-1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/hardy/wine_1.0.0~winehq0~ubuntu~8.04-1_i386.deb)

and double click to install it. You also need to install cabextract:

```
sudo apt-get install cabextract
```

Download the installer below:

[http://ubuntuforums.org/attachment.php?attachmentid=83909&d=1220457406](http://ubuntuforums.org/attachment.php?attachmentid=83909&d=1220457406)

right click the downloaded file (Esword_installer.tar.gz) >> click "extract here".

Right click the extracted file (Esword_installer) >> click properties >> click permission >> tick execute (allow executing file as program)

After that, double click Esword_installer and choose run. It will pop up a menu. Tick the first option (install esword) and other addon you want to install, and then click ok. It will install it automatically for you.

DK

---

### Post by cjm5229 on 2008-09-04
David, This is great! I am waiting for Intrepid Alpha 5, should be out today yet, then I am going to reinstall my Intrepid Partition with that. and try it there. My current Intrepid has eSword installed from your backup guide, and is working great.  I will let you know if it works there.

I am working on coming up with a list of Bible Study programs that will work in Wine by just directly installing them. Free programs that is:) I will put it on Jeremes Wiki when done. I have found several, but none come close to eSword. The Word comes close, especially the new Beta version, it has a module that can convert modules from other apps including some eSword, to work in it. Most of eSwords modules have been password protected by Rick Myers, and he won't allow others to use them, but some of the community eSword modules can be converted. Anyway I have tomorrow off from work so I will devote most of the day to getting that done, and testing your script in Intrepid.
Keep up the good work, and God bless you.
Carl

---

### Post by bobterri73 on 2008-09-05
Thank you so much for the detailed instructions.  I am a newbie to Ubuntu and missed having E-Sword from my other computer.  I was too new to understand what the commands were, but I followed them to the letter and the install went perfectly.

Bob S.

---

### Post by david_kt on 2008-09-05
> **bobterri73 said:**
> Thank you so much for the detailed instructions.  I am a newbie to Ubuntu and missed having E-Sword from my other computer.  I was too new to understand what the commands were, but I followed them to the letter and the install went perfectly.

Bob S.

Congratulation. By the way, did you use manual installation or automatic installer?

DK

---

### Post by joyson20 on 2008-09-09
Thanks a lot bro...I was bit worried about not having e-sword after scraping off windows as i was afraid it might not be the legal version....Thank God-He gave me some way

---

### Post by david_kt on 2008-09-09
> **joyson20 said:**
> Thank God-He gave me some way

Did you install it manually or using the installer? If you are using the installer, please feedback any improvement you want to have and I will try to add it in future installer.

DK

---

### Post by lukeelliot on 2008-09-11
Thank you so much, David, for this wonderful how-to.  I have successfully installed e-sword in Kubuntu 8.04 by following your instructions, but have encountered problems trying to install add-ons using your installer. For some reason, I only get a blue screen when I run it and even Alt Tab doesn't bring up the installation windows.  However, I have found that by blindly pushing Enter over and over, the add-ons do in fact install.  (Hopefully this post will be of help to anyone encountering the same problem).

Again, many thanks for all your hard work in making e-sword accessible for amateur Linux users like myself.

---

### Post by david_kt on 2008-09-11
> **lukeelliot said:**
>  I have successfully installed e-sword in Kubuntu 8.04 by following your instructions, but have encountered problems trying to install add-ons using your installer. For some reason, I only get a blue screen when I run it and even Alt Tab doesn't bring up the installation windows.  However, I have found that by blindly pushing Enter over and over, the add-ons do in fact install.  (Hopefully this post will be of help to anyone encountering the same problem).

Thank you for your feed back. In order to improve the instruction/installer, could you provide me with below:

1. May I know whether you installed e-sword using installer or you do it manually (i.e. download the dll manually)?
2. Which wine version you are using?

Regards,
DK

---

### Post by lukeelliot on 2008-09-11
> **david_kt said:**
> Thank you for your feed back. In order to improve the instruction/installer, could you provide me with below:

1. May I know whether you installed e-sword using installer or you do it manually (i.e. download the dll manually)?
2. Which wine version you are using?

Regards,
DK
1. Come to think of it, I installed e-sword mannually by following your instructions.  I used the installer the first time, but since no launcher appeared either on my desktop or in my K Menu I reinstalled it mannually.

2. I am using Wine version 1.0.

---

### Post by david_kt on 2008-09-12
> **lukeelliot said:**
> 1. Come to think of it, I installed e-sword mannually by following your instructions.  I used the installer the first time, but since no launcher appeared either on my desktop or in my K Menu I reinstalled it mannually.

I could confirm that addon will show blue screen only on Kubuntu/KDE but by pressing enter repeatedly it will still install successfully. But when I try in gnome, addon still run normally.

I have added a script to create desktop launcher automatically. Please download and run the new installer, choose e-sword, it will reinstall e-sword and create a desktop launcher.

DK

---

### Post by travis78 on 2008-09-13
I'm running Ubuntu Hardy Heron 8.04 and Wine 1.1.4; the instructions had to be tweaked a little for me to get e-Sword running properly. 

It was pretty much the same until winecfg. I ran it in the terminal, added the dll's under the libraries tab and switched them to native.I then opened e-Sword, but there was no text at all. The KJV+ tab showed, and the left sidebar with the bible books and chapters showed fine. Everything was there, except no text in the large center column where the bible verses or dictionary should have been. These boxes were completely blank. I tried a number of things and, through trial and error, found that I could add e-Sword.exe in winecfg. The difference was that I got to wine cfg through the menu instead of the terminal. This lets you configure wine globally, across all apps, so make sure you're configuring e-Sword when you get to that step. 

Here's what I did (I'm going off of memory from last night, but I'm pretty certain this is what I did. Of course, try tweaking it if it doesn't work exactly like this for you):

1. Go to: Applications menu>Wine>Configure Wine

2. The Applications tab should be showing. If it's not, click it. At the bottom, click "Add Application."

3. Select e-Sword.exe from Program Files>e-Sword.

4. In the Applications tab, click on e-Sword.exe to highlight it in the list.

5. Follow posted instructions for riched20.dll and oleaut32.dll: > type riched20.dll > press add > press edit > choose Native (windows).Do the same for oleaut32.dll.

6. Click "Apply" then "OK"

7. Run e-Sword by clicking on the desktop launcher. (I had no luck running it via the terminal.) The scripture verses and dictionary (try it with Strong's already packaged with e-Sword) should show now. It's not entirely perfect interface-wise (study notes don't change as you change the verse), but it's pretty close.

8. Install addons: So far I haven't been able to install any addons following the posted instructions. If anyone finds a way for Hardy 8.04 & Wine 1.1.4, post it here.

---

### Post by david_kt on 2008-09-13
> **travis78 said:**
> I'm running Ubuntu Hardy Heron 8.04 and Wine 1.1.4; the instructions had to be tweaked a little for me to get e-Sword running properly. 

8. Install addons: So far I haven't been able to install any addons following the posted instructions. If anyone finds a way for Hardy 8.04 & Wine 1.1.4, post it here.

I have tried the installer with wine 1.1.4, it could run perfectly. It fail to run e-sword uder wine 1.1.3.

Please go to first post, and download the installer attachement, and run it. It will help you to download e-sword and other addons, install and tweak it, and also create a desktop launcher for you. All are done automatically as I realize many people are very new to linux and wine and could not follow the manual instruction carefully.

The installer is 100% GUI i.e. no command line needed. Just right click on the downloaded installer and extract it. And then double click on the extracted file, choose run on terminal (or run) and follow the pop up windows. It is very suitable for beginners of linux and wine.

DK

---

### Post by zandu on 2008-09-14
Hi I get the message "missing msls31.dll " now when I try to copy it from the desktop to the list folder as per instructions , i then get a message saying ...folder does not exist. 
 any ideas ?
 thanks

---

### Post by david_kt on 2008-09-14
> **zandu said:**
> Hi I get the message "missing msls31.dll " now when I try to copy it from the desktop to the list folder as per instructions , i then get a message saying ...folder does not exist. 
 any ideas ?
 thanks

Could you try the automatic installer. Go to the first post of this thread and download the installer attached at the end of the post to your desktop, right click and choose extract it here, and double click on the extracted files, choose run on terminal. And then follow the instruction on the GUI.

DK

---

### Post by david_kt on 2008-09-15
I have just improved the installer script, now it will create desktop launcher, even better than the original launcher. When it asked for an icon, navigate to /home/username/.local/share/icons, normally the e-sword icon is already there. Or you could use any icon you want.

I have just remove a bug, before if you install e-Sword twice, the desktop launcher will not work anymore due to my mistake. But now is already corrected.

The latest script will also check for wine 1.0 and 1.1.4. But I suggest stick to wine 1.0 (stable release) as the wine development prone to have more bugs.

DK

---

### Post by zandu on 2008-09-15
Thanks David , it worked well in Linux Mint, much easier than doing it manually tho I learnt a bit by  trying .

---

### Post by david_kt on 2008-09-15
> **zandu said:**
> Thanks David , it worked well in Linux Mint, much easier than doing it manually tho I learnt a bit by  trying .

I am glad the installer help you. But if you really want to learn to installed it manually, I will try to help you. But please give me the detail of what you have done and on which state it is failing you.

The installer and the manual instruction basically is the same. If the installer works for you, the manual instruction should work as well.

DK

---

### Post by joyson20 on 2008-09-17
> **david_kt said:**
> Thank you for your feed back. In order to improve the instruction/installer, could you provide me with below:

1. May I know whether you installed e-sword using installer or you do it manually (i.e. download the dll manually)?
2. Which wine version you are using?

Regards,
DK
sorry...i did it the manual way..I am using gusty and wine 9.59

---

### Post by beta.tester on 2008-09-18
Hi David

I think it would be prudent to point out that your .deb file/installer gzip file only works on 32 bit - not 64 bit :( I customise my 64 bit Ubuntu to look like Jereme and your install doesnt work on 64 bit - sorry.

Might save a few heart aches for others :)

---

### Post by david_kt on 2008-09-18
> **beta.tester said:**
> Hi David

I think it would be prudent to point out that your .deb file/installer gzip file only works on 32 bit - not 64 bit 

Thanks for the feedback. I do not have 64 bit. But could you specify what is exactly the error and on which stage:
1. extracting the gzip
2. launching the gui
3. downloading files
4. executing exe files

DK

---

### Post by TreyKerux on 2008-09-20
worked nearly flawlessly, thanks!

---

### Post by beta.tester on 2008-09-21
> **david_kt said:**
> Thanks for the feedback. I do not have 64 bit. But could you specify what is exactly the error and on which stage:
1. extracting the gzip
2. launching the gui
3. downloading files
4. executing exe files

DK

Apologies for delay in replying, but having to do my system from scratch. Too many 32 bit applications caused major problems so hopefully will wait till a 64 bit version available as this is my "window to the world" and cannot be without it.

God bless you

---

### Post by david_kt on 2008-09-23
I have just added portable e-Sword on linux. It will help you to run e-sword on any computer with wine 0.59 and above (not tested using wine below 0.59 but might work as well).

DK

---

### Post by tananaBrian on 2008-09-24
I didn't read all zillion pages to see if anyone else answered this or not, but I found out why people have been getting the "Can't find msls31.dll" error when the mouse hovers over a Strong's reference ...When taking a look at ~/.wine_Esword/drive_c/windows/system32 for msls31.dll, I found it alright ...but the file manager seemed to think it was an HTML file, not a 'Windows Executable" like the other dlls.  Sure enough, I cat'd it and it was a short HTML page hidden inside a file named "msls31.dll".  This resulted from right-clicking and saving the file from one of the posts here rather than actually going to [http://www.dlldump.com](http://www.dlldump.com) to get the file ...my bad, and hard to spot!  Just go get the binary from dlldump and copy it to the bottle's system32 folder and all will be well!  Whew!

Brian

---

### Post by david_kt on 2008-09-24
> **tananaBrian said:**
> This resulted from right-clicking and saving the file from one of the posts here rather than actually going to [http://www.dlldump.com](http://www.dlldump.com) to get the file ...my bad, and hard to spot!  Just go get the binary from dlldump and copy it to the bottle's system32 folder and all will be well!  Whew!

Brian

Thanks for the feedback. I could not figure out what happen and there might be other problem such as download fail or incompatible dll. As such, I have made an installer, which download the dll from microsoft instead of dlldump, which is much safer. Please download the installer at the first post of this thread, extract it, and run it. It just a matter of point and click now to install e-Sword in linux. 

DK

---

### Post by tananaBrian on 2008-09-25
Hey DK ...Someone *HAS* to say this:  YOU have been nothing short of *OUTSTANDING* in your assistance in getting e-Sword to people using Linux!  I'm sure that I speak for the crowd in general when I say "Thank you!" for all the work, the persistence, the development of installers, and the whole thing... you're doing a great job and we all appreciate it!  God is being served by *YOU*! Thanks for all the great work and for your tenacity!! :)

Brian

---

### Post by jonathonblake on 2008-10-01
I'm using Ubuntu 8.04 64 bit version.

I didn't realize it would automatically download the e-Sword exectuable. :( That misunderstanding resulted in the wrong version of e-Sword being installed.

However, looking at the script, I saw where to make the edits, and now I have the right version of e-Sword.  :)

Now to migrate my e-sword resources.

###

In this instance, the "right" version is one that is being beta tested. 

xan

jonathon

---

### Post by david_kt on 2008-10-01
> **jonathonblake said:**
> I'm using Ubuntu 8.04 64 bit version.

However, looking at the script, I saw where to make the edits, and now I have the right version of e-Sword.  :)

Now to migrate my e-sword resources.

###

In this instance, the "right" version is one that is being beta tested. 

xan

jonathon

Is the 64 bit version running well? Because beta.tester informed that it did not work:
```

I customise my 64 bit Ubuntu to look like Jereme and your install doesnt work on 64 bit - sorry.
```

I am glad you could edit the script, it is very easy really. Is it running well with the beta version? If yes, I want to add the script to do:

1. Automatic back up.
2. Automatic restore

I thought it would be useful. And once the new version of e-Sword is launched, please let me know and I will edit the script.

DK

---

### Post by jonathonblake on 2008-10-02
> **david_kt said:**
> Is the 64 bit version running well? 

Thus far I haven't had any issues.

Note:I'm using a [COLOR="Red"]Beta [/COLOR] copy of e-Sword. 

[http://tech.groups.yahoo.com/group/e-Sword_l10n/?yguid=190112289](http://tech.groups.yahoo.com/group/e-Sword_l10n/?yguid=190112289) is a screenshot of e-Sword on Ubuntu 8.04 (64 bit).

I'll toss up another screenshot later on.  Something that is more akin to my normal Bible Study Style.   ( [http://www.esnips.com/user/jonathonblake](http://www.esnips.com/user/jonathonblake) has a screenshot of e-Sword with my usual complement of resources.   For obvious reasons I use a single line of tabs, rather than a multiple line of tabs.) 

> 1. Automatic back up.
2. Automatic restore

If I had thought of it when I was editing it, I would have added lines to automatically copy my resource collection from the DVDs I've archived them on.

Instead I wrote a shell script to the copying.  

xan

jonathon

---

### Post by david_kt on 2008-10-02
> **jonathonblake said:**
> Thus far I haven't had any issues.

Note:I'm using a [COLOR="Red"]Beta [/COLOR] copy of e-Sword. 



I only could find updated from old e-Sword to e-Sword beta. Is there any full installer for the beta version?

If anybody else want to try e-Sword beta, you could download it manually at:

[http://www.e-sword.net/beta.html](http://www.e-sword.net/beta.html)

And then launch the esword_installer and choose manual and navigate to the downloaded beta803.exe. It will update the old e-Sword to beta version.

If many people have difficulties in updating to e-Sword beta, I will add a script to install this beta version updater as well.

DK

---

### Post by jonathonblake on 2008-10-02
[QUOTE=david_kt]Is there any full installer for the beta version?
[/quote]

AFAIK, no.

> And then launch the esword_installer and choose manual and navigate to the downloaded beta803.exe. It will update the old e-Sword to beta version.

I've been rewriting the line for e-Sword. (I've forgotten what it said, but it looks for it in the .eswordcache folder.  (Something like that.) )

xan

jonathon

---

### Post by jonathonblake on 2008-10-03
Would it be possible to get the scripts: 
* Esword_installer_150908.tar.gz 
* e-sword_portable230908.tar.gz

Into a repository for Synaptic to retrieve, then install?

xan

jonathon

---

### Post by david_kt on 2008-10-03
> **jonathonblake said:**
> Would it be possible to get the scripts: 
* Esword_installer_150908.tar.gz 
* e-sword_portable230908.tar.gz

Into a repository for Synaptic to retrieve, then install?


I think it would be easy to do that for Jeremy, may be Jeremy could comment on this?

But bear in mind that e-sword portable is intended to be "installed" on usb.

It also could be used as backup script, but I am thinking of a better way to do back up i.e. to have one tar.gz backup file, and a script to restore from it.

If I have time, I will add that function to Esword_installer.tar.gz.

DK

---

### Post by david_kt on 2008-10-04
I have just added e-Sword 8.0.3 beta version on installer. If you want to help Rick Meyer to test the latest beta version, you just need to run the installer, and tick "beta" to upgrade your e-Sword to beta version.

It would download and install beta version for you.

If you have downloaded the beta version updater, select "manual" and navigate to the downloaded beta updater.

DK

---

### Post by david_kt on 2008-10-06
I have added automatic backup and restore on the installer.

Warning!!!!
Restoring from backup file will delete the current e-Sword (move it to trash, you could find it there) and replace with the backup copy.

DK

---

### Post by Tiito on 2008-10-11
How a I can uninstall e-sword from wine.
I need do that and reinstall with add ons.
Are there a way to install Bibles, Comments after install e-sword.

Please help me. I'm new in Ubuntu.

Thank you

---

### Post by david_kt on 2008-10-11
> **Tiito said:**
> How a I can uninstall e-sword from wine.
I need do that and reinstall with add ons.
Are there a way to install Bibles, Comments after install e-sword.

Please help me. I'm new in Ubuntu.

Thank you

In general, you do not need to uninstall anything from wine, just delete the directory. So, how did you install it? If you use the instruction at the first post of this thread, just delete .wine_Esword directory:

1. Open terminal (Applications > Accessories > Terminal)
2. rm -rf $HOME/.wine_Esword

If you install e-Sword in default wine:

1. Open terminal (Applications > Accessories > Terminal)
2.  rm -rf ''$HOME'/.wine/drive_c/Program Files/e-Sword'

If you still confuse, just download the installer at the first post of this thread, I have added the above two functions (to remove e-Sword). And I have added a progress bar GUI as well when the installer downloading files.

After you have uninstall e-Sword (although without uninstalling any e-Sword you could straight away install it using this installer),
run the installer again, and choose the first option (install e-Sword) and any addons you want to install, just "tick" as many as you want. IT would run all options you choose.

If the addon you want to install not available in the menu, you could let me know I will add it. Or, if you have downloaded the addon, tick "manual" and navigate to the downloaded file.

Remember to download the icon as well and remember where you download it, the installer will ask you to choose icon for the desktop launcher.

DK

---

### Post by jonathonblake on 2008-10-11
> **Tiito said:**
> 
Are there a way to install Bibles, Comments after install e-sword.

Assuming the resources are uncompressed, the simplest way to intall them, is to copy them into the e-Sword directory.
/home/user_name/.wine_Esword/drive_c/Program Files/e-Sword
is its location, on my system.

If they are executable files, then the e-Sword_installer program should be able to install them correctly.   

If they are compressed, the uncompress them, and move them to the e-Sword directory.

xan

jonathon

---

### Post by Tiito on 2008-10-12
Thank you very much for your help.
I'm runnig e-sword now and it's ok. I'm using Wine 1.6 (the last version).
but I have a question. I see there's two .wine directories (.wine and .wine-esword). is there some way to have just one. Is it possible copy .wine-esword into .wine?

Thank you again

---

### Post by david_kt on 2008-10-12
> **Tiito said:**
> Thank you very much for your help.
I'm runnig e-sword now and it's ok. I'm using Wine 1.6 (the last version).
but I have a question. I see there's two .wine directories (.wine and .wine-esword). is there some way to have just one. Is it possible copy .wine-esword into .wine?

Thank you again

I purposely create .wine_Esword directory to run e-Sword. The reason is we need to use native dlls and overrides. Those might affect other applications you want to run. So, as a guideline, you should use special directory for application that require tweaks.

If you _only run e-Sword using wine_, then, it is ok to move it to .wine directory.

Here is how you do it:
1. Delete .wine directory.
2. Rename .wine_Esword to .wine
3. Right click on e-Sword desktop launcher > choose properties > Launcher > change .wine_Esword to .wine.

That's it.
After this, DO NOT use e-sword installer anymore if you want to add addons or update e-Sword. Just download the addons and updates and double click to run.

DK

---

### Post by PeregrinGo on 2008-10-21
> **david_kt said:**
> Hi Glenn,

If the fonts has a lock in it, that means there is some file permission issue.

What you can do is right click in the file, and click the permission tab, and then click on the execute, read, write for the appropriate user. You could safely click all the options I think.

But if there are too many files, it could be very trouble some to change the file permission one by one.

What you could do is to open terminal (application>accesories>terminal), 

and then issue below command:

```
chmod 777 -R ~/.wine_Esword/drive_c/windows/fonts
```

you could change 777 to 700, and it should be ok as well. But to be sure, I suggest to use 777.

After that, reload the fonts page in nautilus, all the locks should be disappear. The above command is to give full right for every body to use all files at the fonts folder.

Please let me know if you still have some issue.

DK

When I open e-sword in Wine I see absolutely none of the Scripture texts themselves (even though it APPEARS to have a couple modules installed). I've tried the command you describe above a few times, but it just tells me that the file or directory doesn't exist.

Any ideas what the problem may be?

---

### Post by jonathonblake on 2008-10-21
> **PeregrinGo said:**
> 

Any ideas what the problem may be?

1:  In a terminal
```

cd /home/ user name /.wine_Esword/drive_c/Program Files/e-Sword/
ls -al > resource.txt

```
Paste "resource.txt" here.

2: Open e-Sword;
Take a screenshot of it. 
Put thee screenshot up on the net, and post the URL to it here.  

3: Which version of e-Sword are you using?
* What customizations/modifications to it have you made to it;

xan

jonathon

---

### Post by david_kt on 2008-10-21
> **PeregrinGo said:**
> When I open e-sword in Wine I see absolutely none of the Scripture texts themselves (even though it APPEARS to have a couple modules installed). I've tried the command you describe above a few times, but it just tells me that the file or directory doesn't exist.

Any ideas what the problem may be?

In my opinion, the problem is you install e-Sword in default wine. I suggest you to use the installer at the first post of this thread, it will save you a lot of trouble.

Please go to the first post and read how to use it, it is very easy. Please let me know if you still have problem. 

DK

---

### Post by david_kt on 2008-10-25
I have fixed some bugs for wine portable to run on puppy linux live cd. This time I have tried using various live cd such as Linux Mint, puppy linux, PCOSlinux2007 and all are working without additional software required. THe usb is automatically mounted and you just need to (double) click on e-Sword_wine_launcher on the usb to launch wine.

It failed on dsl though, but dsl is not very friendly when dealing with usb as well. I need to manually mount the usb drive, and need to be root to enter the mounted usb drive.

If you need to run e-Sword portable on any other live cd and it is not working, please let me know may be I could help to add more package in wine portable to overcome some dependencies issue.

DK

---

### Post by Ng Oon-Ee on 2008-10-29
Hey, thanks for the guide =). Fully working eSword along with a ton of bible versions, commentaries, and dictionaries, on Intrepid RC here.

I've just read through this entire thread to see if someone else managed to help with this problem, quoted below:-

> **lukeelliot said:**
> I have successfully installed e-sword in Kubuntu 8.04 by following your instructions, but have encountered problems trying to install add-ons using your installer. For some reason, I only get a blue screen when I run it and even Alt Tab doesn't bring up the installation windows.  However, I have found that by blindly pushing Enter over and over, the add-ons do in fact install.  (Hopefully this post will be of help to anyone encountering the same problem).

> **david_kt said:**
> I could confirm that addon will show blue screen only on Kubuntu/KDE but by pressing enter repeatedly it will still install successfully. But when I try in gnome, addon still run normally.

I can see this is explained on the first post, about just pressing Enter blindly, but perhaps someone would be interested in knowing that the root cause (for me) is Compiz running (perhaps KDE's window manager also causes the same thing). If I switch back to Metacity, I can install the addons with all dialogs with no problem. Not sure if you'd want to add that to your first post, as it may unnecessarily confuse people. But I think its important since most users from Hardy onwards use Compiz or at least some of its features, and may not remember/realize that this can cause visual glitches.

For the record, I've found the easiest way to switch window managers is to use Compiz Fusion Icon (install 'fusion-icon' from Synaptic or 'sudo apt-get install fusion-icon' from the terminal).

Thanks again =)

---

### Post by david_kt on 2008-10-29
> **Ng Oon-Ee said:**
> 
I can see this is explained on the first post, about just pressing Enter blindly, but perhaps someone would be interested in knowing that the root cause (for me) is Compiz running (perhaps KDE's window manager also causes the same thing). If I switch back to Metacity, I can install the addons with all dialogs with no problem. Not sure if you'd want to add that to your first post, as it may unnecessarily confuse people. But I think its important since most users from Hardy onwards use Compiz or at least some of its features, and may not remember/realize that this can cause visual glitches.

For the record, I've found the easiest way to switch window managers is to use Compiz Fusion Icon (install 'fusion-icon' from Synaptic or 'sudo apt-get install fusion-icon' from the terminal).

Thanks again =)

Thank you for your feedback, I will add it on the first post.

DK

---

### Post by Ng Oon-Ee on 2008-10-29
> **david_kt said:**
> Thank you for your feedback, I will add it on the first post.

You're welcome. :)

---

### Post by agasamapetilon on 2008-11-04
I have followed the instructions in this brief tutorial and got running e-Sword in my Ubuntu 8.10. The problem I have is that it appears the following error and it just closes the application abruptly. (Attached picture)

Can someone please help me to find out what can I do?

---

### Post by david_kt on 2008-11-04
> **agasamapetilon said:**
> I have followed the instructions in this brief tutorial and got running e-Sword in my Ubuntu 8.10. The problem I have is that it appears the following error and it just closes the application abruptly. (Attached picture)

Can someone please help me to find out what can I do?

Did you use the installer? If not, please use the installer and make sure there is no error during install (you are connected to internet).

DK

---

### Post by mtcycler on 2008-11-06
Love the new installer!!!!!
THANKS A TON!!!!!!!!!!!!!

---

### Post by david_kt on 2008-11-06
> **mtcycler said:**
> Love the new installer!!!!!
THANKS A TON!!!!!!!!!!!!!

I am glad it works. There are some bugs however I would try to fix:

The installer still run event though there is no cabextract installed. 

1. I will make the installer to abort if there is no cabextract installed. It is not difficult to add it.

2. Download progress GUI not working in Intrepid (but download still running as normal). May be some bugs in intrepid and I have just file a bug report. If there is no solution in near future, I would add one more installer for intrepid only, change to download progress bar to pulsate bar. download progress is much more fun as we could see the download speed and download progress.

And for portable e-sword, I would change the portable wine from compiling from source to extracting from deb package. It is much faster and do not need to run sudo apt-get build-dep wine, which install a lot of software for compiling wine.

Please let me know any other additional things you want to have.

DK

---

### Post by Mattheus on 2008-11-07
I am running ubuntu 8.04, and would like to install E-Sword. I have read through numerous threats. Where can I find the installer or must I just download the program from E-Sword's directory, and do the installation through wine?
Your help will be greatly appreciated.

---

### Post by david_kt on 2008-11-07
> **Mattheus said:**
> I am running ubuntu 8.04, and would like to install E-Sword. I have read through numerous threats. Where can I find the installer or must I just download the program from E-Sword's directory, and do the installation through wine?
Your help will be greatly appreciated.

Go to the first post of this thread:
[http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

The installer could be downloaded there:
[http://ubuntuforums.org/attachment.php?attachmentid=88038&d=1223767812](http://ubuntuforums.org/attachment.php?attachmentid=88038&d=1223767812)

DK

---

### Post by jonathonblake on 2008-11-14
Mainly for David, but other people might be interested.

Over the last three weeks, I've either installed, or attempted to install all of the e-Sword Utility Programs I have, that are "current".  

a)  If the installer script at [http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042) was used, then the utility program has to be installed using the same script;

b) BeST requires NET 2.0. As such, it won't install under Wine.  :(

c) Text2DAO (full version) has to be installed, prior to any of the other utility programs, for them to work. (Mike included every DLL, etc that Text2DAO requires, in the full version.)

You may have to reinstall Text2DAO several times, to get it to work properly.

d) I don't know whether it is better to add a new line, with the utility programs as optional installs, or have the end user edit the appropriate line, or use the "install as a new resource" option.

xan

jonathon

---

### Post by david_kt on 2008-11-14
> **jonathonblake said:**
> Mainly for David, but other people might be interested.

Over the last three weeks, I've either installed, or attempted to install all of the e-Sword Utility Programs I have, that are "current".  

a)  If the installer script at [http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042) was used, then the utility program has to be installed using the same script;

b) BeST requires NET 2.0. As such, it won't install under Wine.  :(

c) Text2DAO (full version) has to be installed, prior to any of the other utility programs, for them to work. (Mike included every DLL, etc that Text2DAO requires, in the full version.)

You may have to reinstall Text2DAO several times, to get it to work properly.

d) I don't know whether it is better to add a new line, with the utility programs as optional installs, or have the end user edit the appropriate line, or use the "install as a new resource" option.

xan

jonathon

Some of the points I don't really understand. 
a) It is true that the script create special wineprefix to run only e-sword, to avoid problem with other program. As such, all utility program need to be installed using this installer as well. I will add a note to make it clear for users. 

b) What is BeST ? Is there any link to download it? May be I will give it a try, who knows I could find some tweak to run it.

c) What is Text2DAO and required by which program in e-Sword? I don't remember installing Text2DAO for e-Sword.

DK

---

### Post by jonathonblake on 2008-11-14
> **david_kt said:**
>  
b) What is BeST ? 

Ben's e-Sword Tool. 

This program enables users to easily create new e-Sword and Pocket e-Sword resources.  

> Is there any link to download it? May be I will give it a try, who knows I could find some tweak to run it.


[http://groups.yahoo.com/group/e-Sword_Tools/files/BeST%20and%20BPeST/](http://groups.yahoo.com/group/e-Sword_Tools/files/BeST%20and%20BPeST/)

If it doesn't find the NET environment in the system, it won't install. Mono does not suffice. 

> 
c) What is Text2DAO and required by which program in e-Sword? 

This is another utility program for e-Sword. Specifically, to enable users to create, or edit e-Sword resources.  (It can also be used to examine any Access database that is not password protected.)

There are roughly twenty e-Sword utility programs.  I'll post a complete list of those programs, and the results of installing them, later on this weekend. (I'm debating whether or not it should be a thread of its own.)

jonathon

---

### Post by jonathonblake on 2008-11-20
A new version of e-Sword was released either last night, or this morning.

e-Sword 8.0.5.
This has some minor bug fixes, from 8.0.4.


For those who want to edit the code themselves.
Find the following line

#-------- Main function, to create bottle (maybe not neccesary anymore?) and install E-sword including the tweak -----------------------
load_esword() { 
# Download and install E-sword installer setup798.exe
wineprefixcreate --prefix $HOME/.wine_Esword
download . [http://www.e-sword.net/files/setup798.exe](http://www.e-sword.net/files/setup798.exe)
try env WINEPREFIX=$WINEPREFIX $WINE "$WINEESWORD_CACHE"/setup798.exe


load_esword() { 
# Download and install E-sword installer setup805.exe
wineprefixcreate --prefix $HOME/.wine_Esword
download . [http://www.e-sword.net/files/setup805.exe](http://www.e-sword.net/files/setup805.exe)
try env WINEPREFIX=$WINEPREFIX $WINE "$WINEESWORD_CACHE"/setup805.exe


For those who have allready installed e-Sword, I _think_ that the following rewrite  works.


load_esword() { 
# Download and install E-sword installer update805.exe
wineprefixcreate --prefix $HOME/.wine_Esword
download . [http://www.e-sword.net/files/update805.exe](http://www.e-sword.net/files/update805.exe)
try env WINEPREFIX=$WINEPREFIX $WINE "$WINEESWORD_CACHE"/update805.exe


###

The script also needs to be rewritten, to install the localization component.  Something along the lines of:

load_localized() { 
# Download and install E-sword localizer localize.exe
wineprefixcreate --prefix $HOME/.wine_Esword
download . [http://www.e-sword.net/files/localize.exe](http://www.e-sword.net/files/localize.exe)
try env WINEPREFIX=$WINEPREFIX $WINE "$WINEESWORD_CACHE"/localize.exe


###

Once the e-Sword utility programs are available from [http://www.e-sword-users.org](http://www.e-sword-users.org), I'll write the modifications that are needed to download, and install them, using the e-sword installation script.

###

I'm trying to figure out a way for the script to download user created resources that are available from [http://www.e-sword.users.org](http://www.e-sword.users.org).   THus far, I don't see one.   

I'm also trying to figure out how to get a shell script to open, and read the contents of an SQLite database.

jonathon

---

### Post by david_kt on 2008-11-21
I have just updated the script as follow:

1. Change the main program from e-Sword 798 to e-Sword 805
2. Add updater to update from old e-Sword installed using this cript to e-Sword 805.
3. Add localizer to install other languages GUI on e-Sword.
4. Add wine 1.1.7 as "tested wine"
5. Detached desktop launcher as separate script as newer wine able to create desktop launcher. You only need to download and run this script if you do not have desktop launcher and you want it.

As a warning, the download progress bar GUI do not work on intrepid. I have filed a bug complaint. But if you use Hardy, it would still working as normal. If many of you are using intrepid, I could change it to pulsating GUI instead of progress bar in order to work in intrepid. But actually the script is still working on intrepid, just be patient when it is downloading.

Please let me know if any of you have suggestions or feedback.

DK

---

### Post by david_kt on 2008-11-21
> **inventorstechnologies said:**
> You also need to copy e-sword folder in your home directory

For what purpose? If for backup and restore, it is already included in the script.

DK

---

### Post by zeroandone on 2008-11-23
I tried to install e-sword today on Ubuntu Intrepid by using the automatic installer but I got an error like this:

Esword_installer error: Note: command 'cp -f /home/jeffrey/.wine_Esword/drive_c/Program Files/e-Sword/riched20.dll /home/jeffrey/.wine_Esword/drive_c/windows/system32' returned status 1. Aborting.

Please help.

Thanks,

Jeffrey

---

### Post by david_kt on 2008-11-23
> **zeroandone said:**
> I tried to install e-sword today on Ubuntu Intrepid by using the automatic installer but I got an error like this:

Esword_installer error: Note: command 'cp -f /home/jeffrey/.wine_Esword/drive_c/Program Files/e-Sword/riched20.dll /home/jeffrey/.wine_Esword/drive_c/windows/system32' returned status 1. Aborting.

Please help.

Thanks,

Jeffrey

I think you are using older wine version ( wine 1.0 may be?). When I updated the script, I am using wine 1.1.7. For intrepid, you could download it [here]("http://wine.budgetdedicated.com/archive/ubuntu/intrepid/wine_1.1.7~winehq0~ubuntu~8.10-0ubuntu1_i386.deb")

Looks like the new e-Sword (8.05) could not be installed properly using older wine.

So, after upgrading you wine to wine 1.1.7, launch the installer again. I will prevent the installer from running unless it is wine 1.1.7.

Thank you for your feedback.
DK

---

### Post by zeroandone on 2008-11-23
Hi David, 
Thank you for your reply and help. Just updating Wine did seem to help me. I ended up doing the following things to get e-Sword installed.

1. Completely remove Wine from my computer, I mean every folder and every file (uninstall Wine through Synaptic leaves some folders and files behind, to be safe, I manually removed all left files and folders).
2. Installed Wine 1.1.7 downloaded from the link you provided.
3. Run the automatic installer provided by you in the first post.

This time everything went well with on error.

Again, thank you very much for your help and your hard work.

---

### Post by david_kt on 2008-11-23
> **zeroandone said:**
> 
1. Completely remove Wine from my computer, I mean every folder and every file (uninstall Wine through Synaptic leaves some folders and files behind, to be safe, I manually removed all left files and folders).

It is very smart move. After I post a reply, I realize I forgot this steps. Without this step it still will work though but you would have unneeded extra file from previous fail installation.

After I investigate, e-Sword 8.0.5 installed on different default directory if use wine 1.0. The default directory is changed from c:\Program Files\e-Sword to c:\ only.
That is the reason the script could not find riched20 dll if we use wine 1.0. As work around, I could add a script to force it to install on the default directory if the script found wine 1.0.
But that would make the script more complicated.

As such, use wine 1.1.7 is more appropriate. Wine 1.1.8 and 1.1.9 should be ok as well but I have not tested it yet.

DK
NB: If you need multiple wine, I have make a script to install multiple wine:
[http://ubuntuforums.org/showthread.php?t=942269](http://ubuntuforums.org/showthread.php?t=942269)

This is if your applications need different wine versions. But for e-Sword, once it is installed, it should be able to run on any wine version.

---

### Post by brjoon1021 on 2008-11-25
Ignore this, I will make a separate post

---

### Post by ubume2 on 2008-11-27
I have had 798 installed for quite some time.  I noticed lately that one of my modules vws had disappeared, and rws,jfb,henry would only display the text for the chapter of the bible it booted up in.  If it was at John 4, and I wanted to go to John 5, I would get a blank page on the commentary part of it.

I deleted e-sword, and wine, and installed the newest version of E-Sword and had the same problem. I deleted it and went back to 798, and am having the same problem.

It looks like the only way I can get it to work is to go to John 5 of the bible, close the program, and then restart it, in order to be able to read the commentary for that chapter.

Does anyone have any ideas on this?

thanks

---

### Post by david_kt on 2008-11-27
> **ubume2 said:**
> I have had 798 installed for quite some time.  I noticed lately that one of my modules vws had disappeared, and rws,jfb,henry would only display the text for the chapter of the bible it booted up in.  If it was at John 4, and I wanted to go to John 5, I would get a blank page on the commentary part of it.

Could you give me the download link for vws, rws, jfb, and henry? (if it is free)

DK

---

### Post by ubume2 on 2008-11-27
Hello, this was the same site I downloaded them from originally.

[http://www.e-sword.net/](http://www.e-sword.net/)

I discovered the program works the same way on XP

I just used the 805 update module and it seems to have corrected the problem. Using 8.05 application module did not.

---

### Post by david_kt on 2008-11-27
> **ubume2 said:**
> Hello, this was the same site I downloaded them from originally.

[http://www.e-sword.net/](http://www.e-sword.net/)

I discovered the program works the same way on XP

I could not find the modules you mean. Anyway, if it works the same way on xp, there is no way I could help.

DK

---

### Post by jonathonblake on 2008-11-27
> **ubume2 said:**
> 
I discovered the program works the same way on XP


a) I never successfully reproduced that behaviour. (Other people have reported that problem.) Until I can reproduce it, I can't tell you how to fix it.  

b) Install e-Sword 8.0.5 and see if that solves the issue.

###

jfb: Jamieson , Faussett & Brown:  This is a commentary
Henry:   Matthew Henry's commentary - the unabridged one;
vws: Vincent's Word Studies: Commentary
rws: Robinson's Word Studies:  I don't see it on the site. Robinson's Word Pictures is on the site.


jonathon

---

### Post by ubume2 on 2008-11-28
Hi, I had an archived copy of e-Sword v7.9.8 that I used to reinstall.

I tried the v8.0.5 of the e-Sword application installation, but it didn't correct the problem.

I completely uninstalled e-Sword 8.0.5 I then reinstalled v7.9.8. Still a problem.

I then installed the e-Sword v8.0.5 update module (Existing e-Sword users running any version between 6.0 and 8.0 may use this update.)  It worked properly where installing a fresh copy of 8.0.5 would not.
8.0.5 complete module  is on the website, as well as the 8.0.5 update module and a e-Sword GUI localization module.
[http://www.e-sword.net/downloads.html](http://www.e-sword.net/downloads.html).

So for me, the problem is solved.

Thanks

---

### Post by zedstrange on 2008-11-30
> **david_kt said:**
> 
As such, use wine 1.1.7 is more appropriate. Wine 1.1.8 and 1.1.9 should be ok as well but I have not tested it yet.



FYI.  

I just installed automatically using Wine 1.1.9 and worked fine.

oh wait,  i ticked all the available options for installing add-ons, and they did not appear to install. Its my first time using e-sword, but i assume I should have a lot of *.bbl files in my e-sword folder and there is only one.   Sorry cant be much more help.

---

### Post by david_kt on 2008-11-30
> **zedstrange said:**
> FYI.  

I just installed automatically using Wine 1.1.9 and worked fine.

oh wait,  i ticked all the available options for installing add-ons, and they did not appear to install. Its my first time using e-sword, but i assume I should have a lot of *.bbl files in my e-sword folder and there is only one.   Sorry cant be much more help.

Try installing using wine 1.1.7. Two users already feedback to me there is problem using wine 1.1.9.

By the way, you could use the installer to remove the e-sword, and then reinstalling again is fast as it will not download again the program (already in the cache).

DK

---

### Post by wilkotb on 2008-11-30
I used the installer program to install E-sword. I only experience problems to get a desktop icon to launch it. The installation created an icon in /root/desktop that work fine if I am locked in as sudo su and run it from nautilus. But I tried to copy it to my desktop: /home/mat/desktop, and even tried to create a link to the created launcher that works, but no luck. This is the command that works in /root/desktop: env WINEPREFIX="/root/.wine_Esword" wine "C:\Program Files\e-Sword\e-Sword.exe" By the way I have wine 1.1.9. Any help would be appreciated.

---

### Post by david_kt on 2008-11-30
> **wilkotb said:**
> I used the installer program to install E-sword. I only experience problems to get a desktop icon to launch it. The installation created an icon in /root/desktop that work fine if I am locked in as sudo su and run it from nautilus. But I tried to copy it to my desktop: /home/mat/desktop, and even tried to create a link to the created launcher that works, but no luck. This is the command that works in /root/desktop: env WINEPREFIX="/root/.wine_Esword" wine "C:\Program Files\e-Sword\e-Sword.exe" By the way I have wine 1.1.9. Any help would be appreciated.

It is not good. You run the installer with sudo or as root, it is a little difficult to repair.

Fortunately, the installer come with uninstaller. Run again the installer using sudo or as root. Choose "remove e_sword".

After that, run again the installer as normal user (without sudo, not as root).

Please let me know if after that you still have problem, you might need to do some more steps, I am not sure as I never try to run wine as root. But I think I could help you.

DK

---

### Post by wilkotb on 2008-11-30
David, thanks. I am happy to report that everything work in wine 1.1.9

---

### Post by david_kt on 2008-12-01
> **wilkotb said:**
> David, thanks. I am happy to report that everything work in wine 1.1.9

Thank you for giving feedback. Wine 1.1.9 might works as well although two users already report it is not working, but it might be problem with other setting, not wine.

I have added a warning as well in the first post of this thread:

```
Do not run the installer with sudo or as root.
```

Hopefully that would prevent other people from doing the same mistake.

Again, thanks for your feedback.

DK

---

### Post by CholericKoala on 2008-12-02
I installed esword using wine 1.1.9 just by double clicking on the setup.exe.  The modules had trouble at first, but I dragged my /windows/system32/msls31.dll from my vista partition over to the /home/$user/.wine/drive_c/windows/system32 and everything worked just fine.

---

### Post by silvagroup on 2008-12-03
Just updated to 8.0.5 today using the downloaded update installer from the website.
Worked fine. Well almost, my tabs for Bibles, Commentaries and Dictionaries is in the most horrid font, practically unreadable.
Is there anyway to change it?

---

### Post by david_kt on 2008-12-03
> **silvagroup said:**
> Just updated to 8.0.5 today using the downloaded update installer from the website.
Worked fine. Well almost, my tabs for Bibles, Commentaries and Dictionaries is in the most horrid font, practically unreadable.
Is there anyway to change it?

What is the wine version you are using now?
When and how did you install the old e-Sword?

What you could try is run the installer and choose the first option (install e-Sword 8.0.5), might solve your problem.

DK

---

### Post by CholericKoala on 2008-12-04
> **silvagroup said:**
> Just updated to 8.0.5 today using the downloaded update installer from the website.
Worked fine. Well almost, my tabs for Bibles, Commentaries and Dictionaries is in the most horrid font, practically unreadable.
Is there anyway to change it?

Go to "Options" "Bible Font" 

I changed mine to Granada 12 point.  Easy enough for me to read ;)  Good luck.

---

### Post by silvagroup on 2008-12-04
I am using version 1.0 of wine. I upgraded from 7.8 which worked just fine. May go back to it.

The old E-Sword was installed the same way I installed the updrage, just cliked on the .exe file.
I have not used the installer mentioned in the posts if that's the installer you are speaking about. 
CholericKoala the font is not in the material text, the bible text or such, but in the tabs at the top.

---

### Post by david_kt on 2008-12-04
> **silvagroup said:**
> I am using version 1.0 of wine. I upgraded from 7.8 which worked just fine. May go back to it.

The old E-Sword was installed the same way I installed the updrage, just cliked on the .exe file.
I have not used the installer mentioned in the posts if that's the installer you are speaking about. 
CholericKoala the font is not in the material text, the bible text or such, but in the tabs at the top.

The easiest way is to run winecfg, click graphic tab, and select slightly higher resolution. That would increase the font size. Please see the first post of this thread, I have explained this trick as well there.

Otherwise, you might consider upgrading to wine 1.1.7 and installing it from scratch using the installer on the first post of this thread. It is very easy.

DK

---

### Post by silvagroup on 2008-12-04
Sorry I was running 7.9.8 previously and I had no problems with it at all. The tab text was fine and everything worked fine.

I will try some of suggestions and post back with results.

---

### Post by paeuk on 2008-12-06
> **david_kt said:**
> I guess you are using old instruction, i.e. you download 4 dlls. For later wine (not sure since which version), those dlls will cause the addon could not run.

So, could you please repeat your installation, using the updated instruction (only download 1 dll i.e. msls31.dll). And one more dll is riched20.dll, copy it from e-sword folder, do not download. Please refer the the first post of this thread for the details, including the troubleshooting section.

DK

Hi David_Kt,

I'm new to Ubuntu and have stumbled across this same problem as described in post #182 with the errors:

wine: Call from 0x7ee055ba to unimplemented function riched20.dll.RichEdit10ANSIWndProc, aborting
wine: Call from 0x7ee055ba to unimplemented function riched20.dll.RichEdit10ANSIWndProc, aborting

I followed your instructions and un-installed eSword (and got rid of the .wine_Esword folder etc. Then redid all the instructions at the beginning of this thread being careful about the dlls, but I still get the same problem with the abort messages.

I'm not sure what else to do or what these abort messages really mean. Is there any other suggestions you have please that could help me work out what is wrong.

I feel I'm really close.

eSword itself works fine by the way. Just adding the add-ons which is the problem.

Many thanks.


Paul

---

### Post by CholericKoala on 2008-12-06
One way that might work is downloading winetricks from the internet (googling it and installing the .deb file).  Type "sh winetricks" in terminal, find riched20 and install.  Hope it works :)

---

### Post by david_kt on 2008-12-06
> **paeuk said:**
> I followed your instructions and un-installed eSword (and got rid of the .wine_Esword folder etc. Then redid all the instructions at the beginning of this thread being careful about the dlls, but I still get the same problem with the abort messages.

I'm not sure what else to do or what these abort messages really mean. Is there any other suggestions you have please that could help me work out what is wrong.
l

One way to test is to use the installer, which could avoid any mistake. Would you please download the installer and try it out? Make sure you have wine 1.1.7.

DK

---

### Post by kneewax on 2008-12-11
Hi DK,

Just wanted to say, that I have used your fabulous instructions to get e-sword running a number of times (rebuilds, new machines etc.)  Always works for me, as long as I follow the instructions properly.

I just downgraded to Hardy after an unhappy Intrepid experience, and when I went to re-read your HowTo, I discovered the new installer.  Thank you so much it is brilliant!  I was able to copy my backed up esword folders into the  .wine_Esword bottle, than I ran your installer using the 'upgrade' setting and it worked brilliantly.  The only tweak I had was I had to manually copy msls32.dll into the system32 folder.

So, yet again, I am in your debt!  Thanks for all your work on this, and particularly the automated installer.  

Cheers

Kneewax

---

### Post by david_kt on 2008-12-11
> **kneewax said:**
>   The only tweak I had was I had to manually copy msls32.dll into the system32 folder.

Thank you for your feedback.
The installer should have taken care msls31.dll as well. That would happen if:

1. There was a problem with your internet connection
2. Microsoft website was down or they change the file location so as the installer could not find msls31.dll from microsoft website
3. You do not have cabextract installed as the msls31.dll need to be extracted using cabextract.

I guess you did not install cabextract so as msls31.dll failed to be extracted to system32 directory.

DK

---

### Post by kneewax on 2008-12-11
Hi DK - this may be the case.  I did attempt to install the cabextract as described  but I got this response:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
cabextract is already the newest version.
The following packages were automatically installed and are no longer required:
  libavahi-gobject0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
So I pressed on anyways, assuming as Hardy figured it was installed, it would be OK.

Anyways, I am not worried, adding a dll is not a major issue :-)

Thanks again.

---

### Post by david_kt on 2008-12-11
> **kneewax said:**
> 
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
cabextract is already the newest version.
The following packages were automatically installed and are no longer required:
  libavahi-gobject0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
So I pressed on anyways, assuming as Hardy figured it was installed, it would be OK.

So, cabextract is already install, it might be problem with microsoft website. I will check it now as sometime some people new to linux/wine have issue copying dll.

edit: I have just checked there is no change in microsoft website, msls31.dll are still available there (extracted from InstMsiA.exe). So, it might be temporary problem or internet connection problem.

DK

---

### Post by CholericKoala on 2008-12-11
I had to manually install the dll myself also.

---

### Post by david_kt on 2008-12-11
> **CholericKoala said:**
> I had to manually install the dll myself also.

I could not detect the problem so far, I have checked the download link and also the script, everything is ok.

Is there any error when you use the installer? Is anybody else having problem with dll using the installer? If you could help to run the installer using command line:

```
./e-Sword_installer
```

choose esword and post the output of terminal here, I might be able to detect the problem.

By the way, which wine version you are using?

DK

---

### Post by david_kt on 2008-12-12
I have made a poll to check how many people faced trouble with installer and how many people could use it without any problem.

If there are many people having trouble, I will investigate further as so far I could not find any problem with the installer.

DK

---

### Post by jonathonblake on 2008-12-12
> **david_kt said:**
> I have made a poll to check how many people faced trouble with installer and how many people could use it without any problem.

I ended up rewriting the code, to make it easier for me to install the various utility programs and resources that I have.

When I can get some licensing issues resolved, I'll release the modifications.


jonathon

---

### Post by CholericKoala on 2008-12-12
> **david_kt said:**
> I could not detect the problem so far, I have checked the download link and also the script, everything is ok.

Is there any error when you use the installer? Is anybody else having problem with dll using the installer? If you could help to run the installer using command line:

```
./e-Sword_installer
```

choose esword and post the output of terminal here, I might be able to detect the problem.

By the way, which wine version you are using?

DK

There is no error in the installer.
Wine version 1.1

---

### Post by zedstrange on 2008-12-13
> **david_kt said:**
> Try installing using wine 1.1.7. Two users already feedback to me there is problem using wine 1.1.9.

By the way, you could use the installer to remove the e-sword, and then reinstalling again is fast as it will not download again the program (already in the cache).

DK

Thanks David, but as I have already gone ahead with downloading the add-ons and installing them I would rather leave it as it is.   Apart from the add-ons the installation under Wine 1.1.9 works fine for me.  
(if i didnt mention it, I am running 64 bit Ubuntu)

---

### Post by cmckdub on 2008-12-25
A few things about e-sword.
1. I have been using it through Wine quite fine for a while now. Considering the problems people have been having with Wine 1.1.9, I though I would start with a clean ~.wine folder and try a clean install. It worked without any dlls added. Previously I did find that I needed to install the dlls (especially riched20.dll) and configure the overrides. So, although I voted to say that I installed with the dll overrides needing to be done, I could now also say that with wine 1.1.10, it seems to install without the additions.
2. When I say that it works fine, I have had a few minor problems with the graphics viewer. There are a few tricks with getting the maps to show. Namely to click on print preview, then click on a different map and back to the original.
3. The other problem I had was why I was looking on the forums today. Despite my preference for Open source software, my wife gave me the NIV for e-sword. This itself is not a problem, I was very pleased to get it. However, it would not install in wine. Instead I needed to install it in windows and copy the bbl files across.
4. Last point is about license. I noticed earlier posts...
> **Dov said:**
> I'm a pretty dedicated open-source user, but I must say that e-sword absolutely leaves for dead anything in the Linux world. Fortunately it runs flawlessly under Wine! 

The GPL would seem to fit the license requirements set by the developer of e-sword, so perhaps he could be persuaded to GPL the code?

I totally agree, and recognise the difference in license. Has anyone actually contacted Rick M about this? He seemed quite approachable on other issues. The other alternative would be for someone he could trust to work alongside Rick to develop it for linux.
I am looking into developing a linux installation for bible college students in developing countries, and suitable Bible software is of course essential. It would be good to do an installation without wine, yet keep the power of e-sword.

---

### Post by silvagroup on 2008-12-25
> Has anyone actually contacted Rick M about this? He seemed quite approachable on other issues. The other alternative would be for someone he could trust to work alongside Rick to develop it for linux.
This has been suggest since the very early days of wine. Even then the earlier versions of e-sword were workable (with some effort) with wine.
Now almost ten years later nothing has come forth from Rick for Linux. It was even suggest that the porting tools and help were available from wine folk and that would make the process easier.
But it would never hurt to continue asking. I have been for ten years and have never even had any acknowledgment to the suggestion.:lolflag:
CLUE: Have you noticed that there's no Apple version. no Palm OS version and no Linux version, cold be Rick is simply a Windows fan !!!!!!

---

### Post by david_kt on 2009-01-02
I have updated the installer script to e-Sword 8.0.6, and add Indonesian and Vietnamese bibles as well.

If you use the installer to install your e-sword before, you could use the new script to upgrade it to new version.

I have not try to use later wine, still using wine 1.1.7 so far without any problem.

Looks like cmckdub misunderstood the vote. We need to copy and overrides some dll for wine 1.1.7, but I have automated it using the installer script at the first post of this thread. Using that installer, you should not need to copy and overrides manually because it has been done automatically. But some users informed that they still need to do it manually (the script do not work) but I still could not figure out what went wrong.

As for NIV, if you use this installer, you could try to choose manual option and see whether it could work.

DK

---

### Post by silvagroup on 2009-01-02
I still have not had to use the install script.
With the release of 8.0.6 the problem with the tab text is gone, the update worked fine. The fonts for the tabs are as they should be now. All is working.

I am still using Wine 1.0, so I don't know what would or will happen eventually when I upgrade wine. However so far this install is the same install of e-Sword I have had for over three years. It has made it trhough every upgragd and update of both wine and e-Sword.

I have my working .wine backed up and try all changes with a test .wine folder before committing anything to the worling .wine folder, that has saved me from some hiccups along  the way.

---

### Post by jonathonblake on 2009-01-02
> **cmckdub said:**
> 
I totally agree, and recognise the difference in license. Has anyone actually contacted Rick M about this?

Part of this is driven by publisher concerns.  It is incredibly difficult --- some would claim impossible --- to distribute a FLOSS program that contains encrypted data, that can not be unencrypted using tools other than those provided within the program. 

> someone he could trust to work alongside Rick to develop it for linux.

The issue is one of:
* The tool chain that Rick knows;
* The database engine to use;
* The text rendering engine that is used;

Secondary issues are:
* KDE v Gnome v other environment managers;
* RPM v Deb v other installation managers;

Tertiary issues are:
* Would a non-FLOSS program gain any traction on the Linux platform? Historically, the only non-FLOSS programs to gain any degree of "acceptance" on Linux have been either high end niche markets, or enforced through the use of patents;

> I am looking into developing a linux installation for bible college students in developing countries, and suitable Bible software is of course essential. 

At the risk of sounding hypocritical, my suggestion is that you work with _The Sword Project_, in either writing tools that simplify the process for users to create their own resources, or code the additional functionality into their front ends, so that they are feature comparable to e-Sword.

jonathon

---

### Post by kneewax on 2009-01-02
Hi DK,

Just to say - after a re-install of Intrepid, I ended up using the latest version of Wine (1.1.11) as I had a bit of trouble with 1.1.7 - well I used the new script and it worked perfectly in the new evironment even witht he latest Wine.

It threw a warning up at the beginning of the script because the ```
wineprefixcreate --prefix 
``` code has been superceded in subsequent versions of wine - but this caused no problems with the script at all.

Thanks again for all your work on this.

Kneewax

---

### Post by silvagroup on 2009-01-02
> Part of this is driven by publisher concerns. It is incredibly difficult --- some would claim impossible --- to distribute a FLOSS program that contains encrypted data, that can not be unencrypted using tools other than those provided within the program.

jonathonblke, you hit it right on the head.
What we need is for some one to fork The Sword Project forget about FLOSS and make it as good as e-Sowrd.

I know that is anathema in the open source world, but not really how many spin offs do we have of Debian, why because so many knew they had to have that proprietary material to provide the level of performance expected by the end user!!!!

The materials are all there already there, e-Sword does it using Access. Olive Tree does it not sure how because they work on Windows Mobile and PalmOS, but all these use licensed materials and there is the key, allowing the use of licensed materials !!!!!!!

So the solution is who can branch The Sword Project and make it as good as those other products.

---

### Post by jonathonblake on 2009-01-02
> **silvagroup said:**
> Now almost ten years later nothing has come forth from Rick for Linux. 

e-Sword was written for the novice computer user, who is also a new Christian. Up until the OLPC was released,  Linux was not the first OS a new computer user would encounter.  Even today, it isn't the first OS one would find.  (Walmart reported that returns of Linuyx boxes were higher than that of Windows boxes.  What they didn't say, was why those returns are higher.  However, a QVC host provided a clue, when they derided Linux netbooks as "using software that is unfamiliar to everybody, and is incompatible with what they are familiar with".)

> CLUE: Have you noticed that there's no Apple version. no Palm OS version and no Linux version,

Both Linux and Mac OS X lack the traction that Windows has. I'll also point out that scripts for installing e-Sword on both the Mac and Linux are available.

Palm _might_ have been a good choice, five or so years ago. Since then, it has lost a lot of ground. If one is going to pour time and money into development, one wants the platform to still be around in three or four years.  Given the finances of the parent company, Palm probably will be history within three years. 

*Accordance* hasn't been ported to either Windows, or Linux. *Libronix* finally --- five years after being announced --- has a version for the Mac. *Illumina*, *QuickVerse*, and *WordSearch* are available for both Mac and Windows.  More to the point, none of the commercial Bible Study Software houses have plans to provide a Linux version, much less are currently shipping anything.   (This is one of the vices of WINE --- developers don't bother rewriting native applications, until they discover that their market has disintegrated into nothingness.]

>  could be Rick is simply a Windows fan !!!!!!

When Rick wrote the first line of code for e-Sword, he did so using the tool chain he was most familiar with. 

One _major issue in porting e-Sword, is that the database engine it uses, is only available for Windows. The current solution --- of using a different database engine for each supported platform --- makes resource construction "complicated".  

If e-Sword changes to a cross-platform database engine, Pocket e-Sword would also need to be rewritten, to support the new database engine.

There will be a hue and cry because "old" resources for e-Sword and Pocket e-Sword are incompatible with the new version of e-Sword, and Pocket e-Sword.

The second issue in a cross-platform version is the text rendering engine. Continue using the existing RTF engine, or use HTML, or XML, or something else.

If both of those conditions are satisfied, then a Linux version becomes a theoretical possibility.

jonathon

---

### Post by jonathonblake on 2009-01-02
> **silvagroup said:**
> we need is for some one to fork The Sword Project forget about FLOSS and make it as good as e-Sword.

*The Sword Project *is distributed under the GNU GPL 2.0.  As such, any fork would have to be FLOSS.  BTW, *The Sword Project* has managed to convince some organizations to allow their material to be distributed in Sword Project file formats.   

> but all these use licensed materials and there is the key, allowing the use of licensed materials !

The publishing world is "an old boys club".  If you aren't part of the club, getting anything is extremely difficult. If you are part of the club, the task is merely "difficult".

jonathon

---

### Post by david_kt on 2009-01-02
> **kneewax said:**
> 
Just to say - after a re-install of Intrepid, I ended up using the latest version of Wine (1.1.11) as I had a bit of trouble with 1.1.7 - well I used the new script and it worked perfectly in the new evironment even witht he latest Wine.

It threw a warning up at the beginning of the script because the ```
wineprefixcreate --prefix 
``` code has been superceded in subsequent versions of wine - but this caused no problems with the script at all.

Thanks again for all your work on this.

Kneewax

I have returned to Hardy as Intrepid has some issue with zenity, it did not show the download progress bar properly. Furthermore, I also have problem with networking in intrepid as I am using my desktop computer to be a router as well for my laptop. But off course if you just use as normal desktop, intrepid would be better than hardy in term of hardware detection. And the zenity thing is just an eye candy, it did not really affect the script performance.

The "wineprefixcreate --prefix" is deprecated. But I still leave it there for people using older wine. I could add detection of wine version and skip wineprefixcreate for newer wine, but the problem is I do not know which wine version start to deprecate wineprefixcreate. And anyway, as you also has said, it just throw out a warning and do not have impact on performance.

I wanted to try wine 1.1.11, but it has not release for hardy yet. I could compile it myself but I just worry that it would be slightly different from the one pre-compiled as deb package.

Anyhow, there is one dll required by e-Sword that is still non existent in wine i.e. msls31.dll. I will surely test it if it is available in the future, to remove native msls31.dll from the script. But from the feedback I saw for wine 1.1.10, it still have some issue without native msls31.dll. As such, I presume that the script will still remain the same for wine 1.1.7 up to wine 1.1.11.

DK

---

### Post by cmckdub on 2009-01-03
> **jonathonblake said:**
> 
At the risk of sounding hypocritical, my suggestion is that you work with _The Sword Project_, in either writing tools that simplify the process for users to create their own resources, or code the additional functionality into their front ends, so that they are feature comparable to e-Sword.

jonathon
Thanks jonathon. This encouraged me to give Gnomesword another go. Some of the complaints I had with Gnomesword (particularly behaviour with Strongs numbers) has been solved by using the latest version of Gnomesword (2.4.1). It is quite an improvement in setting-out too. I can see the potential for what you are suggesting.
I am using the standard installation of Hardy, and it installed version 2.2.3 from the repositories. Now that I have the Gnomesword repository listed as a source, I should be OK, but what about others? Is there a way to get the standard Ubuntu repositories updated to a later version of Gnomesword?
This all may be a bit off topic, but if anyone else is using Gnomesword 2.2.3 try using the Gnomesword repository at:
[http://gnomesword.sourceforge.net/debian.php]("http://gnomesword.sourceforge.net/debian.php")

---

### Post by cmckdub on 2009-01-03
Thanks also for the explanation about e-sword. I see now that my suggestions for a Linux e-sword were far too fanciful. Looks like we stick with Wine.

---

### Post by cmckdub on 2009-01-03
> **david_kt said:**
> Looks like cmckdub misunderstood the vote. We need to copy and overrides some dll for wine 1.1.7, but I have automated it using the installer script at the first post of this thread. Using that installer, you should not need to copy and overrides manually because it has been done automatically. But some users informed that they still need to do it manually (the script do not work) but I still could not figure out what went wrong.

As for NIV, if you use this installer, you could try to choose manual option and see whether it could work.
DK
Sorry david_kt. I had misunderstood. I have now used your installer successfully. Here are the details:
Hardy 32 bit, Wine 1.1.12, e-sword 8.0.6
NIV installed fine.:D
All works wonderfully.:D
(Also copied relevant bible files, books and maps across as I had not kept the installation files).
I do not think I can change my vote to say it installed OK without any need to do anything manually.
The Back-up facility is also a fantastic inclusion. I can see myself using that often.:D

It is great that now the graphics viewer works perfectly (I do not know whether this is because of your installer, the new version of wine, or the new version of e-sword, but it is great that the maps are now working wonderfully.:D
As the Bible memorisation file, Prayer requests and notes file are kept in a common directory, it is great that these were recognised in the new installation.:D
The new version of e-sword also has the ability to turn the annoying red-lettering off too. That's great.

Can I make the suggestion that the initial instructions are a bit verbose for what is normally a simple operation? Should it be simplified by placing the basic instructions (check you have wine installed and run the installer) first under a heading "Installing", then follow with the headings "News", "Explanations" and "Alternatives"? (When I saw it all I thought all of the command lines needed to be followed (a rather daunting concept) rather than simply running the installer).

---

### Post by david_kt on 2009-01-03
> **cmckdub said:**
> Can I make the suggestion that the initial instructions are a bit verbose for what is normally a simple operation? Should it be simplified by placing the basic instructions (check you have wine installed and run the installer) first under a heading "Installing", then follow with the headings "News", "Explanations" and "Alternatives"? (When I saw it all I thought all of the command lines needed to be followed (a rather daunting concept) rather than simply running the installer).

Well, actually I have tried to make it clear that using installer is simple and even easier than installing it in windows as you do not even need to download a thing. Just run the script and point and click what ever you want to install.

As for the verbose instruction, I leave it there and even I still update it to show people what the script does exactly, in case somebody want to improve the script or want to learn a little bit about tweaking wine. But I consider you suggestion to make it clearer for all people.

As for the graphic viewer, I have it works since e-sword 7.7.7 and wine 0.9.19 or even earlier, I could not really remember. And offcourse with some tweaks, earlier I need 4 native dlls. But now I only need 2 native dlls. So, I am sure that 2 native dlls is still needed even with latest e-Sword and latest wine. I monitor the progress of those 2 dlls in wine, once there is a progress, I will try again without those native dlls.

DK

---

### Post by markdean on 2009-01-04
> **Dov said:**
> I'm a pretty dedicated open-source user, but I must say that e-sword absolutely leaves for dead anything in the Linux world. Fortunately it runs flawlessly under Wine! 

The GPL would seem to fit the license requirements set by the developer of e-sword, so perhaps he could be persuaded to GPL the code?

I've brought this up many times in the e-sword forum but there appears to be resistance from the creator of e-sword. According to what I understand the problems with GPL'ing the code is more regarding the copyrighted modules (bibles, encyclopedias, and other reference works). It appears that the owners of various works are afraid of what would happen if e-sword was opened up. Even though it is an unwarranted fear that reflects a lack of understanding that if e-sword was GPL'd, it would only apply to the program code and not content.

I don't know what language it was written in so I don't know if there would be problems porting it to Linux or not.

But think of how much better e-sword would be if it was open to contributions of code from thousands of programmers. One option I would love to see would be a command line option where I can pass a verse as an argument, redirect to a file, etc. E-sword is a very GUI application and is one of only 4 or 5 applications that I actually run X Windows for (even my email is via mutt)...

The best choice when a developer doesn't see the value in OSS is to create our own. So if gnome-sword or whatever can be brought up to at least most of the functionality of e-sword *and* I can import my content (without violation of copyrights, of course) then I'll switch. Until then, like a few other win32 applications that I either prefer (parish the thought!) or must use, wine will work just fine.

OK, never mind, I saw Jonathon's posts, who knows far more of the details of e-sword...:-)

---

### Post by Searcher on 2009-01-04
David, I am new to Linux and Ubuntu, but I have been running e-Sword since version 6.  I have just installed Ubuntu Ultimate Edition 2.0 for 64bit and I am very pleased with it.  I want to install e-Sword too, but I would like to get your script.  Where is it available?  Thank you for your hard work in putting this all together.  It is much appreciated.  Ron

---

### Post by jonathonblake on 2009-01-04
> **cmckdub said:**
>  It is quite an improvement in setting-out too. I can see the potential for what you are suggesting.

I've forgotten which front end it is, :( but one of them is almost on a par with e-Sword 8.0.6,in terms of the feature set it offers.

I'll also point out that in terms of officially released resources, *The Sword Project* currently offers more than e-Sword.

When it comes to user-created content, e-Sword is the leader of the pack. However, the majority of user created resources for e-Sword can not be legally redistributed.  :(

jonathon

---

### Post by jonathonblake on 2009-01-04
> **markdean said:**
> It appears that the owners of various works are afraid of what would happen if e-sword was opened up. 

Not "what would happen", but "what has happened".

More than one publisher has seriously considered filing "criminal conspiracy to violate copyright" against Rick, and the developers of the various utility programs for e-Sword. 

As it is, at least two individuals are currently wanted, for *criminal copyright distribution*, of e-sword resources.  Had e-Sword, or the utility programs been FLOSS, the developers would be co-defendants on both criminal copyright, and conspiracy to violate copyright.


> Even though it is an unwarranted fear that reflects a lack of understanding that if e-sword was GPL'd, it would only apply to the program code and not content.

If you know of a way to enforce DRM, such that it can not be coded around, in a FLOSS program, then the content owners would be more willing to tolerate distribution of their material in FLOSS format.

> But think of how much better e-Sword would be if it was open to contributions of code from thousands of programmers.

The "average" FLOSS project has under 50 contributors to the code base. (I saw this statistic in a discussion on the difference between OOo development, and Linux Kernel development.)

Note to self: Do an analysis of Sword Project utility program, and front end code contributions, and compare them to e-sword utility program development.

> One option I would love to see would be a command line option where I can pass a verse as an argument, redirect to a file, etc.

Rick has discussed offering a more comprehensive set of options for using e-Sword from the command line. 

Try running
```
e-sword -b 31102
```

```
e-sword -b Gen 1:1
```

and watch what happens.

> The best choice when a developer doesn't see the value in OSS is to create our own.

It isn't that Rick doesn't see the value of OSS.  Rather, the issue comes down to copyright protection/enforcement of resource content.

>  So if gnome-sword or whatever can be brought up to at least most of the functionality of e-sword 

This is the kicker for the entire range of Sword Project front ends.

> *and* I can import my content (without violation of copyrights, of course) then I'll switch. 

Currently, *The Sword Project* offers more tools to import content, for more different file formats, than any other Bible Study Program.  However, documentation on using those tools is "lacking".

jonathon

---

### Post by david_kt on 2009-01-04
> **Searcher said:**
> David, I am new to Linux and Ubuntu, but I have been running e-Sword since version 6.  I have just installed Ubuntu Ultimate Edition 2.0 for 64bit and I am very pleased with it.  I want to install e-Sword too, but I would like to get your script.  Where is it available?  Thank you for your hard work in putting this all together.  It is much appreciated.  Ron

This is the link:

[http://ubuntuforums.org/attachment.php?attachmentid=98458&d=1230908760](http://ubuntuforums.org/attachment.php?attachmentid=98458&d=1230908760)

Actually it is at the bottom of the first post of this thread, there are attachment section. There are other attachments there for other functions.

DK

---

### Post by paeuk on 2009-01-12
> **david_kt said:**
> I have updated the installer script to e-Sword 8.0.6, and add Indonesian and Vietnamese bibles as well.

If you use the installer to install your e-sword before, you could use the new script to upgrade it to new version.


DK

Hi David,

Is there any possibility please of including the TSK (Treasury of Scripture Knowledge) in your installer. However I try I cannot manually add the TSK after installing eSword (using your installer and instructions), although all the modules I've tried that you include in your installer list work.

Alternately would be simple for me to understand how you are installing the modules in your installer, so see if I can change the manual process I'm using (which I got from the forums) to get the TSK included that way.

I just find the TSK an invaluable resource and it's the only thing that keeps me reverting to the GnomeSword bible.

Many thanks.

Paul

---

### Post by david_kt on 2009-01-12
> **paeuk said:**
> Hi David,

Is there any possibility please of including the TSK (Treasury of Scripture Knowledge) in your installer. However I try I cannot manually add the TSK after installing eSword (using your installer and instructions), although all the modules I've tried that you include in your installer list work.

Alternately would be simple for me to understand how you are installing the modules in your installer, so see if I can change the manual process I'm using (which I got from the forums) to get the TSK included that way.



I have updated the script to include TSK, I have tested the script and it works. Please download the script at the first post of this thread and try it and hopefully it also work for you. [Here is the link]("http://ubuntuforums.org/attachment.php?attachmentid=99615&d=1231770289").

Alternatively, to install add ons not in the installer, just download the exe (tsk.exe) file first, and remember the location you downloaded it.

Launch the installer script (e-Sword_installer), and choose manual. It will open a browser for you to locate the exe file (tsk.exe).

DK

---

### Post by razor7 on 2009-01-12
Hello...the text in the tabs is too small...

I just downloaded and installed e-sword from the webpage.

Please advise!

Thanks a lot

---

### Post by david_kt on 2009-01-12
> **razor7 said:**
> Hello...the text in the tabs is too small...

I just downloaded and installed e-sword from the webpage.

Please advise!

Thanks a lot

Are you using the installer from the first post of this thread? If yes, what you could do is:

```
Click option > bible font > select bigger font size (default is 11)
```

You could select other font type as well.
If you prefer, you could also change dictionary font, commentary font. etc.

To adjust menu font size, you could see the first post of this page.

DK

---

### Post by razor7 on 2009-01-12
Oh...sorry...just missed the DLL installation part

Now works OK!

---

### Post by david_kt on 2009-01-12
> **razor7 said:**
> Oh...sorry...just missed the DLL installation part

Now works OK!

It is good that it works. I am sure you do it manually, and not using the installer.

That is the very reason I make the installer, to automate everything so that you would not miss any of the steps. The only problem with the installer is when you do not have internet connection, it would practically useless.

DK

---

### Post by paeuk on 2009-01-14
> **david_kt said:**
> I have updated the script to include TSK, I have tested the script and it works. Please download the script at the first post of this thread and try it and hopefully it also work for you. [Here is the link]("http://ubuntuforums.org/attachment.php?attachmentid=99615&d=1231770289").

Alternatively, to install add ons not in the installer, just download the exe (tsk.exe) file first, and remember the location you downloaded it.

Launch the installer script (e-Sword_installer), and choose manual. It will open a browser for you to locate the exe file (tsk.exe).

DK

Fantastic! Thanks David. Was able to install it using your installer but selecting the manual process (beforehand) didn't work. Came up with a Wine error (193 I think). But now is installed using your script so all is fine

Much appreciated :)


Paul

---

### Post by david_kt on 2009-01-14
> **paeuk said:**
> Fantastic! Thanks David. Was able to install it using your installer but selecting the manual process (beforehand) didn't work. Came up with a Wine error (193 I think). But now is installed using your script so all is fine

Much appreciated :)


Paul

Hi Paul, I am glad it finally works for you. I have tried the manual option also works in Hardy. May be you are using Intrepid? I have an issue with zenity in intrepid. The script use zenity to select the exe, so it might be the problem but I could not confirm it as I have downgraded to (re-install) Hardy now.

DK

---

### Post by Will4 on 2009-01-21
Hey brothers, God bless you all
just try to install bibletimes and gnome-sword 

> sudo apt-get install gnomesword
sudo apt-get install bibletime

after you have bibletime installed just run it and F4 to prompt preferences,
after it appears, at the second icon at your left menu, "install/Update books" or something like that
you will find some options.
click on "conect to the library" and you can do whatever after that, download entire libraries of everything.
BUT THE SPECIAL BONUS NOW!!
it will also work for GnomeSword right away. after you install those new libraries for Bibletime, you can open GnomeSword and will have everything there.

---

### Post by varaonaid on 2009-01-21
Hi!

Thanks so much for all the work and suggestions everyone has put into getting e-sword running easily on Linux.

Unfortunately, the script doesn't work at all for me :(

I'm running the latest version of Wine 1.1.13.  After I start the script and choose "esword" as the only item to install, I get this message: 

"Esword_installer error: wine cmd.exe /c echo '%ProgramFiles%' returned empty string

I'm forced to choose "Okay" to exit.  That's as far as I can get.  Any thoughts?

Thanks so much in advance!
Rae

EDIT: I decided to reboot Linux and tried it again...worked perfectly.  I had an older version of Wine installed 1.0, then did upgrade to the newest version (1.1.13) before attempting to install e-Sword but got the above failure.  I guess the newer version of Wine didn't immediately overwrite the previous one without reboot??  Anyway, if you get this error, try to upgrade then reboot.

---

### Post by Neo Cortex on 2009-02-04
Hi
I have just purchased an Acer Aspire and have got e-Sword running well with the default Linpus distribution. The only problem is that the Hebrew text is reversed and the pointing does not appear underneath the consonants but rather in between. Does anyone know how to solve this problem? Alternatively does Hebrew display properly with Ubuntu because if so I might install it?
Thanks for any help

---

### Post by david_kt on 2009-02-04
> **Neo Cortex said:**
> Hi
I have just purchased an Acer Aspire and have got e-Sword running well with the default Linpus distribution. The only problem is that the Hebrew text is reversed and the pointing does not appear underneath the consonants but rather in between. Does anyone know how to solve this problem?

Did you install e-Sword using the installer at the first post of this thread? If not, try to remove e-Sword and re-install it using the installer.

DK

---

### Post by Neo Cortex on 2009-02-05
> **david_kt said:**
> Did you install e-Sword using the installer at the first post of this thread? If not, try to remove e-Sword and re-install it using the installer.

DK
Tried to install using installer but I get a message 
> Esword_installer_error: Note: command 'cabextract --directory=/home/user/.wine_Esword/drive_c/wineeswordtmp/home/user/.wineeswordcache/InstMsiA.exe' returned status 127. Aborting
eSword now runs but no font is displayed for any of the modules. If I try to select a font from the eSword drop down list it just crashes.
I tried uninstalling and then re-installing manually as I did before but this is now broken as well. Any ideas?

---

### Post by david_kt on 2009-02-05
> **Neo Cortex said:**
> Tried to install using installer but I get a message 

eSword now runs but no font is displayed for any of the modules. If I try to select a font from the eSword drop down list it just crashes.
I tried uninstalling and then re-installing manually as I did before but this is now broken as well. Any ideas?

You will need to install cabextract. What I understand, Linpus on Acer come with synaptic package manager. You should be able to install cabextract easily. After you have successfully install cabextract, re-run the e-Sword installer.

DK

---

### Post by Neo Cortex on 2009-02-05
> **david_kt said:**
> You will need to install cabextract. What I understand, Linpus on Acer come with synaptic package manager. You should be able to install cabextract easily. After you have successfully install cabextract, re-run the e-Sword installer.

DK
Thanks. Done that. It is now installed using the installer but the Hebrew font problem is just the same. :(

---

### Post by Neo Cortex on 2009-02-05
I have been playing around with this for a while now. I realised that the Hebrew module which I installed also has Strong's numbers. I installed a module without Strongs and the text is now the right way round but the pointing is still out. I then installed an unpointed module without Strongs. This still doesn't display correctly. The character spacing is wrong: there are gaps in the middle of words and some words run into each other.

I don't know if this helps to isolate the problem.

---

### Post by david_kt on 2009-02-05
> **Neo Cortex said:**
> I have been playing around with this for a while now. I realised that the Hebrew module which I installed also has Strong's numbers. I installed a module without Strongs and the text is now the right way round but the pointing is still out. I then installed an unpointed module without Strongs. This still doesn't display correctly. The character spacing is wrong: there are gaps in the middle of words and some words run into each other.

I don't know if this helps to isolate the problem.

Could you give me a screen shoot or link of what is the correct display for Hebrew text as I do not read any Hebrew at all and I could not differentiate what is right and what is wrong. 

DK

---

### Post by Neo Cortex on 2009-02-05
> **david_kt said:**
> Could you give me a screen shoot or link of what is the correct display for Hebrew text as I do not read any Hebrew at all and I could not differentiate what is right and what is wrong. 

DK
Hi
Here are two images. 

This is how Hebrew should look using Windows. 

[IMG]http://www.sudburybaptist.co.uk/temp/ESword_Windows.jpg[/IMG]

This is how it looks under linpus. The text is going in the correct direction here.

[IMG]http://www.sudburybaptist.co.uk/temp/ESword_Linpus.jpg[/IMG]

---

### Post by jonathonblake on 2009-02-05
> **Neo Cortex said:**
> 
This is how it looks under linpus. The text is going in the correct direction here.

[IMG]http://www.sudburybaptist.co.uk/temp/ESword_Linpus.jpg[/IMG]

That screenshot shows some major problems.
Do both HOT and HOT+ exhibit the same brokup of words and verses?

jonathon

---

### Post by Neo Cortex on 2009-02-05
It's worse with the Strong's module. The individuals words are broken up as in the other module but the text direction is reversed as well. 

Does the Hebrew look the same on other people's systems or is this a Linpus problem?

---

### Post by jonathonblake on 2009-02-05
> **Neo Cortex said:**
> It's worse with the Strong's module. The individuals words are broken up as in the other module but the text direction is reversed as well. 

It _might_ be the tool set used to create the resource.  However,if it is consistent for all your resources, then I'd be looking at either the OS configuration, or Windows emulator.


> Does the Hebrew look the same on other people's systems 

My HOT+ looks ok. The nikkud in my WLC are slightly off, but that is an RTF issue, that can't be fixed.  :(  I don't have the WLC with Strong's  numbers, so I don't know what that looks like. [something else to add to my to do list.]


jonathon

---

### Post by Neo Cortex on 2009-02-05
> **jonathonblake said:**
> It _might_ be the tool set used to create the resource.  However,if it is consistent for all your resources, then I'd be looking at either the OS configuration, or Windows emulator.


 

My HOT+ looks ok. The nikkud in my WLC are slightly off, but that is an RTF issue, that can't be fixed.  :(  I don't have the WLC with Strong's  numbers, so I don't know what that looks like. [something else to add to my to do list.]


jonathon

I think it may be Linpus. I pasted some pointed Hebrew from the web into OpenOffice Writer and it's not brilliant.  I think I might have a look at Ubuntu. Bit reluctant because everything else seems to work so well under Linpus

---

### Post by jonathonblake on 2009-02-05
> **Neo Cortex said:**
> I pasted some pointed Hebrew from the web into OpenOffice Writer and it's not brilliant.  

If that Hebrew included cantillation, then it is going to look bad in OOo, regardless of the platform that is used.   :(

Nikkud _should_ look acceptable,provided one has a decent font.  I don't know which word processor it is, but one of them automatically does a visual differentiation between different nikkud, and cantillation.  The effect looks beautiful.  (Each nikkud is a slightly different shade of the primary.  Likewise, each cantillation mark is slightly different shade of the primary.)

> But reluctant because everything else seems to work so well under Linpus

What does Hebrew text in either GnomeSword and/or BibleTime look like?   If it looks really bad, then it probably is your distro.

jonathon

---

### Post by Neo Cortex on 2009-02-05
> **jonathonblake said:**
> 
What does Hebrew text in either GnomeSword and/or BibleTime look like?   If it looks really bad, then it probably is your distro.

jonathon
BibleTime crashes so I don't know.
GnomeSword is OK but I only have an unpointed text so I can't really compare

---

### Post by david_kt on 2009-02-05
Looks like mine is ok (see attached), right?
May be you could tru to copy all your fonts from windows ( from C:/WINDOWS/Fonts folder) to /home/username/.fonts (please note there is a dot in from of fonts!!!).

If /home/username/.fonts is not  available yet, just create that directory. After that, issue below command in terminal:

```
fc-cache -f -v
```

And then try again your e-Sword.

DK

---

### Post by jonathonblake on 2009-02-05
> **david_kt said:**
> Looks like mine is ok (see attached), right?

Yes.  And no.   

You have  a slightly different issue. It _might_ be related.   (If I could reproduce it, might know what to change to fix it.)

jonathon

---

### Post by Neo Cortex on 2009-02-06
> **david_kt said:**
> Looks like mine is ok (see attached)
Actually my HOT module looks very similar to yours so it seems as if it isn't just a Linpus issue

---

### Post by jonathonblake on 2009-02-06
> **Neo Cortex said:**
> Actually my HOT module looks very similar to yours

I've attached screenshots of my Hebrew Bibles here.  Filenames indicate which is displayed the way it should be.

jonathon

---

### Post by Neo Cortex on 2009-02-06
> **jonathonblake said:**
> I've attached screenshots of my Hebrew Bibles here.  Filenames indicate which is displayed the way it should be.

jonathon
So yours also goes backwards when there are Strong's numbers. Still, at least it is legible unlike mine.

I see what you mean about the Nikkud in the WLC but it looks good enough.

So which Hebrew font are you using?

---

### Post by jonathonblake on 2009-02-06
> **Neo Cortex said:**
> So yours also goes backwards when there are Strong's numbers.

I _may_ go in and hand edit everything, when I redo it for Portable e-Sword.

> So which Hebrew font are you using?

SBL Hebrew.  I have no idea where, or when I acquired it.

jonathon

---

### Post by cytung on 2009-02-07
> **jonathonblake said:**
> I've attached screenshots of my Hebrew Bibles here.  Filenames indicate which is displayed the way it should be.

jonathon

Chase you down from [e-Sword_tools]:D
Looking at your screen captures, there is hope.  
It seems that it is still the Wine configuration issue and perhaps e-Sword tweak.
I copied a verse from WLC and paste it to OO.  
If paste as RTF, it looks perfect, even right to left.  (The lower one)
If paste as unformatted text, well, it is unformatted.  (The upper one)
As I mentioned in the e-Sword_tools, when the text is pasted into notepad, running under Wine, it looks GOOD.  I.e. Wine/Windows display of Hebrew Unicode seems to be ok.

---

### Post by jonathonblake on 2009-02-07
> **cytung said:**
> Wine configuration issue and perhaps e-Sword tweak.

Until the next update of e-Sword is released, I'm not going to bother with any user configuration/tweaking  for e-Sword, under WINE. 

jonathon

---

### Post by david_kt on 2009-02-07
> **cytung said:**
> Chase you down from [e-Sword_tools]:D
Looking at your screen captures, there is hope.  
It seems that it is still the Wine configuration issue and perhaps e-Sword tweak.
I copied a verse from WLC and paste it to OO.  
If paste as RTF, it looks perfect, even right to left.  (The lower one)
If paste as unformatted text, well, it is unformatted.  (The upper one)
As I mentioned in the e-Sword_tools, when the text is pasted into notepad, running under Wine, it looks GOOD.  I.e. Wine/Windows display of Hebrew Unicode seems to be ok.

Thank you for your screenshoot. Looks like the problem is bidirectional support is not enable by default. I have tried to enable it but not so unsuccessful yet. In the mean time, could you advice whether or not below screenshoot acceptable?

DK

---

### Post by cytung on 2009-02-08
> **david_kt said:**
> Thank you for your screenshoot. Looks like the problem is bidirectional support is not enable by default. I have tried to enable it but not so unsuccessful yet. In the mean time, could you advice whether or not below screenshoot acceptable?

DK

Hi David,
Very hard to look at the screenshot, small fonts.  Anyhow, after looking at Jonathon's and your screenshots, and went back to your installation script and explanation, I was able to get "similar" display to yours, mainly by upgrading Wine from 1.0.1 to 1.1.14.
I installed e-Sword by running setup806.exe directly under Wine, like how I installed several other windows programs (while still at 1.0.1).  Then did the unusual things like copying dll's and make them native, per your instructions later found.  That's when I posted on e-Sword tools about the Hebrew display issue.  
No, I still don't think the display is right.  I guess the comparison should be to how it is displayed under notepad.
Here are two, similar to yours on Gen. one with Hot, another with WLC.  I made the fonts much larger...
Ok, let me upload another notepad screenshot too.
BTW, thanks, David for your effort in getting e-Sword running under Linux.

---

### Post by jonathonblake on 2009-02-08
> **cytung said:**
> 

Ok, let me upload another notepad screenshot too.
Is the word wrapping in your Notepad screenshot correct?

Something looks wrong,but I can't put my finger on what it is.

jonathon

---

### Post by david_kt on 2009-02-08
[QUOTE=cytung;6701715] I guess the comparison should be to how it is displayed under notepad.
Here are two, similar to yours on Gen. one with Hot, another with WLC. /QUOTE]

There are 2 errors obious:
1. I have tried to enable bidirectional support but it is still inform that "mirroring character" not yet implemented. I guess we have to wait for the later wine, or a patch from Shachar Shemesh from Israel who is maintaining bidirectional support in wine.

2. Another error is the font is still not available yet, and it is using the nearest fonts. If you happen to know what font is used for HOT, than it might be a great help to render the text better.

DK

---

### Post by david_kt on 2009-02-09
I go to my windows xp box, enable Hebrew language support, and open up e-Sword. The Hebrew bible is pretty much the same as in ubuntu with wine 1.1.4, except the book name and the verse is on the right.

Anybody could help me to make e-Sword render Hebrew perfectly in windows XP? After that may be I would be able to improve e-Sword on linux.

DK

---

### Post by cytung on 2009-02-10
> **jonathonblake said:**
> Is the word wrapping in your Notepad screenshot correct?

Something looks wrong,but I can't put my finger on what it is.

jonathon

Looks right to me, as far as I can tell.   It is left to right with Hebrew text section right to left.

---

### Post by angierfw@gmail.com on 2009-03-03
> **ardchoille42 said:**
> You could also just 
```

sudo apt-get install gnome-sword

```
to get a nice bible app in gnome

or

```

sudo apt-get install bibletime

```
to get a nice bible app in KDE.

As has been pointed out the sword based systems - while usable - do not have a patch on E-Sword.
I have just installed it without the script but with reference to it as I nomally download e-sword and its bits and pieces to create cd's for others and did not want to go through waiting for downloads. As per the manual install notes it just worked first time!
System is Gentoo with KDE3.5. I will now do my home PC and my notebook - both Gentoo.
The wine version on all system is wine-1.1.12. All seems to work like it is advertised! 
Thanks for the info!

Ang

---

### Post by silvagroup on 2009-03-03
> As per the manual install notes it just worked first time!
That's all I have used for several years for installing e-sword. The problem with installing resources seems to have been cleared up with the newer wine versions since 1,0 and if you do have a problem just copy the resource from a Windows install and add it to your e-sword resource directory in the Linux install.

Now what I typically do with Linux installs is run the initial installer form e-sword and then copy all resources from a cd to new install. But please be aware that if you are doing this and it's to some one else's system, to remove any of your licensed materials from there unless they have also purchased the license for it.

---

### Post by benjieg on 2009-03-04
Hi,

Thank you for this post.  I have been a long-time e-Sword user on Windows and have switched to Linux Mint.  I am using GnomeSword which is quite capable, but nothing beats e-Sword.  I now have a running e-Sword install on my Linux Mint system.  Thanks you very much.

-- Benjie

---

### Post by lisati on 2009-03-04
I'm a fan of e-sword too. The only time I've tried it with Wine was from an installation disk for v7.7.7 that I received after donating. It worked well but I wasn't comfortable with Wine.

---

### Post by david_kt on 2009-03-04
> **angierfw@gmail.com said:**
> 
I have just installed it without the script but with reference to it as I nomally download e-sword and its bits and pieces to create cd's for others and did not want to go through waiting for downloads. As per the manual install notes it just worked first time!

I am glad that manual instruction works for you, some people faces difficulties following manual instructions. But if you want to save your time, copy all the downloaded file to /home/username/.wine_Esword and then use the script. If it find the programs there, it would not download it again.

Other addons not available in the script, you could choose "manual" to install from the script. 

DK

---

### Post by david_kt on 2009-03-04
> **lisati said:**
> I'm a fan of e-sword too. The only time I've tried it with Wine was from an installation disk for v7.7.7 that I received after donating. It worked well but I wasn't comfortable with Wine.

Well, then the script I make is exactly for people like you. Try out the script and hope you would be amazed by how easy it is to install e-Sword on linux.

DK

---

### Post by benjieg on 2009-03-04
> **david_kt said:**
> Well, then the script I make is exactly for people like you. Try out the script and hope you would be amazed by how easy it is to install e-Sword on linux.

DK

The pleasant surprise is that I noticed it loads a lot faster on Linux/Wine than on my Windows system.  I'm not sure though if it is due to the small number of modules I've installed so far on Linux compared to Windows.  But it's really fast.

---

### Post by Neo Cortex on 2009-03-05
> **jonathonblake said:**
> Until the next update of e-Sword is released, I'm not going to bother with any user configuration/tweaking  for e-Sword, under WINE. 

jonathon
So is there an update due soon?

---

### Post by zeroandone on 2009-03-12
I tried to install e-Sword under Ubuntu Jaunty (9.04 Alpha 6) with Wine 1.1.16, everything was fine until the e-Sword installer asked for User Name and Organization. Please see the attached screen shot. I installed e-Sword under Ubuntu 8.10 before, but when asked for User Name and Organization, those text boxes were blank, not like the screen attached. Am I missing something or is it normal?

Thanks,

---

### Post by david_kt on 2009-03-13
> **zeroandone said:**
> I tried to install e-Sword under Ubuntu Jaunty (9.04 Alpha 6) with Wine 1.1.16, everything was fine until the e-Sword installer asked for User Name and Organization. Please see the attached screen shot. I installed e-Sword under Ubuntu 8.10 before, but when asked for User Name and Organization, those text boxes were blank, not like the screen attached. Am I missing something or is it normal?

Thanks,

Yes it is normal.

By the way, does the e-sword run as usual after that?

DK

---

### Post by zeroandone on 2009-03-13
Yes. e-Sword was installed correctly after that. One thing I noticed that if I cancel the installation, then it gives me an error message, please see the attached screen shot. 

Also e-sword.lnk never works form me and the error is "The file is of an unknown type." What is e-sword.lnk for?

Another thing but I think it is related to Ubuntu Jaunty: after installation, there is no e-sword launcher icon on the desktop, instead there is a shortcut called **e-sword.desktop**, when you double click on it, the system will warn you that it is an untrusted launcher or something like that, and give you three options: Launch Anyway, Mark it Trusted, Cancel. Click "Mark it Trusted" will turn e-sword.desktop into the normal e-sword launcher icon. I guess Ubuntu Jaunty tightened the security.

---

### Post by david_kt on 2009-03-13
> **zeroandone said:**
> One thing I noticed that if I cancel the installation, then it gives me an error message, please see the attached screen shot. 

Also e-sword.lnk never works form me and the error is "The file is of an unknown type." What is e-sword.lnk for?

Another thing but I think it is related to Ubuntu Jaunty: after installation, there is no e-sword launcher icon on the desktop, instead there is a shortcut called **e-sword.desktop**, when you double click on it, the system will warn you that it is an untrusted launcher or something like that, and give you three options: Launch Anyway, Mark it Trusted, Cancel. Click "Mark it Trusted" will turn e-sword.desktop into the normal e-sword launcher icon. I guess Ubuntu Jaunty tightened the security.

If you cancel the installation, the script will detect it as error as the process has not completed yet, it is intended to be that way. And it will inform you which process has not completed successfully.

For e-sword.lnk, you could just delete it as it is not implemented yet in wine and as a replacement wine create e-sword.desktop.

For the last one it is true it is for security issue. Somebody has demonstrated that by inserting something.desktop file to you computer and attract you to double click it, it could do a lot of harm to your system. As such, it is very good that jaunty has additional security measure to respond to this.

DK

---

### Post by jonathonblake on 2009-03-13
> **benjieg said:**
> it loads a lot faster on Linux/Wine than on my Windows system. 

Most of the decrease in loading time, is due to not running anti-malware programs in Linux. 

I have read several blogs that claim that WINE runs programs faster,and more efficiently than Windows does.   Any version of Windows.)

jonathon

---

### Post by jonathonblake on 2009-03-13
> **Neo Cortex said:**
> So is there an update due soon?

Rick doesn't publish a roadmap, or list of scheduled releases.

There were several features I expected in e-Sword 7.8.5, that were not included in either that version, or e-Sword 8.0.6. 

It will be released before "real soon now", but I don't know how much sooner than that.  

jonathon

---

### Post by aaronhahn777 on 2009-03-23
k51: (regarding to adding bibles/maps/commentaries)

you will have to unpack these files on a PC then simply cut-paste them into your ./wine/e-sword folder

cheers.

(for some reason wine hangs on the additional packages from e-sword)

---

### Post by tom4jean on 2009-03-23
Hello, I have E-sword working with some errors and was looking for some help. I just installed on 8.10 Intrepid Ibex

First, I went through the procedure to update wine, and according to the wine download page the latest development release is 1.1.17 and the stable release is 1.1.1 
So after installing the stable release through the repository I updated to the development release of 1.1.17 and that is the version that I now have running.

**But**, the e-sword installer is telling me I don't have the correct version and it should be **"1.1.7" please notice it ends in "xx.7" not the "xx.17" missing the "1"** that I have now.
I don't see the 1.1.7 version available from the wine download page at all. According to the Wine website 1.1.17 is the most current development release. So, is the reference to 1.1.7 that is both in the thread instructions and the e-sword installer a misprint and should it be 1.1.17?

So, I went ahead and used the installer anyway and e-sword runs with the following errors.

1. "Error 3078 The Microsoft jet database engine cannont find the input table or query "Verse Notes" Make sure it exists and the name is spelled correctly."
2. "Error in loading DLL 48"
3. "Error 3265 Item not found in this collection"
4. "Error updating study notes database"
5. "Invalid verse list file: C:\users\thomas\MyDocuments\e-sword\Bookmarks.lst"

Once I click "ok" and clear these errors e-sword is up and running.

And then finally when I close e-sword I get;

6. "Error compacting database file: C:\users\thomas\MyDocuments\e-sword\study.not"

I have tried re-running the e-sword installer and repairing, and also rebooting and always with the same errors each time.

I am guessing that perhaps updating wine to 1.1.7 may work to fix it, if there is such a version, and then reinstall e-sword?

Or is 1.1.17 the correct release and are my errors unrelated to the wine version I have?

Any help would be greatly appreciated. 
God Bless,
Tom

---

### Post by zeroandone on 2009-03-23
> **tom4jean said:**
> Hello, I have E-sword working with some errors and was looking for some help. I just installed on 8.10 Intrepid Ibex

First, I went through the procedure to update wine, and according to the wine download page the latest development release is 1.1.17 and the stable release is 1.1.1 
So after installing the stable release through the repository I updated to the development release of 1.1.17 and that is the version that I now have running.

**But**, the e-sword installer is telling me I don't have the correct version and it should be **"1.1.7" please notice it ends in "xx.7" not the "xx.17" missing the "1"** that I have now.
I don't see the 1.1.7 version available from the wine download page at all. According to the Wine website 1.1.17 is the most current development release. So, is the reference to 1.1.7 that is both in the thread instructions and the e-sword installer a misprint and should it be 1.1.17?

So, I went ahead and used the installer anyway and e-sword runs with the following errors.

1. "Error 3078 The Microsoft jet database engine cannont find the input table or query "Verse Notes" Make sure it exists and the name is spelled correctly."
2. "Error in loading DLL 48"
3. "Error 3265 Item not found in this collection"
4. "Error updating study notes database"
5. "Invalid verse list file: C:\users\thomas\MyDocuments\e-sword\Bookmarks.lst"

Once I click "ok" and clear these errors e-sword is up and running.

And then finally when I close e-sword I get;

6. "Error compacting database file: C:\users\thomas\MyDocuments\e-sword\study.not"

I have tried re-running the e-sword installer and repairing, and also rebooting and always with the same errors each time.

I am guessing that perhaps updating wine to 1.1.7 may work to fix it, if there is such a version, and then reinstall e-sword?

Or is 1.1.17 the correct release and are my errors unrelated to the wine version I have?

Any help would be greatly appreciated. 
God Bless,
Tom

Did you install **cabextract**? You will need both wine and cabextract to install e-Sword.

---

### Post by tom4jean on 2009-03-23
> **zeroandone said:**
> Did you install **cabextract**? You will need both wine and cabextract to install e-Sword.

Yes, I did.
But when I installed it the installer said I already had the most current version of cabextract and it did not install it.

I also did just search the wine site and see that 1.1.7 is in fact an older development release than 1.1.17, I thought it was a misprint.

I could not find a place to get the 1.1.7 version in a .deb package from wine, it just sends me back to the download site for 1.1.17 when I try to get it from their older 1.1.7 release announcement page.

---

### Post by jonathonblake on 2009-03-23
> **tom4jean said:**
>  So, is the reference to 1.1.7 that is both in the thread instructions and the e-sword installer a misprint and should it be 1.1.17?

WINE 1.1.7 did things slightly differently, and those  differences are enough to make it more compatible with e-Sword than WINE 1.1.17.

One of these days I'm going to figure out what version of WINE works best with e-Sword. (Debian backports, and Debian stable, and Debian unstable have older versions of WINE.)

> Or is 1.1.17 the correct release and are my errors unrelated to the wine version I have?

Whilst I haven't seen those specific errors with e-Sword under WINE 1.1.17, I wouldn't be surprised if they were related to the version of WINE you are using.   


jonathon

---

### Post by tom4jean on 2009-03-23
Jonathon,

Thanks for the response. I again tried uninstalling and using the 1.1.1 from the repository with the same errors, except I did not have the dll48 one. It runs at least, once I get past the errors.
Tom

---

### Post by jonathonblake on 2009-03-23
> **tom4jean said:**
>  repository with the same errors, except I did not have the dll48 one. 

Delete study.not, and Verse.lst in both the program directory, and your user directory.

(I'm sorry, I should have caught that when I first replied. Those are are errors for e-Sword 8.0.6.   They are fairly common for e-Sword 7.8.x.)

jonathon

---

### Post by david_kt on 2009-03-23
> **tom4jean said:**
> Yes, I did.
But when I installed it the installer said I already had the most current version of cabextract and it did not install it.

I also did just search the wine site and see that 1.1.7 is in fact an older development release than 1.1.17, I thought it was a misprint.

I could not find a place to get the 1.1.7 version in a .deb package from wine, it just sends me back to the download site for 1.1.17 when I try to get it from their older 1.1.7 release announcement page.

No, it is not misprinted. Please try using wine 1.1.7 for intrepid. You could donwload it from below link:

[http://wine.budgetdedicated.com/archive/ubuntu/intrepid/wine_1.1.7~winehq0~ubuntu~8.10-0ubuntu1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/intrepid/wine_1.1.7~winehq0~ubuntu~8.10-0ubuntu1_i386.deb)

That is the version I have when I updated the script. Some user has reported 1.1.10 and 1.1.12 are also working well:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14655](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14655)

DK

---

### Post by Crimson Red on 2009-03-24
I got a problem with this. I'm using wine 1.1.17 and the installation kept n hanging up every time I click the install part. What's the possible problem with this?

---

### Post by david_kt on 2009-03-24
> **Crimson Red said:**
> I got a problem with this. I'm using wine 1.1.17 and the installation kept n hanging up every time I click the install part. What's the possible problem with this?

Could you remove wine 1.1.17 and install wine 1.1.7?

If you are using intrepid you could download it here:

[http://wine.budgetdedicated.com/archive/ubuntu/intrepid/wine_1.1.7~winehq0~ubuntu~8.10-0ubuntu1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/intrepid/wine_1.1.7~winehq0~ubuntu~8.10-0ubuntu1_i386.deb)

After that re-run the installer.

DK

---

### Post by zeroandone on 2009-03-24
> **Crimson Red said:**
> I got a problem with this. I'm using wine 1.1.17 and the installation kept n hanging up every time I click the install part. What's the possible problem with this?

I installed e-sword on both Ubuntu 8.10 and 9.04 Alpha 5 with wine 1.1.17 without any problems. Remember though, the first step of the installation is to download e-sword from [www.e-sword.net](www.e-sword.net) and it takes quite some time to download the file and may seem that the installer "has hung up".

---

### Post by david_kt on 2009-03-24
> **zeroandone said:**
> I installed e-sword on both Ubuntu 8.10 and 9.04 Alpha 5 with wine 1.1.17 without any problems. Remember though, the first step of the installation is to download e-sword from [www.e-sword.net](www.e-sword.net) and it takes quite some time to download the file and may seem that the installer "has hung up".

If that is the case, it is problem with zenity and I have filed a bug complain on that. It is true that on intrepid the download GUI do not show properly, but the download is still running as normal.

DK

---

### Post by Crimson Red on 2009-03-24
> **david_kt said:**
> Could you remove wine 1.1.17 and install wine 1.1.7?

If you are using intrepid you could download it here:

[http://wine.budgetdedicated.com/archive/ubuntu/intrepid/wine_1.1.7~winehq0~ubuntu~8.10-0ubuntu1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/intrepid/wine_1.1.7~winehq0~ubuntu~8.10-0ubuntu1_i386.deb)

After that re-run the installer.

DK

I've done it already. It's still the same. The installer hangs up after I click "next" on the the stage where I have to put the "Username and Organization." 

Any other solution for this?

---

### Post by Crimson Red on 2009-03-24
> **david_kt said:**
> If that is the case, it is problem with zenity and I have filed a bug complain on that. It is true that on intrepid the download GUI do not show properly, but the download is still running as normal.

DK

You're right. I think the installer is still running but it does not display properly and looks like it hung up.

How to fix it anyway?

---

### Post by david_kt on 2009-03-24
> **Crimson Red said:**
> You're right. I think the installer is still running but it does not display properly and looks like it hung up.

How to fix it anyway?

First, reboot your computer, and then re-run the installer from command line and copy and paste the output here:

Open terminal > navigate to the installer location > and then:

```
./e-Sword_installer
```

It would run the installer. if it hang, copy and paste the message from that terminal.

DK

---

### Post by zeroandone on 2009-03-24
> **Crimson Red said:**
> You're right. I think the installer is still running but it does not display properly and looks like it hung up.

How to fix it anyway?

What do you mean "it does not display properly"? Did you see a download window with a progress bar that is not moving? Last time I just left the download window there for about 15 minutes and then the e-sword installer started.

---

### Post by david_kt on 2009-03-24
> **zeroandone said:**
> What do you mean "it does not display properly"? Did you see a download window with a progress bar that is not moving? Last time I just left the download window there for about 15 minutes and then the e-sword installer started.

I just check [http://www.e-sword.net/files/setup806.exe](http://www.e-sword.net/files/setup806.exe) sometimes is not responding and inform to use IE or firefox instead of MSN and to disable any download manager. Not sure if it try to block wget as well.

Please help to check as I am on XP now and if it block wget, I would try to think of other alternatives.

DK

---

### Post by Crimson Red on 2009-03-24
I have installed it already but when it started, it hung up. Do I need to do something?

---

### Post by david_kt on 2009-03-24
> **Crimson Red said:**
> I have installed it already but when it started, it hung up. Do I need to do something?

Restart you computer (important), and then open terminal and run below command:

```
env WINEPREFIX=~/.wine_Esword wine "C:\Program Files\e-Sword\e-Sword.exe"

```

Please copy and paste the message in the terminal if it is hanged.

DK

---

### Post by Crimson Red on 2009-03-24
Here is the message:

fixme:storage:StgCreateDocfile Storage share mode not implemented
fixme:win:LockWindowUpdate (0x20030), partial stub!
fixme:win:LockWindowUpdate (0x20030), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!


What does this mean?

The e-sword window just hung up and it's kind of transparent.

---

### Post by david_kt on 2009-03-25
> **Crimson Red said:**
> Here is the message:

fixme:storage:StgCreateDocfile Storage share mode not implemented
fixme:win:LockWindowUpdate (0x20030), partial stub!
fixme:win:LockWindowUpdate (0x20030), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!


What does this mean?

The e-sword window just hung up and it's kind of transparent.

It might be problem with your video card. What is your video card? Please disable compiz and try it again:

```
System>Preferences>Appearance. Go to the Effects tab and select None

```

 If after you disable compiz it is still not working well, you might need to instal special driver for you video card. To check whether your video card is working well or not, open terminal and issue below command:

```
glxinfo | grep render
```

and copy and paste the output here. I saw you are typing the output of terminal, you could copy and paste instead of typing it: 
1. Highlight the text and the terminal using mouse with left click.
2. press ctrl+shift+c to copy.
3. Go to the browser and press ctrl+v to paste

DK

---

### Post by Crimson Red on 2009-03-25
Alright thanks.

Here we go:

direct rendering: Yes
OpenGL renderer string: Mesa DRI UniChrome 20060710 x86/MMX/SSE2

---

### Post by david_kt on 2009-03-25
> **Crimson Red said:**
> Alright thanks.

Here we go:

direct rendering: Yes
OpenGL renderer string: Mesa DRI UniChrome 20060710 x86/MMX/SSE2

Have you try to disable compiz and run e-Sword?

Also please paste the output of:
```

lspci | grep VGA
```

DK

---

### Post by Crimson Red on 2009-03-25
yup, It still hangs up.

Here's the output:

01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] (rev 01)

By the way, I've set my video card memory  to 8mb. Do I need to set it back to default?

---

### Post by david_kt on 2009-03-25
> **Crimson Red said:**
> yup, It still hangs up.

Here's the output:

01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] (rev 01)

By the way, I've set my video card memory  to 8mb. Do I need to set it back to default?

Not sure about video card memory. Anyhow, you could try to set it back to default and see if that help.

But for wine, the problem is more on the dri. What you could do is to disable dri by editing /etc/X11/xorg.conf and disable DRI in the "Module" section.

open terminal and:

```
gksudo gedit /etc/X11/xorg.conf
```

Find section below:

```
    Section "Module"
        ...
        Load    "dri"
        ...
    EndSection
```

and change it to

```
    Section "Module"
       ...
       Disable    "dri"
       ...
    EndSection
```

Restart you computer and launch e-Sword again.

DK

---

### Post by Crimson Red on 2009-03-25
Funny. I did not find the "Module" section.
All I found is these:
```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

---

### Post by david_kt on 2009-03-25
> **Crimson Red said:**
> Funny. I did not find the "Module" section.
All I found is these:
```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

Then could you try to add:

```

Section "Module"
        Disable "glx"
        Disable "dri"
EndSection


```

at the end of the file, and after that restart your computer and launch e-sword.

DK

---

### Post by Crimson Red on 2009-03-26
It still won't work. I've set my memory sharing to default already, yet it still hangs up.

---

### Post by david_kt on 2009-03-26
> **Crimson Red said:**
> It still won't work. I've set my memory sharing to default already, yet it still hangs up.

Then try to force to use Vesa:

```
gksudo gedit /etc/X11/xorg.conf
```

Copy and paste below (delete all other entries):


```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

Reboot and see if this help.

DK

---

### Post by Crimson Red on 2009-03-29
Great! It's working now! Thanks a lot. God bless. :)

---

### Post by david_kt on 2009-03-29
> **Crimson Red said:**
> Great! It's working now! Thanks a lot. God bless. :)

By the way, it is comfirmed you have problem with your graphic card/chipset. To have get the best result, you should try to make your graphic card work but I am not sure whether or not I will be able to help you to tweak the configuration to get your video card working, or you will be able to have a correct driver for your chipset in the future.

For me, I play it safe and always choose intel graphic card, normally well supported by linux.

DK

---

### Post by Crimson Red on 2009-03-29
Right, I'll keep that in mind. Thanks.

---

### Post by asmotj on 2009-04-05
I had the wine 1.01. and simply uninstalled it and reinstalled wine 1.17 from page 38 and it worked flawless with 9.04
The old version started OK but would not show text now it works grweat
Thanks for all the support  

:guitar:

---

### Post by asmotj on 2009-04-05
> **zeroandone said:**
> I installed e-sword on both Ubuntu 8.10 and 9.04 Alpha 5 with wine 1.1.17 without any problems. Remember though, the first step of the installation is to download e-sword from [www.e-sword.net](www.e-sword.net) and it takes quite some time to download the file and may seem that the installer "has hung up".

BE patient it took me a long time as well almost 20 minutes I just got up and cleaned the kitchen):P

---

### Post by david_kt on 2009-04-05
I have added font smoothing as David Devonshire fedback that in Jaunty wine fonts looks very bad (jagged). Please see the first post of this thread to download the script to smoothen the fonts. I found the script from:
[http://www.wine-reviews.net/wine-reviews/tips-n-tricks/how-to-enable-font-anti-aliasing-in-wine.html](http://www.wine-reviews.net/wine-reviews/tips-n-tricks/how-to-enable-font-anti-aliasing-in-wine.html)

and I edited it to suite e-Sword wineprefix. You have to choose run in terminal.

I have also fixed the download progress bar, now it will show nice download progress bar when downloading in Intrepid and also in hardy and ubuntu previous release. I have not tested it yet in Jaunty.

DK

---

### Post by Shabakthanai on 2009-04-23
Jaunty Rc kde  I had lots of trouble getting Wine installed but think it is in and OK now.  I tried to download the e-Sword installer, but it is a .tar.gz and I don't seem to have the appropriate package to open it.  I tried kate which said it needed to be read/write and is read only.  I tried Ark but it doesn't have the ability to open tar.gz.  I am sure I am doing something very wrong, but some help would be greatly appreciated.  What application should be used to open the package?  Thanks!

---

### Post by silvagroup on 2009-04-23
Easiest way is to download the e-Sword installer exe from the e-Sword web site right click on the downloaded file and select run with wine application launcher.
That has always worked for me.

---

### Post by jonathonblake on 2009-04-23
> **Shabakthanai said:**
>  I tried to download the e-Sword installer,

Are you talking about the scripts in the first message of the thread at [http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042) or the tarball installer available from  WhatWouldJesusDownload?

Either way the following commands will make it read/write, and then extract it:
```

sudo chmod 777 *.tar.gz
tar -xvvf *.tar.gz

```

jonathon

---

### Post by ag65151 on 2009-04-23
There is never a reason to ```
chmod 777
``` anything.

Those numbers are for read/write/execute bits for user/group/world. If you enable all bits, anyone can write to it whatever they want and then execute it. 
```
chmod 755 
```

means only the user can read/write/execute and everyone else can only read/execute. It should be more than enough to accomplish any task and it doesn't open the door for someone to input a malicious command.

I don't mean to sound angry, but I am a bit passionate about computer security.

---

### Post by silvagroup on 2009-04-23
No, try this, [http://www.e-sword.net/files/setup806.exe]("http://www.e-sword.net/files/setup806.exe").
It has always worked for me.

---

### Post by david_kt on 2009-04-24
> **Shabakthanai said:**
> Jaunty Rc kde  I had lots of trouble getting Wine installed but think it is in and OK now.  I tried to download the e-Sword installer, but it is a .tar.gz and I don't seem to have the appropriate package to open it.  I tried kate which said it needed to be read/write and is read only.  I tried Ark but it doesn't have the ability to open tar.gz.  I am sure I am doing something very wrong, but some help would be greatly appreciated.  What application should be used to open the package?  Thanks!

Just **_right click_** and the downloaded file and choose _**extract here**_. After that _**double click**_ on the extracted file.

DK

---

### Post by jonathonblake on 2009-04-24
> **ag65151 said:**
> I don't mean to sound angry, but I am a bit passionate about computer security.

You are absolutely right. 755 is far more appropriate. 

Using 777 is a sloppy habit I got into, as a sysadmin for Windows and Dos.  (And I did use chmod on those systems.)

jonathon

---

### Post by wildman4god on 2009-04-25
I am trying to install bibles, commentaries, etc but when I launch the installer it takes forever and never finishes, I ran the installer from the cli and it keeps repeating the same line over and over for an hour, then I stop the process, is it supposed to take hours to install a bible? I am using ubuntu 9.04 and wine version 1.0.1

---

### Post by ChristianConservative.ca on 2009-04-27
Was having issues with the script in Jaunty, was getting the following error at the end of the install:> Esword_installer error: Note: command 'cp -f /home/USER/.wine_Esword/drive_c/Program Files/e-Sword/riched20.dll /home/apresco0/.wine_Esword/drive_c/windows/system32' returned status 1. Aborting.When I tried to launch the app, it launched, but with no content... it showed the books listed on the left, and I could access the chapters, but no verses showed in the main screen.

I then followed some of the recomendations for the manual install, and I got it to work, I think key was using winecfg to set riched20.dll and oleaut32.dll to "(Windows) native" via the following command, then by following the steps in the original installer instructions here... [http://ubuntuforums.org/showthread.php?t=404042&highlight=e-sword](http://ubuntuforums.org/showthread.php?t=404042&highlight=e-sword):

> env WINEPREFIX=~/.wine_Esword winecfg 

Press the Libraries tab > type riched20.dll > press add > press edit > choose Native (windows).
Do the same for oleaut32.dll.I then ran the following, modifying the command because of where my e-Sword was installed:
 
> env WINEPREFIX=~/.wine_Esword wine "C:\Program Files\e-Sword\e-Sword.exe"(mine was installed on the root of the Wine C: drive, so I replaced "C:\Program Files\e-Sword\e-Sword.exe" with just "C:\e-Sword.exe"... while we're on that note, that's another bug I noticed, the root of the Wine C: is where the installer script wanted to put e-Sword, and it crashed whenever I tried to change that)

Worked like a charm after that, and every time since.  Hope that helps someone out there... I'm a re-newbie to Ubuntu/Linux (last time I touched Linux was in college, back in 1999) so this is my first official "contribution" to the Open Source movement!  (and I hope it's a blessing to my brethren/sisteren!)

---

### Post by david_kt on 2009-04-27
> **wildman4god said:**
> I am trying to install bibles, commentaries, etc but when I launch the installer it takes forever and never finishes, I ran the installer from the cli and it keeps repeating the same line over and over for an hour, then I stop the process, is it supposed to take hours to install a bible? I am using ubuntu 9.04 and wine version 1.0.1

Please upgrade you wine to wine 1.1.7

DK

---

### Post by zeroandone on 2009-05-03
A new version of e-sword is released, will this e-sword installer be upgraded as well?

Thank you for the hard work.

---

### Post by david_kt on 2009-05-03
> **zeroandone said:**
> A new version of e-sword is released, will this e-sword installer be upgraded as well?

Thank you for the hard work.

I am upgrading to Jaunty, I will surely make installer for the new e-Sword. But bear in mind that the new version use completely different database system and not compatible with old database.

As such, I would make separate installer and install it on separate directory so that you could have  version of e-Sword at the same time.

DK

---

### Post by jonathonblake on 2009-05-04
> **david_kt said:**
> 
As such, I would make separate installer and install it on separate directory so that you could have  version of e-Sword at the same time.

e-Sword 9.0.1 automatically converts files in the user directory, to the new format. 

If possible, would either use the same e-sword user directory for both versions of e-Sword, or else offer to copy resources to the user directory for the new version of e-Sword?

jonathon

---

### Post by david_kt on 2009-05-07
Good news!!! I have updated the installer to use e-Sword 9.0.1. I have tested using hardy and jaunty, both work without any problem.

As suggested by Jonathon, I put it on the same wineprefix as before. If you worry the new e-Sword is not compatible with some of the addons, you could run the backup first in the installer. Just in case you want to revert back to old e-sword, you could use restore functions in the installer script.

If you want to run both version, just let me know I will help you to do that. It is simple.

Again, please let me know if you have difficulty in installing e-Sword.

DK
NB: Do not worry about below message, I use other mirror (brothersoft) for the script to download the main program, but all addons are downloaded from official website. I will revert back to the official site if necessary later. You could use the script now!!!

ATTENTION

Due to the extreme amount of traffic volume for downloading e-Sword version 9, I have to discontinue the main download for a few days while the colo pulls in another 4 GB of fiber to accommodate this load. Unfortunately the local hospitals were being brought down by e-Sword using all of the available bandwidth! If you have already installed version 9, then no worries as the updated Bibles and other add-on modules are still available for you to download. If you have not updated to version 9, then please do not bother downloading any add-on modules as they will not install for older versions anyway. Thank you for your patience, and keep checking back.

---

### Post by zeroandone on 2009-05-07
Thank you David for the hard work.

---

### Post by silvagroup on 2009-05-07
I just downloaded the setup.exe from e-sword web site ran by right clicking on it and it installed.
When I launched e-sword I got an some errors related to mfc42u.dll. So I copied it to my .wine drive_c/windows/system32 directory launched e-sword again and it worked just fine.
Data base engine has been changed so modules need to downloaded old one won't work with version 9.

---

### Post by david_kt on 2009-05-07
> **silvagroup said:**
> I just downloaded the setup.exe from e-sword web site ran by right clicking on it and it installed.
When I launched e-sword I got an some errors related to mfc42u.dll. So I copied it to my .wine drive_c/windows/system32 directory launched e-sword again and it worked just fine.
Data base engine has been changed so modules need to downloaded old one won't work with version 9.

How about graphic viewer? Is it working as well?

DK

---

### Post by silvagroup on 2009-05-07
Does not. You know I am not sure it ever has worked with wine. I have never had a real need to use the graphic viewer so I am not sure if it actually ever has worked.

Some one else may have info on the specifics of graphic viewer.

Actually I usually go back to 7.8.9 version after trying the newest and latest. 
I like it better. I use E-Sword more as a search tool, my main study tool is Libronix Logos.

---

### Post by david_kt on 2009-05-07
> **silvagroup said:**
> Does not. You know I am not sure it ever has worked with wine. I have never had a real need to use the graphic viewer so I am not sure if it actually ever has worked.

Some one else may have info on the specifics of graphic viewer.

Actually I usually go back to 7.8.9 version after trying the newest and latest. 
I like it better. I use E-Sword more as a search tool, my main study tool is Libronix Logos.

Using the installer, graphic viewer does always works. But offcourse there is some tweaks to make it works. I just want to know whether or not that tweak is still necessary or not. Now I am sure it is still need some tweak.

I am considering to remove tweaks of msls31.dll and riched20.dll, looks like not necessary anymore.

DK

---

### Post by silvagroup on 2009-05-07
DK thanks for the info. I have just been updating since my original wine install of E-Sword from maybe 5 or 6 years ago.
I have never tried the script, but keep it up because it can be a time saver for the newer user who has to install E-sword and doesn't know about the intricacies and complexity still associated with wine, which is really still beta software.

---

### Post by jonathonblake on 2009-05-07
> **silvagroup said:**
> I use E-Sword more as a search tool, my main study tool is Libronix Logos.

I'm sure that more than a couple of people in Bellingham will be scratching their heads at that one.

jonathon

---

### Post by silvagroup on 2009-05-08
> I'm sure that more than a couple of people in Bellingham will be scratching their heads at that one.

Well they can scratch as hard as they want, they are pretty thick headed so it won't hurt them much.

Two things to note, E-Sword, is dramatically faster in doing bible searches, because of course it has less than a hundred books compared to several hundred books in smaller versions of Logos to several thousand books, as is in my version and countless other resources in Logos.

And the last, is that E-Sword runs in Wine, it running in Linux, to run Logos I have to use a virtual machine, so I can run XP. 
Although it is fairly responsive once I get it started up I also have get Logos loaded and running, then add to that the minor performance loss. By that time I have completed a considerable number of searches with E-Sword.

I can then take those search results done in E-Sword and to do a deeper study and analysis with Logos. If all I need is a quick word search for a verse reference I can do that in several seconds with E-Sword and I don't even bother with Logos.

---

### Post by cycle_mycle on 2009-05-10
Thank you David_kt for this wonderful way to install e-sword. This is the very first time WINE has ever worked for me and I'm so glad.

My Ubuntu is perfect now. God bless you my friend!

By the way I do use Xiphos (formerly gnomesword) it is a very excellent Bible study tool also. Now my computer is able to help me study like it has never before.

P.S. I'm a Christian missionary in the Philippines and I have some friends in Vietnam and throughout S.E. Asia as well. Thank you again!

---

### Post by RPG Master on 2009-05-11
Why use e-Sword when you could use GNOME-Sword?

---

### Post by cycle_mycle on 2009-05-11
RPG Master - I guess the short answer for using both would be for the same reason I use more than one version of the Bible. Just trying to get the most out of my time in the word.

I surely do like gnomesword a lot, but I also like e-sword. Some of the features are the same for instance study notes. I like the fact that I can have my study notes in the same window with e-sword.

I'm glad you brought this up though because; I need help in getting the personal commentary to work in gnomesword, for some reason I've never been able to get it working. I click to edit it, the edit window opens, I make my entries but they are never saved. Do you know what I might be able to do? Maybe there is a setting I'm missing or something? Can you offer any suggestions?

One more thing I like about e-sword is that the daily devotionals open in a separate window so that I can keep it open and do further meditation on them as I study. Usually there's a lasting message there that coincides with a study I'm doing. Not surprisingly due to the way God works. :)

So both of them together make great companion study tools and I'm all the better off being more useful and fruitful in my preparations.

I also like to have them both for the reason that I live in a third-world country and I can use all the help I can get. There are so many resources that I used to take for granted before when I lived in the States and now I can really appreciate the fact that God can do so much with so little, it's truly a big blessing to see God at work in so many ways. Amen!

God bless you brother!

---

### Post by cycle_mycle on 2009-05-11
Opps! I'm ranting about my favorite Bible study tool and I almost forgot why I came here.

I'm trying to get some addons installed and I get this message:

"Esword_installer error: Note: command 'env WINEPREFIX=/home/miguelh/.wine_Esword wine /home/miguelh/Windows Programs/E-Sword/hoekstra.exe' returned status 2.  Aborting."

When I try to install by clicking the .exe file I get a different error message:

"The e-Sword add-on cannot be installed because e-Sword is not currently installed, or the currently installed version is older than version 9.0."

e-Sword version is 9.0.1

I think it has something to do with the fact that it's looking or trying to install in the wrong place. Or also something about copying dll's manually.

I've noticed there are more than one place where files and programs are installed.

---

### Post by david_kt on 2009-05-11
> **cycle_mycle said:**
> Opps! I'm ranting about my favorite Bible study tool and I almost forgot why I came here.

I'm trying to get some addons installed and I get this message:

"Esword_installer error: Note: command 'env WINEPREFIX=/home/miguelh/.wine_Esword wine /home/miguelh/Windows Programs/E-Sword/hoekstra.exe' returned status 2.  Aborting."

When I try to install by clicking the .exe file I get a different error message:

"The e-Sword add-on cannot be installed because e-Sword is not currently installed, or the currently installed version is older than version 9.0."


Did you try to install downloaded addons? Could you give more explanation about this addons such as what is the name and where you downloaded it?

If using the installer, you could not just double click the exe file as it would go to default (wrong) directory. So, please use the installer to install any addons.

DK

---

### Post by cycle_mycle on 2009-05-11
> **david_kt said:**
> Did you try to install downloaded addons? Could you give more explanation about this addons such as what is the name and where you downloaded it?

If using the installer, you could not just double click the exe file as it would go to default (wrong) directory. So, please use the installer to install any addons.

DK

I first tried to install from the e-Sword_installer (I selected manual) and I got the error message:  

Esword_installer error: Note: command 'env WINEPREFIX=/home/miguelh/.wine_Esword wine /home/miguelh/Windows Programs/E-Sword/hoekstra.exe' returned status 2.  Aborting. 

Then I tried to install by clicking the .exe file and got the other error.

Both times they are files hoeskra.exe I downloaded from:

[http://www.e-sword.net/downloads.html](http://www.e-sword.net/downloads.html)

Any file I try to install that is not on the e-Sword_installer menu will give me that error. According to the e-sword.net website they are up to date and will install in the latest e-sword.

I will not try to install by clicking the .exe file anymore. What is the error? ("returned status 2")

Thank you DK for your help.

---

### Post by david_kt on 2009-05-11
> **cycle_mycle said:**
> I first tried to install from the e-Sword_installer (I selected manual) and I got the error message:  

Esword_installer error: Note: command 'env WINEPREFIX=/home/miguelh/.wine_Esword wine /home/miguelh/Windows Programs/E-Sword/hoekstra.exe' returned status 2.  Aborting. 

I tried it on my computer but there is no such error. But not to worry, just re-download the new installer at the first page of this thread, and viola.... there is hoekstra in the installer now !! Hopefully the script works for you.

DK

---

### Post by cycle_mycle on 2009-05-11
Yes! That worked.

I guess then, the question would be; Why isn't there more options to install all or any of the options on the website? [http://www.e-sword.net/downloads.html](http://www.e-sword.net/downloads.html)

Or maybe an option to load only the add-ons we want....

I appreciate what you have done. I also hope you realize the wonderful thing you have created with your software. I wish for you the best of everything in our Lord Jesus Christ. Thank you so much! God bless you richly in all that you put your hand to DK, my brother in the Lord.

I made a special prayer request in my e-sword so I can be praying for you. PM me for anything else I can pray about for you. Thanks again DK.

---

### Post by david_kt on 2009-05-11
> **cycle_mycle said:**
> Yes! That worked.

I guess then, the question would be; Why isn't there more options to install all or any of the options on the website? [http://www.e-sword.net/downloads.html](http://www.e-sword.net/downloads.html)

Or maybe an option to load only the add-ons we want....

The reason is that there are so many things there and not all people here are using it. I have added almost all the bibles available, but other than that I will wait for people that have specific problem/request.

Another good news is that I have figure out why you got an error when using manual option. The problem is my script could not take directory name with space in it. You have "Windows Programs" directory, which has space in between "Windows" and "Programs". And I have edited again the script and now it could take any directory name, including the one with space.

So, you have give me a good feedback so that other people would not face the same issue again as I have corrected a bug in the script based on your feedback.

DK

---

### Post by ahbeng on 2009-05-11
Thank you! Thank you!

Using Jaunty with Wine 1.1.20. Installed flawlessly.

New computer. Was previously using Hardy Heron and wine 1.1.7 which worked well. Been frustrated for a week.

---

### Post by cycle_mycle on 2009-05-11
I was able to finish installing all the add-ons I want by changing the config in WINE to Windows version: Windows Vista.

I guess e-Sword 9.0.1 is a Vista program or Vista enhanced or something.

I will keep using your script and bookmark this thread in case I install other add-ons or meet with any other problems.

But right now I am so happy that I was able to get e-Sword because of your wonderful installer script. Thank you again, God bless you DK my friend!

I'm glad I was of some assistance to you after all the help you have given me.

---

### Post by david_kt on 2009-05-11
For those installed old version using my script, please do not install version 9 first as I found out that the installer fail to convert old format modules and then crash before completing the installation, and cause e-Sword unable to launch anymore.

If you have run the backup script, you could restore it using the restore script.

I will work on the conversion issue and let you know after I have succeeded to solve the problem. 

Another option is to make both version available, which much easier for me I think. Please let me know if you prefer this method.

DK

---

### Post by t_pearce on 2009-05-11
I just tried that again. The restore works fine.

I thought it might have been because I was using EasyPeasy (a Ubuntu derivative for netbooks).

It's great being able to take my Linux EeePC 1000 along to Bible studies. I can instantly compare a verse in multiple versions for comparisons. I haven't mastered the art  of looking up a passage elsewhere and then coming back. I guess a bookmark would help.

Tim

---

### Post by ahbeng on 2009-05-13
I'm using jaunty with wine 1.1.20. e-sword installed just fine with the installer and is running.

Problem is, I am unable to use my usual hotkeys to access the menu. eg I used to be able to use Alt-B to open the "Bible" menu and then press "C" to copy a verse. But now the hotkeys are not underlined, and I simply get a beep when I press the usual buttons.

Is this a problem with wine, and if so, how would I correct it?

Thanks!

---

### Post by t2technology on 2009-05-18
I am using Jaunty with wine 1.1.21.

I didn't have to do anything extra. This was a fresh ubuntu install. Using this script was the first thing I did. Thank you so much. I can't say it enough.

One note: I installed Ubuntu through Wubi (it's a work computer and I can't partition the drive without IT backlash) and I copied all of the modules from the Windows partition to the wine folder and all of the modules worked perfectly. Thanks again.

---

### Post by manney on 2009-05-19
I am using Jaunty with wine 1.17

Does anyone know why, when using the installer, none of the EXTRAS will install?  It says returned status 2 aborting.  However if I use the manual method, eg. env WINEPREFIX=~/.wine_Esword wine creeds.exe  I can install the extras this way.  I was also wondering how do I import my topic notes, study notes, exc from e-sword 7.98

---

### Post by manney on 2009-05-19
I just noticed another issue after installing some of my Extras.  The navigation bar along the left side of the screen is gone.  So now to move to another book or chapter of the bible I have to type it in instead of just being able to click on it.  Does anyone know how to fix this?

---

### Post by jonathonblake on 2009-05-19
> **manney said:**
> 
Does anyone know why, when using the installer, none of the EXTRAS will install?  It says returned status 2 aborting. 
My guess is that the anti-bot scripts on e-Sword.net are kicking in.

> I was also wondering how do I import my topic notes, study notes, exc from e-sword 7.98

If they were in the user directory, they should have automatically updated.
If they weren't, download the conversion tool in e-Sword Extras, and use that.

###
If the option to include that isn't in the install script, then it should be added.  
Something else that might be useful, is if the isntall script copies all content from the program directory, to the user directory, Prior to install the new version of e-Sword.  On second thoughts, do that as a _upgrade from 8.x script_, and not the standard installation script.

jonathon

---

### Post by manney on 2009-05-20
my study notes were in the user directory and they were not updated.  I downloaded and installed the e-sword user module conversion utility but my notes are still not visible in e-sword.

---

### Post by manney on 2009-05-20
I also emailed rick meyers and he told me to

1. Select "Reset e-Sword Settings" from the e-Sword "Help" menu.
 
2. Delete all files from the e-Sword user directory (typically "My
Documents\e-Sword\").
 
3. Copy your old user files into that same directory in step #2.
 
4. Start e-Sword and your old files will get converted for use in the new
version.

this also did not restore my study notes.  Any suggestions?

---

### Post by cmckdub on 2009-05-22
> **david_kt said:**
> For those installed old version using my script, please do not install version 9 first as I found out that the installer fail to convert old format modules and then crash before completing the installation, and cause e-Sword unable to launch anymore.

If you have run the backup script, you could restore it using the restore script.

I will work on the conversion issue and let you know after I have succeeded to solve the problem. 

Another option is to make both version available, which much easier for me I think. Please let me know if you prefer this method.

DK

David, thanks for the warning. 
I am using Wine 1.1.20 and e-sword 8.0.6, originally installed using the script from this thread. 
However I am a little confused about what you are suggesting we do if we want to update e-sword. Is it safe to remove the old e-sword package and then re-install e-sword and packages? Will the back-up feature work? 
I get the impression from the e-sword site that even if I was still using Windows that a re-installation is the only way to upgrade.
I am happy to wait for your continued great efforts with this, if you can somehow make old modules convert, but it seems to be opposite to what is being indicated from e-sword.

---

### Post by david_kt on 2009-05-25
> **cmckdub said:**
> David, thanks for the warning. 
I am using Wine 1.1.20 and e-sword 8.0.6, originally installed using the script from this thread. 
However I am a little confused about what you are suggesting we do if we want to update e-sword. Is it safe to remove the old e-sword package and then re-install e-sword and packages? Will the back-up feature work? 
I get the impression from the e-sword site that even if I was still using Windows that a re-installation is the only way to upgrade.
I am happy to wait for your continued great efforts with this, if you can somehow make old modules convert, but it seems to be opposite to what is being indicated from e-sword.

I am still in holiday and have limited internet access so as  could not reply all mails sooner. What I suggest is:
1. to backup the old installation, or just rename the .esword directory.
2. Delete/rename .wineeswordcache directory so as it would download new module instead of using old module downloaded earlier 


I will refine the installer after I go back home from my holiday.

DK

---

### Post by JDArnott on 2009-06-06
Greetings

No joy. I used WINE 1.0.1 (am trying to upgrade to one higher than the 1.1.20 mentioned in the installation) but on completion got:

Esword_installer error: Note: command 'cp -f /home/justin/.wine_Esword/drive_c/Program Files/e-Sword/riched20.dll /home/justin/.wine_Esword/drive_c/windows/system32' returned status 1, Aborting

e-Sword is in the WINE folder, but it doesn't run. Will keep trying.

Enjoy!

---

### Post by david_kt on 2009-06-06
> **JDArnott said:**
> Greetings

No joy. I used WINE 1.0.1 (am trying to upgrade to one higher than the 1.1.20 mentioned in the installation) but on completion got:

Esword_installer error: Note: command 'cp -f /home/justin/.wine_Esword/drive_c/Program Files/e-Sword/riched20.dll /home/justin/.wine_Esword/drive_c/windows/system32' returned status 1, Aborting

e-Sword is in the WINE folder, but it doesn't run. Will keep trying.

Enjoy!

Wine 1.0.1 install e-Sword on the wrong folder, that is why the dll is not found. If you notice, it install e-Sword on c: folder instead of c:/Program Files/e-Sword folder. Please update you wine and try again.

DK

---

### Post by david_kt on 2009-06-07
I have just updated the installer to use e-Sword 9.0.3 and fixed a bug for people doing upgrading. Now it could upgrade. But the catch is most of the modules will not be converted, means you will loss all your modules and you will need to download new version of modules.

If your modules are available from the installer I make, then it should be easy for you to re-download:

1. Run the installer and choose Clear Cache
2. Run the installer again and then you could select as many option as you want.

If you do not clear cache, it will use old module installer in the cache.

But if some of your modules were from other site or paid modules, please check again if they have provide new version otherwise you will lose your modules. If you could not afford to lose that modules:
[B]
 PLEASE DO NOT UPGRADE eSword.[/B]

For those of you decide to upgrade, please let me know if you face problems, hopefully I could help.

DK

---

### Post by chzumbrunnen on 2009-06-10
Thanks for the description and script.

It didnd't work for me.

I had e-Sword installed before tried to uninstall and install again but in every case had the follwing error:

Esword_installer error: Note: command 'cp -f /home/[username]/.wine_Esword/drive_c/Program Files/e-Sword/riched20.dll /home/[username]/.wine_Esword/drive_c/windows/system32' returned status 1. Aborting.

E-Sword doesn't even start now, although it's in the menue.
So I can't even find out if it's the "old" install or the new one...

Any hints or ideas on how to go on?

---

### Post by david_kt on 2009-06-10
> **chzumbrunnen said:**
> Thanks for the description and script.

It didnd't work for me.

I had e-Sword installed before tried to uninstall and install again but in every case had the follwing error:

Esword_installer error: Note: command 'cp -f /home/[username]/.wine_Esword/drive_c/Program Files/e-Sword/riched20.dll /home/[username]/.wine_Esword/drive_c/windows/system32' returned status 1. Aborting.

E-Sword doesn't even start now, although it's in the menue.
So I can't even find out if it's the "old" install or the new one...

Any hints or ideas on how to go on?

Probably you are using old wine version (1.0.1 ?), please upgrade to wine 1.1.23, and then try again the script.

DK

---

### Post by chzumbrunnen on 2009-06-10
> **david_kt said:**
> Probably you are using old wine version (1.0.1 ?), ...

DK

Actually my wine version is 1.23.

---

### Post by david_kt on 2009-06-10
> **chzumbrunnen said:**
> Actually my wine version is 1.23.

Did you change the installation path? You should leave at default location otherwise the script could not find the riched20.dll.

DK

---

### Post by chzumbrunnen on 2009-06-10
> **david_kt said:**
> Did you change the installation path? You should leave at default location otherwise the script could not find the riched20.dll.

DK

I don't know. Today, I didn't change any path but I find the folders .wine, .wine_Esword, .wineeswordcache, which all have a actual change date. Don't know why.

riched.dll is in dosdevices, c:, windows, system32 in both .wine and .wine_Esword

---

### Post by david_kt on 2009-06-10
> **chzumbrunnen said:**
> I don't know. Today, I didn't change any path but I find the folders .wine, .wine_Esword, .wineeswordcache, which all have a actual change date. Don't know why.

riched.dll is in dosdevices, c:, windows, system32 in both .wine and .wine_Esword

Could you run again the installer, this time use command line to see what is the output there.

I just tried it here using portable ubuntu, it could install e-Sword 903 without any problem.

DK

---

### Post by chzumbrunnen on 2009-06-10
This is what I get in the terminal:

Wine version is ok
Using builtin override for following DLLs: riched20 oleaut32
Executing env WINEPREFIX=/home/chzumbrunnen/.wine_Esword wine regedit /home/chzumbrunnen/.wine_Esword/drive_c/wineeswordtmp/override-dll.reg
Note: wineprefixcreate is deprecated and shouldn't be needed anymore.
      WINEPREFIX creation and updates now happen automatically when needed.

fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x32cf94
0[1a4098]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nspr4.dll") - Symbol NSGetModule not found
0[1a4098]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\softokn3.dll") - Symbol NSGetModule not found
0[1a4098]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nssdbm3.dll") - Symbol NSGetModule not found
0[1a4098]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\freebl3.dll") - Symbol NSGetModule not found
0[1a4098]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\plugins\npnul32.dll") - Symbol NSGetModule not found
0[1a4098]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nssutil3.dll") - Symbol NSGetModule not found
0[1a4098]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nss3.dll") - Symbol NSGetModule not found
0[1a4098]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\plc4.dll") - Symbol NSGetModule not found
0[1a4098]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\xpcom.dll") - Symbol NSGetModule not found
fixme:iphlpapi:NotifyAddrChange (Handle 0x3f9e888, overlapped 0x3f9e890): stub
0[1a4098]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\smime3.dll") - Symbol NSGetModule not found
0[1a4098]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nssckbi.dll") - Symbol NSGetModule not found
0[1a4098]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\sqlite3.dll") - Symbol NSGetModule not found
0[1a4098]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\plds4.dll") - Symbol NSGetModule not found
0[1a4098]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\ssl3.dll") - Symbol NSGetModule not found
0[1a4098]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\xul.dll") - Symbol NSGetModule not found
0[1a4098]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\js3250.dll") - Symbol NSGetModule not found
fixme:shell:DllCanUnloadNow stub
wine: configuration in '/home/chzumbrunnen/.wine_Esword' has been updated.
Executing env WINEPREFIX=/home/chzumbrunnen/.wine_Esword wine /home/chzumbrunnen/.wineeswordcache/setup903.exe
fixme:advapi:LookupAccountNameW (null) L"chzumbrunnen" (nil) 0x32ec20 (nil) 0x32ec24 0x32ec18 - stub
fixme:advapi:LookupAccountNameW (null) L"chzumbrunnen" 0x139de8 0x32ec20 0x13ac60 0x32ec24 0x32ec18 - stub
fixme:advapi:LookupAccountNameW (null) L"chzumbrunnen" (nil) 0x33f80c (nil) 0x33f810 0x33f804 - stub
fixme:advapi:LookupAccountNameW (null) L"chzumbrunnen" 0x137438 0x33f80c 0x1382b0 0x33f810 0x33f804 - stub
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 1 ignored L"Upgrade" table values
fixme:msi:ControlEvent_HandleControlEvent unhandled control event L"Reinstall" arg(L"ALL")
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 1 ignored L"Upgrade" table values
fixme:msi:msi_unimplemented_action_stub RemoveExistingProducts -> 1 ignored L"Upgrade" table values
fixme:msi:msi_unimplemented_action_stub UnregisterFonts -> 5 ignored L"Font" table values
fixme:msi:msi_unimplemented_action_stub UnregisterProgIdInfo -> 88 ignored L"ProgId" table values
fixme:msi:msi_unimplemented_action_stub RemoveShortcuts -> 2 ignored L"Shortcut" table values
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 7 ignored L"CreateFolder" table values
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:mscoree:LoadLibraryShim (0x7ee23a8c L"fusion.dll", (nil), (nil), 0x33f934): semi-stub
fixme:shell:DllCanUnloadNow stub
Executing cp -f /home/chzumbrunnen/.wine_Esword/drive_c/Program Files/e-Sword/riched20.dll /home/chzumbrunnen/.wine_Esword/drive_c/windows/system32
cp: Aufruf von stat für „/home/chzumbrunnen/.wine_Esword/drive_c/Program Files/e-Sword/riched20.dll“ nicht möglich: No such file or directory
Note: command 'cp -f /home/chzumbrunnen/.wine_Esword/drive_c/Program Files/e-Sword/riched20.dll /home/chzumbrunnen/.wine_Esword/drive_c/windows/system32' returned status 1.  Aborting.
^A

---

### Post by david_kt on 2009-06-10
Could you see where the e-Sword is installed? Suppose it is on:

/home/chzumbrunnen/.wine_Esword/drive_c/Program Files/e-Sword/

Could you navigate to that directory and see whether or not riched20.dll is there?

DK

---

### Post by chzumbrunnen on 2009-06-10
it's on drive_c/**Programme**/e-Sword/ as in a German install.

---

### Post by david_kt on 2009-06-10
Could you run the installer and choose:

"remove_esword         To remove e-Sword installed using this installer"

After that, run again the installer and install the main program. I hope you have done your backup before running the new script. Otherwise, copy all your module first before removing e-Sword.

DK

---

### Post by david_kt on 2009-06-10
> **chzumbrunnen said:**
> it's on drive_c/**Programme**/e-Sword/ as in a German install.

Really, I guess I have to edit the script in that case. Wait a moment.

DK

---

### Post by david_kt on 2009-06-10
Download and try attached installer and let me know if there is any other error.

DK

---

### Post by chzumbrunnen on 2009-06-10
F A N T A S T I C !

This time it worked although the first time the installer asked for additional modules to install and when I had nothing to choose the installer stopped completely.
The second time the installer was in .wineswordcache folder where I chose the setup903.exe... maybe a little recursive or so.... but it worked!

Thank you so much for your effort in helping me. I appreciate it.

---

### Post by david_kt on 2009-06-10
> **chzumbrunnen said:**
> F A N T A S T I C !

This time it worked although the first time the installer asked for additional modules to install and when I had nothing to choose the installer stopped completely.
The second time the installer was in .wineswordcache folder where I chose the setup903.exe... maybe a little recursive or so.... but it worked!

Thank you so much for your effort in helping me. I appreciate it.

I am not really sure what happened when you said "the installer asked for additional modules".

Anyhow, do you able to launch e-Sword now? If it is ok, I will think of a way to make the installer more general i.e to find the location of riched20.dll first before trying to copy it.

DK

---

### Post by jshane on 2009-06-11
The script worked fine with my Xubuntu Intrepid 8.10 and Wine 1.1.8 on an IBM ThinkPad T23. I now have e-Sword 9.03 working.

Thanks for a helpful tool. John

---

### Post by JDArnott on 2009-06-12
> **JDArnott said:**
> Greetings

No joy. I used WINE 1.0.1 (am trying to upgrade to one higher than the 1.1.20 mentioned in the installation) but on completion got:

Esword_installer error: Note: command 'cp -f /home/justin/.wine_Esword/drive_c/Program Files/e-Sword/riched20.dll /home/justin/.wine_Esword/drive_c/windows/system32' returned status 1, Aborting

e-Sword is in the WINE folder, but it doesn't run. Will keep trying.

Enjoy!

Great joy! After WINE upgrade ran e-Sword_installer_070609 and all installed smoothly and running fine as far as I can tell. 

I voted "*No, it runs perfectly" *in the poll.

Thankyou

---

### Post by joyson20 on 2009-06-15
I used wine 1.1.23.....The installer did the work perfectly in jaunty and now i have e-sword running...thanks for your kind help..Praise God

---

### Post by manola on 2009-06-16
The installer did the work perfectly in jaunty and now i have e-sword running
[[color=#FFFFFF]_sonnerie portable gratuite_[/color]](http://sonneriegratuite.org)

---

### Post by majagray on 2009-06-28
> **david_kt said:**
> Are sure it is msis31.dll? I thought it is supposed to be msls31.dll. Could you let me know in which step throw that error (copy and paste your terminal output if you could, including the command issued).

Make sure  you have downloaded msls31.dll from:

[http://www.dlldump.com/cgi-bin/testwrap/downloadcounts.cgi?rt=count&path=dllfiles/M/msls31.dll](http://www.dlldump.com/cgi-bin/testwrap/downloadcounts.cgi?rt=count&path=dllfiles/M/msls31.dll) 

And copy it to ~/.wine_Esword /drive_c/windows/system32 

If you downloaded it in your home directory, open terminal and copy and paste below command:

```
cp msls31.dll ~/.wine_Esword /drive_c/windows/system32 
```If you downloaded it on your Desktop, then you should go to Desktop first before issuing above command (cd Desktop).

After that rerun the command that give you error. Make sure other dlls are also copied to ~/.wine_Esword /drive_c/windows/system32 

Please let me know if you still have problem.

DK


I had the same problem with my e-Sword set up - thanks heaps DK for your help!

Maranatha.

---

### Post by ChrisNZ on 2009-06-29
Hi All

I too was stumped after updating from 8.04 to 9.04...? Jaunty.

So the same old search on the net and very Quickly came back to the forums here to find this excellent thread. Thanks for the help in a very easy to follow manner.

cheers from NZ

---

### Post by silvagroup on 2009-06-29
It is msls31.dll

---

### Post by davidtrounce on 2009-07-02
great installer. flawless set up. Can anyone tell me how i can import my study notes and topic notes from version 8 now that I am using 9.03?

---

### Post by ChrisNZ on 2009-07-04
> **davidtrounce said:**
> 
Can anyone tell me how i can import my study notes and topic notes from version 8 ...

Yes I too have notices this, it looks like the programmers have changes from Jet databased bbls to Sql lite database and notes have also changed extensions - I'm still looking for a fix so will tag this thread. Have you tried another forums on Ubuntu and results?

Cheers - Chris

---

### Post by david_kt on 2009-07-04
> **ChrisNZ said:**
> Yes I too have notices this, it looks like the programmers have changes from Jet databased bbls to Sql lite database and notes have also changed extensions - I'm still looking for a fix so will tag this thread. Have you tried another forums on Ubuntu and results?

Cheers - Chris

Even in windows there are many problems in converting to new database. So, it is better to re-download the whole things.

DK

---

### Post by Nathanael Culver on 2009-07-12
Reporting that I was able to install e-Sword under Wine 1.1.25; so far it seems to run flawlessly.

However, the install was not flawless. Installing under 64-bit Jaunty, the first several times I attempted to run the install script I just received an error. Sorry, I neglected to jot it down, and I can't reproduce it now, but something about an invalid window, and then a message containing the words "Program Files".

After messing around manually installing and configuring the DLLs, when I attempted the script again it ran fine, and has done so since. I've used it to install a dozen or more manually-downloaded add-ons.

Just two nits at present:

1) It's a bit annoying to have to respond to both the "unknown Wine version" and the subsequent "please report your success" windows every time I run the script. It'd be nice if there were a way to disable them, or at the least combine them into a single window.

2) How about the ability to specify multiple add-on modules at once? I've got a couple of dozen already-downloaded modules I'd like to install, and it's a bit cumbersome to have to re-run the script for each.

NathanaelCulver

---

### Post by david_kt on 2009-07-12
> **Nathanael Culver said:**
> 
Just two nits at present:

1) It's a bit annoying to have to respond to both the "unknown Wine version" and the subsequent "please report your success" windows every time I run the script. It'd be nice if there were a way to disable them, or at the least combine them into a single window.

2) How about the ability to specify multiple add-on modules at once? I've got a couple of dozen already-downloaded modules I'd like to install, and it's a bit cumbersome to have to re-run the script for each.

NathanaelCulver

1. Actually I have made a deb package that I did not post here as the script here is meant for general use, not only for debian/ubuntu. With this deb package, you will not see unknown wine version anymore. You could download it from here:

[http://thuygiang.homelinux.com/Ubuntu_CE/binary/e-sword-installer_1.2_all.deb](http://thuygiang.homelinux.com/Ubuntu_CE/binary/e-sword-installer_1.2_all.deb)

Once install, you could launch the script located at:
 application >> System tools >> e-sword-installer

2. I will think of a way to loop the installation of downloaded addons so as not to launch the script again and again. Thank you for your feedback.

DK

---

### Post by twal34 on 2009-07-13
David,
 
Thank God for your efforts and your install tool. I was able to successfully install e-Sword 9.03 on Ubuntu 9.04. I had to upgrade to the latest Wine (1.1.25) ([http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) ). I did get some errors using your install package but it successfully installed the base e-Sword. It failed to add the remaining modules. (ie: ESV, etc.) Unfortuantely, being new to Ubuntu I only figured out how to take screenshots after the fact so I don't have the error messages but they seemed to be more related to Wine dll's not being found. It is also possible that I missed a step somewhere. Anyway, I copied those modules manually to the .wine_Esword/drive_c/Program Files/e-Sword folder in my home folder. (Showing hidden files of course.) I was also able to copy fonts over manually for customized modules. I have my Windows e-Sword totally migrated over to Linux now and I am delighted about it. Because of this I feel much better about switching to Linux. I'll certainly be doing it at home.
 
BTW: I think I used one of your earlier tool versions because I noticed the one you posted here is a later version.

---

### Post by david_kt on 2009-07-13
> **twal34 said:**
> 
BTW: I think I used one of your earlier tool versions because I noticed the one you posted here is a later version.

If you are using ubuntu, please use the latest version of deb package:

[http://ubuntuce.com/repos/Ubuntu_CE/binary/e-sword-installer_1.2_all.deb](http://ubuntuce.com/repos/Ubuntu_CE/binary/e-sword-installer_1.2_all.deb)

Or you could add 

deb [http://ubuntuce.com/repos/Ubuntu_CE/](http://ubuntuce.com/repos/Ubuntu_CE/) binary/

to your repository (/etc/apt/source.list)

and then:

sudo apt-get update
sudo apt-get install e-sword-installer

Whenever I post now version of installer, it would be updated automatically to your computer.

The installer could be found at Applications >> system tools >> e-sword-installer

DK

---

### Post by McBatman on 2009-07-14
Hey Guys, I am complete noob to Ubnutu. I am trying to install Esword and your first post helped alot. However, when I try to run the program the desktop loads and then exits immediently again. I am using Ubuntu 9.04 and the latest version of Esword. Any help would be greatly appreciated thanks :)

---

### Post by david_kt on 2009-07-14
> **McBatman said:**
> Hey Guys, I am complete noob to Ubnutu. I am trying to install Esword and your first post helped alot. However, when I try to run the program the desktop loads and then exits immediently again. I am using Ubuntu 9.04 and the latest version of Esword. Any help would be greatly appreciated thanks :)

Could you try to use deb package below:

[http://ubuntuce.com/repos/Ubuntu_CE/binary/e-sword-installer_1.2_all.deb](http://ubuntuce.com/repos/Ubuntu_CE/binary/e-sword-installer_1.2_all.deb)

And re-install e-Sword.

If it is still could not launch e-Sword, choose "clear cache" and re-install e-Sword.

DK

---

### Post by shammond on 2009-08-12
Worked great with Ubuntu 9.04 and Wine 1.1.27!  Just wish there was an easier way to install multiple addons (that aren't on the list).  But the BACKUP/RESTORE feature is a great idea.  Too bad I didn't discover this forum message before wiping my partition clean to perform an upgrade. :-(

---

### Post by david_kt on 2009-08-13
> **shammond said:**
> Just wish there was an easier way to install multiple addons (that aren't on the list).

Please download the installer again, now I have made manual selection to install multiple addons.

DK

---

### Post by SmittyMeista on 2009-08-13
I have e-sword on a CD that someone gave me a few years ago. I used to use it, and the thought occurred to me to try it under Wine. But I don't really use it anymore anyway because frankly, the Bible study tools available at crosswalk.com are very good, so I pretty much just use those. No need to take up the HD space with a big app.

---

### Post by ubume2 on 2009-08-15
Update: I completely removed all wine files and all e-sword files and followed the instructions EXACTLY on this thread.  Installed flawlessly.  I also use the e-sword installer script and reinstalled other windows apps through it, and they work better than ever.
Thanks

Hi, I am trying to install e-Sword on a second computer. I use Ubuntu 8.04 LTS and have successfully installed it on another computer.  I have tried Jaunty and Ubuntu CE Jaunty with no luck. wine 1.1.27 appears to be installed.I am trying to install e-Sword 9.03. Under /home/usr/ i have a directory .wine and one .wine_E-Sword.  

I have installed riched20 and msls31 and the mfc dll using winetricks.
When I try to start e-Sword either from the terminal or the e-Sword shortcut on Desktop I get a Program error dialog box indicating that e_Sword has encountered a serious problem.

Any help would be appreciated.  Note: I have also tried to install e-Sword 798. I can get the basic module to run, but other bibles or commentaries will not install.

Thanks
Jerry

---

### Post by Jerriy on 2009-08-22
> **david_kt said:**
> Please let me know if this instruction does not work for you.

DKIt doesn't work for me at the following step in your instruction that is on the very first post of this thread:```
env WINEPREFIX=~/.wine_Esword wine "C:\Program Files\e-Sword\e-Sword.exe"
```I've also tried variants of that command (specifying the "home" directory, and writing the the "C:\..." address in linux style etc), but to no avail. It failed to deliver the result:```
fixme:ole:OleLoadPictureEx (0xf8a9dc,18910,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9d0), partially implemented.
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
err:dc:CreateDCW no driver found for L""
fixme:ole:OleLoadPictureEx (0xf8f85c,3334,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f150), partially implemented.
fixme:richedit:ME_HandleMessage WM_STYLECHANGING: stub
fixme:richedit:ME_HandleMessage WM_STYLECHANGED: stub
fixme:richedit:ME_HandleMessage WM_STYLECHANGING: stub
fixme:richedit:ME_HandleMessage WM_STYLECHANGED: stub
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:richedit:ME_HandleMessage WM_STYLECHANGING: stub
fixme:richedit:ME_HandleMessage WM_STYLECHANGED: stub
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\Codejock.Controls.v13.0.0.ocx"
err:ole:CoGetClassObject no class object {7fe78b17-88b4-42e0-b47e-5d7feca6b0e6} could be created for context 0x3
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.swprintf_s, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
wine: Call from 0x7bc48af0 to unimplemented function msvcrt.dll.__CxxFrameHandler3, aborting
err:seh:setup_exception_record stack overflow 2008 bytes in thread 0009 eip b7d0a853 esp 00230b58 stack 0x230000-0x231000-0x330000


```

---

### Post by david_kt on 2009-08-23
> **Jerriy said:**
> It doesn't work for me at the following step in your instruction that is on the very first post of this thread:[CODE]env WINEPREFIX=~/.wine_Esword wine "C:\Program Files\e-Sword\e-Sword.exe"

Could you try the installer instead of alternative installation?

DK

---

### Post by Jerriy on 2009-08-23
The installer gives me this baffling response that there is a file missing in a particular place while I am looking at this very file with my own naked eye!(riched20.dll)```
Executing cp -f /home/mypc/.wine_Esword/drive_c/Program Files/e-Sword/riched20.dll /home/mypc/.wine_Esword/drive_c/windows/system32
cp: cannot stat `/home/mypc/.wine_Esword/drive_c/Program Files/e-Sword/riched20.dll': No such file or directory
Note: command 'cp -f /home/mypc/.wine_Esword/drive_c/Program Files/e-Sword/riched20.dll /home/mypc/.wine_Esword/drive_c/windows/system32' returned status 1.  Aborting.

```

---

### Post by Jerriy on 2009-08-23
By the way the installer gives me only three options and none of them are for installing (the response I posted in my previous post came after I chose the repair option):

---

### Post by david_kt on 2009-08-23
> **Jerriy said:**
> The installer gives me this baffling response that there is a file missing in a particular place while I am looking at this very file with my own naked eye!(riched20.dll)

What language is your operating system? Last time there is one similar feedback, that is because he is using German. What is the output of:

```
ls /home/mypc/.wine_Esword/drive_c/
ls '/home/mypc/.wine_Esword/drive_c/Program Files/'
```

DK

---

### Post by Jerriy on 2009-08-23
And by the way pressing the allegedly installed esword that I saw popup inside my wine programs menu produces... nothing - not even an electronic version of a puff of smoke

And the previously mentioned "modify" option gives me this white blank empty thing with no options:

---

### Post by Jerriy on 2009-08-23
> **david_kt said:**
> What language is your operating system? Last time there is one similar feedback, that is because he is using German. What is the output of:

```
ls /home/mypc/.wine_Esword/drive_c/
ls '/home/mypc/.wine_Esword/drive_c/Program Files/'
```

DKMy OS's language is (I believe) English

ls /home/mypc/.wine_Esword/drive_c/ resulted in:```

Program Files  users  windows  wineeswordtmp
```And ls '/home/mypc/.wine_Esword/drive_c/Program Files/' resulted in:
```
Common Files  e-sword  Internet Explorer

```

---

### Post by lukeelliot on 2009-08-23
**[COLOR="Blue"]*I don't know what made the difference, but since posting what I wrote below e-sword suddenly started working.*[/COLOR]**

I have successfully installed e-sword a number of times in the past by using the instructions in this thread.  However, this time around I keep getting this message when I try to launch e-sword (I am using Kubuntu 8.04):

> fixme:storage:StgCreateDocfile Storage share mode not implemented.
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\system32\\tx4ole14.ocx") not found
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\tx4ole14.ocx"
err:ole:CoGetClassObject no class object {15a32f01-b939-11dc-af58-0013d350667c} could be created for context 0x3
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\system32\\tx4ole14.ocx") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\system32\\tx4ole14.ocx") not found
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\tx4ole14.ocx"
err:ole:CoGetClassObject no class object {15a32f01-b939-11dc-af58-0013d350667c} could be created for context 0x3

---

### Post by david_kt on 2009-08-24
> **Jerriy said:**
> My OS's language is (I believe) English

ls /home/mypc/.wine_Esword/drive_c/ resulted in:```

Program Files  users  windows  wineeswordtmp
```And ls '/home/mypc/.wine_Esword/drive_c/Program Files/' resulted in:
```
Common Files  e-sword  Internet Explorer

```

Could you once again try the installer, preferably after system reboot. First, choose remove e-Sword installed using this installer, and then install e-Sword.

DK

---

### Post by kneewax on 2009-08-25
Hi folks,

I just had a to re-install Ubuntu and as part of the process upgraded to version 9 of e-sword using David's fabulous script.

BUT I have to say I really hate the new version of the software - none of my modules work (I know other found this) including versions I bought. The strange 'script' (for alt+1 etc) icons are a mess and the loss of the scripture navigation tool (I got it back once, but now it's gone again) is a real loss.  Added to that it keeps locking up and freezig on my x64 machine.

This is not the script or David's fault, I am really grateful forr all the help David has given me getting revious versions working - and the script is just fantastic.  Does anyone have a copy of version 8 setup.exe they could mail me as it's no longer available on Rick's site?  I think I'll do a manual install of that rather than struggle with this.  Not sure what it's like under windows but if it's as bad as it is under Wine then I fear Rick may have made a mistake with this latest version.....

---

### Post by jonathonblake on 2009-08-28
I'm using the stock Ubuntu  9.04 (64 bit) Live CD.

Results from running e-sword installer

```

ubuntu@ubuntu:~$ cd /media/My Book/e-sword/new_stuff
bash: cd: /media/My: No such file or directory
ubuntu@ubuntu:~$ cd "/media/My Book/e-sword/new_stuff"
ubuntu@ubuntu:/media/My Book/e-sword/new_stuff$ ls *.sh
ls: cannot access *.sh: No such file or directory
ubuntu@ubuntu:/media/My Book/e-sword/new_stuff$ sh e-sword-installer
Using builtin override for following DLLs: riched20 oleaut32
Executing env WINEPREFIX=/home/ubuntu/.wine_Esword wine regedit /home/ubuntu/.wine_Esword/drive_c/wineeswordtmp/override-dll.reg
fixme:system:SetProcessDPIAware stub!
fixme:iphlpapi:NotifyAddrChange (Handle 0x7ce7b9e8, overlapped 0x7ce7b9cc): stub
fixme:shell:DllCanUnloadNow stub
wine: configuration in '/home/ubuntu/.wine_Esword' has been updated.
Note: wineprefixcreate is deprecated and shouldn't be needed anymore.
      WINEPREFIX creation and updates now happen automatically when needed.

fixme:iphlpapi:NotifyAddrChange (Handle 0x7d2b49e8, overlapped 0x7d2b49cc): stub
fixme:shell:DllCanUnloadNow stub
wine: configuration in '/home/ubuntu/.wine_Esword' has been updated.
Executing env WINEPREFIX=/home/ubuntu/.wine_Esword wine /home/ubuntu/.wineeswordcache/setup903.exe
fixme:advapi:LookupAccountNameW (null) L"ubuntu" (nil) 0x33f87c (nil) 0x33f880 0x33f874 - stub
fixme:advapi:LookupAccountNameW (null) L"ubuntu" 0x12f940 0x33f87c 0x131ea0 0x33f880 0x33f874 - stub
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 1 ignored L"Upgrade" table values
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 1 ignored L"Upgrade" table values
fixme:msi:msi_unimplemented_action_stub RemoveExistingProducts -> 1 ignored L"Upgrade" table values
fixme:msi:msi_unimplemented_action_stub UnregisterFonts -> 5 ignored L"Font" table values
fixme:msi:msi_unimplemented_action_stub UnregisterProgIdInfo -> 88 ignored L"ProgId" table values
fixme:msi:msi_unimplemented_action_stub RemoveShortcuts -> 2 ignored L"Shortcut" table values
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 7 ignored L"CreateFolder" table values
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"ScheduleReboot"
Executing cp -f /home/ubuntu/.wine_Esword/drive_c/Program Files/e-Sword/riched20.dll /home/ubuntu/.wine_Esword/drive_c/windows/system32
cp: cannot stat `/home/ubuntu/.wine_Esword/drive_c/Program Files/e-Sword/riched20.dll': No such file or directory
Note: command 'cp -f /home/ubuntu/.wine_Esword/drive_c/Program Files/e-Sword/riched20.dll /home/ubuntu/.wine_Esword/drive_c/windows/system32' returned status 1.  Aborting.

```

e-Sword appears to install, but I can't find the directory that it installs to.  :(

Thinking  that maybe the "My Book"  was responsible, I tried again at  /home/ubuntu/Desktop.

```

ubuntu@ubuntu:~/Desktop$ e-sword-installer
bash: e-sword-installer: command not found
ubuntu@ubuntu:~/Desktop$ ls
e-Sword.desktop  e-sword-installer  e-Sword.lnk
ubuntu@ubuntu:~/Desktop$ sh e-sword-installer
Using builtin override for following DLLs: riched20 oleaut32
Executing env WINEPREFIX=/home/ubuntu/.wine_Esword wine regedit /home/ubuntu/.wine_Esword/drive_c/wineeswordtmp/override-dll.reg
Note: wineprefixcreate is deprecated and shouldn't be needed anymore.
      WINEPREFIX creation and updates now happen automatically when needed.

fixme:iphlpapi:NotifyAddrChange (Handle 0x7d1579e8, overlapped 0x7d1579cc): stub
fixme:shell:DllCanUnloadNow stub
wine: configuration in '/home/ubuntu/.wine_Esword' has been updated.
Executing env WINEPREFIX=/home/ubuntu/.wine_Esword wine /home/ubuntu/.wineeswordcache/setup903.exe
fixme:advapi:LookupAccountNameW (null) L"ubuntu" (nil) 0x33f87c (nil) 0x33f880 0x33f874 - stub
fixme:advapi:LookupAccountNameW (null) L"ubuntu" 0x12fac0 0x33f87c 0x132020 0x33f880 0x33f874 - stub
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 1 ignored L"Upgrade" table values
fixme:msi:ControlEvent_HandleControlEvent unhandled control event L"Reinstall" arg(L"ALL")
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 1 ignored L"Upgrade" table values
fixme:msi:msi_unimplemented_action_stub RemoveExistingProducts -> 1 ignored L"Upgrade" table values
fixme:msi:msi_unimplemented_action_stub UnregisterFonts -> 5 ignored L"Font" table values
fixme:msi:msi_unimplemented_action_stub UnregisterProgIdInfo -> 88 ignored L"ProgId" table values
fixme:msi:msi_unimplemented_action_stub RemoveShortcuts -> 2 ignored L"Shortcut" table values
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 7 ignored L"CreateFolder" table values
Executing cp -f /home/ubuntu/.wine_Esword/drive_c/Program Files/e-Sword/riched20.dll /home/ubuntu/.wine_Esword/drive_c/windows/system32
cp: cannot stat `/home/ubuntu/.wine_Esword/drive_c/Program Files/e-Sword/riched20.dll': No such file or directory

```

Displayed error message in both instances:
Note: command 'cp -f /home/ubuntu/.wine_Esword/drive_c/Program Files/e-Sword/riched20.dll /home/ubuntu/.wine_Esword/drive_c/windows/system32' returned status 1.  Aborting.


jonathon

---

### Post by david_kt on 2009-08-28
> **jonathonblake said:**
> 
Note: command 'cp -f /home/ubuntu/.wine_Esword/drive_c/Program Files/e-Sword/riched20.dll /home/ubuntu/.wine_Esword/drive_c/windows/system32' returned status 1.  Aborting.


You are the second person informing this problem. But I could not find the reason it fail so far.

Previously there is one person report this issue on German version of wine/ubuntu, and I make a separate installer for him.

Could you try below installer (without copying riched20), and see how it goes.

DK

---

### Post by Jerriy on 2009-08-29
David, regarding the language issue, you are talking about Ubuntu's language, right? Or you by any chance be talking about the language of another OS which is also installed on my PC, namely Microsoft Windows Vista in a separate partition, from where, by the way, I sneaked in (inside C:\windows\system32 i think) and borrowed from there three ".dll" files that were identical in name to the ones required by E-sword, hoping that replacing them might solve the problem but alas, it didn't, as far as I can tell)

> **david_kt said:**
> ...First, choose remove e-Sword installed using this installer, and then install e-Sword.

DKJust hit the uninstall button but that doesn't seem to be solving the issue either (I still see the programes in my file browser so I dunno what, if anything, actually got uninstalled. 

Anyway I hit the install button again and here's what happened: this time that annoying "bla bla bla... Aborting." error message+pop-up did NOT apperar. So I thought cool (by the way what I tried was the "repair" option) but then I had no luck: nothing appeared on my screen - no window was opened. 

One more thing: could this be perhaps a specifically Wine problem? FYI I never used Wine before (I got Vista so normally I use that if windows is needed) so maybe it can be determined that Wine is doing ok (or not ok) by installing something-else in Wine and seeing what happenes then? You have any test suggestions?

Edit: The installer I tried this time was that latest installer you got there in your last post.

---

### Post by jonathonblake on 2009-08-29
> **david_kt said:**
> You are the second person informing this problem. But I could not find the reason it fail so far.

If a live disk user can select a default language, then I selected _English (South Africa)_.  Next time I reboot, I'll pay attention to what I actually do.

> Could you try below installer (without copying riched20), and see how it goes.

That installed it correctly.

I ran out of space on the virtual drive,  so I can't see how well resources install. Solvable, by dumping e-Sword 9.x resources on an external drive. (One of the problems with using live disks.)

jonathon

---

### Post by jonathonblake on 2009-08-29
> **Jerriy said:**
> David, regarding the language issue, you are talking about Ubuntu's language, right?

Default language for Ubuntu.(French, German, English, etc.  Not programming language  --- for anybody who might be confused.)

FWIW, there  are  a couple of user created e-Sword resources, that expect "C:\Program Files\e-Sword", because the packager that is used doesn't know that other languages exist. OTOH, there is an e-Sword utility program that expects to see "C:\Programme".  

jonathon

---

### Post by david_kt on 2009-08-30
> **Jerriy said:**
> David, regarding the language issue, you are talking about Ubuntu's language, right? Or you by any chance be talking about the language of another OS which is also installed on my PC, namely Microsoft Windows Vista in a separate partition, from where, by the way, I sneaked in (inside C:\windows\system32 i think) and borrowed from there three ".dll" files that were identical in name to the ones required by E-sword, hoping that replacing them might solve the problem but alas, it didn't, as far as I can tell)

Windows Vista's dll would not be compatible with the installer. In wine, you have to choose the windows version (98, XP, vista etc) and then if needed you should copy the correct version of dll.

> **Jerriy said:**
> 
Just hit the uninstall button but that doesn't seem to be solving the issue either (I still see the programes in my file browser so I dunno what, if anything, actually got uninstalled. 

Anyway I hit the install button again and here's what happened: this time that annoying "bla bla bla... Aborting." error message+pop-up did NOT apperar. So I thought cool (by the way what I tried was the "repair" option) but then I had no luck: nothing appeared on my screen - no window was opened. 

One more thing: could this be perhaps a specifically Wine problem? FYI I never used Wine before (I got Vista so normally I use that if windows is needed) so maybe it can be determined that Wine is doing ok (or not ok) by installing something-else in Wine and seeing what happenes then? You have any test suggestions?

Edit: The installer I tried this time was that latest installer you got there in your last post.

Where do you see the programes? Could you try again to uninstall using the installer, and see whether or not the programes is still there. Remember to reload/refresh nautilus after uninstalling.

DK

---

### Post by david_kt on 2009-08-30
> **jonathonblake said:**
> 
That installed it correctly.
jonathon

I will check whether or not wine could find the dll in the program folder instead of system32 folder. If that is the case, I will remove copying of riched20.dll into system32 folder.

DK

---

### Post by Jerriy on 2009-08-30
> **david_kt said:**
> Windows Vista's dll would not be compatible with the installer. In wine, you have to choose the windows version (98, XP, vista etc) and then if needed you should copy the correct version of dll.



Where do you see the programes? Could you try again to uninstall using the installer, and see whether or not the programes is still there. Remember to reload/refresh nautilus after uninstalling.

DKI see a file (with stuff in it) called ".wine_Esword" even after uninstalling.
I'll delete that too and try to install again and see what happenes then...

---

### Post by Jerriy on 2009-08-30
Finally it's done!

And look what it says: 'All done, no errors."

Thank you so much for your effort!

---

### Post by staffie on 2009-08-31
hey, so my e-sword in working on my Mint box, 32 bit and 64 bit, so what about Slackware, will it be posible?

---

### Post by david_kt on 2009-08-31
> **staffie said:**
> hey, so my e-sword in working on my Mint box, 32 bit and 64 bit, so what about Slackware, will it be posible?

Sure it is possible. Please try and feedback if there is a problem.

DK

---

### Post by staffie on 2009-08-31
:popcorn:tonight i will try then , will come back to say what happens

---

### Post by jonathonblake on 2009-08-31
> **staffie said:**
> so what about Slackware, will it be posible?

It should work.  About eighteen months ago I used an unmodified version of the script to install e-Sword on BSD.

jonathon

---

### Post by Eladon on 2009-09-09
Does anyone know how to do a search using wildcard characters?  The docs say you can use *, ?, #, etc, as wildcard characters in search expressions, but it doesn't work for me.  I can search for "love", or "loved", but if I search for "love*" it just gives me an empty list.

I do understand how Partial match works, but I want to do more complex searches, like "she love*" to include specifically the word "she" and any word starting with "love".  If I use Partial match, I'll get a gazillion hits on she* that I'm just not interested in.

---

### Post by david_kt on 2009-09-11
Updated to new e-Sword: 9.5.1. Please re-download the installer at the first post.

For people using ubuntu ce, you just need to wait for a while, I will update the repository and what you need to do is sudo apt-get update && sudo apt-get upgrade.

DK

---

### Post by kneewax on 2009-09-12
hey folks,

I upgraded to e-sword 9.x d I just can't get on with it - added to that I actually have too many modules to update 1-by-1 - not to mention having long ago lost my receipts for bought modules! 

Anyway I have a backup of my modules but not the 8.x installer - just wondered if anyone had a copy lying around I could get a copy?

Many Thanks

---

### Post by jonathonblake on 2009-09-12
> **kneewax said:**
> 
 added to that I actually have too many modules to update 1-by-1 
Most of the user-created resources that can be legally redistributed,  are available for e-Sword 9.x, from e-Sword-users.org.


>  not to mention having long ago lost my receipts for bought modules! 
If you log into eStudysource.com, there is a section that enables you  to download the resources you have purchased from them.

>  but not the 8.x installer - just wondered if anyone had a copy lying around I could get a copy?

You can install e-Sword 8.x, using the 9.x installer, by selecting the "manual installation" option.  

jonathon

---

### Post by david_kt on 2009-09-12
> **kneewax said:**
> 
Anyway I have a backup of my modules but not the 8.x installer - just wondered if anyone had a copy lying around I could get a copy?

Many Thanks

Do you need the linux installer script or the e-Sword setup.exe file?

DK

---

### Post by MikeYoung on 2009-09-13
wow you are so awesome. I love the ubuntu but was so frustrated could not get E-sword working. Thanks to you it is installed and working thanks a million. God Bless.

---

### Post by Pepe Lebuntu on 2009-09-13
> **JDArnott said:**
> Greetings

No joy. I used WINE 1.0.1 (am trying to upgrade to one higher than the 1.1.20 mentioned in the installation) but on completion got:

Esword_installer error: Note: command 'cp -f /home/justin/.wine_Esword/drive_c/Program Files/e-Sword/riched20.dll /home/justin/.wine_Esword/drive_c/windows/system32' returned status 1, Aborting

e-Sword is in the WINE folder, but it doesn't run. Will keep trying.

Enjoy!

I had the same problem - it's definitely important that people go to the wine web link in the first post, and upgrade your software sources so that you can get wine updates.

Also, one more thing. I tried to install BEFORE doing the upgrade of Wine, and that messed with the install. Whenever I tried to do the install again from then on, it would not work - even after I'd updated Wine, even after a restart. What you need to do, is go to the bottom of the installer DK's made, and choose the "Remove E-Sword" function. THEN when you try to install again, then it worked fine.

Oh, one last thing - fairly low-tech, but handy. If you've got heaps of extra resources to install, open up your file manager (Nautilus, Thunar, etc), and go to the folder where you've put them all. Then, just so you can keep track of which ones you've already installed, just click-once on each one as you go. That way you can say, "Which one am I up to?" And your File Manager will show you.

The ONLY thing I'm trying to figure out now is where to move my personal preferences (my extra not files, my bookmarks, my highlights, etc). E-Sword isn't reading them in my Documents Folder any more.

---

### Post by david_kt on 2009-09-13
> **Pepe Lebuntu said:**
> 
The ONLY thing I'm trying to figure out now is where to move my personal preferences (my extra not files, my bookmarks, my highlights, etc). E-Sword isn't reading them in my Documents Folder any more.

Usualy in /home/username/e-Sword
If it is still fail, probably there is no link to /home/username folder and you have to make a link in /home/username/.wine_Esword/drive_c/users/username

DK

---

### Post by Pepe Lebuntu on 2009-09-13
> **david_kt said:**
> Usualy in /home/username/e-Sword
If it is still fail, probably there is no link to /home/username folder and you have to make a link in /home/username/.wine_Esword/drive_c/users/username

DK

Thanks mate. I've figured out that it's not that the files aren't in the right place, it's that they're no longer in the right format. Got to make them all notx, etc now...

---

### Post by kneewax on 2009-09-14
Hi guys, thanks for your responses - I am after the setup.exe for e-sword itself. The script is awesome, but  I want to use 8.x for now and have lost the install files.  I have the e-sword folder backed up nicely though!  :-)

I can use the manual configuration settings for installing - as we did before your marvelous script!

Thanks

Ali

---

### Post by staffie on 2009-09-15
what is the latest version of wine that works best

and will someone pretty please put a link  up to the downlaod site

and last things does the new installer have commentary in 

thanks

---

### Post by Pepe Lebuntu on 2009-09-15
Here you go: [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)
This also comes with excellent instructions. You're gonna need to tweak your Software Sources as well.

How does this Installer go for other people, in terms of individual modules AFTER the initial installation? I've got an extra few modules I want to load AFTER the initial install (my NASB update has come through, I want to install the Imitation of Christ topic, etc). I've tried to install these using the installer, and it gives me an error message. But Wine won't even touch them when I just double-click them in Nautilus.

---

### Post by david_kt on 2009-09-15
> **Pepe Lebuntu said:**
> Here you go: [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)
This also comes with excellent instructions. You're gonna need to tweak your Software Sources as well.

How does this Installer go for other people, in terms of individual modules AFTER the initial installation? I've got an extra few modules I want to load AFTER the initial install (my NASB update has come through, I want to install the Imitation of Christ topic, etc). I've tried to install these using the installer, and it gives me an error message. But Wine won't even touch them when I just double-click them in Nautilus.

You just need to make sure the modules are of correct version. I mean for version 9 onward, you will need new modules. If you want to install automatically, launch the installer and choose clear cache, and then launch the installer again and choose whatever module you want to install.

DK

---

### Post by Pepe Lebuntu on 2009-09-15
I downloaded the module from the link Rick sent me yesterday, and I'd told him I'd updated, so I presume it's the right one.

I tried your trick of using the installer to empty the cache and then using its module function, but it still gave me the error.

---

### Post by david_kt on 2009-09-15
> **Pepe Lebuntu said:**
> I downloaded the module from the link Rick sent me yesterday, and I'd told him I'd updated, so I presume it's the right one.

I tried your trick of using the installer to empty the cache and then using its module function, but it still gave me the error.

Which module do you want to install?
What exactly the error do you face?

DK

---

### Post by jonathonblake on 2009-09-15
> **jonathonblake said:**
> If a live disk user can select a default language, then I selected _English (South Africa)_.  Next time I reboot, I'll pay attention to what I actually do.

It seems that the default for the live disk I use is "English (US)"


jonathon

---

### Post by phoenix137 on 2009-09-19
I am getting a similar error to [lukeelliot]("http://ubuntuforums.org/member.php?u=199396") on Ubu 9.04.  I tried the script w/o wine update (using standard repository wine) and found it didn't work (got that cp -f error).  I uninstalled wine via the Add/Remove package manager and then RTFM for the script and installed wine from the link ([http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)).  After this, the script finished install (I did note an error in the beginning of the terminal output about ALSA but script didn't seem to care and I don't know what it would be doing with sound anyway).

To my dismay, this new version of wine does not seem to put any links in the applications menu (very annoying).  I dug through folders to /home/jason/.wine/drive_c/Program Files/e-sword and tried running the exe in a terminal.  I got the following in return:

> jason@x2x64:~/.wine/drive_c/Program Files/e-sword$ ./e-Sword.exe 
fixme:ole:OleLoadPictureEx (0xf4af1c,18910,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f980), partially implemented.
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\system32\\tx4ole14.ocx") not found
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\tx4ole14.ocx"
err:ole:CoGetClassObject no class object {15a32f01-b939-11dc-af58-0013d350667c} could be created for context 0x3
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\system32\\tx4ole14.ocx") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\system32\\tx4ole14.ocx") not found
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\tx4ole14.ocx"
err:ole:CoGetClassObject no class object {15a32f01-b939-11dc-af58-0013d350667c} could be created for context 0x3
Seems as if it can't find MFC42.DLL, but I don't know what that file is (MS Foundation Class?) and I can't find it either when I search my filesystem.

P.S.  I RTFM again and noticed that the script was trying to run winetricks, which I did not have.  I did (from home directory):

wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)
chmod +x winetricks
./winetricks mfc42

it said 'Install of mfc42 done' but I still don't seem to be able to find the file (nor can e-sword... even after an uninstall/reinstall I get the same error quoted above).

P.P.S.  lil' further digging makes me think that my launching problem might be due to the fact that I no longer have that 'desktop launcher' I was complaining about (I am not much better than a newb when it comes to WINE BTW).  After un-installing WINE, I had removed its menu entries under Applications (to tidy up before the reinstall of current version)... how do I get them back? (it doesn't seem to appear where it was before in System->Preferences->Main Menu)

---

### Post by david_kt on 2009-09-19
> **phoenix137 said:**
> 
To my dismay, this new version of wine does not seem to put any links in the applications menu (very annoying).  I dug through folders to /home/jason/.wine/drive_c/Program Files/e-sword and tried running the exe in a terminal.  I got the following in return:

Seems as if it can't find MFC42.DLL, but I don't know what that file is (MS Foundation Class?) and I can't find it either when I search my filesystem.

Open terminal and run below command:

```

env WINEPREFIX=$HOME/.wine_Esword wine "C:\Program Files\e-Sword\e-Sword.exe"
```

DK

---

### Post by phoenix137 on 2009-09-19
> **david_kt said:**
> Open terminal and run below command:

```

env WINEPREFIX=$HOME/.wine_Esword wine "C:\Program Files\e-Sword\e-Sword.exe"
```

DK
Thanks!!  That gets it running for now... I'll have to figure out how to get that in my Applications menu later I guess.

---

### Post by david_kt on 2009-09-19
> **phoenix137 said:**
> Thanks!!  That gets it running for now... I'll have to figure out how to get that in my Applications menu later I guess.

Here is how to do it. Open gedit and copy and paste below:

```
<!DOCTYPE Menu PUBLIC "-//freedesktop//DTD Menu 1.0//EN"
"http://www.freedesktop.org/standards/menu-spec/menu-1.0.dtd">
<Menu>
  <Name>Applications</Name>
  <Menu>
    <Name>wine-wine</Name>
    <Directory>wine-wine.directory</Directory>
  <Menu>
    <Name>wine-Programs</Name>
    <Directory>wine-Programs.directory</Directory>
  <Menu>
    <Name>wine-Programs-e-Sword</Name>
    <Directory>wine-Programs-e-Sword.directory</Directory>
    <Include>
      <Filename>wine-Programs-e-Sword-e-Sword.desktop</Filename>
    </Include>
  </Menu>
  </Menu>
  </Menu>
</Menu>
```

Save it as /home/username/.config/menus/applications-merged/wine-Programs-e-Sword-e-Sword.menu

Open new document in gedit and copy and paste below:

```
[Desktop Entry]
Name=e-Sword
Exec=env WINEPREFIX="$HOME/.wine_Esword" wine "C:\\Program Files\\e-Sword\\e-Sword.exe" 
Type=Application
StartupNotify=true
Path=$HOME/.wine_Esword/dosdevices/c:/Program Files/e-Sword/
Icon=$HOME/.local/share/icons/check_some_icon_here.png
```

Save it as /home/david/.local/share/applications/wine/Programs/e-Sword/e-Sword.desktop

Please replace Icon=$HOME/.local/share/icons/check_some_icon_here.png with a valid icon file.

DK

---

### Post by zeroandone on 2009-10-01
Maybe a new thread should be started. The current thread is getting too long.

---

### Post by jonnyg on 2009-10-05
I am trying to install on Kubuntu 9.04 on an Eee PC.  The automatic method did not work.  It kept trying to install to C: rather than under Program Files, and when I tried to click the button to change that, the installer crashed.  So I ended up installing manually.  I followed every step.  Whenever I run via:

env WINEPREFIX=$HOME/.wine_eSword wine "C:\Program Files\e-Sword\e-Sword.exe"

I get this output:

err:listview:LISTVIEW_WindowProc unknown msg 2210 wp=00000001 lp=00010034
err:listview:LISTVIEW_WindowProc unknown msg 2210 wp=00000001 lp=00010038
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\system32\\tx4ole14.ocx") not found
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\tx4ole14.ocx"
err:ole:CoGetClassObject no class object {15a32f01-b939-11dc-af58-0013d350667c} could be created for context 0x3
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\system32\\tx4ole14.ocx") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\system32\\tx4ole14.ocx") not found
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\tx4ole14.ocx"
err:ole:CoGetClassObject no class object {15a32f01-b939-11dc-af58-0013d350667c} could be created for context 0x3

Any ideas on where to start debugging?  This happened to me when I was running Xandros.  I finally got sick of Xandros, installed Kubuntu, and this same thing is still happening.

Thanks.

---

### Post by jonnyg on 2009-10-05
BTW, I should have mentioned, I am using wine version 1.0.1.  I just installed it tonight from freshly-updated repos.

---

### Post by jonnyg on 2009-10-05
Well, that was shortlived.  I did some googling and found this:

[http://mattrudge.wordpress.com/2009/07/20/basic-troubleshooting-for-wine-step-1/](http://mattrudge.wordpress.com/2009/07/20/basic-troubleshooting-for-wine-step-1/)

Followed the instructions there, and it's working great now.

I definitely used winetricks to install mfc42.  It gave me a success message.  I feel like maybe that was supposed to copy the dll I was missing.

BTW, I'm not sure if you ever found the issue everyone was having with copying riched20.dll, but I'm pretty sure their installation was going in to C: just like mine was.  I got that error too.  It was because riched20.dll was in drive_c, not drive_c/Program Files/e-Sword.  I could be wrong, but I know that's what was causing the same error in my case.

---

### Post by david_kt on 2009-10-06
> **jonnyg said:**
> Well, that was shortlived.  I did some googling and found this:

[http://mattrudge.wordpress.com/2009/07/20/basic-troubleshooting-for-wine-step-1/](http://mattrudge.wordpress.com/2009/07/20/basic-troubleshooting-for-wine-step-1/)

Followed the instructions there, and it's working great now.

I definitely used winetricks to install mfc42.  It gave me a success message.  I feel like maybe that was supposed to copy the dll I was missing.

BTW, I'm not sure if you ever found the issue everyone was having with copying riched20.dll, but I'm pretty sure their installation was going in to C: just like mine was.  

Please follow the steps on the first post of this thread (upgrade to latest wine), and the script should run without problem, installing e-Sword on the correct folder.

DK

---

### Post by jonnyg on 2009-10-06
For the record, I did follow the steps on the first post of this thread.  The e-Sword installer kept trying to install to C: instead of Program Files.  I tried multiple times by deleting the .wine folder and starting over.  Every time it behaved the same way.  And I did install the most recent version of wine, 1.0.1.

The setup program straight from e-Sword also tried to install to C: when I ran it, but the difference was it didn't crash when I changed install locations.

---

### Post by david_kt on 2009-10-06
> **jonnyg said:**
> For the record, I did follow the steps on the first post of this thread.  The e-Sword installer kept trying to install to C: instead of Program Files.  I tried multiple times by deleting the .wine folder and starting over.  Every time it behaved the same way.  And I did install the most recent version of wine, 1.0.1.

The setup program straight from e-Sword also tried to install to C: when I ran it, but the difference was it didn't crash when I changed install locations.

Nope. If you follow the first step to install wine, you will have wine 1.1.30, not 1.0.1. For ubuntu, the step 1 would lead you to below page:

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

which tell you step be step to add wine repository and upgrade to latest wine, which is 1.1.30 at the moment. So, please follow the step until you could get wine 1.1.30.

Please let me know if you have problem installing wine 1.1.30.

DK

---

### Post by jonnyg on 2009-10-06
Thanks for the info.  I see now under the **Explanation of the Installation Script** section where you mention the script doesn't work with wine 1.0.  I should have noticed that earlier.  However, I rarely ever install beta versions of anything, and the instructions in the first section don't specifically mention using beta wine.  The first step just says "Install wine" and "choose your distro".  And to be fair, the instructions you just linked to me state at the top:

[I]The packages here are beta packages.  This means they will  periodically suffer from  [regressions]("http://wiki.winehq.org/Regression"), and as a result an  update may break functionality in Wine.  If the latest stable release of Wine  (currently Wine 1.0.1) works for you, then you may not want to use these  beta packages.

[/I]Based on this, I was at the latest wine (albeit stable).  In this case though, 1.0.1 *wasn't* working for me.  :-)  I'll upgrade wine, but probably won't mess with my e-Sword install since it's working.

Thanks for your work on this thread.

---

### Post by david_kt on 2009-10-06
> **jonnyg said:**
> However, I rarely ever install beta versions of anything, and the instructions in the first section don't specifically mention using beta wine.  The first step just says "Install wine" and "choose your distro".  And to be fair, the instructions you just linked to me state at the top:

[I]The packages here are beta packages.  This means they will  periodically suffer from  [regressions]("http://wiki.winehq.org/Regression"), and as a result an  update may break functionality in Wine.  If the latest stable release of Wine  (currently Wine 1.0.1) works for you, then you may not want to use these  beta packages.

[/I]Based on this, I was at the latest wine (albeit stable).  In this case though, 1.0.1 *wasn't* working for me.  :-)  I'll upgrade wine, but probably won't mess with my e-Sword install since it's working.

Thanks for your work on this thread.

Many people does not know the meaning of wine stable release (1.0 for this case). The meaning of the stable release is only for 4 applications:
1. Photoshop CS2,
2. PowerPoint Viewer 97 and 2003, 
3. Word Viewer 97 and 2003,
4. Excel Viewer 97 and 2003 

[http://wiki.winehq.org/WineReleaseCriteria?action=show&redirect=WineReleasePlan](http://wiki.winehq.org/WineReleaseCriteria?action=show&redirect=WineReleasePlan)

Whereas for e-Sword, so far we could consider 1.1.6 and above as "stable release". Recently there is a regression on the desktop launcher, but I am still not sure whether it is due to wine of due to new e-Sword.

DK

---

### Post by a__l__a__n on 2009-10-09
I have e-Sword 9.5.1 running under Ubuntu 9.04 (64 bit) on my laptop.  I've had a long and happy relationship with earlier versions of e-Sword under wine (just overriding riched20.dll).   This time around, installing the latest e-sword version into the current fully-up-to-ate Ubuntu 9.04, I just ran the stock e-sword installer under wine, added mfc42.dll from XP, ran winecfg and set the override for that dll, applied font-smoothing, and downloaded and installed the 9.x version of the bibles, commentaries, etc.  And it all works...  except for this: my NET bible does not display.  It is there, and in the correct 9.x format.  I get a tab for that version (actually, two tabs -- one for the version with notes and one without).  But when I choose that version, the bible pane is empty.

I can search the NET version, and the search results top pane shows the text from the NET bible. But the bottom pane of search results is blank -- not displaying the selected verse. So I know the text is there, and e-Sword is successfully reading it.  Something goes wrong in displaying.

Similarly, the scripture tooltips pop up blank when the selected version is NET.  

My other versions (including several downloaded from e-Sword, plus the purchased NIV bundle) work fine.  

Here's the kicker: the NET bible works perfectly under Windows XP... the same identical file.  Just not under ubuntu and wine.

I attempted to repair it by copying all the font files from my XP machine to the wine windows/fonts directory.  That did not help.  Didn't seem to hurt either...

Can anyone suggest a solution?
Thanks!

---

### Post by david_kt on 2009-10-09
> **a__l__a__n said:**
> And it all works...  except for this: my NET bible does not display.  It is there, and in the correct 9.x format.  I get a tab for that version (actually, two tabs -- one for the version with notes and one without).  But when I choose that version, the bible pane is empty.

Where could I download the NET bible?

Edit:
I downloaded NET bible free version from below link:

[http://bible.org/assets/downloads/esword/net_free_esword_setup2.exe](http://bible.org/assets/downloads/esword/net_free_esword_setup2.exe)

It could display everything normally, including the search bottom pane. Please try to use e-Sword installer from the first post of this thread. For downloaded modules, use "manual" option to install it.

DK

---

### Post by jonnyg on 2009-10-09
> **a__l__a__n said:**
> I get a tab for that version (actually, two tabs -- one for the version with notes and one without).  But when I choose that version, the bible pane is empty.

I can search the NET version, and the search results top pane shows the text from the NET bible. But the bottom pane of search results is blank -- not displaying the selected verse. So I know the text is there, and e-Sword is successfully reading it.  Something goes wrong in displaying.

If you haven't already, try 1) clicking in the pane and dragging 2) clicking in the pane and hitting ctrl-a or 3) clicking in the pane and scrolling your mouse wheel up and down.  Sometimes when I switch between panes in Linux, the Bible pane comes back empty except for the one verse which is currently selected.  If I scroll or select all text, it shows back up again.

I have a feeling this may not work for you because it sounds like not even one verse is showing up.  But it's worth a try.

---

### Post by jonathonblake on 2009-10-10
> **david_kt said:**
> 
Whereas for e-Sword, so far we could consider 1.1.6 and above as "stable release".

I think that  for the time being 1.1.6 is  the highest version of WINE that should be considered "stable" for e-Sword.

> still not sure whether it is due to wine of due to new e-Sword.


I think that it is a combination of e-Sword version, and WINE version.   

With the same version of WINE  and installer script,  some versions of e-Sword install, and some won't install.   Change the installer script, and versions that wouldn't install can install, but versions that would install might not install. Change the version of WINE, and  different versions of e-Sword exhibit the same phenomena.

jonathon

---

### Post by jonathonblake on 2009-10-10
> **david_kt said:**
> Please try to use e-Sword installer from the first post of this thread. For downloaded modules, use "manual" option to install it.

For reasons I don't understand, using the "manual" option of the e-Sword installer script makes installation and display of virtually all Bible Study Software for Windows much easier & more reliable than installing them without that script.

I'll grant that it didn't help with Libronix, but getting that to run on Linux is a lost cause.

jonathon

---

### Post by okos on 2009-10-22
Thank you so much! It worked on Debian Lenny without any problems!:P

---

### Post by n36atr0n on 2009-10-31
Everything running smooth at last! thanks alot for all your help. But, there still one weird. My Navigation Trees has lost, dont know how to bring it back. Its usually place at the very left of esword view. 

Im still can using the look scripture reference that available at top-left. But its still uncomfortable using e-sword without navigations tree. please help me to solve it

Im using wine -1.1.32 and esword 9.03

---

### Post by zeroandone on 2009-10-31
> **n36atr0n said:**
> Everything running smooth at last! thanks alot for all your help. But, there still one weird. My Navigation Trees has lost, dont know how to bring it back. Its usually place at the very left of esword view. 

Im still can using the look scripture reference that available at top-left. But its still uncomfortable using e-sword without navigations tree. please help me to solve it

Im using wine -1.1.32 and esword 9.03
The installer needs to be updated to get the latest version of e-sword to fix the problem. According to e-sword web site:

[B]e-Sword version 9.5 changes from 9.0

A fully dockable user interface enables you to completely customize the layout in hundreds of different ways! Display what you want, where you want it by dragging the views into position with their titlebar.
 
Back by popular demand, the Bible Browser! The new dockable interface allows you to place it wherever you want, or not display it at all.
[/B]

---

### Post by n36atr0n on 2009-11-01
> **zeroandone said:**
> The installer needs to be updated to get the latest version of e-sword to fix the problem. According to e-sword web site:

[B]e-Sword version 9.5 changes from 9.0

A fully dockable user interface enables you to completely customize the layout in hundreds of different ways! Display what you want, where you want it by dragging the views into position with their titlebar.
 
Back by popular demand, the Bible Browser! The new dockable interface allows you to place it wherever you want, or not display it at all.
[/B]

Its so amazing! Thank you all!!! after im upgrading this, its normal again.
Im waiting this for so long time. Thanks for all friends here that so much helping me. Thanks

---

### Post by frank cox on 2009-11-03
> **kneewax said:**
> Hi folks,

I just had a to re-install Ubuntu and as part of the process upgraded to version 9 of e-sword using David's fabulous script.

BUT I have to say I really hate the new version of the software - none of my modules work (I know other found this) including versions I bought. The strange 'script' (for alt+1 etc) icons are a mess and the loss of the scripture navigation tool (I got it back once, but now it's gone again) is a real loss.  Added to that it keeps locking up and freezig on my x64 machine.

This is not the script or David's fault, I am really grateful forr all the help David has given me getting revious versions working - and the script is just fantastic.  Does anyone have a copy of version 8 setup.exe they could mail me as it's no longer available on Rick's site?  I think I'll do a manual install of that rather than struggle with this.  Not sure what it's like under windows but if it's as bad as it is under Wine then I fear Rick may have made a mistake with this latest version.....

Hi Kneewax:

  I have a copy of 8.0 I paid for. After using it for years I figure I should contribute.
I regret trying to upgrade because everything worked but the maps and the text was fuzzy but I am now pretty sure i could at least have fixed the text.
I have a lot of the plug ins as well as well. 
There is another program called  TheWord that is supposed to be very Linux friendly and I may try running it on puppy which I like.

I can send you a copy since it is share ware. If you give me your address , or I can send it general delivery . I would not be offended.

If anyone can help me get the maps to work in 8  would be most grateful.

---

### Post by david_kt on 2009-11-03
> **frank cox said:**
> 
I regret trying to upgrade because everything worked but the maps and the text was fuzzy but I am now pretty sure i could at least have fixed the text.
If anyone can help me get the maps to work in 8  would be most grateful.

Last time the 8 version work very well, including the maps and text. Below is my notes on winehq:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14655&iTestingId=34011](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14655&iTestingId=34011)

```
Need to add msls31.dll from windows, copy riched20.dll from e-Sword directory to system32 directory, and add dlloverrides for riched20.dll and oleaut32.dll.
```

If you could find my older script for this purpose is the best (e-Sword_installer_211108.tar.gz).

DK

---

### Post by rgroene on 2009-11-03
For some reason, I could never get E-sword to work on Jaunty. A few days ago though, I upgraded to Karmic, and now it works great (not sure if it uses an upgraded version of Wine?). Even the modules can be added now simply by downloading and double clicking them (just like on Windows).

Before, using E-Sword was one of the few times that I rebooted my computer into Windows. The other main reason is when I need to do recording because I haven't been able to get that to work in Ubuntu. But, I'm happy to say that I am finding fewer and fewer reasons to ever boot into Windows (the fact that I have Vista dissuades me even more)!

Anyway, E-Sword is the first Bible software I have ever used and definitely the best free Bible software I have ever come across. I have Xiphos, and while that has some good resources, it doesn't come close to E-Sword. I really think that free Bible software is a good idea, and I would like to see more things become available for free through agreements with publishing companies, etc. It's nice to know that the ESV, one of the best modern translations, has been made available on this and other programs for free.

Also, I really think E-Sword should be made open source so that it can be developed natively for Mac and Linux and improved by the community.

---

### Post by david_kt on 2009-11-04
> **rgroene said:**
> For some reason, I could never get E-sword to work on Jaunty. A few days ago though, I upgraded to Karmic, and now it works great (not sure if it uses an upgraded version of Wine?). Even the modules can be added now simply by downloading and double clicking them (just like on Windows).

That is because newer wine. Check wine --version. I notice karmic repository has 2 wine, stable version (1.0.1) and beta version (1.1.32). Whereas in Jaunty only 1.0.1. So, it might be you use 1.1.32 in karmic.

Anyhow, I doubt it would run perfectly. You still need msls31 to enable pop up when pointing to reference number, and dlloverride to show map properly. That is the reason I still maintain the installer.

DK

---

### Post by rgroene on 2009-11-04
If you are talking about the pop-ups that come up when you hover over the reference numbers in KJV+Strong's reference numbers, that seems to be working OK. I haven't tried displaying maps. I think I may have installed some add-ons a while back through winetricks, but I don't remember if that was on my current installation. The only other programs I have running through Wine are Notepad++ (for programming), iTunes+QuickTime (for listening to *.m4a and other formats not supported), and ies4linux (for those very rare occasions in which I actually need to use Internet Explorer, such as testing)

In any case, it doesn't run *perfectly*. The one thing I have found that wasn't perfect was the rendering. While most of the text on the screen is easily readable, some of the smaller text at the very bottom of the application is barely readable and the text in the pop-ups is sort of hard to read. But, anyway, it's been running well enough that it doesn't justify booting into Windows.

Also, my current version number of Wine is 1.1.31.

---

### Post by saquerocl on 2009-11-10
Friends, when after the install with the script I get the same message than chzumbrunne[COLOR=Black]n but with the spanish variation: instead of Program files, I have Archivos de programa; this is my directory:

/home/erwin/.wine_Esword/drive_c/Archivos de programa/e-Sword

instead of the default in the script (I guess):

[/COLOR][[COLOR=Black]/home/erwin/.wine_Esword/drive_c/Program Files/e-Sword/[/COLOR]]("http://ohioloco.ubuntuforums.org/member.php?u=692394")

Some suggestions, please. I'm here after few hours fighting against my machine :)

I'm using wine 1.1.32 under Xubuntu 9.10. 

(Sorry my english, I just speak spanish, from Chile)
--------------------------------------------------------------

Edit:

I have final solution for the "returned status 1.  Aborting." message: I create a **/Program Files/e-Sword/** folder in **/.wine_Esword/drive_c/** and make the install there. Problem solved. Hope this help other people! 

(again, sorry my english)

---

### Post by david_kt on 2009-11-10
> **saquerocl said:**
> Friends, when after the install with the script I get the same message than chzumbrunne[COLOR=Black]n but with the spanish variation: instead of Program files, I have Archivos de programa; this is my directory:

/home/erwin/.wine_Esword/drive_c/Archivos de programa/e-Sword

instead of the default in the script (I guess):

[/COLOR][[COLOR=Black]/home/erwin/.wine_Esword/drive_c/Program Files/e-Sword/[/COLOR]]("http://ohioloco.ubuntuforums.org/member.php?u=692394")

Some suggestions, please. I'm here after few hours fighting against my machine :)

I'm using wine 1.1.32 under Xubuntu 9.10. 

(Sorry my english, I just speak spanish, from Chile)
--------------------------------------------------------------

Edit:

I have final solution for the "returned status 1.  Aborting." message: I create a **/Program Files/e-Sword/** folder in **/.wine_Esword/drive_c/** and make the install there. Problem solved. Hope this help other people! 

(again, sorry my english)

I will think of a way to suit other languages version other than English, hopefully I could find solution soon.

DK

---

### Post by david_kt on 2009-11-11
I have amended the script to support other languages. Please help to test and feedback.

DK

---

### Post by saquerocl on 2009-11-15
> **david_kt said:**
> I have amended the script to support other languages. Please help to test and feedback.

DK

It work flawless for me, under Linux Mint 8 RC (based on Ubuntu 9.10), using Wine 1.1.31.  font_smoothing script work just fine too.

Good work, thanks!

---

### Post by Pepe Lebuntu on 2009-11-17
Hi, I just reinstalled on my computer to have a fresh version of ubuntu 9.10. The only thing I can't get to work is (you guessed it...) E-Sword.

I've got the Wine version 1.1.33 (and have done all the software source stuff the wine site says to do) and am trying to get E-Sword 9.05.001 to work. Whether I'm trying to install, modify, or remove, or whatever, it seems like the install gets a little of the way through, but then dies.

Lord, give me patience!

---

### Post by david_kt on 2009-11-17
> **Pepe Lebuntu said:**
> Hi, I just reinstalled on my computer to have a fresh version of ubuntu 9.10. The only thing I can't get to work is (you guessed it...) E-Sword.

I've got the Wine version 1.1.33 (and have done all the software source stuff the wine site says to do) and am trying to get E-Sword 9.05.001 to work. Whether I'm trying to install, modify, or remove, or whatever, it seems like the install gets a little of the way through, but then dies.

Lord, give me patience!
Did you use the latest installer at the first post of this thread?
What is the error message?

DK

---

### Post by Pepe Lebuntu on 2009-11-17
Hey mate,

I tried and tried and tried... and on about the tenth try, it miraculously decided to work. What I needed to do, it seems, was move all the installation files (including your installer) into an "e-Sword Install" folder in the C drive of the .wine folder. Then it was all happy.

Once I actually GOT the E-Sword thing running, it was easy. I've since just copied over all the old modules that I had backed up elsewhere, and chucked them into the new E-Sword folder.

The next thing I have to ask is about where it stores my notes. I've moved my "Documents" Folder under a Dropbox to keep it backed up. Hence, my e-Sword files SHOULD be in "user/Dropbox/Documents/E-Sword/". I've told Wine that this is where "My Documents" should be located - but your E-Sword isn't recognising that, and is insisting on putting it under my user folder. How can I get into your E-Sword's settings?

---

### Post by david_kt on 2009-11-17
> **Pepe Lebuntu said:**
> 
The next thing I have to ask is about where it stores my notes. I've moved my "Documents" Folder under a Dropbox to keep it backed up. Hence, my e-Sword files SHOULD be in "user/Dropbox/Documents/E-Sword/". I've told Wine that this is where "My Documents" should be located - but your E-Sword isn't recognising that, and is insisting on putting it under my user folder. How can I get into your E-Sword's settings?

You should add:  env WINEPREFIX=~/.wine_Esword
For example if it is winecfg, then it would be:

```
 env WINEPREFIX=~/.wine_Esword winecfg
```

DK

---

### Post by ubume2 on 2009-11-19
I recently downloaded Ubuntu Karmic.  I installed wine 1.0.1 from Karmic's repository. I used the e-sword-installer script referred to in this thread. E-Sword (9.5.1) worked fine, but I noticed that the font smoothing script didn't work.

I removed that version of wine. and attempted to install Karmic's version of wine.  It refused to install because of unmet dependencies.

I went to **WINE_HQ Ubuntu 9.04** repository and installed that version of wine.  It installed fine.  It asked to install Gecko Installer for Wine. Installation went smoothly.  And the font-smoothing script worked great this time. This was wine version 1.1.33.

Edit: Sorry for the wasted space. After removing 9.04's WINEHQ version I reinstalled wine using Karmic's  wine 1.2  1.1.31-0ubuntu3. Works great.

---

### Post by frank cox on 2009-11-23
[COLOR=Red]**SOLVED!**[/COLOR]

This is the error I got:


ESword_Installer error : Note: command 'env WINEPREFIX=Home/forrest.wine_Esword ./winetricks mfc42


I reinstalled the basic program and Voila!

It works better than when I tried it with Crossover which I nuked!

Thanks fo rthe links-help!

---

### Post by frank cox on 2009-11-23
Everything works but the graphic viewer, sermon illustrations  and ,daily devotions
The copy and paste into study notes is grayed out but right clicking works fine.

The only one I am really worried about is the viewer.  Any idea on how to turn it on?

TIA

---

### Post by david_kt on 2009-11-23
> **frank cox said:**
> Everything works but the graphic viewer, sermon illustrations  and ,daily devotions
The copy and paste into study notes is grayed out but right clicking works fine.

The only one I am really worried about is the viewer.  Any idea on how to turn it on?

TIA

Have installed any graphic modules? If not yet, please install it first.

DK

---

### Post by frank cox on 2009-11-24
Wher4 do I get the graphics viewer?

I installed a few maps before I realized there was no graphics viewer and I did not see it at the E-sword site.

Thanks

---

### Post by david_kt on 2009-11-24
> **frank cox said:**
> Wher4 do I get the graphics viewer?

I installed a few maps before I realized there was no graphics viewer and I did not see it at the E-sword site.

Thanks

Not graphic viewer, but the maps. Now try to launch e-Sword installer again, and choose cbm (classical Bibble Map). After it finish installing the map, launch e-Sword.

DK

---

### Post by manney on 2009-11-26
Has anyone noticed that the Locate study notes freezes after they have used the highlighter.   E sword still runs but the locate study notes does not come up, my cpu reads 100% used and I have to kill e sword from the system monitor to get my cpu down to a normal reading

---

### Post by frank cox on 2009-11-27
> **david_kt said:**
> Not graphic viewer, but the maps. Now try to launch e-Sword installer again, and choose cbm (classical Bibble Map). After it finish installing the map, launch e-Sword.

DK


Thanks!

That is bizarre because I had downloaded and installed  several maps including the NASA maps and nothing happened. I put the classic Bible map in and voila it loaded and so did the Antiquities of the Jews and the other Bibles etc. etc.

Why that worked I don't know but thanks a million!
I have to have my E-Sword, thanks to you I do!

---

### Post by cgul1 on 2009-11-29
I just wanted to post a thank you
I am relatively new to ubuntu and had not experienced wine until going through this tutorial.
everything worked great under karmic installing esword and ASV.
thanks so much

Jerry

---

### Post by Andytater on 2009-12-14
I also want to say thank you for this tutorial.  It worked flawlessly.  I new to Ubuntu having switched from XP.  I'm finding Ubuntu to be an excellent alternative to windows.

Many thanks!

Peace

---

### Post by Eutaw on 2009-12-15
David,
Thanks again for all your hard work (especially getting us noobies up and running). I'm very happy to have eSword up and running, and your instructions were straightforward and simple to follow.
Thumbs up, bud!

---

### Post by zeroandone on 2009-12-25
Just want to let you know that the installer works well on Ubuntu 10.04 Lucid Lynx Alpha 1 with Wine 1.1.35. :popcorn::popcorn:

One thing though, when I first tried to run the installer without Wine installed, it didn't inform me the absence of Wine, and actually it didn't do anything at all. It took me a while to realize my stupidity of not installing Wine first.

Thank you soooo much for your hard work, David.

God bless,

Jeffrey

---

### Post by zeroandone on 2009-12-31
For those who use Chinese Bible and apply Font Smoothing, DO NOT choose option 2 or 3 in Font Smoothing and only option 4 works for Chinese Bible. See the attached screen shot after using option 3 or 4 in Font Smoothing.

---

### Post by frank cox on 2010-01-12
I have had zero problems with mt Ubuntu install of e-sword but no luck in Puppy. 
Wine is there,Internet explorer works but I cannot get e-sword to execute. 
Anyone here have experience with Puppy?
Ubuntu is a great program but too big for a flash drive i think.

---

### Post by david_kt on 2010-01-13
> **frank cox said:**
> I have had zero problems with mt Ubuntu install of e-sword but no luck in Puppy. 
Wine is there,Internet explorer works but I cannot get e-sword to execute. 
Anyone here have experience with Puppy?
Ubuntu is a great program but too big for a flash drive i think.

What is the wine version?

DK

---

### Post by frank cox on 2010-01-13
> **david_kt said:**
> What is the wine version?

DK

1,31 I think, it just says 1.0 under about in config. I have tried so many I forget.

I will be happy to use another if there is an advantage.

Thanks!

---

### Post by david_kt on 2010-01-13
> **frank cox said:**
> 1,31 I think, it just says 1.0 under about in config. I have tried so many I forget.

I will be happy to use another if there is an advantage.

Thanks!

There is no 1.3X version yet, the highest is 1.1.36.
What you could do is open terminal and:
```
wine --version
```
to check the wine version.

Try to use wine 1.1.23 or above, and then re-install e-Sword.

DK

---

### Post by frank cox on 2010-01-14
> **david_kt said:**
> There is no 1.3X version yet, the highest is 1.1.36.
What you could do is open terminal and:
```
wine --version
```to check the wine version.

Try to use wine 1.1.23 or above, and then re-install e-Sword.

DK

I did . Wine installs fine, Internet Explorer works, eword says it installed and the executable is in .wine/Drive_C/Program Files/E-Sword/esword.exe but nothing happens when you click on it.

Thanks!

---

### Post by david_kt on 2010-01-14
> **frank cox said:**
> I did . Wine installs fine, Internet Explorer works, eword says it installed and the executable is in .wine/Drive_C/Program Files/E-Sword/esword.exe but nothing happens when you click on it.

Thanks!

Did you use the installer at the first post of this thread?

DK

---

### Post by Reg on 2010-01-14
I've gone through pages of this looking for a similar problem but can't find one!! I may have missed it of course, in which case I apologise.

I'm running Mint 8 and I've installed e-Sword with Wine. It runs fine if I rt click e-Sword.exe in the File with the Wine Windows Program Launcher but I can't get a launcher on the desktop or menu to open it. I've tried all sorts of syntax but to no avail. Can you help, please?
Blessings
Reg
Helsinki

---

### Post by david_kt on 2010-01-14
> **Reg said:**
> I've gone through pages of this looking for a similar problem but can't find one!! I may have missed it of course, in which case I apologise.

I'm running Mint 8 and I've installed e-Sword with Wine. It runs fine if I rt click e-Sword.exe in the File with the Wine Windows Program Launcher but I can't get a launcher on the desktop or menu to open it. I've tried all sorts of syntax but to no avail. Can you help, please?
Blessings
Reg
Helsinki

Could you try below syntax on the launcher:

```
env WINEPREFIX=/absolute/path/to/.wine_Esword wine "C:\Program Files\e-Sword\e-Sword.exe"
```

The absolute path to the wineprefix (could be .wine or wine_Esword) is depend on how you install e-Sword. And the wine "C:\Program Files\e-Sword\e-Sword.exe" is the default location. If you install it in on different location, adjust it to suit your location. 

DK

---

### Post by Reg on 2010-01-15
Thanks for the quick reply. This is how the launcher is now but it doesn't work, I'm afraid:

env WINEPREFIX=/home/reg/.wine_Esword wine "C:\Program Files\e-Sword\e-Sword.exe".

I can't understand why e-Sword.exe doesn't react!
Thanks

Reg

---

### Post by david_kt on 2010-01-15
> **Reg said:**
> Thanks for the quick reply. This is how the launcher is now but it doesn't work, I'm afraid:

env WINEPREFIX=/home/reg/.wine_Esword wine "C:\Program Files\e-Sword\e-Sword.exe".

I can't understand why e-Sword.exe doesn't react!
Thanks

Reg

Probably it is installed in different wineprefix. Try:

```
env WINEPREFIX=/home/reg/.wine wine "C:\Program Files\e-Sword\e-Sword.exe"
```

Failing that, please give me the absolute path to e-Sword.exe file.

DK

---

### Post by Reg on 2010-01-16
I'm afraid it doesn't start up.

This is path:
home/reg/.wine_Esword/drive_c/Program Files/e-Sword/e-Sword.exe.
Thanks
Reg

---

### Post by david_kt on 2010-01-16
> **Reg said:**
> I'm afraid it doesn't start up.

This is path:
home/reg/.wine_Esword/drive_c/Program Files/e-Sword/e-Sword.exe.
Thanks
Reg

Could you try whether or not the script work in terminal:

```
env WINEPREFIX=/home/reg/.wine_Esword wine "C:\Program Files\e-Sword\e-Sword.exe"
```

If it works, open gedit (or any text editor) and copy and paste below:

```
#!/bin/bash
env WINEPREFIX=/home/reg/.wine_Esword wine "C:\Program Files\e-Sword\e-Sword.exe"
```

save it as esword.sh at location of your choice, lets say /home/reg/
And then in terminal:
```
chmod +x /home/reg/esword.sh
```

After that, change the to your launcher:

```
/home/reg/esword.sh
```

DK

---

### Post by frank cox on 2010-01-16
Thanks-I will give that a shot. if it works you will be a big hero on the puppy forum!

---

### Post by Reg on 2010-01-17
No good I'm afraid. This is what I got using the Terminal
env WINEPREFIX=/home/reg/.wine_Esword wine "C:\Program Files\e-Sword\e-Sword.exe"
err:ole:CoGetClassObject class {fa3794c8-2db6-460a-8d60-cb17a6b8bfb7} not registered
err:ole:CoGetClassObject class {fa3794c8-2db6-460a-8d60-cb17a6b8bfb7} not registered
err:ole:CoGetClassObject no class object {fa3794c8-2db6-460a-8d60-cb17a6b8bfb7} could be created for context 0x3

Is this any guide?

Thanks

Reg
err:ole:CoGetClassObject class {fa3794c8-2db6-460a-8d60-cb17a6b8bfb7} not registered
err:ole:CoGetClassObject class {fa3794c8-2db6-460a-8d60-cb17a6b8bfb7} not registered
err:ole:CoGetClassObject no class object {fa3794c8-2db6-460a-8d60-cb17a6b8bfb7} could be created for context 0x3

---

### Post by david_kt on 2010-01-17
> **Reg said:**
> No good I'm afraid. This is what I got using the Terminal
env WINEPREFIX=/home/reg/.wine_Esword wine "C:\Program Files\e-Sword\e-Sword.exe"
err:ole:CoGetClassObject class {fa3794c8-2db6-460a-8d60-cb17a6b8bfb7} not registered
err:ole:CoGetClassObject class {fa3794c8-2db6-460a-8d60-cb17a6b8bfb7} not registered
err:ole:CoGetClassObject no class object {fa3794c8-2db6-460a-8d60-cb17a6b8bfb7} could be created for context 0x3


How did you install e-Sword?
Please use the script at the first post of this thread or the manual instruction there.

DK

---

### Post by frank cox on 2010-01-18
> **david_kt said:**
> How did you install e-Sword?
Please use the script at the first post of this thread or the manual instruction there.

DK

Hi David:

  The problem there is that no one seems to be able to get the installer to execute in Puppy. Here is the workaround that some Puppy users have found by copying the files installed using your system from Ubuntu to Puppy.

[http://murga-linux.com/puppy/viewtopic.php?p=383046#383046](http://murga-linux.com/puppy/viewtopic.php?p=383046#383046)

I would rather use the same method you gave us for Ubuntu directly  but it is over my head to make it work in Puppy,

---

### Post by david_kt on 2010-01-18
> **frank cox said:**
> Hi David:

  The problem there is that no one seems to be able to get the installer to execute in Puppy. Here is the workaround that some Puppy users have found by copying the files installed using your system from Ubuntu to Puppy.

[http://murga-linux.com/puppy/viewtopic.php?p=383046#383046](http://murga-linux.com/puppy/viewtopic.php?p=383046#383046)

I would rather use the same method you gave us for Ubuntu directly  but it is over my head to make it work in Puppy,

If you need to hack, it is better to use e-Sword portable method, available at the first post of this thread. I am downloading Lighthousepup to see how the easy way to run e-Sword.

DK

---

### Post by James Willis on 2010-01-18
Hi David,

Thank you for your installation program.  It worked flawlessly for me in both ubuntu and kubuntu.(including 10.04 beta2):D

Also tried it with various derivatives of Puppy linux using your installer and your detailed manual procedures.  Unfortunately, that didn't work, so I copied the files over to puppy from the successful installation in Kubuntu and it worked great as Frank Cox has noted above.  I'm looking forward to your improvements on the techniques I used.

Thanks again, I couldn't have done it without your installer and detailed procedure outlined in your first post.

Jim:D

---

### Post by zeroandone on 2010-01-18
> **James Willis said:**
> Hi David,

Thank you for your installation program.  It worked flawlessly for me in both ubuntu and kubuntu.(including 10.04 beta2):D
Jim:D
Has 10.04 **beta2** been released? Did you mean Alpha 2 instead?

---

### Post by James Willis on 2010-01-18
alpha 2 :(

---

### Post by frank cox on 2010-01-20
Hi David:

  I really hate to bother you again but when I tried to copy the wine esword cache and the ,wine e-sword directory to a flash disk to install to puppy it got corrupted and disappeared.
When I fixed a problem with my sources.list and got all my software sources back up the files magically reappeared but the program won't run.
All the Bibles etc are still there . I tried using the built in uninstaller and it said it worked but nothing changed. Wine still works, even IE 6.

How can I uninstall esword? Will just deleting all the files I can find work?

Thanks!

---

### Post by david_kt on 2010-01-20
> **frank cox said:**
> Hi David:

  I really hate to bother you again but when I tried to copy the wine esword cache and the ,wine e-sword directory to a flash disk to install to puppy it got corrupted and disappeared.
When I fixed a problem with my sources.list and got all my software sources back up the files magically reappeared but the program won't run.
All the Bibles etc are still there . I tried using the built in uninstaller and it said it worked but nothing changed. Wine still works, even IE 6.

How can I uninstall esword? Will just deleting all the files I can find work?

Thanks!

1. I am not clear what happened. When you copy the files, the original files should not be disappeared. It might be problem with your harddisk.
2. To uninstall e-Sword, you could just deleted the whole folder of .wine_Esword.
3. But in my opinion, just relaunch e-Sword installer to re-install e-Sword. It would repair it. Only if it fail to repair, then you should delete .wine_Esword folder.

DK

---

### Post by sputnikeee on 2010-01-30
I am another happy installer.  Thank you very much, worked perfectly without a hitch. Like many others I read, felt lost without e-sword due to Linux switch, now I have it all! And a very HUGE thank you to Rick Meyers as well, should he ever see this.                                            Mike

---

### Post by stevehaines on 2010-01-30
Using 9.10 on an older 32 bit system I did not need to use the latest beta version of Wine. Indeed, the latest version would not install. Just using the version suggested by Synaptic installed fine.

The eSword installation worked perfectly by following the rest of the instructions, but a little slow with only 256M of RAM. To put in the rest of the modules I did not have to run the installer in a terminal. Just selecting "Run" was enough.

Great job, and many thanks!:D

---

### Post by kewl1uk on 2010-02-04
If it's a Bible app you're after just install Bibletime from the Ubuntu Software Centre. This gives direct download of Crosswire titles through Settings > Bookshelf Manager. Looks a little like Mobipocket on Windows and works a little bit like it too.

---

### Post by Anastasis on 2010-02-04
> **kewl1uk said:**
> If it's a Bible app you're after just install Bibletime from the Ubuntu Software Centre. This gives direct download of Crosswire titles through Settings > Bookshelf Manager. Looks a little like Mobipocket on Windows and works a little bit like it too.

I would also add that you can export sword modules directly from BibleTime to Bible Edit. So if you're a Bible Edit user like I am, and work on translation or footnote additions to sword modules, then BibleTime really is indispensable.

---

### Post by billstei on 2010-02-08
My own experience with installing e-Sword 9.5.1 in Karmic/Wine 1.1.37:

1) Install setup951.exe
2) Add mfc42.dll to system32 folder
3) Add msls31.dll to e-Sword folder (or put it in system32 folder)
4) Override riched20 in winecfg (the dll is already in the e-Sword folder)
5) Run winetricks and select fontsmooth-rgb (not sure if this did anything)

So far so good, but I haven't tested everything ;)

---

### Post by frank cox on 2010-02-21
Hi David:

  I just got through installing to Puppy and UBU 9.04 . 
With Puppy I never got the installer to work but manually installing the dlls did the trick.
I am having trouble with font smoothing there but it may be unrelated-not enough space.

In 9.04 The installer worked fine ..

The only problem I have had is with the portable installer. Here is the error I got.
/media/disk/eSword_portable/drive_c/Program Files/e-Sword/e-Sword.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/disk/eSword_portable/drive_c/Program Files/e-Sword/e-Sword.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/disk/eSword_portable/drive_c/Program Files/e-Sword/e-Sword.exe or
          /media/disk/eSword_portable/drive_c/Program Files/e-Sword/e-Sword.exe.zip, and cannot find /media/disk/eSword_portable/drive_c/Program Files/e-Sword/e-Sword.exe.ZIP, period.

I had a similar error with Ubuntu relating to 7zips so I uninstalled it and it seemed to do the trick.

Any ideas.

I will send a donation if you tell me where, you obviously have a passion for this project and spend a great deal of time on it . Thank you so much!

---

### Post by frank cox on 2010-02-21
Hi David:

I just got through installing to Puppy and UBU 9.04 .
With Puppy I never got the installer to work but manually installing the dlls did the trick.
I am having trouble with font smoothing there but it may be unrelated-not enough space.

In 9.04 The installer worked fine ..

The only problem I have had is with the portable installer. I may have misunderstood how you start it.  Is there a terminal command to start

Here is the error I got.
/media/disk/eSword_portable/drive_c/Program Files/e-Sword/e-Sword.exe]
End-of-central-directory signature not found. Either this file is not
a zipfile, or it constitutes one disk of a multi-part archive. In the
latter case the central directory and zipfile comment will be found on
the last disk(s) of this archive.
note: /media/disk/eSword_portable/drive_c/Program Files/e-Sword/e-Sword.exe may be a plain executable, not an archive
zipinfo: cannot find zipfile directory in one of /media/disk/eSword_portable/drive_c/Program Files/e-Sword/e-Sword.exe or
/media/disk/eSword_portable/drive_c/Program Files/e-Sword/e-Sword.exe.zip, and cannot find /media/disk/eSword_portable/drive_c/Program Files/e-Sword/e-Sword.exe.ZIP, period.

I had a similar error with Ubuntu relating to 7zips so I uninstalled it and it seemed to do the trick.

This time I never saw it install anything, all the sudden all the modules and the main program were there. I tried to run it from program files on the usb stick. Is there a terminal command to start

Any ideas.

---

### Post by david_kt on 2010-02-22
> **frank cox said:**
> 
The only problem I have had is with the portable installer. I may have misunderstood how you start it.  Is there a terminal command to start



To start it, just double click on:

"e-Sword_portable_launcher" on the root folder of your usb.

Provided you have done the previous steps:

2. Extract it and you will have 3 scripts.
3. Copy those 3 scripts to root folder of any usb.
4. double click "create_e-Sword_Wine_portable" on the usb and choose "run in terminal", it will open menu. You could choose to create e-Sword portable only.

DK

---

### Post by frank cox on 2010-02-22
> **david_kt said:**
> To start it, just double click on:

"e-Sword_portable_launcher" on the root folder of your usb.

Provided you have done the previous steps:

2. Extract it and you will have 3 scripts.
3. Copy those 3 scripts to root folder of any usb.
4. double click "create_e-Sword_Wine_portable" on the usb and choose "run in terminal", it will open menu. You could choose to create e-Sword portable only.

DK

I did that and got that error .

---

### Post by david_kt on 2010-02-22
> **frank cox said:**
> I did that and got that error .

Open terminal and issue below command:

```
ls $HOME/.wine_temp
```

What is the output?

Double click the e-Sword_portable_launcher and if it give you error, do not close it yet but open terminal and issue below again:

```
ls $HOME/.wine_temp
```

What is the output?

DK

---

### Post by zeroandone on 2010-02-27
This great installer worked well in Lucid Lynx Alpha 2, but not in Alpha 3. I upgraded my system to Alpha 3 and tried to re-install e-sword, I got this error (after the installation was complete):
```
Esword_installer error: Note: command 'env WINEPREFIX=/home/jeffrey/.wine_Esword wine /home/jeffrey/.wineswordcache/setup951.exe' returned status 194. Aborting.
```

I am running the latest development version of Wine: 1.1.39.

I am not sure if it is related to Lucid Lynx Alpha 3 or Wine.

---

### Post by frank cox on 2010-03-03
The output is :
ls: cannot access /home/myfolder/.wine_temp: No such file or directory
myname@mymachine-Ubu-1:~$ 

Now for the good news. I got the program working on a new install with the installer.

I could only seem to install wine 1.1.38 instead of 39 but by simply installing the mfc42.dll 
I was able to install e-sword 9.5 with no installer and it worked perfectly save the graphics viewer.

It works better than with the installer.

The credit for that trick goes to Jim on the puppy forums.

If anyone has an idea why i can't view the maps let me know. The viewer is there and the maps are there , I can switch between them but they don't display.

The method works as well in Puppy Linux , i imagine it will work in any Linux distro as long as you have the at least 1.1.38  

Anyone who can tell me how to install 1.1.39 please let me know, I think I followed all the instructions on winehq but I must have erred somewhere.

---

### Post by cmckdub on 2010-03-04
> **frank cox said:**
> 
Now for the good news. I got the program working on a new install with the installer.

I could only seem to install wine 1.1.38 instead of 39 but by simply installing the mfc42.dll 
I was able to install e-sword 9.5 with no installer and it worked perfectly save the graphics viewer.

It works better than with the installer.

The credit for that trick goes to Jim on the puppy forums.

If anyone has an idea why i can't view the maps let me know. The viewer is there and the maps are there , I can switch between them but they don't display.

I had a similar problem with the graphics viewer when I tried installing e-sword without the installer, and the best solution was to use the installer. (Thanks David)
The [work-around]("http://ubuntuforums.org/showpost.php?p=6433686&postcount=296") was to click on print preview, then click on a different map and back to the original. However such is hardly satisfactory. As I said the solution was to use the installer.;)

---

### Post by frank cox on 2010-03-06
> **cmckdub said:**
> I had a similar problem with the graphics viewer when I tried installing e-sword without the installer, and the best solution was to use the installer. (Thanks David)
The [work-around]("http://ubuntuforums.org/showpost.php?p=6433686&postcount=296") was to click on print preview, then click on a different map and back to the original. However such is hardly satisfactory. As I said the solution was to use the installer.;)

Thanks but it did not help. I uninstalled e-sword and then installed with the installer. 

At first it worked save the graphics again and then it lost the KJV and left me with the KJV w/ Apocrapha and then it said either eword was not installed or it was an older version .

I am about ready to wipe the drive and start over if I can't figure out how to get rid of traces of the previous install that must be causing me problems.  I can down loads maps and get by without them if I have to although I do like them.

I never have figured out how to use the installer in Puppy Linux which I use on dialup. 
It installs beautifully withoutit  and has other have no problem except with the graphics. I am wondering if it could be the driver for the graphics card. It did not help on this one. 

I don't have a printer on this machine at the moment to test your idea but I don't think I will like that as you said.

Thanks anyway, I appreciate you trying.

---

### Post by HellionDarkLord on 2010-03-27
I have been trying this myself with very little success.  Then I came across another post for another program installed with wine and that discussion says that desktop effects programs interfere with wine.  It causes things to become unstable in wine.  

Shut down compiz and try again from the beginning I hope that works for you!! I love esword and am using it to create my very own version of the bible for my own use using the HOT with strongs as much as I can.

This is a very helpful post I hope that shutting compiz down will solve your problems.

HD

---

### Post by Lemuel111 on 2010-04-11
I cannot get King James concordance or Brown Driver Briggs lexicon to install. Anyone had any success & if so any suggestions?

Thanks

---

### Post by david_kt on 2010-04-11
> **Lemuel111 said:**
> I cannot get King James concordance or Brown Driver Briggs lexicon to install. Anyone had any success & if so any suggestions?

Thanks
How did you install e-Sword?, If you are using the installer at the first post if this thread, then follow below steps:

[LIST=1]
[*]Download both add on and remember where you put it.
[*]Launch e-sword-installer and choose "Manual".
[*]Navigate to the add on you have downloaded.
[*]After finish installation, choose another add on.
[*]If all add on has been installed, choose cancel.
[/LIST]

Launch e-Sword, it should be installed properly now.

DK

---

### Post by Lemuel111 on 2010-04-12
Great stuff. Thanks for that.

---

### Post by angelsguitar on 2010-04-29
Hi.

I believe e-sword version has been upgraded to 9.6.0 . It may be necessary to upgrade the script, since the current one gives an error about not finding the previous version.

By the way, thanks for such a useful script.:)

Edit: Ok, I tried to edit the script manually and change the version references to 9.6.0 (setup960.exe). The script downloaded the installer, and ran it, but after finishing it displayed the following error:

"Esword_installer error: Note: command 'env WINEPREFIX=/home/angelsguitar/.wine_Esword wine /home/angelsguitar/.wineeswordcache/setup960.exe' returned status 194. Aborting"

I'm using Lucid Lynx with the latest wine (1.1.43).

---

### Post by david_kt on 2010-04-29
> **angelsguitar said:**
> Hi.

I believe e-sword version has been upgraded to 9.6.0 . It may be necessary to upgrade the script, since the current one gives an error about not finding the previous version.

By the way, thanks for such a useful script.:)

Edit: Ok, I tried to edit the script manually and change the version references to 9.6.0 (setup960.exe). The script downloaded the installer, and ran it, but after finishing it displayed the following error:

"Esword_installer error: Note: command 'env WINEPREFIX=/home/angelsguitar/.wine_Esword wine /home/angelsguitar/.wineeswordcache/setup960.exe' returned status 194. Aborting"

I'm using Lucid Lynx with the latest wine (1.1.43).

I have updated the script and test it with wine 1.0.1 on ubuntu karmic and it works. Could your try wine 1.0.1?

DK

---

### Post by jim64k on 2010-04-29
I can't download the script

appear the messaje "Invalid Attachment specified. If you followed a valid link, please notify the administrator"

---

### Post by david_kt on 2010-04-29
> **jim64k said:**
> I can't download the script

appear the messaje "Invalid Attachment specified. If you followed a valid link, please notify the administrator"

Sorry, I forgot to update link, now it is updated.

DK

---

### Post by jim64k on 2010-04-30
Now is fine, thank's

---

### Post by angelsguitar on 2010-04-30
> **david_kt said:**
> I have updated the script and test it with wine 1.0.1 on ubuntu karmic and it works. Could your try wine 1.0.1?

DK

Thanks, now it works. As you specified, I had to install wine 1.0.1 in Lucid Lynx. 

So Lucid Lynx users: be warned against using the latest development and/or recent version (wine 1.2 is also in Lucid Lynx's repos) at the moment. Only use wine 1.0 to avoid problems, at least for the moment.

David, as a suggestion, you can put a note about this in the first post.

Thanks again.

---

### Post by mtcycler on 2010-05-04
Just thought I would let 'yall know, it works fine in my install Ubuntu 10.04 LTS and Wine 1.2, e-Sword 9.6.0

---

### Post by GlennW on 2010-05-07
Hey all,

I've just followed the first post with the installer attempting to load e-sword onto my laptop. I'm running 10.04 having upgraded from 9.10. Wine installed fine, font smoothing went fine, checked all the addons that I needed and let the installer run its course. 

The desktop icon needed to be changed to executable. However, when double clicking either the desktop icon or Applications>Wine...>E-Sword, the cursor shows it's working for a couple of seconds and then quits. There's no message, nada.

I'm a bit new to all of this so any assistance would be appreciated. 

I agree with one of the previous posters that yes there other bible programs out there that run on linux but nothing like e-sword. 

Thanks.

---

### Post by GlennW on 2010-05-07
I thought I'd have a look at the desktop icon and its properties. I noticed this:

env WINEPREFIX="/home/glenn/.wine_Esword" wine "C:\Program Files\e-Sword\e-Sword.exe" 

The thing that caught my eye is that, after navigating to C:\Program Files\, the only thing in that folder is Common Files and Internet Explorer. 

Not knowing how Wine functions, does it somehow cause the exe in the /home folder to run?

I think there's a path issue.

Thanks for your help.

---

### Post by david_kt on 2010-05-07
> **GlennW said:**
> I thought I'd have a look at the desktop icon and its properties. I noticed this:

env WINEPREFIX="/home/glenn/.wine_Esword" wine "C:\Program Files\e-Sword\e-Sword.exe" 

The thing that caught my eye is that, after navigating to C:\Program Files\, the only thing in that folder is Common Files and Internet Explorer. 

Not knowing how Wine functions, does it somehow cause the exe in the /home folder to run?

I think there's a path issue.

Thanks for your help.

No, it is not path issue. Could you try to open terminal (Application >> Accessories >> terminal )

and then copy (ctrl + c) and paste to terminal ( ctrl + shifht + v) below command:


```
env WINEPREFIX="/home/glenn/.wine_Esword" wine "C:\Program Files\e-Sword\e-Sword.exe"
```

Check what is the output in terminal.

DK

---

### Post by backflip on 2010-05-08
I've had the same problem as GlennW and I've deleted twice already and tried for  re-installs. I may try again. I too thought the problem was related to the path, but it seems that may not be the case from what you write.
I'll keep my eye on the thread for a solution.

---

### Post by backflip on 2010-05-08
Well, that was quick, I tried yet again and got an'xmessage' stating  Esword_installer error: Note: command 'env WINEPREFIX=/home/james/.wine_Esword wine /home/james/.wineeswordcache/setup960.exe' returned status 194.  Aborting.  

When I clicked on the e-sword link icon it read ' Could not display "/home/james/Desktop/e-Sword.lnk".

When I clicked the e-sword desktop icon it stated 'Untrusted Application Launcher'.....The application launcher "e-Sword.desktop" has not been marked as trusted. If you do not know the source of this file, launching it may be unsafe.

When I run the command you suggested to GlennW in the terminal I get ..fixme:ole:OleLoadPictureEx (0xe5afdc,18910,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f970), partially implemented.
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\Codejock.Controls.v13.3.1.ocx"
err:ole:CoGetClassObject no class object {1ab6973d-11a7-47d2-af9d-43fcf80cee71} could be created for context 0x3
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\system32\\tx4ole14.ocx") not found
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\tx4ole14.ocx"
err:ole:CoGetClassObject no class object {15a32f01-b939-11dc-af58-0013d350667c} could be created for context 0x3
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\system32\\tx4ole14.ocx") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\system32\\tx4ole14.ocx") not found
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\tx4ole14.ocx"
err:ole:CoGetClassObject no class object {15a32f01-b939-11dc-af58-0013d350667c} could be created for context 0x3


I hope this helps.
Cheers
James

---

### Post by david_kt on 2010-05-08
> **backflip said:**
> Well, that was quick, I tried yet again and got an'xmessage' stating  Esword_installer error: Note: command 'env WINEPREFIX=/home/james/.wine_Esword wine /home/james/.wineeswordcache/setup960.exe' returned status 194.  Aborting.  

When I clicked on the e-sword link icon it read ' Could not display "/home/james/Desktop/e-Sword.lnk".

When I clicked the e-sword desktop icon it stated 'Untrusted Application Launcher'.....The application launcher "e-Sword.desktop" has not been marked as trusted. If you do not know the source of this file, launching it may be unsafe.

When I run the command you suggested to GlennW in the terminal I get ..fixme:ole:OleLoadPictureEx (0xe5afdc,18910,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f970), partially implemented.
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\Codejock.Controls.v13.3.1.ocx"
err:ole:CoGetClassObject no class object {1ab6973d-11a7-47d2-af9d-43fcf80cee71} could be created for context 0x3
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\system32\\tx4ole14.ocx") not found
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\tx4ole14.ocx"
err:ole:CoGetClassObject no class object {15a32f01-b939-11dc-af58-0013d350667c} could be created for context 0x3
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\system32\\tx4ole14.ocx") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\system32\\tx4ole14.ocx") not found
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\tx4ole14.ocx"
err:ole:CoGetClassObject no class object {15a32f01-b939-11dc-af58-0013d350667c} could be created for context 0x3


I hope this helps.
Cheers
James

If the installer give you error, you should repeat the installation. First, launch the installer and select clear remove cache. After that try install again, make sure no error during install.

DK

---

### Post by backflip on 2010-05-08
I tried again, after removing cache as you suggested, and got EXACTLY the same faults as in my previous post when the two desktop icons were clicked and the same xmessage appeared.


James

---

### Post by david_kt on 2010-05-08
> **backflip said:**
> I tried again, after removing cache as you suggested, and got EXACTLY the same faults as in my previous post when the two desktop icons were clicked and the same xmessage appeared.


James

Is the installer finished without error?

DK

---

### Post by backflip on 2010-05-08
I'm not entirely sure I understand you. The installation didn't throw up any difficulties and appeared to install, then the above xmessage splashed across my desktop. It seemed to go through the normal installation process, naming the folders where things were being installed etc and ended with 'finish.' When I clicked the two desktop icons I got the messages I reported earlier.
I've now completely removed e-sword from wine, but will try again if you come up with any remedy.
Thanks
James

---

### Post by david_kt on 2010-05-08
> **backflip said:**
> I'm not entirely sure I understand you. The installation didn't throw up any difficulties and appeared to install, then the above xmessage splashed across my desktop. It seemed to go through the normal installation process, naming the folders where things were being installed etc and ended with 'finish.' When I clicked the two desktop icons I got the messages I reported earlier.
I've now completely removed e-sword from wine, but will try again if you come up with any remedy.
Thanks
James

If you mean this message:

```
error: Note: command 'env WINEPREFIX=/home/james/.wine_Esword wine /home/james/.wineeswordcache/setup960.exe' returned status 194. Aborting. 
```

Then it is not completed. Try to downgrade to wine 1.0.1, and try to install it again and see if there any error during install.

DK

---

### Post by backflip on 2010-05-08
Thanks for your help, but I shan't bother downloading wine 1.0.1, I have Xiphos installed and I'll make do with that.
I have other applications which depend on the installed version of wine (1.1.42) and I don't want to risk having problems with them, either  through having an alternative version of wine or with having two versions installed.
I much appreciate your time and effort, but I'm too much of a nooby/coward to take chances with what is presently a very smooth running system (e-sword apart).
James

---

### Post by GlennW on 2010-05-08
@david_kt, sorry I didn't get back to you sooner. I appreciate that you took time to check this out. Here's the terminal output to that command:

env WINEPREFIX="/home/glenn/.wine_Esword" wine "C:\Program Files\e-Sword\e-Sword.exe"

fixme:ole:OleLoadPictureEx (0xe5afdc,18910,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f970), partially implemented.
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\system32\\tx4ole14.ocx") not found
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\tx4ole14.ocx"
err:ole:CoGetClassObject no class object {15a32f01-b939-11dc-af58-0013d350667c} could be created for context 0x3
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\system32\\tx4ole14.ocx") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\system32\\tx4ole14.ocx") not found
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\tx4ole14.ocx"
err:ole:CoGetClassObject no class object {15a32f01-b939-11dc-af58-0013d350667c} could be created for context 0x3

Thank you so very much for your attention to this.

---

### Post by david_kt on 2010-05-08
> **backflip said:**
> Thanks for your help, but I shan't bother downloading wine 1.0.1, I have Xiphos installed and I'll make do with that.
I have other applications which depend on the installed version of wine (1.1.42) and I don't want to risk having problems with them, either  through having an alternative version of wine or with having two versions installed.
I much appreciate your time and effort, but I'm too much of a nooby/coward to take chances with what is presently a very smooth running system (e-sword apart).
James

No, wine 1.0.1 is for installation purpose only. After installation completed, you could upgrade the wine back to latest wine.

DK

---

### Post by backflip on 2010-05-09
> **david_kt said:**
> No, wine 1.0.1 is for installation purpose only. After installation completed, you could upgrade the wine back to latest wine.

DK

I checked the synaptic package manager and I can download 1.0.1 from there. Would I need to remove my present version first or is it safe for me to install 1.0.1 alongside my present wine install and then remove it after E-sword is  finally running?  That would be my preferred option, I really don't want to delete my present version.
Thanks
James

---

### Post by david_kt on 2010-05-09
> **backflip said:**
> I checked the synaptic package manager and I can download 1.0.1 from there. Would I need to remove my present version first or is it safe for me to install 1.0.1 alongside my present wine install and then remove it after E-sword is  finally running?  That would be my preferred option, I really don't want to delete my present version.
Thanks
James

If you install it through synaptic, it would automatically remove the other version. You could not install both versions.

DK

---

### Post by backflip on 2010-05-09
> **david_kt said:**
> If you install it through synaptic, it would automatically remove the other version. You could not install both versions.

DK

Thanks, that did it, finally got E-sword installed. Your help was much appreciated.

James

---

### Post by GlennW on 2010-05-09
@david_kt. I ascertained that it indeed was not a path issue but a Wine version problem. As per the last few post, I uninstalled the latest version, went back to ver. 1.0 and did the install over again. Beautiful!

The icon that came with the installer was a bit hideous so I cleaned it up and added a drop shadow. Not bad...

Thanks for your help.

To all the Mommies out there - happy Mother's Day! Your efforts, although largely unnoticed, are so appreciated.

---

### Post by cepcer on 2010-05-14
That couldn't have been easier! I already had Wine installed on Ubuntu 9.1. I did the cabextract, the next step didn't work, so I skipped it. I went ahead and installed Esword with desired resources. It ran perfectly with no further intervention, so I downloaded more resources, including my purchased NASB, and installed manually without any trouble. It works perfectly! I still run Windows on my desktop, but was missing E-sword on my Ubuntu laptop. Thank you, thank you, thank you!

Courtney

---

### Post by geo316 on 2010-05-26
What pain... a whole day of trying to install everything...

I have a new laptop running 10.4, I downgraded Wine to 1.0 (as suggested here), I first tried to install using the script, then tried to restore a back up from my old desktop (which works fine), but nothing works.

I can usually get the installer to finish and e-Sword to actually run, but when I try to install my own downloaded books somewhere along the way e-Sword ceases to run. Interesting that I get no errors, after spending a whole lot of time installing I try to open e-Sword and it doesn't work anymore...

Anyone else having this issue? Any other way to install add on books besides through the installer script?

also, I hope I don't offend, but this forum is very painful to use. I get that the relevant info is in the first post, but troubleshooting becomes a very tedious process as one has to sort through posts from as far back as 2007, many of which are dead, irrelevant or off topic. Can a new thread be created for each new version?

Anyway - thanks in advance for help...

George

---

### Post by david_kt on 2010-05-26
> **geo316 said:**
> I get that the relevant info is in the first post, but troubleshooting becomes a very tedious process as one has to sort through posts from as far back as 2007, many of which are dead, irrelevant or off topic. Can a new thread be created for each new version?

Just read the first post and ask if you have problem. Could we try it step by step.

1. First, run the installer and select remove_ esword, remove_esword_default, and clear_cache. This is to ensure you have clean system to start with.

2. After that, run the installer again and select esword. MAke sure there is no error.

3. Launch e-Sword to see if it is ok.

DK

---

### Post by geo316 on 2010-05-27
> **david_kt said:**
> Just read the first post and ask if you have problem. Could we try it step by step.

1. First, run the installer and select remove_ esword, remove_esword_default, and clear_cache. This is to ensure you have clean system to start with.

2. After that, run the installer again and select esword. MAke sure there is no error.

3. Launch e-Sword to see if it is ok.

DK

David, just as before it installs just fine and runs just fine...

anticipating the next step I ran the installer again and selected several books to be added... again it finished and the app works...

---

### Post by geo316 on 2010-05-27
> **geo316 said:**
> David, just as before it installs just fine and runs just fine...

anticipating the next step I ran the installer again and selected several books to be added... again it finished and the app works...

OK... finally found my issue. It was a PBCK issue. That's "problem between chair and keyboard" :-)

Just as I experienced many times previously the basic install went ok, the addition of installer provided options was ok, but my own books tanked the install.

Apparently when copying over my downloaded books from my old computer I grabbed an older folder with the pre- 9x versions of some of the books. Once I copied over the new versions the entire install worked all the way to the end.

For what it's worth, if anyone has half a bazillion add on books like me I recommend verifying that e-Sword still works and even doing a backup from the installer every 3 or 4 book installs in case something goes wrong. That way you can revert to the last working state without having to start the install all over again.

Note that if you run "manual" from the installer, it always waits for you to give it the path to the next book to install. During this pause you can run e-Sword to verify that it still works, or even run another instance of the installer to backup, restore - even reinstall if need be. When done you can simply resume the previous instance and pick up where you left off.

All this probably wont be relevant to the majority of users, but I hope it helps someone save a little time...

George

---

### Post by geo316 on 2010-05-27
...and just a thought:

Can the install script be modified to allow you to do a batch install of manual add on books?

Instead of selecting a single file point it to a folder full of downloaded books to be installed...

That would be a huge time saver....

g

---

### Post by MissouriNewb on 2010-05-27
I read the instructions. I promise!

I installed wine from Synaptic first and followed all the other instructions. After I chose my addons it gave me an error message, which I ctrl+c'd and it didn't in fact copy.

So I went back into Synaptic chose a complete uninstallation of Wine and the config files.

Then I went to the Wine HQ page and did as directed and chose the latest Dev. I went to the Wine installer and double clicked and I saw this message in Terminal. I know the instructions stated that we were NOT to install this as root or sudo. But, is this message what it was referring to?

[ATTACH]158463[/ATTACH]

---

### Post by david_kt on 2010-05-27
> **MissouriNewb said:**
> I read the instructions. I promise!

I installed wine from Synaptic first and followed all the other instructions. After I chose my addons it gave me an error message, which I ctrl+c'd and it didn't in fact copy.

So I went back into Synaptic chose a complete uninstallation of Wine and the config files.

Then I went to the Wine HQ page and did as directed and chose the latest Dev. I went to the Wine installer and double clicked and I saw this message in Terminal. I know the instructions stated that we were NOT to install this as root or sudo. But, is this message what it was referring to?

[ATTACH]158463[/ATTACH]

What distribution you are using? Try to use wine stable (wine 1.0.1) I have just edited the instruction.
Anyhow, to install wine you have to use sudo/root. The instruction not to use root/sudo is for the script downloaded from the first post of this thread.

DK

---

### Post by MissouriNewb on 2010-05-27
1.2-rc1

Should I uninstall the latest dev and install 1.0?

BTW thanks very much David.

---

### Post by david_kt on 2010-05-27
> **MissouriNewb said:**
> 1.2-rc1

Should I uninstall the latest dev and install 1.0?

BTW thanks very much David.

Yes, install 1.0 and then try again the script and let me know if there is a problem.

DK

---

### Post by MissouriNewb on 2010-05-27
> **david_kt said:**
> Yes, install 1.0 and then try again the script and let me know if there is a problem.

DKI don't know how but I think I got it to work?

I did get this error message although

"Esword_installer error: Note: command 'env WINEPREFIX=/home/steve/.wine_esword/drive_c/home/steve/.wine_Esword wine /home/steve/ .wine_Esword/drive_c/wineswordtmp/cabinet.dll' returned status 1. Aborting"

Is This of any consequence?

Respectfully Submitted

MN

Gal. 2:20

---

### Post by david_kt on 2010-05-28
> **MissouriNewb said:**
> I don't know how but I think I got it to work?

I did get this error message although

"Esword_installer error: Note: command 'env WINEPREFIX=/home/steve/.wine_esword/drive_c/home/steve/.wine_Esword wine /home/steve/ .wine_Esword/drive_c/wineswordtmp/cabinet.dll' returned status 1. Aborting"

Is This of any consequence?

Respectfully Submitted

MN

Gal. 2:20

Not sure what that error is. Could you run e-Sword now? If yes, just ignore that error. If could not run, please re-download the script.

DK

---

### Post by MissouriNewb on 2010-05-28
> **david_kt said:**
> Not sure what that error is. Could you run e-Sword now? If yes, just ignore that error. If could not run, please re-download the script.

DKYes it is running well.

Thank you very much David, I and I am sure many others appreciate your sincere efforts.

Respectfully Submitted

MN

Gal. 2:20

---

### Post by jonathonblake on 2010-05-28
> **geo316 said:**
> 
Can the install script be modified to allow you to do a batch install of manual add on books?

The script can be so modified.  

> That would be a huge time saver.

If those files are self installing executables, self extracting executables, or have directory names included in the compressed archive, it takes longer to install them using a script, or set of scripts, than doing so manually.

jonathon

---

### Post by Akiviri on 2010-06-03
Hi

I'm fairly new to Ubuntu yet, and am having a problem with e-sword module add-ons. I got it installed just fine (TY for all your work) and after finding some Catholic modules [http://www.esnips.com/web/CatholicApolegetics](http://www.esnips.com/web/CatholicApolegetics) here, I've found I can't install them because they aren't .exe's. I can use the topx modules, they work just by dropping into the folder. But the rest, apparently, need to be installed. Any suggestions?

Kinda at a loss. I do get an error message, when I try to use the installer - but as I can't read all of it (any help?) i don't know what it is. I have tried changing permissions on the module (to run as .exe), just in case it might work, but - no help there.

P.S. the modules from e-sword loaded with the installer work fine also.
*edit - I'm using Ubuntu 10.4 and the newest e-sword...ummm..9.xxx something - lol.

Thanx for all your efforts

God Bless You

John

---

### Post by david_kt on 2010-06-03
> **Akiviri said:**
>  I got it installed just fine (TY for all your work) and after finding some Catholic modules [http://www.esnips.com/web/CatholicApolegetics](http://www.esnips.com/web/CatholicApolegetics) here, I've found I can't install them because they aren't .exe's
*edit - I'm using Ubuntu 10.4 and the newest e-sword...ummm..9.xxx something - lol.

Which add on do you want to install? Could you give me the exact link and name?
There are two version of e-Sword, old (version 8 and below) and new (version 9). You have to make sure it is the correct add on version.

DK

---

### Post by Akiviri on 2010-06-04
> **david_kt said:**
> Which add on do you want to install? Could you give me the exact link and name?
There are two version of e-Sword, old (version 8 and below) and new (version 9). You have to make sure it is the correct add on version.

DK


Hi 

TY for your response.

Yes, I have all the correct Modules. Here is a link to the download - [http://www.esnips.com/doc/83ac7a7d-5bdc-44b6-8361-028d57b4145c/Hebrew-English-Interlinear-esword-Bible-module-----SQLite-Data-base-for-Latest-Esword--9.0](http://www.esnips.com/doc/83ac7a7d-5bdc-44b6-8361-028d57b4145c/Hebrew-English-Interlinear-esword-Bible-module-----SQLite-Data-base-for-Latest-Esword--9.0) It's the Hebrew- English - Interlinear.
I tried using the .zip dowbload, as I said - no luck...and when I downloaded the e-snips downloader, using wine - it installed correctly, and seemed to be working (?) however, the download page didn't seem to recognize it regardless if it was open and running or not. So...

I had the same problem with it in windows occasionally, however.

Anyway - any help you could give will be appreciated

God Bless


John

---

### Post by david_kt on 2010-06-04
> **Akiviri said:**
> 
Yes, I have all the correct Modules. Here is a link to the download - [http://www.esnips.com/doc/83ac7a7d-5bdc-44b6-8361-028d57b4145c/Hebrew-English-Interlinear-esword-Bible-module-----SQLite-Data-base-for-Latest-Esword--9.0](http://www.esnips.com/doc/83ac7a7d-5bdc-44b6-8361-028d57b4145c/Hebrew-English-Interlinear-esword-Bible-module-----SQLite-Data-base-for-Latest-Esword--9.0) It's the Hebrew- English - Interlinear.
I tried using the .zip dowbload, as I said - no luck

Download the zip file, and then download [the attached script]("http://ubuntuforums.org/attachment.php?attachmentid=159297&stc=1&d=1275630506")

Right click and choose "Extract here" and double click on the extracted file and choose run.

It will open a window for you to select the downloaded zip file, one file at a time.
Click cancel if you have completed all the zip file zip have downloaded.

The zip modules should be installed now.

DK

---

### Post by Akiviri on 2010-06-04
> **david_kt said:**
> Download the zip file, and then download [the attached script]("http://ubuntuforums.org/attachment.php?attachmentid=159297&stc=1&d=1275630506")

Right click and choose "Extract here" and double click on the extracted file and choose run.

It will open a window for you to select the downloaded zip file, one file at a time.
Click cancel if you have completed all the zip file zip have downloaded.

The zip modules should be installed now.

DK

Hi

Worked perfectly. Thank-You Very Much :):):)

God Bless You

John

---

### Post by bkcyberfreak on 2010-06-07
Worked peferctly fine for me. Thank you very much for your work.

Greets, BKC

---

### Post by Eladon on 2010-06-13
Been googling and reading posts here for hours, still not sure if there's any solution to this...

I installed Wine 1.0.1 from repositories on a Lucid system, followed the instructions to install E-Sword, upgraded Wine to the new repository release 1.1.42  and no problems, E-Sword runs fine.

Unfortunately the Hebrew fonts are messed up making the Hebrew versions unusable.  Some letters mushed together, some far apart, sometimes words are mixed up and the verse references are in the wrong place.

Any ideas how to fix this?

---

### Post by jonathonblake on 2010-06-13
> **Eladon said:**
> 
Unfortunately the Hebrew fonts are messed up making the Hebrew versions unusable

a) Which Hebrew resources does this occur with?
b) Which Hebrew fonts are you using?

jonathon

---

### Post by Eladon on 2010-06-14
> a) Which Hebrew resources does this occur with?
HOT & HOT+, and HOT+ is really messed up.
> b) Which Hebrew fonts are you using?
It says "TITUS Cyberbit".  Since you mentioned it, I found Ezra SIL and tried it too, but same issue.

---

### Post by Eladon on 2010-06-15
I found the answer to my question, while surfing for alternatives!

I found a program that actually does exactly what I was looking for, called "Interlinear Scripture Analyzer" (ISA), which I loaded up into a WinXP virtual machine, and it's awesome:
[http://www.scripture4all.org/]("http://www.scripture4all.org/")

Even found some instructions for Ubuntu here:
[http://www.scripture4all.org/ISA2_help/FAQ/ISA_faq.htm#ISAandLinux]("http://www.scripture4all.org/ISA2_help/FAQ/ISA_faq.htm#ISAandLinux")

Unfortunately the instructions were for Wine 0.9.59.  I tried getting it going but couldn't.  But in them was a hint to get the Hebrew working in that program:
> For using the Hebrew right-to-left the USP10.DLL is needed and copied to drive_c/windows/system32 of your .wine folder.
I tried this for E-Sword, and added the dll override into the wine config, and lo and behold the Hebrew works great now!  (I used a copy of the dll from my virtual machine, but probably it's available from a dll repository too).  I definitely recommend adding this to your installation process!

The down side is, now I'm also hooked on ISA.  If only someone knew how to get that program working... 8-)

---

### Post by david_kt on 2010-06-16
> **Eladon said:**
> I found the answer to my question, while surfing for alternatives!

I found a program that actually does exactly what I was looking for, called "Interlinear Scripture Analyzer" (ISA), which I loaded up into a WinXP virtual machine, and it's awesome:
[http://www.scripture4all.org/]("http://www.scripture4all.org/")

Even found some instructions for Ubuntu here:
[http://www.scripture4all.org/ISA2_help/FAQ/ISA_faq.htm#ISAandLinux]("http://www.scripture4all.org/ISA2_help/FAQ/ISA_faq.htm#ISAandLinux")

Unfortunately the instructions were for Wine 0.9.59.  I tried getting it going but couldn't.  

Please use wine 1.0.1 for ISA.

DK

---

### Post by Eladon on 2010-06-17
> Please use wine 1.0.1 for ISA.

Hi DK, thanks for the help!

Unfortunately that didn't work for me.  I tried Wine 1.0.1, 1.1.42, and the latest 1.2 beta, and they all install fine but give the following error message a couple times when you run the program, then it dies:
```
Application Error
Exception EAccessViolation in module ISA.exe at 0032FF3D.
Access violation at address 0072FF3D in module 'ISA.exe'. Read of address 0000000C.

```
Maybe you are using an older version of ISA that still works?  The one on their web page is v 2.1.3

---

### Post by david_kt on 2010-06-17
> **Eladon said:**
> Hi DK, thanks for the help!

Unfortunately that didn't work for me.  I tried Wine 1.0.1, 1.1.42, and the latest 1.2 beta, and they all install fine but give the following error message a couple times when you run the program, then it dies:
```
Application Error
Exception EAccessViolation in module ISA.exe at 0032FF3D.
Access violation at address 0072FF3D in module 'ISA.exe'. Read of address 0000000C.

```
Maybe you are using an older version of ISA that still works?  The one on their web page is v 2.1.3

I have upgraded to v 2.1.3, and it is still working as normal. Try this:

```
rm -R ''HOME'/.wine/drive_c/Program Files/ISA2'
```

And then install ISA2.

DK

---

### Post by Eladon on 2010-06-20
Wow, after way too much troubleshooting, I found out that the only way to get the program to run is by having the current working directory in the same path as the ISA.exe.  

So I installed ISA to a separate wine profile like so:
```
$ cd /to/wherever/ISA/installer/is/
$ env WINEPREFIX="$HOME/.wine_ISA" wine ISA_basic_v2_1_3.exe
```

Then I made my launcher using the following command:
```
bash -c "cd \"$HOME/.wine_ISA/drive_c/Program Files/ISA2/\" ; env WINEPREFIX=$HOME/.wine_ISA wine \"C:/Program Files/ISA2/ISA.exe\""
```

And voila, it works!

Subsequently I put a copy of usp10.dll into the system32 directory (~/.wine_ISA/drive_c/windows/system32), ran the winecfg as follows:
```
$ env WINEPREFIX=$HOME/.wine_ISA winecfg
```
and then added usp10 into the Libraries DLL overrides.

I even took a copy of the font_smoothing script from here, and changed the appropriate line in the script as follows, and was able to use it to turn font smoothing on for ISA!
```
WINEPREFIX=${WINEPREFIX:-$HOME/.wine_ISA}
```

On top of all of this, I was able to upgrade my Wine to 1.1.42 and everything still works great!  Yay!

---

### Post by Chupipe on 2010-06-22
Hi!


Well, after many attemps to get E-Sword 9 working I found a way to make it work, I know that many of you might have used these way, but I wn¿ant to contribute:

1.- First I installed Wine 1.1.42

2.- Then I copied the following dll's to the windows/system32 folder of wine:

I.- msls31.dll
II.- riched20.dll
III.- riched32.dll
IV.- oleaut32.dll
V.- When I tried to run E-Sword from the terminal it said it needed a dll, which was mfc42.dll, so I copied it to the system32 folder.

3.- I ran E-Sword from the terminal but it said it couldn't find the e-sword.exe (it wa trying to run it from the system32 folder), so I copied the e-sword.exe to the system32 folder, tried again to run it and it ran!! It runs smoothly without any font-viewing problems. My computer is slow, but it works pretty well.

Well, that's the way i got it to work, I hope this can be helpful! And thanks for all your comments which have helped me a lot.

God bless you!

---

### Post by Cityscape on 2010-07-13
Okay, there are 67 pages now in this thread and tons of different advice. Could someone point me to which way is best for installing a modern version of eSword (9.x)?

I heard Ubuntu CE was supposed to make it easy to install eSword, how does that work?

---

### Post by david_kt on 2010-07-13
> **Cityscape said:**
> Okay, there are 67 pages now in this thread and tons of different advice. Could someone point me to which way is best for installing a modern version of eSword (9.x)?

I heard Ubuntu CE was supposed to make it easy to install eSword, how does that work?

Please try the installer at the first post of this page first.

DK

---

### Post by Scott Neolife on 2010-08-02
Thank you for making this available, e-sword installed easily and is working well.;)

---

### Post by manney on 2010-09-02
Sorry jonathonblake, I did not know that I had to start a new thread to ask a question.  I suppose it should have been obvious to me considering my question had nothing to do with s-sword.  Again I Apologize.

---

### Post by jonathonblake on 2010-09-03
> **manney said:**
> Have any of you tried the word from [http://theword.gr/](http://theword.gr/)

The thread for issues in installing that program can be found at [http://ubuntuforums.org/showthread.php?t=400170](http://ubuntuforums.org/showthread.php?t=400170)

[http://ubuntuforums.org/showthread.php?t=1282936](http://ubuntuforums.org/showthread.php?t=1282936) is where it was suggested being included in the Wine Christian Repository.

If you want to discuss that program, do so in another thread.  Do not hijack, or attempt to hijack threads.

jonathon

---

### Post by ubunterooster on 2010-09-18
There have been other threads showing how to install e-sword but this one still works best for me.

---

### Post by bushpilot on 2010-10-03
Worked great, no problems, including the font smoothing.  Thank you.

Greg

---

### Post by ubunterooster on 2010-10-10
[COLOR=Red]Thread No longer Valid!
[/COLOR]

See: [http://ubuntuforums.org/showthread.php?p=9947567#post9947567](http://ubuntuforums.org/showthread.php?p=9947567#post9947567)

---

### Post by david_kt on 2010-10-10
> **ubunterooster said:**
> [COLOR=Red]Thread No longer Valid!
[/COLOR]

See: [http://ubuntuforums.org/showthread.php?p=9947567#post9947567](http://ubuntuforums.org/showthread.php?p=9947567#post9947567)

I have updated the installer, now it is not hard-coded to any version. It would check latest version of e-Sword, download and install it. So, in future, if there is new version released, the same installer could be used. There is no need to edit or download new installer.

DK

---

### Post by ubunterooster on 2010-10-10
Thanks! :D

---

### Post by Nathanael Culver on 2010-10-13
On Ubuntu 10.10, Wine 1.1.42, the install script died with:

```
Connecting to e-sword.net|208.67.58.170|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `downloads.html'

    [  <=>                                  ] 9,559       31.1K/s   in 0.3s    

2010-10-14 00:58:04 (31.1 KB/s) - `downloads.html' saved [9559]

Executing env WINEPREFIX=/home/nathanael/.wine_Esword wine /home/nathanael/.wineeswordcache/setup972.exe
Note: command 'env WINEPREFIX=/home/nathanael/.wine_Esword wine /home/nathanael/.wineeswordcache/setup972.exe' returned status 129.  Aborting.

```

Downloaded setup972.exe manually and attempted to work through the manual install described in the initial post. When I got to 

```
env WINEPREFIX=~/.wine_Esword wine setup972.exe
```

I got:

```
wine: cannot find L"C:\\windows\\system32\\setup972.exe"
```

So I tried the following:

```
cp setup972.exe ~/.wine/drive_c/windows/system32
wineprefixcreate --prefix .wine_Esword
cd~/.wineeswordcache
wine setup972.exe
```

and got "Error reading setup initialization file".

Then I gave up.

--Nathanael

---

### Post by ubunterooster on 2010-10-13
I gave a link to my alternate script here: [http://ubuntuforums.org/showthread.php?p=9947567#post9947567](http://ubuntuforums.org/showthread.php?p=9947567#post9947567)

See if that works

Edit: might not due to yet another update :(

---

### Post by david_kt on 2010-10-13
> **Nathanael Culver said:**
> 

Downloaded setup972.exe manually and attempted to work through the manual install described in the initial post. When I got to 

```
env WINEPREFIX=~/.wine_Esword wine setup972.exe
```

So I tried the following:

```
cp setup972.exe ~/.wine/drive_c/windows/system32
wineprefixcreate --prefix .wine_Esword
cd~/.wineeswordcache
wine setup972.exe
```

and got "Error reading setup initialization file".

Then I gave up.

--Nathanael

Most likely due to failed download. If the manual download successfull, try:
```
cp -f setup972.exe ~/.wineeswordcache
```

and then launch the installer.

OR, launch the installer and choose clear_cache, and relaunch the installer.

DK

---

### Post by david_kt on 2010-10-13
> **ubunterooster said:**
> I gave a link to my alternate script here: [http://ubuntuforums.org/showthread.php?p=9947567#post9947567](http://ubuntuforums.org/showthread.php?p=9947567#post9947567)

See if that works

Edit: might not due to yet another update :(

Hard link to 971 will not work for 972. Please use the installer at the first post of this thread, should work for any version of e-sword, including future releases.

DK

---

### Post by dbain25 on 2010-11-18
I consider myself still somewhat a ubuntu noob, but I was able to install e-sword with these directions. I thank you very much, as this will greatly help with my devotional life.

Thank you, thank you, thank you...

- D

---

### Post by jeff3211 on 2010-12-09
Thank You very much for this tutorial on proper installation of e-sword. I had already tried to install with no success using 10.4 ubuntu with wine 1.2 . Your directions to use 1.0.1 made it possible to create a useful installation. I had to remove wine 1.2 with the package manager, and replace it with the 1.0.1 version, then when I went to run the terminal I was advised that there were unused packages remaining and I used "sudo apt-get autoremove" as instructed by the terminal messages to remove the packages that remained which were associated with wine 1.2 I then used wine config in the 1.0.1 version and removed the e-sword installation which seemed stubbornly anchored in the wine menus. Once removed with wine config, it was actually gone. Then I was able to follow the tutorial and install e-sword per your instructions. It sounded more difficult than it really turned out to be, your instructions were succinct, accurate and easy to follow! I am happy to be learning more about linux, and the Word all at the same time!!! Thanks again!

---

### Post by Diolectic on 2010-12-22
I don't know if this was asked already, but how/where could I download more bibles/commentaries/dictionaries?
Thanks...

BTW... tutorial was excellent, installed easily.

---

### Post by david_kt on 2010-12-22
> **Diolectic said:**
> I don't know if this was asked already, but how/where could I download more bibles/commentaries/dictionaries?


Di you use [e-sword installer]("http://ubuntuforums.org/attachment.php?attachmentid=171842&d=1286730861") to install e-Sword? If yes, re-launch e-sword installer and you could see selected bibles/commentaries/dictionaries there, just tick on the ones you like, as many as you want. It would download and install it for you.

DK

---

### Post by Diolectic on 2010-12-23
> **david_kt said:**
> Di you use [e-sword installer]("http://ubuntuforums.org/attachment.php?attachmentid=171842&d=1286730861") to install e-Sword? If yes, re-launch e-sword installer and you could see selected bibles/commentaries/dictionaries there, just tick on the ones you like, as many as you want. It would download and install it for you.

DKThanx for the reply, Yes I have all the available bibles etc... however, there is no choice of the others that are available from [http://www.e-sword.net/bibles.html](http://www.e-sword.net/bibles.html).
I've also have some that are paid for in the MS Windows E-sword; how may I (at least) get all the others that are free?

Thanx

---

### Post by david_kt on 2010-12-23
> **Diolectic said:**
> Thanx for the reply, Yes I have all the available bibles etc... however, there is no choice of the others that are available from [http://www.e-sword.net/bibles.html](http://www.e-sword.net/bibles.html).
I've also have some that are paid for in the MS Windows E-sword; how may I (at least) get all the others that are free?

Thanx

Yes you could install all of that, including the paid ones. Actually I have explain it at the first post if this thread, which is step no. 4:

4. Install other addon 
If the addon you want to install is not in the installer, please download the exe file first. After that, run the e-Sword_installer and tick manual option (no. 4 from the top). It will open a browser for you to locate your addon, select that exe file and click ok to install.

If you already have it on other computer, just copy over the exe file.

DK

---

### Post by Diolectic on 2010-12-28
> **david_kt said:**
> Yes you could install all of that, including the paid ones. Actually I have explain it at the first post if this thread, which is step no. 4:

4. Install other addon 
If the addon you want to install is not in the installer, please download the exe file first. After that, run the e-Sword_installer and tick manual option (no. 4 from the top). It will open a browser for you to locate your addon, select that exe file and click ok to install.

If you already have it on other computer, just copy over the exe file.

DKThank you for your help, all went smoothly.

---

### Post by Caraibes on 2010-12-31
It had been a couple of years I had been running both e-Sword & the Word natively in Windows 7 on other computers... (maybe you remember me from that time...)

Since November, I inherited an older MacBook 2.1, got rid of the older OSX 10.4 for Lucid, in single boot.

As of my Bible needs, I was running Xiphos, it is a good app. Occasionally Bibletime as well, but it doesn't display too nice in Gnome/LXDE/Fluxbox...

Finally today I re-installed e-Sword with this thread's script, and it works like a charm, thank you very much David, God bless you generously for helping the brothers & sisters out there running Ubuntu...

---

### Post by platinumYeti on 2011-01-02
This is the xmessage error I'm receiving.

"Esword_installer error: sha1sum mismatch!  Rename /home/thera/.wineeswordcache/./setup981.exe and try again."

This is using Wine 1.0.1.

Any help would be much appreciated!

---

### Post by bob2011 on 2011-01-03
> **platinumYeti said:**
> This is the xmessage error I'm receiving.
 
"Esword_installer error: sha1sum mismatch! Rename /home/thera/.wineeswordcache/./setup981.exe and try again."
 
This is using Wine 1.0.1.
 
Any help would be much appreciated!
 
I have the same problem here.

---

### Post by david_kt on 2011-01-03
There is a change at the download page of e-Sword, I have make some improvement of the script. Please download it from the first post of this thread, or direct link [here]("http://ubuntuforums.org/attachment.php?attachmentid=179982&d=1294055596")

I could not fine the download link for other modules but the files is still thee so as you could use the installer to install selected modules. I think Rick is doing some more changes in near future so as I might need to edit the installer again.

DK

---

### Post by slashell on 2011-01-04
I just used the info on the first page of this (now very long) post and e-sword installed like a charm under Ubuntu 10.04 with Wine 1.2.

Thanks for all your work!

---

### Post by jonathonblake on 2011-01-05
> **Caraibes said:**
> Finally today I re-installed e-Sword with this thread's script, and it works like a charm, 

Did you use the script to install e-Sword on your Mac system, or on your Ubuntu system?

jonathon

---

### Post by bob2011 on 2011-01-08
> **david_kt said:**
> There is a change at the download page of e-Sword, I have make some improvement of the script. Please download it from the first post of this thread, or direct link [here]("http://ubuntuforums.org/attachment.php?attachmentid=179982&d=1294055596")
 
I could not fine the download link for other modules but the files is still thee so as you could use the installer to install selected modules. I think Rick is doing some more changes in near future so as I might need to edit the installer again.
 
DK
 
Works fine now with the new installer.
 
Thanks very much,
God Bless you,
 
Bob :D

---

### Post by Dailey on 2011-01-14
Can confirm the new installer also works with Debian.

Words do not express how grateful I am to have access to this great software on all of my machines.  Thank you for your labor of love & desire to be a part of something that will not be destroyed.

Hold Fast.
D.

---

### Post by frank cox on 2011-02-01
The installer works even better now!

---

### Post by frank cox on 2011-02-01
The problem I have now is not with the installer . When I try to download from the program it lists the available downloads but no dice on making the links work.
Guess I will have to use windows to download as I see no way to download from the site any more save the main program.

---

### Post by frank cox on 2011-02-01
I downloaded the desired modules with Esword in windows but when I tried to install them with I get this error message:
               Esword_installer error: Note: command 'env WINEPREFIX=/home/User/.wine_Esword wine /media/Dual-Use-2/Esword/abs.mapx' returned status 193.  Aborting

---

### Post by david_kt on 2011-02-01
> **frank cox said:**
> I downloaded the desired modules with Esword in windows but when I tried to install them with I get this error message:
               Esword_installer error: Note: command 'env WINEPREFIX=/home/User/.wine_Esword wine /media/Dual-Use-2/Esword/abs.mapx' returned status 193.  Aborting

I need to update the installer for addon as Rick has move the file and change it to database file instead of exe file. If you have downloaded it in windows, just copy it over to the directory of e-Sword you install, probably ~/.wine_Esword/drive_c/Program Files/

DK

---

### Post by polarise on 2011-02-18
Hi,

First of all, thanks for your instructions. Worked like a charm and I have ISA running.

Question: where do you get the usp10.dll file from?

Paul

---

### Post by ricgal on 2011-02-23
Thank you for the installer. I had tried to install just using wine, but files were missing; could not get past gearsec.exe but when  I used your installer script it ran just fine.
I took the advice of another user and moved the extracted file into a esword_installer folder in the .wine/drive_c folder.

I am using lucid 10.04 64bit.

---

### Post by david_kt on 2011-02-26
Now you could install addons using the installer. In case you have addons from windows (not exe file), you could install it as well using manual option.

DK

---

### Post by Ventriloquist on 2011-03-07
I am trying to run E-sword installer.  When I open e-sword installer with the Archive mounter it brings up a new drive on my desk top.  I right click that new drive and hit properties.  I get the message that the permissions could not be determined.

I am trying to add a bible file gnt.tr.exe to my bible program but have not had any success.

Please help
Ventriloquist

---

### Post by david_kt on 2011-03-07
> **Ventriloquist said:**
> I am trying to run E-sword installer.  When I open e-sword installer with the Archive mounter it brings up a new drive on my desk top.  I right click that new drive and hit properties.  I get the message that the permissions could not be determined.

I am trying to add a bible file gnt.tr.exe to my bible program but have not had any success.

Please help
Ventriloquist

Did you install e-Sword using this installer or other method?

DK

---

### Post by Ventriloquist on 2011-03-08
I installed E-sword 9.5.1 with other method.  Trying to install new E-sword but have not been able to get the job don.  I tried again today and this is the message that I get.

Archive:  /home/office/Desktop/setup983.exe
[/home/office/Desktop/setup983.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /home/office/Desktop/setup983.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /home/office/Desktop/setup983.exe or
          /home/office/Desktop/setup983.exe.zip, and cannot find /home/office/Desktop/setup983.exe.ZIP, period.

Any Ideas.
Ventriloquist
P.S. thanks for getting back to me.  :-)

---

### Post by Ventriloquist on 2011-03-08
> **Ventriloquist said:**
> I installed E-sword 9.5.1 with other method.  Trying to install new E-sword but have not been able to get the job don.  I tried again today and this is the message that I get.

Archive:  /home/office/Desktop/setup983.exe
[/home/office/Desktop/setup983.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /home/office/Desktop/setup983.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /home/office/Desktop/setup983.exe or
          /home/office/Desktop/setup983.exe.zip, and cannot find /home/office/Desktop/setup983.exe.ZIP, period.

Any Ideas.
Ventriloquist
P.S. thanks for getting back to me.  :-)

I stopped trying to use E-sword installer and just use wine and finally got my program e-sword up to date.  Now the download opens up in a new window but it does not work like it does in windows.  It does not mark the file in the bottom of the box and show up as you download it.  We need a file for Ubuntu to fix this problem.  

Ventriloquist

---

### Post by david_kt on 2011-03-09
> **Ventriloquist said:**
> I stopped trying to use E-sword installer and just use wine and finally got my program e-sword up to date.  Now the download opens up in a new window but it does not work like it does in windows.  It does not mark the file in the bottom of the box and show up as you download it.  We need a file for Ubuntu to fix this problem.  

Ventriloquist

Unfortunately the download function is not working. Either you copy it manually from windows or use the installer to download addons. But you have to use the installer as well to install e-sword in case you want to download addons using this installer.

DK

---

### Post by jeff.biggeek02 on 2011-03-16
I wanted to share a few tips for getting this to work in Linux.  I had trouble getting both e-sword and Amazon Kindle for PC to work under wine.  E-sword complained about missing dependencies for tx4ole14.ocx (which is a TX Text Control component), and Kindle just didn't load.  The Kindle error was a problem with a COM component, as well as a fixme error for system:SetProcessDPIAware.

I am posting because what fixed this for me was very surprising.  Here's what I did.

After some frustrating attempts, I finally blew away all files/folders in my ~/.wine prefix, and tried again (Aside: I should have made an e-sword specific prefix like is mentioned earlier in this post.  That is a better way to do things, if you're worried about other apps breaking e-sword).

After blowing it away, I downloaded winetricks (a script that helps to install common windows libraries such as the .NET framework or MFC, Visual C++ redistributables, etc).  The first time I ran winetricks, it told me that it couldn't find Gecko, and wanted to download it for me automatically.  I let it, but unfortunately that didn't work.  So I blew away my prefix again (see above) and followed some instructions online on manually downloading it for my version of wine ([http://wiki.winehq.org/Gecko](http://wiki.winehq.org/Gecko)).

Once I did that and ran winetricks, winetrick's menu came up rather than complaining about not finding Gecko as it did before.  Ok, that's a good thing.  On to the next problem.

I knew from some forum posts that e-sword's TX Text Control dependency apparently needed MFC42 installed to work.  I used winetricks to install that.  Once I did that, I ran the e-sword installer, then ran the link it put on my desktop.  To my surprise, no TX Text Control error!  Everything works great!

I remembered from a few months back that Kindle for PC was having problems for me in Wine, so I thought I'd install that for kicks too.  Sure enough, it now works just fine by simply running the installer!

So, the moral of the story is that some apps seem to need Gecko installed, and winetricks to setup their dependencies before you ever run the installer for them in Wine.  That was my experience anyhow, and corrected two major issues for me.  Yes!

By the way, I am Linux for life, now.  I switched over about 8 months ago and never looked back.  Getting these two apps going really sells me on the switch.  I have absolutely no reason to dual boot Windows now.  Open source has really came a long way since my last attempt to use it in 2005 or so.  I am a developer, and look forward to contributing to this community!

---

### Post by david_kt on 2011-03-16
> **jeff.biggeek02 said:**
> 
So, the moral of the story is that some apps seem to need Gecko installed, and winetricks to setup their dependencies before you ever run the installer for them in Wine.  That was my experience anyhow, and corrected two major issues for me.  Yes!


Are you able to download addons using e-Sword in linux?

DK

---

### Post by jeff.biggeek02 on 2011-04-03
Yes, the module functionality in e-sword does work for me.

---

### Post by david_kt on 2011-04-03
> **jeff.biggeek02 said:**
> Yes, the module functionality in e-sword does work for me.

Could you give me a snap shoot of module downloader downloading addons?

DK

---

### Post by rob4Christ on 2011-04-16
Thanks Jeff, DK and ventriloquist,

I got e-sword running thanks to your help. I just did 3 steps:

run Winetricks and install vcrun6.
in terminal: 
cd ~/.wine/drive_c/windows/system32

regsvr32 tx4ole14.ocx

then try E-sword again.  hope this works for you..

God Bless!!

Rob

---

### Post by Pepe Lebuntu on 2011-04-22
Hi there,

I'm trying to get the Editor's default font to change (Options>Editor Options>Default Font), but the box won't come up for me to change it. Any ideas?

---

### Post by Mickeyj4j on 2011-04-27
I just want to say that as far as i know any portable version of e-sword is not official and is not supported by e-sword. i notice there is one attached to this post.

---

### Post by My_World on 2011-04-29
> 
--2011-04-29 13:36:33--  [http://www.e-sword.netdownloads.html/](http://www.e-sword.netdownloads.html/)
Resolving [www.e-sword.netdownloads.html](www.e-sword.netdownloads.html)... failed: Name or service not known.
wget: unable to resolve host address `[www.e-sword.netdownloads.html](www.e-sword.netdownloads.html)'

Is the script still being maintained? Seems the wget command is not perfect.
:p

---

### Post by david_kt on 2011-04-29
> **My_World said:**
> Is the script still being maintained? Seems the wget command is not perfect.
:p

Please download the latest script, there was a problem with wget. But not sure which one ( wget of e-sword server) caused the change.

DK

---

### Post by My_World on 2011-04-30
Thank you kind sir, that was very speedy indeed!

---

### Post by ubume2 on 2011-05-04
I run E-Sword on a Desktop. Lately on several installs I no longer get the blue E-Sword launcher, but a wine gobblet.

One post indicated that the png file at the end of david_kt's tutorial could be used.  It is not a launcher.

Is there a way to get that launcher?

It started happening on a second install of 10.04 and now on 10.10 and 11.04.

E-Sword is a fantastic program, but I do miss that nice looking launcher on my Desktop.

Thanks

---

### Post by david_kt on 2011-05-04
> **ubume2 said:**
> I run E-Sword on a Desktop. Lately on several installs I no longer get the blue E-Sword launcher, but a wine gobblet.

One post indicated that the png file at the end of david_kt's tutorial could be used.  It is not a launcher.

Is there a way to get that launcher?

It started happening on a second install of 10.04 and now on 10.10 and 11.04.

E-Sword is a fantastic program, but I do miss that nice looking launcher on my Desktop.

Thanks
 
1. download the png file and remember where you save it
2. right click on e-sword launcher and choose properties
3. click on the wine goblet and navigate to png file on step 1.

DK

---

### Post by danti on 2011-05-04
I have a couple modules I'd like, but can't get them to work:

#1) The Complete Apostle's Bible module - This one I downloaded from e-sword-users.net, and I can run through the steps in Wine, but in the end, it doesn't show up in e-sword.

#2) The Apostolic Bible Polyglot - This one appears as a downloadable module in e-sword module downloader, but it looks like it can't be installed that way.

Thanks for your help.

---

### Post by jonathonblake on 2011-05-04
> **danti said:**
> #1) The Complete Apostle's Bible module - This one I downloaded from e-sword-users.net, and I can run through the steps in Wine, but in the end, it doesn't show up in e-sword.

Which directory does WINE install it in?
Which directory does e-Sword look for e-Sword Bibles in?

Do you have any resources that display "CAB" in the tab?
Do you have any resources that display "Complete Apostles Bible" in the tab?

My guess is that either it is not installed in the directory that e-Sword looks for Bibles, or you have at least two resources that contain the same content in the abbreviation field of the description table.

> #2) The Apostolic Bible Polyglot - This one appears as a downloadable module in e-sword module downloader, but it looks like it can't be installed that way.

In e-Sword 9.9.0, it can be downloaded, by clicking on it, and then clicking on the "download" button in the resource manager.    
In e-Sword 9.8.x, it could be downloaded and correctly installed using the download manager, but it was prone to failure.  
In e-Sword 9.7.2, and earlier versions, you had to download and install it manually.

jonathon

---

### Post by ubume2 on 2011-05-04
> **david_kt said:**
> 1. download the png file and remember where you save it
2. right click on e-sword launcher and choose properties
3. click on the wine goblet and navigate to png file on step 1.

DK

Thanks.  Works great!

---

### Post by danti on 2011-05-05
Jonathan,
Thanks, I have gotten both of those in now.

When I first went to install the Apostolic Polyglot, I clicked it & it seemed to do nothing - but I guess I was actually just selecting it & needed to use the "start download" menu item to get it to install.

The Complete Apostle's Bible: When I run through this in the Wine installer, it only gives me the option of C:\Program Files\e-sword, so I didn't know what I should do with that. So after installing, I cut & paste the file over the wine_esword directory & that worked.

---

### Post by ScottyK7 on 2011-05-08
> **rob4Christ said:**
> Thanks Jeff, DK and ventriloquist,

I got e-sword running thanks to your help. I just did 3 steps:

run Winetricks and install vcrun6.
in terminal: 
cd ~/.wine/drive_c/windows/system32

regsvr32 tx4ole14.ocx

then try E-sword again.  hope this works for you..

God Bless!!

Rob
Wanted to give a big shout out to Rob4Christ! The steps he listed was exactly what I needed to get E-Sword working again. 

I'm running Kubuntu 10.10 with Wine version 1.2.2 and E-Sword version 9.9.0 

The big hang up was wine looking for mfc42.dll file that was required by tx4ole14.ocx

---

### Post by BlueVark on 2011-05-10
Upgraded to e-Sword version 9.9.0 via the script and everything went great.  Thanks again for a great script, but one problem...now my bible search won't work.  It will not return any results for any text using any bible.  Nada, nothing works.  Search works for commentary, dictionary, and notes, but not for bible.  Any ideas why?

---

### Post by david_kt on 2011-05-10
> **BlueVark said:**
> Upgraded to e-Sword version 9.9.0 via the script and everything went great.  Thanks again for a great script, but one problem...now my bible search won't work.  It will not return any results for any text using any bible.  Nada, nothing works.  Search works for commentary, dictionary, and notes, but not for bible.  Any ideas why?

Make sure you select the bible with the same language you search.

DK

---

### Post by jonathonblake on 2011-05-10
> **BlueVark said:**
> now my bible search won't work. 

Known issue. The VBScript.DLL is not getting correctly registered.

If you use CrossOver, the fix is to rebuild the bottle.

I haven't fixed it using WINE, yet.  (I'm chasing down other bugs in e-Sword 9.9.0, completed with screen shots and log files.)

jonathon

---

### Post by BlueVark on 2011-05-10
Thanks Jonathon...I figured this must be a known issue.  

I always hesitate to upgrade from something that was working, but I thought this would be safe since I hadn't noticed any complaints.  I wish they would list the problems we might encounter while we upgrade so we could make smart decisions and not waste so much time trying to fix issues that used to work on older versions.  Is there any way to downgrade back to a workable version?

---

### Post by david_kt on 2011-05-10
> **BlueVark said:**
> Thanks Jonathon...I figured this must be a known issue.  

I always hesitate to upgrade from something that was working, but I thought this would be safe since I hadn't noticed any complaints.  I wish they would list the problems we might encounter while we upgrade so we could make smart decisions and not waste so much time trying to fix issues that used to work on older versions.  Is there any way to downgrade back to a workable version?

You could try to use the installer to remove the existing e-Sword (option second last), and reinstall it after that. 

DK

---

### Post by jonathonblake on 2011-05-10
> **BlueVark said:**
> but I thought this would be safe since I hadn't noticed any complaints.

I mentioned it at [http://ubuntuforums.org/showthread.php?t=1739879](http://ubuntuforums.org/showthread.php?t=1739879), amongst other places.

> I wish they would list the problems we might encounter while we upgrade

This only affected WINE and CrossOver users. 

I posted a message about search issues on e-Sword-users.org, the eSword support list, CrossOver Forum, and as a follow up to the announcement here about the release of e-Sword 9.9.0. Rick announced a fix for it on the CrossOver forum on 2 May.

I have no idea where else to post issues of this type. My e-Sword blog? 

> Is there any way to downgrade back to a workable version?

Assuming you still have the e-Sword 9.8.x executable, uninstall Windows, then blow away .wine, and reinstall everything.  Use David's script, but select "manual", rather than e-Sword.  When it pops up the screen for what to install, navigate to where your e-Sword 9.8.x executable is, and use that.   (It doesn't have to be e-Sword 9.x.  It can be used for everything from e-Sword 4.0, through e-Sword 9.9.0.)

jonathon

---

### Post by david_kt on 2011-05-10
> **jonathonblake said:**
> 
Assuming you still have the e-Sword 9.8.x executable, uninstall Windows, then blow away .wine, and reinstall everything.  Use David's script, but select "manual", rather than e-Sword.  When it pops up the screen for what to install, navigate to where your e-Sword 9.8.x executable is, and use that.   (It doesn't have to be e-Sword 9.x.  It can be used for everything from e-Sword 4.0, through e-Sword 9.9.0.)

jonathon

That should be script before 03/01/11, and might not work as the tweaks will not be executed when you use manual. You should follow the manual instruction at the first post of this thread.

DK

---

### Post by geiroffenberg on 2011-05-12
ANy way to fix the search function? I use it all the time in win.

---

### Post by david_kt on 2011-05-12
> **geiroffenberg said:**
> ANy way to fix the search function? I use it all the time in win.

Fresh install using the script should not have problem with search function. So far I have never had problem with it.

DK

---

### Post by geiroffenberg on 2011-05-17
thats weird. Did a fresh install after removing the old, using newest everything, still the search function does not work for me. 
I know theres a web version of the e-sword now, where a search function works, but it does not nearly have the features and translations of the installed e-sword. I hope i get this to work in linux, it would be very helpful.

BTW, i just found out i CAN search the commentaries, just not the bibles.

---

### Post by david_kt on 2011-05-17
> **geiroffenberg said:**
> thats weird. Did a fresh install after removing the old, using newest everything, still the search function does not work for me. 
I know theres a web version of the e-sword now, where a search function works, but it does not nearly have the features and translations of the installed e-sword. I hope i get this to work in linux, it would be very helpful.

BTW, i just found out i CAN search the commentaries, just not the bibles.

I have updated the installer to solve this problem, please download [the latest installer]("http://ubuntuforums.org/attachment.php?attachmentid=192485&d=1305674700") and reinstall e-Sword.

DK

---

### Post by geiroffenberg on 2011-05-18
Hmmm... now i get 
"Esword_installer error: Note: command 'env WINEPREFIX=/homegeiroffenberg/.wine-Esword ./winetricks mfc42' returned status 2. Aborting."

update: looks like the installer hangs on one of the download links, probable the mfc file. Ill try again later.

update2: YAY! it works! Thanks david, you're a genius!

---

### Post by BlueVark on 2011-05-18
Thanks again David for the update that fixes the "Bible Search"!!!

---

### Post by Kafreen on 2011-05-22
Thanks, David! 
Tried so many other fixes, but yours works beautifully!!

---

### Post by andreisun on 2011-06-03
Hi there, i tried installing with wine, but the E-sword doesn't work...
I am trying with Crossover Linux as recommended on E-sword site.

---

### Post by tak1150 on 2011-06-06
I was able to install e-sword (thanks for the installer), and I have Bible files I've purchased (*.bbl) before that I copied into the /home/me/.wine/drive_c/Program\Files/e-Sword/, but those Bibles (both free and purchased ones) do not appear at all in e-sword. Any ideas?

---

### Post by david_kt on 2011-06-06
> **tak1150 said:**
> I was able to install e-sword (thanks for the installer), and I have Bible files I've purchased (*.bbl) before that I copied into the /home/me/.wine/drive_c/Program\Files/e-Sword/, but those Bibles (both free and purchased ones) do not appear at all in e-sword. Any ideas?


You have to get the new version of your purchased bible (if any) which is *.bblx. Otherwise, install old version of e-Sword or convert from bbl to bblx.

DK

---

### Post by tak1150 on 2011-06-07
Thank you for your quick help! How do you convert bbl to bblx?

---

### Post by david_kt on 2011-06-07
> **tak1150 said:**
> Thank you for your quick help! How do you convert bbl to bblx?

I have never converted it yet. But see below link for such tool:

[http://goodolclint.com/e-sword](http://goodolclint.com/e-sword)

DK

---

### Post by aneumann91 on 2011-06-07
I have got a problem, too. I have got Ubuntu 11.04 and wine 1.2.2
When I install the script I always get:

```
Esword_installer error: Note: command 'wget -nd -read-timeout=300 --retry-connrefused --header Accept-Encodeing: gzip,deflate http://www.esword.net/files/werden.' returned status 8. Aborting.

```

If I click 'okay', i get

```


Esword_installer error: Note: command 'env WINEPREFIX=/home/xxx/.wine_Esword wine /home/xxx/.wineeswordcache/werden.' returned status 2. Aborting.


```

May anybody help me please?

---

### Post by jonathonblake on 2011-06-07
> **aneumann91 said:**
> May anybody help me please?

I'll test my theories out later on tonight:

a) Rick has changed the website again, to disallow more web scrapers;
b) The site has been pounded by people updating to e-Sword 9.9.1;

Did you use the most recent of David's script to install e-Sword?

jonathon

---

### Post by david_kt on 2011-06-08
> **jonathonblake said:**
> I'll test my theories out later on tonight:

a) Rick has changed the website again, to disallow more web scrapers;
b) The site has been pounded by people updating to e-Sword 9.9.1;

Did you use the most recent of David's script to install e-Sword?

jonathon

Option b or
c) Rick was editing the website.

I could install the latest version of E-sword a few minutes ago.

DK

---

### Post by aneumann91 on 2011-06-08
It is strange, I believe that you have installed correctly but, i still get the same errors. Always error 8 and error 2. Maybe I have got anywher something wrong things? If yes, please tell me. I just downloaded double-clicked (checked if executable before) and executed it.

I tried the manual way, too, but then I couldn't start esword.

---

### Post by david_kt on 2011-06-08
> **aneumann91 said:**
> It is strange, I believe that you have installed correctly but, i still get the same errors. Always error 8 and error 2. Maybe I have got anywher something wrong things? If yes, please tell me. I just downloaded double-clicked (checked if executable before) and executed it.

I tried the manual way, too, but then I couldn't start esword.

Download, extract, and double click.
First, choose clear cache (option no. 3) to clear the leftover file.
And then, run again and choose esword (option no. 1)

DK

---

### Post by aneumann91 on 2011-06-08
done as you said, this is the terminal output (after double-clicking i run by terminal):

```
andy@andypc:~/Downloads$ sh e-sword-installer
Using builtin override for following DLLs: riched20 oleaut32
Executing env WINEPREFIX=/home/andy/.wine_Esword wine regedit /home/andy/.wine_Esword/drive_c/wineeswordtmp/override-dll.reg
--2011-06-08 12:29:07--  http://www.e-sword.net/downloads.html
Auflösen des Hostnamen www.e-sword.net... 208.67.58.170
Verbindungsaufbau zu www.e-sword.net|208.67.58.170|:80... verbunden.
HTTP-Anforderung gesendet, warte auf Antwort... 200 OK
Länge: 5789 (5,7K) [text/html]
In »downloads.html« speichern.

100%[======================================>] 5.789       --.-K/s   in 0,1s    

2011-06-08 12:29:07 (43,0 KB/s) - »downloads.html« gespeichert [5789/5789]

Executing env WINEPREFIX=/home/andy/.wine_Esword wine /home/andy/.wineeswordcache/werden.
wine: cannot find '/home/andy/.wineeswordcache/werden.'
Note: command 'env WINEPREFIX=/home/andy/.wine_Esword wine /home/andy/.wineeswordcache/werden.' returned status 2.  Aborting.

```

---

### Post by david_kt on 2011-06-08
> **aneumann91 said:**
> done as you said, this is the terminal output (after double-clicking i run by terminal):

```

Executing env WINEPREFIX=/home/andy/.wine_Esword wine /home/andy/.wineeswordcache/werden.
wine: cannot find '/home/andy/.wineeswordcache/werden.'
Note: command 'env WINEPREFIX=/home/andy/.wine_Esword wine /home/andy/.wineeswordcache/werden.' returned status 2.  Aborting.

```

May be I have to adjust the installer for German language, but temporary you could use attached installer just for this e-sword version (991).

DK

---

### Post by aneumann91 on 2011-06-08
Thank you very very much, it worked fine :)

---

### Post by jburlap on 2011-06-08
I just installed the e-sword 9.9.1 .exe file and installed using wine 1.2. Installation is successful, but when I click the Icon, nothing opens. I will be reading this thread to see if there are any instructions that directly deal with what I am dealing with. If anyone has any quick tips, or can direct me to a post with the helpful information, I would greatly appreciate it!

---

### Post by david_kt on 2011-06-08
> **jburlap said:**
> I just installed the e-sword 9.9.1 .exe file and installed using wine 1.2. Installation is successful, but when I click the Icon, nothing opens. I will be reading this thread to see if there are any instructions that directly deal with what I am dealing with. If anyone has any quick tips, or can direct me to a post with the helpful information, I would greatly appreciate it!

Please reinstall using the script in the first post of this thread or click [here]("http://ubuntuforums.org/attachment.php?attachmentid=192485&d=1305674700") to download it.

DK

---

### Post by jonathonblake on 2011-06-09
> **david_kt said:**
> May be I have to adjust the installer for German language, 

This is not the first time that a special script for German users has been created.  I need to notate that in my list of issues with installing e-Sword.

Thus.

d) The problem is that a German localization is being used;

jonathon

---

### Post by benkong2 on 2011-06-21
I have a problem with the latest installer and installing downloaded modules. 9.91 esword updated correctly but when I install downloaded modules I can only do it manually. An example "env WINEPREFIX=~/.wine_Esword wine nlt.exe" This works, but running ./e-sword-installer and selecting "manual" gives me the file dialog box I can select the file and then it just goes straight to the "Done" dialog. It does move the exe file from the Download location to .wine_Esword/drive_c subdirectory. What am I doing wrong?

---

### Post by david_kt on 2011-06-21
> **benkong2 said:**
> I have a problem with the latest installer and installing downloaded modules. 9.91 esword updated correctly but when I install downloaded modules I can only do it manually. An example "env WINEPREFIX=~/.wine_Esword wine nlt.exe" This works, but running ./e-sword-installer and selecting "manual" gives me the file dialog box I can select the file and then it just goes straight to the "Done" dialog. It does move the exe file from the Download location to .wine_Esword/drive_c subdirectory. What am I doing wrong?

Yes, the new one is not exe file so it only need to be moved to correct folder. For exe file, you should do it manually as I have remove that option, or should I put it back?

DK

---

### Post by benkong2 on 2011-06-22
> **david_kt said:**
> Yes, the new one is not exe file so it only need to be moved to correct folder. For exe file, you should do it manually as I have remove that option, or should I put it back?

DK

To put it back or not I cannot say but there is a manual option in the selection box and that is what I assumed was supposed to install the files I download from e-sword site. But I am still happy with what I have.

Thank you and may Yeshua bless you for this effort

---

### Post by javaman90 on 2011-07-06
FYI, the installer runs fine on Maverick Meerkat. I haven't fully run the program, but it started up, I was able to get to verses and look up strong's links so far.
Thanks for this script!

---

### Post by dankegel on 2011-07-11
My impression is that you don't need any fancy installer thingy;
all you need is
  winetricks mfc42
Then the installer runs fine and the app runs ok.

---

### Post by jonathonblake on 2011-07-11
> **david_kt said:**
> For exe file, you should do it manually as I have remove that option, or should I put it back?

I'm going to suggest two options here:
* Executable files;
* Non-executable files;

a)  Historically, Biblical software for windows that is installed using the "manual" option the e-Sword-installer script has been more stable, and less buggy, than using the more usual wine installation techniques and tools;

b) BibleSupport.com is distributing resources that are self-executing files. The current script merely drops them into the program folder, without installing them;

jonathon

---

### Post by david_kt on 2011-07-11
> **dankegel said:**
> My impression is that you don't need any fancy installer thingy;
all you need is
  winetricks mfc42
Then the installer runs fine and the app runs ok.

From previous record, below are additional problems:

- Need special wine prefix so as not to disturb other application, 
- the text won't appear 
- graphic viewer does not work.

By the way, the installer is for newbie only. For experience user, they do not even need winetricks to run e-Sword.

DK

---

### Post by ahbeng on 2011-07-26
Not sure whether anyone else is having this problem, but I was unable to change the Scripture Tooltip font size because the popup dialog just refused to appear. I could change the default font, though. 

I discovered that there is a file named "user.reg" in the directory:

/home/*yourname*/wine_Esword/drive_c. 

On a hunch, I edited this file and added the line:

"Tooltip Font Size"="14"

Bingo! The tooltip font size is now what I want it to be! PTL!

Just wanted to share this.

Incidentally I still have the problem of not being able to access the menu items "File", "Edit", "Format", "Bible" etc using the keyboard shortcuts (eg Alt-B to pull down the "Bible" menu and "Alt-C" to Copy the verses). I have to either use the mouse or hit "Alt" followed by using the arrow keys.

I wonder if anyone else has this problem and has found a solution?

Thanks!

---

### Post by My_World on 2011-08-18
I have the following error when trying to run e-Sword:

```

wine e-Sword.exe 
fixme:ole:OleLoadPictureEx (0xfccd44,276546,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f97c), partially implemented.
fixme:ole:OleLoadPictureEx (0xfd17ec,3334,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f0fc), partially implemented.
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:ole:OLEFontImpl_SetHdc (0x1a90c8)->(0x5c4): Stub
fixme:ole:OleLoadPictureEx (0xfd17ec,3334,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f0fc), partially implemented.
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:ole:OleLoadPictureEx (0xfd76b4,1150,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f538), partially implemented.
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x1d3ea4), stub!
fixme:ole:OleLoadPictureEx (0xfd17ec,3334,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f0fc), partially implemented.
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\system32\\tx4ole14.ocx") not found
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\tx4ole14.ocx"
err:ole:CoGetClassObject no class object {15a32f01-b939-11dc-af58-0013d350667c} could be created for context 0x3
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\system32\\tx4ole14.ocx") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\system32\\tx4ole14.ocx") not found
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\tx4ole14.ocx"
err:ole:CoGetClassObject no class object {15a32f01-b939-11dc-af58-0013d350667c} could be created for context 0x3
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}


```

It seems a few dll's are missing:
```

winetricks mfc42
Executing w_do_call mfc42
mfc42 already installed, skipping

```

All the dll's are installed into c:/windows/syswow64 and not into system32.

I tried to force a 32bit installation on the installer with:
```

export WINEARCH="win32"

./e-sword-installer

wine: WINEARCH set to win32 but '~/.wine_Esword' is a 64-bit installation.

```

How do one get around this dll nightmare?

---

### Post by My_World on 2011-08-18
It seems the 64-bit wine and the installer script does not work too well together, so if you choose to run 64-bit wine, read on.

I got the problem solved with a little help form this:
[http://forum.sabayon.org/viewtopic.php?t=22775#p127929](http://forum.sabayon.org/viewtopic.php?t=22775#p127929)

What I did:
```

rm -r ~/.wine_Esword
export WINEPREFIX=$HOME/.wine_Esword
export WINEARCH=win32
winecfg
./e-sword-installer

```

Works now.
:P

---

### Post by dwoodu21 on 2011-08-21
I've been on Ubuntu for less than a week now and still trying to learn the ropes.  I followed the above instructions for e-sword and have it running perfectly.  I have been able to add modules from the main site.  But what about modules from the users that are contained at Biblesupport (.com)?  Will these work?  

There is a particular commentary that I would like to have (Pulpit Commentary) will it work within wine?  Here is the [link]("http://www.biblesupport.com/e-sword-downloads/file/7-pulpit-commentary-all-66-books-for-e-sword/") (if it helps).

Thank you for your help, wouldn't have been able to get this far without it.

---

### Post by dwoodu21 on 2011-08-23
I figured it out.  I just got the .cmtx file from the commentaries that I wanted.

cp command from my home folder to the e-Sword folder.  I opened my esword program and there it was!  Thanks for all your help.

---

### Post by david_kt on 2011-08-24
> **dwoodu21 said:**
> I figured it out.  I just got the .cmtx file from the commentaries that I wanted.

cp command from my home folder to the e-Sword folder.  I opened my esword program and there it was!  Thanks for all your help.

In the installer, I put the manual option for this purpose i.e. to move those files copied from windows.

DK

---

### Post by davidtrounce on 2011-08-28
> **jonathonblake said:**
> I'm going to suggest two options here:
* Executable files;
* Non-executable files;

a)  Historically, Biblical software for windows that is installed using the "manual" option the e-Sword-installer script has been more stable, and less buggy, than using the more usual wine installation techniques and tools;

b) BibleSupport.com is distributing resources that are self-executing files. The current script merely drops them into the program folder, without installing them;

jonathon

Regarding the above: 
b) BibleSupport.com is distributing resources that are self-executing  files. The current script merely drops them into the program folder,  without installing them;

I have this problem. THey have moved to the program folder but they have not installed. How do I install them? (they are .exe m,odules from biblesupport.com.

---

### Post by geiroffenberg on 2011-08-29
> **davidtrounce said:**
> Regarding the above: 
b) BibleSupport.com is distributing resources that are self-executing  files. The current script merely drops them into the program folder,  without installing them;

I have this problem. THey have moved to the program folder but they have not installed. How do I install them? (they are .exe m,odules from biblesupport.com.

Hey, i just did that with the KJV+ w/ tenses and dictionary module from biblesupport.
Just run the downloaded and extracted .exe file in wine, you may have to right click on it first and change permission to "allow execution". They will then be extracted to the .wine folder, under c: programs, wine.
You c/ then run the e-sword installer script, choose "manually install downloaded modules" and browse to these files and click one, click ok, then click next module, click ok, untill you got them all. next time you start up e-sword they will be there.

---

### Post by david_kt on 2011-08-30
As suggested by jonathonblake, today I have added back the addons installer to use with executable. Please download the latest installer at the first page of this thread.

DK

---

### Post by davidtrounce on 2011-09-04
As always, thank you David for your prompt help.

---

### Post by snowman024 on 2011-09-13
I got the following error message:

Esword_installer error: Note: command 'wget -nd --read timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate [http://www.e-sword.net/files/bibles/jps.bblx](http://www.e-sword.net/files/bibles/jps.bblx)' returned status 4. Aborting

---

### Post by david_kt on 2011-09-13
> **snowman024 said:**
> I got the following error message:

Esword_installer error: Note: command 'wget -nd --read timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate [http://www.e-sword.net/files/bibles/jps.bblx](http://www.e-sword.net/files/bibles/jps.bblx)' returned status 4. Aborting

Could you try other bible first again today, and if successful, then try again the jps bible.

DK

---

### Post by ubume2 on 2011-09-27
Hello,
I have used E-Sword for several years and love it. I've installed some modules that I downloaded from bible support.com, specifically, J.C. Ryle Commentary and Calvin's Commentary.

I have it installed on 10.04 (wine1.2) and 11.04 (wine1.3, I think), and PCLOS using the e-Sword install script.

Until yesterday, J. C. Ryle and Calvin's were working properly on my 10.04 install. Today, all I get when I click on Ryle is a blank page. Calvin's still works fine. 

On 11.04 all is working great.

Has anybody experienced this problem?  Any solutions?  Thanks.

---

### Post by ubume2 on 2011-09-30
bump

---

### Post by michaelcarey95 on 2011-10-08
I've installed e-Sword with WINE, but it won't run.  According to [this]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=23609"), I need to install mfc42.dll and register vbscript.dll but I don't know how to do that.  Any advice?  I've used e-Sword in Windows 7 and absolutely love it, I hope I can get it in Ubuntu.  (not running the CE)

Edit: I've figured out how to do it.

---

### Post by TREESofRIGHTEOUSNESS on 2011-10-09
Xiphos is pretty nice compared to bible time....  never used E-sword.   I used Davar for windows, which is really nice

---

### Post by geiroffenberg on 2011-10-18
oh....e-sword crashes at startup after upgrading to oneric. I begins to startup, then its just gone. I've had so much freezes, unstabiliy and crashes since upgrading.

*edit-> I guess its not esword that crashes but wine that broke all my installed packeges, there must have been a upgrade of wine happened when i move to 11.10
 guess my question then is, do i have to do a fresh install of e-sword again, and rebuild my perfect setup of modules AGAIN? I cant see myself be doing this everytime ubuntu or wine updates itself.

---

### Post by david_kt on 2011-10-18
> **geiroffenberg said:**
> oh....e-sword crashes at startup after upgrading to oneric. I begins to startup, then its just gone. I've had so much freezes, unstabiliy and crashes since upgrading.

*edit-> I guess its not esword that crashes but wine that broke all my installed packeges, there must have been a upgrade of wine happened when i move to 11.10
 guess my question then is, do i have to do a fresh install of e-sword again, and rebuild my perfect setup of modules AGAIN? I cant see myself be doing this everytime ubuntu or wine updates itself.

Reboot your computer and try again e-Sword. If still crash, re-install the esword main program.

DK

---

### Post by geiroffenberg on 2011-10-19
> **david_kt said:**
> Reboot your computer and try again e-Sword. If still crash, re-install the esword main program.

DK
thanks dave, so far to reinstall esword installer script returns the "wine cmd.exe /c echo '%ProgramFiles%' returned emty string" error.

*edit: finally did a fresh install of ubuntu, and everything and wine esword. It worked for one day, now the same problem came back. This is horrible, seriously.

*edit 2, did ANOTHER fresh install of ubuntu and everything. so far so good.

I have another dave: i tried the download function that is inside inside e-sword and it worked flawlessly. Is this something you recomend to use, rather than the install script now (lots more bibles and commentaries available there). I still need to script tho  to install manually some modules that is not from the e-sword website.

*edit 3 now the installer doesnt work for manualy moduls! gets error: command 'env WINEPREFIX=/home/geiroffenberg/.wine_Esword wine /home/geiroffenberg/kjv+tvm_bible_&_dictionary_9x.exe' returned status 193.  Aborting.
and "bad exe format"

*edit 4, been working in this for DAYS! but it now seems to all be in order. Basicly i just tried and retried until it worked. May this NEVER happen again, i has been horrible lol. But i got my perfect setup and my favourite bibles back and workin, so im happy.

---

### Post by jonathonblake on 2011-10-28
> **michaelcarey95 said:**
>  I need to install mfc42.dll and register vbscript.dll but I don't know how to do that. 

I put it into /home/ user-name /.wine/drive_c/windows/system32 and also into /home/ user-name /.wine_Esword/drive_c/Program Files/e-Sword directories.

jonathon

---

### Post by jonathonblake on 2011-10-28
> **geiroffenberg said:**
>  do i have to do a fresh install of e-sword again, and rebuild my perfect setup of modules AGAIN? 

That is why I put resources in /home/ user-name/e-Sword/program, and reconfigure e-Sword when I reinstall it.

That way, when WINE updates break things, I can safely blow away the .wine_eSword directory, and reinstall e-Sword. You can prevent WINE from updating, but the ease of doing that depends upon which tool chain is used to update/install software.

jonathon

---

### Post by javaman90 on 2011-10-29
I'm running Ubuntu 10.10, and when I run the e-sword-installer I get this output:

```
vance@vance-ub:~/Downloads/Programs/Esword$ ./e-sword-installer
Using builtin override for following DLLs: riched20 oleaut32
Executing env WINEPREFIX=/home/vance/.wine_Esword wine regedit /home/vance/.wine_Esword/drive_c/wineeswordtmp/override-dll.reg
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x33cfdc
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\system32\\gecko\\1.0.0\\wine_gecko\\components\\xpti.dat" 1 536870916 (nil) (nil) 0x1ba01c (nil)
fixme:iphlpapi:NotifyAddrChange (Handle 0xa62e8d8, overlapped 0xa62e8e0): stub
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\system32\\gecko\\1.0.0\\wine_gecko\\components\\compreg.dat" 1 536870916 (nil) (nil) 0x1daa6ec (nil)
wine: configuration in '/home/vance/.wine_Esword' has been updated.
--2011-10-29 14:38:02--  http://www.e-sword.net/downloads.html
Resolving www.e-sword.net... 208.67.58.170
Connecting to www.e-sword.net|208.67.58.170|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `downloads.html'

    [ <=>                                                                                                                               ] 8,392       --.-K/s   in 0.05s   

2011-10-29 14:38:02 (160 KB/s) - `downloads.html' saved [8392]

sha1sum mismatch!  Rename /home/vance/.wineeswordcache/./setup1001.exe and try again.
```


The installer quits with a dialog telling me to rename the setup1001.exe. I am using Wine 1.2, but I got this same error when using Wine 1.0.1

Any ideas to get this to work?
Thanks,
Vance

---

### Post by david_kt on 2011-10-29
> **javaman90 said:**
> 
sha1sum mismatch!  Rename /home/vance/.wineeswordcache/./setup1001.exe and try again.


The installer quits with a dialog telling me to rename the setup1001.exe. I am using Wine 1.2, but I got this same error when using Wine 1.0.1

Any ideas to get this to work?
Thanks,
Vance

Run ./e-sword-installer and choose clear_cache. After that run ./e-sword-installer again to install e-Sword.

DK

---

### Post by javaman90 on 2011-10-29
Thanks for the suggestion, but I had already tried that. I tried it again, and re-ran the installer only to get the sha1um problem again.

Thanks,
Vance

---

### Post by mattman on 2011-10-29
I just downloaded the 10.0.1 installer from the E-sword website and installed it and it works fine.

---

### Post by javaman90 on 2011-10-30
Ok, I'll re-download and try again. What version of Wine are you using?

---

### Post by david_kt on 2011-10-30
> **javaman90 said:**
> Ok, I'll re-download and try again. What version of Wine are you using?

Please download the latest installer (at the first post of this thread) I make today, the problem is there are two version of e-Swords to download. You could choose 991 version (stable) or 1001 version (release candidate) from the installer.

DK

---

### Post by javaman90 on 2011-10-30
Hi,
I re-downloaded and I get a dialog box that allows the user to choose whether to run the 1001 or 991 installer. I have tried choosing both, but I get this error message:


```
vance@vance-ub:~/Downloads/Programs/E-sword$ ./e-sword-installer
Using builtin override for following DLLs: riched20 oleaut32
Executing env WINEPREFIX=/home/vance/.wine_Esword wine regedit /home/vance/.wine_Esword/drive_c/wineeswordtmp/override-dll.reg
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x33cfdc
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\system32\\gecko\\1.0.0\\wine_gecko\\components\\xpti.dat" 1 536870916 (nil) (nil) 0x191954 (nil)
fixme:iphlpapi:NotifyAddrChange (Handle 0xa62e8d8, overlapped 0xa62e8e0): stub
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\system32\\gecko\\1.0.0\\wine_gecko\\components\\compreg.dat" 1 536870916 (nil) (nil) 0x1daa62c (nil)
wine: configuration in '/home/vance/.wine_Esword' has been updated.
--2011-10-30 09:07:03--  http://www.e-sword.net/downloads.html
Resolving www.e-sword.net... 208.67.58.170
Connecting to www.e-sword.net|208.67.58.170|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `downloads.html'

    [ <=>                                                                                                                               ] 8,392       --.-K/s   in 0.06s   

2011-10-30 09:07:03 (144 KB/s) - `downloads.html' saved [8392]

Executing env WINEPREFIX=/home/vance/.wine_Esword wine /home/vance/.wineeswordcache/setup991.exe
wine: cannot find '/home/vance/.wineeswordcache/setup991.exe'
Note: command 'env WINEPREFIX=/home/vance/.wine_Esword wine /home/vance/.wineeswordcache/setup991.exe' returned status 2.  Aborting.
```

The message is the same if I choose 1001, but the error messages states it can't find setup1001.exe.

Thanks for the help,
Vance

---

### Post by mattman on 2011-10-30
I'm using the version in the official Ubuntu Oneiric repo.

---

### Post by david_kt on 2011-10-30
> **javaman90 said:**
> 
The message is the same if I choose 1001, but the error messages states it can't find setup1001.exe.

Thanks for the help,
Vance

Very sorry for that, I forgot to put back the download line after I remove it while troubleshooting the script. Please re-download the script (same name), I have just repair it.

DK

---

### Post by javaman90 on 2011-10-30
No worries. I appreciate your quick replies and fixing the script. I couldn't create this script myself, so it's great someone else (you) has done so. 
I re-downloaded and the program seems to be working now. I haven't tested all the functionality in the program, but what I have used before seems to be fine. 

There was an error though in the console, and I've copied it here in case your interested: 

```
vance@vance-ub:~/Downloads/Programs/E-sword$ ./e-sword-installer
Using builtin override for following DLLs: riched20 oleaut32
Executing env WINEPREFIX=/home/vance/.wine_Esword wine regedit /home/vance/.wine_Esword/drive_c/wineeswordtmp/override-dll.reg
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x33cfdc
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\system32\\gecko\\1.0.0\\wine_gecko\\components\\xpti.dat" 1 536870916 (nil) (nil) 0x19190c (nil)
fixme:iphlpapi:NotifyAddrChange (Handle 0xa62e8d8, overlapped 0xa62e8e0): stub
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\system32\\gecko\\1.0.0\\wine_gecko\\components\\compreg.dat" 1 536870916 (nil) (nil) 0x1daa6bc (nil)
wine: configuration in '/home/vance/.wine_Esword' has been updated.
--2011-10-30 14:41:03--  http://www.e-sword.net/downloads.html
Resolving www.e-sword.net... 208.67.58.170
Connecting to www.e-sword.net|208.67.58.170|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `downloads.html'

    [ <=>                                                                                                                               ] 8,392       --.-K/s   in 0.06s   

2011-10-30 14:41:03 (132 KB/s) - `downloads.html' saved [8392]

Executing env WINEPREFIX=/home/vance/.wine_Esword wine /home/vance/.wineeswordcache/setup991.exe
fixme:advapi:LookupAccountNameW (null) L"vance" (nil) 0x33f160 (nil) 0x33f164 0x33f158 - stub
fixme:advapi:LookupAccountNameW (null) L"vance" 0x13d138 0x33f160 0x13d848 0x33f164 0x33f158 - stub
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 1 ignored L"Upgrade" table values
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 1 ignored L"Upgrade" table values
fixme:msi:msi_unimplemented_action_stub RemoveExistingProducts -> 1 ignored L"Upgrade" table values
fixme:mscoree:LoadLibraryShim (0x7ed461cc L"fusion.dll", (nil), (nil), 0x33f918): semi-stub
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\e-Sword\\" 1 4 (nil) (nil) 0x583df0 (nil)
Trying to load PE image for unsupported architecture (AMD-64)
Trying to load PE image for unsupported architecture (AMD-64)
Executing cabextract --directory=/home/vance/.wine_Esword/drive_c/wineeswordtmp /home/vance/.wineeswordcache/InstMsiA.exe
Extracting cabinet: /home/vance/.wineeswordcache/InstMsiA.exe
  extracting /home/vance/.wine_Esword/drive_c/wineeswordtmp/msi.dll
  extracting /home/vance/.wine_Esword/drive_c/wineeswordtmp/msiexec.exe
  extracting /home/vance/.wine_Esword/drive_c/wineeswordtmp/msihnd.dll
  extracting /home/vance/.wine_Esword/drive_c/wineeswordtmp/msisip.dll
  extracting /home/vance/.wine_Esword/drive_c/wineeswordtmp/msimsg.dll
  extracting /home/vance/.wine_Esword/drive_c/wineeswordtmp/msimain.sdb
  extracting /home/vance/.wine_Esword/drive_c/wineeswordtmp/msiinst.exe
  extracting /home/vance/.wine_Esword/drive_c/wineeswordtmp/riched20.dll
  extracting /home/vance/.wine_Esword/drive_c/wineeswordtmp/usp10.dll
  extracting /home/vance/.wine_Esword/drive_c/wineeswordtmp/msls31.dll
  extracting /home/vance/.wine_Esword/drive_c/wineeswordtmp/shfolder.dll
  extracting /home/vance/.wine_Esword/drive_c/wineeswordtmp/instmsi.msi
  extracting /home/vance/.wine_Esword/drive_c/wineeswordtmp/imagehlp.dll
  extracting /home/vance/.wine_Esword/drive_c/wineeswordtmp/cabinet.dll
  extracting /home/vance/.wine_Esword/drive_c/wineeswordtmp/mspatcha.dll
  extracting /home/vance/.wine_Esword/drive_c/wineeswordtmp/sdbapi.dll

All done, no errors.
Executing cp -f /home/vance/.wine_Esword/drive_c/wineeswordtmp/msls31.dll /home/vance/.wine_Esword/drive_c/windows/system32
Using native,builtin override for following DLLs: riched20 oleaut32
Executing env WINEPREFIX=/home/vance/.wine_Esword wine regedit /home/vance/.wine_Esword/drive_c/wineeswordtmp/override-dll.reg
Executing env WINEPREFIX=/home/vance/.wine_Esword ./winetricks mfc42
Executing w_do_call mfc42
Executing load_mfc42
Executing mkdir -p /home/vance/.cache/winetricks/vcrun6
Downloading http://download.microsoft.com/download/vc60pro/update/1/w9xnt4/en-us/vc6redistsetup_enu.exe to /home/vance/.cache/winetricks/vcrun6
--2011-10-30 14:41:51--  http://download.microsoft.com/download/vc60pro/update/1/w9xnt4/en-us/vc6redistsetup_enu.exe
Resolving download.microsoft.com... 96.17.160.82, 96.17.160.26
Connecting to download.microsoft.com|96.17.160.82|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1833232 (1.7M) [application/octet-stream]
Saving to: `vc6redistsetup_enu.exe'

100%[==================================================================================================================================>] 1,833,232    766K/s   in 2.3s    

2011-10-30 14:41:54 (766 KB/s) - `vc6redistsetup_enu.exe' saved [1833232/1833232]

Executing wine /home/vance/.cache/winetricks/vcrun6/vc6redistsetup_enu.exe /T:C:\windows\Temp\_mfc42 /c
Executing cabextract -q /home/vance/.cache/winetricks/vcrun6/vcredist.exe -d /home/vance/.wine_Esword/dosdevices/c:/windows/system32 -F mfc42*.dll
cp: `./drive_c/windows/system32/riched20.dll' and `/home/vance/.wine_Esword/drive_c/windows/system32/riched20.dll' are the same file
Executing env WINEPREFIX=/home/vance/.wine_Esword wine regsvr32 vbscript.dll
Successfully registered DLL vbscript.dll
Install of esword done
Executing mv /home/vance/.wineeswordcache/kjva.bblx ./
mv: cannot stat `/home/vance/.wineeswordcache/kjva.bblx': No such file or directory
Note: command 'mv /home/vance/.wineeswordcache/kjva.bblx ./' returned status 1.  Aborting.
vance@vance-ub:~/Downloads/Programs/E-sword$ 
```

In the download selection dialog I had selected the kjva, hot+, and gnt-wh+.

Thanks for the help,
Vance

---

### Post by Diolectic on 2011-11-03
I've been trying to install esword on my new Ubuntu laptop but the desktop shortcut never worked (at first, it didn't even show up). All that worked is the link from the programs list. However, I was thinking last night on how to resolve this issue before I try a fresh install of my OS of Ubuntu (desperate last result). I figured that I would un-install wine & esword. then I re-installed wine then also esword. Voila, it all works like it should now.

I posted this so if someone might want to try it to fixs any problems that they are having.

---

### Post by James78 on 2011-11-16
Doing 'regsvr32 vbscript.dll' doesn't work for me anymore. It succeeds, but esword search function still doesn't work. I used to do this manually, so I tried the installer instead, but that didn't fix anything either. :( Any solutions? I'm using latest WINE, 1.3.32 or so.

Edit::

I fixed the search problem. Using WINE 1.4, esword 10.0.7, this is what I did. Perhaps this should be added to the script installer...

Using winetricks, install:

(Cosmetic - may be skipped)
fontsmooth=rgb
fontfix

Set wine version to nt4.0 and install this one
6851 - Microsoft Visual C++ 6.0 Redistributable
Then set it back to XP and install the rest

6894 - Microsoft Visual Basic 6 Service Pack 6 runtime
7857 - msls31
7886 - Windows Script 5.7 (added for e-Sword 10.0.3 for an msi installation error)
6849 - Microsoft XML Parser (MSXML) 3.0 (needed for bible/commentary/module download tool)

Set dll override
oleaut32==builtin

To fix the active verse problem, go into system32 and delete "msftedit.dll"

Now install e-sword.

Search and everything now works properly. :)

Note: I got all this information from the esword crosstie (attached below).

---

### Post by jesse100 on 2011-12-19
Just an update. I recently installed Mint Linux (Ubuntu 11 I believe) and then the latest Wine. Installed E-sword and it could not have been easier or smoother. I then copied all my files from my windows version, pasted them to the directory on the Linux version and viola! I have gone through all the hoops and surgeries with previous attempts but this was painless.No bugs or glitches so far. It's easier than ever to install e-sword on Linux.

---

### Post by uboer on 2012-01-18
I have tried a number of ways in properly installing e-sword under ubuntu (10.11 with all latest updates 18 Jan 12) and finally managed to have search and graphics functions working properly.

I have previously installed Wine 1.3.? and installed e-sword by double clicking on file which resulted in a sub-performance installation.  Then un-installed both Wine and e-sword without cleaning up first, installed wine 1.2.3 and again installing e-sword by double clicking.

The installation was again poor.

I then tried this solution (david_kt's e-Sword_installer_301011) in an attempt to "rescue" the installation, but then I realized that the previous installation might have been so corrupted that these problems still remained after david's solution.

There was perhaps corruption that is not targeted by david's solution, and I also do not suggest that david's solution should target all and sundry problems.:D

So if you also have a totally wrecked installation after doing the same nonsense I did, you might find this another possible solution without any guarantees ;)

I DO NOT KNOW ANYTHING ABOUT WINE OR FOR THAT MATTER LINUX INSTALLATION ISSUES - I STRICTLY FOLLOW PROCEDURES FOUND ON THE WEB
THIS IS JUST TO SHARE MY EXPERIENCE

Using Wine 1.2.3 (running in WinXP mode) I have used a few other ways of installing of which I think the best summary is as follows:[INDENT]1. After having installed and un-installed david_kt's e-Sword_installer_301011 (which I suspect rectifies a corrupted wine environment), I use winetricks -> select default wineprefix -> install dll ... -> and selected from the menu[/INDENT][INDENT][INDENT]mfc42; msls31; msxml3; msxml6; riched20; riched30; vb5run; wsh56vb; wsh57

I do not know whether all of these are required, but at least "mfc42, msls31 & riched20" as suggested by david_kt

[/INDENT]2. Used "Configure Wine" to set "riched20" and "oleaut32" to "native(windows)" as per david_kt

3. Used "Uninstall Wine Software" (I know, funny name) to install "ESwordsetup1005.exe" (after install graphics worked, but not search)

4. Used "Uninstall Wine Software" to 
             a) un-install  "ESwordsetup1005.exe" and although wine reports success, the programme is still listed as being installed, 
             b) and installed "ESwordsetup983.exe" in tandem
thereafter install search worked, but not graphics

5. Used "Uninstall Wine Software" to 
             a) again un-install  "ESwordsetup983.exe"
             b) and re-installed "ESwordsetup1005.exe"
after install BOTH search AND graphics WORKS.  

[/INDENT]I have since not worked exhaustively with e-sword and I am therefore not aware of any other possible problems.

Resolve : I suspect that there is a "environment component" installed by 983 that 1005 requires but is not installed by 1005 (obviously also the contribution of david_kt's e-Sword_installer_301011 to the environment)  A nag is that both versions of e-sword is reported to be installed by Wine.

I will report on any further bugs, if any.

---

### Post by david_kt on 2012-01-18
> **uboer said:**
> 
After numerous attempts at this solution (david_kt's e-Sword_installer_301011) there were still problems (the installer automatically downloads every session the latest e-sword version - in my case 10.05) with searching returning nothing.

I just tried a few minutes ago on Maverick, the installer works fine. Search and graphic functioning properly. Just makes sure there is no error when you use the installer.

DK

---

### Post by uboer on 2012-01-19
Dear David

I can see from the quoted portion of my previous message it might seem as if I am critical.  This is however not what I intended.  I will edit my entry to be more explanatory.

Regards

---

### Post by James78 on 2012-02-28
Whoever wants to avoid all the problems, follow my post on page 79. I kept having all these weird issues, and could never get anything to work, so I went to the place where they have the official installer, and took the information out of it, did it their way, and it couldn't work better!

I've also found that some packages like riched don't even need to be installed. (crosstie installer doesn't mention it!)

P.S. uboer: riched20 made the graphics go blank for me.......

Edit: jonathonblake brings up a good point. I had forgotten to mention that the SermonAudio doesn't work. Everything else does, however it is not my fault this doesn't. The reason is that WINE fails to install the needed packages for this feature....

---

### Post by jonathonblake on 2012-03-03
> **James78 said:**
> Whoever wants to avoid all the problems,

Did you ever get the SermonAudio component to work correctly?
">Tools >SermonAudio.com"

>  follow my post on page 79.

Post # 792 in this thread.

jonathon

---

### Post by david_kt on 2012-03-03
> **James78 said:**
> Whoever wants to avoid all the problems, follow my post on page 79. I kept having all these weird issues, and could never get anything to work, so I went to the place where they have the official installer, and took the information out of it, did it their way, and it couldn't work better!

I've also found that some packages like riched don't even need to be installed. (crosstie installer doesn't mention it!)

P.S. uboer: riched20 made the graphics go blank for me.......

You should use riched20 that comes with e-Sword, just need to override the wine dll with native dll.

DK

---

### Post by James78 on 2012-03-06
> **jonathonblake said:**
> Did you ever get the SermonAudio component to work correctly?
">Tools >SermonAudio.com"



Post # 792 in this thread.

jonathon
I should've mentioned that that doesn't work. I had meant that everything works except that part. The reason it doesn't work is that WINE won't properly install the programs required for it correctly. I guess that highlights one of CrossOver's strengths compared to WINE; slightly more compatibility with some programs.

> **david_kt said:**
> You should use riched20 that comes with e-Sword, just need to override the wine dll with native dll.

DK
Interesting. Is it needed though? As I had mentioned earlier, I didn't see the CrossOver tie file mentioning riched at all, so I assumed it wasn't needed as it's not in their official e-Sword install file... So far, I haven't seen any problems without it at least.

---

### Post by forrestcupp on 2012-03-06
> ** said:**
> 
Interesting. Is it needed though? As I had mentioned earlier, I didn't see the CrossOver tie file mentioning riched at all, so I assumed it wasn't needed as it's not in their official e-Sword install file... So far, I haven't seen any problems without it at least.
riched20 is needed in e-Sword to display the text correctly. it's the dll for the rich text control. It's needed for a lot of things, but probably not for anything that has to do with audio. But as far as riched20 goes, it's not a bad idea to install the native dll with winetricks, since it's needed for a lot of things.

---

### Post by ScottyK7 on 2012-03-09
On a fresh install of Pinguy OS, Wine version 1.4-rc6 and E-sword version 10.0.7.

Downloaded and ran the setup program from the terminal.

Installed with no problems, and upon a brief delay when opening the program, everything works except for the search function.


Noticed from some of the above posts that some files should be installed before installing E-sword. Will installing the files work after installing E-sword, or should I wipe it out and start fresh?

---

### Post by david_kt on 2012-03-09
> **ScottyK7 said:**
> 
Noticed from some of the above posts that some files should be installed before installing E-sword. Will installing the files work after installing E-sword, or should I wipe it out and start fresh?

Registering vbscript should solve that problem:

```
wine regsvr32 vbscript.dll
```

Or, just wipe it out and use the installer at the first post of this thread to start fresh.

DK

---

### Post by ScottyK7 on 2012-03-09
Just nuked the previous install, and downloaded and ran the installer as referenced to on the first post.

Installation appeared to be flawless, however when I start the program, I'm unable to read any of the bible verses. Even the text in the "about" is all white. I checked in the options in case the color was set to white, but that wasn't it.

Read about to install the rich02 (?) to get the text to install correctly, but that had no effect.

Suggestions? Thanks!

---

### Post by david_kt on 2012-03-09
> **ScottyK7 said:**
> Just nuked the previous install, and downloaded and ran the installer as referenced to on the first post.

Installation appeared to be flawless, however when I start the program, I'm unable to read any of the bible verses. Even the text in the "about" is all white. I checked in the options in case the color was set to white, but that wasn't it.

Read about to install the rich02 (?) to get the text to install correctly, but that had no effect.

Suggestions? Thanks!

Could you re-run the installer in the command line and report the exact message come out in the terminal?

DK

---

### Post by forrestcupp on 2012-03-10
No offense at all to david_kt's hard work, but I couldn't get the script to work, either. A lot of people have great success with that script, but if you're like me, and you don't, [I posted a solution right here](http://ubuntuforums.org/showpost.php?p=11673552&postcount=2) where you can manually install e-Sword and everything about it works flawlessly, even searches and dictionaries.

---

### Post by ScottyK7 on 2012-03-10
Forrestcupp's walk through worked. Although I ran into a problem with  the winetricks giving me an error that it couldn't find the  .wine/drive_c/windows/system32/msvbvm60.dll after installing the vbrun  package that you suggested.

When I went to that directory, the .dll was there, so I decided to just press on with the E-sword install and see what happens.

Upon program launch, I could see the text, and the search worked.

Still want to run david_KT's script on the test computer and see if it works, and look at that further. 

But in the meantime, thanks for the link forrestcupp!

---

### Post by 1peter318 on 2012-04-13
I appreciate the hard work you put into getting E-sword to work under Linux, which for one as myself who is yet a Linux newbie seems quite complex. I just installed Mint 12 and and am using both native Gnome and also the KDE which i installed later, and am not sure if these old instructions would work on that. 

I also have not found any Linux programs that compare with what E-sword does, but   i am sure that someone has mentioned TheWord Bible program ([http://www.theword.net](http://www.theword.net))  which is comparable, and highly customizable, and has run fine for me under WINE. I would suggest  you take time to explore the options (one of which is that you can hit s on your kbrd to   toggle Strong's #s on the default). 

For more basic programs BPBible would be a good  a possibility if you can figure out why it does not run: [http://www.bpbible.com/download](http://www.bpbible.com/download) 

Likewise the old QuickVerse for Windows with King James Version (qv4nonav.exe) ([http://www.genesis.net.au/~bible](http://www.genesis.net.au/~bible))

---

### Post by david_kt on 2012-04-13
> **1peter318 said:**
> I appreciate the hard work you put into getting E-sword to work under Linux, which for one as myself who is yet a Linux newbie seems quite complex. I just installed Mint 12 and and am using both native Gnome and also the KDE which i installed later, and am not sure if these old instructions would work on that. 

You could try the installer at the first post of this thread, choose run in terminal. Please wait until the installer exit.

DK

---

### Post by sirkeith on 2012-04-18
I had e-Sword working well thru Wine in Lucid. Also had a dual boot going and had e-sword in XP. I took the leap and got rid of Windoze. I also lost e-Sword when I updated Wine. Anyway, have been using theWord for quite awhile now, with no problems in Wine. I keep retrying e-Sword and it is so off and on I gave up. TheWord works good and with a little adjustment on my part we get along good. Having good bible softwre and no Windows is incredibly freeing.

---

### Post by ubume2 on 2012-04-30
For the latest available E-Sword 10.10 the installer does not work. (Either blank pages or the search function does not work) Thanks to the solution provided by forrestcupp at:

[http://ubuntuforums.org/showthread.php?p=11673552#post11673552](http://ubuntuforums.org/showthread.php?p=11673552#post11673552)

 the search function works great.

Winetricks may have to be done twice before all of the dlls and the msi appear in .cache/winetricks.

Download the EXE file from [www.e-sword.net](www.e-sword.net) after you do all the necessary configurations mentioned in the post above

I also get the error message  mentioned by ScottyK7 in post 805, but e-Sword works fine, even with that message.


Another thanks to forrestcupp!:)

---

### Post by Lemuel111 on 2012-07-23
I've tried to follow the various threads for installation but still have having no success with the search function. I'm using the current edition of Wine as I have not been able to install Wine 1.0.1. Any help much appreciated.

---

### Post by ubume2 on 2012-08-13
> **Lemuel111 said:**
> I've tried to follow the various threads for installation but still have having no success with the search function. I'm using the current edition of Wine as I have not been able to install Wine 1.0.1. Any help much appreciated.

What version of Ubuntu are you using?

I don't think Wine 1.0.1 is available anymore.  It looks like 1.0.4 is the default install for Ubuntu 12.04.

 I think maybe the original solution in Post 1 is outdated. See posts 804,805, and Post 809 above.

I recommend deleting E-Sword if you used the installer script.  Make sure all instances of E-Sword are deleted in /home/user. If not, manually delete them. I also recommend deleting all instances of wine in /home/user.  Then remove Wine.

1. Reinstall Wine (Probably Wine 1.4)
2. Set up winecfg and winetricks as recommended in post 804. Winetricks can be       tricky.   You may have to do it twice.

3. Then manually install E-Sword which is available from the e-Sword website.

---

### Post by ctmusicstraps on 2012-09-11
Well, I am using Ubuntu 12.04 with Wine 1.5 . I have installed a few windows programs via Wine with no problems including Microsoft Office 2007 Enterprise business suite and the programs run fine.

I have used E-Sword for years, and LOVED the search function.  Well I downloaded the new e-sword 10.1 from the main e-sword website, and installed it.  Everything worked great EXCEPT the search function.  I even wrote RICK, and he replied I just needed to register my dlls. Well, I did not know which ones or how to go about that....so...

I came to this topic, and I have tried it BOTH ways with the auto installer and the method where someone installed from RICK's site and just reconfigured wine / wine tricks, etc. by installing the add-ons, and followed to the Microsoft site, etc. I even did the wine config TWICE.

Results: Now I can not even get e-sword to launch and though I have the files, the icon will not launch, nor is it recognized in Dash.  I have uninstalled it using BOTH methods and tried to reinstall it.  E-sword will say it is installed, but never launches.  So now I am in worst shape than I was.

Thing is most of the posts on this thread in the beginning were made like 5 years ago, so I can't help thinking that may be the problem.

Now I have the task of BACK-TRACKING to see which .dll or add on that I installed or changed.  CURRENTLY I have UNINSTALLED the e-sword program until I can figure things out.

~CT

---

### Post by ubume2 on 2012-09-13
@CT

Have you read posts 804, 805 and 809?  

I would try to install wine 1.4.

Completely remove all instances of E-Sword, then remove wine using synaptic or the command line. Check your /home/user file for any instances of the hidden files .wine .wine-esword. If they are present delete them. 

Install wine then configure it per this url:

[http://ubuntuforums.org/showthread.php?p=11673552#post11673552](http://ubuntuforums.org/showthread.php?p=11673552#post11673552)

Then manually install E-Sword.

Worked fine for me, but your results may vary.

---

### Post by ctmusicstraps on 2012-09-13
> **ubume2 said:**
> @CT

Have you read posts 804, 805 and 809?  

I would try to install wine 1.4.

Completely remove all instances of E-Sword, then remove wine using synaptic or the command line. Check your /home/user file for any instances of the hidden files .wine .wine-esword. If they are present delete them. 

Install wine then configure it per this url:

[http://ubuntuforums.org/showthread.php?p=11673552#post11673552](http://ubuntuforums.org/showthread.php?p=11673552#post11673552)

Then manually install E-Sword.

Worked fine for me, but your results may vary.


Yes. Following those posts is what caused my e-sword that was launching to no longer launch.  As for going back to Wine 1.4, I realize that was the last stable, but I moved to 1.5 because some suggestions before I installed my other windows programs - which by the way all work fine.  I just don't want to keep fooling around and mess those up too.

I will let you know if I get things fixed.

~CT

---

### Post by ctmusicstraps on 2012-09-18
> **ubume2 said:**
> @CT

Have you read posts 804, 805 and 809?  

I would try to install wine 1.4.

Completely remove all instances of E-Sword, then remove wine using synaptic or the command line. Check your /home/user file for any instances of the hidden files .wine .wine-esword. If they are present delete them. 

Install wine then configure it per this url:

[http://ubuntuforums.org/showthread.php?p=11673552#post11673552](http://ubuntuforums.org/showthread.php?p=11673552#post11673552)

Then manually install E-Sword.

Worked fine for me, but your results may vary.

OK, it looks like things are working great now!  

ubume2, I had followed the posts (804, 805 and 809) numerous times and even added the extra fixes, add-ons, etc.  I took YOUR ADVICE, and installed Wine 1.4.

I had been hesitant to remove my wine 1.5 (developer version) but finally out of frustration I thought - "Well, I can always re-install the other software if they get screwed up".

When I looked into uninstalling the wine 1.5, it wanted to remove all my wine installed programs so I did not go that route.  Instead I used the ubuntu software center and searched for Wine. It came up as 1.4 (stable version) so I chose to INSTALL it.  It warned me that in doing so it would have to remove (2) versions of wine 1.5, so I clicked INSTALL anyway.  It went through the process, installing 1.4 with add-ons.

I then UNINSTALLED e-sword via the official website exe, and also ran the auto-installer that Dave created and chose to remove the version it had installed. I then searched a few folders and removed the rest of e-sword directories under some hidden directories.

Next, (knowing I had already installed the dlls in the past) I decided just to RIGHT click on the esword 10 exe (downloaded right from Rick's website), which I had retained in my downloads folder, and chose to open with Wine. I followed the typical installer process with the wizard that comes up as you would any windows program.

It installed. It launched!

My SEARCH function WORKS!

SPECIAL NOTE: when the search box comes up and you enter a word, the "ok" button at the bottom right still appears greyed out. Do not worry, all you do it click the BINOCULARS icon in the top right, and a full SEARCH is performed, rendering your results!

THANKS guys!

It seemed my main problem was Wine 1.5 was not fully compatible with the files I had installed.  Once I returned to 1.4 all WORKS.

~CT

---

### Post by ubume2 on 2012-09-19
Fantastic!

And Good Luck.

---

### Post by geo316 on 2012-10-03
ok... all went well following the instructions in posts 804, 805 and 809.

e-Sword installed, runs, and searches just fine. I'm using 10.1.0 under Ubuntu 12.04 with Wine 1.4.

One annoyance though, the verses in the left pane do not highlight when I click on them, and most (maybe even all) of the verse links clicked in the right pane commentaries do not cause the left pane to go to the verse -it goes to the book and chapter, but not to the verse. 

If I click a verse and then switch translations the left pane does not stay on the verse. 

If I click a verse, the icons in the commentary tabs change (indicating available content) as they should, but the open commentary won't scroll to the text pertaining to the verse. 

It's as if the little "chain" icon were not clicked.

Any ideas anyone?

George

---

### Post by geo316 on 2012-10-27
Really? No one? not even a commiserate??

---

### Post by frank cox on 2012-10-31
E-Sword is great but The Word under Wine is idiot proof and very close.

---

### Post by padeco on 2012-11-24
hi there,
i have installed esword in ubuntu 12.04. systems are working fine, the only issue i had was the NET bible not showing any font etc. following the advice below (which i already had the DLLs) i only had to add it in the dll overrides!
great stuff!
thanks

> **david_kt said:**
> Last time the 8 version work very well, including the maps and text. Below is my notes on winehq:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14655&iTestingId=34011](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14655&iTestingId=34011)

```
Need to add msls31.dll from windows, copy riched20.dll from e-Sword directory to system32 directory, and add dlloverrides for riched20.dll and oleaut32.dll.
```

If you could find my older script for this purpose is the best (e-Sword_installer_211108.tar.gz).

DK

---

### Post by erngab on 2013-01-09
I haw a problem when install - 1152 error extracting to the temporary location

---

### Post by tak1150 on 2013-03-27
Got the same issue here... and it's reproducible on a few different distro.

---

### Post by david_kt on 2013-03-27
I am unable to edit the first post anymore. Please see attached updated installer, should work with wine-1.4.
I have checked using this installer:
1. Search function fully work
2. Download function fully work.
3. Graphic function fully work, at least download one graphic first to use it.

I have not checked other functions but all should work properly.

DK

---

### Post by jonathonblake on 2013-03-27
How about closing this thread, and continuing the discussion at [http://ubuntuforums.org/showthread.php?t=2129887&p=12576688#post12576688](http://ubuntuforums.org/showthread.php?t=2129887&p=12576688#post12576688), for reasons outlined there, and in some earlier posts in this thread?

jonathon

---

### Post by gneders on 2013-07-08
Thank you so much for the fix, I have been installing and uninstalling for days , and this fixed my search problem instantly, thanks again, gneders

---

### Post by ubume2 on 2013-07-19
> **gneders said:**
> Thank you so much for the fix, I have been installing and uninstalling for days , and this fixed my search problem instantly, thanks again, gneders

+1

---

### Post by Frank_Avallone on 2013-08-29
Greetings everyone,

I assume you are here because of the same search I have done.  Here is what I found in trying to install e-sword under wine.

First I am using Zorin 7.  Almost all features work in it for me including Wine 1.4.

 I read the above thread and the instructions to install oleaut32 to builtin then add the other dlls is correct for e-Sword 10.1 only (and below, I suppose).  Those instructions will not work with the latest e-Sword 10.2.  I tried a lot of things.  What tripped me up was I was installing esword for some customers on their new Linux boxes and I was successful on one but not the other.  I couldn't figure it out!  After days and hours of struggling I finally realized that Rick Meyers had updated to 10.2.

For each PC I simply went to the esword website and downloaded the program.  One day it was 10.1 the next it was 10.2.  My own installation of esword was working well but with extra dlls as per older threads.  So I decided to reinstall not realizing I was downloading 10.2.  I was stymied!!

So, until someone figures out how to get tooltips in bibles window and the search function working correctly under 10.2, be sure to install esword 10.1 and follow this:

[I]Hi Dave

 I have been running mint 11 and ubuntu 11.10. I am running wine 1.2.3 stable on both systems. The following has worked for me with both systems.

 Do this before installing E-sword:

 Set oleaut32 to builtin in winecfg

 In winetricks install

 msls31
 msxml3 *
 vbrun6
 vcrun6
 wsh57

 Once these are installed you can install E-sword and it should work.

 * To install msxml3 winetricks will open an MS download site where you can get the file. Once downloaded put it in: home/user-name/.cache/winetricks/msxml3

 To find the .cache type ctl-h while in your home dir to show the hidden files. You my have to reselect the files to have winetricks install them.


[/I]Let me know if you have success with the above instructions.

For His Glory,

Frank

---

### Post by david_kt on 2013-08-29
Frank,
Have you tried installer above ([http://ubuntuforums.org/attachment.php?attachmentid=240602&d=1364391904](http://ubuntuforums.org/attachment.php?attachmentid=240602&d=1364391904)) ?
It works with latest e-sword (10.2.1) and wine-1.6-rc3 .
So far only sermon audio did not work.
DK

---

### Post by david_kt on 2013-08-29
Double post.

---

### Post by Frank_Avallone on 2013-08-29
I don't know how to install the installer.  I actually tried the other day but I gave up.

Frank

---

### Post by david_kt on 2013-08-29
> **Frank_Avallone said:**
> I don't know how to install the installer.  I actually tried the other day but I gave up.

Frank

Download the installer and extract it, double click the extracted file and run it. 

DK

---

### Post by Frank_Avallone on 2013-08-30
When I do that gedit opens with the details of the installer.  Thanks.

---

### Post by david_kt on 2013-08-30
> **Frank_Avallone said:**
> When I do that gedit opens with the details of the installer.  Thanks.

You could see the instruction on the first post [http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042) :

After double clicked, make sure you choose run or run in terminal, do not choose display. Or, if the option not appear, right click to the extraced file:
Properties > Permissions > allow executing files as program

and after close the properties window, double click the file again.

Also make sure cabextract is installed: sudo apt-get install cabextract

DK

---

### Post by ma223y on 2013-09-12
Is there any way to make the installer work with wine 1.4?  When I try to use the installer I get the error "Esword_installer error: Note: command 'env WINEPREFIX=/home/manney/.wine_Esword ./winetricks mfc42' returned status 1. Aborting."   I then tried manually installing but when I try to run esword I get these errors,
err:module:import_dll Library oleaut32.dll (which is needed by L"C:\\windows\\system32\\windowscodecs.dll") not found
err:module:import_dll Library windowscodecs.dll (which is needed by L"C:\\windows\\system32\\winemenubuilder.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\winemenubuilder.exe" failed, status c0000135
err:module:import_dll Library OLEAUT32.dll (which is needed by L"C:\\windows\\system32\\MSVBVM60.DLL") not found
err:module:import_dll Library MSVBVM60.DLL (which is needed by L"C:\\Program Files (x86)\\e-Sword\\e-Sword.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files (x86)\\e-Sword\\e-Sword.exe" failed, status c0000135

The only version of wine 1.0.1 I could find was from oldapps.com

---

### Post by david_kt on 2013-09-12
> **ma223y said:**
> Is there any way to make the installer work with wine 1.4?  When I try to use the installer I get the error "Esword_installer error: Note: command 'env WINEPREFIX=/home/manney/.wine_Esword ./winetricks mfc42' returned status 1. Aborting."   

It should work with wie 1.4. Make sure you are connected to internet when running the installer. If it always fail although the internet connection is good, choose clear cache first, and the run it again.

DK

---

### Post by ma223y on 2013-09-13
My internet connection is fine.  I uninstalled and reinstalled several times, deleting the cache each time, still get the error "Esword_installer error: Note: command 'env WINEPREFIX=/home/manney/.wine_Esword ./winetricks mfc42' returned status 1. Aborting."  I then tried  env WINEPREFIX="/home/manney/.wine_Esword" winetricks mfc42, which returned Executing w_do_call mfc42 mfc42 already installed, skipping.  I then used your manual installation guide to see if everything installed properly.  Everything was except in env WINEPREFIX=~/.wine_Esword winecfg , under the libraries tab the oleaut32.dll and the riched20.dll were set at native, builtin.  I attemped to run esword and it launched, except the pop outs did not work and downloads would not start when downloading a dictionary.  When I changed oleaut32.dll and the riched20.dll to native, windows esword would not run at all.  
  Thank you for your response and any help you can offer me.

---

### Post by david_kt on 2013-09-13
> **ma223y said:**
> My internet connection is fine.  I uninstalled and reinstalled several times, deleting the cache each time, still get the error "Esword_installer error: Note: command 'env WINEPREFIX=/home/manney/.wine_Esword ./winetricks mfc42'.

I just realised you are using old installer. Please use the latest one downloaded from [here]("http://ubuntuforums.org/attachment.php?attachmentid=240602&d=1364391904"). The latest one does not require mfc42.

Before installing, make sure you remove the old using the installer.

DK

---

### Post by ma223y on 2013-09-13
The new installer worked, thank you.  The only remaining issue is the downloading of bibles/dictionaries/commentaries.  These still do not download.  I will leave esword running for awhile to see if they eventually download.

---

### Post by ma223y on 2013-09-13
Downloading Bibles/Dictionaries/Commentaries still not working, but everything else is.  Can anyone suggest an alternative download location for the free modules in the download section?

---

### Post by david_kt on 2013-09-13
> **ma223y said:**
> Downloading Bibles/Dictionaries/Commentaries still not working, but everything else is.  Can anyone suggest an alternative download location for the free modules in the download section?

Downloading should work. What stage of downloading is the problem? Selecting file or file selected but could not start downloading?

DK

---

### Post by ma223y on 2013-09-13
I can select a download, but the download never starts.  The status stays at Downloaded 0 KB, Percent 0%, Remaining 100 %, Rate 0.00 KB/s, exc.

---

### Post by david_kt on 2013-09-13
> **ma223y said:**
> I can select a download, but the download never starts.  The status stays at Downloaded 0 KB, Percent 0%, Remaining 100 %, Rate 0.00 KB/s, exc.

After select a download, you have to start it, click:

Download > Start

Have you started the download or just selecting the file to download? Only selecting the file to download will not download anything.

DK

---

### Post by ma223y on 2013-09-13
Thank you, although I sort of feel like a moron right now.

---

### Post by ma223y on 2013-09-19
Would you be able to tell me where wine e-sword stores its icons?  I've been Googling it and can't find the info anywhere.

---

### Post by david_kt on 2013-09-19
> **ma223y said:**
> Would you be able to tell me where wine e-sword stores its icons?  I've been Googling it and can't find the info anywhere.

You could download it from here:
[http://ubuntuforums.org/attachment.php?attachmentid=65806&d=1208046990](http://ubuntuforums.org/attachment.php?attachmentid=65806&d=1208046990)

Or

$HOME/.local/share/icons/hicolor/

DK

---

### Post by revdjenk on 2013-11-07
Trying to install to a new laptop... but after extracting the tar file, the installer fails with this report:
There is no setup program to install, please inform the maintainer of this script in ubuntuforum

---

### Post by david_kt on 2013-11-08
> **revdjenk said:**
> Trying to install to a new laptop... but after extracting the tar file, the installer fails with this report:
There is no setup program to install, please inform the maintainer of this script in ubuntuforum

There is a change in the e-Sword website, as such I need to modify the script. Please download the updated installer attached.

DK

---

### Post by revdjenk on 2013-11-08
Thanks david_kt !!  Quick and wonderful response!
I am still having the same problem I reported in September with Greek and Hebrew being rendered in nonsense letters.  Well, HOT is rendering correctly, but not HOT+. 
Here is Luke 23:33 in GNT-TR+
(Luk 23:33)  êáéG2532 CONJ  ïôåG3753 ADV  áðçëèïíG565 V-2AAI-3P  åðéG1909 PREP  ôïíG3588 T-ASM  ôïðïíG5117 N-ASM  ôïíG3588 T-ASM  êáëïõìåíïíG2564 V-PPP-ASM  êñáíéïíG2898 N-ASN  åêåéG1563 ADV  åóôáõñùóáíG4717 V-AAI-3P  áõôïíG846 P-ASM  êáéG2532 CONJ  ôïõòG3588 T-APM  êáêïõñãïõòG2557 A-APM  ïíG3739 R-ASM  ìåíG3303 PRT  åêG1537 PREP  äåîéùíG1188 A-GPF  ïíG3739 R-ASM  äåG1161 CONJ  åîG1537 PREP  áñéóôåñùíG710 A-GPF 
No, NA26 is doing this same thing, positing that it may have been an issue with just the versions with Strong's numbers.

As a side issue, maybe related, when I hover over the strong's number, I am not getting the popup, no matter which + version I have in the Bible window.

I did not install these, but copied over the modules from a backup file...could this be the problem?  edit: just installed GNT-WH+ from within e-sword...and same behavior.

I am running on LinuxMint 15 64bit on Acer S3-391 intel graphics (7 Series)  wine 1.41 e-sword 10.2.1

God bless
Doug

---

### Post by onlooker828 on 2014-07-22
Has anyone come up with a solution for the Strong's tool tips not working?  The scripture tool tips work fine, and if I type in a strong's reference in the editor, ie H30, the strong's tool tip will pop up, but not in the bible section itself.

Yes the option to display Strong's tooltips is on.

Any help would be appreciated.

---

### Post by peter161 on 2014-12-11
The steps from 
 	[**[COLOR=#000000]djh-compnet[/COLOR]**]("http://ubuntuforums.org/member.php?u=1260569") 	 
 						[IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG]  					 					 						First Cup of Ubuntu 					at 
[h=2]Re: E-Sword 10.3 and Ubuntu 14.04[/h]
[http://ubuntuforums.org/showthread.php?t=2238985&p=13175344#post13175344](http://ubuntuforums.org/showthread.php?t=2238985&p=13175344#post13175344)

worked well for me!!!!

Except I cannot get NET PRemium Bible to work.

---

