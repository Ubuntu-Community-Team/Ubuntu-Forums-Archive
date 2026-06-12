---
title: "Multiple Iso installation"
date: 2009-05-19
forum: Wine
---

### Post by Flasimbufasa on 2009-05-19
Hey everyone, Newbie 1.0 here.

Version: 1.1.21
No 3rd party applications that are interfering.
Registry unchanged.

Trying to install: Rome Total War.
Issue: No prompt to change Cds. Whenever I get to 1/3rd done, I get an error:
>  Errore di transferimento dei funzioni
errore: -1603 Errore irreversibile durante I'installazione

Per ulteriori informazioni, vedere la Guida di Windows Installer (Msi.chm) o MSDNIn latin, [I speak english but the game sounds cooler in latin]
Google translated:

> 
[LEFT]Error of transfer of functions 
 Error: -1603 Fatal error during installation

 For more information, see the Windows Installer Help (Msi.chm) or MSDN[/LEFT]
[LEFT]

I am attempting to install the game on my external hardrive [Ubuntu wine is missing the .dll Files so when I tried to play it without installing it on here, got an error of a path missing] (Just a guess :P)

Anyone feel like helpin me out? [Plays just fine on Winfail]
[/LEFT]

---

### Post by cogadh on 2009-05-19
Error 1603 indicates a problem with the directory you are trying to install to. Either:
The folder that you are trying to install the Windows Installer package to is encrypted.

OR

The drive that contains the folder that you are trying to install the Windows Installer package to is accessed as a substitute drive.

OR

The SYSTEM account does not have Full Control permissions on the folder that you are trying to install the Windows Installer package to. You notice the error message because the Windows Installer service uses the SYSTEM account to install software.

If I had to guess, the second option is probably what is happening here, since the first is unlikley and the third only really applies on real Windows. I'm not sure I understand why you are installing to a location outside of Wine's defaults. If Wine is missing a particular DLL, then you can just add it, so it shouldn't be an issue to install it in Wine's "fake Windows" directory.

---

### Post by Duskao on 2009-05-19
If I were you I would just try to copy the contents of the disc and paste them into a single folder. All 3 discs in one folder. Just merge. Works great with some other games, hope it works with yours as well. 

Oh and when your don't copy/pasting all 3 discs then you just run the setup or istall or whatever .exe to get it going. 

Best of luck.

---

### Post by Flasimbufasa on 2009-05-20
More Information:
I am installing the game on an external hardrive because I play the game on here, and other computers. Also I only have 20 free gigs of memory on this laptop [40 gigs total] So I can not install them in the default directory, I need the room for school.

I fixed the installation error.  Removing the files did get rid of it..

Anyways:
I have tried just mounting the .iso's all at once, but whenever it gets to the switch CD, and I unmount and mount the next cd- Just pops right back up... One at a time, and all at once mounted [vitual windows too] always do the same thing... >>;

@Duskao

So All I have to do is open the disks with archive manager, extract them all to the same folder, and run the install-shield?
I will give that a try and reply the results.

---

### Post by Duskao on 2009-05-20
Well, I haven't found that to work. But what I do is when it is mounted I open the mounted drive folder. Then I highlight all of the files then right click and select copy. Then I make a folder on my desktop and just paste it in there. That way it is a 1:1 copy of the disc. Then when I do the next cd's the same way. open mounted drive, highlight then copy, then paste in the same folder as I did with the first disc, then merge and overwrite if necessary. The only game I have had issues with doing this is call of duty 2, but I think it is more to do with my crappy cd/dvd drive then to do the the actual game. In fact I just did this today with Vampire the Masquerade: Bloodlines (can be tought to install) and it worked like bread and butter :D. 
I hope this covers when you need. If I have been to vague or anything let me know, I'll try to help as much as I can. 
The error you were receiving was almost identical to the one I was getting, but I'm not certain that it was the exact one that I was originally getting.

---

### Post by Flasimbufasa on 2009-05-20
Hmm well I will try that next then-


New stuff though- I burned the disks and guess what. The stupid installer prompted for second disk, insterted. Then I pressed "retry"

Came back with the error AGAIN...

Maybe it was that the disk didnt finish mounting. I am going to retry with the disk again.

Oh yeah- After that happened, I had to force the installshield to quit. Then after I ran the installation again, it got to "extracting files to install" or something like that and froze right there, Left it for an hour. I am restarting to see if that fixes it. If not then I shall cuss out my laptop :D

EDIT:

Alrighty then so here is what I have determined with the little multiple CD installation:
The file copy pasta works, as long as you make sure the files are copied into the same directory as the first CD's files were.

Also if using a burned CD, MAKE SURE that the cd is completely mounted on the computer BEFORE hitting next.  [Do not be like me and hit next right afterwards, it will cause an error]

Only things that work for Wine installation stuff.

Also I have realized that if the first installation fails you MUST restart the computer. You may be able to restart wine, but I do not know how to do that.  [Logging out and back in does nothing by the way, same error]

******************************************************************
All these things are just assumptions from experience, correct me if I am wrong
******************************************************************

But the game installed perfectly. So Hoorah.

---

### Post by Flasimbufasa on 2009-05-21
Gah! I do not get what is wrong here. I have tried disks, I have tried the file installation... Every time errors.

With the disks I got to the 3rd cd before getting a weird error... Do not recall which one. I believe it was error -1237

Also every time with the file installation I get the error I stated in my first post.

> 
The drive that contains the folder that you are trying to install the Windows Installer package to is accessed as a substitute drive.What do you mean by a substitute drive?
How would I know if it is and how would I go about fixing it if this was the problem?

-headdesks- ](*,) Ubuntu does not like me!!  :cry:

---

### Post by cogadh on 2009-05-21
A substitute drive is essentially a folder or directory that is mapped as a drive letter in Windows, instead of as a directory on an existing drive letter (did that make sense?). Since that is basically what Wine does, it seems to make sense that it would be the source of your error.

Have you tried just creating a whole new Wine prefix on the external drive, then running the entire install from that prefix?
```
wineprefixcreate --prefix /path/to/drive/.winertw
env WINEPREFIX=/path/to/drive/.winertw wine install.exe
```
When you run the game, you will also need to specify that prefix as well:
```
env WINEPREFIX=/path/to/drive/.winertw wine "C:\Program Files\path\to\game\game.exe"
```

---

### Post by Duskao on 2009-05-21
Yeah, might I also suggest trying to use POL (playonlinux). At first I hated the program, but after playing with both wine and with that and also with crossover games, I found wine to be the best because of customisation. However, I later found that with POL you can download "advancedwineconfiguration" plugin and then you can customize in POL like you would with wine, but actually easier. And another great thing about it is that it creates a new prefix for each game installation (like a separate fresh wine install for each game). So then if you have multiple games that require different settings, you don't need to mess with anything before you play it. ie. wizard101 (allow pixel shader -disabled, fbo, virtual desktop) as opposed to Chronicles of riddick: Escape from butcher bay (fbo, full screen {no virtual desktop}, alloted video RAM.) Get the picture? 

Anyway, if you can try what cogadh said by trying to install wine or POL on the external drive. Worst case scenario you could try cutting and copying the .wine or .playonlinux folder to the external drive. Never know, might work.

---

### Post by Flasimbufasa on 2009-05-21
*head explodes*

Alrighty then, after reading that a few times, I [finally] understood what you said... [/slowness]

So what I get from this is: Getting to the 3rd cd was just sheer luck.


Anyways, I shall try that later, however, for now i must work on a project, i will post back later with how I failed [Well, with how Ubuntu likes me, Just seems like that is what shall happen]

---

### Post by Flasimbufasa on 2009-05-21
$ sudo wineprefixcreate --prefix /media/OneTouch4.winertw
[sudo] password
Note: wineprefixcreate is deprecated and shouldn't be needed anymore.
      WINEPREFIX creation and updates now happen automatically when needed.

fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x33cf94
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\gecko\\0.9.1\\wine_gecko\\components\\xpti.dat" 1 536870916 (nil) (nil) 0x33c960 (nil)
fixme:iphlpapi:NotifyAddrChange (Handle 0x2dae888, overlapped 0x2dae890): stub
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\gecko\\0.9.1\\wine_gecko\\components\\compreg.dat" 1 536870916 (nil) (nil) 0x33ca50 (nil)
0[199d60]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\sqlite3.dll") - Symbol NSGetModule not found
0[199d60]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\plc4.dll") - Symbol NSGetModule not found
0[199d60]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\js3250.dll") - Symbol NSGetModule not found
0[199d60]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\softokn3.dll") - Symbol NSGetModule not found
0[199d60]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nss3.dll") - Symbol NSGetModule not found
0[199d60]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nssckbi.dll") - Symbol NSGetModule not found
0[199d60]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nssutil3.dll") - Symbol NSGetModule not found
0[199d60]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\smime3.dll") - Symbol NSGetModule not found
0[199d60]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\plugins\npnul32.dll") - Symbol NSGetModule not found
0[199d60]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nssdbm3.dll") - Symbol NSGetModule not found
0[199d60]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\ssl3.dll") - Symbol NSGetModule not found
0[199d60]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\freebl3.dll") - Symbol NSGetModule not found
0[199d60]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\xpcom.dll") - Symbol NSGetModule not found
0[199d60]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nspr4.dll") - Symbol NSGetModule not found
0[199d60]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\plds4.dll") - Symbol NSGetModule not found
0[199d60]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\xul.dll") - Symbol NSGetModule not found
fixme:shell:DllCanUnloadNow stub
wine: configuration in '/media/OneTouch4.winertw' has been updated.
$ env WINEPREFIX=/media/OneTouch4.winertw wine install.exe
wine: /media/OneTouch4.winertw is not owned by you
$ sudo env WINEPREFIX=/media/OneTouch4.winertw wine install.exe
wine: could not load L"C:\\windows\\system32\\install.exe": Module not found
[/code]

Lololol, What?

Uhmm What did I do wrong here? The location of the driver is in /media/OneTouch4
What?

---

### Post by cogadh on 2009-05-21
[NEVER USE SUDO WITH WINE!]("http://wiki.winehq.org/FAQ#head-96bebfa287b4288974de0df23351f278b0d41014") Doing so allows Wine, and therefore any Windows programs including viruses and other malware, complete access to the system, plus it screws up the permissions on the Wine prefix you are using (hence the "is not owned by you" message). Since you haven't installed anything in that prefix, it is just easiest to delete it and start over:
```
sudo rm -rf /media/OneTouch4.winertw
```
Now for the other issues. You left a "/" out of the prefix create command, so you did not actually create the new prefix on the external drive, it was instead created in your /media directory on your hard drive. The correct command should be this:
```
wineprefixcreate --prefix /media/OneTouch4/.winertw
```
As for the "module not found" error when you ran the install, that was due to not specifying where the install.exe actually is. The command should be:
```
env WINEPREFIX=/media/OneTouch4/.winertw wine /path/to/install.exe
```
Make sure you replace the "/path/to/" with the correct path to where you have the game's installer.

---

### Post by Flasimbufasa on 2009-06-17
Alright, thanks for the help! It actually worked, FINALLY.

However, I did have to reinstall Ubuntu [again] xD
Ran out of room in Ubuntu to do much of anything. I had barely a gig of free room. But at least now I know how to get the external hardrive installation :D

---

