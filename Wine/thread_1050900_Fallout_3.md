---
title: "Fallout 3"
date: 2009-01-26
forum: Wine
---

### Post by Ole Andersen on 2009-01-26
Hey All 

I´m in urgent need for help with wine and fallout 3
I have forund an installation guide, but I do not understand it (newbie)

Here it is.: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=14322](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14322) 

Allready at the beginning i´m lost:

"At this point only way to get it to work is to download latest(1.1.8.) sources, patch them and then compile wine.
WinD3D patch: [http://bugs.winehq.org/attachment.cgi?id=17130](http://bugs.winehq.org/attachment.cgi?id=17130)
Download it, paste it to wine sources dir (wine-1.1.8.) and type
patch -p1 < filename.diff
" 

What am I to doo, and what is it about?

Next step isent easeyer for a newbie like mee

"Next step will be to download winetricks and install directx9
Get winetricks: [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)
Grand it executable permissions: chmod +x winetricks
Install directx9: ./winetricks directx9" 

Im still new to Linux, but really want to keep it instead of Vista. But I just need fallout 3 to run in linux.

/Ole

---

### Post by cogadh on 2009-01-26
You need to download the source code for Wine version 1.1.8 and patch it with the Direct3D patch using the command listed in the how-to, then compile Wine. You might be able to do it with the current Wine source code (version 1.1.13) as well, but I am not certain of that. For some basic instructions on compiling Wine, look [here]("http://tuxarena.blogspot.com/2008/09/how-to-compile-and-install-wine-114-in.html"). That how-to is for an older version of Wine and Ubuntu, but everything still applies.

---

### Post by sirdilznik on 2009-01-26
The Direct3D patch works with any wine version > 1.1.8.

---

### Post by Ole Andersen on 2009-01-28
After trying out your suggestions, i finally succeded!! Amazing.
Fallout now runs - thou it runs in a window, but that should be an easy fix.

The next issue is the mouse. It´s stuck to the center of the screen/window. it seems "magnetic", I can pull i away for ½ a secon, but i reutrns emedietly. 

In the wine *how to* i found the following:

To fix problem with mouse, in fallout.ini set following value:
bBackground Mouse= 1
If you still have mouse issues, set one of following registry values:
"MouseWarpOverride"="enable" 
or 
"MouseWarpOverride"="force"


I have changed the *bBackground-value* to 1, but that dident help. The next step is to try  setting the *registry value*, but I havent got a clue to what and were that is.

Is it a wine setting or a fallout .txt file i have to edit?

Thanx in adwance - hoping for your help.

/Ole

---

### Post by cogadh on 2009-01-28
Its a Wine registry setting, just like a registry setting in Windows. See the Wine [Useful Registry Keys]("http://wiki.winehq.org/UsefulRegistryKeys") page for details.

BTW - Many of the keys on the Useful Registry Keys page do not exist by default. I'm not sure if the mouse warping is one of them, but if it is, that means you need to create it yourself using regedit.

---

### Post by Ole Andersen on 2009-01-31
OK thanks for the help....now I have made the new key "DirectInput" the key "MouseWrapOverride" And set the value to enable, but that dident work afterwards i tried "force"

I might be doing something wrong, pr leaving something out...I&#7743; just new to regedit, so I can't tell right from wrong.
Here is a screenshot - am I on track? And what can i do?
The "how to" hs no more options.

---

### Post by cogadh on 2009-01-31
That screenshot is too small to read.

---

### Post by Ole Andersen on 2009-02-04
Hi again 
hope you are still up for help. 
The ubuntu forum shrinkss the picture, so I dont know how to post it. i havent got an Homepage.
But lets do as if I managed to place the key right - am I then supposed to update the regestry db? og somethink similar?

---

### Post by AllRadioisDead on 2009-02-04
> **Ole Andersen said:**
> Hi again 
hope you are still up for help. 
The ubuntu forum shrinkss the picture, so I dont know how to post it. i havent got an Homepage.
But lets do as if I managed to place the key right - am I then supposed to update the regestry db? og somethink similar?

[http://aquate.us](http://aquate.us)

---

### Post by cogadh on 2009-02-04
> **Ole Andersen said:**
> Hi again 
hope you are still up for help. 
The ubuntu forum shrinkss the picture, so I dont know how to post it. i havent got an Homepage.
But lets do as if I managed to place the key right - am I then supposed to update the regestry db? og somethink similar?
If you have made the change correctly, you don't need to do anything else. 

As for the pic, There are several free hosting sites you could use, like the one ihermit posted or you could post it as a PNG instead of a JPG. There are no dimension limitations for PNGs on the forums, just file size limitations (976.6KB).

---

### Post by Dizzle7677 on 2009-02-04
> **Ole Andersen said:**
> OK thanks for the help....now I have made the new key "DirectInput" the key "MouseWrapOverride" And set the value to enable, but that dident work afterwards i tried "force"

I might be doing something wrong, pr leaving something out...I&#7743; just new to regedit, so I can't tell right from wrong.
Here is a screenshot - am I on track? And what can i do?
The "how to" hs no more options.

Try (string)"MouseWarpOverride"->"disable" not enable/force.

Check out the [Appdb]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=14322"). Good luck with it b/c Fallout3 is buggy as all get out.

---

### Post by Ole Andersen on 2009-02-06
Here the .png is.
am I doing something wrong

---

### Post by cogadh on 2009-02-06
Yup. You made the string "Mouse**Wrap**Override" when it should be "Mouse**Warp**Override".

---

### Post by brMichal on 2009-03-01
It is my first time patching compiling and playing with Wine, but I could not get right results. 

After patching, compiling, installing wine, winetricks and DirecX9 and finally Fallout 3 I have the following deviations from your results:

1) in regedit: I do not have Current_user/Software/Wine/Direct3D directory,

2) when I start FalloutLauncher.exe I get the following: 

```

```$ wine FalloutLauncher.exe
fixme:win:EnumDisplayDevicesW ((null),0,0x1abf850,0x00000000), stub!
fixme:d3d:test_pbo_functionality >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Loading the PBO test texture
 @ directx.c / 3823```

```



3) when I choose "Play" I get repeatedly the following: 

```

```fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3584
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 526
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 276
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 127 requests (127 known processed) with 0 events remaining.```

```




I can never see video at this point. Sometimes I can navigate out based on sound and sometimes I have to force quit application. 

It is my first time patching compiling and playing with Wine. Can anyone tell me how to interpret and identify the problem here? 

I would greatly appreciate it. Thanks,

---

### Post by TheLastExodus on 2009-04-05
Um.......sorry to sound like a noob but I haven't even been able to figure out..um....how to apply the patch to wine....all the instructions seam kinda....vague...also does a steam download version of fallout3 work?
edit
using 8.10 64bit an i'm very clueless on programing >.<

---

