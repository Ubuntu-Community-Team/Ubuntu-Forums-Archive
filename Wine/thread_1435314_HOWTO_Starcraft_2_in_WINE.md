---
title: "HOWTO: Starcraft 2 in WINE"
date: 2010-03-21
forum: Wine
---

### Post by sandyd on 2010-03-21
I just finished the last of the testing on starcraft 2 (and the last patch testing)

as of right now, starcraft II is kinda usable, and I hope it will also be usable in the future when the real game comes out.

So, lets begin...

Firstly, you will need to download the game from blizzard (you have to have a beta invite to do so)

After downloading, place the file (or zip)(I dont remember what format it came in)
on the desktop. Extract it if necessary.
NOTE: the following instructions assumes the installer is named Installer.exe (in my case it is)

NOTE: Ive only tested this on the dev versions of wine, not the stable releases.

```

wget -c  [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)
chmod 667 winetricks
WINEPREFIX=~/.wine_starcraft ./winetricks droid fontfix fontsmooth-rgb gdiplus gecko vcrun2008 vcrun2005 allfonts d3dx9 win7
WINEPREFIX=~/.wine_starcraft winecfg

```go to the "libraries" tab.
enter in the box "mmdevapi"
find it in the "existing overrides" list, and click on it.
click edit and set to diabled.
go to the audio tab, and select alsa if you havent done so already.

navigate to where you put the starcraft installer, and 
```

ls
```using that output, identify the starcraft installer file (should end in .exe)
replace "starcraft_installer" with the starcraft installer file
```

WINEPREFIX=~/.wine_starcraft/ wine starcraft_installer
```While its applying the patches, ignore the error boxes that come up, their redundant and dont mean anything.
tada!

p.s. starcraft 2 doesnt work in windowd mode. still workin on that.

p.p.s. Ive omitted part of the howto becasue of some blurryness on the CoC. The full howto is avalible here: [http://www.carleedolphinaura.co.cc/software/starcraft-ii-wings-of-liberty-wineii-wings-of-liberty-wine/]("http://www.carleedolphinaura.co.cc/2010/04/05/starcraft-ii-wings-of-liberty-wine/")

---

### Post by Uncle Spellbinder on 2010-03-21
Thanks for the tutorial. But wouldn't it be better placed in [Tutorials & Tips](http://ubuntuforums.org/forumdisplay.php?f=100)?

---

### Post by sandyd on 2010-03-21
> **Uncle Spellbinder said:**
> Thanks for the tutorial. But wouldn't it be better placed in [Tutorials & Tips]("http://ubuntuforums.org/forumdisplay.php?f=100")?
im still waiting on the consensus that it works, so that I can update the starcraft 2 winehq page.

which is why im posting it here, so more people will see it.

---

### Post by _h_ on 2010-03-21
> **Uncle Spellbinder said:**
> Thanks for the tutorial. But wouldn't it be better placed in [Tutorials & Tips]("http://ubuntuforums.org/forumdisplay.php?f=100")?

Already a step ahead of you Uncle and reported it to a mod to move into either WINE or Tutorial forum, whatever they choose. :P

---

### Post by beastrace91 on 2010-03-21
Sweet! Thanks for the HOWTO. Waiting eagerly for my SC2 beta invite... Two of my friends have their's already so as soon as they get an invite key I get it :D

~Jeff

---

### Post by 1mrfab on 2010-03-22
Thx 4 guide however i get a permission denied when i come to
```
WINEPREFIX=~/.wine_starcraft ./winetricks droid fontfix fontsmooth-rgb gdiplus gecko vcrun2008 vcrun2005 allfonts d3dx9 win7
```what am i doing wrong ?

PS:Sorry for bad english

Does this tutorial works for online playing on battlenet ??

---

### Post by hugo87 on 2010-03-23
Didn't work with wine-1.1.38 (latest in fedora repos)
Seems like A **LOT** of work to compile the latest wine development  version.

```

[hugo@chaos-2 WingsofLibertyBeta]$ WINEPREFIX=~/.wine_starcraft/ wine Installer.exe 
err:wineboot:pendingRename couldn't get file attributes (3)
err:wineboot:pendingRename couldn't get file attributes (2)
err:wineboot:pendingRename couldn't get file attributes (3)
err:wineboot:pendingRename couldn't get file attributes (2)
err:wineboot:pendingRename couldn't get file attributes (2)
err:wineboot:pendingRename couldn't get file attributes (3)
err:wineboot:pendingRename couldn't get file attributes (2)
err:wineboot:pendingRename couldn't get file attributes (3)
err:wineboot:pendingRename couldn't get file attributes (2)
err:wineboot:pendingRename couldn't get file attributes (3)
err:wineboot:pendingRename couldn't get file attributes (2)
err:wineboot:pendingRename couldn't get file attributes (2)
err:wineboot:pendingRename couldn't get file attributes (2)
err:wineboot:pendingRename couldn't get file attributes (2)
err:wineboot:pendingRename couldn't get file attributes (2)
err:wineboot:pendingRename couldn't get file attributes (3)
err:wineboot:pendingRename couldn't get file attributes (2)
err:wineboot:pendingRename couldn't get file attributes (3)
err:wineboot:pendingRename couldn't get file attributes (2)
err:wineboot:pendingRename couldn't get file attributes (3)
err:wineboot:pendingRename couldn't get file attributes (2)
fixme:ntdll:NtPowerInformation semi-stub: SystemPowerCapabilities
fixme:font:CreateScalableFontResourceW (0,L"C:\\users\\hugo\\Temp\\Blizzard Installer Temporary Data - 000b7d6e\\EurostileExt-Med.fot",L"C:\\users\\hugo\\Temp\\Blizzard Installer Temporary Data - 000b7d6e\\EurostileExt-Med.ttf",(null)): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x15bac8,0x15b9c8): stub
wine: Unhandled page fault on write access to 0x063fa000 at address 0x4ffb2a (thread 0019), starting debugger...
[hugo@chaos-2 WingsofLibertyBeta]$ wine --version
wine-1.1.38
[hugo@chaos-2 WingsofLibertyBeta]$ 

```


All the inicial setup steps finished without issues.

---

### Post by sandyd on 2010-03-23
> **hugo87 said:**
> Didn't work with wine-1.1.38 (latest in fedora repos)
Seems like A **LOT** of work to compile the latest wine development  version.

```

[hugo@chaos-2 WingsofLibertyBeta]$ WINEPREFIX=~/.wine_starcraft/ wine Installer.exe 
err:wineboot:pendingRename couldn't get file attributes (3)
err:wineboot:pendingRename couldn't get file attributes (2)
err:wineboot:pendingRename couldn't get file attributes (3)
err:wineboot:pendingRename couldn't get file attributes (2)
err:wineboot:pendingRename couldn't get file attributes (2)
err:wineboot:pendingRename couldn't get file attributes (3)
err:wineboot:pendingRename couldn't get file attributes (2)
err:wineboot:pendingRename couldn't get file attributes (3)
err:wineboot:pendingRename couldn't get file attributes (2)
err:wineboot:pendingRename couldn't get file attributes (3)
err:wineboot:pendingRename couldn't get file attributes (2)
err:wineboot:pendingRename couldn't get file attributes (2)
err:wineboot:pendingRename couldn't get file attributes (2)
err:wineboot:pendingRename couldn't get file attributes (2)
err:wineboot:pendingRename couldn't get file attributes (2)
err:wineboot:pendingRename couldn't get file attributes (3)
err:wineboot:pendingRename couldn't get file attributes (2)
err:wineboot:pendingRename couldn't get file attributes (3)
err:wineboot:pendingRename couldn't get file attributes (2)
err:wineboot:pendingRename couldn't get file attributes (3)
err:wineboot:pendingRename couldn't get file attributes (2)
fixme:ntdll:NtPowerInformation semi-stub: SystemPowerCapabilities
fixme:font:CreateScalableFontResourceW (0,L"C:\\users\\hugo\\Temp\\Blizzard Installer Temporary Data - 000b7d6e\\EurostileExt-Med.fot",L"C:\\users\\hugo\\Temp\\Blizzard Installer Temporary Data - 000b7d6e\\EurostileExt-Med.ttf",(null)): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x15bac8,0x15b9c8): stub
wine: Unhandled page fault on write access to 0x063fa000 at address 0x4ffb2a (thread 0019), starting debugger...
[hugo@chaos-2 WingsofLibertyBeta]$ wine --version
wine-1.1.38
[hugo@chaos-2 WingsofLibertyBeta]$ 

```All the inicial setup steps finished without issues.
it works only in 1.1.41

you can also build it from git.

---

### Post by 1mrfab on 2010-03-23
I got 1.1.41

Update installed the by clicking on the exe file this worked before this guide to...

What does not work battlenet returning to desktop when logging in.

---

### Post by sandyd on 2010-03-23
> **1mrfab said:**
> I got 1.1.41

Update installed the by clicking on the exe file this worked before this guide to...

What does not work battlenet returning to desktop when logging in.

thats an issue were still working on. 
see
[http://www.carleedolphinaura.co.cc/blog/11-tutorials/6-starcraft-ii-wings-of-liberty-wine](http://www.carleedolphinaura.co.cc/blog/11-tutorials/6-starcraft-ii-wings-of-liberty-wine)

if you still want to play w/o battle.net

---

### Post by ROSS-MAX on 2010-03-25
How to do these below ?
-----------------------------------------
navigate to where you put the starcraft installer, and 

Code:
ls

using that output, identify the starcraft installer file (should end in .exe)
replace "starcraft_installer" with the starcraft installer file

Code:
WINEPREFIX=~/.wine_starcraft/ wine starcraft_installer

---

### Post by beastrace91 on 2010-03-25
> **hugo87 said:**
> Didn't work with wine-1.1.38 (latest in fedora repos)
Seems like A **LOT** of work to compile the latest wine development  version.

You need at least 1.1.40 from what I've seen... Compiling Wine from source is not hard on debian based distros, because you just run **sudo apt-get build-dep wine** 

Yum lacks this feature by default but maybe take a look into using [yum-builddep](http://linux.die.net/man/1/yum-builddep) package. Never used it personally, but looks like it might function for Wine to make your building process easy.

~Jeff

---

### Post by deadalnix on 2010-03-27
Maybe we can do a .pol file for playonLinux ?

Does anyone know how to do this ?

---

### Post by deadalnix on 2010-03-27
```
#!/bin/bash
# Date: (2009-08-21 19-25)
# Distribution used to test: Ubuntu - Karmic
# Wine version used: 1.1.41
# Author: Deadalnix

#fetching PROGRAMFILES environmental variable
PROGRAMFILES=`wine cmd /c echo "%ProgramFiles%"`
PROGRAMFILES=${PROGRAMFILES:3}

#Vérifier que PlayOnLinux est bien exécuté avant
[ "$PLAYONLINUX" = "" ] && exit 0

#Charger les librairies
source "$PLAYONLINUX/lib/sources"

Title="Starcraft2 : Beta"
Prefix="Starcraft2_Beta"

if [ "$POL_LANG" == "fr" ]; then
LNG_WAIT_END="Appuyez sur \"Suivant\" UNIQUEMENT quand l'installation du jeu sera
terminée sous peine de devoir recommencer l'installation."
else
LNG_WAIT_END="Click on \"Next\" ONLY when the game installation
is finished or you will have to redo the installation.."
fi

POL_SetupWindow_Init

#Presentation
POL_SetupWindow_presentation "$Title" "Blizzard" "http://www.starcraft2.com/" "Deadalnix" "$Prefix"

#Installation de Wine
POL_SetupWindow_install_wine "1.1.41"

#selectiond e wine
Use_WineVersion "1.1.41"

#Préparation de Wine
select_prefixe "$REPERTOIRE/wineprefix/$Prefix"
POL_SetupWindow_prefixcreate

#install some packages using winetrick
wget http://winezeug.googlecode.com/svn/trunk/winetricks -O "$REPERTOIRE/ressources/winetricks"
sh "$REPERTOIRE/ressources/winetricks" droid fontfix fontsmooth-rgb gdiplus gecko vcrun2008 vcrun2005 allfonts d3dx9 win7

#Taille de la mémoire graphique
POL_SetupWindow_textbox "Your Memory Graphic ?" "Memory Graphic"
VMS="$APP_ANSWER"

#Réglage DirectDrawRenderer
cd "$WINEPREFIX/drive_c/windows/temp"
echo "[HKEY_CURRENT_USER\\Software\\Wine\\Direct3D]" > OGL.reg
echo "\"VideoMemorySize\"=\"$VMS\"" >> OGL.reg
regedit OGL.reg

#Override dll
echo "[HKEY_CURRENT_USER\\Software\\Wine\\DllOverrides]" > override.reg
echo "\"mmdevapi\"=\"diabled\"" >> override.reg
regedit override.reg

#Configuration de Wine
Set_OS win7
Set_SoundDriver "alsa"

wine "$REPERTOIRE/ressources/Installer.exe"

POL_SetupWindow_message "$LNG_WAIT_END" "$Title"

#Création Launcher
POL_SetupWindow_make_shortcut "$Prefix" "$PROGRAMFILES/sc2beta/" "StarCraft II.exe" "" "$Title"

Set_WineVersion_Assign "1.1.41" "$Title"

POL_SetupWindow_Close
exit

```

To make it run in play on linux ;)

It have to be installed in Program Files/sc2beta to work, so be careful in the installation process.

---

### Post by cistym on 2010-03-31
Tried the walkthrough, didn't work for me. first tried it with wine 1.1.41 from source, but missing libwine.so.1 (i hate compiling from source, there's always stuff missing), reinstalled wine from repos, used the prefix and the winetricks, got sound working on the login screen, but closes after i put my email address in, not giving any errors in the terminal or a crash report.
thoughts? something i'm doing wrong?

---

### Post by sandyd on 2010-04-01
> **carlee said:**
> thats an issue were still working on. 
see
[http://www.carleedolphinaura.co.cc/blog/11-tutorials/6-starcraft-ii-wings-of-liberty-wine](http://www.carleedolphinaura.co.cc/blog/11-tutorials/6-starcraft-ii-wings-of-liberty-wine)

if you still want to play w/o battle.net

> **cistym said:**
> Tried the walkthrough, didn't work for me. first tried it with wine 1.1.41 from source, but missing libwine.so.1 (i hate compiling from source, there's always stuff missing), reinstalled wine from repos, used the prefix and the winetricks, got sound working on the login screen, but closes after i put my email address in, not giving any errors in the terminal or a crash report.
thoughts? something i'm doing wrong?
see above.
we seem to be having a lot of battle.net issues lately.....

and no, you havent done anything wrong. I cant log in either.

---

### Post by deadalnix on 2010-04-02
Please let me know any progress you made.

I have some issue know either with the new SC2 patch. If you find any workaround, I would be happy to integrate this into the PlayOnLinux script ;)

---

### Post by deadalnix on 2010-04-02
Ok, I think I have something here !

Have to make some tests and a tutorial if it work fine.

---

### Post by deadalnix on 2010-04-02
[http://bit.ly/d66ffj](http://bit.ly/d66ffj)

And then it run ;) Howevern plan to do it when you have free time, this is quite long.

---

### Post by 1mrfab on 2010-04-17
So battlenet is finally working but i had heavy graphic problems when i was following the tuturial on winehq so now i am trying to get playonlinux to work without the git package from winehq.how do i add the battlenet script to playonlinux?

Winehq tutorial: 
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=19376](http://appdb.winehq.org/objectManager.php?sClass=version&iId=19376)
:guitar:

---

### Post by Alatar1 on 2010-04-20
So i can't get this work...I got it installed but I am getting that bug where it quits when you put in your account name

*edit* what ive tried so far... is this [http://www.youtube.com/watch?v=ZBq8HLfsKTo](http://www.youtube.com/watch?v=ZBq8HLfsKTo) <--this one makes it so i can click the "agree" button on the EULA

and this [http://bugs.winehq.org/show_bug.cgi?id=21809...just](http://bugs.winehq.org/show_bug.cgi?id=21809...just) confuses the crap out me

---

### Post by ninja senses on 2010-04-27
I keep crashing on the login screen also

---

### Post by dbd on 2010-04-28
> **ninja senses said:**
> I keep crashing on the login screen also

That problem is mentioned on the HOWTO at the top of SC2's page on wine:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=19376](http://appdb.winehq.org/objectManager.php?sClass=version&iId=19376)

Looks like you need to apply a patch before compiling wine to get it to work.

(BTW: I've tried this, but when I use the version of wine I compiled SC2 won't even start. If I run the version in the repositories, then SC2 starts, but crashes on the login screen. I've tried going back to the version in the repo (1.1.43) and compilling that, but that doesn't help either.)

---

### Post by dkartik on 2010-04-28
It looks like I'm in the same boat as most people here as well.  It installs the application, downloads and installs the patches, but after the loading screen, it just quits out to the desktop with no error pop-up and I can't seem to find a log record anywhere.

If anyone has figured this out, please let me know.

I'm running a Dell Studio 1558 with an 1GB ATI Radeon Mobility HD5470 on Lucid RC.

---

### Post by rannel on 2010-04-29
I have followed the instructions from this video on Youtube by Deadalnix


at [http://www.youtube.com/watch?v=ZBq8HLfsKTo](http://www.youtube.com/watch?v=ZBq8HLfsKTo)

I followed the instructions but I cannot get the installer to launch and Im not sure why... any ideas, I have the beta code and I really want to play this game.

---

### Post by ninja senses on 2010-04-30
> **dbd said:**
> That problem is mentioned on the HOWTO at the top of SC2's page on wine:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=19376](http://appdb.winehq.org/objectManager.php?sClass=version&iId=19376)

Looks like you need to apply a patch before compiling wine to get it to work.

(BTW: I've tried this, but when I use the version of wine I compiled SC2 won't even start. If I run the version in the repositories, then SC2 starts, but crashes on the login screen. I've tried going back to the version in the repo (1.1.43) and compilling that, but that doesn't help either.)

Im getting this error:

can't find file to patch at input line 10
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|---
| dlls/kernel32/tests/debugger.c | 98 +++++++++++++++++++++++++++++++++++++++-
| dlls/ntdll/loader.c | 7 ++-
| 2 files changed, 101 insertions(+), 4 deletions(-)
|
|diff --git a/dlls/kernel32/tests/debugger.c b/dlls/kernel32/tests/debugger.c
|index 057b977..f9b3889 100644
|--- a/dlls/kernel32/tests/debugger.c
|+++ b/dlls/kernel32/tests/debugger.c
--------------------------
File to patch:

maybe im not in the right directory?  does anyone know which directory you need to be in to apply this patch?

---

### Post by dbd on 2010-04-30
> **ninja senses said:**
> maybe im not in the right directory?  does anyone know which directory you need to be in to apply this patch?

Yeah, you need to be in ~/wine-git Which the last command you entered should have taken you too.

Be sure to let us know if you get it working

Good luck :)

---

### Post by ninja senses on 2010-05-01
> **dbd said:**
> Yeah, you need to be in ~/wine-git Which the last command you entered should have taken you too.

Be sure to let us know if you get it working

Good luck :)

Yea I was in the wrong directory cause I went through the directions once before, so the command before was not running properly.  However I changed to the right directory and it still did not work :(

---

### Post by dbd on 2010-05-01
> **ninja senses said:**
> Yea I was in the wrong directory cause I went through the directions once before, so the command before was not running properly.  However I changed to the right directory and it still did not work :(

What error do you get now? It worked two days ago, so I doubt things have changed so much to break the patch already.

Did wine download correctly when you used the command:
```
git clone git://source.winehq.org/git/wine.git ~/wine-git
```

It might be worth deleting wine-git and starting again.

---

### Post by ninja senses on 2010-05-02
> **dbd said:**
> What error do you get now? It worked two days ago, so I doubt things have changed so much to break the patch already.

Did wine download correctly when you used the command:
```
git clone git://source.winehq.org/git/wine.git ~/wine-git
```

It might be worth deleting wine-git and starting again.

yea thats what Im thinking...how can I remove wine-git though?  google is comming up empty...

---

### Post by dbd on 2010-05-02
> **ninja senses said:**
> yea thats what Im thinking...how can I remove wine-git though?  google is comming up empty...

Well, it's just a folder. So either use your file manager, or the command:
```
rm -rdf wine-git
```

---

### Post by dbd on 2010-05-02
If you don't want to compile the source then you could try using Matthew Ernisse's package with the patch already installed:
> I have built a binary package of Wine 1.1.43 from a snapshot of the git repo from last night and included the sc2-login patch from the Howto post in this thread. It should be easier to install this than to build it yourself. You may fetch it from my PPA at the following address: 

edge.launchpad.net/~mernisse/+archive/ppa/+packages 

(Taken from [http://appdb.winehq.org/objectManager.php?sClass=version&iId=19376](http://appdb.winehq.org/objectManager.php?sClass=version&iId=19376) )

It doesn't work for me, but who knows, it might work for you :)

---

### Post by dbd on 2010-05-02
OK. I've just got it to work! I deleted my .wine folder, and then started SC without making any changes to the wine settings. The problem is that I have no sound, and also I have to delete .wine before every time I run it. Also, I'm still suffering from the stuttering bug I've been suffering from in Windows since patch 9, and the whole reason I'm using wine was to try and avoid that bug. Must be some kind of weird network issue.

---

### Post by ninja senses on 2010-05-05
> **dbd said:**
> If you don't want to compile the source then you could try using Matthew Ernisse's package with the patch already installed:


(Taken from [http://appdb.winehq.org/objectManager.php?sClass=version&iId=19376](http://appdb.winehq.org/objectManager.php?sClass=version&iId=19376) )

It doesn't work for me, but who knows, it might work for you :)

i downloaded and installed 
    *   wine_1.1.43-git20100421~ppa1_amd64.deb  (9.1 MiB)
    * wine-dev_1.1.43-git20100421~ppa1_amd64.deb (1.5 MiB)

still no luck...are you still having issues with the sound.  Im pretty sure you have to uninstall some driver in wine...its posted on the winehq starcraft2 page
edit - delting my .wine folder totally removed everything and wine will not work at all anymore, even after getting it from the repository
edit2:by going to the synaptic pacjkage manager and removing wine completley i am able to get an older version which runs but does not run SC2, although anytime I try to get the newest version of wine i get an error

---

### Post by Shannon_VanWagner on 2010-05-22
I was getting "Permission Denied" when running line 2 below. So I changed line 2. to the command shown in < > below and then was able to run step 3. Hope this helps someone.

1.) wget -c  [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)
2.) chmod 667 winetricks
< **chmod 755 winetricks** >
3.) WINEPREFIX=~/.wine_starcraft ./winetricks droid fontfix fontsmooth-rgb gdiplus gecko vcrun2008 vcrun2005 allfonts d3dx9 win7
4.) WINEPREFIX=~/.wine_starcraft winecfg

---

### Post by beastrace91 on 2010-05-22
Are you on SC2 now Shannon? We should play :)

~Jeff

---

### Post by Neo40 on 2010-05-24
Hi,

Just out of curiosity, are you playing SC2 in D3D mode or in OpenGL?
And how is the performance? Your settings are low, medium, high or ultra?

Thanks

---

### Post by epimeth on 2010-05-31
hi there people! has anybody gotten starcraft II working with the patch? I followed the howto, merged the wine patch, recompiled and the game crashes at exactly where the patch is supposed to fix....
I'm not sure where I get debug info from so let me know so I can post it...

---

### Post by beastrace91 on 2010-06-01
> **epimeth said:**
> hi there people! has anybody gotten starcraft II working with the patch? I followed the howto, merged the wine patch, recompiled and the game crashes at exactly where the patch is supposed to fix....
I'm not sure where I get debug info from so let me know so I can post it...

I have SC2 working under Wine 1.1.44 with the patch applied. I run it under D3D (the default setting)

~Jeff

---

### Post by slickeel on 2010-06-07
The Starcraft 2 Beta Wings of Liberty works great with Ubuntu Lucid Lynx here. I have made an howto on how i got it to work.

HOWTO:

[http://slickeel.wordpress.com/2010/06/02/starcraft-2-beta-wings-of-liberty-in-ubuntu-lucid-lynx-with-wine/]("Ive http://slickeel.wordpress.com/2010/06/02/starcraft-2-beta-wings-of-liberty-in-ubuntu-lucid-lynx-with-wine/")

---

### Post by qute on 2010-07-30
A little help.

I can install with sound for a little while.
I upgrade and start playing. But no sound.
ALSO: I can only play once. I cannot start the game again.

Any advice?

I tried this guide:
[http://slickeel.wordpress.com/2010/06/02/starcraft-2-beta-wings-of-liberty-in-ubuntu-lucid-lynx-with-wine/]("http://ive%20http//slickeel.wordpress.com/2010/06/02/starcraft-2-beta-wings-of-liberty-in-ubuntu-lucid-lynx-with-wine/")
It fails patching number 2.

And this guide:
[http://www.youtube.com/watch?v=ZBq8HLfsKTo](http://www.youtube.com/watch?v=ZBq8HLfsKTo)
Fails with this message:
Note: command 'wine /home/qute/.winetrickscache/vcrun2008-ms09-035/vcredist_x86.exe' returned status 66.  Aborting.


Thanks.

---

### Post by Mas0ne on 2010-08-01
> **qute said:**
> A little help.

I can install with sound for a little while.
I upgrade and start playing. But no sound.
ALSO: I can only play once. I cannot start the game again.

Any advice?

I tried this guide:
[http://slickeel.wordpress.com/2010/06/02/starcraft-2-beta-wings-of-liberty-in-ubuntu-lucid-lynx-with-wine/]("http://ive%20http//slickeel.wordpress.com/2010/06/02/starcraft-2-beta-wings-of-liberty-in-ubuntu-lucid-lynx-with-wine/")
It fails patching number 2.

And this guide:
[http://www.youtube.com/watch?v=ZBq8HLfsKTo](http://www.youtube.com/watch?v=ZBq8HLfsKTo)
Fails with this message:
Note: command 'wine /home/qute/.winetrickscache/vcrun2008-ms09-035/vcredist_x86.exe' returned status 66.  Aborting.


Thanks.

Try this and see if it helps you in anyway:
[http://www.zealouscraft.com/index.php/linux/35-gaming/48-starcraft-2-on-linux](http://www.zealouscraft.com/index.php/linux/35-gaming/48-starcraft-2-on-linux)

---

### Post by LutraMan on 2010-08-01
Hi,
I can't install.
I'm getting a C++ runtime error about 52% into the installation.

I've just bought the SC2 cd, and I executed the Install.exe file only after I copied it all to my HDD, because if I try to run it directly, it doesn't do anything.

this is the output:
```
d 0034), starting debugger...
Process of pid=0019 has terminated
No process loaded, cannot execute 'echo Modules:'
Cannot get info on module while no process is loaded
No process loaded, cannot execute 'echo Threads:'
process  tid      prio (all id:s are in hex)
0000000e services.exe
	00000029    0
	00000014    0
	00000010    0
	0000000f    0
00000011 winedevice.exe
	00000018    0
	00000017    0
	00000013    0
	00000012    0
0000001b explorer.exe
	0000001c    0
You must be attached to a process to run this command.
No process loaded, cannot execute 'detach'

```
this is only the part when I'm getting the error, I've left out a lot of redundant fixme messages.

---

### Post by urbanus on 2010-08-01
I'm running a machine with a ATI HD 4870X2 and the Catalyst 10.7 driver. But when starting StarCraft 2, the graphics are all wrong in the login screen part, the terran face shown first is ok.

Anyone else got this problem?

tl;dr: starcraft 2, ati, corrupt graphics

---

### Post by gloken on 2010-08-10
> **urbanus said:**
> I'm running a machine with a ATI HD 4870X2 and the Catalyst 10.7 driver. But when starting StarCraft 2, the graphics are all wrong in the login screen part, the terran face shown first is ok.

Anyone else got this problem?

tl;dr: starcraft 2, ati, corrupt graphics

The menus and load screens look great to me. After I start a campaign I can see video corruption in the intro video, and the menu screen for the campaign itself is all corrupted and missing text and textures.

This is with latest Catalyst drivers for ATI and a latest WINE.

I don't know if that relates to your problem, but it's the same driver and situation.
Anyone have any thoughts on this?

---

### Post by gloken on 2010-08-11
> **gloken said:**
> The menus and load screens look great to me. After I start a campaign I can see video corruption in the intro video, and the menu screen for the campaign itself is all corrupted and missing text and textures.

This is with latest Catalyst drivers for ATI and a latest WINE.

I don't know if that relates to your problem, but it's the same driver and situation.
Anyone have any thoughts on this?

For the record, my problems were solved by moving to a nvidia card. 
ATI is a problem.

StarCraft runs great for me now, with no problems at all. FPS could be better, but I wasn't expecting perfection and I can live with low graphics.

Thanks for the tips.

---

### Post by AChunkee on 2010-08-11
Ok my starcraft 2 works while running on ubuntu 10.04 with WINE but whenever I try to go to medium graphic settings my game always crashes!!!! im stuck on low settings. the fps is pretty darn good though I have to admit. I have an Nvidia gtx460 graphics card which should be able to run starcraft 2 on ultra no problem. I have the latest drivers installed for my card straight from nvidias website. I have no audio problems or startup problems what so ever just can't get my game to run on better graphics settings. Compiz is disabled. Anyone know how to help?

---

### Post by urbanus on 2010-08-12
I was partially able to solve my problems.

Wine and StarCraft 2 created a folder named "StarCraft II" in my home folder. It contains a file named "Variables.txt", so I changed some of it's settings so it would load with them (I have had problems with video corruption, so reaching the options menu is problematic).

I changed the following:
width=1024
height=768
GraphicsOption...(All of them)=0

This enables me to use start the game and play. The framerate is however unusable. It advices me to lower the settings, but they are already at their lowest, hehe.

My hardware:
Ati HD4870x2
QuadCore 2.8 ghz
8 GIG Ram
2 x 298GB HDD's in software Raid0

---

### Post by gloken on 2010-08-12
> **urbanus said:**
> I was partially able to solve my problems.

Wine and StarCraft 2 created a folder named "StarCraft II" in my home folder. It contains a file named "Variables.txt", so I changed some of it's settings so it would load with them (I have had problems with video corruption, so reaching the options menu is problematic).

I changed the following:
width=1024
height=768
GraphicsOption...(All of them)=0

This enables me to use start the game and play. The framerate is however unusable. It advices me to lower the settings, but they are already at their lowest, hehe.

My hardware:
Ati HD4870x2
QuadCore 2.8 ghz
8 GIG Ram
2 x 298GB HDD's in software Raid0

Some people will disagree with me, but I really don't think it's worth your time trying to get the thing to work with an ATI card. The driver support just isn't there.

...but I also realize that most people are going to be reticent to throw out expensive hardware, so maybe somebody else has better advice.

Are you running Lucid?
What kernel? Kernel seems to matter a LOT with the Catalyst drivers and SC2.

---

### Post by urbanus on 2010-08-12
I'm running Linux Mint 9 (fully updated), but unsure of what kernel since i booted back into Windows 7.

The thing is that I like to try and make things work, and I like Linux. But I knew even before I started that the chances it would work where REALLY slim. StarCraft played smoothly thou :-P

I guess I'm stuck in Windows 7 (which isn't all that bad really) unless I want to dual boot, and I don't like dual booting to switch application :-/

---

### Post by gloken on 2010-08-12
> **urbanus said:**
> I'm running Linux Mint 9 (fully updated), but unsure of what kernel since i booted back into Windows 7.

The thing is that I like to try and make things work, and I like Linux. But I knew even before I started that the chances it would work where REALLY slim. StarCraft played smoothly thou :-P

I guess I'm stuck in Windows 7 (which isn't all that bad really) unless I want to dual boot, and I don't like dual booting to switch application :-/




Here's how you can get your kernel:

>     uname -a : print all information

    uname -r : print the kernel release

    uname -v : print the kernel version

    uname -o : print the operating system

And here's how you can install the latest kernel:

> [http://www.ramoonus.nl/2010/08/linux-kernel-2-6-35-installation-guide-for-ubuntu-linux/](http://www.ramoonus.nl/2010/08/linux-kernel-2-6-35-installation-guide-for-ubuntu-linux/)


My understanding is that the 2-6-35 has better support for ATI drivers, and that some people have had issues with StarCraft on some kernels. (I can't find a link to confirm the StarCraft issues, so maybe someone can corroborate this!)

I know that's not enormously helpful, but maybe it'll get you somewhere.
Dual booting wouldn't be an option for me either. StarCraft 2 will run in WINE, but frankly the Catalyst drivers are working against you there.

---

### Post by urbanus on 2010-08-12
> **gloken said:**
> StarCraft 2 will run in WINE, but frankly the Catalyst drivers are working against you there.

mhm.....amen to that :(

---

### Post by gloken on 2010-08-12
I picked up a few tips for getting better performance out of NVIDIA drivers. I haven't tried them all yet, but I thought I'd post them here for the benefit of anyone running it:

1) Update to the latest drivers:
> 
**Update** 256.44 are now the latest

SC2 is quite the resource monster, these drivers gives you a huge perfomance improvement over the older default Ubuntu ones. Open a terminal, alt+f2 and type in gnome-terminal.
Then, copy and paste the line below.

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

Hit enter and then copy and paste.

sudo apt-get update && sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings

Then go to System > Administration > Hardware Drivers and make sure Nvidia 256.35 graphics drivers are activated.

2) Disable UseGLSL in WINE.

'UseGLSL' to disabled
[http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys)

Reportedly this should cause a very significant speed increase.

3) Vista Compatibility mode in WINE.
I don't know about that one... doesn't seem like a very good approach, I'm much more comfortable with editing specific things in the WINE registry. Who knows, haven't tried it.

4) Someone on the WINE forum suggested enabling OpenGL and pbuffer. 
I read elsewhere that OpenGL doesn't work with it, so again, can't vouch for that.

I listed the tips in order of reliability, as you've no doubt noticed if you've read this far. Good luck.

---

### Post by gloken on 2010-08-14
Anyone having an issue with strange, intermittent crashes?
I've been plagued with them about once every couple hours, usually while loading a level.

And then this: [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1553055](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1553055) 

...I'm not saying the last error is related, but I'm not saying it isn't either.

Update: Unless this happens again, I'm calling it hardware failure.

---

### Post by aigarius on 2010-08-29
If anyone is having problems with the downloader crashing during update, just close the crash message and wait a bit. When you do see that the downloader stops working (no traffic and no download progress for a minute, even at 0 Mb remaining) the open a terminal and use 'killall -9 BlizzardDownloa'. I had to do that quite many times during initial install and patching.

The downloader would 'crash', then it would download a few more megabytes and stall, then I kill it and the patcher restarts it, it ddownloads a few megs, crashes, stalls and it repeats. But at least it does go forward.

---

### Post by evil_urna on 2010-08-31
It runs like a dream for me. My only problem is that I have some black bars that are an inch wide crossing the map that wont go away. I am not sure whats wrong there. Any ideas? 

I have a NVIDIA gt240 graphics card with the most recent drivers I am running Ubuntu 10.1 x64, Phenom 8950,

---

### Post by calthefish on 2010-10-20
I know this forums been dead for a couple of months but I really want to play SC2 so thought I might as well try. 

I can install and start SC2 without any trouble but when I try to start the campaign no video plays during the cut-scene, I just get the sound. When I actually start the first mission I get a blank screen with menus and sound.

I'm running it on a Dell inspiron 1525 with an Intel Mobile GM965/GL960 Integrated Graphics Controller.

---

### Post by qualtch on 2010-11-06
SC2 installation worked flawlessly on my PC via PlayOnLinux (couldn't see texts in installation, but I managed to guess where the buttons needed were). Though, I have AMD Radeon HD 5770 1GB GFX card (using Ubuntu 10.10, AMD's proprietary drivers installed via Ubuntu with Wine 1.3.6) and I'm having issues everywhere but in the main menu.

So, the menu works properly but everything after menu doesn't: Text in the loading screen is partly missing and when in-game, I can't see any units or structures - only the map. Also every time when I quit the game it crashes my PC...

I guess the problem with seeing only units was already marked as a bug with 'NEW' status in WineApp DB, so I'll just have to wait for a fix. :)

EDIT:

These are the bugs I'm experiencing myself right now:
[Missing letters and numbers in Starcraft II]("http://bugs.winehq.org/show_bug.cgi?id=24097")
[Starcraft II - In game, can only see the map.]("http://bugs.winehq.org/show_bug.cgi?id=22971")

Though the crashing when exiting weren't listed yet I think.

---

### Post by txitxi on 2010-11-06
Wow I cant believe game as heavy as this will work on linux.
Wish wine full support every windows application
:D

---

### Post by Dave999 on 2010-11-14
Hi, everyone! I've played a few sc2 games and I have problems to move the camera left and right. Up and down is no issue. But when it comes to left and right it seems that the cursor is visible from ubuntu(9.xx) desktop instead of sc2 cursor. Anyone else have this problem? any solution?

Thx

EDIT: found this thread. [http://ubuntuforums.org/showthread.php?t=1554995](http://ubuntuforums.org/showthread.php?t=1554995)

No solution for this bug?

---

### Post by Dave999 on 2010-12-04
facing problems when I'm trying to update with the latest patch from blizzard.

the download jump to 100% immediately and after that nothing happens. So i reboot my computer and try again. now as smaller window appear. "Blizzard updater" and the text "waiting for files to close" but nothing happens.

anyone else facing this problem or have any solution?

---

### Post by herbyg on 2011-03-30
> **AChunkee said:**
> Ok my starcraft 2 works while running on ubuntu 10.04 with WINE but whenever I try to go to medium graphic settings my game always crashes!!!! im stuck on low settings. the fps is pretty darn good though I have to admit. I have an Nvidia gtx460 graphics card which should be able to run starcraft 2 on ultra no problem. I have the latest drivers installed for my card straight from nvidias website. I have no audio problems or startup problems what so ever just can't get my game to run on better graphics settings. Compiz is disabled. Anyone know how to help?

I know this was posted a long time ago, but the fix for this is to set the VideoMemorySettings emulation keys in the Wine registry.  Using the Wine environment where you Starcraft II is installed, run regedit.  Once the Registry Viewer is visible, go to HKEY_CURRENT_USERS, and if it doesn't exist already, create a "Direct3D" key under "HKEY_CURRENT_USER/Software/Wine".  Within "Direct3D", create a string value whose name is "VideoMemorySize" and set the value to be however much video mem your video card has, in megabytes.  So if your card has a gig, set it to 1024.

You'll find more info here: [http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys)

---

### Post by RootsLINUX on 2011-05-11
Anyone having problems with the F10 key? I just played my first multiplayer match in Wine and everytime I hit F10, instead of bringing up that menu it would instead bring up the Wireless Connection Settings from my Ubuntu desktop (?). All the other function keys worked fine. May have been because I was running in Ubiquity. I switched back to classic (for sanity's sake) but don't know if that's going to make a difference.

---

### Post by 8Kuula on 2011-05-11
Ubuntu UI shortcut keys are handeled first, had similar problem with D2, alt+mouse1 wanted to move window instead showing up loot labels and picking them up.

So easiest way is to change wireless connection shortcut key.

---

### Post by RootsLINUX on 2011-05-12
Actually I fixed it by using the classic desktop instead of Unity (which I was already planning to abandon anyway). Now the game runs fine, except for the performance. Its good enough for single player but the lag is too strong to micro effectively in multiplayer matches.

---

