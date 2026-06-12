---
title: "3D Boot"
date: 2009-02-02
forum: The Cafe
---

### Post by tom72 on 2009-02-02
Hi,
I'm tired of watching the boring old graphical boot loader with a two dimensional, low res image. That's soo 20th century. I'd really like to see a 3D boot loader on my screen, maybe a rotating cube or something. That should be really possible.

Does anyone know if such a project exists? I've googled a bit, but was unsuccessful.

/tom

---

### Post by lukaszr on 2009-02-02
i doubt it exists because not many people really care what their boot looks like. You can have all those special graphical effects once you log in. Whats the point on increasing boot time to have a 3d cube? The point its all 2d text base is to increase the load time. Having more graphic images or effects would require more system resources...which would increase load time.

---

### Post by DeadSuperHero on 2009-02-02
I think what would need to be done effectively is to have the system load the graphics driver and start the X server before the loading screen comes up. 
 
Alternatively, one could have Coreboot (which is embedded linux) have some kind of Cairo-based libraries run alongside a 3D driver and start a sort of "in-between" Xserver to run basic graphics and work as a bootloader.
 
Just a theory, though. What I'd like to see is a bootloader/loading screen that smoothly transitions into the GDM/KDM, which could then be capable of simple animations. With that working, it would be nice to see some simple animations as you log in, and the default desktop compositors (Kwin, Compiz Fusion, etc.) could smoothly start without any delays whatsoever.
 
Again, just theorizing.

---

### Post by smartboyathome on 2009-02-02
No project exists for that, and it would be very hard to do this short of modifying the new Fedora bootloader to use your hardware to generate 3D (which graphics cards still have problems with).

---

### Post by DeadSuperHero on 2009-02-02
> **smartboyathome said:**
> No project exists for that.
 
No such project exists for that...yet! :D

---

### Post by Sand &amp; Mercury on 2009-02-02
I like having no bootscreen at all. It's strangely entertaining watching all the console messages speeding up the screen.

---

### Post by tom72 on 2009-02-02
Hm all good points. In general I was thinking that today we really should have some more fancy boot loaders. It's not important allright but: Why not?
It shouldn't take up too many resources, if you consider that with some direct memory addressing can achieve a lot (have a look at the tiny <10k intros and demos on those demo sites). I don't want to dive too deeply into the details but my point is that some low level routines that are quick too load and don't depend much on other higher level layers such as the X window system could probably work. Of course all set up with some fall back loaders just in case the graphics card doesnt like it.
Nowadays the systems usually have quite a lot of resources. Standard systems with 4GB of RAM, really fast graphics cards and whatsoever. Maybe it's possible to develop something independent of X, like a tiny low level application running before the main boot process?

---

### Post by lukaszr on 2009-02-02
> **Sand & Mercury said:**
> I like having no bootscreen at all. It's strangely entertaining watching all the console messages speeding up the screen.

same here. 
i like seeing whats loading and what error messages (if any) i get. i like knowing whats going on in the background. i could care less for a nice pretty splash screen lol.

---

### Post by FuturePilot on 2009-02-02
I think this would be very difficult to do seeing that you would have to initialize the entire graphics system very early in the boot process.

---

### Post by tom72 on 2009-02-02
I remember when the first 3D demos on PCs came out using DOS. No Windows (excuse my french), no drivers. That must have been the late 80's early 90's. They took a few seconds to load but showed quite impressive 3D stuff. With todays hardware it should take less than a second to load such a program. 8)

---

### Post by bash on 2009-02-02
Well Fedora's new Plymouth utilising KMS will bring some bling to the boot-loading process.

---

### Post by Mr. Picklesworth on 2009-02-02
There is absolutely no point whatsoever to having a 3D boot graphic be rendered in real time since it is always the same.

---

### Post by eragon100 on 2009-02-02
Why don't you use set your boot screen to be a 3d image, and then use a 3d glasses to watch it? I know it's a bit cumbersome, but wouldn't that do the trick? :wink:

---

### Post by mips on 2009-02-02
> **eragon100 said:**
> Why don't you use set your boot screen to be a 3d image, and then use a 3d** brill **to watch it?

lol, I doubt english speaking people (or other languages) will understand 'brill'.

---

### Post by jeffjanzen on 2009-02-02
> **tom72 said:**
> I remember when the first 3D demos on PCs came out using DOS. No Windows (excuse my french), no drivers. That must have been the late 80's early 90's. They took a few seconds to load but showed quite impressive 3D stuff. With todays hardware it should take less than a second to load such a program. 8)

hells yes! DOS kicked some serious ***.  id software made smart, efficient use of the limited computing power most people had in the 90's.  i mean, where the hell does all of our processing power go these days?  quake ran on a 486 with 4MB of RAM!! we can have a 3d bootloader--or at least, 3d-looking. as Mr. Picklesworth said, there's no need for real-time 3d rendering.  just give us a 2d animated 16-bit-colored 3d something-or-other. **id** could do it.

oh, and Merriam-Webster.com says:
> Brill: a European flatfish

:confused:

---

### Post by MaxIBoy on 2009-02-02
Since the graphics card drivers are compiled into the Linux kernel, you'd have to boot an entire Linux distro just to get 3D acceleration. So first you boot Linux, just to get some 3D effects, then you boot Linux *again* so you can actually use it.

Pointless.

---

### Post by tom72 on 2009-02-02
True. Unless you're not using the drivers. However I don't have any idea on how to do this ;)
The Fedora Plymouth boot looks quite nice though, way better than the old standard boot screen :)

---

### Post by eragon100 on 2009-02-02
I meant glasses, not brill.

Anyway, wouldn't Kernel Mode Setting allow for this somehow?

---

### Post by miggols99 on 2009-02-02
> **Mr. Psychopath said:**
> I think what would need to be done effectively is to have the system load the graphics driver and start the X server before the loading screen comes up. 
 
Alternatively, one could have Coreboot (which is embedded linux) have some kind of Cairo-based libraries run alongside a 3D driver and start a sort of "in-between" Xserver to run basic graphics and work as a bootloader.
 
Just a theory, though. What I'd like to see is a bootloader/loading screen that smoothly transitions into the GDM/KDM, which could then be capable of simple animations. With that working, it would be nice to see some simple animations as you log in, and the default desktop compositors (Kwin, Compiz Fusion, etc.) could smoothly start without any delays whatsoever.
 
Again, just theorizing.
Didn't Fedora already try this? And their boot times were slooooow. They've changed to something much better now. Can't remember what it's called though.

---

### Post by K.Mandla on 2009-02-02
I suppose you could insert a series of images that appeared to be a spinning cube, instead of a true one. That would certainly be possible.

I have to agree with those who find the idea less than enticing though. Gimmicky loaders slow things down, and unfortunately I am addicted to fast startups.

---

### Post by LinuxGuy1234 on 2009-02-02
> **K.Mandla said:**
> I suppose you could insert a series of images that appeared to be a spinning cube, instead of a true one. That would certainly be possible.

I have to agree with those who find the idea less than enticing though. Gimmicky loaders slow things down, and unfortunately I am addicted to fast startups.

I agree with this idea. It's so good to see the kernel boot messages too...

---

### Post by smartboyathome on 2009-02-02
> **eragon100 said:**
> Anyway, wouldn't Kernel Mode Setting allow for this somehow?

It would most definitely be able to support this if it had the right drivers supporting it. In fact, Fedora has something like this (but 2D) included right now, but so few users can use it due to the drivers not being compatible yet that it isn't as noticed. Only hangup I would see is in how slow it would be on some graphic cards. For example, up until the Intel 2.6.1 driver, it didn't support GEM, and thus had very poor performance with 3D. Now, it has got better performance, but it still is very wimpy compared to NVidia and ATI with their proprietary driver.

---

### Post by MaxIBoy on 2009-02-02
> **MaxIBoy said:**
> Since the graphics card drivers are compiled into the Linux kernel, you'd have to boot an entire Linux distro just to get 3D acceleration. So first you boot Linux, just to get some 3D effects, then you boot Linux *again* so you can actually use it.

Pointless.
A little clarification to what I posted earlier:

Yes, I know you could use software rendering with the framebuffer, but that could be even slower than booting twice in a row without framebuffering. 

Although, maybe this could be remedied by someone from the demoscene...

---

### Post by Polygon on 2009-02-02
so what your wanting is to add like 20-60 seconds to the boot process? ill pass.

---

### Post by f37u5g0d on 2009-02-02
I think that the only reason you feel that you need to see something slick and entertaining is because your system takes too long to boot as it is.  I suggest to the ubuntu community that they try to make ubuntu boot faster (I've heard this is planned for 9.04).  However I am not against what was mentioned earlier about making things a more smooth transition.  I know when I boot ubuntu my screen flickers 4 or 5 times from black, to text, to the random tan background before the gdm, to the gdm, then when I log in it slides the gnome-panel down, get stuck 95% of the way down, flickers, dissappears, and then re-appears because compiz started.  My mouse does the same thing because I have a custom theme installed.  I think it gives ubuntu a shoddy look.  Once compiz is running though its' better looking than vista :)

---

### Post by Polygon on 2009-02-02
> **f37u5g0d said:**
> I think that the only reason you feel that you need to see something slick and entertaining is because your system takes too long to boot as it is.  I suggest to the ubuntu community that they try to make ubuntu boot faster (I've heard this is planned for 9.04).  However I am not against what was mentioned earlier about making things a more smooth transition.  I know when I boot ubuntu my screen flickers 4 or 5 times from black, to text, to the random tan background before the gdm, to the gdm, then when I log in it slides the gnome-panel down, get stuck 95% of the way down, flickers, dissappears, and then re-appears because compiz started.  My mouse does the same thing because I have a custom theme installed.  I think it gives ubuntu a shoddy look.  Once compiz is running though its' better looking than vista :)

ubuntu's boot sequence for me is faster and more professional looking the vista's. 

vista, it flickers when it goes from the windows logo to the logon screen, then, when you enter your password, it flickers again to black, shows your wall paper, then goes back to the green 'Logging in..." screen, then it actually gets to the desktop and starts loading the icons, and usually flickers to black for half a second there too.

---

### Post by Frak on 2009-02-02
Closest thing to this is what Fedora uses now for boot.

---

### Post by 4th guy on 2009-02-03
[QUOTE=jeffjanzen;6663907]hells yes! DOS kicked some serious ***.  id software made smart, efficient use of the limited computing power most people had in the 90's.  i mean, where the hell does all of our processing power go these days?  quake ran on a 486 with 4MB of RAM!! we can have a 3d bootloader--or at least, 3d-looking. as Mr. Picklesworth said, there's no need for real-time 3d rendering.  just give us a 2d animated 16-bit-colored 3d something-or-other. **id** could do it.QUOTE]Can you please give me some examples?

---

### Post by jeffjanzen on 2009-02-04
> **f37u5g0d said:**
> I think that the only reason you feel that you need to see something slick and entertaining is because your system takes too long to boot as it is.

YES.  currently, long boot times are boring.  if there was something entertaining going on *during* startup, it wouldn't be as boring.  heck, i wouldn't mind adding 30 seconds to the boot time if i could watch a funny cartoon or play asteroids or something while it was booting, you know?

> **4th guy said:**
> Can you please give me some examples?

well, quake was my primary example of efficient use of hardware to produce a nice-looking, high-framerate 3d environment. (and before quake, there was hexen, heretic, doom, wolfenstein 3d...)  but forget quake. it was actually rendering in real-time.  lots of people would be satisfied with 2d animation in this case. much simpler and less demanding.

---

### Post by smartboyathome on 2009-02-05
> **jeffjanzen said:**
> YES.  currently, long boot times are boring.  if there was something entertaining going on *during* startup, it wouldn't be as boring.  heck, i wouldn't mind adding 30 seconds to the boot time if i could watch a funny cartoon or play asteroids or something while it was booting, you know?

Red Hat had something like this in their old distro. It is called RHGB (Red Hat Graphical Boot), and it added a minute to the boot time just to provide what you mentioned.

---

### Post by MaxIBoy on 2009-02-05
> **pmicheal said:**
> Is this possible to change Windows XP boot screen to a rotating 3d logo?
Technically, yes. In most countries, though, Windows XP cannot be modified without breaking the law. And even if you don't get arrested, you'll probably get sued to the tune of way too much money. Which is kinda sad, because MS has been trying to dump XP for a while now.

---

