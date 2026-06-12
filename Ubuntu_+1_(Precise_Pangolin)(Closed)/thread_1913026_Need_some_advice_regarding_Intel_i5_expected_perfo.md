---
title: "Need some advice regarding Intel i5 expected perfomance on PP"
date: 2012-01-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2012-01-21
I gave up using laptops with Linux some time ago (probably one year or a little more) and was using tablets with android when travelling or visiting clients. Also, I gave up using Intel CPUs in my desktops and haven't used an OnBoard GPU in 3 or more years. Now, unfortunately, I'll have to use a laptop (Intel based-i5) again and I'm lost as to what performance should I expect when running PP. I don't have a way to compare: My desktops are really fast machines, with high-end AMD CPUs (Phenom II X6 1100BE, Opteron CPUs), NVidia GPUs, high-performance RAM, SATA 3 SSDs, overclocked, etc.

I have just installed PP in a [ASUS K43E-VX260R]("http://www.asus.com/Notebooks/Versatile_Performance/K43E/#specifications"): Intel Core i5 2410M, 6GB DDR3 1333MHz RAM, Intel GMA HD and a standard 5400RPM HDD. The installation of the latest daily ISO via USB went flawlessly, respecting previous (Windows/Windows Recovery) partitions, everything seems to work out-of-the-box. I'm impressed so far.  

Now to the performance: Booting is fast enough I guess (from grub to DM in about 20sec) but, between pressing <enter> after my password in Lightdm and actually seeing anything in the Compiz/Unity desktop takes about 2 minutes. glxgears (I know, not the ideal benchmark) is talking about 1000 FPS. It feels really sluggish. Is it what I should expect from this hardware? Or should I start debugging to fix whatever is causing a loss in performance?

If you could give me some idea on how your Intel-based hardware (ideally i5/HD3000) performs, it would really help me. 

Regards,
Effenberg

---

### Post by TDK800 on 2012-01-21
Experienced the same thing with Unity 3D, switched to Unity 2D, loads in 1-2 seconds.

Also, 5400 RPM HDD is a big bottleneck in your conf, try going SSD, you'll probably get 3x faster boot and shutdown times. SSD speeds up everything else too, e.g. web pages load a lot faster.


What browser score do You get with i5 on: [http://www.speed-battle.com](http://www.speed-battle.com)

---

### Post by VinDSL on 2012-01-21
> **TDK800 said:**
> What browser score do You get with i5 on: [http://www.speed-battle.com](http://www.speed-battle.com)
Don't mean to hijack this thread, but...

Is that test page accurate?!?!?!?

My results (best results):
[LIST]
[*]Chromium (15.0.874.120) = 75.59
[*]Opera-Next (12.00 alpha) = 196.17
[*]Firefox (10.0) = 354.51
[/LIST]
That's a huge difference!  :shock:

I would have sworn that Chromium is running circles around the others...

---

### Post by williejones on 2012-01-21
Intel seems to be slow on updating/upgrading their drivers for PP, or maybe it is Xorg being slow.  I use the intel I915 video and have to use acpi_ois= boot parameter to allow the backlight to work. When booting, I press Function + screen brightness down to see the screen.  My brightning keys are reversed (dim makes brighter, brighter makes dimmer).

I know that does not answer your question since you have a different Intel.  Just saying
things seem slow with Intel's progress.

---

### Post by whatthefunk on 2012-01-21
I have an Intel i5 2400 in my desktop and its ripping fast.  I run Kubuntu on this machine.  No problems at all so far.

---

### Post by teh603 on 2012-01-21
Intel chips are very weak when it comes to OpenGL rendering. I'd stick to 2D rendering just to be safe. I keep compositing and desktop effects turned off whenever I can, and the speed gain is noticeable even in Kubuntu.

---

### Post by kaldor on 2012-01-21
> **effenberg0x0 said:**
> 

Now to the performance: Booting is fast enough I guess (from grub to DM in about 20sec) but, between pressing <enter> after my password in Lightdm and actually seeing anything in the Compiz/Unity desktop takes about 2 minutes. glxgears (I know, not the ideal benchmark) is talking about 1000 FPS. It feels really sluggish. Is it what I should expect from this hardware? Or should I start debugging to fix whatever is causing a loss in performance?

If you could give me some idea on how your Intel-based hardware (ideally i5/HD3000) performs, it would really help me. 

Regards,
Effenberg

I have the slow login issue also on my main PC. Literally over a minute sometimes.

Intel graphics are very low end, but are supposed to be very stable with their open source drivers on Linux. You'll never get good 3d or HD playback, but the desktop experience should be silky smooth. Your laptop should be far more than enough to run a modern Linux distro with all the eyecandy. The login issue is probably a bug, but the glxgears is expected.

Currently, there are some known issues with screen tearing on Sandybridge. But, you should have no problems.

I used to run GNOME Shell on an old, outdated Intel machine and it ran acceptably. 

Sorry for briefness. Typing from a tablet :-)

---

### Post by effenberg0x0 on 2012-01-21
<rant>I've been working on it for the last hours, read everything I could find, tried a couple different workarounds. Looking at all these sites, threads, blogs, etc made me remember why I gave up on Linux laptops to begin with: So many years talking about battery life, eternal problems suspending/hibernating/resuming, the damned brightness and acpi issues, the lid behaviour, the LEDs that don't lit correctly, etc... Wasting time fixing everything and then see it broken once again at the next update. And always finding out that the laptop you didn't choose is the one that is fully compatible now.</rant> 

Although I think I have all the hardware working and, according to most sites I could read so far, I should be happy with the performance, it doesn't feel reasonably fast (Linux-like) at all. I guess it's time to format and try Lubuntu. Thanks for the tips guys!

Regards,
Effenberg

---

### Post by kaldor on 2012-01-21
> **effenberg0x0 said:**
> <rant>I've been working on it for the last hours, read everything I could find, tried a couple different workarounds. Looking at all these sites, threads, blogs, etc made me remember why I gave up on Linux laptops to begin with: So many years talking about battery life, eternal problems suspending/hibernating/resuming, the damned brightness and acpi issues, the lid behaviour, the LEDs that don't lit correctly, etc... Wasting time fixing everything and then see it broken once again at the next update. And always finding out that the laptop you didn't choose is the one that is fully compatible now.</rant> 

Although I think I have all the hardware working and, according to most sites I could read so far, I should be happy with the performance, it doesn't feel reasonably fast (Linux-like) at all. I guess it's time to format and try Lubuntu. Thanks for the tips guys!

Regards,
Effenberg

My laptop has been almost flawless for years. If it's just for basic, portable use, then give the HP dv2817 a go. It's old, but works great. Suspend, resume, graphics, wireless, etc. All great :-)

Point is that you might be able to find a similar model for cheap somewhere.

---

### Post by jfernyhough on 2012-01-22
There are some issues with Compiz+Unity and Intel (and fglrx). I'm following a couple of bugs...

There are a few similar/related bug reports, check these for starters (I know the first is fglrx but there are mentions of Intel graphics in there too):

**Compiz's "Sync to Vblank" makes display stutter/slow with fglrx**
[https://bugs.launchpad.net/bugs/763005](https://bugs.launchpad.net/bugs/763005)

**[regression] Moving windows lags behind the mouse by 1-2 seconds; appear to freeze when dragging**
[https://bugs.launchpad.net/bugs/764330](https://bugs.launchpad.net/bugs/764330)


You might try Daniel van Vugt's PPA for a possible fix/workaround:

[https://launchpad.net/~vanvugt/+archive/compiz](https://launchpad.net/~vanvugt/+archive/compiz)

There are some fixes in there for Oneiric that are upstream; Precise should get them whenever it's next synced. The packages install on Precise at the moment and help hugely for me, though transparency seems to be a bit borked when I run Unity. GNOME Classic+Effects (i.e. Compiz) is fine.

---

### Post by mattlach on 2012-01-22
Any Sandy Bridge intel CPU speed will be overkill.

Intel is currently leaving AMD in the dust performance wise.

In non-multithreaded benchmarks any Sandy Bridge based Intel CPU (like your i5-2410M) will on average be about 50% faster than a current AMD CPU at the same clock speed, regardless of wheter they are i3s i5s or i7s.  AMD is simply getting blown out of the water right now by Intel.  Even intels low end desktop i3-2100's are faster in single threaded performance than AMD's highest end FX-8150's

So, in non-multithreaded code, your core i5-2410m will turbo up to 2.9Ghz.  At this speed it will be equivalent to a recent AMD CPU at ~4.35Ghz.  There is no AMD cpu sold at this high speed.  Phenom II's won't typically even overclock this high.

In well threaded code or code with a lot of paralellism AMD can make up for this deficit with its higher core counts, so if your Phenom II X6 is overclocked to 4ghz or so, it may actually be faster than your mobile i5, but at stock speeds it won't be even in threaded code.

So, CPU wise the i5-2410m is overkill.

GPU wise is another matter all together.  The integrated GPU's in Sandy bridge processors are the fastest yet from Intel, but they still don't come even close to comparing to a good discrete GPU.  The HD3000 in your is plenty capable for desktop use and good even for light gaming.  I have yet to test these in Ubuntu though, so I don't know how mature the drivers are.  My previous gen Core i5-520m laptop seems to handle everything I throw at it in linux, but I don't use it for games.

---

### Post by effenberg0x0 on 2012-01-22
Hi, thank you for your inputs. Although most of the time I work on a Phenom II X6 Black Edition@3.9GHz, it rarely scales to 100% speed. Even when multitasking heavily and running a couple VMs, eclipse, etc, it won't go further than 1.7GHz. 

I am familiar with i5/i7 benchmarks and was expecting a system with the same performance or close to it. Something that feels just as snappy. 

I thought the 5400 WD HDD was the bottleneck in the comparison (the desktop uses Corsair 3 SSDs) and installed another one of these in the laptop. There was some improvement, obviously, but not as much as I was hoping to see.

I'm convinced what I feel to be slow in this laptop is GPU related. In this desktop I mentioned above, as it's my favourite machine, I have two GTS450 (sli) installed. I guess that is the main factor that causes such a performance difference. The HD3000 seems to be really weak.


> **mattlach said:**
> Any Sandy Bridge intel CPU speed will be overkill.

Intel is currently leaving AMD in the dust performance wise.

In non-multithreaded benchmarks any Sandy Bridge based Intel CPU (like your i5-2410M) will on average be about 50% faster than a current AMD CPU at the same clock speed, regardless of wheter they are i3s i5s or i7s.  AMD is simply getting blown out of the water right now by Intel.  Even intels low end desktop i3-2100's are faster in single threaded performance than AMD's highest end FX-8150's

So, in non-multithreaded code, your core i5-2410m will turbo up to 2.9Ghz.  At this speed it will be equivalent to a recent AMD CPU at ~4.35Ghz.  There is no AMD cpu sold at this high speed.  Phenom II's won't typically even overclock this high.

In well threaded code or code with a lot of paralellism AMD can make up for this deficit with its higher core counts, so if your Phenom II X6 is overclocked to 4ghz or so, it may actually be faster than your mobile i5, but at stock speeds it won't be even in threaded code.

So, CPU wise the i5-2410m is overkill.

GPU wise is another matter all together.  The integrated GPU's in Sandy bridge processors are the fastest yet from Intel, but they still don't come even close to comparing to a good discrete GPU.  The HD3000 in your is plenty capable for desktop use and good even for light gaming.  I have yet to test these in Ubuntu though, so I don't know how mature the drivers are.  My previous gen Core i5-520m laptop seems to handle everything I throw at it in linux, but I don't use it for games.

---

### Post by Gyokuro on 2012-01-24
Intel all the way but I have to admit that I'm more interested in to get out the max of batteries and therefore I deactivated all eye candy stuff. i5 is good enough for HD videos but not for gaming - for such a task a console or gamer pc is better suited. The next thing is I like Intel's open source support - as soon new hardware arrives Intel is sending patches (kernel, xorg, different libs) and they work - how long is AMD working now on their radeon driver? For more power i7 and that's a beast, workstation Xeon and everything is good - AMD died for me a long time ago.  In case more graphic power is needed - intel + nvidia but it depends on your task - I need only a shell and a browser :-)

---

### Post by fjgaude on 2012-01-24
As a retired graphic designer still working, Intel i5 is wonderful, but not for intense games. Fine for HD video. And fast, fast at CPU stuff. Get a 6+ with gtkperm. Notice my signature, again! <smile>

And Intel, in real time, supports Linux.

---

### Post by TDK800 on 2012-01-24
> **VinDSL said:**
> Don't mean to hijack this thread, but...

Is that test page accurate?!?!?!?

My results (best results):
[LIST]
[*]Chromium (15.0.874.120) = 75.59
[*]Opera-Next (12.00 alpha) = 196.17
[*]Firefox (10.0) = 354.51
[/LIST]
That's a huge difference!  :shock:

I would have sworn that Chromium is running circles around the others...

Seems about right, FireFox 10 scores on avg 368 there, FireFox 12.0a1 (nightly) scores on avg 515!!! As a very happy FireFox 12.0a1 user I can +1 that it leaves Chrome and all others in the dust.

---

### Post by xyzzyman on 2012-01-24
> **Gyokuro said:**
> Intel all the way but I have to admit that I'm more interested in to get out the max of batteries and therefore I deactivated all eye candy stuff. i5 is good enough for HD videos but not for gaming - for such a task a console or gamer pc is better suited. The next thing is I like Intel's open source support - as soon new hardware arrives Intel is sending patches (kernel, xorg, different libs) and they work - how long is AMD working now on their radeon driver? For more power i7 and that's a beast, workstation Xeon and everything is good - AMD died for me a long time ago.  In case more graphic power is needed - intel + nvidia but it depends on your task - I need only a shell and a browser :-)

bash shell and [lynx]("http://lynx.isc.org/lynx2.8.7/lynx2-8-7/lynx_help/Lynx_users_guide.html")?

---

### Post by Gyokuro on 2012-01-25
> **xyzzyman said:**
> bash shell and [lynx]("http://lynx.isc.org/lynx2.8.7/lynx2-8-7/lynx_help/Lynx_users_guide.html")?

yes - that's my environment :-) - for more light of the web I have to use chromium ;-)

---

### Post by edujose on 2012-01-25
I have a sandy bridge i5 2500 desktop for a few months now, with win7 / ubuntu 11.10 oneiric.

Graphics are smooth under Unity 3D, the desktop is perfectly usable and window movement is smooth too.

Time from login to a full desktop is about 4-5 seconds, good in my opinion.

Though my glxgears gives me a paltry 85.447 FPS, they run smoothly with no artifacts nor slowdowns when moving around the little window with the gears.

I think a sandy bridge i5 laptop with intel HD 3000 graphics should work well (better without additional AMD or NVidia GPUs, to avoid driver problems and lower power comsumption).

---

### Post by alphacrucis2 on 2012-01-25
> **jfernyhough said:**
> There are some issues with Compiz+Unity and Intel (and fglrx). I'm following a couple of bugs...

There are a few similar/related bug reports, check these for starters (I know the first is fglrx but there are mentions of Intel graphics in there too):

**Compiz's "Sync to Vblank" makes display stutter/slow with fglrx**
[https://bugs.launchpad.net/bugs/763005](https://bugs.launchpad.net/bugs/763005)

**[regression] Moving windows lags behind the mouse by 1-2 seconds; appear to freeze when dragging**
[https://bugs.launchpad.net/bugs/764330](https://bugs.launchpad.net/bugs/764330)


You might try Daniel van Vugt's PPA for a possible fix/workaround:

[https://launchpad.net/~vanvugt/+archive/compiz](https://launchpad.net/~vanvugt/+archive/compiz)

There are some fixes in there for Oneiric that are upstream; Precise should get them whenever it's next synced. The packages install on Precise at the moment and help hugely for me, though transparency seems to be a bit borked when I run Unity. GNOME Classic+Effects (i.e. Compiz) is fine.


I have found that Daniel's PPA has greatly sweetened the behaviour of compiz/unity on my laptop running Oneiric.

---

### Post by effenberg0x0 on 2012-01-26
> **alphacrucis2 said:**
> I have found that Daniel's PPA has greatly sweetened the behaviour of compiz/unity on my laptop running Oneiric.
There are many posts that mention his PPA but I couldn't find an explanation: What is different in his build of Compiz/Unity that produces an improvement in this specific hardware? Many of his fixes are merged. 
Regards,
Effenberg

---

### Post by alphacrucis2 on 2012-01-26
> **effenberg0x0 said:**
> There are many posts that mention his PPA but I couldn't find an explanation: What is different in his build of Compiz/Unity that produces an improvement in this specific hardware? Many of his fixes are merged. 
Regards,
Effenberg

Well he seems to be a bit ahead as far as the 11.10 repos go. As soon as I started using it an annoying problem where there was a 30% chance of compiz going awol when skype started stopped happening. I also notice there seems to be better stability and less occurrence of weird window behaviour related to the unity bar icon states. It may be that many of the issues I had previously noted are already fixed in the main repos but I wouldn't know as I haven't been running vanilla for a while.

---

