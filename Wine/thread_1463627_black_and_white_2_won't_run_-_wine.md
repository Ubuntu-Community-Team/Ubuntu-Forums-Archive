---
title: "black and white 2 won't run - wine"
date: 2010-04-27
forum: Wine
---

### Post by jason_n89 on 2010-04-27
i've been having a bit of a problem with wine. my distro is ubuntu karmic on an acer aspire 57207, i'm running wine 1.1.42 and have installed winetricks. when i open the file from the gui it loads to the main menu but when i try to start a new game it encounters a "serious error" and needs to shutdown the program. when i try to run it through the shell the game does  not even initialize and wine pipes this code at me

ALSA lib pcm_dsnoop.c:559:(snd_pcm_dsnoop_open) unable to create IPC semaphore
fixme:heap:HeapSetInformation 0x2b20000 0 0x269fd4c 4
fixme:process:GetProcessWorkingSetSize (0xffffffff,0x269f77c,0x269f780): stub
fixme:process:GetProcessWorkingSetSize (0xffffffff,0x269f77c,0x269f780): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x269f064,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x269f1f4,0x00000000), stub!

i've tried looking through the forums and the only information they give is patch it to v1.2 and nocd crack which i have done and still to no avail and am at a total loss. any suggestions would be greatly appreciated. thank you

---

### Post by asdfoo on 2010-04-28
Try with Wine 1.1.43

also, when you start it with the shell, make sure you cd to the install directory first

---

### Post by jason_n89 on 2010-04-29
well navigating to the folder got it to get to the start menu...however it still hangs at the same place. wine also pipes out a lot more data which i have included as an attachment. i will try 1.1.43 in the morning but i really doubt any change as i have now tried it with both versions of wine available through the software channel (1.0.1 and 1.1.31) as well as well as 1.1.42. i think it may be a configuration problem.

---

### Post by jason_n89 on 2010-04-30
> **asdfoo said:**
> Try with Wine 1.1.43

also, when you start it with the shell, make sure you cd to the install directory first

after doing this the game kind of runs but it seems as tho a graphics layer is missing. in the shell it still has all the d3d errors. is it possible that it is my graphics driver that is the problem?

---

### Post by asdfoo on 2010-04-30
could you attach plain text log, I don't have open office here

---

### Post by jason_n89 on 2010-04-30
i decided to just take a sample as it is all much the same

for the main menu and intro movie it has a lot of this
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x1692f0) Unhandled query type 4
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table

then in the actual game it pipes stuff like this
err:d3d_shader:shader_glsl_deselect_depth_blt >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION (0x506) from glUseProgramObjectARB @ glsl_shader.c / 4612
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1503
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1503
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1503
err:d3d_shader:shader_glsl_deselect_depth_blt >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION (0x506) from glUseProgramObjectARB @ glsl_shader.c / 4612
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1503
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1503
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1503
err:d3d_shader:shader_glsl_deselect_depth_blt >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION (0x506) from glUseProgramObjectARB @ glsl_shader.c / 4612
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1503
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1503
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1503
err:d3d_shader:shader_glsl_deselect_depth_blt >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION (0x506) from glUseProgramObjectARB @ glsl_shader.c / 4612
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1503
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1503
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1503
err:d3d_shader:shader_glsl_deselect_depth_blt >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION (0x506) from glUseProgramObjectARB @ glsl_shader.c / 4612
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1503
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1503
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1503
err:d3d_shader:shader_glsl_deselect_depth_blt >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION (0x506) from glUseProgramObjectARB @ glsl_shader.c / 4612
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1503
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1503

---

### Post by jason_n89 on 2010-04-30
also i have been doin a little experimenting, every program i open with wine regardless of if they run or not pipe this (and sometimes nothing more) initially

fixme:d3d_caps:wined3d_guess_card No card selector available for GL vendor 3 and card vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x32eb88,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1e57a0,0x1e5710): stub

---

### Post by asdfoo on 2010-04-30
> **jason_n89 said:**
> also i have been doin a little experimenting, every program i open with wine regardless of if they run or not pipe this (and sometimes nothing more) initially

fixme:d3d_caps:wined3d_guess_card No card selector available for GL vendor 3 and card vendor 8086.


hmm, do you have an intel video card?

---

### Post by jason_n89 on 2010-04-30
yes it's "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller" ccording to system profiler. is that a problem when it comes to ubuntu?

---

### Post by asdfoo on 2010-04-30
> **jason_n89 said:**
> yes it's "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller" ccording to system profiler. is that a problem when it comes to ubuntu?

Speaking generally, the video drivers for intel cards don't have as feature complete drivers as nvidia/ati.  Never the less, Wine tries to cater for them but sometimes it's not 100%.

If you're comfortable with compiling Wine from latest git (or atleast want to venture trying) you might have some luck.  The d3d area of Wine is always undergoing constant change due to improvements, restructuring and so on.  Recently it caused Intel to work less well, but I think I read within the past few days they're trying to fix that.

If you get the latest git and it still doesn't work properly (shows those opengl/shader errors), it's probably worth filing a bug report in the wine bugzilla.   Just make sure to attach as a text file (not paste) the terminal output with the latest git.

If you don't want to go to the trouble of compiling, I think 1.1.44 is due to be released in about 6 hours.

---

### Post by jason_n89 on 2010-04-30
thanks mate you been a huge help, i'll check wine for updates in the morning (more than 6 hours away) and if that doesn't work well i guess i'll have fun and try the git method. also i think i may try a dual boot with xp if nether of those work. anyways will mark as solved thanks

---

