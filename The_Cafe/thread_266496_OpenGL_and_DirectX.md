---
title: "OpenGL and DirectX"
date: 2006-09-27
forum: The Cafe
---

### Post by MaximB on 2006-09-27
I have a few questions about all this OpenGL  and DirectX thing.
1.which are better ? (not easier to code but better performance).
2. why games that are made using directx won't work on linux ?
3. is there a real chance that linux will support directx ?

---

### Post by NoTiG on 2006-09-27
Heres a snippet about working with directx in linux through wine from the recent summit:
> 
But what would a Direct3D presentation be without some eye candy? Stefan showed off screenshots of some games. There was also a small contingent of DirectX folks in attendance with some really high-powered laptops that could show off the games. It's quite impressive to see the latest and greatest games running on Linux. Jon Parshall extensively, um, "tested" World of Warcraft throughout the conference (did you finally make it to level 48, Jon?) Tom Wickline had 3DMark2000, 3DMark2001SE and 3DMark2003 running all of there test. There is still some artifacts in the rendering of a couple of the test, but the DirectX guys knew what was to blame for it. Stefan showed off the Microsoft DirectX logo "proving" DirectX is being properly detected.

Much of the current work surrounds context and state management. It's known that better state management would improve performance and Wine is taking the dumb approach right now. Other things on the to-do list include better offscreen rendering with FBOs and pbuffers and multithreading support. In the OpenGL world, it seems the decision has been made to move Direct3D to the WGL framework. This will also allow Wine's Direct3D code to run on Windows as well. Talking with Stefan later, it doesn't sound like there will be much of a performance penalty by going through that layer since the OpenGL calls will mostly get passed straight through.

While Direct3D looks pretty good, there are issues with other areas of DirectX. The DirectInput code still suffers from things like the mouse getting stuck. DirectSound continues to be a pain in the *** and there's a need for ALSA improvements. DirectPlay has an undocumented network protocol that needs to be implemented for older games, though Stefan noted that native works fine. Licensing issues prevent the use of native, so unfortunately that's not an option. Finally, OpenGL really needs to be abstracted a bit more, with part of the reason being better MacOS support.

**Direct3D10, which will ship with Windows Vista in a few months, doesn't seem to be a large cause for concern. At first glance it appears to be more of an evolutionary change rather than revolutionary. New shader support will be needed, but extending ours once OpenGL supports it should be pretty easy**. Stefan mentioned Microsoft is currently offering a lot of incentives for Windows developers who develop D3D10-only games since they'll only be usable on Vista - there's no plan to backport D3D10 to XP. Dan Kegel asked if that means we should port Wine's forthcoming D3D10 implementation to Windows, which would be relatively easy when we switch to WGL.

To wrap things up, Stefan presented some of the obstacles they've run into. Most games ship with a set of Microsoft helper libraries named D3DX_##.dll. There are approximately 30 different versions of those right now. They contain higher-level functions, such as a shader compiler. There's no problem using the native ones, but they must be installed by the game. Some games don't ship with them and that's a problem. Another big issue is copy protection; but as we noted above there's work being done on that area.

Phil Costin brought up another topic that needs to be addressed: figuring out how much video memory cards have. Currently Wine just reports 64MB available, however games really need to know the true amount so they know how many textures can be uploaded. One idea was to just stuff textures into memory until no more fit, however there's never a point with OpenGL where no more fit. If video memory runs out, it simply spills over to system memory and that just spills over to virtual memory. 

[http://www.winehq.com/?issue=320](http://www.winehq.com/?issue=320)

Basically John Carmac (the developer of the doom series) use to claim that OpenGL was better.... but that changed after like directx8 ... when it caught up or perhaps even surpassed openGL. I know that developers like how everything is integrated in directx... like directinput... directdraw... and then sound... all in one place. For linux you need openGL + SDL . 

other interesting articles:

[http://www.gamedev.net/reference/articles/article1775.asp](http://www.gamedev.net/reference/articles/article1775.asp)
[http://en.wikipedia.org/wiki/Comparison_of_Direct3D_and_OpenGL](http://en.wikipedia.org/wiki/Comparison_of_Direct3D_and_OpenGL)

---

### Post by bruce89 on 2006-09-27
> **MAXDDARK said:**
> I have a few questions about all this OpenGL  and DirectX thing.
1.which are better ? (not easier to code but better performance).
If you believe MS, DirectX, otherwise OpenGL.
> **MAXDDARK said:**
> 2. why games that are made using directx won't work on linux ?
DirectX is a Windows-only thing, as it is proprietary.
> **MAXDDARK said:**
> 3. is there a real chance that linux will support directx ?
No, but a fork of WINE (Cedega) does, but it costs money.

---

### Post by skymt on 2006-09-27
> **bruce89 said:**
> No, but a fork of WINE (Cedega) does, but it costs money.

Actually, recent versions of Wine proper have some DirectX support, including Direct3D.

---

### Post by bruce89 on 2006-09-27
> **skymt said:**
> Actually, recent versions of Wine proper have some DirectX support, including Direct3D.

Indeed it does, I've been out of contact with WINE for some time though, as I use the AMD64 version.  It's a good thing that the real WINE has this capability.

---

### Post by blueturtl on 2006-09-27
DirectX is a complete set of layers that are directed for multimedia use. It has frameworks for video, audio as well as network and game controllers and such. OpenGL provides no other functionality than graphics. OpenGL is simply Open Graphics Layer. OpenGL works on several operating systems whereas DirectX is Windows-only. Once you understand the difference between the two you understand that no direct comparison can be made. DirectX exists for the sole purpose of making games easier to program for Windows. It provides a dumbed down functionality to the programmers and then directs their requests to spesific hardware. The good thing is they don't need to worry about things like the compatibility of each and every sound- and videocard out there. The problem with this approach is the same as with any other abstraction layer, it slows things down.

Back some time ago when I still used Windows I remember always preferring OpenGL to Direct3D. If a game had the selection of two renderers I always took OpenGL because it gave me better framerates. Some games of course don't have the option of both, and for some hardware and software combination the results might even reverse. I don't know enough about either to make claims of superiority, but John Carmack is nearly a god when it comes to graphics so if he prefers OpenGL that should say something. Doom3 which came out quite recently and was the top-technological achievement in graphics thus far (subjective reviews aside) was done in OpenGL. That's why it also runs on Linux with very little modification.

I wouldn't worry about Direct3D until there's support for nothing but (and we're caught in yet another MS-lock-in).

---

