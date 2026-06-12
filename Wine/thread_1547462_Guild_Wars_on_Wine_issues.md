---
title: "Guild Wars on Wine issues"
date: 2010-08-06
forum: Wine
---

### Post by devakikao on 2010-08-06
First of all, I am really new to Ubuntu, up until the last three days, I have never even used any type of Linux, so I'm pretty newbie right now, and everything I have done so far I found by searching the internet.

I am not sure how to check what version of wine is installed, but when I installed it, I found a website that said to do this:
```
ppa:ubuntu-wine/ppa
```in System>Administration>Software Sources, then 
```
sudo apt-get update
``` and ```
sudo apt-get install wine 
```in a terminal window.( But after looking at the sticky on here, it said  to never run wine using sudo, so could this be related to my problem?)

After installing Guild Wars with Wine, it was really glitchy, so in "winecfg" I added D: /Setup.exe under the "Drives" tab, and  am using it with "Windows XP". 

After doing this, the user interface began showing up in the game, but everything else was a black screen. So then I added the following strings under HKEY_CURRENT_USER>Software>Wine>Direct3D in "wine regedit":
DirectDrawRenderer = opengl
OffscreenRenderingMode = backbuffer
opengl = enabled
PixelShaderMode = enabled
RenderTargetLockMode = auto
UseGLSL = disabled
VideoMemorySize = 256       

Now the game seems completely normal, except it is running very slowly, so slow that it won't even load after selecting a character. 

When I run
```
wine "C:\Program Files\Guild Wars\Gw.exe"
```from the terminal window, I get this in it:
```
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x32e94c,0x00000000), stub!
fixme:imm:ImmDisableTextFrameService Stub
err:alsa:wine_snd_pcm_recover underrun occurred

```As for the hardware/specs of the laptop, have no idea how to find them using Ubuntu. All I know is the laptop is an Acer Aspire 3610, and I'm pretty sure it's a 32-bit system.

So if anybody could help me, that would be great. I hope I included everything the sticky said to, but if you need more information, let me know, thanks.

---

### Post by asdfoo on 2010-08-06
> **devakikao said:**
> ```
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver

```

If you're using a 3D application, Wine relies on the OpenGL support provided by your video drivers.   The message above indicates you may have an integrated intel video card, which are low end and do not offer very good performance or featureset on GNU/Linux.

Since you have a laptop there is not much you can do, except perhaps try ubuntu edgers, which is a way of using more up to date software packages that relate to video performance, but even that may not be enough.   In general, nvidia offers the best support for 3D graphics in terms of stability and features, followed by ati with much less stability and intel is in last place.

---

### Post by devakikao on 2010-08-06
Okay, I was afraid it might be related to something like that.... Can these software packages be found on the internet? And if so, should I look under "nvidia" then?

Sorry all these new things(with the new OS and whatnot) at once make it difficult to wrap my head around them all at once.

---

### Post by asdfoo on 2010-08-06
> **devakikao said:**
> Okay, I was afraid it might be related to something like that.... Can these software packages be found on the internet? And if so, should I look under "nvidia" then?

Sorry all these new things(with the new OS and whatnot) at once make it difficult to wrap my head around them all at once.

nvidia is a hardware manufacturer, they make video cards which physically exist.  since you have a laptop, you cannot do anything except perhaps research your next buy.

The software packages I was suggesting is referred to as ubuntu edgers, it's more advanced since it's intended for people wishing to try the most recent developments.  If you want more information I suggest you post in a different subforum, because this isn't wine related.

---

