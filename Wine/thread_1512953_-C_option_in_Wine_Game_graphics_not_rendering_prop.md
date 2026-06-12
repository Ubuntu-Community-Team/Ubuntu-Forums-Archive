---
title: "-C option in Wine? Game graphics not rendering properly"
date: 2010-06-18
forum: Wine
---

### Post by Zireth ZH on 2010-06-18
Hey guys ive been trying to run Emperor Battle for dune with wine under ubuntu 10.04 with ati vga...

I got to install it .. run it .. it loads but in game the graphics wont render completely.. its all BLACK 
They mentioned something about -C option.. i dunno what the hell is that and ive been googling for it... no info regarding this at all...

take a look at this from winehq to see what i mean, this is from a guy who had the same issue has me.

Thanks in advance please help
**************************************************************************
I have Nvidia NV43 [GeForce 6600] card and the latest Nvidia drivers (173.14.12). I have also disabled composite extensions and updated Emperor to the latest 1.09 patch. The game runs, but when I load a map (with tutorial, for example or start a campaign) I have something like this: 
img262.imageshack.us/img262/2669/dune7jz7.png 
img262.imageshack.us/img262/4406/dune8af2.png 

There are my graphic settings in the game: 
img127.imageshack.us/img127/9725/dune3mx5.png 
img127.imageshack.us/img127/9725/dune3mx5.png 

When Emperor is running, I have in console a lot of messages like this: 

ixme:d3d_surface:surface_convert_format Cannot find a conversion function from format WINED3DFMT_R8G8B8 to WINED3DFMT_DXT1 
fixme:d3d_surface:surface_convert_format Cannot find a conversion function from format WINED3DFMT_R8G8B8 to WINED3DFMT_DXT1 
fixme:d3d_surface:surface_convert_format Cannot find a conversion function from format WINED3DFMT_R8G8B8 to WINED3DFMT_DXT1 
fixme:d3d_surface:surface_convert_format Cannot find a conversion function from format WINED3DFMT_X1R5G5B5 to WINED3DFMT_DXT1 
fixme:d3d_surface:surface_convert_format Cannot find a conversion function from format WINED3DFMT_R8G8B8 to WINED3DFMT_DXT1 
fixme:d3d_surface:surface_convert_format Cannot find a conversion function from format WINED3DFMT_R8G8B8 to WINED3DFMT_DXT1 
fixme:d3d_surface:surface_convert_format Cannot find a conversion function from format WINED3DFMT_A1R5G5B5 to WINED3DFMT_DXT1 
fixme:d3d_surface:surface_convert_format Cannot find a conversion function from format WINED3DFMT_X1R5G5B5 to WINED3DFMT_DXT1 

This problem persists in Wine 1.1.0 and 1.1.2. Any sugestion?

[post new] [reply to this] 


	


RE: missing textures on nvidia drivers by Jerry on Friday August 8th 2008, 5:44				RE: missing textures on nvidia drivers
by Jerry on Friday August 8th 2008, 5:44
Try to disable Multitexture. Most of the graphics artifacts were caused by this option.

[post new] [reply to this] 


	


RE: missing textures on nvidia drivers by Christian Horn on Sunday November 23rd 2008, 10:14				RE: missing textures on nvidia drivers
by Christian Horn on Sunday November 23rd 2008, 10:14
Same problem here. 

debian unstable amd64, nvidia proprietary drivers 177.82, Geforce 7600GS. 

Problem exists with selfcompiled wine 1.1.9 as well as 1.0.1-1 from debian unstable. Disabling graphic-options doesnt improve situation.

[post new] [reply to this] 


	


RE: missing textures on nvidia drivers by Morten Silcowitz on Sunday November 30th 2008, 16:16				RE: missing textures on nvidia drivers
by Morten Silcowitz on Sunday November 30th 2008, 16:16
Try using the -C option to Emperor.exe, like some of the other posts mention. It disables texture compression. That fixed the bug for me. (also nvidia card)

---

### Post by asdfoo on 2010-06-18
> **Zireth ZH said:**
> Hey guys ive been trying to run Emperor Battle for dune with wine under ubuntu 10.04 with ati vga...

I got to install it .. run it .. it loads but in game the graphics wont render completely.. its all BLACK 
They mentioned something about -C option.. i dunno what the hell is that and ive been googling for it... no info regarding this at all...

take a look at this from winehq to see what i mean, this is from a guy who had the same issue has me.

Thanks in advance please help


cd to the install directory
then type:  wine emperor.exe -C

assuming the main executable is called emperor.exe
Suggestions:  
* make sure you're using the latest version of wine, which is wine-1.2-rc4.
* make sure you have the latest video drivers for your card "ati vga" is very non-descript.  

For example, if it's a ati 4xxx series or 5xxxx series, then you should be using fglrx 10.6 I think

If it's a 3xxx series or lower, ATI has dropped support and you can use an older buggier version of fglrx or you can use the free/open source drivers.

---

### Post by Zireth ZH on 2010-06-18
Do you got an idea whats going on? am i doing this right?

[email]backstage@backstage-desktop:~/.wine[/email]/drive_c/Westwood/Emperor$ wine emperor.exe -C
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x12f868,0x12f7f0): stub
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  137 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  644
  Current serial number in output stream:  644
[email]backstage@backstage-desktop:~/.wine[/email]/drive_c/Westwood/Emperor$


The game wont start... not even doing wine emperor.exe

I can run it clicking the icon in the menus....

---

### Post by hikaricore on 2010-06-18
> **Zireth ZH said:**
> 
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  137 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)

Looks like something is terribly whacked out with your video drivers.
This is not normal output.

---

### Post by Zireth ZH on 2010-06-18
> **hikaricore said:**
> Looks like something is terribly whacked out with your video drivers.
This is not normal output.

Got an idea on how to fix this? ):P

---

### Post by asdfoo on 2010-06-18
> **Zireth ZH said:**
> Got an idea on how to fix this? ):P

Go back and read my original reply.

---

### Post by Zireth ZH on 2010-06-19
> **asdfoo said:**
> Go back and read my original reply.

Im using the latest drivers from ATI for my hd 4670 and the latest version of wine already...

---

### Post by asdfoo on 2010-06-20
what is "latest", are you using catalyst 10.6 and wine-1.2-rc4?

---

### Post by Zireth ZH on 2010-06-20
yes the latest everything ... 
idun see no difference between all the versions ive installed >_>

---

### Post by asdfoo on 2010-06-20
are you sure you have catalyst 10.6 it was only released 3 days ago.

anyway
can you attach all terminal output here

---

### Post by Zireth ZH on 2010-06-21
yeah ... i had those drivers.. i downloaded em from [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

but i just sold the card.. i bought an used 8400 gs, i kept the rest of the money for other stuff this is an old machine anyways...

lets see if it works now.. the drivers are amazing compared to the one for the hd 4670 .. the ati card was tons of times better than this 8400 gs, butthe performance was not even the 20 % of this one .... 

will see if the game works now ...

---

### Post by asdfoo on 2010-06-22
that's a contradiction

the drivers cannot be amazing and then have really bad performance

---

