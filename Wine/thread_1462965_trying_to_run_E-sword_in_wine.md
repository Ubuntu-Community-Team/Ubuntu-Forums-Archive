---
title: "trying to run E-sword in wine"
date: 2010-04-26
forum: Wine
---

### Post by Synoc on 2010-04-26
ok I installed wine, downloaded e-sword from their website, went through the installshield, e-sword shows up in my wine folder, I click on it, it starts to try to run it, but I never get the program to load. it stays at my desktop. it shows up briefly in the task bar, but then it disappears.

What info do you need to help?

for what it may be worth, I'm running Ubuntu 9.10 in KDE

---

### Post by cogadh on 2010-04-26
Run it from the terminal to get any error messages from Wine that might explain what is happening. Post those errors here and we'll see what we can do.

Alternatively, you go forgo Wine and use one of the Linux native apps like Xiphos: [http://xiphos.org/](http://xiphos.org/)

---

### Post by Synoc on 2010-04-26
I admittedly have no idea how to run anything in terminal at all. I started linux with ubuntu and am ignorant in the wise, wise ways of all things Linux when it comes to using it as a text base.

I tried xiphos, but e-sword has my strongs hebrew and greek translation, no cost and I'm poor.

---

### Post by cogadh on 2010-04-26
Open up a terminal window, then change directories to where the app is installed:
```
cd ~/.wine/drive_c/Program\ Files/path/to/app
```
Change that "path/to/app" to the appropriate application path for e-Sword.

Once you are in the correct directory, run the app using Wine's terminal command:
```
wine <application name>.exe
```
Obviously, change that "<application name>" to the actual name of the e-Sword executable.

Now when the app runs (or fails to run) Wine will out put any error messages to the terminal window which may help us figure out what is going on. Copy/paste that output here. It is possible that the output will be very long and filled with lots of error messages. Don't panic, most of them can be ignored, but it will still help to have all of them.

---

### Post by Carl Hamlin on 2010-04-26
I had the same problem, but made out OK by switching to e-spear after a brief but ultimately doomed fling with e-quarterstaff.

Your mileage may vary, of course.

---

### Post by Synoc on 2010-04-26
> **cogadh said:**
> Open up a terminal window, then change directories to where the app is installed:
```
cd ~/.wine/drive_c/Program\ Files/path/to/app
```Change that "path/to/app" to the appropriate application path for e-Sword.

Once you are in the correct directory, run the app using Wine's terminal command:
```
wine <application name>.exe
```Obviously, change that "<application name>" to the actual name of the e-Sword executable.

Now when the app runs (or fails to run) Wine will out put any error messages to the terminal window which may help us figure out what is going on. Copy/paste that output here. It is possible that the output will be very long and filled with lots of error messages. Don't panic, most of them can be ignored, but it will still help to have all of them.
 ok I get to ~/.wine/drive_c/Program Files$ and ls, and I see e-Sword right there, type "wine e-Sword" and it tells me... 
"wine: cannot find L"C:\\windows\\system32\\e-Sword.exe"

---

### Post by cogadh on 2010-04-26
You have to change directories further, right into the e-Sword directory. Once there, look for the e-Sword executable (probably called esword.exe or something similar). When you run the Wine command, you need to specify that executable: "wine esword.exe"

---

### Post by Synoc on 2010-04-26
> fixme: ole:OleLoadPictureEx (0xe5afdc,18910,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f970), partially implemented.
err: module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\system32\\tx4ole14.ocx") not found
err: ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\tx4ole14.ocx"
err:  ole:CoGetClassObject no class object {15a32f01-b939-11dc-af58-0013d350667c} could be created for context 0x3
err: module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\system32\\tx4ole14.ocx") not found
err: module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\system32\\tx4ole14.ocx") not found
err: ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\tx4ole14.ocx"
err: ole:CoGetClassObject no class object {15a32f01-b939-11dc-af58-0013d350667c} could be created for context 0x3
hope this makes sense to you I had to add spaces after every : to I wouldn't get any more emotes...

---

### Post by cogadh on 2010-04-26
Next time, don't use the quote tags, use the code tags, that way the emotes won't even happen.

Actually, it makes a lot of sense. The app is looking for the MFC42.dll file, which is part of the Visual C++ Runtime and not part of Wine by default (or it is part of Wine, but barely works). Easiest way to get that into Wine is to use the winetricks script, found here:
[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

Once installed, try running the app again the same way. The error messages will very likely change and there is a good chance that a new DLL will pop up as missing... or the app could just run. Trial and error is a huge part of getting apps to work in Wine.

---

### Post by Synoc on 2010-04-26
my main problem with wine is, no matter how much of it I drink, I can't get anything to work right... ok one more glass

---

### Post by Synoc on 2010-04-26
> fixme: ole:OleLoadPictureEx (0xe5afdc,18910,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f970), partially implemented.
err: module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\system32\\tx4ole14.ocx") not found
err: ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\tx4ole14.ocx"
err:  ole:CoGetClassObject no class object {15a32f01-b939-11dc-af58-0013d350667c} could be created for context 0x3
err: module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\system32\\tx4ole14.ocx") not found
err: module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\system32\\tx4ole14.ocx") not found
err: ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\tx4ole14.ocx"
err: ole:CoGetClassObject no class object {15a32f01-b939-11dc-af58-0013d350667c} could be created for context 0x3
hope this makes sense to you I had to add spaces after every : to I wouldn't get any more emotes...

---

### Post by Synoc on 2010-04-26
```
fixme:ole:OleLoadPictureEx (0xe5afdc,18910,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f970), partially implemented.
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\system32\\tx4ole14.ocx") not found
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\tx4ole14.ocx"
err:ole:CoGetClassObject no class object {15a32f01-b939-11dc-af58-0013d350667c} could be created for context 0x3
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\system32\\tx4ole14.ocx") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\system32\\tx4ole14.ocx") not found
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\tx4ole14.ocx"
err:ole:CoGetClassObject no class object {15a32f01-b939-11dc-af58-0013d350667c} could be created for context 0x3

```next : )

---

### Post by cogadh on 2010-04-26
Nothing at all changed. Did you use winetricks as I suggested?

---

### Post by Synoc on 2010-04-26
I thought so, I know it d/l'd let me check and see what happened

---

### Post by Synoc on 2010-04-26
```
prerequisite vcrun6 already installed, skipping
Install of mfc42 done
winetricks done.
patrick@patrick-laptop:~/.wine/drive_c/Program Files/e-Sword$ wine e-Sword
fixme:ole:OleLoadPictureEx (0xe5afdc,18910,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f970), partially implemented.
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\system32\\tx4ole14.ocx") not found
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\tx4ole14.ocx"
err:ole:CoGetClassObject no class object {15a32f01-b939-11dc-af58-0013d350667c} could be created for context 0x3
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\system32\\tx4ole14.ocx") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\system32\\tx4ole14.ocx") not found
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\tx4ole14.ocx"
err:ole:CoGetClassObject no class object {15a32f01-b939-11dc-af58-0013d350667c} could be created for context 0x3

```
definitely installed mfc42 this time

---

### Post by cogadh on 2010-04-26
Yup, it did. Run winecfg and check the libraries tab to be certain that there is an exception set up for MFC42.dll. It should be set to "native", meaning it will use the real Windows version of that DLL instead of the Wine version.

---

### Post by Synoc on 2010-04-26
there are no overrides in the library tab, nor can I select MFC42 from the drop-down menu oh well back to drinking more wine for me.... sooner or later it'll work.

---

### Post by flying_174 on 2010-04-27
> **Synoc said:**
> my main problem with wine is, no matter how much of it I drink, I can't get anything to work right... ok one more glass

You got that right.

I had the same problem as the OP. I've been looking for a fix for 2 days now. Glad this thread was posted. I had been trying all of the other fixes that others had put on the forum. None worked. 
WineTricks did the trick so to speak. Thanks for this information.

---

### Post by flying_174 on 2010-04-27
did you just try to run MFC42 or did you install all of winetricks?
I ran the whole code    ```
sh winetricks corefonts vcrun6
```

and that is what worked for me. I didn't have to make any changes to anything after running that.

---

### Post by cogadh on 2010-04-27
> **Synoc said:**
> there are no overrides in the library tab, nor can I select MFC42 from the drop-down menu oh well back to drinking more wine for me.... sooner or later it'll work.
You can manually add files to the overrides, you don't have to stick to just the ones on the list. Just type the name in the add field.


> **flying_174 said:**
> did you just try to run MFC42 or did you install all of winetricks?
I ran the whole code    ```
sh winetricks corefonts vcrun6
```

and that is what worked for me. I didn't have to make any changes to anything after running that.
If you notice, one of his terminal outputs shows "prerequisite vcrun6 already installed, skipping", so there may be something odd going on here.

---

### Post by Synoc on 2010-04-27
```
 fixme:ole:OleLoadPictureEx (0xe5afdc,18910,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f970), partially implemented.
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\system32\\tx4ole14.ocx") not found
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\tx4ole14.ocx"
err:ole:CoGetClassObject no class object {15a32f01-b939-11dc-af58-0013d350667c} could be created for context 0x3
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\system32\\tx4ole14.ocx") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\system32\\tx4ole14.ocx") not found
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\tx4ole14.ocx"
err:ole:CoGetClassObject no class object {15a32f01-b939-11dc-af58-0013d350667c} could be created for context 0x3

```
set it to native here's my code

---

### Post by Synoc on 2010-04-28
bump

---

### Post by wernbrenk on 2010-04-29
BTW there is a linux version of E-Sword available. Just go to Applications->Add/Remove and search for it there.

Regards,
Werner

---

### Post by Synoc on 2010-04-29
I don't even find add/Remove. I run KDE normally, but even with my gnome all I see is software center. and e-sword is not there

---

### Post by Synoc on 2010-04-30
sorry for the rebump, but... bump.

If e-sword is available for linux, I can't find it through my Ubuntu/Kubuntu or on the e-sword website, therefore I tend not to trust it. I've heard about the hack jobs people have done through third party sites.

---

### Post by wernbrenk on 2010-04-30
I see what you mean. I was running 9.04 up until this morning and it still had e-sword in the repository, but I have now moved to 10.04 and it's not there either.

Sorry.

---

### Post by Synoc on 2010-04-30
I'd be perfectly happy getting it to work in wine

---

### Post by jonathonblake on 2010-05-01
> **Synoc said:**
> I'd be perfectly happy getting it to work in wine

Use the script that is attached to the first message in the thread at [http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)  
to install e-Sword.

jonathon

---

### Post by jonathonblake on 2010-05-01
> **Synoc said:**
>  If e-sword is available for linux, I can't find it through my Ubuntu/Kubuntu or on the e-sword website, 

The OP is confusing *The Sword Project*, more specifically, *Xiphos* with *e-Sword*.

jonathon

---

### Post by Synoc on 2010-05-02
I apparently don't have archive manager either. (noob here, I admit it)

---

### Post by usnica on 2010-05-04
Although this is the forum for Wine, there are some references to the Gnome version of Sword so I'm posting some help.  Try looking for Xiphos instead of gnome-sword.  If it's not in the software center, try using Synaptic to install.  After installing Xiphos, make sure the KJV (Bible texts), StongsGreek and StrongsHebrew (dictionaries) are installed.  Then, in the pane that displays the Bible text (only works for KJV) right click > Module Options > check Strong's Numbers box.

---

### Post by cepcer on 2010-05-14
I am a complete noob to Linux and Ubuntu. Using the following tutorial for installing Esword in Wine worked perfectly without any additional tweaking.

[http://ubuntuforums.org/showthread.php?t=404042&highlight=esword](http://ubuntuforums.org/showthread.php?t=404042&highlight=esword)

---

### Post by michaelsanders on 2010-06-14
Anyone know how to get reword on a Dell mini. 10 running Moblin.  I'm desperate and a real novice.

---

### Post by Julia A on 2010-07-10
Please can anybody help? I've been following the tutorial to install E-Sword onto my netbook (using Eeebuntu 3, which is based on Ubuntu 9.04). I've installed version 1.0.1 of Wine, cabextract, and mfc42.dll. I've also downloaded the e-Sword installer, but when I try to install it I get the following error message:

Esword installer error:Note: command 'env WINEPREFIX=/home/julia/.wine_Esword ..winetricks mfc42 returned status 1. Aborting.

Now does this mean that there's something wrong with mfc42? I put it in under "libraries" in winecfg, and set it to "native". 

I'd be grateful for any advice, as,like lots of others, I don't think there's anything to touch e-Sword. I'm very much a novice on Linux, so please provide step by step instructions.

Thank you, and God bless

Julia A

---

### Post by James78 on 2011-05-10
I had problems running it.

All I did was install vcrun6 into the prefix. That's it, and all was good. (I also installed fonts too though so I could have something useful to use)

---

