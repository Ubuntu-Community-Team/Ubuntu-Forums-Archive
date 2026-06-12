---
title: "Error drawing chess boards"
date: 2010-09-07
forum: Wine
---

### Post by oldmankit on 2010-09-07
Hi,

I'm feeling positive about wine as it's worked for those critical applications.  So I'm willing to put work into getting other ones up and working.  Time for: Chessmaster 9000, a brilliant piece of software, unfortunately not designed for linux.

The game loads fine, the opening movie runs, with the following warnings so far:
```

fixme:imm:ImmDisableIME (-1): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x21fa80,0x21f9f0): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x21fa80,0x21f9f0): stub
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x32f6b8,0x00000000), stub!
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_UNSUPPORTED (0x8cdd)
fixme:d3d:context_check_fbo_status     Color attachment 0: (0x387ade8) WINED3DFMT_B8G8R8X8_UNORM 1280x1024
fixme:d3d:context_check_fbo_status     Depth attachment: (0x387af48) WINED3DFMT_D24_UNORM_S8_UINT 1280x1024
err:d3d:IWineD3DDeviceImpl_ClearSurface >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION (0x506) from glClear @ device.c / 4525
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x130b50,0x130ac0): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x130b50,0x130ac0): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x3a50d98,0x3a50c98): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x3a50d98,0x3a50c98): stub
fixme:win:LockWindowUpdate (0x3010a), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!

```I log in successfully, with the following accompaniment:
```

fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x3d89320,0x3a50ea0): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x3d89320,0x3a50ea0): stub
fixme:win:LockWindowUpdate (0x3010a), partial stub!
fixme:win:LockWindowUpdate (0x40270), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:win:LockWindowUpdate (0x3010a), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!

```But when I go to the game room it goes wild messages which all look like a variation on the following theme:
```

err:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION (0x506) from glDrawArrays @ drawprim.c / 53
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_UNSUPPORTED (0x8cdd)
fixme:d3d:context_check_fbo_status     Color attachment 0: (0x387ade8) WINED3DFMT_B8G8R8X8_UNORM 1280x1024
fixme:d3d:context_check_fbo_status     Depth attachment: (0x387af48) WINED3DFMT_D24_UNORM_S8_UINT 1280x1024

```It's drawing the menus OK but I can't actually see a chess board!  Not much use in the end.

I just updated to wine 1.2 but all it did was make the menu text go a crazy pink colour.

Can anyone help me?

---

