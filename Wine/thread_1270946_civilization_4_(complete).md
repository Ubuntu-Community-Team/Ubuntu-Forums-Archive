---
title: "civilization 4 (complete)"
date: 2009-09-20
forum: Wine
---

### Post by Post Monkeh on 2009-09-20
i bought this yesterday (primarily for the extensions for my desktop running xp that already has civ 4 vanilla installed) and thought i would have a go sticking it on my laptop (asus x58l, 2ghz celeron processor, 2 gb ram, intel gma x3100 running jaunty).

i didn't actually hold out much hope of getting it working, after doing a bit of research and seeing the number of problems some people were having, but i used [this]("http://forums.civfanatics.com/showthread.php?t=327508") guide to install (i wiped wine and did a clean install) and everything actually worked pretty well. civ 4, and worlords were already fully patched, and the BTS patch installed easily. i used a no cd exe for civ 4 & warlords (although tbh both games loaded up fine with the cd in the drive)

the problem is the graphics. i realise my graphics card isn't going to be able to run everything super-fast, but the game itself runs ok, however EVERYTHING that isn't a menu is blank, or very very distorted. i've attached a few screenies to show what i mean. also, if you scroll the screen in the main game, everything creates ghost images. yet the menus are perfect

it's a little annoying because it seems like i'm so close to getting it working, and it looks like it should be some fairly simple setting that needs adjusted, but i'm beat.
i've tried copying all the d3dx9_xx.dll files from 24 to 34 into my system 32 folder, i've tried setting over rides for them all, and i've also trie3d using winetricks to install the d3dx9 package, but it still does the same thing.

anyone have any idea what might be wrong? (by the way, i'm running wine-1.1.29)

---

### Post by Post Monkeh on 2009-09-20
i tried to get a terminal output of a game load from running beyond the sword until starting a new game, but i had so many errors that the terminal got full.

here's what was left after i exited the game

```
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d:IWineD3DDeviceImpl_ClearSurface >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glClear @ device.c / 5042
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d:IWineD3DDeviceImpl_ClearSurface >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glClear @ device.c / 5042
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d:IWineD3DDeviceImpl_ClearSurface >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glClear @ device.c / 5042
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d:IWineD3DDeviceImpl_ClearSurface >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glClear @ device.c / 5042
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d:IWineD3DDeviceImpl_ClearSurface >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glClear @ device.c / 5042
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d:IWineD3DDeviceImpl_ClearSurface >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glClear @ device.c / 5042
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d:IWineD3DDeviceImpl_ClearSurface >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glClear @ device.c / 5042
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d:IWineD3DDeviceImpl_ClearSurface >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glClear @ device.c / 5042
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT_EXT (0x8cd6)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x1be4a6e0) WINED3DFMT_X8R8G8B8 256x128
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x1be6a878) WINED3DFMT_D24S8 256x128
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION_EXT (0x506) from glDrawElements @ drawprim.c / 50
fixme:wtsapi:WTSUnRegisterSessionNotification Stub 0x20032
civ@will-laptop:~$ 

```

here's what i get if i just load the game up, then exit without trying to start a game

```
civ@will-laptop:~$ wine /home/civ/.wine/drive_c/Program\ Files/2K\ Games/Firaxis\ Games/Sid\ Meier\'s\ Civilization\ 4\ Complete/Beyond\ the\ Sword/Civ4BeyondSword
fixme:system:SystemParametersInfoW Unimplemented action: 55 (SPI_SETMOUSEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
err:menubuilder:Process_Link unable to load L"C:\\Program Files\\2K Games\\Firaxis Games\\Sid Meier's Civilization 4 Complete\\Beyond the Sword\\Logs.lnk"
fixme:shell:DllCanUnloadNow stub
err:menubuilder:WinMain failed to build menu item for C:\Program Files\2K Games\Firaxis Games\Sid Meier's Civilization 4 Complete\Beyond the Sword\Logs.lnk
err:menubuilder:Process_Link unable to load L"C:\\Program Files\\2K Games\\Firaxis Games\\Sid Meier's Civilization 4 Complete\\Beyond the Sword\\Saves.lnk"
fixme:shell:DllCanUnloadNow stub
err:menubuilder:WinMain failed to build menu item for C:\Program Files\2K Games\Firaxis Games\Sid Meier's Civilization 4 Complete\Beyond the Sword\Saves.lnk
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x20032 0x00000000
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:shell:DllCanUnloadNow stub
err:menubuilder:Process_Link unable to load L"C:\\Program Files\\2K Games\\Firaxis Games\\Sid Meier's Civilization 4 Complete\\Beyond the Sword\\CivilizationIV.ini.lnk"
fixme:shell:DllCanUnloadNow stub
err:menubuilder:WinMain failed to build menu item for C:\Program Files\2K Games\Firaxis Games\Sid Meier's Civilization 4 Complete\Beyond the Sword\CivilizationIV.ini.lnk
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
'import site' failed; use -v for traceback
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:win:EnumDisplayDevicesW ((null),0,0x32eee8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f420,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f42c,0x00000000), stub!
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:win:EnumDisplayDevicesW ((null),0,0x32ef74,0x00000000), stub!
fixme:d3d:state_lastpixel Last Pixel Drawing Disabled, not handled yet
fixme:wtsapi:WTSUnRegisterSessionNotification Stub 0x20032
civ@will-laptop:~$
```

btw, at first i was using wine version 1.1.29, but i downgraded to 1.1.25 as stated in the guide.

also, i can't get it to run as win2000, i can only get it to run as xp.

---

### Post by hikaricore on 2009-09-20
There are no errors in the first block you posted.

As far as I can tell in the 2nd block the only errors are pertaining to .lnk files which I assume the game is trying to access?
These may be ***dows shortcuts and are probably not handled by WINE for one reason or another mostly because they shouldn't have to be.

---

### Post by Post Monkeh on 2009-09-20
are all those invalid frame buffer arguments ok then?

it could be a problem with my system more than anything else. there are some minor graphical quirks when i do various things (watching flash videos for instance) 
like i said, i didn't think i'd even get the game running, but to have it run pretty well in terms of speed, yet not display the textures is just teasing.

also, i've tried an install of civ 4 vanilla (after wiping my wine folder) and i still get the same graphical glitches even after updating to 1.74.

i've seen other people saying they have civ running under wine with my graphics card, so i guess it's one of my settings causing the problems.

---

### Post by simon013 on 2009-11-14
i had a similar issue under wine 1.1.32 and civilization 4 with 9.10, karmic koala. i have a crappy intel graphics controller, so perhaps that's it?

so the movies loaded pretty bad, but they still were bad when this was a windows computer. then i get to the menu and its totally normal. all the staging parts of the game look fine. except, when i choose maps, it does not show the land mass, just blackness. during the loading of the actual game, after the staging windows, the map is all messed up. the tiles are a combination of white, grey, and pixelated chunks of green. And it becomes incredibly laggy. I cannot see anything well enough to play the game. I pretty much have tried everything, so I'm convinced it's the graphics card.

Anyone have any ideas?

---

### Post by Post Monkeh on 2009-12-27
i installed windows xp and civ 4 runs flawlessly, i guess the driver for the graphics card is the problem. seems a bit of a waste to have an entire os installed to run a game, but then civ 4 is some game

---

