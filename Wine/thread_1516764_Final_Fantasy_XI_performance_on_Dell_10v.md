---
title: "Final Fantasy XI performance on Dell 10v"
date: 2010-06-24
forum: Wine
---

### Post by Chrisn02 on 2010-06-24
Hi everyone,

I had one of my crazy ideas.  Why not try running Final Fantasy XI on my Dell 10v.  After various successes & failures over the last year on and off I finally get it running without crashing on me and with text I could read.

Specifications
Intel 945 GSE UMA graphics
1.6-GHz Intel Atom N270 (Think this is right)
1GB ram
Ubuntu 10.04

Installation, in case anyone needs it.
Originally installed to my pc using a guide on the allakhazam forums in PlayOnLinux from the CDs.  I'll try and post the link if I can find it.
Normal boring install except I had to run "wine eject" when changing disks.
Then copied my old install from windows for all the updates.
This was all then copied to the netbook.

Block or bar code text.
Cased by a missing S3 Texture Compression (S3TC) library (thanks to Lobivopis on the Allakhazam forums for giving me the clue I needed to fix this)  
Required for some systems like the Dell10v

To fix you need to install.
Warning: These may be covered by patents and other IP issue.
[http://debian-multimedia.org/dists/unstable/main/binary-i386/package/libtxc-dxtn0.php](http://debian-multimedia.org/dists/unstable/main/binary-i386/package/libtxc-dxtn0.php)
or for 64bit 
[http://debian-multimedia.org/dists/unstable/main/binary-amd64/package/libtxc-dxtn0.php](http://debian-multimedia.org/dists/unstable/main/binary-amd64/package/libtxc-dxtn0.php)

My current wine settings
Basic settings.  Only things changed are
Disabling of window manager decorations and controls and enabling virtual desktop at 800x600.  Windows version is set to 7
Registry
HKEY_CURRENT_USER\Software\Wine\Direct3D
DirectDrawRenderer opengl
OffscreenRenderingMode fbo    (backbuffer causes a black border at the bottom of the screen if background setting in ffxi is bigger than overlay)
PixelShaderMode disabled
RenderTargetLockMode textex 

No DLL overrides

Playonline view config
Only sound is enabled


FFXI config tool.
General tab
Disabled mip mapping and start in windowed mode.
Gamma base 0.0

Screen size tab
640x640 overlay
512x512 background

Textures tab
Both uncompressed

Effects tab
Bump mapping and environmental Animation is off

Sound tab
Sound is enabled with 12 SoundEffectNum

Misc tab
Opening movie enabled
All others disabled.

View distance and number of models displayed is at minimum.
 
Only other thing I've done is removed pulseaudio and installed the  xorg-edgers ppa
[https://edge.launchpad.net/~xorg-edgers/+archive/ppa](https://edge.launchpad.net/~xorg-edgers/+archive/ppa)

Now to the probelm.
The only problem left if the performance.
Is there any way to speed things up a bit?  Some wine,driver,ubuntu,ffxi setting I've missed?
Not holding out much hope due to the limited hardware but I've come this far it would be a shame to not to make this somewhat usable.

Any ideas?

Thanks in advance.

---

### Post by asdfoo on 2010-06-24
> **Chrisn02 said:**
> 
Intel 945 GSE UMA graphics
1.6-GHz Intel Atom N270 (Think this is right)
1GB ram


The video card is going to be letting you down the most, while great work as gone into the drivers by free software developers, it's left behind by proprietary drivers offered by nvidia and ati for their cards which have much more featureful and performant implementations of OpenGL.

Someone else might be able to offer advice on the state of affairs for Intel 945 driver support, gallium et al?  But that's not really related to Wine.

---

### Post by Chrisn02 on 2010-07-07
Thanks for your reply.  I expected as much. :D

To be honest I wasn't sure if this belonged in the Wine or Multimedia & Video forum.

---

