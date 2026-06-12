---
title: "snowbound online + wine = error"
date: 2010-04-09
forum: Wine
---

### Post by luvgirl12345 on 2010-04-09
could someone look at this and tell me what wrong with the firewall? p.s. [SIZE="1"]im using lucid 10.4 beta 2 xD[/SIZE]

---

### Post by asdfoo on 2010-04-09
> **luvgirl12345 said:**
> ```
lorenz@lorenz-desktop:~$ wine '/home/lorenz/.wine/dosdevices/c:/gamigo/SnowBoundOnline/Run.exe' 
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 53 (SPI_SETTOGGLEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 51 (SPI_SETFILTERKEYS)
fixme:hnetcfg:fw_app_get_Enabled 0x135ab0, 0x32f580
Authorized application C:\GAMIGO\SNOWBOUNDONLINE\RUN.EXE is disabled in the firewall.
fixme:hnetcfg:fw_app_get_Enabled 0x135ab0, 0x32f534
Authorized application C:\GAMIGO\SNOWBOUNDONLINE\RUN.EXE is disabled in the firewall.
fixme:hnetcfg:fw_app_put_ProcessImageFileName 0x135ab0, L"C:\\GAMIGO\\SNOWBOUNDONLINE\\RUN.EXE"
fixme:hnetcfg:fw_app_put_Name 0x135ab0, L"SnowBound Online"
fixme:hnetcfg:fw_apps_Add 0x135a68, 0x135ab0
Authorized application C:\GAMIGO\SNOWBOUNDONLINE\RUN.EXE is now enabled in the firewall.
err:winediag:X11DRV_WineGL_InitOpenglInfo Direct rendering is disabled, most likely your OpenGL drivers haven't been installed correctly
err:d3d:match_fbo_tex_update FBO status 0
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8A8_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8X8_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:d3d:check_fbo_compat Format WINED3DFMT_B5G6R5_UNORM rtInternal format is not supported as FBO color attachment.
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16_UNORM rtInternal format is not supported as FBO color attachment.
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16B16A16_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:win:EnumDisplayDevicesW ((null),0,0x32ef24,0x00000000), stub!
X Error of failed request:  GLXBadDrawable
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  1470
  Current serial number in output stream:  1470
lorenz@lorenz-desktop:~$ 

```

could someone look at this and tell me what wrong with the firewall? p.s. [SIZE="1"]im using lucid 10.4 beta 2 xD[/SIZE]

please start the application correctly by cd'ing into the install directory and then starting it.

make sure you are using the most recent version of Wine, 1.1.42

---

