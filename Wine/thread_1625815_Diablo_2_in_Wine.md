---
title: "Diablo 2 in Wine"
date: 2010-11-19
forum: Wine
---

### Post by giddensdb on 2010-11-19
I installed Diablo 2 and LOD via the Battle.net clients with no error.  I can't get full screen video or sound during the game.  Sound works in the intro screens until I get to the menu.  Here is the output I get when I start the game.
> broc@broc-Aspire-5515 ~/.wine/drive_c/Program Files/Diablo II $ wine game.exe
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32f084,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:d3d:swapchain_init The application requested more than one back buffer, this is not properly supported.
Please configure the application to use double buffering (1 back buffer) if possible.
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1f40308,0x1f3fbe0): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1f40308,0x1f3fbe0): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1f40308,0x1f3fbe0): stub
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:d3d:swapchain_init The application requested more than one back buffer, this is not properly supported.
Please configure the application to use double buffering (1 back buffer) if possible.
err:d3d:swapchain_setup_fullscreen_window Changing the window style for window 0x20054, but another style (94080000, 00040008) is already stored.
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
err:d3d:swapchain_setup_fullscreen_window Changing the window style for window 0x20054, but another style (94080000, 00040000) is already stored.
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
err:ddraw:IDirectDrawSurfaceImpl_Flip Can't find a flip target
err:ddraw:IDirectDrawSurfaceImpl_Flip Can't find a flip target
err:ddraw:IDirectDrawSurfaceImpl_Flip Can't find a flip target
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:d3d:swapchain_init The application requested more than one back buffer, this is not properly supported.
Please configure the application to use double buffering (1 back buffer) if possible.
err:d3d:swapchain_setup_fullscreen_window Changing the window style for window 0x20054, but another style (94080000, 00040000) is already stored.
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK


---

### Post by khelben1979 on 2010-11-21
I've been running Diablo 2 and the expansion with different versions of Wine and there has been no problem in playing it in window mode or fullscreen, as long as my graphic drivers has been working properly.

For instance, you might be needing non-free drivers if the default graphic driver causes you problem. Do you have problems with other wine applications as well?

---

### Post by got2get on 2010-11-21
you should try to reinstall PlayOnLinux. should be able to find it in the software center
or @ [http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

---

### Post by mastablasta on 2010-11-22
i can run it with openGL patch, but not full screen as i can still see the panels. the problem is sort of solved by hiding the panels.
 
what are your sound card and graphics card?

---

### Post by jandugacek on 2010-11-24
Hi, I have a minor problem with Diablo 2 too. When I try to activate maphack (I am playing on a server where it's allowed), wine tells me something like parent process *UNKNOWN* is hidden, may be a virus/trojan and it prevents the maphack from working. Can someone tell me how to prevent this, please?

---

