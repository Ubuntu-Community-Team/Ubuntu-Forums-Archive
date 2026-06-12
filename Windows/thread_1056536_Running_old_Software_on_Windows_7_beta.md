---
title: "Running old Software on Windows 7 beta?"
date: 2009-01-31
forum: Windows
---

### Post by keithwwalker on 2009-01-31
OK,

I did a virgin install of Windows 7 on my virgin partitioned 500gb harddrive (the other partition has Ubuntu 8.10 running quite smartly).

Problem is, my 2 most useful pieces of software which ran on WinXP now refuse to load up on Win7.

The software titles are:
[LIST]
[*]Call of Duty 2, WinXP
[*]Corel Draw 8, Win95
[/LIST]

On both programs, I put them in Compatibility mode for their respective OS's but I get an identical error message for both:

```
MEM_BAD_POINTER
```

Now I would of been alright if it was only Corel Draw since it is a Win95 release, but COD2 is for XP.  It should run in Vista or Win7, at least that is my expectation.

Further, Corel Draw 8 ran perfectly well in Compatibility mode in WinXP.

Can anyone help out with a solution?
I googled the error and it comes up with a *shw32.dll* file as a solution, but that file to be replaced is not to be found in Win7 at all.

Thanks
Keith Walker

PS: I know I can run Wine for running COD2 but I hear that it slows down the responsiveness of the system.  Further, I have noted that in Ubuntu, my internet is noticeably slower which may be due to lack of dedicated modem and/or network card drivers (translation: not fast enough for gaming, but fast enough for internet)

PPS: I am also trying to work with OOorg's Draw package, but it isn't as good as Corel

---

### Post by PoopyTheJ on 2009-02-01
have you tried grabbing a copy of shw32.dll and registering it in windows 7? you can get a copy of that DLL here [http://www.dll-files.com/dllindex/dll-files.shtml?shw32](http://www.dll-files.com/dllindex/dll-files.shtml?shw32), then as administrator run ```
regsvr 32 shw32.dll
``` in windows 7. If it's a 32 bit win7 it should register fine, if it's 64 bit then you'll need to look around for a 64bit version of shw32.dll or comparable.

---

### Post by keithwwalker on 2009-02-02
I tried that command in the terminal but get the following error message:
```

The module "C:\Windows\System32\SHW32.dll" was loaded but the entry point DIIRegisterServer was not found.
Make sure that "C:\Windows\System32\SHW32.dll" is a valid DLL or OCX file and then try again.
```

> **PoopyTheJ said:**
> have you tried grabbing a copy of shw32.dll and registering it in windows 7? you can get a copy of that DLL here [http://www.dll-files.com/dllindex/dll-files.shtml?shw32](http://www.dll-files.com/dllindex/dll-files.shtml?shw32), then as administrator run ```
regsvr 32 shw32.dll
``` in windows 7. If it's a 32 bit win7 it should register fine, if it's 64 bit then you'll need to look around for a 64bit version of shw32.dll or comparable.

---

### Post by NoSmokingBandit on 2009-02-02
Instead of setting the compatibility mode yourself choose the option that had win7 figure out how to make it work (i forget what its called). Its in the menu if you right-click the exe. It worked for me on several apps.

---

### Post by Ptero-4 on 2009-02-03
Or you could always just run winxp in virtualbox/virtualpc.

---

### Post by jrusso2 on 2009-02-03
> **keithwwalker said:**
> OK,

I did a virgin install of Windows 7 on my virgin partitioned 500gb harddrive (the other partition has Ubuntu 8.10 running quite smartly).

Problem is, my 2 most useful pieces of software which ran on WinXP now refuse to load up on Win7.

The software titles are:
[LIST]
[*]Call of Duty 2, WinXP
[*]Corel Draw 8, Win95
[/LIST]

On both programs, I put them in Compatibility mode for their respective OS's but I get an identical error message for both:

```
MEM_BAD_POINTER
```

Now I would of been alright if it was only Corel Draw since it is a Win95 release, but COD2 is for XP.  It should run in Vista or Win7, at least that is my expectation.

Further, Corel Draw 8 ran perfectly well in Compatibility mode in WinXP.

Can anyone help out with a solution?
I googled the error and it comes up with a *shw32.dll* file as a solution, but that file to be replaced is not to be found in Win7 at all.

Thanks
Keith Walker

PS: I know I can run Wine for running COD2 but I hear that it slows down the responsiveness of the system.  Further, I have noted that in Ubuntu, my internet is noticeably slower which may be due to lack of dedicated modem and/or network card drivers (translation: not fast enough for gaming, but fast enough for internet)

PPS: I am also trying to work with OOorg's Draw package, but it isn't as good as Corel

This is what the cheer leader for Windows 7 don't seem to understand.  Beneath the new skin beats the heart of Vista.  With the same hardware and software issues.  If the hardware or software didn't work on Vista its not likely to work on Windows 7.

---

### Post by keithwwalker on 2009-02-03
I am rapidly moving away from the Windows 7 as a solution.  

Instead of the Corel Draw Package, I downloaded Inkscape.  My vector needs are quite light, so hopefully it will be enough.

For Call of Duty 2, I am trying out Wine (I have heard of mixed success with this).

That leaves the issue with the TV tuner, and the microphone.

I also ordered a restoration DVD from Sony for my PC that 'may' restore the PC to XP status (translation: no more worries).  I somehow doubt that since I created my own XP restoration disc and that doesn't work.

The disadvantage to virtualbox is that I still need a copy of winXP softare.  Sony didn't supply that with a NEW PC.  :-({|=



> **Ptero-4 said:**
> Or you could always just run winxp in virtualbox/virtualpc.

---

### Post by pmicheal on 2009-02-04
I was failed to install the latest TeamViewer 4 on Windows 7. Installation stucks on 71% always. Strange a latest software denied to be installed on a modern OS

[Linux Archive]("http://www.linux-archive.org/")

---

