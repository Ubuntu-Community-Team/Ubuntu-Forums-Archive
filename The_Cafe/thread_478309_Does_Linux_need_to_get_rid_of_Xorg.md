---
title: "Does Linux need to get rid of Xorg?"
date: 2007-06-19
forum: The Cafe
---

### Post by FuturePilot on 2007-06-19
I'm just curious of what others think about Xorg Xserver. It seems to me that Xorg has this slight sluggishness to it. I'd even hate to say this, but the graphical environment doesn't seem quite as snappy as Windows does. For example, when I switch tabs in Firefox in Linux, there's like a 1/2 to 1 second delay before it switches, whereas on Windows the switch is immediate without the slightest delay. Now maybe that's something totally unrelated to Xorg and maybe it's just a Firefox thing. But Xorg just seems to have a slight slowness to it. Maybe I'm wrong, but could this slowness be due to the fact that it's running as a layer?

What I'm wondering is if Xorg is able to handle the demands we're placing on it these days with all the compositing and stuff? Should Linux move towards a built in graphical environment? I know there's certain advantages to to running the graphical environment as a layer, such as a program freezing won't take the whole system down with it. Or would the disadvantages of a built in graphical environment out weigh the advantages?

---

### Post by starcraft.man on 2007-06-19
IMO, the xorg is fine to me. I edit it all the time and really like the easy control I get with it. I haven't seen any slow down in switching tabs in firefox. I definitely _don't_ want an integrated graphical environment like Windows, that is one of Windows worst problems (leading of course to the well known BSoD in lots of cases). The ease with which we can drop in and out environments makes it amazing to use I think and if we lose that were losing something that makes us great.

---

### Post by Johnsie on 2007-06-19
It might depend on your graphics card and other hardware how snappy it is. For me it works ok on some computers and not on others. I've heard there are some big changes to Xorg in the upcoming version of Ubuntuu which might address a few problems

---

### Post by FuturePilot on 2007-06-19
> **starcraft.man said:**
> IMO, the xorg is fine to me. I edit it all the time and really like the easy control I get with it. I haven't seen any slow down in switching tabs in firefox. I definitely _don't_ want an integrated graphical environment like Windows, that is one of Windows worst problems (leading of course to the well known BSoD in lots of cases). The ease with which we can drop in and out environments makes it amazing to use I think and if we lose that were losing something that makes us great.

True. I do like that you can drop down to a tty if needed. And I can think of a lot of advantages of using Xorg, but this little lag.....:(

---

### Post by Canis familiaris on 2007-06-19
You use the vesa driver or acclerated intel/nvidia/ati driver? I think this "sluggish behaviour" may be due to your Xorg drivers.

---

### Post by 23meg on 2007-06-19
[QUOTE=FuturePilot]It seems to me that Xorg has this slight sluggishness to it. I'd even hate to say this, but the graphical environment doesn't seem quite as snappy as Windows does.[/QUOTE]

This is true regarding certain windowing operations; it does feel like that in practice, even though this has been debunked in technical terms in a few places. Window resizing, repaints (especially during workspace switching) and some other operations can be slow, but to the best of my knowledge, this also has to do with performance bottlenecks that widget toolkits introduce, not just X itself. It's also due to bad coding practices of application developers sometimes.

In any case, there's a lot of room for improvement in the 2D drawing acceleration area, but there are a lot of reasons to be optimistic for the near future as well. Once the Glitz backend is coupled with Xrender and drivers that support it have matured, the problem will be solved.

But getting rid of X instead of fixing its shortcomings is simply a ridiculous idea, which luckily is impossible to happen. 

(Pedant note: X isn't specific to Linux; it's used in many other platforms such as BSD, Solaris, MacOS and other proprietary UNIX-like systems.)

---

### Post by Circus-Killer on 2007-06-19
are you sure it Xorg's fault? what about the desktop environment (gnome/kde)?

if you having sluggish performance, and you cant afford better hardware, why not try a more lightweight desktop environment such as xfce or fluxbox.
maybe try XuBuntu....or the other derivitive that uses fluxbox (dont know what its called).
or just install either from within ubuntu. but i honestly dont think that xorg is the problem. (just an opinion, could be wrong).

---

### Post by FuturePilot on 2007-06-19
Ok well then maybe we should fix it instead of getting rid of it. I hope the newer release keep improving. So there is hope:)
I don't think it's hardware related. I use the Nvidia driver with a GeForce 6600, 2 GB RAM and a Pentium 4 HT @ 3.4 GHz

---

### Post by frodon on 2007-06-19
> **FuturePilot said:**
> I'm just curious of what others think about Xorg Xserver. It seems to me that Xorg has this slight sluggishness to it. I'd even hate to say this, but the graphical environment doesn't seem quite as snappy as Windows does. For example, when I switch tabs in Firefox in Linux, there's like a 1/2 to 1 second delay before it switches, whereas on Windows the switch is immediate without the slightest delay. Now maybe that's something totally unrelated to Xorg and maybe it's just a Firefox thing. But Xorg just seems to have a slight slowness to it. Maybe I'm wrong, but could this slowness be due to the fact that it's running as a layer?This not related to xorg, firefox is a slow program in general and especially on linux, try epiphany if you are not convinced.


> **FuturePilot said:**
> What I'm wondering is if Xorg is able to handle the demands we're placing on it these days with all the compositing and stuff? If you compare to the resources needed for aero vista effects which provide 0.5% of what beryl provides to the ressource of the so called beryl then i would answer yes to your question without any kind of doubt.

In my mind 2D drawing effect performances are more related to the window manager than xorg. I suggest you to do a simple and install xfwm4 then use it instead of metacity. You will see that metacity (the gnome WM) is just more ressource eater than xfwm4. So for me your point is more related to the WM than xorg.

---

### Post by forrestcupp on 2007-06-19
> **Anurag_panda said:**
> You use the vesa driver or acclerated intel/nvidia/ati driver? I think this "sluggish behaviour" may be due to your Xorg drivers.

+1

Are you sure you're using the best video card drivers?  Or maybe is your system slow/old enough that maybe you should be using a more lightweight DE instead of gnome or KDE?

I don't experience any problems at all, and my tab switching is instantaneous.

---

### Post by prizrak on 2007-06-19
X server idea is pretty cool on machines that might be running headless with remote GUI (I done that before was loads of fun), but I do think that a simpler application would be better. I am not talking about an integrated GUI like Windows has but perhaps just an application that would run on top of the shell like X server does except it won't be a server-client application. Of course I don't know enough about those things so my idea is likely idiotic :)

---

### Post by FuturePilot on 2007-06-19
> **frodon said:**
> This not related to xorg, firefox is a slow program in general and especially on linux, try epiphany if you are not convinced.


If you compare to the resources needed for aero vista effects which provide 0.5% of what beryl provides to the ressource of the so called beryl then i would answer yes to your question without any kind of doubt.

That's what I though. Firefox does seem slower on Linux. And I do see your point about the compositing. Beryl provides way more than Aero does, and when you compare that to the resources it is clear.:)

---

### Post by starcraft.man on 2007-06-19
> **FuturePilot said:**
> True. I do like that you can drop down to a tty if needed. And I can think of a lot of advantages of using Xorg, but this little lag.....:(

I was actually also referring to how we can swap environments so easy too. Like installing xfce or fluxbox if you want and removing em just as easy. If the desktop environment was integrated like Windows, that would be very difficult to impossible to do no? I mean just look at all the poor hacks on top of Windows people try to sell... It is good we have so many options to get to a console though :).

> **FuturePilot said:**
> That's what I though. Firefox does seem slower on Linux. And I do see your point about the compositing. Beryl provides way more than Aero does, and when you compare that to the resources it is clear.:)

You know, I don't think its fair to compare Beryl to Aero... it just makes MS look so bad, I almost feel sorry for the Windows users paying 400$ for an inferior DM/WM. I mean I have even heard that some people with motion sickness apparently get nautious after too many hours using Vista (with full effects), I dunno why...

Anyway, go xorg. I hope the new version turns out great.

---

### Post by FuturePilot on 2007-06-19
> **starcraft.man said:**
> I was actually also referring to how we can swap environments so easy too. Like installing xfce or fluxbox if you want and removing em just as easy. If the desktop environment was integrated like Windows, that would be very difficult to impossible to do no? I mean just look at all the poor hacks on top of Windows people try to sell... It is good we have so many options to get to a console though :).
Yes, you made a good point. It would be difficult to switch your DE if the GUI was integrated. I really do like the way things are now, it's just that this lag was bugging me.

---

