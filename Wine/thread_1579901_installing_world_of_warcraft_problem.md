---
title: "installing world of warcraft problem"
date: 2010-09-22
forum: Wine
---

### Post by jh77if on 2010-09-22
i installed wine properly. go to run installwow.exe (the blizzard  downloader from the website), the window with the drop down menu to  select which game version to install comes up, i select wrath of the  lich king and hit ok, the window then closes and nothing happens. sorry  for the run-on.

typed wine in terminal then dropped the installer and hit enter got THIS:
~$ wine '/home/andrew/Downloads/InstallWoW.exe'
system.reg is not a valid registry file
user.reg is not a valid registry file
fixme:actctx: parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls" (6.0.0.0)
fixme:actctx: parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls" (6.0.0.0)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 10000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 10000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 3000
err: ole:CoGetClassObject class {8856f961-340a-11d0-a96b-00c04fd705a2} not registered
err: ole:CoGetClassObject class {8856f961-340a-11d0-a96b-00c04fd705a2} not registered
err: ole:CoGetClassObject no class object {8856f961-340a-11d0-a96b-00c04fd705a2} could be created for context 0x3

also, this is the third time i have had to move this thread. so im getting a little frustrated at this point only because i am a dumbass and didnt test ubuntu enough before i decided to install it and delete XP.

today i am going to try to install WoW from a windows machine onto an external HD and then copy it to this machine. any help much appreciated as i know there is a large player-base that plays from linux and DOESNT have problems.

---

### Post by jh77if on 2010-09-22
bumpppppp

---

### Post by dardack on 2010-09-22
How do you know wine is installed properly?  What version of wine?

Also the user.reg/system.reg errors seem like there is a problem with wine.

---

### Post by jh77if on 2010-09-22
well i installed from synaptic package manager. its version 1.2 though i do not know how to check if it is installed properly.

---

### Post by jh77if on 2010-09-22
actually first i installed via [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

then i removed wine and installed via software center

then i tried removing the program and reinstalled via synaptic.

i am trying wine 1.3 right now.

---

### Post by jh77if on 2010-09-22
voila wine 1.3 works. (SO FAR) will be back to confirm download after it is complete *crosses fingers*

---

### Post by jh77if on 2010-09-22
wine 1.3 does not work. finished installing and then had difficulties with patching so i ran blizzard repair tool. that said that permissions cannot be repaired please reinstall wow. so i uninstalled wow. and now i am having the same issue that the box comes up to choose which game to install and i choose WotLK and then it closes and doesnt do anything. i checked system moniter > processes and nothing remotely related to WoW on the list. help much appreciated. i do not have windows discs so i cant go back and this is pretty much the only thing i do on the computer aside from web browsing and audio production. i would like to stay linux so PLEASE HELP ME

---

### Post by cwwilson721 on 2010-09-22
We need more info than "it doesn't work"


[LIST]
[*]What actual error messages in the terminal? (Run 'wine <downloadedfile> in the terminal, post the error message here)
[*]What enviornment are you installing to? (XP, 2000, Vista, Windows 7)? Try XP
[*]Make a backup of the file you downloaded
[*]Have you tried deleting the ~/.wine folder and running winecfg again then redo the install?
[/LIST]

---

### Post by jh77if on 2010-09-23
> **cwwilson721 said:**
> We need more info than "it doesn't work"


[LIST]
[*]What actual error messages in the terminal? (Run 'wine <downloadedfile> in the terminal, post the error message here)
[*]What enviornment are you installing to? (XP, 2000, Vista, Windows 7)? Try XP
[*]Make a backup of the file you downloaded
[*]Have you tried deleting the ~/.wine folder and running winecfg again then redo the install?
[/LIST]

did your 4th bullet. it's working properly now. but it was working properly last time i did that earlier today. what happened is when patching 3.3.5 it became corrupt i ran blizzard repair tool and it said that it was unrepairable and that i needed to erase and reinstall. and i was back to square one. i am currently downloading wow on a windows laptop directly to an external hard drive and am planning on copying it to this one if all else fails.

---

### Post by jh77if on 2010-09-23
alright installed properly (and quickly i might add) opened up the launcher hit play. computer adjusted to lower resolution (which is normal for first time run after installation) and then gave me a black screen (not including bottom and top task bars (new to linux dont know what theyre called)) i figured it froze after about 5 minutes of waiting. closed it. tried to reopen it and got "launcher couldn't be opened for some reason. please close all applications and try again" closed all of the open applications (sarcasm;none were open) retried it. same error message. drag and dropped the wow icon into terminal and get:

:~$ '/home/andrew/Desktop/World of Warcraft.desktop' 
/home/andrew/Desktop/World of Warcraft.desktop: line 1: [Desktop: command not found
/home/andrew/Desktop/World of Warcraft.desktop: line 2: of: command not found
system.reg is not a valid registry file
userdef.reg is not a valid registry file
user.reg is not a valid registry file
wine: cannot find 'C:\\Program\'
/home/andrew/Desktop/World of Warcraft.desktop: line 6: here: command not found

**please explain step by step what i should do i am NEW TO UBUNTU. please be polite as well im doing my best to provide info and i dont need people on my case about stuff when im just trying to get an answer :(

---

### Post by pedro_orange on 2010-09-23
What happens when you run the WoW.exe file? 
(Located in ~/.wine/Program Files/World of Warcraft/)

You're dropping the desktop shortcut into the terminal. Thats not going to do a great deal. If we read the output it clearly says:

```
wine: cannot find 'C:\\Program\'
```

This just tells me your shortcut is wrong, it's looking for a folder called "Program" inside "~/.wine", this doesn't exist. Drop the WoW.exe into the terminal and run it, so the command should look something like:

```
wine 'path/to/Warcraft/WoW.exe'
```

Case is important!
Please read the Ubuntu Wiki post on how to install WoW, it's very informative and covers nearly everything you need to know about getting it to work.
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

### Post by jh77if on 2010-09-26
bump help please

---

### Post by jh77if on 2010-09-26
bump, who wants to go remote desktop and figure this out for me.

---

### Post by jh77if on 2010-09-27
> **pedro_orange said:**
> What happens when you run the WoW.exe file? 
(Located in ~/.wine/Program Files/World of Warcraft/)

You're dropping the desktop shortcut into the terminal. Thats not going to do a great deal. If we read the output it clearly says:

```
wine: cannot find 'C:\\Program\'
```This just tells me your shortcut is wrong, it's looking for a folder called "Program" inside "~/.wine", this doesn't exist. Drop the WoW.exe into the terminal and run it, so the command should look something like:

```
wine 'path/to/Warcraft/WoW.exe'
```Case is important!
Please read the Ubuntu Wiki post on how to install WoW, it's very informative and covers nearly everything you need to know about getting it to work.
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

:~$ '/home/andrew/.wine/dosdevices/c:/Program Files/World of Warcraft/Wow.exe' 
err:wineboot:pendingRename couldn't get file attributes (3)
err:wineboot:pendingRename couldn't get file attributes (2)
err:wineboot:pendingRename couldn't get file attributes (2)
fixme:advapi:SetSecurityInfo stub
archive Data\enUS\patch-enUS.MPQ opened
archive Data\patch.MPQ opened
archive Data\enUS\patch-enUS-2.MPQ opened
archive Data\enUS\patch-enUS-3.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\patch-3.MPQ opened
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
fixme:d3d_caps:wined3d_guess_card No card selector available for GL vendor 3 and card vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x39ea1c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f234,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f348,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f50c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f508,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39ef8c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f0c4,0x00000000), stub!
fixme:d3d_caps:wined3d_guess_card No card selector available for GL vendor 3 and card vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x39f428,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:win:EnumDisplayDevicesW ((null),0,0x39ef8c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f0c4,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x153608,0x153508): stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x39f7a8): stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x39f7a8): stub
failed to open C:/Program Files/World of Warcraft/Interface/AddOns
fixme:win:EnumDisplayDevicesW ((null),0,0x39de70,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39de98,0x00000000), stub!
fixme:d3d_caps:wined3d_guess_card No card selector available for GL vendor 3 and card vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x39dd18,0x00000000), stub!
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try adjusting the vblank_mode configuration parameter.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:d3d:buffer_PreLoad Too many declaration changes or converting dynamic buffer, stopping converting
err:d3d_shader:shader_arb_generate_vshader >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glProgramStringARB() @ arb_program_shader.c / 4015
fixme:d3d_shader:shader_arb_generate_vshader HW VertexShader Error at position 128: "line 6, char 16: error: syntax error, unexpected IDENTIFIER\n"

fixme:d3d_shader:shader_arb_dump_program_source     !!ARBvp1.0
fixme:d3d_shader:shader_arb_dump_program_source     TEMP TMP_OUT;
fixme:d3d_shader:shader_arb_dump_program_source     PARAM helper_const = { 2.0, -1.0, 0.0, 0.0 };
fixme:d3d_shader:shader_arb_dump_program_source     TEMP TA;
fixme:d3d_shader:shader_arb_dump_program_source     PARAM posFixup = program.local[0];
fixme:d3d_shader:shader_arb_dump_program_source     DP4 TMP_OUT.x, C0, vertex.attrib[0];
fixme:d3d_shader:shader_arb_dump_program_source     DP4 TMP_OUT.y, C1, vertex.attrib[0];
fixme:d3d_shader:shader_arb_dump_program_source     DP4 TMP_OUT.z, C2, vertex.attrib[0];
fixme:d3d_shader:shader_arb_dump_program_source     DP4 TMP_OUT.w, C3, vertex.attrib[0];
fixme:d3d_shader:shader_arb_dump_program_source     MOV result.color.primary, vertex.attrib[1].zyxw;
fixme:d3d_shader:shader_arb_dump_program_source     MOV result.texcoord[0].xy, vertex.attrib[2];
fixme:d3d_shader:shader_arb_dump_program_source     ADD result.fogcoord, posFixup.x, -posFixup.x;
fixme:d3d_shader:shader_arb_dump_program_source     MUL TA, posFixup, TMP_OUT.w;
fixme:d3d_shader:shader_arb_dump_program_source     ADD TMP_OUT.x, TMP_OUT.x, TA.z;
fixme:d3d_shader:shader_arb_dump_program_source     MAD TMP_OUT.y, TMP_OUT.y, posFixup.y, TA.w;
fixme:d3d_shader:shader_arb_dump_program_source     MOV TA, -helper_const.w;
fixme:d3d_shader:shader_arb_dump_program_source     MOV result.texcoord[7], TA;
fixme:d3d_shader:shader_arb_dump_program_source     MAD TMP_OUT.z, TMP_OUT.z, helper_const.x, -TMP_OUT.w;
fixme:d3d_shader:shader_arb_dump_program_source     MOV result.position, TMP_OUT;
fixme:d3d_shader:shader_arb_dump_program_source     END
fixme:d3d_shader:shader_arb_dump_program_source 
err:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 47
err:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 47
err:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 47

i've read that page you linked multiple times prior. i reinstalled the OS, then wine, then WoW. and then on patch 3.2.0 the installer crashed. so far this has been a game of whack-a-mole. first the installer wouldnt open. then it crashed halfway thru. then it installed all the way and wow wouldnt open rinse repeat etc.

---

### Post by cbilljones on 2010-09-27
Could this be a directx issue? Run with '/home/andrew/.wine/dosdevices/c:/Program Files/World of Warcraft/Wow.exe' -OpenGl
That should force opengl

---

### Post by jh77if on 2010-09-27
> **sanxsaint said:**
> if the console continues not work, it's better to send it to the manufacture. and let the experts do the job.
 
send what to what manufacturer? the console? to ubuntu?

---

### Post by jh77if on 2010-09-27
> **cbilljones said:**
> Could this be a directx issue? Run with '/home/andrew/.wine/dosdevices/c:/Program Files/World of Warcraft/Wow.exe' -OpenGl
That should force opengl

did this. i got the same error 132 which from research is a generalization error where a lot of things could possibly be wrong. in my case it seems to be the memory but I have never opened this machine. and I haven't patched WoW since last time i played on Windows XP. also why would the memory stop working now if it worked FINE on windows last week. ugh!

---

### Post by jh77if on 2010-09-27
ok i ran memtest 86 and passed 100% ok. memory is not the issue. obviously i am doing something wrong with the opengl configuration. someone please direct me

---

### Post by jh77if on 2010-09-27
it appears to be an IRQ problem. just one week ago i did a full 25 man  raid with 20-30 fps on medium settings. I cannot fathom how changing to  ubuntu could cause a problem with my hardware.

---

