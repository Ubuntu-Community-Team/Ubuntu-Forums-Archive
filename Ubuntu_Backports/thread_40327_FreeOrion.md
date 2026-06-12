---
title: "FreeOrion"
date: 2005-06-08
forum: Ubuntu Backports
---

### Post by Corey on 2005-06-08
FreeOrion just released a new version. To install it you must download the source and compile it yourself. (no problem here) I Check the dependencies and I find I have to CVS Gigi and compile that as well. Kinda annoying but hey, I can pull that off too. Then  I check the rest of the dependencies and Ubuntu seems to either have none of them, or have versions that arn't up to date enough for free orion. So I gave up :( Looks like an awesome game though even if it is in such an early state. I hope some of you backporters can update enough of the packages that I can CVS gigi and compile FreeOrion.

Thanks,
Corey

---

### Post by Gtaylor on 2005-06-08
How about some linkage?

---

### Post by AndyAWS on 2005-06-09
[www.freeorion.org](http://www.freeorion.org) 

I took a look, to compile you need the following that are not in the repos:

GiGi
Boost 1.32.0  (1.31.0 is in the repo)
FMOD


Everything else you should be able to apt-get (I think)

Personally I'll just wait until there are binaries or it becomes avialable through the repos.
I don't mind compiling, but this looks like a pain. ](*,)

---

### Post by tyreth on 2005-12-23
FreeOrion 0.3 has been released now.  You can find out more at the website [http://www.freeorion.org/](http://www.freeorion.org/)

---

### Post by Ryba on 2005-12-27
[quote=tyreth]FreeOrion 0.3 has been released now.  You can find out more at the website [http://www.freeorion.org/]("http://www.freeorion.org/")[/quote]
And I still can't figure out how to get the darn thing (0.3.1) to even run since all the precompiled crap is gcc 3.4 and missing most of the static dependencies and trying to compile the rest of it is a pain and fails on a multitude of errors.

Why can they make windows prepackaged binaries but not linux I wonder :(

---

### Post by Garyu on 2006-01-27
Wow, Master of Orion II is one of my favorite games of all time! I sure hope that this game will be included in the ubuntu repositories eventually, like FreeCiv. :D

I wanted to try it out, so I downloaded the windows .exe-file (couldn't find the code to compile it no matter where I looked at sourceforge). I ran it with just
"wine FreeOrion....exe"
and I got the following output:
```
dan-erik@minotaur:~/tmp$ wine FreeOrion-0.3.1-RC1-Setup.exe
fixme:win:SetWindowTextA setting text "FreeOrion 0.3 Setup" of other process window (nil) should not use SendMessage
fixme:win:SetWindowTextA setting text "FreeOrion 0.3 Setup" of other process window (nil) should not use SendMessage
fixme:richedit:RichEditANSIWndProc WM_SETFONT: stub
fixme:richedit:RichEditANSIWndProc EM_AUTOURLDETECT: stub
fixme:richedit:RichEditANSIWndProc EM_EXLIMITTEXT: stub
fixme:shell:SHAutoComplete SHAutoComplete stub
err:menubuilder:extract_icon32 LoadLibraryExW (L"C:\\Program Files\\FreeOrion\\uninst.exe") failed, error 126
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
fixme:win:SetWindowTextA setting text "Execute: \"c:\\Program Files\\FreeOrion\\freeorion.exe\" --fullscreen" of other process window 0x2004c should not use SendMessage
fixme:win:SetWindowTextA setting text "Delete file: C:\\windows\\temp\\nsb411.tmp\\ioSpecial.ini" of other process window 0x2004c should not use SendMessage
fixme:win:SetWindowTextA setting text "Delete file: C:\\windows\\temp\\nsb411.tmp\\modern-wizard.bmp" of other process window 0x2004c should not use SendMessagefixme:win:SetWindowTextA setting text "Delete file: C:\\windows\\temp\\nsb411.tmp\\InstallOptions.dll" of other process window 0x2004c should not use SendMessage
fixme:win:SetWindowTextA setting text "Remove folder: C:\\windows\\temp\\nsb411.tmp\\" of other process window 0x2004c should not use SendMessage
dan-erik@minotaur:~/tmp$ err:module:import_dll Library MSVCP71.dll (which is needed by L"C:\\Program Files\\FreeOrion\\log4cpp.dll") not found
err:module:import_dll Library log4cpp.dll (which is needed by L"C:\\Program Files\\FreeOrion\\freeorion.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\FreeOrion\\freeorion.exe" failed, status c0000135

```
So I guess it is impossible to install this program with Wine? :(

---

### Post by spartan777 on 2007-02-06
I can't find the source either, what a bummer.

---

### Post by Garyu on 2007-02-06
> **spartan777 said:**
> I can't find the source either, what a bummer.

Hmm, strange. But at least it is possible to get it through svn. Not sure how you would do that, but from this page:
[http://sourceforge.net/svn/?group_id=75752](http://sourceforge.net/svn/?group_id=75752)

I'm guessing you would have to
1) sudo apt-get install subversion
2)  svn co [https://freeorion.svn.sourceforge.net/svnroot/freeorion](https://freeorion.svn.sourceforge.net/svnroot/freeorion) freeorion

But that is just a guess. Let us know if you get it to work, and if you know how to build a .dep... Definitely let us know about that. :)

---

### Post by Unseelie on 2007-02-09
the above command definately works to download the source, but it still wont compile,
has anyone been able to make the GiGi that came with the source work? and how would i compile Fmod?

---

### Post by juicymixx on 2007-10-21
> **Unseelie said:**
> the above command definately works to download the source, but it still wont compile,
has anyone been able to make the GiGi that came with the source work? and how would i compile Fmod?

I'm having the same problem with gigi not compiling properly...
Actually, the problem appears to be with OGRE detection.   From scons in the GG directory:
...
Checking for pkg-config... yes
Checking for OGRE >= 1.4.3... no
Checking Ogre version >= 1.4.3... (cached) no
Warning: Ogre not configured.  The GiGiOgre library will not be built!
Configuration successful... (cached) no
KeyError: 'LIBPATH':
  File "/root/bin/Orion/gigi/GG/SConstruct", line 636:
    CreateGiGiPCFile(['GiGi.pc'], ['GiGi.pc.in'], env)
  File "/root/bin/Orion/gigi/GG/build_support.py", line 91:
    for path in env['LIBPATH']:
  File "/usr/lib/scons/SCons/Environment.py", line 309:
    return self._dict[key]

--??

---

### Post by juicymixx on 2007-10-21
ugh... I didn't have it installed.
sudo aptitude install libogre-dev
got it fixed.

---

