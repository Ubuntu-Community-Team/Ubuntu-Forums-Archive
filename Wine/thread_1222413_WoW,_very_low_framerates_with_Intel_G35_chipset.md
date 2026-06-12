---
title: "WoW, very low framerates with Intel G35 chipset"
date: 2009-07-24
forum: Wine
---

### Post by Rishkaa on 2009-07-24
Before I begin, let me say that I'm new to the general idea of forums, so if I posted this in the wrong area, I am sorry.

I recently began using Ubuntu via a Wubi install and so still have Windows. I've learned a lot but what bothers me is, like many others here, I can't get WoW to run smoothly in Wine. The framerates is usually 9fps or less, and I must run in Direct3D mode because OpenGL causes everything to leave trails. 

I am an avid (mainly console) gamer, but my computer is not made for gaming. Its specs are as follows.

Can boot into Ubuntu 9.04 or Windows XP SP3 (Desktop)
Processor: IntelDuoCore @ 2.53 Ghz each
RAM: 3GB
Video: Intel G35 express chipset 

The Intel chipset ruins eveything, but at this time I cannot afford an actual card, and don't know if I ever can get one. On Windows, I am able to play with everything on the lowest settings and triple buffering/VSync on. I get 17-20 fps or more and am even able to dualbox.

But Wine is a different story. If I try to mimic anything other than 2000/XP/98, running WoW crashes Ubuntu and I have to physically reset my computer. Last night I spent 6 hours going back and forth between threads here, and other sites. I've tried everything. I've edited config.wtf. I've tried the registry fix (the screen swirled whenever I rotated the camera) I've ran in openGL, DirectX and Direct3D and gotten the aforementioned trails, or a black screen with some white polygons. I've turned shaders off, and the game will render, but framerates are poor. 

Ubuntu states my chipset, in a VGA check, to be claimed. I've considered updating the drivers but have no idea how to compile from source, which is mostly what intellinuxgraphics.org gave me. 

If it helps, I'm running WoW from the original Windows install on my C: drive. Sound is fine.

I apologize for the lack of order in this post. The bottom line: If I need to resort to using Windows solely for WoW, I will, but I want to move away from it; I like the opportunities Ubuntu presents and am learning to do more with it.

If you need additional information, I will do my best to provide it.

---

### Post by Fox Dark Master on 2009-07-26
have you tried to turn off the antialiasing of wow?

---

### Post by Rishkaa on 2009-07-26
> have you tried to turn off the antialiasing of wow?Hello, and thanks for replying. 

I'm not sure. Would I do that through the in-game settings or the config.wtf file?

---

### Post by OrbJinzo on 2009-07-26
Intel doesnt have decent driver support for opengl in linux.

---

### Post by Rishkaa on 2009-07-26
I know. Today I found that turning off triple buffering/vsync helped a little. But the map and character portraits still do not render well in d3d mode. A new video card is still not in my future, so I'll just stick with grudgingly running WoW in Windoze; d3d mode helps quite a bit with smoothness there, at least.

---

### Post by castlefox on 2009-07-27
Idk, I had problems with my Intel chipset in 9.04 , none of the advanced desktop options worked for me.  

Anyways, getting to my point.   IDK if using Ubuntu 8.10 instead would be any better because of the different x.org used in that release.

Does changing the resolution help the FPS at all ?

---

### Post by Uiztr0llin on 2009-07-27
if you want to play wow on ubuntu forget about 9.04. it sucks for intel because of a stupid bug. install 8.04 and run in opengl mode with triple buffering on and vsync off. thats a start.

---

### Post by Rishkaa on 2009-07-27
> Idk, I had problems with my Intel chipset in 9.04 , none of the advanced desktop options worked for me.  

Anyways, getting to my point. IDK if using Ubuntu 8.10 instead would be any better because of the different x.org used in that release.

Does changing the resolution help the FPS at all ?     When I downloaded Ubuntu, I accidentally clicked 9.04, though I'd planned on getting 8.10. I think I've heard that 8.10 is better... And I haven't tinkered with the res... I was running ubuntu in my monitor's native 1024x768, and a maximized WoW window. I tried changing the res of WoW ingame and Ubuntu crashed. I'll change my desktop res next time I boot Ubuntu and see what happens. 


> if you want to play wow on ubuntu forget about 9.04. it sucks for intel because of a stupid bug. install 8.04 and run in opengl mode with triple buffering on and vsync off. thats a start.I figured... :( Well I suppose it isnt too much of a problem to use Windows... I'm using this as a learning experience of sorts, so I thank you both for your input. :)

---

### Post by Uiztr0llin on 2009-07-27
> **Rishkaa said:**
> When I downloaded Ubuntu, I accidentally clicked 9.04, though I'd planned on getting 8.10. I think I've heard that 8.10 is better... And I haven't tinkered with the res... I was running ubuntu in my monitor's native 1024x768, and a maximized WoW window. I tried changing the res of WoW ingame and Ubuntu crashed. I'll change my desktop res next time I boot Ubuntu and see what happens. 


I figured... :( Well I suppose it isnt too much of a problem to use Windows... I'm using this as a learning experience of sorts, so I thank you both for your input. :)

we both have the same problem. i have to use the opensource ati drivers because they dropped support for my chip. but i dont even have windows to go back to :(

---

### Post by Rishkaa on 2009-07-27
> we both have the same problem. i have to use the opensource ati drivers because they dropped support for my chip. but i dont even have windows to go back to :sad: 

Ouch...

I'm fortunate enough that mine is still supported under Windows, but my little brother isn't so lucky. The most current driver for his chipset was released way back in 2005... :( (needless to say, his comp won't run anything that uses DirectX9.)

I wish you the best, and hope you can find a way to get Windows back, if you want to go that way, or that some kind of support is given to us by Intel soon. It'd take a miracle for anything to happen soon, I know, but...

Hmm, you can use ATI drivers with Intel chips? I thought the different brands weren't compatible and it'd totally ruin the computer's ability to display things. If so, that's interesting...  :-k

---

### Post by Uiztr0llin on 2009-07-27
> **Rishkaa said:**
> Ouch...

I'm fortunate enough that mine is still supported under Windows, but my little brother isn't so lucky. The most current driver for his chipset was released way back in 2005... :( (needless to say, his comp won't run anything that uses DirectX9.)

I wish you the best, and hope you can find a way to get Windows back, if you want to go that way, or that some kind of support is given to us by Intel soon. It'd take a miracle for anything to happen soon, I know, but...

Hmm, you can use ATI drivers with Intel chips? I thought the different brands weren't compatible and it'd totally ruin the computer's ability to display things. If so, that's interesting...  :-k

nooooooooo.i hate an ati chip in my laptop that i have to use the opensource ati driver for it. use have an intel chip that uses the opensource intel driver. i meant we both have to use the awful OSS drivers

---

### Post by Rishkaa on 2009-07-27
> nooooooooo.i hate an ati chip in my laptop that i have to use the opensource ati driver for it. use have an intel chip that uses the opensource intel driver. i meant we both have to use the awful OSS drivers

Ah, I'm sorry, I had a naive moment there... didn't think that that would work. I don't know if I have the latest driver from intellinuxgraphics.org. If I don't there isn't much I can do; the site expects you to build the package from tar.gz files and I fail to understand compiling and such...

---

### Post by Uiztr0llin on 2009-07-27
> **Rishkaa said:**
> Ah, I'm sorry, I had a naive moment there... didn't think that that would work. I don't know if I have the latest driver from intellinuxgraphics.org. If I don't there isn't much I can do; the site expects you to build the package from tar.gz files and I fail to understand compiling and such...

i know it sucks so bad :(

---

### Post by Rishkaa on 2009-07-28
The Windows side of my computer refuses to connect to any networks as of today though Ubuntu is fine--with a good speed and signal--, for reasons unknown. So I was forced to use Wine. I thought it might work until I got into combat. Constant red latencies combined with 9fps make the game unplayable. I don't have the money or the will to waste the time of tech support (my internet had to be fixed just a few days ago).

I've done all I can do and it appears the only apparent option now is to give up WoW and every other MMO. I am losing my composure over how Windows is adding to this problem and how Ubuntu can't solve it at the moment.

I thank those of you who offered some form of help and advice. Unless a moracle happens, however, my issue is closed.

---

### Post by castlefox on 2009-07-28
Are you having a bad wireless connection or wired connection?

Sometimes when I have connection problems with my computer connecting unplugging and then plugging in the router sometimes helps.

Did you ever get a chance to install a different version of ubuntu besides 9.04 ???

---

### Post by tufcamman on 2009-07-28
Hi,

I use a toshiba t-6836, with 9.04.  And yes, the included driver for the intel video does limit performance and stability.

I followed the instructions here

[http://webupd8.blogspot.com/2009/05/reverting-xorg-video-intel-driver-of.html](http://webupd8.blogspot.com/2009/05/reverting-xorg-video-intel-driver-of.html)

To downgrade my graphics to what they were in 8.04.  I have seen a huge performance increase in my graphics.  Might help for you.

---

### Post by DOS4dinner on 2009-07-28
> **Rishkaa said:**
> 

If it helps, I'm running WoW from the original Windows install on my C: drive. Sound is fine.



Wait...are you pointing Wine to your real C: drive, and running it from there? If so, your Windows side can get royally destroyed (The official WineHQ FAQ states to not do this). 

Also, Newegg's got a [Geforce 9500]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814133230") for $30 after a rebate. Might give ya a performance boost:P

---

### Post by Rishkaa on 2009-07-28
> Are you having a bad wireless connection or wired connection?

Sometimes when I have connection problems with my computer connecting unplugging and then plugging in the router sometimes helps.

Did you ever get a chance to install a different version of ubuntu besides 9.04 ???     I use wireless, but not wired. We would do that to the router when Windows Internet failed, but the router is in my parents' room and I don't have easy access. I get a good signal and speed in Ubuntu (same as Windows). Everything works fast and fine, except WoW. (now at least my Windows Internet is back.)

And although Wubi says you can uninstall it just like a program, I've heard that people have problems with GRUB and it messes up Windows when you try to boot... I don't want to lose all my hard drive contents and the best backup I have is a 1GB mp3....


> Hi,

I use a toshiba t-6836, with 9.04.  And yes, the included driver for the intel video does limit performance and stability.

I followed the instructions here

[http://webupd8.blogspot.com/2009/05/...driver-of.html]("http://webupd8.blogspot.com/2009/05/reverting-xorg-video-intel-driver-of.html")

To downgrade my graphics to what they were in 8.04. I have seen a huge performance increase in my graphics. Might help for you.
Hello there, and thanks for the link! I'm on windows right now, so I'll try it as soon as I can, and post back the results; seems like it may work from what others have told me! :D


> Wait...are you pointing Wine to your real C: drive, and running it from there? If so, your Windows side can get royally destroyed (The official WineHQ FAQ states to not do this). 

Also, Newegg's got a [Geforce 9500]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814133230") for $30 after a rebate. Might give ya a performance boost:razz:
Yes I am... oh no. WoWWiki said that was ok... :(

Well, I have the extra hard drive space to throw around at the moment, so I can install the client on the Ubuntu side too and get rid of it if it doesn't work, I suppose. But it'd have to be using that online InstallWoW application. Or, at worst, I can see if I can find a blank DvD and copy my Windows files to that... probably won't work.

I've seen some articles hinting at it, but I don't know how to install WoW using Wine... where would I put the files...?

Thanks for looking it up, but (and it shames me to admit it) I don't know how rebates work... I'm only 16, so no credit card. My parents could probably order it, but 60$ without rebate is still a lot of money, at least from my point of view. I've been encouraged by my parents to save my savings and probably could afford it by the time I'm 18 and getting Social Security checks. So I'm stuck in the land of integrated graphics till then, or at least Christmas maybe. :)

(Plus I only use this computer to play WoW and mess around with free to play mmos-- a controller is easier for me to use than a keyboard, and my PS2 works fine... If I'd a choice, I'd rather have a PS3.)

---

### Post by DOS4dinner on 2009-07-28
> **Rishkaa said:**
> 
Yes I am... oh no. WoWWiki said that was ok... :(

Well, I have the extra hard drive space to throw around at the moment, so I can install the client on the Ubuntu side too and get rid of it if it doesn't work, I suppose. But it'd have to be using that online InstallWoW application. Or, at worst, I can see if I can find a blank DvD and copy my Windows files to that... probably won't work.

I've seen some articles hinting at it, but I don't know how to install WoW using Wine... where would I put the files...?

Maybe with WoW it's not a problem, but usually they don't recommend you do that. See this [FAQ]("http://wiki.winehq.org/FAQ#head-497f1a295d53dd3444f211df2b13312c7767afa2")

You would install it just like you do in Windows. Just put the CD in (or whereever you got the installer), run the setup.exe, and let it install. It's just like windows, but less microsofty.

edit: Oh, and don't worry about Wubi. It's pretty safe, and, worse case scenario, you could use a Ubuntu disk to boot off of and get your important files off. I used to use it, and I had no problems at all.

---

### Post by Rishkaa on 2009-07-28
> Maybe with WoW it's not a problem, but usually they don't recommend you do that. See this [FAQ]("http://wiki.winehq.org/FAQ#head-497f1a295d53dd3444f211df2b13312c7767afa2")

You would install it just like you do in Windows. Just put the CD in (or whereever you got the installer), run the setup.exe, and let it install. It's just like windows, but less microsofty.

edit: Oh, and don't worry about Wubi. It's pretty safe, and, worse case scenario, you could use a Ubuntu disk to boot off of and get your important files off. I used to use it, and I had no problems at all.

OK. That makes me feel much better. I should be able to try this later on tonight, or maybe tomorrow!

---

### Post by dardack on 2009-07-29
> **DOS4dinner said:**
> 

You would install it just like you do in Windows. Just put the CD in (or whereever you got the installer), run the setup.exe, and let it install. It's just like windows, but less microsofty.


You actually don't need to install, just copy the folder from the windows partion over to your ubuntu partition.  Setup takes for freaking ever with wow, copying took me like 25 minutes or something.

---

### Post by Rishkaa on 2009-07-29
> You actually don't need to install, just copy the folder from the windows partion over to your ubuntu partition. Setup takes for freaking ever with wow, copying took me like 25 minutes or something.

That's good news--25 minutes isn't near as bad as when I installed it on Windows the first time.... took me almost a whole day. (laughs)

---

