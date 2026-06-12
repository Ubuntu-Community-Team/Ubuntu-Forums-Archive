---
title: "WoW crashing on startup."
date: 2009-12-19
forum: Wine
---

### Post by RareHunter on 2009-12-19
I recently switched to Ubuntu and have been having problems running WoW. I copy pasted my installation from another computer then tried to run it with wine, the installation guide didn't give much help in regards to copying the file over so I assumed it would work. When I run WoW without the WTF folder it simply closes the game on startup and a new Config.wtf isn't created but I can copy paste my old still; however, when I use the WTF of my original installation WoW locks up as soon as it opens and then causes my computer to crash. I tried altering the Windows emulation from Windows 2000 all the way to Vista (its original OS from the computer I copied) with no luck. 

I can watch the opening movie fine if I delete the WTF folder / remove the Config.WTF but once the movie wow pops open for a second then simply closes and my Screen resolution in Linux switches to 800x600 and won't revert until I restart. I have no idea what's causing it to crash as I can't get an error report and playing around with the settings in the Config.wtf hasn't yielded any success (Ranging from switching windowed mode / graphics / opengl etc.)

Also the game won't open when I try to run it from the launcher, when I click play the launcher closes like normally but the game never opens, I can run Wow.exe manually from the terminal or by simply right clicking and opening with wine (as long as the config.wtf is missing) but I don't really know what all the stuff in the terminal means...

fixme:actctx:p****_assembly_elem wrong version for assembly manifest: 8.0.50727.762 / 8.0.50727.4053
fixme:actctx:p****_manifest_buffer failed to parse manifest L"C:\\Program Files\\World of Warcraft\\Microsoft.VC80.CRT.manifest"
fixme:actctx:p****_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
fixme:advapi:SetSecurityInfo stub
archive Data\enUS\patch-enUS.MPQ opened
archive Data\patch.MPQ opened
archive Data\enUS\patch-enUS-2.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\expansion.MPQ opened
archive Data\lichking.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
archive Data\enUS\expansion-locale-enUS.MPQ opened
archive Data\enUS\lichking-locale-enUS.MPQ opened
archive Data\enUS\expansion-speech-enUS.MPQ opened
archive Data\enUS\lichking-speech-enUS.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x39ed30,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39ea44,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f234,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f348,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f50c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f508,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39ef8c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f0c4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f450,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x18a9b0) Event query: Unimplemented, but pretending to be supported
fixme:win:EnumDisplayDevicesW ((null),0,0x39ef8c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f0c4,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x19f200,0x19f100): stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x39f7a8): stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x39f7a8): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x39de70,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39de98,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39dd40,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
r300VertexProgUpdateParams:Params exhausted

I don't really want to run the downloader to install WoW mainly because my internet is really slow being on DSL and coincidentally the farthest possible place between the 2 providers in my area and would take at least 4-5 days to install and I don't even know if it would fix the problem or not.

I'm currently running Ubuntu 9.10 with wine 1.1.34

---

### Post by Alatar1 on 2009-12-19
for the launcher problem... The easiest and least technical way to fix this would be to first browse on over to /home/<yourusername>/.wine/drive_c/Program Files/World of Warcraft ,
There will more than likely be an X on the world of warcraft folder, simply right click on it,go to properties, click the "permissions" tab, right under where it says owner: username-group, change the drop down box to "create and delete files".
Now that that is set, ***In the World of Warcraft directory, Run the game via the "WoW.exe" file , NOT LAUNCHER.EXE (the launcher is whats causing it, it will lock you out everytime!!) once your on the title/login screen, UN-check the little box on the bottom left that says "show launcher".***
***_DO NOT USE THE LAUNCHER! it WILL lock you out again!!! this should fix this issue.***_

IF while working on the issue above, you cannot change file permissions due to it telling you the owner is "root"...
you will need to change the permissions as root,
the way i know how to do this is go to terminal and enter
Code:

sudo nautilus

or whatever file browser you use (nautilus is the default for ubuntu) this will allow you browse files as root,
BE VERY CAREFUL HOWEVER, Tinkering with files as root can have very bad consequences and compromise your machine possibly, that being said...
simply browse to the directy as stated above and change the permissions that way...there are also console commands to do it manually, but for the sake of the not so savvy, I've omitted those.

and for the Crashing... browse yourself to your config.wtf file, open it to edit and paste this on its own line...

```
SET gxApi "opengl"
```

try running wow in opengl, it's favoredto do so in linux. also make sure your video drivers are full updated.

---

