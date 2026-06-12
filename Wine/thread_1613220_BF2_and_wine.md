---
title: "BF2 and wine"
date: 2010-11-04
forum: Wine
---

### Post by masterskop on 2010-11-04
Hi,

Has anyone got BF2 to run really well with the graphics maxed out and not having any artifacts?  I know that BF2 runs D3D and not opengl.  Are the artifacts caused by the driver,wine, or both? 

Also, has anyone tried running the 32bit wine on a 64bit system and got this game to work well?

thanks,

I'm running
Ubuntu 10.10 
wine 1.2.1
Geforce 260
driver 260.19.17

---

### Post by lkjoel on 2010-11-05
> **masterskop said:**
> Hi,

Has anyone got BF2 to run really well with the graphics maxed out and not having any artifacts?  I know that BF2 runs D3D and not opengl.  Are the artifacts caused by the driver,wine, or both? 

Also, has anyone tried running the 32bit wine on a 64bit system and got this game to work well?

thanks,

I'm running
Ubuntu 10.10 
wine 1.2.1
Geforce 260
driver 260.19.17
Have you tried PlayOnLinux?
```

sudo wget http://deb.playonlinux.com/playonlinux_karmic.list -O /etc/apt/sources.list.d/playonlinux.list
sudo apt-get update
sudo apt-get install playonlinux

```
And try using the latest development version of WINE.
```
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine1.3
```

---

### Post by masterskop on 2010-11-06
[I]lkjoel,

Have you tried PlayOnLinux?
Code:

sudo wget [http://deb.playonlinux.com/playonlinux_karmic.list](http://deb.playonlinux.com/playonlinux_karmic.list) -O /etc/apt/sources.list.d/playonlinux.list
sudo apt-get update
sudo apt-get install playonlinux[/I]

No, I haven't use PlayOnLinux yet.  If I did, is there a way to play BF2 in POL from the .wine directory?  I would hate to reinstall BF2.  Is the D3D rendering any better in POL then wine?




[I]And try using the latest development version of WINE.
Code:

sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine1.3[/I]


I upgraded to wine 1.3.6.  I can finally see the "2" flip from left to right like in windows! :)   Graphics look great except for the artifacts. :(  I have tried everything in changing out the video selections in BF2 as well as changing out the Direct3D settings in the wine regedit file.

Any suggestions?

Here is the image of BF2 w/ max settings.  Notice the 'black' blotches.

---

### Post by Soulcage on 2010-11-06
Try wine 1.3.6 maybe?

---

### Post by ronnielsen1 on 2010-11-06
Depending on the version of BF2 you have here's the links to winehq that will help you get it running in wine 

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3438](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3438)

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3438](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3438)

---

### Post by masterskop on 2010-11-06
Soulcage and ronnielsen1,

Thx for the replies!  Soulcage, in my post above, I already installed wine 1.3.6.  Ronnielsen1, BF2 is fully patched/updated to the latest and greatest!  I've used the methods stated at winehq.  But, the issue is with the 'artifacts'.  If it's not wine, could this be an nvidia driver issue?  

Does anyone have BF2 running w/ no artifacts and has an nvidia card?  If so, how did you do it?

thx....

---

### Post by lkjoel on 2010-11-06
Did you install DirectX?

---

### Post by bobwyajnr on 2010-11-07
> **masterskop said:**
> Hi,

Has anyone got BF2 to run really well with the graphics maxed out and not having any artifacts?  I know that BF2 runs D3D and not opengl.  Are the artifacts caused by the driver,wine, or both? 

Also, has anyone tried running the 32bit wine on a 64bit system and got this game to work well?

thanks,

I'm running
Ubuntu 10.10 
wine 1.2.1
Geforce 260
driver 260.19.17

Hi

I can confirm the problems you are having.
I was running (till 2 weeks ago):
Ubuntu 10.04 (now on Kubuntu 10.04)
WINE 1.3.6
Nvidia 8800 GTX 768Mb
driver 260.19.17

I submitted some screenshots of those graphical glitches you are experiencing as to an existing [AppDB bug]("http://bugs2.winehq.org/attachment.cgi?id=31380"). (BTW ignore the black bars - they were introduced due to me trying to use the PRINT-SCREEEN button to take my screenshots :P )

Allegedly (in that bug report) it helps a bit (reducing the glitches) if you bump up the anti-aliasing, etc. in the Nvidia control panel (overriding application preferences)... Personally I didn't see much difference. But you do have a newer generation card then me... so perhaps worth a try!

One wierd problem I had with my install was that I **could** play Multiplayer but my Singleplayer server would crash as soon as I started to try and play a map! I never resolved that... :-({|=

I had trouble getting any sensible console output when running Battlefield 2 through Steam. I might have a go at running my retail copy directly. Basically you need to find the relevant **D3D:fixme** in amongst all the spew!

What might interest you to know is that when I first installed Steam on Windows 7 I tried running Battlefield 2 (on the same machine/ GPU). I was using a slightly dated Nvidia driver and I had experienced exactly the same effect - a patchwork of shifting mipmap surfaces flickering to black as I moved. Switching to a newer Nvidia Windows driver sorted out the problem at the time...

The main problem with Battlefield 2 however is that it is never going to work properly through WINE due to Punkbuster. I understand this code has a lot of Windows kernel hooks that make it very hard to circumvent/fully support. DICE weren't/aren't prepared to sort out the problem (I believe there was some pressure on them prior to the delayed 1.5 patch)...

Bob

NB I recently reinstalled my OS (moving over to the darkside - KDE - so I am still at the stage of trying to get the stupid opening movies not to crap out (because I don't have display mode 800x600@85) ](*,)

---

### Post by masterskop on 2010-11-07
> Hi

I can confirm the problems you are having.
I was running (till 2 weeks ago):
Ubuntu 10.04 (now on Kubuntu 10.04)
WINE 1.3.6
Nvidia 8800 GTX 768Mb
driver 260.19.17

I submitted some screenshots of those graphical glitches you are experiencing as to an existing AppDB bug. (BTW ignore the black bars - they were introduced due to me trying to use the PRINT-SCREEEN button to take my screenshots )

Allegedly (in that bug report) it helps a bit (reducing the glitches) if you bump up the anti-aliasing, etc. in the Nvidia control panel (overriding application preferences)... Personally I didn't see much difference. But you do have a newer generation card then me... so perhaps worth a try!

One wierd problem I had with my install was that I could play Multiplayer but my Singleplayer server would crash as soon as I started to try and play a map! I never resolved that...

I had trouble getting any sensible console output when running Battlefield 2 through Steam. I might have a go at running my retail copy directly. Basically you need to find the relevant D3D:fixme in amongst all the spew!

What might interest you to know is that when I first installed Steam on Windows 7 I tried running Battlefield 2 (on the same machine/ GPU). I was using a slightly dated Nvidia driver and I had experienced exactly the same effect - a patchwork of shifting mipmap surfaces flickering to black as I moved. Switching to a newer Nvidia Windows driver sorted out the problem at the time...

The main problem with Battlefield 2 however is that it is never going to work properly through WINE due to Punkbuster. I understand this code has a lot of Windows kernel hooks that make it very hard to circumvent/fully support. DICE weren't/aren't prepared to sort out the problem (I believe there was some pressure on them prior to the delayed 1.5 patch)...

Bob

NB I recently reinstalled my OS (moving over to the darkside - KDE - so I am still at the stage of trying to get the stupid opening movies not to crap out (because I don't have display mode 800x600@85) 

Bob,

Thanks for the reply!  Seems after reading your post the latest linux driver can't do proper d3d rendering.  I wonder if there is a glide driver that would work?  Just a thought.  So, for now we are stuck...that's too bad.  I was able to get the shadowing to work in the game!  Everything worked but those mipmaps.  I have tried the 4xAA.  I can go higher, but the game is limited to 4xAA.  I'll do an override.  I don't see it working either.  I'll post back soon.  Any thing else in Direct3D that can be done?  I have followed the suggestions at winehq.

---

### Post by bobwyajnr on 2010-11-07
> **masterskop said:**
> Bob,

Thanks for the reply!  Seems after reading your post the latest linux driver can't do proper d3d rendering.  I wonder if there is a glide driver that would work?  Just a thought.  So, for now we are stuck...that's too bad.  I was able to get the shadowing to work in the game!  Everything worked but those mipmaps.  I have tried the 4xAA.  I can go higher, but the game is limited to 4xAA.  I'll do an override.  I don't see it working either.  I'll post back soon.  Any thing else in Direct3D that can be done?  I have followed the suggestions at winehq.

Hi

I haven't necessarily ruled out a problem in the Wine D3D->OpenGL translation. The Nvidia Linux blob drivers are not comparable to the ATI blob drivers after all (i.e. much less buggy). I have both Bioshock and World in Conflict running, in DirectX 9.0c mode via WINE 1.3.6, without **any** visible glitches what-so-ever. Battlefield 2 is an older game and uses a subset of the DirectX 9.0c API.

Like I said in my post. If and when I resolve the (AARGegegegg!!) problem with the intro movie resolution switch at the game start... Then I will try and capture the D3D calls that correspond to the visible glitching we are seeing.

What fixes did you use to get around the startup problem (I can't remember what I did before ](*,))?? Are you running BF2 fullscreen (again I was previously)? Editing the default profile doesn't do anything useful for me... Are you using any .dll overrides with the latest WINE version?

Bob

---

### Post by masterskop on 2010-11-07
Bob,

I will post more today.  I haven't used any overrides yet.  I went to the 'Libraries' tab in 1.3.6 and everything was blank.  The intro movie is smooth as glass.  Everything worked but the mipmaps problems persists.  I'll start using the library overrides one at a time next to see if there are any improvements.

---

### Post by bobwyajnr on 2010-11-07
> **masterskop said:**
> Bob,

I will post more today.  I haven't used any overrides yet.  I went to the 'Libraries' tab in 1.3.6 and everything was blank.  The intro movie is smooth as glass.  Everything worked but the mipmaps problems persists.  I'll start using the library overrides one at a time next to see if there are any improvements.

Ah OK

Nop .dll overrides won't help you then. Like I said the next step is staring at console output to find "fix-me"'s related to Direct3D .dll's!! You can redirect all the console output into a file...
```

wine BF2.exe &> ~/winelog.txt

```
Run that command in you Battlefield 2 folder in a BASH terminal window. It will put all the Wine console output in a file called **winelog.txt** in your home folder. Post the file as an attachment if you have any joy collecting the data!

You tried 4xAA in the Nvidia control panel -right?? As a global override. Some guy on AppDB claimed it solved the visual glitches. Mind you he didn't actually say what visual glitches... :)

Bob

---

### Post by masterskop on 2010-11-07
Bob,

I took the pic bellow with the following settings:

sync to vblank
allow flipping
texture clamping
High Quality

4x (4xMS) on AA
4x on AF

Texture sharpening not checked

In Wine I did the following:

windows ver: windows xp
Libraries: 
d3d10 (builtin, native)
d3d8 (builtin, native)
d3d9 (builtin, native)
d3dim (builtin, native)
d3drm (builtin, native)

Graphics:

Allow the window manager to decorate the windows
allow the window manager to control the windows
emulate a virtual desktop
vertex shader support: hardware
allow pixel shader

I haven't used the log file yet.

---

### Post by masterskop on 2010-11-07
Bob,

As you can see I now added the texture sharpening.  I don't see much of a difference.

---

### Post by masterskop on 2010-11-07
Bob,

As you can see in the following pictures that the color looks good as well as the images.  I'll keep experimenting.  Btw....I have bf2 maxed out in the settings.  [ATTACH]174912[/ATTACH]

[ATTACH]174913[/ATTACH]

[ATTACH]174914[/ATTACH]

[ATTACH]174915[/ATTACH]

[ATTACH]174916[/ATTACH]

---

### Post by masterskop on 2010-11-07
Bob,

Here are a few pics of my settings:

---

### Post by lkjoel on 2010-11-07
It looks nice.
What is the problem?

---

### Post by masterskop on 2010-11-07
lkjoel,

The mipmapping on Desert Maps.  Strike at Karkand is terrible.

---

### Post by lkjoel on 2010-11-07
> **masterskop said:**
> lkjoel,

The mipmapping on Desert Maps.  Strike at Karkand is terrible.
Do you mean the ground?

---

### Post by masterskop on 2010-11-07
lkjoel,

Here is a pick of downtown Karkand.  As you can tell even w/ these settings the map doesn't render well.

---

### Post by bobwyajnr on 2010-11-07
> **masterskop said:**
> 
Here is a pick of downtown Karkand.  As you can tell even w/ these settings the map doesn't render well.

Hey don't be so fussy. I'm looking at a black screen... :-({|=

Bob

---

### Post by lkjoel on 2010-11-07
> **masterskop said:**
> lkjoel,

Here is a pick of downtown Karkand.  As you can tell even w/ these settings the map doesn't render well.
I get it.
Did you install DirectX?
If you did, that might be the reason.

---

### Post by masterskop on 2010-11-08
lkjoel,

Yes, I believe directx is installed.  I did figure out that I needed to unzip the shaders' file and put those files into the 'empty' shaders folder.  But, the problem remained.  I'll have to check that out about directx.

Thank you for the info.

---

### Post by lkjoel on 2010-11-08
> **masterskop said:**
> lkjoel,

Yes, I believe directx is installed.  I did figure out that I needed to unzip the shaders' file and put those files into the 'empty' shaders folder.  But, the problem remained.  I'll have to check that out about directx.

Thank you for the info.

[http://ubuntuforums.org/showthread.php?t=885111]("http://ubuntuforums.org/showthread.php?t=885111")

---

### Post by masterskop on 2010-11-08
lkjoel,

What are the chances of uninstall directx and screwing something up?  And, by uninstalling directx, will fix the video problem with desert maps in bf2?

---

### Post by bobwyajnr on 2010-11-08
@**masterskop**

Sorry to butt in on your thread again. I confirmed that my problem with BF2 and BF2142 is to with display modes. In that my X-Server doesn't have a dynamic option which these games try to switch to at launch of 800x600@85Hz. I can't seem to add this manually using **xrandr**. The display mode is present in my Nvidia control panel listing and is supported by my TFT display (hooked up via DVI).

Anyway I can run both games in a 800x600 window (oh great!! not) and they work OK.

It would help me (and perhaps others) to get a copy of your **xorg.conf** file and the output from the command **xrandr**.

Sorry to trouble you ... but I am starting to feel quite troubled myself... :-?:-({|=:sad::icon_frown::frown:[-(](*,):confused:

Bob

---

### Post by masterskop on 2010-11-08
Bob,

Here's a copy of my xorg file:


Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
	Option  "Coolbits"     "1"
EndSection

Section "InputDevice"
Driver "mouse"
Identifier "Counfigured Mouse"
Option "Buttons" "7"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Name" "Logitech USB-PS/2 Optical Mouse"
Option "Protocol" "explorerps/2"
Option "Vendor" "Sysp"
Option "ZAxisMapping" "4 5"
Option "ButtonMapping" "1 2 3 6 7"
EndSection


Here's a copy of my xrandr file

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1680 x 1050, maximum 1680 x 1050
default connected 1680x1050+0+0 0mm x 0mm
   1680x1050      50.0*    51.0  
   1600x1000      52.0  
   1440x900       53.0  
   1400x1050      54.0     55.0     56.0  
   1360x768       57.0     58.0  
   1280x1024      59.0     60.0  
   1280x960       61.0  
   1152x864       62.0     63.0     64.0     65.0  
   1152x720       66.0  
   1024x768       67.0     68.0     69.0  
   960x600        70.0  
   960x540        71.0  
   840x525        72.0     73.0     74.0     75.0  
   832x624        76.0  
   800x600        77.0     78.0     79.0     80.0  
   720x450        81.0  
   700x525        82.0     83.0  
   680x384        84.0     85.0  
   640x480        86.0     87.0     88.0     89.0  
   512x384        90.0     91.0  
   400x300        92.0  
   320x240        93.0     94.0  


I'm running my 22" widescreen 1680x1050 at 60 hz

---

### Post by bobwyajnr on 2010-11-09
> **masterskop said:**
> 
   800x600        77.0     78.0     79.0     80.0  


Hmmm,

So maybe the output from **xrandr** is a bit of a red herring. 800x600@85Hz isn't supported in your mode list either...

Thanks for the information. I'll try starting a separate multimedia thread about it (the Wine forum is a bit too quiet :rolleyes: )...

Bob

---

