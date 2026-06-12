---
title: "Installed Office 2007: Few Questions"
date: 2011-02-01
forum: Wine
---

### Post by mixint27 on 2011-02-01
So i just installed office 2007 following the instructions from winehq.com. i also followed the post installation instructions:
-------------------------
[SIZE=4]_**Post Installation Instructions***_[/SIZE]
   Once installed, one override is necessary. Without it, Powerpoint  and Infopath with not start, and some dialog boxes in other Office apps  will not display correctly. Follow the steps below:                                                             

   Open ***winecfg*** by going to ***Applications > Wine > Configure Wine***. Or open a terminal and type:                                                                  

   winecfg                                                                      

   In the ***Libraries*** tab in the area labeled "*New override for library*" type in **riched20.dll** and click on ***Add***.
   You will see it appear in the list below. Now select the **riched20** in the list that we just added and click on the **Edit** button.
    Set it to **Native (Windows)** and click OK.
   This will allow Powerpoint and the other applications to run correctly.
   **Note :**Do not install riched20 with winetricks. Office 2007 installs its own  version of riched20. 
   If Office is installed in a separate wineprefix, you can safely set  the override globally. If not, set the overrides separately for each  Office application.                                                                                               
------------------------

Do i need to do anything else? Any other tweaks I need to do to run word, excel, powerpoint smoothly? I have wine version 1.2.2. Im not experiencing problems yet; powerpoint crashed on me once. i closed it, opened it again and it was working fine. i got an error about wine being the issue that it crashed. but like i said, after the crash it was running fine again.



Thank you! ):P

---

### Post by marl30 on 2011-02-01
Install core fonts using Winetricks, as well as turn on font smoothing RBG. Install Tohoma fonts as well. There is also another addon you would need to get the dictionery working. Can't remember it off the top of my head since I'm currently browsing from my mobile phone. 

Type winetricks in terminal and hit enter to launch winetricks. If it's not installed go to Synaptic, type in winetricks and install it.

---

### Post by mixint27 on 2011-02-01
[LEFT]if you could tell me what other addons i need i would appreciate it. thank you![/LEFT]

---

### Post by mixint27 on 2011-02-04
bump!

---

### Post by ronnielsen1 on 2011-02-04
> 
Do i need to do anything else? Any other tweaks I need to do to run word, excel, powerpoint smoothly? 

What part are you having trouble with. You need to go to the individual web winehq pages and see if there's tweaks
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992)

[word:]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=12811")

> 
[LIST]
[*]Beginning with 1.1.42, the add-in to save as PDF/XPS works. Do  not install it in earlier versions, as it did not work and was reported  to prevent Word from being able to save files.
[*]Set riched20 to native (needed for correct display of some  dialogs) and usp10 to native, builtin (needed for equation toolbar)  after installing. There is no need to copy the dlls, as Office 2007  installs its own versions, but the overrides must be set in winecfg in  order for Wine to use them.  These overrides should not be set globally  unless Office is installed in a separate wineprefix.
[*]The thesaurus needs Windows Scripting Host 5.6 (jscript); use winetricks wsh56js to install it.
[*]Beginning with 1.1.16, Wine includes its own symbol.ttf, so there is no longer a need to install it separately.
[*]The problem with bullets and numbering not working was fixed as  of 1.1.11, but requires a fresh install under that version or later. If  you do not wish to upgrade and/or reinstall, the workaround (for the  English version, at least) is to go into Word Options, Language Settings  and delete all languages other than U.S. English.
[*]The default bullet characters are from Wingdings. If you want them to look the same as on Windows, install that font.
[/LIST]


[Excel:]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=12812")

> After installing, set riched20.dll to native (needed for some dialog  boxes and numbers on graphs to display properly). It is not necessary to  install the dll, as Office installs its own version. Do not set this  override globally unless you have Office installed in a separate  wineprefix.
   To use the thesaurus, install winetricks wsh56js.                 

[Powerpoint:]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=12813")

> In order to run Powerpoint 2007, you must set riched20.dll to (native) in winecfg. Note that you do **not **have  to copy the dll from a Windows partition or use winetricks to install  it. Office 2007 installs its own version of richedit in a private  directory, but Wine will not use it unless you set the override.  Do not  set the override globally unless you have Office installed in a  separate wineprefix.          
[LIST]
[*]To get the thesaurus to work, install Windows Scripting Host with winetricks wsh56js.*                                                        
*
[*]The default bullet characters are from Wingdings. If you want them to look the same as on Windows, install that font.
[*]For mp3 sound to play out of the box, you must have 32 bit  libmpg123 installed on your system and Wine must have been compiled with  mp3 support. Not all distro packages provide this. *The workaround for  lack of winemp3.acm is to use the codec installed by WMP9,  l3cod*eca.acm. Copy l3codeca.acm to the  wineprefix's /windows/system32 directory (or use winetricks to install  WMP9), then create a symlink to it named winemp3.acm in *the same  directory. *
[*]To insert movies (wmv or avi), you must have WMP9 and the  necessary codecs  installed in the same wineprefix. Use winetricks to  install WMP9.* The K-Lite Codec Pack or the Combined Community Codec  Pack both *work well for installing the codecs. *      
[*]Bug 19797 is fixed as of 1.2-rc2. To work around it in earlier  Wine versions, rotate text using Text direction=>More options=>3D  rotation.*       *                                                                             
[/LIST]


[Access:]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=16862")

> Currently, Access will install but not start up (bugs 18889 & 1*9297). There are two known workarounds (tested in 1.1.33): 
   **Workaround 1:**(preferred method, as it does not remove any dependencies)     

   
[LIST=1]
[*]Use a resource editor to extract the manifest from ACEDAO.DLL  (you will find it in the same directory as msaccess.exe). (I used  Resource Tuner; it has a free trial and runs well under Wine.)
[*]Save the extracted manifest as acedao.manifest in the same directory as msaccess.exe.
[*]Delete or rename the ACEDAO.DLL located in that directory.  (There is another copy in another directory--no need to change it.)
[/LIST]


[One Note:]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=12899")

> This program crashes when run in Vista or 7 mode but works ok in XP mode.


---

