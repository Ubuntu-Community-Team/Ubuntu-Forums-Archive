---
title: "Render Creation Error while emulating Morrowind"
date: 2010-04-19
forum: Wine
---

### Post by zomgneeks on 2010-04-19
Hi all,

I'm trying to run the original patched Morrowind with wine.

```

# wine Morrowind.exe err:winediag:X11DRV_WineGL_InitOpenglInfo Direct rendering is disabled, most likely your OpenGL drivers haven't been installed correctly
fixme:d3d_caps:wined3d_guess_card No card selector available for GL vendor 4 and card vendor 0000.
err:d3d:match_fbo_tex_update FBO status 0
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8A8_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8X8_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:d3d:check_fbo_compat Format WINED3DFMT_B5G6R5_UNORM rtInternal format is not supported as FBO color attachment.
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16_UNORM rtInternal format is not supported as FBO color attachment.
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16B16A16_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:win:EnumDisplayDevicesW ((null),0,0x33eed4,0x00000000), stub!

```

a small window also comes up with the message
Render Creation Error: "Unknown stencil mode format."

When wine is in windowed mode an outline of window along with the message window appears. If I minimize the outline the message changes to
Render Creation Error: "Unknown frame buffer mode."

Snooping around online I've found out that this error has something to do with ATI drivers. As far as I know players with nvidia don't have this problem.
But I have an intel card

```

lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

```


I'm going to install the expansions and see what happens.

---

### Post by asdfoo on 2010-04-20
the log tells you in the first line:

err:winediag:X11DRV_WineGL_InitOpenglInfo Direct rendering is disabled, most likely your OpenGL drivers haven't been installed correctly

secondly, do not run wine as root.

---

