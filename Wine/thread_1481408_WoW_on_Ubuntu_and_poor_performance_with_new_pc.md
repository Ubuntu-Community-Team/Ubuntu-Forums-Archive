---
title: "WoW on Ubuntu and poor performance with new pc"
date: 2010-05-12
forum: Wine
---

### Post by bemarh on 2010-05-12
Hello, thank you for taking the time to read this post. I am a new linux user, my husband has just recently built me a new computer and put Ubuntu on it for me. He is a long-time linux user, though I am coming from a Mac myself. 

We both play World of Warcraft, and we built this computer with WoW in mind. But for some reason, it is not performing as we thought it would. My husband has been pretty busy with work and hasn't had alot of time to help me research it, so I thought I would post on this forum to see if anyone has any advice. The main issue is that the framerates aren't what I think they could be, especially from what others can get on a similar machine to mine. I currently have anywhere from 12-35 fps in game. In Dalaran, where it is always the hardest on computers, I get from 12-24 typically. In other areas I might have 28-35, lowering in instances and such. I still get stuttering/lag on my screen at times as well when I turn around in the game, even in the vanilla content. My latency is 50s-60s average. My settings are maxed for the most part, as we made the computer with the idea that it would handle it. I have turned the shadows down to low and lowered the viewing distance a small amount. 

Here are my computer specs as I know its hard to help without them:

Running Ubuntu 10.04
Screen: AOC 21.5in 1920x1080
AMD Phenom II x4 955 Black Edition Deneb 3.2 Socket AM3 125W Quad-Core
8GB DDR3 SDRAM
EVGA GeForce 9800 GTX+ 512MB (updated driver: 195.36.15)
1TB ATA Hitachi Hard drive
MSI 770-C45 AM3 AMD 770 ATX AMD motherboard
Antec EarthWatts 650W Powersupply


Any advice, is there something wrong? I mean, this system should be knocking the socks off the game, right? Thanks for any help ahead of time!!

---

### Post by Vakman on 2010-05-12
Well you are running this game under Wine, correct?
That will hurt performance but it usually does run pretty well. There are probably also some tweaks you can do for WoW to run better under Wine.
Open Terminal, and post the output of
```
glxinfo | grep direct
```

---

### Post by bemarh on 2010-05-12
Yes, it is running under wine. I typed what you said, and the response given was yes.

---

### Post by joeelmex on 2010-05-12
Bemarh make sure you have all desktop effects to off.  See if that helps you.

Also make sure you edit the config file in Wow and added the -opengl line.

---

### Post by bemarh on 2010-05-12
Thisislaw: sorry, I didn't add the rest that came after "yes", I was running out to pick up my son from preschool. Now that I'm back, I realize there's more: GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_direct_state_access. Not sure if that's important.

Joeelmex: I'll check about the desktop effects, not sure about how to do that. Like I said, very new to linux. I'm trying to figure out where the wow files are so I can check the config file, I know, I don't know much. But still trying to figure out the linux file system. 

Thanks for the help both of you!!

---

### Post by hikaricore on 2010-05-12
As I said no one reads the damn stickies..  this is not the wine forum.

---

### Post by bemarh on 2010-05-12
> **hikaricore said:**
> As I said no one reads the damn stickies..  this is not the wine forum.

If you would read the whole thread, wine is not my issue and if that ends up being the problem, how could I know ahead of time? For all my knowledge, wine is working fine. That's why I'm asking for help in a more general forum. And I'm new here, and just looking for advice related to wow and using linux. No need to be rude, and if there's a specific sticky that can help me, why not be helpful and link it?

---

### Post by hikaricore on 2010-05-12
> **bemarh said:**
> If you would read the whole thread, wine is not my issue and if that ends up being the problem, how could I know ahead of time? For all my knowledge, wine is working fine. That's why I'm asking for help in a more general forum. And I'm new here, and just looking for advice related to wow and using linux. No need to be rude, and if there's a specific sticky that can help me, why not be helpful and link it?

Wine related issues belong in the wine forum, no matter how you try and split hairs.
The sticky in the gaming and leisure forum specifically states this in plain english.
Since this thread has already been moved I'll happily drop it.  But next time read the stickies first.

---

### Post by bemarh on 2010-05-12
> **hikaricore said:**
> Wine related issues belong in the wine forum, no matter how you try and split hairs.
The sticky in the gaming and leisure forum specifically states this in plain english.
Since this thread has already been moved I'll happily drop it.  But next time read the stickies first.

Thank you for moving this to the correct forum, yes, I didn't read that sticky, though I did happen to skim the others. Not sure how I missed that part, but went back and read it. I am brand new to this forum, and didn't even realize there was a wine forum and that this needed to be posted there. I'm also new to linux, and my husband has done all the work on my computer, so I didn't realize the significance of wine either. 

Now that I'm in the right spot, could anyone offer some suggestions, I realize you all need my version of wine: 1.1.42. 

I also don't know anything about the terminal output or wine configuration, so if you need this I can wait for my husband to get it for me when he is home. Thanks ahead of time.

---

### Post by Vakman on 2010-05-12
Hm, there shouldn't be anything after that if I remember correctly. If it is simply "Yes" then you would likely be good "No" or anything else is odd. But they are likely installed correctly.
Follow this link: [https://help.ubuntu.com/community/WorldofWarcraft#OpenGL](https://help.ubuntu.com/community/WorldofWarcraft#OpenGL) or Direct3D
It will change you from using Direct3D (the default) and since Direct3D is only supported through WineD3D which lowers the FPS a fair bit since it is running Direct3D through an emulation layer, so some people opt to use OpenGL instead.
That link shows you how.
Also, on that same page: [https://help.ubuntu.com/community/WorldofWarcraft#Graphics](https://help.ubuntu.com/community/WorldofWarcraft#Graphics) troubleshooting
There is a spot for Graphics troubleshooting. These two tweaks help a lot of people get it working better as well.
Hope this helps.
ADD/EDIT: I forgot and what someone else posted above about changing the visual effects, try that before doing anything I said.
[https://help.ubuntu.com/9.10/desktop-effects/C/compiz-configure.html](https://help.ubuntu.com/9.10/desktop-effects/C/compiz-configure.html)
Since you are new that is the link on how to do it. When gaming, I usually turn them completely off.
As the link says, Click System > Preferences > Appearance > Visual Effects
The Visual Effects is a tab within Appearence.

---

### Post by bemarh on 2010-05-13
Thanks for the response, we looked into all those things, and have implemented what we could. We also shut off the cool and quiet feature of the amd processor. But honestly, the fps have really only improved by about 5 or so. Now I'm averaging 18-20 fps in Dalaran, and about 30-40 in other areas, but still alot of screen stuttering even when at 35. And it easily drops to 22 when flying or doing something.

Could there be another issue with the graphics card or having a quad core processor with an older game? Some configuration issue? I've also been trying to peruse the wow technical forums, but so far haven't found anything that really helps. Am I wrong to assume this computer can do better?! Thanks.

---

### Post by rJ~ on 2010-05-14
This doesn't really help other than confirming it's not just your system, but I'm using a PhenomII X4 940, 790GX motherboard, 8GB DDR2 Ram and a Geforce 8800 GT and I'm seeing the same "bad" performance in Linux (Running 10.04 as well).

In Windows 7 WoW runs with all the details (Except shadows) maxed at 1680x1050 without a problem. 

In Ubuntu I've turned down most settings except particle density, textures and projected textures. View distance around 50%. I find most things playable, except Dalaran, Alterac Valley and Wintergrasp.

Turning down view distance should help with FPS when flying around. 

If you want to keep cool and quiet enabled when not playing WoW you can add the 'CPU Frequency Scaling Monitor' applet to your gnome panel and change it to performance mode when playing WoW.

---

### Post by Vakman on 2010-05-14
Err, so all that I posted only raised your FPS by about 5?
Hm...
In your Wine settings try telling it to run it like it is Windows XP, if it is already set to that compatibility mode, change it to Vista or 7.
Will look into this again after. Your hardware is not the problem.
I am wondering if it is the performance of the drivers in 10.04 but that is also unlikely I think.
It is now more likely they are installed oddly. We will see. I have to go now, I will post more later, unless someone else more useful than myself comes here.

---

### Post by bemarh on 2010-05-14
Thisislaw -  Good news is, last  night we messed around more with it, and my husband did more with the  opengl and flag. We also came across this thread on the nvidia forums: [http://forums.nvidia.com/index.php?showtopic=164046](http://forums.nvidia.com/index.php?showtopic=164046) ,  specifically the one by Sray. My husband wondered if the gpu and cpu  weren't running in sync causing the poor quality, and if the gpu was  going too fast. So he messed with the drivers, not sure exactly what he  did, but it worked. I'm now getting average of 30 fps in Dalaran and  50-80 everywhere else. But the important part is, its smooth!!! No more stuttering or anything.  And this is all on ultra settings with the shadows turned down a bit.

rJ~ : Sounds like you might be having a similar problem to what I had. In researching this, it seems there's alot of people with higher end computers that have a hard time with WoW. Doesn't take long to do a search on the WoW forum technical board to find this. I'm posting some info below one one other minor issue I've noticed, and when my husband gets home from work tomorrow, I'll see if he can post exactly what he did, and explain it in technical terms. Hopefully this will help you to get it working better as well as anyone else that has this problem. 

So the only other thing is that the cursor can be a bit laggy at times, mainly in Dalaran. I was given this info on another forum and thought it might be helpful to others as well as myself. Hopefully my husband will look through it with me when he gets home, as alot of it is over my head.

             This is taken directly from the WineDB for the latest Gold rated wow:
    > 
[SIZE=1]**Stuttering while walking**

This is caused by a bug in the latest Xserver release. This should be  fixed by the next round of distribution releases this fall. In the mean  time, you can disable key repeat by going to System/Preferences/Keyboard  in Gnome.[/SIZE] [SIZE=1]

** Mouse cursor slow**[/SIZE] [SIZE=1]

This is because Blizzard has not implemented OpenGL hardware cursor  functionality in the Windows version. However, there is a patch here  that simulates a real hardware cursor.[/SIZE] [SIZE=1]

** Graphic corruption**[/SIZE] [SIZE=1]

Scroll down and try the registry tweak, if that does not work, reinstall  the driver. [/SIZE] [SIZE=1]

Corruption when doing "Maintaining the Sunwell Portal" and WOTLK  'flashback' Quests:[/SIZE] [SIZE=1]

Add this to your config.wtf file:[/SIZE] [SIZE=1]

SET ffxNetherWorld "0" ~ thanks to Adys[/SIZE] [SIZE=1]


Note that this used to be a tweak needed to boost FPS, but is apparently  not needed anymore for non-ATI users.[/SIZE]   [SIZE=1]

   1. Open the registry editor and navigate to the following key[/SIZE] [SIZE=1]

      HKEY_CURRENT_USER\Software\Wine\[/SIZE] [SIZE=1]
   2. Highlight the wine folder in the left hand pane by clicking left  on it. The icon should change to an open folder
   3. Right-click on the wine folder and select [NEW] then [KEY]
   4. Replace the text New Key #1 with OpenGL
   5. Right-click in the right hand pane and select [NEW] then [String  Value]
   6. Replace New Value #1 with DisabledExtensions (Notice it's case  sensitive!)
   7. Then double click anywhere on the line, a dialog box will open.
   8. In the value field type GL_ARB_vertex_buffer_object

      Please note that after using this tweak, the icon pictures may  misplace themselves. For example, the icon for "gold" will look like and  icon for an orb.[/SIZE] [SIZE=1]

**NVIDIA issues**[/SIZE] [SIZE=1] 
GLXBadDrawable[/SIZE] [SIZE=1]

Make sure triple-buffering is turned off. ~ Thanks to DRH[/SIZE] [SIZE=1]

FPS stutter[/SIZE]  [SIZE=1]

Set farclip (the view distance slider) to 777 (about midway on the  slider) ~ Thanks to Andrew[/SIZE] [SIZE=1]

**Bad FPS in general:**[/SIZE] [SIZE=1]

Please make sure that you are not suffering from high latency, as this  will cause some FPS problems. If the small 'computer' icon shows you  more than 600ms, or if it is red, then you are having high latency.  Please check with your ISP.[/SIZE] [SIZE=1]

** Mouse cursor jumps**[/SIZE] [SIZE=1]

"If I show the hide buttons on my Gnome panel and hide the panel before I  start the game, then the mouse behaves normally. The hide button isn't  visible in-game." ~ Thanks to NV[/SIZE] [SIZE=1]

Please note that the mouse will not be perfectly smooth in OpenGL mode  because Blizzard Entertainment does not support Hardware Cursor in  OpenGL with the Windows version of the game. However, there is a patch  available here[/SIZE] [SIZE=1]

** Hard Drive Thrashing**[/SIZE] [SIZE=1]

There is no solution yet. It seems it is a windows problem too when you  are using more then 4GB RAM.[/SIZE] [SIZE=1]

** Lags/Stuttering**[/SIZE] [SIZE=1]

"Tried the setting "Reduce input lag" and that helped incredibly much  for me and the same for the first person I told to try it. Definetly not  a placebo." ~ Thanks to Anders Aa.[/SIZE] [SIZE=1]

** Low FPS**[/SIZE] [SIZE=1]

Disable screen glow effect and the lighting effect. ~ Thanks to Ram[/SIZE] [SIZE=1]

Try to run the game with the -opengl argument in the terminal. ~ Thanks  to Fluffles[/SIZE] [SIZE=1]
[B]
Ati Users:[/B] Make sure you have the latest drivers![/SIZE] [SIZE=1]

Bad graphical corruption in certain areas[/SIZE] [SIZE=1]

   *  Find the following registry entry:[/SIZE] [SIZE=1]

      HKEY_CURRENT_USER\Software\Wine\Direct3D\[/SIZE] [SIZE=1]

    *  Add a new key (type String) and name it 'OffscreenRenderingMode'[/SIZE] [SIZE=1]

    * Double click the new key and add the value 'pbuffer'[/SIZE] [SIZE=1]

** Dalaran and/or other areas cause crashes**[/SIZE] [SIZE=1]

This is due to WoW running 32-bit (there is no 64-bit client) and trying  to allocate more than roughly 4GB of memory for advanced textures. This  is a bug in Wine, since wine, by default, reserves 4096MB (the maximum  for 32bit systems) of virtual memory to mimic the win32 memory layout.  WoW allocates progressively more memory for textures and this forces the  display drivers (which are loaded in the same section of memory) to  quit with an GL_OUT_OF_MEMORY error.[/SIZE] [SIZE=1]

Dalaran is a good example of this. Dragonblight and Icecrown may also  suffer from this bug.[/SIZE] [SIZE=1]

A possible workaround includes trying is to force Linux to use less  memory than what you have, or to make it think it has less memory (eg,  limit it to 3GB). The preferred way to do this is to add the mem=3G (for  3GB) or mem=2G (For 2GB) flag to your kernel boot parameters.[/SIZE] [SIZE=1]

How to do this can be found in your particular distro's documentation.[/SIZE] [SIZE=1]

Some people have reported it to work, whilst for others it has not. You  may need to sacrifice the advanced textures if you try this.  [/SIZE][SIZE=1]
[/SIZE]

---

### Post by rJ~ on 2010-05-14
@Thisislaw
Performance was about the same in 9.10 with the included driver version, so no regressions for WoW that I know of.

@bemarh
Sounds very interesting. It's around the performance I got in Windows so I would be very interested in seeing how you achieved that.

---

### Post by Vakman on 2010-05-15
All right, good good.
I was guessing it was now driver related in one way or another.
Either way, glad it is all working.

---

