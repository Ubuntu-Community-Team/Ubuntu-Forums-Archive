---
title: "Running Touhou Hisoutensoku"
date: 2010-11-08
forum: Wine
---

### Post by Insertion_Epsilon on 2010-11-08
Just in case you're wondering, Touhou 12.3 UNL/Hisoutensoku is a doujin game made by Tasogare Frontier in collaboration with Team Shanghai Alice (ZUN). But that's not my point.

I tried to run Touhou 12.3 UNL/Hisoutensoku with the command:
LANG=ja-JP.UTF-8 wine th123.exe

...and what I get is this:
```

fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x32f354,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x170578,0x171478): stub
fixme:imm:NotifyIME IMC_SETCANDIDATEPOS
fixme:d3dx:D3DXCreateTexture (0x12c618, 640, 78, 1, 0, 15, 1, 0xbcc958): semi-stub
fixme:d3dx:D3DXCreateTexture (0x12c618, 128, 128, 1, 0, 15, 1, 0xbcc95c): semi-stub
fixme:d3dx:D3DXCreateTexture (0x12c618, 64, 65, 1, 0, 15, 1, 0xbcc960): semi-stub
fixme:d3dx:D3DXCreateTexture (0x12c618, 32, 32, 1, 0, 15, 1, 0xbcc964): semi-stub
fixme:d3dx:D3DXCreateTexture (0x12c618, 640, 76, 1, 0, 15, 1, 0xbdc590): semi-stub
fixme:d3dx:D3DXCreateTexture (0x12c618, 160, 160, 1, 0, 15, 1, 0xbdc594): semi-stub
fixme:d3dx:D3DXCreateTexture (0x12c618, 80, 80, 1, 0, 15, 1, 0xbdc598): semi-stub
fixme:d3dx:D3DXCreateTexture (0x12c618, 160, 160, 1, 0, 15, 1, 0xbdc59c): semi-stub
fixme:d3dx:D3DXCreateTexture (0x12c618, 640, 96, 1, 0, 15, 1, 0xbdc610): semi-stub
fixme:d3dx:D3DXCreateTexture (0x12c618, 640, 48, 1, 0, 15, 1, 0xbdc614): semi-stub
fixme:d3dx:D3DXCreateTexture (0x12c618, 296, 34, 1, 0, 15, 1, 0xbdc618): semi-stub
fixme:d3dx:D3DXCreateTexture (0x12c618, 198, 24, 1, 0, 15, 1, 0xbdc61c): semi-stub
fixme:d3dx:D3DXCreateTexture (0x12c618, 128, 128, 1, 0, 15, 1, 0xbdc5a8): semi-stub
fixme:d3dx:D3DXCreateTexture (0x12c618, 64, 65, 1, 0, 15, 1, 0xbdc5ac): semi-stub
fixme:d3dx:D3DXCreateTexture (0x12c618, 32, 32, 1, 0, 15, 1, 0xbdc5b0): semi-stub
fixme:d3dx:D3DXCreateTexture (0x12c618, 640, 68, 1, 0, 15, 1, 0xbdc5b4): semi-stub
fixme:d3dx:D3DXCreateTexture (0x12c618, 312, 312, 1, 0, 15, 1, 0xbddd20): semi-stub
fixme:d3dx:D3DXCreateTexture (0x12c618, 160, 160, 1, 0, 15, 1, 0xbddd24): semi-stub
fixme:d3dx:D3DXCreateTexture (0x12c618, 80, 80, 1, 0, 15, 1, 0xbddd28): semi-stub
fixme:d3dx:D3DXCreateTexture (0x12c618, 400, 400, 1, 0, 15, 1, 0xbddd2c): semi-stub
fixme:d3dx:D3DXCreateTexture (0x12c618, 160, 160, 1, 0, 15, 1, 0xbdc5c0): semi-stub
fixme:d3dx:D3DXCreateTexture (0x12c618, 640, 64, 1, 0, 15, 1, 0xbdc5c4): semi-stub
fixme:d3dx:D3DXCreateTexture (0x12c618, 216, 32, 1, 0, 15, 1, 0xbdc5c8): semi-stub
fixme:d3dx:D3DXCreateTexture (0x12c618, 216, 32, 1, 0, 15, 1, 0xbdc5cc): semi-stub
fixme:d3dx:D3DXCreateTexture (0x12c618, 330, 74, 1, 0, 15, 1, 0xbddcf8): semi-stub
fixme:d3dx:D3DXCreateTexture (0x12c618, 64, 24, 1, 0, 15, 1, 0xbddcfc): semi-stub
fixme:d3dx:D3DXCreateTexture (0x12c618, 64, 24, 1, 0, 15, 1, 0xbddd00): semi-stub
fixme:d3dx:D3DXCreateTexture (0x12c618, 64, 24, 1, 0, 15, 1, 0xbddd04): semi-stub
fixme:d3dx:D3DXCreateTexture (0x12c618, 64, 24, 1, 0, 15, 1, 0xbcc930): semi-stub
fixme:d3dx:D3DXCreateTexture (0x12c618, 216, 32, 1, 0, 15, 1, 0xbcc934): semi-stub
fixme:d3dx:D3DXCreateTexture (0x12c618, 480, 480, 1, 0, 15, 1, 0xbcc938): semi-stub
fixme:d3dx:D3DXCreateTexture (0x12c618, 480, 480, 1, 0, 15, 1, 0xbcc93c): semi-stub
fixme:d3dx:D3DXCreateTexture (0x12c618, 512, 16, 1, 0, 15, 1, 0xbdf448): semi-stub
fixme:d3dx:D3DXCreateTexture (0x12c618, 20, 20, 1, 0, 15, 1, 0xbdf44c): semi-stub
fixme:d3dx:D3DXCreateTexture (0x12c618, 20, 20, 1, 0, 15, 1, 0xbdf450): semi-stub
fixme:d3dx:D3DXCreateTexture (0x12c618, 248, 336, 1, 0, 15, 1, 0xbdf454): semi-stub
fixme:d3dx:D3DXCreateEffectEx (0x12c618, 0x84e8f8, 6944, (nil), (nil), (nil), 0, (nil), 0x887ae0, (nil)): semi-stub
fixme:d3dx:D3DXCreateEffectEx (0x12c618, 0x850418, 1668, (nil), (nil), (nil), 0, (nil), 0x887ae8, (nil)): semi-stub
fixme:d3dx:D3DXCreateTexture (0x12c618, 256, 64, 1, 0, 15, 1, 0xbe4240): semi-stub
wine: Unhandled division by zero at address 0x41190a (thread 0009), starting debugger...

```

My question is whether there's something wrong with Wine's configuration.

---

### Post by howefield on 2010-11-08
Moved to the Wine forum.

---

