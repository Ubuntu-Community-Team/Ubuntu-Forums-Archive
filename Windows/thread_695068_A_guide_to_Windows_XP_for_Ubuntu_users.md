---
title: "A guide to Windows XP for Ubuntu users"
date: 2008-02-12
forum: Windows
---

### Post by cudjoe on 2008-02-12
Hi guyz,

... please don't hit me ! (I know this a Ubuntu forum)

Here is my story : I have been using Linux for years and I just got employed in a company where all desktop computers are under Windows. No way to change, all tools depend on MS stuff.

Before thinking of resigning, I would like to know if you guyz have setup tricks in order to make Windows usable. I guess many of us have a linux box at home, and ugly XP machines at work.

The guides from Windows to Linux are usually for beginners and don't cover subjects like shell scripts, services, conf files, etc... therefore they can't be used the other way.

Questions or tricks would be like :

0) Where is located /etc/hosts ?
C:\windows\system32\drivers\etc\hosts

1) How do I put a windows "always on top" ?
With [PowerMenu]("http://www.abstractpath.com/powermenu/") 

2) How do I enable multi desktops ?
With [VirtuaWin]("http://virtuawin.sourceforge.net/")

3) How do I start/stop services from command line ?
sc [start|stop] servicename

4) How to launch a program in background in a shell ? (ex: gedit &)
Start command 
*(thanks Daveski)*

5) How to restart the network without rebooting ?
Using menus : Disable/Enable network card
*(thanks Daveski)*
Using command line ?

6) How do I add all executables in $PATH in the console completion ?
7) How do I do symbolic links ?
Impossible.
There is a way to make virtual drive mapping on folders with [VirDir]("http://www.digitalwidget.net/virdir/")

8) What are the native script languages ?
PowerShell (.ps1), VBS (.vbs), cmd.exe (.cmd), command.com (.bat)
(thanks Daveski, k2t0f12d) 

9) How to launch application with keyboard ? (katapult,gnomedo)
[Colibri]("http://colibri.leetspeak.org/")

10) How to use GNU utilities ?
[Win32 ports of GNU utilities]("http://unxutils.sourceforge.net/") (light), Cygwin (heavy)

11) How to have a crontab ?
[PyCron]("http://www.kalab.com/freeware/pycron/pycron.htm")

12) How to run a script when logging in ?
Copy a link to 
C:\Documents and Setting\%username%\Start Menu\Startup

13) What is the best way to get a remote access (like sshd) ?

14) How to define system wide hot keys ?

15) How to create a new folder with keyboard ? (Ctrl+Shift+N in Nautilus)

16) How to change Places in Open Dialogs ? (Favorite Places in Gnome)
With [PlacesBar Tweaker]("http://www.ioisland.com/placesbar/")

17) How to move a window without having to point the title bar ? (Alt+ mouse move)

18) How to set an environment variable ? (export VAR=value, echo $VAR)
SET VAR=value
echo %VAR%

19) What is the equivalent of the which command ?



...if you're sure it is not possible, please notify us. 

Thanks a lot, I hope it could help somebody else.

(Updated with post's answers on 13/02/2008)

---

### Post by Whiffle on 2008-02-12
This could come in really handy :D After 6 years with linux I'm starting to get confused when using windows (especially w/o middle click copy paste!)

Does anyone know how to make windows run a script when you login?  I don't have admin access to it, but if I could put some kind of script in My Documents and have it get run on login that would be awesome.  The windows machines at school forget *everything* as soon as you logoff, since the only thing you can write to is your My Documents on the network drive. Its really annoying.

---

### Post by k2t0f12d on 2008-02-12
Scripts on Microsoft's operating systems are *batch files*, with syntax that is a hold over from the MS-DOS era.  *PowerShell* for Windows might be that tool you'll want to look at to do a CLI on Windows.  Otherwise grab MinSYS and MinGW, or Cygwin to have the interface you are already comfortable with from your experience with Linux.

---

### Post by Daveski on 2008-02-12
> **cudjoe said:**
> Hi guyz,

So here are some other questions :
4) How to launch a program in background in a shell ? (ex: gedit &)
5) How to restart the network without rebooting ?
6) How do I add all executables in $PATH in the console completion ?
7) How do I do symbolic links ?

...if you're sure it is not possible, please notify us. 

Thanks a lot, I hope it could help somebody else.

4 - use the command 'Start'. You can also supply options for running it at different priorities, minimised, maximised etc.

5 - My best trick it to disable and then re-enable the network card. Right-click the card in Network Connections.

6 - Good question. Tab completion has been around a while in windows (although needed a registry tweak in older versions) but I do not know how or if it can be configured.

7 - I think there are only shortcuts (.lnk files) which are an absolute pain and not very flexible.

---

### Post by Daveski on 2008-02-12
> **k2t0f12d said:**
> Scripts on Microsoft's operating systems are *batch files*, with syntax that is a hold over from the MS-DOS era.  

No, VBS (Visual Basic Scripts) are native to Windows now. (**.vbs** files).

Also, **.bat** files run with command.com as the 'shell'. **.cmd **files run with cmd.exe as the 'shell', which is the more advanced command processor for NT/2K/XP and presumably Vista.

---

### Post by K.Mandla on 2008-02-12
Moved to Windows Discussions.

---

### Post by amingv on 2008-02-12
> **Whiffle said:**
> This could come in really handy :D After 6 years with linux I'm starting to get confused when using windows (especially w/o middle click copy paste!)

Does anyone know how to make windows run a script when you login?  I don't have admin access to it, but if I could put some kind of script in My Documents and have it get run on login that would be awesome.  The windows machines at school forget *everything* as soon as you logoff, since the only thing you can write to is your My Documents on the network drive. Its really annoying.

Just copy a link to the script in 'C:\Documents and Setting\%username%\Start Menu\Programs\Startup'. You should have access to your documents and settings folder by default.

Change %username% to "All Users" to make it system wide, if you're Admin.

> Scripts on Microsoft's operating systems are batch files, with syntax that is a hold over from the MS-DOS era.

You can run Python/Perl/VBS too...

---

### Post by cudjoe on 2008-02-13
Thank you guys, that's a really good start !
I update the original post with your answers.

---

### Post by ir_newbie on 2008-04-04
ok... serious problem...
i downloaded and installed mingw on my windows xp
now what...
i tried doin gcc from cmd prompt it doesnt work...
its the same with gvim...
i can use vim command only when im in the vim folder and nowhere else...
help please...

---

### Post by cudjoe on 2008-04-04
Your binaries folders should be in your PATH.
The PATH is global variable for your whole system.
You should be able to see it doing :

echo %PATH%

In order to modify it. Go to MyComputer > Properties > Advanced > Environment Variables.
You'll find it in the bottom list (system wide).

Good luck !

---

### Post by heartburnkid on 2008-04-04
> **Daveski said:**
> No, VBS (Visual Basic Scripts) are native to Windows now. (**.vbs** files).

Also, **.bat** files run with command.com as the 'shell'. **.cmd **files run with cmd.exe as the 'shell', which is the more advanced command processor for NT/2K/XP and presumably Vista.

Not true in XPSP2 and beyond; both .bat and .cmd now execute in cmd.exe

To prove this, you can create a batch file with the following text:

```
echo %comspec%
pause
```

Whether this is in a .bat file or a .cmd file, it will return the path to cmd.exe.

As well, I often use the Windows command extensions in .bat files.

As for .vbs files, they are still native to the Windows Scripting Host; the only difference is that WSH comes pre-installed now.  If you run a .vbs script, you will notice in your task list wscript.exe; that is WSH.

---

### Post by heartburnkid on 2008-04-04
> **amingv said:**
> Just copy a link to the script in 'C:\Documents and Setting\%username%\Start Menu\Programs\Startup'. You should have access to your documents and settings folder by default.

Change %username% to "All Users" to make it system wide, if you're Admin.



You can run Python/Perl/VBS too...

Actually, on rare occasions (read: if the username is changed after the account is created, or if the same username exists on both the account and the domain, or if the profile folder is moved with TweakUI or registry hacking), the profile folder name may not exactly match the user name.  You should instead use either one of the following:

```
%userprofile%\Start Menu\Programs\Startup
%homedrive%\%homepath%\Start Menu\Programs\Startup
```

This will generate the right shortcut no matter where the user profile resides.

For system-wide, you should use:

```
%allusersprofile%\Start Menu\Programs\Startup
```

Other handy folder shortcuts:

%windir% = Windows' installation directory (usually C:\Windows)
%systemroot% = Same
%temp% = Temporary Files directory
%tmp% = Same
%systemdrive% = Drive that Windows booted from (usually C:\)
%comspec% = Path to current command interpreter (i.e. cmd.exe)
%programfiles% = Path to Program Files directory (usually c:\Program Files)

---

### Post by AlphaMack on 2008-04-05
If you have a LUA, don't forget about [SuRun](http://kay-bruns.de/wp/software/surun/).

---

