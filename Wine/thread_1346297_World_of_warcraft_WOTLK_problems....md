---
title: "World of warcraft WOTLK problems..."
date: 2009-12-04
forum: Wine
---

### Post by domosplace on 2009-12-04
Hey everyone

Im a complete noobie to Ubuntu 9.10 I love to Ubuntu about 3 weeks ago and been looking for away to fix my wow problem. I have downloaded wow successful with no problem. I know the lancher locks the wow file. My problem is i cant seem to get pass the video. It closes wow completely. I ran it thur terminal here is the following 
[php]
lee@lee-desktop:~$ env WINEPREFIX="/home/lee/.wine" wine "C:\Program Files\World of Warcraft\Wow.exe"
fixme:advapi:SetSecurityInfo stub
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
fixme:win:EnumDisplayDevicesW ((null),0,0x39ed54,0x00000000), stub!
fixme:d3d_caps:wined3d_guess_vendor Received unrecognized GL_VENDOR "VA Linux Systems, Inc.". Returning VENDOR_WINE.
fixme:win:EnumDisplayDevicesW ((null),0,0x39eb44,0x00000000), stub!
fixme:d3d_caps:wined3d_guess_vendor Received unrecognized GL_VENDOR "VA Linux Systems, Inc.". Returning VENDOR_WINE.
fixme:win:EnumDisplayDevicesW ((null),0,0x39f01c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f264,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f3c4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f534,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f530,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39efa4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f0e4,0x00000000), stub!
fixme:d3d_caps:wined3d_guess_vendor Received unrecognized GL_VENDOR "VA Linux Systems, Inc.". Returning VENDOR_WINE.
fixme:win:EnumDisplayDevicesW ((null),0,0x39f54c,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexEnvf(GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, GL_COMBINE_EXT); @ context.c / 1310
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x186de:cool: Event query: Unimplemented, but pretending to be supported
fixme:win:EnumDisplayDevicesW ((null),0,0x39efa4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f0e4,0x00000000), stub!
failed to open C:/Program Files/World of Warcraft/Interface/AddOns
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:d3d:state_psizemin_w WINED3DRS_POINTSIZE_MIN not supported on this opengl, value is 0.000000
fixme:d3d:state_psizemin_w WINED3DRS_POINTSIZE_MAX not supported on this opengl, value is 1.000000
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, comb_target, GL_MODULATE @ state.c / 2473
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src0_target, src1 @ state.c / 2475
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr0_target, opr1 @ state.c / 2477
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src1_target, src2 @ state.c / 2479
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr1_target, opr2 @ state.c / 2481
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, scal_target, 1 @ state.c / 2483
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, useext(GL_COMBINE) @ state.c / 2916
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, comb_target, GL_MODULATE @ state.c / 2473
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src0_target, src1 @ state.c / 2475
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr0_target, opr1 @ state.c / 2477
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src1_target, src2 @ state.c / 2479
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr1_target, opr2 @ state.c / 2481
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, scal_target, 1 @ state.c / 2483
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, useext(GL_COMBINE) @ state.c / 2916
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, comb_target, GL_REPLACE @ state.c / 2443
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src0_target, GL_PREVIOUS_EXT @ state.c / 2445
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr0_target, GL_SRC_ALPHA @ state.c / 2447
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, scal_target, 1 @ state.c / 2449
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, useext(GL_COMBINE) @ state.c / 2916
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, comb_target, GL_REPLACE @ state.c / 2443
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src0_target, GL_PREVIOUS_EXT @ state.c / 2445
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr0_target, GL_SRC_ALPHA @ state.c / 2447
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, scal_target, 1 @ state.c / 2449
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, useext(GL_COMBINE) @ state.c / 2916
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, comb_target, GL_REPLACE @ state.c / 2443
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src0_target, GL_PREVIOUS_EXT @ state.c / 2445
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr0_target, GL_SRC_ALPHA @ state.c / 2447
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, scal_target, 1 @ state.c / 2449
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, useext(GL_COMBINE) @ state.c / 2916
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, comb_target, GL_REPLACE @ state.c / 2443
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src0_target, GL_PREVIOUS_EXT @ state.c / 2445
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr0_target, GL_SRC_ALPHA @ state.c / 2447
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, scal_target, 1 @ state.c / 2449
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, useext(GL_COMBINE) @ state.c / 2916
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, comb_target, GL_REPLACE @ state.c / 2443
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src0_target, GL_PREVIOUS_EXT @ state.c / 2445
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr0_target, GL_SRC_ALPHA @ state.c / 2447
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, scal_target, 1 @ state.c / 2449
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, useext(GL_COMBINE) @ state.c / 2916
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, comb_target, GL_REPLACE @ state.c / 2443
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src0_target, GL_PREVIOUS_EXT @ state.c / 2445
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr0_target, GL_SRC_ALPHA @ state.c / 2447
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, scal_target, 1 @ state.c / 2449
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, useext(GL_COMBINE) @ state.c / 2916
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, comb_target, GL_REPLACE @ state.c / 2443
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src0_target, GL_PREVIOUS_EXT @ state.c / 2445
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr0_target, GL_SRC_ALPHA @ state.c / 2447
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, scal_target, 1 @ state.c / 2449
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, useext(GL_COMBINE) @ state.c / 2916
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, comb_target, GL_REPLACE @ state.c / 2443
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src0_target, GL_PREVIOUS_EXT @ state.c / 2445
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr0_target, GL_SRC_ALPHA @ state.c / 2447
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, scal_target, 1 @ state.c / 2449
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, useext(GL_COMBINE) @ state.c / 2916
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, comb_target, GL_MODULATE @ state.c / 2473
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src0_target, src1 @ state.c / 2475
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr0_target, opr1 @ state.c / 2477
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src1_target, src2 @ state.c / 2479
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr1_target, opr2 @ state.c / 2481
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, scal_target, 1 @ state.c / 2483
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, useext(GL_COMBINE) @ state.c / 2916
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, comb_target, GL_MODULATE @ state.c / 2473
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src0_target, src1 @ state.c / 2475
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr0_target, opr1 @ state.c / 2477
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src1_target, src2 @ state.c / 2479
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr1_target, opr2 @ state.c / 2481
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, scal_target, 1 @ state.c / 2483
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, useext(GL_COMBINE) @ state.c / 2916
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, comb_target, GL_MODULATE @ state.c / 2473
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src0_target, src1 @ state.c / 2475
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr0_target, opr1 @ state.c / 2477
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src1_target, src2 @ state.c / 2479
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr1_target, opr2 @ state.c / 2481
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, scal_target, 1 @ state.c / 2483
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, useext(GL_COMBINE) @ state.c / 2916
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, comb_target, GL_MODULATE @ state.c / 2487
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src0_target, src1 @ state.c / 2489
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr0_target, opr1 @ state.c / 2491
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src1_target, src2 @ state.c / 2493
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr1_target, opr2 @ state.c / 2495
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, scal_target, 2 @ state.c / 2497
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, useext(GL_COMBINE) @ state.c / 2916
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, comb_target, GL_MODULATE @ state.c / 2487
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src0_target, src1 @ state.c / 2489
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr0_target, opr1 @ state.c / 2491
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src1_target, src2 @ state.c / 2493
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr1_target, opr2 @ state.c / 2495
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, scal_target, 2 @ state.c / 2497
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, useext(GL_COMBINE) @ state.c / 2916
Error: Rage 128 timed out... exiting
[/php]Now i couldnt find the confwtf that everyone was talking about should i put the opengl in the Runonce_WLK.wtf thing or what? I mean i left windows to the dogs and i really dont wanna go back at all. I have configured wine like they said in all the other fourms i have read. Im completely lost and i really wanna play wow. Oh i cant get the patches to download 
I get the following
[php]
lee@lee-desktop:~$ env WINEPREFIX="/home/lee/.wine" wine "C:\Program Files\World of Warcraft\Blizzard Updater.exe" 
Missing symbol {InternalArchive}! (SymbolTable::UnmappedSymbolSubstitution)
Missing symbol {InternalArchive}! (SymbolTable::UnmappedSymbolSubstitution)
fixme:eek:le:OleCreateStaticFromData (not shown), stub!
[/php]and when i try to run the background downloader i get following 
[php]
lee@lee-desktop:~$ env WINEPREFIX="/home/lee/.wine" wine "C:\Program Files\World of Warcraft\BackgroundDownloader.exe" -
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 60000

http error code = 404
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 60000
[/php]no i know these are problems i can fix i just dont know where to start...

and another thing my monitor is Unknown how do i fix that too

My computer
Dell Dimension 4500
Vid- 32mb Ati Rage 128 Ultra
1 GB ram 
40gb HD 

I really need help i will be on here every day untill i get a reply to fix this. I am also willing to fix this over aim just send me a private message and i will send u my aim or yahoo i also have a msn but dont use it but i will if u have one. thank you very much 

Oh and i forgot since i was reading up up on drivers i didnt download one cause i didnt know how too also this OS really doesnt have one that works with my video card...

Thanks Lee[

---

