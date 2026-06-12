---
title: "Fish Aquarium test how does your hardware/software stack up?"
date: 2014-12-01
forum: The Cafe
---

### Post by irv on 2014-12-01
The Fish Aquarium test can be found at this [LINK]("http://webglsamples.org/aquarium/aquarium.html")
My laptop checks out at 60 fps at 2000 fish, and 43 fps at 4000 fish.
[ATTACH=CONFIG]258308[/ATTACH]   [ATTACH=CONFIG]258309[/ATTACH]

---

### Post by Linuxratty on 2014-12-01
15fps at 1,000 fish on my 4 gig box. Fire Fox browser NVIDIA GT610.

---

### Post by grahammechanical on 2014-12-01
Well someone does not know what they are talking about. I am told: "It appears that your computer does not support WebGl." More likely it is the Chromium browser that does not support WebGL.

[http://en.wikipedia.org/wiki/WebGL](http://en.wikipedia.org/wiki/WebGL)

Firefox gives me 20 fps @ 50 fish: 17 fps @ 100 fish; 11 fps @ 4000 fish.

Regards.

---

### Post by Habitual on 2014-12-01
I get 60fps (fish per second?) @4000 using Chrome [COLOR=#303942][FONT=DejaVu Sans]38.0.x.xxx [/FONT][/COLOR]but only 23 fps @4000  using FF 27.0.1

---

### Post by irv on 2014-12-01
I was using the Chrome browser and my specs on my laptop is in my signature. I know Chrome does support WebGL.

---

### Post by SagaciousKJB on 2014-12-01
10 fps @ 50 fish :/

AMD Turion X2 RM-70 2 Ghz
3 GB DDR2800 RAM
Mobility Radeon HD 3100

---

### Post by irv on 2014-12-02
> **SagaciousKJB said:**
> 10 fps @ 50 fish :/

AMD Turion X2 RM-70 2 Ghz
3 GB DDR2800 RAM
Mobility Radeon HD 3100

What Browser did you use for the test?

---

### Post by pqwoerituytrueiwoq on 2014-12-02
chrome 60fps 4k fish
firefox developer build 4k fish gets 60fps, but it freezes every 2 seconds for 5 seconds, 2k works just fine at 60fps
using my desktop and all its overkill powers

---

### Post by Dennis N on 2014-12-02
OK, I get identical 60 fps for Fish=1 to 500, then it drops by 5 fps (to about 55) for 1000, down another 10 fps (to about 45) for 2000, down another 13 fps (to about 32) for 4000. This machine - using Firefox 33 with i3-4150 processor, Intel HD 4400 integrated graphics.

---

### Post by SagaciousKJB on 2014-12-02
> **irv said:**
> What Browser did you use for the test?

Whatever the latest Firefox for 12.04 is

Seems like it's bottleknocked by the graphics card.  I tried on my AMD Phenom 9950 but with Radeon HD 3300 graphics and it was pretty much the same.  Actually only 7 fps per fish, but it looked smoother :/

On the laptop I run Xinerama though so maybe that's why it ran so sloppy.

---

### Post by irv on 2014-12-02
With Firefox 33.0 I get 28 fps with 2000 and 18 fps with 4000. Much slower with then Chrome.

---

### Post by SagaciousKJB on 2014-12-02
To be fair Chrome nor Midori even ran the WebGL plugin for me.  I've been trying to move away from FireFox.

You know what's interesting me?  My laptop got 10 FPS despite displaying two screens in Xinerama mode and having a mobility Radeon HD 3100 right?  Well my desktop has a HD 3300 integrated GPU and is just a single display, but it only got 7 FPS.  Meanwhile the dispaly on the laptop didn't look visually as smooth as on the desktop?! O.o

One difference is I'm just using the open source "radeon" driver on the desktop but the proprietary drivers on the laptop.

---

### Post by Old_Grey_Wolf on 2014-12-02
I use Chrome v39. On my laptop I get ~60 fps at 1000, ~40 fps at 2000, and ~30 fps at 4000. Whatever that means.

With Firefox 33, I get 8 fps no matter what I select.

---

### Post by Jonor on 2014-12-02
Firefox 33.0 gets 60fps at 4k with GeForce GTX 750 Ti graphics running nvidia 343.22 and no other browser tabs. 
Youtube vids do not like sharing FF with plenty of fish. 8 tabs drops to around 40 fps.
Enjoyed fiddling the advanced options, speaking as a non-gamer.

---

### Post by Hansiman on 2014-12-02
Chrome: Stable 60fps at 4000 fish.
Using a GeForce GTX780ti card.

---

### Post by irv on 2014-12-02
The WebGL uses hardware acceleration. From the Wiki page it said "code that is executed on a computer's Graphics Processing Unit (GPU)" and I did notice that if I let it run for, say 5 to 10 minutes, it does heat up the GPU and the fan kicks on and and starts blowing out the heat. This means that there are some factors in the fps on graphics. One being the browser and the other being the GPU speed.
It sounds like this is done by code within JavaScript.

---

### Post by coldcritter64 on 2014-12-03
> **irv said:**
> The Fish Aquarium test can be found at this [LINK]("http://webglsamples.org/aquarium/aquarium.html")
...
Only got to try out the 50 fish setting .... :p

Both google-chrome-stable and chromium on Debian Wheezy give the error grahammechanical noted earlier.
Firefox Nightly, 1 fps then the browser seizes solid requiring a kill signal.
Iceweasel (Debian branded firefox), similar to Nightly without seizing (a painful 1fps)


> how does your hardware/software stack up?
It doesn't here, the next quote box from this install may give a clue why 
> 01:00.0 VGA compatible controller: NVIDIA Corporation G72M [GeForce Go 7400] (rev a1)
On an old HP dv6 dual core laptop. Can't even use VDPAU acceleration with mplayer on this old "pile of junk" :)
I really need to get off my big butt and fix my desktop tower.:wink:

---

### Post by xubu2 on 2014-12-06
48 fps with 100 fish.
37 fps with 1000 fish.
21 fps with 4000 fishies.
Not really ground braking but a nice test!
Used firefox 34 and intel gpu.

---

### Post by linuxyogi on 2014-12-07
My result is pathetic. 1fps @50 fishes.

AMD 64 X2 5600+ 
Ram : 2GB
Nvidia 6150 SE (Non free driver)
Firefox 34.0.5

---

### Post by QIII on 2014-12-07
4000 fish at 60 fps in Chrome.

4000 fish at 15 fps in FF.

---

### Post by ventrical on 2014-12-07
16@4000 on Sandy Bridge.

Sheesh ... :)

---

### Post by Elfy on 2014-12-07
4000 @ 21fps in ff

---

### Post by bapoumba on 2014-12-07
Does not even start here, all options greyed-out. A poor machine is poor :)
FF 34.0.

---

### Post by oldos2er on 2014-12-07
4000 fish @ 46 fps, FF34

---

### Post by irv on 2014-12-07
The reason I went with the Aquarium and not the [Fish Bowl speed test]("http://ie.microsoft.com/testdrive/performance/fishbowl/") was MS has it rigged to make IE look Good.

---

### Post by xubu2 on 2014-12-07
> **QIII said:**
> 4000 fish at 60 fps in Chrome.

4000 fish at 15 fps in FF.

Seriously?
Have to try chrome again :)

---

### Post by howefield on 2014-12-07
Chrome hardly missing a beat at 60fps for 4000 fish whereas Firefox barely got past 25 fps for 4000 fish.

Opera performing slightly below Chrome for me, 60 fps for 4000 fish but every 20 seconds or so would fall back to 35ish before recovering back to 60.

---

### Post by pfeiffep on 2014-12-07
This was an interesting test ... I've never even wondered about frame rate when editing video which my system performs to my liking. 
I do not play games - and from the review of this card I couldn't play 3D games very effectively. [TABLE="class: grid, width: 100, align: left"]
[TR]
[TD]#fish[/TD]
[TD]fps[/TD]
[/TR]
[TR]
[TD]1[/TD]
[TD]28[/TD]
[/TR]
[TR]
[TD]250[/TD]
[TD]27[/TD]
[/TR]
[TR]
[TD]1000[/TD]
[TD]23[/TD]
[/TR]
[TR]
[TD]4000[/TD]
[TD]15[/TD]
[/TR]
[/TABLE]
Firefox 34.0
Memory 12 G
Processor Intel® Core™ i7 CPU 960 @ 3.20GHz × 8[INDENT]display               
       description: VGA compatible controller
       product: Caicos [Radeon HD **6450**/7450/8450 / R5 230 OEM] [1002:6779]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI] [1002]
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
[/INDENT]
[INDENT=2]driver   : fglrx - distro non-free
driver   : xserver-xorg-video-ati - distro free builtin recommended
driver   : fglrx-updates - distro non-free
[/INDENT]

---

### Post by xc3RnbFO8P on 2014-12-07
Unity Mir
Ubuntu WebBrowser 
4000 fish  28 fps

---

### Post by irv on 2014-12-08
@pfeiffep if you tried the test with Chrome I bet you would see a great improvement. Your system has more horsepower then mine, as you can see in my signature.

---

### Post by irv on 2014-12-08
I just installed lubuntu on an old laptop with a pentium M processor and thought I would try the Fish Aquarium test on it just for kicks but it won't work. All I get is:
> It does not appear your computer supports WebGL.
Click here for more information.

Status: Could not create a WebGL context.

Looks like this old hardware does not support the WebGL code in the JavaScrip.

---

### Post by pfeiffep on 2014-12-08
> **irv said:**
> @pfeiffep if you tried the test with Chrome I bet you would see a great improvement. Your system has more horsepower then mine, as you can see in my signature. I ran the test again on both Chrome and Chromium with very little difference
Firefox 34  
[TABLE="class: cms_table_grid, align: left"]
[TR]
[TD]#fish[/TD]
[TD]fps[/TD]
[/TR]
[TR]
[TD]1[/TD]
[TD]28[/TD]
[/TR]
[TR]
[TD]250[/TD]
[TD]27[/TD]
[/TR]
[TR]
[TD]1000[/TD]
[TD]23[/TD]
[/TR]
[TR]
[TD]4000[/TD]
[TD]15[/TD]
[/TR]
[/TABLE]
Chrome / Chromium
[TABLE="class: cms_table_grid, width: 100, align: left"]
[TR]
[TD]#fish[/TD]
[TD]fps[/TD]
[/TR]
[TR]
[TD]1[/TD]
[TD]30[/TD]
[/TR]
[TR]
[TD]250[/TD]
[TD]30[/TD]
[/TR]
[TR]
[TD]1000[/TD]
[TD]29[/TD]
[/TR]
[TR]
[TD]4000[/TD]
[TD]21[/TD]
[/TR]
[/TABLE]
I really don't notice any lag when I view videos, streaming content nor when I edit videos. For my use I don't think frame rate is very important.
Next time I fire up my Dell laptop I'll run the test on it!

---

### Post by Frogs Hair on 2014-12-08
Firefox  16 fps/4000 ><>
Opera 26 Stable 30 fps/4000 ><>

```
HP Compaq 8460p
i5-2540M CPU @ 2.60GHz vendor: Intel Corp.
VGA compatible controller product: 2nd Generation Core Processor Family Integrated
Memeory:size: 4GiB
```

---

### Post by Jonor on 2014-12-08
Try clicking on Advanced options, change the eye radius to about 62 and the mouse around the eye height for the 4k setting.
Make sure there are no drinks nearby.

---

