---
title: "Magix Music Maker &amp; Wine"
date: 2012-06-26
forum: Ubuntu Studio
---

### Post by Eplanet on 2012-06-26
ok, so finally linux is installed on one of my computers!!

now why isnt magix music maker basic edition working?

i installed ubuntu, many updates (i'll finish, but they dont seem to apply), then went and installed the first/main wine package.

it stalls at 89% (where it calls for 3rd party database install, firebird sql). a relaunch will install a couple more files to 90%...then its magically finished.

clicking the desktop icon does nothing. wine works with one other small file, so wine base is installed ok.

and i know there is one or two good linux multi-track studios, but i need to finish this project with this program. i also have an xp cd, but would need to install sp2 for this program.

thanks:guitar:

---

### Post by sgx on 2012-06-26
It 'probably' wont, but in case its just an alsa missing problem,
use the command

wine regedit

and edit the registry, which maybe incorrect. Go to

HKEY_CURRENT_USER and go down through the folders

Software

Wine

Drivers

Winealsa

set the first line to alsa, not jack, or default

close the editor, reboot, and try to start your app by its name.

wine /home/you/.wine/drive_c/Program Files/Magix/magixcreator.exe

substitute your username, path, and .exe title.

As a general rule, use Reaper, or the windows version of energyXT.
A few have been OK using Podium, Bidule, FLStudio, with Reaper
being the one stable for a few years now, for basic multitrack
recording. Some users report massive projects working fine.

wine has never had audio production as a main goal, rather, games,
and commercial office apps. Apps requiring lots of windows
accessories, and 3rd party support software, will fail, as well
as items with weird copy protection, or dongles.

Cheers

---

### Post by Eplanet on 2012-06-27
"The problem with designing something completely foolproof is to underestimate the ingenuity of a complete idiot." (Douglas Adams)=D>

this was posted by the guy who made some sort of patch for something wine related....i have no idea if it applies to my problem or not, although the wine admin suggested it....wow, the patch guy really has it in for ubuntu. i posted this at the wine forum also.:evil:

:-({|=so, idk, i am supposed to compile it, that is if my 1.5.7beta version doesnt fix it....except i have to figure out how to manually install it since adding a ppa line to my software browser/installer didnt do anything to let me browse what wine versions are available.](*,)

oh, i put that quote there, because u didnt say how to regedit....terminal command line didnt do anything, and there wasnt anything in the wine start menu folder. ;(](*,)

:popcorn:

---

### Post by sgx on 2012-06-27
wine regedit

starts the registry editor, unless there is something
very broken in your wine system.

The Magix installer might even have broken something. You can
rename the .wine folder to oldwine etc, and install a different wine
version, or reinstall the current version, and start again. You'll
get a new .wine folder to use when use run a winecfg or other wine command.

I don't think Magix will work, (happy if it does) but that is a way forward, without risk.

Cheers

---

