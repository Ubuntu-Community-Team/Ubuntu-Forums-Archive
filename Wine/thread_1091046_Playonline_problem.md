---
title: "Playonline problem"
date: 2009-03-09
forum: Wine
---

### Post by Bofur on 2009-03-09
Apparently I posted this in the wrong discussion so here it is again: 

When I try running Playonline I get a black screen. I've done the dx override as native but it still doesn't work. Here is my output: 
```
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:dsound:IKsPrivatePropertySetImpl_Get unsupported property: {f2957840-260c-11d1-a4d8-00c04fc28aca}
fixme:advapi:GetCurrentHwProfileA (0x32f46c) semi-stub
fixme:advapi:GetCurrentHwProfileA (0x32f498) semi-stub
fixme:advapi:GetCurrentHwProfileA (0x32f2f4) semi-stub
fixme:advapi:GetCurrentHwProfileA (0x32f2f4) semi-stub
fixme:advapi:GetCurrentHwProfileA (0x32f2f4) semi-stub
fixme:advapi:GetCurrentHwProfileA (0x32f2f4) semi-stub
fixme:advapi:GetCurrentHwProfileA (0x32f2f4) semi-stub
fixme:advapi:GetCurrentHwProfileA (0x32f2f4) semi-stub
fixme:advapi:GetCurrentHwProfileA (0x32f2f4) semi-stub
fixme:advapi:GetCurrentHwProfileA (0x32f2f4) semi-stub
fixme:advapi:GetCurrentHwProfileA (0x32f2f4) semi-stub
fixme:advapi:GetCurrentHwProfileA (0x32f2f4) semi-stub
fixme:advapi:GetCurrentHwProfileA (0x32f2f4) semi-stub
fixme:advapi:GetCurrentHwProfileA (0x32f2f0) semi-stub
fixme:advapi:GetCurrentHwProfileA (0x32f2f0) semi-stub
fixme:advapi:GetCurrentHwProfileA (0x32f2f0) semi-stub
fixme:advapi:GetCurrentHwProfileA (0x32f46c) semi-stub
fixme:advapi:GetCurrentHwProfileA (0x32f498) semi-stub
fixme:advapi:GetCurrentHwProfileA (0x32f2f4) semi-stub
fixme:advapi:GetCurrentHwProfileA (0x32f2f4) semi-stub
fixme:advapi:GetCurrentHwProfileA (0x32f2f0) semi-stub
fixme:advapi:GetCurrentHwProfileA (0x32f2f0) semi-stub
fixme:advapi:GetCurrentHwProfileA (0x32f2f0) semi-stub
fixme:advapi:GetCurrentHwProfileA (0x32f2f0) semi-stub
fixme:advapi:GetCurrentHwProfileA (0x32f2f0) semi-stub
fixme:advapi:GetCurrentHwProfileA (0x32f2f0) semi-stub
fixme:advapi:GetCurrentHwProfileA (0x32f2f0) semi-stub
fixme:advapi:GetCurrentHwProfileA (0x32f2f0) semi-stub
fixme:advapi:GetCurrentHwProfileA (0x32f2f0) semi-stub
fixme:advapi:GetCurrentHwProfileA (0x32f46c) semi-stub
fixme:advapi:GetCurrentHwProfileA (0x32f498) semi-stub
fixme:advapi:GetCurrentHwProfileA (0x32f2f4) semi-stub
fixme:advapi:GetCurrentHwProfileA (0x32f2f4) semi-stub
fixme:advapi:GetCurrentHwProfileA (0x32f2f4) semi-stub
fixme:advapi:GetCurrentHwProfileA (0x32f2f4) semi-stub
fixme:advapi:GetCurrentHwProfileA (0x32f2f4) semi-stub
fixme:advapi:GetCurrentHwProfileA (0x32f2f0) semi-stub
fixme:advapi:GetCurrentHwProfileA (0x32f2f0) semi-stub
fixme:advapi:GetCurrentHwProfileA (0x32f2f0) semi-stub
fixme:advapi:GetCurrentHwProfileA (0x32f2f0) semi-stub
fixme:advapi:GetCurrentHwProfileA (0x32f2f0) semi-stub
fixme:advapi:GetCurrentHwProfileA (0x32f2f0) semi-stub
fixme:advapi:GetCurrentHwProfileA (0x32f2f0) semi-stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32d680,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
dummy
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
err:d3d_surface:IWineD3DSurfaceImpl_LoadLocation Reading back render target but SFLAG_INDRAWABLE not set
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:imm:ImmReleaseContext (0x1002a, 0x131628): stub
fixme:imm:NotifyIME IMC_SETCONVERSIONMODE
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface



```Anyone know how to fix this? Thanks in advance.

---

### Post by Bofur on 2009-03-10
Anyone?

---

