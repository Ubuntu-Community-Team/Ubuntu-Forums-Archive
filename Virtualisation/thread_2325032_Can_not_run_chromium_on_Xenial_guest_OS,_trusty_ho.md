---
title: "Can not run chromium on Xenial guest OS, trusty host"
date: 2016-05-18
forum: Virtualisation
---

### Post by ajgreeny on 2016-05-18
I have both Xubuntu and Ubuntu 16.04 64bit systems running as guests on my Xubuntu Trusty host but in both systems I can not get chromium to run and show a window with any content; there is just a window with large black patches showing.

I have taken a screenshot in my guest, and strangely the chromium window in that shows as totally transparent apart from the titlebar.
[ATTACH=CONFIG]269145[/ATTACH]

I have searched as best I can both here and in the VBox forum, the latter of which says "Search is not usable at the moment; try later" and I can find no answer so far so I am now asking if anyone else has seen this and found any solution to it.

All VMs of *ubuntu 14.04 with chromium on the same host work very well; it is only chromium on 16.04 that presents this problem.

Running chromium via terminal command gives the below output, suggesting that compositing may be the problem but I have tried both with and without compositing in both the host and the guest and it makes no difference.  Full screen or windowed also makes no difference.
Firefox runs fine; only chromium presents this behaviour.
```
$ chromium-browser
Using PPAPI flash.
[2327:2327:0516/223334:ERROR:sandbox_linux.cc(334)] InitializeSandbox() called with multiple threads in process gpu-process
[2327:2327:0516/223335:ERROR:texture_manager.cc(2278)] [.CommandBufferContext.Compositor-0x256ca18bd600]GL ERROR :GL_INVALID_ENUM : glTexImage2D: <- error from previous GL command
[2327:2327:0516/223335:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_ENUM : GLES2DecoderImpl::DoBindTexImage2DCHROMIUM: <- error from previous GL command
[2327:2327:0516/223335:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223335:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223335:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223335:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223335:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223335:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223335:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223335:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223335:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223335:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223335:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223335:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223335:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223336:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223336:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223336:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223336:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223336:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223336:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223336:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:texture_manager.cc(2278)] [.CommandBufferContext.RenderCompositor-0x3716585d5c00]GL ERROR :GL_INVALID_ENUM : glTexImage2D: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_ENUM : GLES2DecoderImpl::DoBindTexImage2DCHROMIUM: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2113)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_OPERATION : ScopedTextureBinder::ctor: was unhandled
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223337:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223338:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223338:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223338:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223338:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223338:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223338:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223338:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223338:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223338:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223338:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223338:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223338:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223338:ERROR:gles2_cmd_decoder.cc(2113)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_OPERATION : ScopedTextureBinder::ctor: was unhandled
[2327:2327:0516/223338:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223338:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223338:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223338:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223338:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223338:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223338:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223338:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.RenderWorker-0x3716585d5d80]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223338:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223338:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223339:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223339:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223340:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223340:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223341:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223341:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223342:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223342:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223343:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223343:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223344:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223344:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223345:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223345:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223346:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223346:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223347:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223347:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223348:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223348:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223349:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223349:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223350:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223350:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223351:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223351:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223352:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223352:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223353:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223353:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223354:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223354:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223355:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223355:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223356:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2186:2186:0516/223356:ERROR:logging.h(813)] Failed to call method: org.freedesktop.DBus.ObjectManager.GetManagedObjects: object_path= /: org.freedesktop.DBus.Error.TimedOut: Failed to activate service 'org.bluez': timed out
[2186:2186:0516/223356:ERROR:logging.h(813)] Failed to call method: org.freedesktop.DBus.ObjectManager.GetManagedObjects: object_path= /: org.freedesktop.DBus.Error.TimedOut: Failed to activate service 'org.bluez': timed out
[2327:2327:0516/223356:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223357:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223357:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223358:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223358:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223359:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223359:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223359:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223359:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
[2327:2327:0516/223359:ERROR:gles2_cmd_decoder.cc(2109)] [.CommandBufferContext.CompositorWorker-0x256ca18bd900]GL ERROR :GL_INVALID_VALUE : ScopedTextureBinder::dtor: <- error from previous GL command
```

---

### Post by bapoumba on 2016-05-18
May be this after disabling 3D acceleration ?
[https://forums.virtualbox.org/viewtopic.php?f=3&t=77404](https://forums.virtualbox.org/viewtopic.php?f=3&t=77404)

---

### Post by ajgreeny on 2016-05-18
Oh my goodness; so simple!  Thanks bapoumba.

Why did I not think of doing a search for Google-chrome as well as chromium with this problem.  I have never used chrome in Linux and it did not occur to me to look at that appl;ication instead of chromium.

Presumably this is a problem only in a VM and not something that would occur in a hard metal installation to a machine?  I have only looked at 16.04 as VMs so far and this was a bit of a showstopper if I could not get chromium to run.

---

### Post by bapoumba on 2016-05-19
:)
Yes, I suppose this affects VMs only.

Pick the most representative error line (sometimes there are several) and run that in your favorite search engine. Now you know everything I could ever know.
Of course I stick to subjects I can evaluate or test the fixes/solutions. Hoping you are not too disappointed ^_^

---

### Post by ajgreeny on 2016-05-20
Just as a note related to this 3D problem, I have also found that it is impossible to run chromium in a VBox VM of 14.04, as well as 16.04, and incidentally if you want to use flash 21.0.0.242 by installing the browser-plugin-freshplayer-pepperflash package, that is also stopped by using 3D display in a VM.

---

### Post by MAFoElffen on 2016-05-22
As noted eariler this month, Google has this as a Bug when inside of VM Guests, with VirtualBox. They had this as a bug about a year ago... and is now back again. Still not fixed. And not just with Ubuntu Guests. I would have figured they would have fixed this by now (3 weeks ago), but I was wrong. I also though tit would have been something to do with VirtualBox, but I was wrong with that also.

---

