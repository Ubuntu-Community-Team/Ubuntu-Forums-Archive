---
title: "World of Warcraft - Screen Tearing"
date: 2010-03-23
forum: Wine
---

### Post by khormin on 2010-03-23
Using Ubuntu 9.10, WINE 1.0.1 (system keeps locking on trying to add the ppa for the development version). i3 system w/ higher-end nVidia card. I'm using the restricted drivers, ensured they're not the 'broken' ones that cause fan failure. 
 
I've taken the time to add a registry key for Direct3D, and am making sure that the system is using OpenGL rather than piling it over DirectX as it is normally wont. 
 
The system is eating WoW in maximum settings without having to pause for dessert, but for an error that keeps arising in areas of high population / multiple 'zone loading'. 
 
The error takes form as 'shards' of color radiating out at random, though only within the graphics region of the game; my user interface (a layer series over the top of the graphics) is unaffected. Reloadui (a command to reset the game as though you have just freshly logged in) does nothing to affect the issue (it logs you back in with the same torn graphics), but a full shut-down and restart of WINE removes the issue until it arises next. 
 
Unfortunately, running it in terminal to produce a log file hasn't given me any clues; included below is the results of that file. I'm new to Linux (fresh from Windows a week ago), but have picked up the basics and have a background with computers; if there's anything else I can do to help flesh out this issue, let me know. And thanks if you can help.

Same issue as in: [http://ubuntuforums.org/showthread.php?t=826304](http://ubuntuforums.org/showthread.php?t=826304)

Unlike the above, this is on a commercial server, using a legitimate copy of World of Warcraft.

[INDENT]fixme:advapi:SetSecurityInfo stub 
fixme:win:EnumDisplayDevicesW ((null),0,0x39ed8c,0x00000000), stub! 
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers 
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers 
fixme:win:EnumDisplayDevicesW ((null),0,0x39ec5c,0x00000000), stub! 
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers 
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers 
fixme:win:EnumDisplayDevicesW ((null),0,0x39f134,0x00000000), stub! 
fixme:win:EnumDisplayDevicesW ((null),0,0x39f3d0,0x00000000), stub! 
fixme:win:EnumDisplayDevicesW ((null),0,0x39f568,0x00000000), stub! 
fixme:win:EnumDisplayDevicesW ((null),0,0x39f564,0x00000000), stub! 
fixme:win:EnumDisplayDevicesW ((null),0,0x39f558,0x00000000), stub! 
fixme:win:EnumDisplayDevicesW ((null),0,0x39f120,0x00000000), stub! 
fixme:win:EnumDisplayDevicesW ((null),0,0x39ded0,0x00000000), stub! 
fixme:win:EnumDisplayDevicesW ((null),0,0x39def8,0x00000000), stub! 
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB 
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB 
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB 
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 
fixme:reg:GetNativeSystemInfo (0x37404484) using GetSystemInfo() 
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB 
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB 
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB 
fixme:win:EnumDisplayDevicesW ((null),0,0x39da98,0x00000000), stub! 
fixme:imm:ImmReleaseContext (0x30024, 0x1379c8): stub 
fixme:win:EnumDisplayDevicesW ((null),0,0x39de88,0x00000000), stub! 
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB 
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB 
fixme:win:EnumDisplayDevicesW ((null),0,0x39da98,0x00000000), stub! 
fixme:win:EnumDisplayDevicesW ((null),0,0x39de88,0x00000000), stub! 
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB 
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB 
fixme:win:EnumDisplayDevicesW ((null),0,0x39da98,0x00000000), stub! 
fixme:win:EnumDisplayDevicesW ((null),0,0x39de88,0x00000000), stub! 
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB 
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB 
fixme:win:EnumDisplayDevicesW ((null),0,0x39da98,0x00000000), stub! 
err:ntdll:RtlpWaitForCriticalSection section 0x552e7bc "?" wait timed out in thread 002d, blocked by 0009, retrying (60 sec) 
err:ntdll:RtlpWaitForCriticalSection section 0x552e7bc "?" wait timed out in thread 002d, blocked by 0009, retrying (60 sec) 
fixme:win:EnumDisplayDevicesW ((null),0,0x39de88,0x00000000), stub! 
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB 
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB 
fixme:win:EnumDisplayDevicesW ((null),0,0x39da98,0x00000000), stub![/INDENT]

---

### Post by dazer26 on 2010-03-24
Try installing the latest version of wine from here...

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

I have always had issues with the "stable" version of wine.  I also run wow in DirectX mode with the newer versions as it runs just as well as the opengl mode except you get a hardware cursor.

Edit:
Just noticed that you couldn't add the ppa.  Are you using synaptic?  It almost sounds like your list of repos is broken, are you able to update your system or do you get an error?

---

### Post by khormin on 2010-03-24
I can update, but adding the ppa crashes me out, with Synaptic, the Software Sources admin tool, and with the terminal instructions; [I]sudo add-apt-repository ppa:ubuntu-wine/ppa

[/I]Terminal hangs after a few seconds of updating, and Synaptic simply freezes right up, greys out, then crashes out after approximately fifteen minutes of silence. Software Sources has identical results to Synaptic. And I have some other ppas for canonical and for a while there had the Play On Linux ppa as well; I can update them easily...

---

