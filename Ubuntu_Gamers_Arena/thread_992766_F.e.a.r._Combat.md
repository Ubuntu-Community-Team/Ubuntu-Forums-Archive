---
title: "F.e.a.r. Combat"
date: 2008-11-25
forum: Ubuntu Gamers Arena
---

### Post by Meremoth on 2008-11-25
I use to play FEAR COMBAT a lot using Windows XP on this same PC. I've recently switched OS's from XP to Ubuntu Intrepid 8.10. When I try to run FEAR under Wine, I get the error "The video card in this computer is not supported. Refer to the readme.txt file for more information."

The strange thing is that I am using the exact same video card that I was using on Windows XP, GeForce 3 Ti200.

In the readme file it has the following NVIDIA cards listed as supported:

NVIDIA(R)

ForceWare(TM) Drivers (Windows(R) 2000/XP): v81.98

GeForce(TM) 4 Ti Series
GeForce(TM) FX 5900 Series
GeForce(TM) 6600 Series
GeForce(TM) 6800 Series
GeForce(TM) 7800 Series

I know my card isn't on that list, but it worked before.

Is there anyway possible to solve or get around this problem?

Thanks in advance for any help or suggestions.

---

### Post by Cresho on 2008-11-25
I had an issue like this for "world in conflict" which was resolved in a particular way.  Not sure how it will work for you but it's worth a shot.

```
Previously, it was necessary to install a crack for this game. Beginning with recent versions of Wine (~1.1 and later), this is no longer required. However, if we attempted to start the game now, it would crash right away. This is because World In Conflict comes with optional support for DirectX 10. As DirectX 10 is currently not supported in Wine, we need to disable it.

In addition, due to a few missing functions in Wine, the game would currently not be able to detect the hardware of your computer properly. Until these functions are supported in Wine, we will use Microsoft's original DLL to do the job for us. Therefore, get the file dxdiagn.dll from dlldump and save it to the 'drive_c/windows/system32' folder in your Wine directory:

www.dlldump.com/download-dll-files_new.php/dllfiles/D/dxdiagn.dll/5.03.2600.2180/download.html

Now let's instruct Wine about DirectX 10 and the dxdiagn.dll. Open a console and enter: 
Click the Libraries tab, type in d3d10 under New override for library and click Add. You'll now see "d3d10 (native,builtin), hit Edit and select Disabled and hit OK. Then again under New override for library, type in dxdiagn and click Add. You'll now see "dxdiagn (native,builtin)" added to the list, so hit Apply and then OK to exit.

The game might still complain about its inability to detect your computer's hardware but you should now be able to set textures and other effects to "high" which was impossible before. Just hit "Cancel" whenever you see the warning dialogue in order to start the game. 
By changing registry values in Wine's registry, the performance of the game can be increased with the downside of a slightly decreased visual quality during gameplay.

The values you might want to set are as follows:

[HKEY_CURRENT_USER\Software\Wine]

[HKEY_CURRENT_USER\Software\Wine\Direct3D]
"UseGLSL"="disabled" 

```

but what really helped me was this part.

under the libraries tab, add into existing overrides d3d10 "disabled" and dxdiagn (native).

this stoped the nagging pop up on my game.  I use to hit escape and maybee you should try escape to see if you can bypass it.

---

### Post by Meremoth on 2008-11-25
No luck, same problem.  Thanks for the reply, though.

Any other suggestions?

---

### Post by Meremoth on 2008-11-25
I thought maybe installing DirectX 9.0c within Wine would solve my problem.

I followed the instructions found here:

```
http://howto.landure.fr/gnu-linux/install-directx-9-0c-on-linux-using-wine
```

I get all the way to the end where you actually install DirectX.  I paste:

```
/usr/bin/wine "C:\DIRECTX\DXSETUP.exe"
```

into my terminal and this is what pops up about a million times:

```
err:setupapi:do_file_copyW Unsupported style(s) 0x144
```

The DirectX window says it needs to restart the computer, however, clicking Next does nothing and the terminal just has a flashing cursor under the last error line.  It never returns to username@username-desktop:~$

If it ain't one thing it's another.

Any help or suggestions anyone?

Thanks in advance.

---

