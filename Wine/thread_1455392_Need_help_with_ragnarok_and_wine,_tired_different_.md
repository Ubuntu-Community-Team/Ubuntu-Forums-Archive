---
title: "Need help with ragnarok and wine, tired different things nothing has worked"
date: 2010-04-15
forum: Wine
---

### Post by Linux Ninja2 on 2010-04-15
Been on linux (ubuntu 9.10) for about a month now. Starting to get the hang of it. The only thing from windows I am missing is being able to play this game. I've read a lot of stuff on the net and tried different things. Some say i need to trick the ip but I am unable to figure out the server IP address. A lot of private servers have certain things in place to prevent hacking, so I think that might be why i am unable to find the ip address. But I think there are other problems as well. This is the code I get when I run the program (winetricks allfonts corefonts, allcodecs drdx9 d3dx10 directx9 dinput8 directplay gdiplus): 
 
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1835b0,0x1839e0): stub 
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1835b0,0x1839e0): stub 
fixme:d3d_caps:wined3d_guess_card No card selector available for GL vendor 3 and card vendor 8086. 
fixme:win:EnumDisplayDevicesW ((null),0,0x32f2ec,0x00000000), stub! 
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats 
fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (112,0)-(918,625) 
fixme:imm:ImmReleaseContext (0x10054, 0x134778): stub 
fixme:ddraw:IDirectDrawImpl_RestoreAllSurfaces (0x1b8070): Stub 
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x1b8070)->(1,(nil)): Stub 
^Ca17@a17-laptop:~/.wine/dosdevices/c:/Program Files/Gravity/RO$ wine drolr.exe 
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1835b0,0x1839e0): stub 
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1835b0,0x1839e0): stub 
fixme:d3d_caps:wined3d_guess_card No card selector available for GL vendor 3 and card vendor 8086. 
fixme:win:EnumDisplayDevicesW ((null),0,0x32f2ec,0x00000000), stub! 
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats 
fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (112,0)-(918,625) 
fixme:imm:ImmReleaseContext (0x10054, 0x134778): stub 
fixme:ddraw:IDirectDrawImpl_RestoreAllSurfaces (0x1b8070): Stub 
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x1b8070)->(1,(nil)): Stub 
fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (112,0)-(918,625) 
err:d3d_surface:IWineGDISurfaceImpl_UnLoad (0x1c3710): UnLoad is not supported on X11 surfaces! 
err:d3d_surface:IWineGDISurfaceImpl_UnLoad (0x1c3710): Most likely the parent library did something wrong. 
err:d3d_surface:IWineGDISurfaceImpl_UnLoad (0x1c3710): Please report to wine-devel 
fixme:d3d:IWineD3DDeviceImpl_Release (0x1c0570) Device released with resources still bound, acceptable but unexpected 
fixme:d3d:dumpResources Leftover resource 0x1c3710 with type 1,WINED3DRTYPE_SURFACE 
 
##### 
This is the in game error that comes up in wine 
 
Module Name: C:\Program Files\Gravity\RO\drolr.exe 
Time Stamp: 0x4ad4401b - Tue Oct 13 01:53:47 2009 
 
 
Exception Type: 0xc0000005 
 
0x005f2404	drolr 
0x005f02b4	drolr 
0x005efe58	drolr 
0x006e22d0	drolr 
0x006f6b4c	drolr 
0x7b858af4	kernel32 
0x7bc6efa4	ntdll 
0x7bc6f170	ntdll 
0x7bc4afea	ntdll 
0x68007e9d	 
 
eax: 0x0001581b	ebx: 0x6862af70 
ecx: 0x00000000	edx: 0x00000000 
esi: 0x0001d4c0	edi: 0x0c78aa68 
ebp: 0x0032faa4	esp: 0x0032fa8c 
 
stack 0032fa8c - 0032fe8c 
0032FA8C : 00 00 00 00 00 00 00 00 00 00 00 00 6A EF 7D 00  
0032FA9C : 68 AA 78 0C FF FF FF FF C0 FA 32 00 B4 02 5F 00  
0032FAAC : 04 00 00 00 6A EF 7D 00 68 AA 78 0C FF FF FF FF  
0032FABC : EC FA 32 00 EC FA 32 00 58 FE 5E 00 92 EF 7D 00  
0032FACC : 58 EF 7D 00 2C 75 51 00 18 FE 32 00 10 CE 77 00  
0032FADC : 00 00 00 00 98 FE 32 00 26 F5 70 00 FF FF FF FF  
0032FAEC : 1C FE 32 00 D0 22 6E 00 00 00 00 00 68 AA 78 0C  
0032FAFC : 6C 6A 6F 00 00 00 00 00 F4 1F 88 7B 00 00 00 00  
0032FB0C : 60 CB 12 00 48 49 4A 4B 4C 4D 4E 4F 50 51 52 53  
0032FB1C : 54 55 56 57 58 59 5A 5B 5C 5D 5E 5F 60 CB 12 00  
0032FB2C : 44 45 46 47 48 49 4A 4B 4C 4D 4E 4F 50 51 52 53  
0032FB3C : 40 05 11 00 60 CB 12 00 7C 7D 7E 7F 80 81 82 83  
0032FB4C : 84 85 86 87 88 89 8A 8B 8C 8D 8E 8F 90 91 92 93  
0032FB5C : 94 95 96 97 98 99 8A 9B 8C 9D 8E 9F A0 A1 A2 A3  
0032FB6C : A4 A5 A6 A7 A8 A9 AA AB AC AD AE AF B0 B1 B2 B3  
0032FB7C : B4 3F B6 B7 B8 B9 BA BB BC BD BE BF C0 C1 C2 C3  
 
Launch Info  
0000 0000 0000 0000 0000 0000 0000 0000  
0000 0000 0000 0000 0000 0000 0000 0000  
0000 0000 0000 0000 0000 0000 0000 0000  
0000 0000 0000 0000 0000 0000 0000 0000  
 
Job : Novice 
 
 
Any help you can give will be most appreciated as this is the only game I really have an interest in.

---

### Post by dino99 on 2010-04-16
i suppose you're using the latest wine release, the first thing to be found about that game is what it needs to be run and only add the required dll with winetricks + fonts

have you looked into .wine/drive_c/your game/logs

an other way is to try playonlinux

---

