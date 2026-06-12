---
title: "Hooray, MPX is merged to master!"
date: 2008-05-27
forum: The Cafe
---

### Post by Mr. Picklesworth on 2008-05-27
[MPX]("http://wearables.unisa.edu.au/mpx/") is a really cool project adding multi pointer support to the X server. Indeed, that means working multitouch in a way that keeps legacy apps alive (and better) and integrates perfectly with existing parts of the operating system.

Here are some videos to show what this means:
[LIST]
[*][Technical presentation](http://www.youtube.com/watch?v=AryCQ8Ybp6A), showing cool stuff like multiple cursors on one window and windows only taking particular cursors.
[*][Blingy demo](http://www.youtube.com/watch?v=olWjnfBoY8E), featuring a big table. ([NUI Group]("http://nuigroup.com/") has hundreds of these).
[/LIST]Thanks to [Morgan Collett](http://morgancollett.wordpress.com/2008/05/21/multipointer-x-for-xo/) for the videos!

Indeed, it is [now merged]("http://wearables.unisa.edu.au/mpx/?q=node/144") into the real X Server!

I am particularly excited because I have a huge number of cursor input devices (Wacom tablet, mouse, touchpad). Having them each with a unique cursor is bound to be cooler than all fighting over one.

---

### Post by Steveway on 2008-05-27
Hoo-fscking-ray!!!!!!!!!
MPX is one of the most awesome things I know of.
No other operating-system that I know of supports several pointers at once, this is a big innovation-plus for us.
This is soo awesome.

---

### Post by klange on 2008-05-27
I was just talking to a friend about this today. I was teaching the rest of my Comp Sci class Python and we were making a game and he was talking about how you *can't* have two mouse cursors with two mice, and I told him about MPX and how it was being added to the core of the FOSS graphics and input system.

Technically, we (the C-F developers) could use MPX to cheat our way to input redirection by making our own input device and blocking all input from the mouse.

---

### Post by brnetonboy on 2008-06-10
That is very cool!

Has anyone had any success in actually getting it to work in Ubuntu? If so, please share! I know there are a lot of people who would love to get it running but are new to Linux and can't figure it out on their own.

---

### Post by FuturePilot on 2008-06-10
Wow! That is incredible. Imagine the possibilities with Compiz :shock:

---

### Post by ghindo on 2008-06-10
The most exciting possibility I see?

Multi-touch Starcraft.

[http://www.youtube.com/watch?v=CYY-g6ionzM](http://www.youtube.com/watch?v=CYY-g6ionzM)

---

### Post by motin on 2008-06-11
Let's get a Howto for Hardy going: [http://ubuntuforums.org/showthread.php?t=397414](http://ubuntuforums.org/showthread.php?t=397414)

Anyone that has managed to get this going in Ubuntu using the latest X from git please contribute to that thread - thanks a million!

---

### Post by nmz787 on 2009-01-19
here is a howto I wrote... I seem to have lost my final version, but it should suffice for those who wish to see this software running:

[http://innovation.csh.rit.edu/mpxhowto.html](http://innovation.csh.rit.edu/mpxhowto.html)

---

### Post by hanzomon4 on 2009-01-19
How is this cool... exactly? Who uses two mice at the same time?

---

### Post by sydbat on 2009-01-19
> **hanzomon4 said:**
> How is this cool... exactly? Who uses two mice at the same time?If you are collaborating on a project, either at the same computer or (I imagine) via VNC. Each person in the collaboration can point out things, act upon things, etc to keep the project moving forward.

Of course there will be those who will use it for their own evil purposes...

---

### Post by ghindo on 2009-01-19
> **hanzomon4 said:**
> How is this cool... exactly? Who uses two mice at the same time?I think it's mostly intended for touch-screens.

---

### Post by cardinals_fan on 2009-01-19
[color="white"]d[/color]
=D>

---

### Post by Mr. Picklesworth on 2009-01-19
The big thing here that really sets this apart from a proprietary multitouch system is what it does for conventional software and input methods. Indeed, multiple mice *is* a big thing. Think of how annoying it is that you must give up your mouse pointer on the local machine for an interactive VNC session. It's all about multi user support :)

Mango Lassi (Synnergy done better, for the GNOME platform) is hoping to use MPX for pointer sharing, where when a pointer moves to another computer it simply adds another pointer, instead of morphing into that other computer's pointer.

---

### Post by zmjjmz on 2009-01-19
> **Mr. Picklesworth said:**
> The big thing here that really sets this apart from a proprietary multitouch system is what it does for conventional software and input methods. Indeed, multiple mice *is* a big thing. Think of how annoying it is that you must give up your mouse pointer on the local machine for an interactive VNC session. It's all about multi user support :)

Mango Lassi (Synnergy done better, for the GNOME platform) is hoping to use MPX for pointer sharing, where when a pointer moves to another computer it simply adds another pointer, instead of morphing into that other computer's pointer.

mmm, mango lassi is good.

---

### Post by spupy on 2009-01-19
Actually you could do some funky stuff using two mice; or a mouse and a touchpad.

---

### Post by MaxIBoy on 2009-01-19
Controlling two selection rectangle corners at once would be cool. 


Remember that MPX also supports multiple keyboards. In other words, split-screen gaming on Linux is now 100% doable.

---

### Post by CarpKing on 2009-01-20
> **spupy said:**
> Actually you could do some funky stuff using two mice; or a mouse and a touchpad.

Or multiple Wiimotes?

---

### Post by Mr. Picklesworth on 2009-01-26
Nice little goodie posted on Planet GNOME right now: The Vino VNC server now supports MPX.

Chris's demo should convince all the nonbelievers, and amaze everyone else.
(I didn't realize the keyboard stuff was so cleanly associated, too. I wonder if this means my caps lock and scroll lock lights / statuses will start behaving sensibly when I have multiple keyboards attached?)

[http://blog.printf.net/articles/2009/01/26/multi-pointer-remote-desktop](http://blog.printf.net/articles/2009/01/26/multi-pointer-remote-desktop)

I have a hunch that this will win the enterprise desktop.

---

### Post by ubunaut on 2009-01-29
There are lots of fun and useful possibilities for multipointer x, how difficult is it now to configure and enable in Ubuntu?

---

### Post by Xbehave on 2009-01-29
is it possible to use a single laptop touchpad as two pointers? i mean obviously its better with hardware support but it would be cool if software emulation supported it.

---

### Post by mcduck on 2009-01-29
> **Xbehave said:**
> is it possible to use a single laptop touchpad as two pointers? i mean obviously its better with hardware support but it would be cool if software emulation supported it.

Might be, if your touchpad supports multitouch (most don't).

---

### Post by motin on 2009-02-28
> **nmz787 said:**
> here is a howto I wrote... I seem to have lost my final version, but it should suffice for those who wish to see this software running:

[http://innovation.csh.rit.edu/mpxhowto.html](http://innovation.csh.rit.edu/mpxhowto.html)

The link is currently broken. Any chance you could post this to the Ubuntu community wiki or in the forums?

Cheers

---

### Post by forrestcupp on 2009-02-28
This is awesome.  I've been waiting a long time for this.

A long time ago, I posted a thread in these forums asking if this could be done.  I said that you have two hands that you use in real life, so doesn't it make sense that it would be useful to be able to have a working mouse in each hand for manipulating things on the computer.  Everyone thought I was crazy and no one could see how it could possibly be useful.

Now that there *is* such a thing and there are videos, you all see how useful it *can* be.  Nobody ever listens to forrestcupp.

---

### Post by Polygon on 2009-03-01
MPX didn't make it in to the latest xserver, 1.60. oh well.

---

### Post by SoftwareExplorer on 2009-12-25
MPX was in the Lucid Daily release I was testing. I found a how to here:[http://alec.mooo.com/mpx.php](http://alec.mooo.com/mpx.php)

---

### Post by zonyl on 2009-12-26
Confirmed in 10.04 Alpha1.  Installed on my TabletPC TC4200 and got two separate pointers for my trackpoint and my touchpad!   Very cool beginning to what I hope will be multi-touch enabled Gnome.

Unfortunately the hand-off between the two pointers in Compiz was very buggy.  When one pointer is engaged in a menu, the other cannot interact with it at the same time.  Couldnt drag windows, etc. 

Great start though and would like to thank all of those involved!  Im excited to see what can come of this.

---

### Post by phrostbyte on 2009-12-26
Anyone have a howto for actually making a multitouch table?

---

### Post by phrostbyte on 2009-12-26
> **zonyl said:**
> Confirmed in 10.04 Alpha1.  Installed on my TabletPC TC4200 and got two separate pointers for my trackpoint and my touchpad!   Very cool beginning to what I hope will be multi-touch enabled Gnome.

Unfortunately the hand-off between the two pointers in Compiz was very buggy.  When one pointer is engaged in a menu, the other cannot interact with it at the same time.  Couldnt drag windows, etc. 

Great start though and would like to thank all of those involved!  Im excited to see what can come of this.

I think with DeviceKit it is possible to program something in that when you plug in another mouse, it asks you if you want to create another pointer or not.

---

### Post by jastonas on 2010-03-17
This is truly amazing. Just heard of this thanx to motin and his signature! Subscribing to this thread so as to be updated to further changes. Will probably try to use it when i go home where i have 10.04 installed.

---

### Post by kaefert66014235 on 2011-05-16
is MPX in Ubuntu, and if it is, in which versions? is it in 10.10 and or 11.04?

---

### Post by brnetonboy on 2011-05-16
> **kaefert66014235 said:**
> is MPX in Ubuntu, and if it is, in which versions? is it in 10.10 and or 11.04?

I think it's been in for a while, and is probably in both 10.10 and 11.04. I have Natty and I was able to follow these instructions to get it to work in 5 mins: 

[http://alec.mooo.com/mpx.html](http://alec.mooo.com/mpx.html)

A little buggy, but it really works and even I can figure it out. Also look at this thread [http://ubuntuforums.org/showthread.php?t=1732511](http://ubuntuforums.org/showthread.php?t=1732511)

---

### Post by kaefert66014235 on 2011-05-19
@brnetonboy: thanks for the link! man is this beatiful!

---

