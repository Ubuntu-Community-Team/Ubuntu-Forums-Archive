---
title: "Sonar LE from Boss ME-25 on Linux with Wine?"
date: 2012-05-05
forum: Ubuntu Studio
---

### Post by sirriffsalot on 2012-05-05
Hey!

I've had this guitar effect panel from boss (ME-25) for a while and am enjoying it very much. But more than most and littler than much do I want to have windows touch my computer more than necessary, haha:)

I wonder if anyone has any idea if the Sonar LE software that comes along with the Boss ME-25 is in any way functional with Wine? When I try to run it in Wine I get an error simply stating "File not found", and judging from the little coverage or even mention of requests/hints on the web I fear hope is dim, but nonetheless I'll make sure here.

Virtual machine just wouldn't be practical because I'd have to reinstall things every time and I'd have to move the recorded files from the virtual machine to the real install (Ubuntu) anyway... So hope someone has a solution!

Thanks for reading:)

--> Leo

---

### Post by sgx on 2012-05-05
Hi, run the installer from a terminal, and if it fails,
look in the window for complaint of missing .dlls, which are
easy to get, and put in .wine/drive_c/windows/system32/
If it appears to stall, check behind open windows for
popups.

You can also copy the cakewalk folders/apps from their
windows haunts, to the equivalents in .wine.

The windows Documents folder in wine used to be set as your
/home/username folder, but I make sure the full paths are all
manually created, some experiments usually need to be run.

Their Rapture, z3ta, Triangle and Triangle II installers and
vsts work, I doubt the daw will work like reaper does,
but 20 minutes of sneakernet may yield a nice surprise.
The paths you make will be useful sooner or later.
Cheers

---

### Post by sirriffsalot on 2012-05-06
```
fixme:setupapi:CMP_WaitNoPendingInstallEvents 0
wine: Unhandled page fault on read access to 0x00000020 at address 0x4147ec (thread 0023), starting debugger...
```

That's the output I get from running the installer... Also comes a "Program Error" window from Wine saying "The program Setup.exe has encountered a serious problem and needs to close. We are sorry for the inconvenience. This can be cause by a problem in the program or a deficiency in Wine..." etc etc

As for the rest the terminology you used got the better of me, and I could not understand half of it... Gonna do some searching in relation to what you told me to do, but a more thorough explanation would be very helpful, haha :-) Cheers!

---

### Post by sgx on 2012-05-06
these .dll files, easy to find in google, or your windows
partition, and should added to

/home/leo/.wine/drive_c/windows/system32 

and may help the installer, and various apps and plugins.

gdiplus
mfc42
mfc71
msvcp60

mscvsc60
msvcp71

msvcr71
msvcr80

msvcp90

msvcr90

look in the windows drive, and find all the places
where Cakewalk puts files. Copy them on a media,
(sneakernet from the '90s) and copy them in the duplicated
locations you make in linux .wine folder, using a file manager
like nautilus, pcmanfm, konqueror, etc.
Windows C:\ is linux .wine/drive_c/

or use terminal commands cd (cd is short for change directory)

cd .wine/drive_c/Program*Files  then

mkdir Cakewalk   (mkdir is short for make directory)

----------------------------------------------------------------

In terminal commands, ALL blank spaces in windows paths must be
filled with a *  it is sometimes tedious...

Program*Files/Native*Instruments/Guitar*Rig*5/Guitar*Rig*5.exe

-----------------------------------------------------------------

running the z3ta+ installer, would create

/home/leo/.wine/drive_c/Program Files/Cakewalk
/home/leo/.wine/drive_c/Program Files/Cakewalk/z3ta+
/home/leo/.wine/drive_c/users/Public/Application Data/Cakewalk/z3ta+
/home/leo/.wine/drive_c/Program Files/Steinberg/VstPlugins/z3ta+

Reaper wisely places everything in one folder, which can
go in /home/leo for convenience, and ignores teh eeevil registry

cheers
also, try different wine versions,  perhaps
falkTX, if this all fails.

[https://launchpad.net/~falk-t-j/+archive/festige](https://launchpad.net/~falk-t-j/+archive/festige)

---

