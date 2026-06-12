---
title: "Multiple Monitors and Productivity"
date: 2007-03-04
forum: The Cafe
---

### Post by warlock_handler on 2007-03-04
How many monitors do you have?

I am a coder, uses to use win xp till end 2006.. 2007 was my redemption year... and I became a Luser (Linux user) and after few days of testing I settled with uBuntu... I used to have a multiple monitor setup on Win XP but after the uBuntu i didnt have much time to setup my second monitor, so here I am to ask for tips/tricks while using multiple monitors... help me guys

---

### Post by jenhsun on 2007-03-04
Try this one
[http://synergy2.sourceforge.net/](http://synergy2.sourceforge.net/)

Or from your synaptic package manager, type

synergy

to search and install. this software can control both xp and linux, cross-platform.

I have 4 pc, 4 monitor with only one keyboard and mouse.
Copy and paste strings to and from xp or Linux.
Oh, of course. You need a router too.


Very good utility, you better try. :guitar:

---

### Post by kerry_s on 2007-03-04
Twin view is a cinch if you have nvidia, you just install the driver and run> sudo nvidia-xconfig --twinview
done.
gksu nvidia-settings <-nvidia gui settings editor, for fine tunning.

---

### Post by RandomJoe on 2007-03-04
Actually, I have FOUR monitors on my desktop, but the poll only went to three... :)  Okay, the fourth isn't normally used - it's the projector for movie-watching!

It really is pretty simple to set up, although it's a LOT easier if the cards are all the same.  I have had some real annoyances getting multi-head working when one of the heads is an on-motherboard output (all Dells), some silly tricks are sometimes needed when initially getting things set up.

My 4-head setup is two dual-head nVidia cards, once I figured out what I was doing wrong (which wouldn't have taken so long had I bothered to RTFM) it was a snap to get things going.  I didn't use TwinView, though - just Xinerama to get a single continuous desktop.  I might play with that one of these days...

---

### Post by kerry_s on 2007-03-04
> **RandomJoe said:**
> Actually, I have FOUR monitors on my desktop, but the poll only went to three... :)  Okay, the fourth isn't normally used - it's the projector for movie-watching!

It really is pretty simple to set up, although it's a LOT easier if the cards are all the same.  I have had some real annoyances getting multi-head working when one of the heads is an on-motherboard output (all Dells), some silly tricks are sometimes needed when initially getting things set up.

My 4-head setup is two dual-head nVidia cards, once I figured out what I was doing wrong (which wouldn't have taken so long had I bothered to RTFM) it was a snap to get things going.  I didn't use TwinView, though - just Xinerama to get a single continuous desktop.  I might play with that one of these days...


Did you read the part on panning, i just learned about it after reading the manual. It's like sliding around a window, i been playing with different sizes, i can simulate a super wide screen or just plain huge, so its like like having extra monitors, it's cool and annoying at the same time, but a very handy feature.
I'm only panning my small 15" right now.
I have 1 15" and 1 18", 15's on the left 18's on the right.
15" max=1280x1024
18" max=1600x1200

```
    Option         "MetaModes" "1280x1024 @1600x1024, 1280x1024"
```

For panning you just use the @ to specify the new size, you can not pan lower than the actual size.
Example:

1600x1200 @1600x1024 <- can not, cause lower than the 1200 base
1600x1200 @1940x1400 <- can

It's just 1 of those things that's interesting to play with. :)

---

### Post by kevinf311 on 2007-03-04
Well, I chose two LCD. My setup is really one 15" LCD and one TV (can't remember the size... a good bit bigger than my monitor though).

I use Twinview to handle it, but I just tweaked the xorg.conf file myself. Didn't think about the config utility.

Both are in 1024x768 I use the TV for watching movies and editing pictures in Gimp. I find it very useful because it doubles the amount of space I have. Especially when watching movies. I can fullscreen the video and still have my monitor to work on. The only problem I had was getting the scale effect on Beryl to only show up on my 15" monitor. I got it, but I'm not really sure how... the last thing I changed made it work, but doesn't really jive with anything the scale option should handle. 

I thought about putting the TV in a more "TV friendly" resolution, but I hate the size change windows have when you drag across heads.

---

### Post by warlock_handler on 2007-03-04
> **kerry_s said:**
> Did you read the part on panning, i just learned about it after reading the manual. It's like sliding around a window, i been playing with different sizes, i can simulate a super wide screen or just plain huge, so its like like having extra monitors, it's cool and annoying at the same time, but a very handy feature.
I'm only panning my small 15" right now.
I have 1 15" and 1 18", 15's on the left 18's on the right.
15" max=1280x1024
18" max=1600x1200

```
    Option         "MetaModes" "1280x1024 @1600x1024, 1280x1024"
```

For panning you just use the @ to specify the new size, you can not pan lower than the actual size.
Example:

1600x1200 @1600x1024 <- can not, cause lower than the 1200 base
1600x1200 @1940x1400 <- can

It's just 1 of those things that's interesting to play with. :)

Interesting this is something i feel like trying... will tell you what happened after I did that...

---

### Post by spockrock on 2007-03-04
I have 3 pcs and 4 monitors on my desk :\ what do I pick lol, and yes I use synergy across the 4 monitors.....

---

### Post by ~LoKe on 2007-03-04
Dual monitors and could not live without them.

---

### Post by Enigmus on 2007-03-04
My desk only has enough room for one, so I use a KVM Switch since that suits my needs better than multiple monitors does.

---

