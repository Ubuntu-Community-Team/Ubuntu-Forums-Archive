---
title: "Grand Theft Auto III Real Mod ~ Wine 1.1.23"
date: 2009-06-17
forum: Wine
---

### Post by Dark Aspect on 2009-06-17
Hello,

I have only ever played the unmodified version of [gta III]("http://en.wikipedia.org/wiki/Grand_Theft_Auto_III") and I was wanting to go back and relive the classic with various mods. For the most part, [gta III]("http://en.wikipedia.org/wiki/Grand_Theft_Auto_III") runs very well though wine but I am having an issue with [realmod]("http://grandtheftauto.filefront.com/file/Real_GTA_III;41903") rendering correctly. As the screen shot below shows, cars and some textures are missing or corrupt.

[IMG]http://img151.imageshack.us/img151/7677/gtarealmodwine.png[/IMG]
[SIZE="2"]*Note that the actually test was inside another xorg thus compiz was disabled[/SIZE]

I am hoping its fixable, I checked my wine output and I couldn't find any missing dll references:

```
fixme:win:EnumDisplayDevicesW ((null),0,0x32f6f0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f6d8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f390,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f7d4,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:quartz:MPEGSplitter_query_accept MPEG-1 system streams not yet supported.
fixme:quartz:MPEGSplitter_query_accept MPEG-1 system streams not yet supported.
fixme:d3d:CompareFunc Unrecognized WINED3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
LOAD frontend
LOAD sprite
fixme:win:EnumDisplayDevicesW ((null),0,0x32f768,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f768,0x00000000), stub!
2138:LODctm_rd4_ug txd has been set to generic
2472:LODnt7 txd has been set to generic
2474:LODnt6 txd has been set to generic
PreparePathData
Single car node: 311.002502 -938.778015 22.178200 (1817)
GraphType:0. FloodFill groups:4
GraphType:1. FloodFill groups:87
Done with PreparePathData
Done Initing waterlevels
Start loading taxi
Finish loading taxi
Start loading police
Finish loading police
Start loading train
Finish loading train
Start loading airtrain
Finish loading airtrain
Start loading deaddodo
Finish loading deaddodo
&&&&&&&&&&&&&Creating player: 0
REMOVE frontend
REMOVE menu textures
pools have beem cleared 
fixme:win:EnumDisplayDevicesW ((null),0,0x32f750,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f750,0x00000000), stub!
Start loading train
Finish loading train
Start loading airtrain
Finish loading airtrain
Start loading deaddodo
Finish loading deaddodo
LOAD frontend
LOAD sprite
REMOVE frontend
REMOVE menu textures
Shutdown pool started
Shutdown pool done
```

Any ideas? I believe I have set offscreenrendering = fbo, could registry hacks help this problem?

---

