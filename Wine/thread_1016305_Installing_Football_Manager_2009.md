---
title: "Installing Football Manager 2009"
date: 2008-12-19
forum: Wine
---

### Post by zenacim on 2008-12-19
hello everyone

when i launch the installation, i get:

> wine setup.exe 
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:exec:SHELL_execute flags ignored: 0x00000400
nass@nass-desktop:~/iso$ ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
fixme:win:EnumDisplayDevicesW ((null),0,0x32ad44,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x32ad44,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33bcf4,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:font:WineEngCreateFontInstance Untranslated charset 255
fixme:imm:ImmGetOpenStatus (0x9d8ead0): semi-stub
fixme:imm:ImeHandleNotify WM_IME_NOTIFY:IMN_SETCOMPOSITIONWINDOW
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:imm:ImeHandleNotify WM_IME_NOTIFY:IMN_SETCOMPOSITIONWINDOW
fixme:imm:ImeHandleNotify WM_IME_NOTIFY:IMN_SETCOMPOSITIONWINDOW
l'installation se lance mais rien ne s'affiche :


[img]http://img186.imageshack.us/img186/4164/capturesn3.jpg[/img]

I installed wintricks and the modules


what can i do?

thank u

---

### Post by cogadh on 2008-12-19
Have you followed the how-to here:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14555](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14555)

---

### Post by zenacim on 2008-12-25
thank u, i ll check that

---

### Post by __Henke on 2008-12-27
Well!

I installed Ubuntu yesterday as to test if FM09 runs faster in Linux, I know FM07 did so here goes my yesterday evening:

1. Installed Ubuntu and later Wine.

2. Tried to install FM. Well, big fail.

I had to look on the web, and found the winetricks program. Used that with all the programs mentioned in this thread and then it started.

3. Next problem, the installwindow shows nothing at all. FMtux.net has a "good" guide, although, the E TTT S TTTT E didn't work for me, so I read in the thread more, then I came to a post that said when the install is running, try to delete the "jar" folder in ~/.wine/drive_c/windows/temp/I???

somehere in a folder that has windows/resources, then in the I???? folder, run "wine setup.exe", then I got the full install GUI. Fantastic.

I finally got the game installed without any fuss.

4. Now, the activation. SIs v2 of the fix didn't work, but the offline v3 did!

5. Now, the game is activated, but it wont start. The same symptom as the failing installation GUI. I can click things, I see the pointing cursor wehere the "Start new game", "Load game" etc, etc is.

And I'm stuck. 
VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) - this is what lspci says, and I'm thinking that is the problem.

Gonna try to install the drivers with wine...

I hope this little post can be to some help for people. I also played around with NT4.0/2K/XP/Vista in winecfg with every step.

---

### Post by __Henke on 2008-12-27
> **__Henke said:**
> Well!

I installed Ubuntu yesterday as to test if FM09 runs faster in Linux, I know FM07 did so here goes my yesterday evening:

1. Installed Ubuntu and later Wine.

2. Tried to install FM. Well, big fail.

I had to look on the web, and found the winetricks program. Used that with all the programs mentioned in this thread and then it started.

3. Next problem, the installwindow shows nothing at all. FMtux.net has a "good" guide, although, the E TTT S TTTT E didn't work for me, so I read in the thread more, then I came to a post that said when the install is running, try to delete the "jar" folder in ~/.wine/drive_c/windows/temp/I???

somehere in a folder that has windows/resources, then in the I???? folder, run "wine setup.exe", then I got the full install GUI. Fantastic.

I finally got the game installed without any fuss.

4. Now, the activation. SIs v2 of the fix didn't work, but the offline v3 did!

5. Now, the game is activated, but it wont start. The same symptom as the failing installation GUI. I can click things, I see the pointing cursor wehere the "Start new game", "Load game" etc, etc is.

And I'm stuck. 
VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) - this is what lspci says, and I'm thinking that is the problem.

Gonna try to install the drivers with wine...

I hope this little post can be to some help for people. I also played around with NT4.0/2K/XP/Vista in winecfg with every step.

Crap!

Im sorry, thought I was in some other thread!

Im posting the same post here:
[http://ubuntuforums.org/showthread.php?t=967618](http://ubuntuforums.org/showthread.php?t=967618)

Disregard the prevoius post!

---

