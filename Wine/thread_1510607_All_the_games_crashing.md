---
title: "All the games crashing"
date: 2010-06-15
forum: Wine
---

### Post by Zireth ZH on 2010-06-15
Hey guys..... ):P

I got no luck running games in this pc... all the games crashes.. applications dont. After 3 or 4 mins the game crashes the whole OS... sound keeps going though

cant even do ctrl alt f1!!!! gotta force restart the thing pressing the reset button all the time!:confused:

Heres the output from Ether saga online :

backstage@BackstagePC:~$ cd /home/backstage/.wine/drive_c/Perfect\ World\ Entertainment/Ether\ Saga\ Online/element/
[email]backstage@BackstagePC:~/.wine[/email]/drive_c/Perfect World Entertainment/Ether Saga Online/element$ wine elementclient.exe
fixme:win:EnumDisplayDevicesW ((null),0,0x32e6fc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32ec20,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32eb78,0x00000000), stub!
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x17f068,0x17ef88): stub
err:ole:CoGetClassObject class {5959df60-2911-11d1-b049-0020af30269a} not registered
err:ole:CoGetClassObject no class object {5959df60-2911-11d1-b049-0020af30269a} could be created for context 0x1
fixme:win:EnumDisplayDevicesW ((null),0,0x32ebc8,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:d3d8:ValidateVertexShader (0x37f70a0 (nil) (nil) 0 (nil)): stub
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:d3d8:ValidatePixelShader (0x37e1738 (nil) 0 (nil)): stub
fixme:d3d:buffer_PreLoad Too many declaration changes or converting dynamic buffer, stopping converting
fixme:d3d:buffer_PreLoad Too many declaration changes or converting dynamic buffer, stopping converting
fixme:d3d:buffer_PreLoad Too many declaration changes or converting dynamic buffer, stopping converting
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCompressedTexSubImage2DARB @ surface.c / 751
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCompressedTexSubImage2DARB @ surface.c / 751
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCompressedTexSubImage2DARB @ surface.c / 751
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCompressedTexSubImage2DARB @ surface.c / 751
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCompressedTexSubImage2DARB @ surface.c / 751
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCompressedTexSubImage2DARB @ surface.c / 751
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCompressedTexSubImage2DARB @ surface.c / 751
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCompressedTexSubImage2DARB @ surface.c / 751
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCompressedTexSubImage2DARB @ surface.c / 751
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCompressedTexSubImage2DARB @ surface.c / 751
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCompressedTexSubImage2DARB @ surface.c / 751
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCompressedTexSubImage2DARB @ surface.c / 751
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCompressedTexSubImage2DARB @ surface.c / 751
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCompressedTexSubImage2DARB @ surface.c / 751
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCompressedTexSubImage2DARB @ surface.c / 751
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCompressedTexSubImage2DARB @ surface.c / 751
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCompressedTexSubImage2DARB @ surface.c / 751
fixme:d3d:buffer_PreLoad Too many declaration changes or converting dynamic buffer, stopping converting
fixme:d3d:buffer_PreLoad Too many declaration changes or converting dynamic buffer, stopping converting
fixme:imm:ImmReleaseContext (0x4005c, 0x141120): stub
fixme:d3d:buffer_PreLoad Too many declaration changes or converting dynamic buffer, stopping converting
fixme:d3d:buffer_PreLoad Too many declaration changes or converting dynamic buffer, stopping converting
fixme:d3d:buffer_PreLoad Too many declaration changes or converting dynamic buffer, stopping converting
fixme:d3d:buffer_PreLoad Too many declaration changes or converting dynamic buffer, stopping converting
fixme:d3d:buffer_PreLoad Too many declaration changes or converting dynamic buffer, stopping converting
fixme:d3d:buffer_PreLoad Too many declaration changes or converting dynamic buffer, stopping converting
fixme:thread:NtQueryInformationThread Cannot get kerneltime or usertime of other threads







Anyone got an idea on how to fix this? lend me a hand thanks! ):P

---

### Post by Zireth ZH on 2010-06-15
By the way I use ATI HD Radeon 4670 works as an extra info?

---

### Post by cogadh on 2010-06-15
You didn't by any chance try to install DirectX in Wine, did you? If so, that is probably the issue, installing DirectX can break Wine's own built-in DirectX functionality.

---

### Post by Zireth ZH on 2010-06-15
hmmm what do u mean by that? downloading it from winetricks?

If thats the problem im not getting it.. alot of ppl does that .. i followed a guide.... >_> 

Although i dunno if i did that thing on my works pc.. i recently instaled a fresh copy of kubuntu ... but at my homes pc yeah...

---

### Post by cogadh on 2010-06-16
I know a lot of people do that, but what a lot of people apparently don't realize is you don't need to install the full DirectX redistributable (and usually shouldn't), you really only might need some parts of the redistributable, like the d3dx9_##.dll files, which you can also install, separate from the full redistributable, with winetricks. From the [Wine FAQ]("http://wiki.winehq.org/FAQ#head-fbaa851e07d7484640cc10b6d0c48abc741260b2"):
> [SIZE="3"]**8.1. Does Wine support DirectX? Can I install Microsoft's DirectX under Wine?**[/SIZE]

Wine itself provides a DirectX implementation that, although it has a few bugs left, should run fine. Wine supports DirectX 9.0c at this time. Plans for DirectX 10 are underway.

**If you attempt to install Microsoft's DirectX, you will run into problems.** It is not recommended nor supported by Wine HQ to attempt this. You can install the runtime, but it will not run. The runtime needs access to the Windows drivers, and Wine cannot access them for obvious reasons. The only native Microsoft DLLs that could be useful anyway are the d3dx9_xx.dll type ones, and these require you to accept Microsoft's license. Additionally these DLLs are now part of the Wine tree. So, as Wine improves these DLLs will only become less relevant.

That said, there are some guides out there which describe how you can install Microsoft's DirectX. I reiterate: It is not recommended nor supported by Wine HQ to attempt this. Furthermore it is considered off topic in Wine HQ support mediums (such as the forums). Please use a clean Wine configuration folder before seeking help. (You may need to rm -rf ~/.wine and re-install your Windows applications.)

---

### Post by asdfoo on 2010-06-16
make sure you're using the latest ati drivers (catalyst 10.5) also, if your pc crashes entirely then that's usually due to a bug in video drivers, not wine.

---

### Post by Zireth ZH on 2010-06-16
So if its not recommended why does playonlinux installs directx? 

Imma have to reinstall it again how do i clean up everything? start from 0... will sudo apt-get --purge remove wine do?

native linux games runs ok .. well not ok LAAAAAAAAAAAAGGGGGGGGGGGGGGGG!!!!!!!!!!!!!!! ati drivers are not good in here.. im replacin my card to nvidia 

I installed the drivers through ''hardware drivers'' ive been running into problems installing the ones from ati site.. it just wont let me install... I only run got problems installing drivers in kubuntu and opensuse, both KDE and i dunno if thats the problem cuz it seems too...

i had no issues at all installing the drivers in gnome ubuntu, ive done that many times, but still the whole system freezes even with the latest drivers when playing the games in wine

---

### Post by cogadh on 2010-06-16
If you want to start all over with a fresh Wine install, you don't even have to uninstall Wine, just delete the .wine directory from your home directory and everything will be restored to its original state.

As for why things like PlayOnLinux install DX, it is kind of the "shotgun approach" to solving potential problems when they should be using the "sniper approach". Lets say you have a game that doesn't work because of some lacking function in dinput.dll. POL (and other how-to guides) solve this problem by installing the full DirectX redistributable. Sure, it might solve the problem with dinput.dll, since the Wine version of that DLL is replaced by the real version, but it also replaces dozens of other Wine DLLs that didn't have any problems at all: they tried to solve the problem with a shotgun and hit way more than just the intended target. What they should do is target just the specific cause of the problem and only correct that. In other words, don't install the full DX, just replace dinput.dll: take it out with a sniper shot. The shotgun approach is easier, but the sniper approach is better.

---

### Post by Zireth ZH on 2010-06-16
ok i get it .. i also got to install the drivers from amd successfully.. but the performance is POOR as hell... any ideas on how to fix this.. LAGS like hell.. i got to run the game but it lags just way too bad

also i want to add that changing some of the game settings crashes the game.. sometimes starting the game kicks me out of the kubuntu session...

---

### Post by hikaricore on 2010-06-16
Why in the hell are you trying to install AMD drivers in wine....

*sigh*

---

### Post by cogadh on 2010-06-16
I'm pretty sure he's referring to the Linux drivers for his video card. He's just trying to play the game in Wine.

---

### Post by Zireth ZH on 2010-06-17
> **cogadh said:**
> I'm pretty sure he's referring to the Linux drivers for his video card. He's just trying to play the game in Wine.

Yes, i meant the linux drivers... are there any guide or something like to improve the drivers performance? i cant belive my video card performs like a integrated vga......

---

### Post by cogadh on 2010-06-17
Very likely, it is not the installation or configuration that is the problem, it is the quality of the drivers themselves. Unfortunately, ATI's Linux driver support has never been the best (really it is not much more than a token effort on their part) and the open source drivers for ATI cards haven't matured enough to be all that useful.

---

### Post by asdfoo on 2010-06-17
ATI is trying to fix fgrlx, but unfortunately they only have a few people working on it and there is a delay of about 6 months from getting a bug fixed to it actually going in a release.

To compound this, I've heard that the original design of the drivers was more or less a hack inherited from non-linux systems held together with a lot of tape which makes it even more difficult for them to maintain, probably why they dropped a lot of support for slightly older cards.

Before you buy a nvidia card thinking it will solve all your problems, check the AppDB to see how well the game runs already, otherwise you might just have to end up going back to windows for acceptable performance.

---

