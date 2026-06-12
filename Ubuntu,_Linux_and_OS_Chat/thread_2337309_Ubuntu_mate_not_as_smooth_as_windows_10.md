---
title: "Ubuntu mate not as smooth as windows 10"
date: 2016-09-16
forum: Ubuntu, Linux and OS Chat
---

### Post by 0wafi0 on 2016-09-16
Hey there guys,

I have been playing around with ubuntu for a little bit. I am running it on a dual boot alongside windows 10 on my laptop. I have an ASUS UX305UA with a core i7-6500u skylake, Intel HD graphics 520 and 8 gb of ram 256 gb ssd.

I really wanted to make the change to ubuntu-Mate but what's been pulling back from that was how ubuntu-mate is not running as smooth as windows 10. For me responsiveness and user experience is important. I have disabled the cpu scaling, configured the fn keys as much as possible, decreased the swappiness and seem to have done all of it by the book, however I don't feel the gui is as smooth as the windows one. when I scroll in chrome is not as smooth when I do so in windows, and although windows 10 may have a lot of bells and whistles, I still like its buttery smooth GUI.

Now I am wondering is should I try other distros? If so which ones would you recommend for my situation?

---

### Post by oldrocker99 on 2016-09-16
MATE is pretty lightweight, but you can try Lubuntu or Xubuntu, which use the LXQT and XCFE desktops respectively. It is true that Windows runs pretty well on low-powered devices, but then so does Linux. I run Ubuntu MATE on my cheapo Toshiba laptop, and it runs pretty smoothly for what it is.

---

### Post by ian-weisser on 2016-09-16
I'm not sure I understand your 'situation'.
What do you mean by 'not running as smooth'? Jittery? Freezing? Slow?

Have you checked dmesg and syslog for clues?

---

### Post by QIII on 2016-09-16
With those specs, even Unity should be fine.  No need for a lighter DE.

I'm with ian-weisser: we need objective data to make any sort of recommendation.

---

### Post by Geoffrey_Arndt on 2016-09-16
Mate is a great desktop (as was Gnome2, which it's based on).    IF by "smooth" - - do you mean polished and avant (modern)?    The best looking and polished desktops in Linux as of 2016 are Gnome3, KDE and Unity.   These have built in effects enabled, and many finishing touches.

I think I would start out with _Unity as the flagship product of Ubuntu_, and also try Koraraa which uses an especially nice version of Gnome3.      KDE on Mint or on Open Suse is also worth a look with it's Plasma 5 Desktop.

My personal favorite on a moden machine is Unity as I love it's good looks combined with it's elegant-functionality.    The HUD, the Dash, it Scopes  . . . set it apart and make it both easy to learn and productive out of the box (provided one doesn't have their head wrapped around the old & stale (imho) start menu metaphor).

On a light machine, I like Xubuntu with XFCE - - but it is a _plain spartan_ type of DE that's stable and very configurable.

---

### Post by wildmanne39 on 2016-09-16
I use Ubuntu Mate on a laptop with a lot less resources then yours and it works great and looks good. Like the last post said if you want newer fancy desktops then Unity and Gnome3 may be what you are looking for.

---

### Post by kurt18947 on 2016-09-17
I agree with Geoffrey_Arndt & Wildman. Ubuntu Mate I think is intended to have sort of a  retro feel. It came about as an effort to preserve the classic panel and drop down menu feel of Gnome 2 when Gnome introduced Gnome 3 which was a substantial departure from Gnome 2, comparable IMO to the change from Windows 7 to Windows 8. I don't know that any of the Linux desktops are as jarring as the Windows 7 -> 8 transition. I don't have much experience with either Unity or KDE but KDE in particular is well regarded by its users for its quality and modern-feeling desktop and artwork. It might be worth trying those with a live USB and see if they suit your fancy. Xubuntu uses a classic menu and panel desktop sort of like Ubuntu Mate but Xubuntu lends itself to user tweaking. Unity and Ubuntu-Gnome can be modified to some degree but I don't know if it's as easy as XFCE/Xubuntu.

---

### Post by Bucky Ball on 2016-09-17
*Thread moved to **Ubuntu, Linux and OS Chat**.*

You can try any *buntu from the install media you create from the ISO without changing your hard drive. Suggest you do so and see what you like, what suits your workflow. 

Only you are going to know what works for you. Impossible for anyone else to answer that. Best way to find out is try them all! I use Xubuntu-core 16.04 on all machines. I don't need bells and whistles. I like to not notice the computer too much when I'm using a computer, if that makes sense. Just want to 'get it done'.

Before that I was using the Ubuntu minimal install with xfce4 desktop. Even lighter.

My desktop has a 6700 processor and 16Gb of RAM so Xubuntu-core flies ...

Have fun. :)

---

### Post by 0wafi0 on 2016-09-18
thanks a lot for all the reply...I really loved ubunt mate for it's design...it look pretty to me and the colours popped...but the smooth scrolling wasnt on par and compiz was glitchy..I have sine then tried elementary os which is nice looking but no smooth scrolling...ended up switching to ubuntu...I think I'l stick with unity and just tweaking it accordingly

---

### Post by kurt18947 on 2016-09-18
> **0wafi0 said:**
> thanks a lot for all the reply...I really loved ubunt mate for it's design...it look pretty to me and the colours popped...but the smooth scrolling wasnt on par and compiz was glitchy..I have sine then tried elementary os which is nice looking but no smooth scrolling...ended up switching to ubuntu...I think I'l stick with unity and just tweaking it accordingly

There is one benefit to unity - the entire stack is supported for 5 years, I believe.

---

### Post by montag dp on 2016-09-18
It sounds like a video problem to me. I know that support for Skylake in Linux can still be a little flakey depending on the kernel and firmware version. So what kernel and Intel video firmware are you on? It might worth trying to upgrade them if possible and see if it makes a difference.

---

### Post by simonsaysthis on 2016-09-18
As much as I dislike Windows 10 because it runs terribly by default without installing all the drivers from the manufacturers your point might be correct.

I also have a Skylake laptop with Intel HD520 and I have been struggling ever since to get videos to play and stream without being choppy. IMHO Skylake CPUs don't have great Linux support yet. The problem is a bit more serious with Ubuntu 16.04 as it is not bleeding edge and takes its own sweet time to update drivers and software. My best solution so far is to add this repo:
```
pp:oibaf/graphics-drivers
```

Just type this in a terminal:

```
sudo add-apt-repository ppa:oibaf/graphics-drivers
sudo apt-get update
sudo apt-get dist-upgrade
``` 
...and then you get some pretty recent GPU drivers. So far its been much better. The other alternative is to use an Arch-based distro as these are rolling releases. I am obviously an Ubuntu fan so you have to do some additional fixes that don't come standard. 
[B]
A word of advice. There is Intel Graphics Sofware for Ubuntu tool which has recently been updated. These drivers have not given me any improvement. Stay away from them[/B]

---

### Post by simonsaysthis on 2016-09-18
ok so the emotions above are not meant to be - replace them with ":" and "o" with no spacing between them

---

### Post by simonsaysthis on 2016-09-18
> **QIII said:**
> With those specs, even Unity should be fine.  No need for a lighter DE.

I'm with ian-weisser: we need objective data to make any sort of recommendation.

He is probably right due to Skylake and HD520 support in Ubuntu 16.04 which I also suffer from. Without non-official drivers and repos the experience when playing videos for example is not great at all

---

### Post by howefield on 2016-09-18
> **simonsaysthis said:**
> ok so the emotions above are not meant to be - replace them with ":" and "o" with no spacing between them

Note that code tags will prevent this as you'll see above from the edited post.

---

