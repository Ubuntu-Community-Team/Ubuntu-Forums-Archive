---
title: "Alpha 3 and daily build don't boot properly"
date: 2012-08-01
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by GreatEmerald on 2012-08-01
I wanted to test the latest Ubuntu builds to see if there are any improvements for my Poulsbo hardware in the latest kernels, and it seems that I've struck a rather nasty regression. I tried three Ubuntu images so far, and the two latest ones don't even boot on my machine.

When I attempt to launch the LiveCD, the screen turns off and no input is accepted. Unfortunately, that also makes is difficult to find out what goes wrong. I even tried booting into runlevel 3, and it didn't help, either. All I can see is the first two lines that appear when I try to  launch the LiveCD, and just when the VGA mode is about to be set to a  new value, the screen goes dark, with no input being accepted.

I tested Alpha 3 and today's daily build, and both have this problem. On the other hand, Alpha 1 works just fine (or, well, as fine as it gets on this hardware so far).

The machine I'm testing this on is a Fujitsu Stylistic Q550 tablet, an Intel Oak Trail device. Since the graphics chip has always been trouble on these devices, I suspect that this problem has to do with the kernel updates, but then it strikes me as odd that it would fail like that even when I'm attempting to boot to runlevel 3.

Anyone else having this kind of a problem? Any way to find out what exactly is the cause of it? I guess I'll also try Alpha 2 and see if it worked or not, and perhaps the betas of other distributions, to see if the problem may be related to userspace after all.

EDIT: Apparently, Alpha 2 is no longer available. Hmm.

---

### Post by balloons on 2012-08-01
> **GreatEmerald said:**
> I wanted to test the latest Ubuntu builds to see if there are any improvements for my Poulsbo hardware in the latest kernels, and it seems that I've struck a rather nasty regression. I tried three Ubuntu images so far, and the two latest ones don't even boot on my machine.

When I attempt to launch the LiveCD, the screen turns off and no input is accepted. Unfortunately, that also makes is difficult to find out what goes wrong. I even tried booting into runlevel 3, and it didn't help, either. All I can see is the first two lines that appear when I try to  launch the LiveCD, and just when the VGA mode is about to be set to a  new value, the screen goes dark, with no input being accepted.

I tested Alpha 3 and today's daily build, and both have this problem. On the other hand, Alpha 1 works just fine (or, well, as fine as it gets on this hardware so far).

The machine I'm testing this on is a Fujitsu Stylistic Q550 tablet, an Intel Oak Trail device. Since the graphics chip has always been trouble on these devices, I suspect that this problem has to do with the kernel updates, but then it strikes me as odd that it would fail like that even when I'm attempting to boot to runlevel 3.

Anyone else having this kind of a problem? Any way to find out what exactly is the cause of it? I guess I'll also try Alpha 2 and see if it worked or not, and perhaps the betas of other distributions, to see if the problem may be related to userspace after all.

EDIT: Apparently, Alpha 2 is no longer available. Hmm.

Check again, Alpha 2 is back up.. hang onto your alpha 1 image. Let me know the outcome of alpha 2 and we'll try and pin down when this regressed.

---

### Post by GreatEmerald on 2012-08-01
All right, tried it, and Alpha 2 is regressed as well. I also tried openSUSE 12.2 RC1, and it worked fine in VESA mode (they don't have gma500_gfx built in the kernel, it seems). But then it uses kernel 3.4, same with Quantal Alpha 1. I'll see if I can test another distribution with kernel 3.5 in the mean while.

---

### Post by ventrical on 2012-08-01
Todays daily zsync works just beautiful.!

---

### Post by GreatEmerald on 2012-08-01
I now built myself an image of openSUSE with kernel 3.5.0, and it works fine (with VESA again... Hmm, perhaps I should write them a message that they should build gma500_gfx by default...). So it's probably not a kernel problem after all. Though it would be nice to also see what happens in a distribution where the video driver is enabled and that has the 3.5 kernel, anyway. I just can't think of such a distribution that would have that at this point, though. I might end up compiling such a kernel myself if I can't find one precompiled, then...

---

### Post by balloons on 2012-08-01
Hmm, well interesting.. So alpha 1 with 3.4 works, yet it doesn't seem to be a 3.5 kernel issue? SUSE might have a patch for your hardware -- can you open a bug on this anyway and mention your results? There might be something we can pick up into the 3.5 patch.

---

### Post by GreatEmerald on 2012-08-31
Did some testing today and it's still the same, it won't boot. However, I did get a bit further this time. Strangely enough, if I add "gma500_gfx.anytexthere=anyvaluehere", I get a bit further. It still won't give me the X server, but at least I get to runlevel 3. The odd thing is that it doesn't matter what the parameter and the value is, just that it's there.

Also, when it boots to the point where it's supposed to be starting the X server, it just flickers to a black screen a bit, and then falls back to tty1. And if I add a "vga=ask" parameter, it freezes when it gets to starting the X server (and the input freezes as well).

So overall it would seem to be related to gma500_gfx module.

---

### Post by GreatEmerald on 2012-09-02
Just tested on Gentoo with the 3.6.0-rc3 kernel, and the problem is there as well. It's nearly identical, although the trick with setting a parameter doesn't work.

If I can get Icecream or distcc working, I will do a bisect and see what change broke it.

---

