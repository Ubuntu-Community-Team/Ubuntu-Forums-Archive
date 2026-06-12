---
title: "Has Anyone Tried to Build an OSX Clone Desktop on Top of xfce?"
date: 2009-02-26
forum: The Cafe
---

### Post by Mark76 on 2009-02-26
I'm thinking that since it already has a native compositor (no need for Compiz) it should be fairly easy.  I'd try it myself but I don't really want two operating systems (my current one and a Xubuntu partition).

---

### Post by kevin11951 on 2009-02-26
> **Mark76 said:**
> I'm thinking that since it already has a native compositor (no need for Compiz) it should be fairly easy.  I'd try it myself but I don't really want two operating systems (my current one and a Xubuntu partition).

I dont know about if they have or not, but if you are worried about having to OS's, then why dont you just use a VM like virtualbox?

---

### Post by chucky chuckaluck on 2009-02-26
i wish someone would do a newton clone.

---

### Post by Mark76 on 2009-02-26
> I dont know about if they have or not, but if you are worried about having to OS's, then why dont you just use a VM like virtualbox?

I tried. But, God, it was so effing sloooowwwww that I lost the will to live.

If only it were possible to do a Wubi in Ubuntu.

---

### Post by marco123 on 2009-02-26
sudo apt-get install xfce4

Then log out change the session to Xfce and experiment.  When your finished log back into Gnome.

---

### Post by loboc on 2009-02-26
> **Mark76 said:**
> I'm thinking that since it already has a native compositor (no need for Compiz) it should be fairly easy.  I'd try it myself but I don't really want two operating systems (my current one and a Xubuntu partition).

Why clone OSX when you can clone Mac OS 8/9 (Classic)

[http://ubuntuforums.org/showthread.php?t=723107](http://ubuntuforums.org/showthread.php?t=723107)

---

### Post by Naiki Muliaina on 2009-02-26
There is OSX themes and icon packs on [XFCE-Look]("http://www.xfce-look.org/")

---

### Post by Mark76 on 2009-02-26
Okay. I just wasted an hour trying to get cairo-dock and the globalmenubar plugin for xfce4 panel to work.

I'm not doing that again.

---

### Post by kk0sse54 on 2009-02-26
> **Mark76 said:**
> 
If only it were possible to do a Wubi in Ubuntu.

Say hello to [_**Lubi**_]("http://lubi.sourceforge.net/")

---

### Post by Grant A. on 2009-02-26
You can try to use AWN and download an OSX-like theme for GTK2 from [here]("http://www.xfce-look.org/content/show.php/Aurora+Smooth?content=80431").

Don't worry about the Window bar, there should be an OSX-like title bar in the XFCE4 theme section of Xubuntu.

P.S. If you are afraid of patents, be careful emulating the OSX dock, it was recently patented by Apple Computer, Inc.

---

### Post by kk0sse54 on 2009-02-26
> **Grant A. said:**
> 
P.S. If you are afraid of patents, be careful emulating the OSX dock, it was recently patented by Apple Computer, Inc.
I seriously don't think you are going to be sued by Apple if you use a dock that is themed to looked like the OS X bar on your desktop.

@Op have you seen the Mac4Lin project?

[http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac](http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac)

---

### Post by Grant A. on 2009-02-26
> **C!oud said:**
> I seriously don't think you are going to be sued by Apple if you use a dock that is themed to looked like the OS X bar on your desktop.

@Op have you seen the Mac4Lin project?

[http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac](http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac)


You're right, they most likely won't, but it is still a good idea to steer clear of any patented objects. Those patents stack up pretty quickly if you don't pay attention to them.

---

### Post by zmjjmz on 2009-02-26
> **Grant A. said:**
> You're right, they most likely won't, but it is still a good idea to steer clear of any patented objects. Those patents stack up pretty quickly if you don't pay attention to them.
Look man, we have an expression over at Slashdot called "RTFA". It stands for Read The Fine Article. It would be helpful if you did that before claiming things patented by xyz company, because Apple patented not the concept of a dock, but the algorithm that is used to make them zoomy. And even then the patent is invalid outside of the US, so you don't have to worry about it ;)

---

### Post by swoll1980 on 2009-02-26
[Dream linux]("http://www.dreamlinux.com.br/") [Screenshots]("thecodingstudio.com/opensource/linux/screenshots/index.php?linux_distribution_sm=Dreamlinux 3.1")

---

### Post by Skripka on 2009-02-26
> **C!oud said:**
> I seriously don't think you are going to be sued by Apple if you use a dock that is themed to looked like the OS X bar on your desktop.

@Op have you seen the Mac4Lin project?

[http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac](http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac)

The Dock is a Dumb GUI interface idea anyway (note the capital "D"). ;)

---

### Post by Grant A. on 2009-02-26
> **zmjjmz said:**
> Look man, we have an expression over at Slashdot called "RTFA". It stands for Read The Fine Article. It would be helpful if you did that before claiming things patented by xyz company, because Apple patented not the concept of a dock, but the algorithm that is used to make them zoomy. And even then the patent is invalid outside of the US, so you don't have to worry about it ;)

What article? I simply said that using an OS X dock clone that emulates patented features may not be a good idea. It was just a warning.

---

### Post by kk0sse54 on 2009-02-26
> **Grant A. said:**
> What article? I simply said that using an OS X dock clone that emulates patented features may not be a good idea. It was just a warning.

What is it with you and patent infringement tonight? There's no apple police that's going to jump out and lay a law suit on you for installing and using something like avant-window-navigator and I don't think anybody needs to be warned about it either.

---

### Post by Grant A. on 2009-02-26
> **C!oud said:**
> What is it with you and patent infringement tonight? There's no apple police that's going to jump out and lay a law suit on you for installing and using something like avant-window-navigator and I don't think anybody needs to be warned about it either.

It's better safe than sorry, I like to give people warnings and make sure that they know exactly what they are doing before they get in too deep. I'm just trying to look out for people here who don't know about the dangers of patent suits. We are in a recession, and all it takes is for one desperate fortune 500 company to sue one FOSS project before the sky starts falling.

Again, I'm just trying to look out for people, and I get yelled at? :(

---

### Post by zmjjmz on 2009-02-26
> **Grant A. said:**
> What article? I simply said that using an OS X dock clone that emulates patented features may not be a good idea. It was just a warning.

The news articles going around when the USPTO granted Apple the patent after 9 years? Search for it on Ars Technica.

---

### Post by RiceMonster on 2009-02-26
People from apple are going to kick down your door, steel your computer, and track mud all over your nice clean floor.

---

### Post by Grant A. on 2009-02-26
> **RiceMonster said:**
> People from apple are going to kick down your door, steel your computer, and track mud all over your nice clean floor.

Nice, I try to help people, and you mock me. What does that say about you? :(

---

### Post by HuaiDan on 2009-02-26
Grant, I've started typing out 3 replies to you already, but stopped to reflect on this before I committed my thoughts to print.


What you are doing here is absurd. It's FUD (FYI means F-ed up disinformation, or Fear, Uncertainty, and Doubt).

You might as well be telling Osama Bin Laden to fear eternal damnation if he doesn't accept the lord and savior jesus christ into his life.

No one here is going to be dissuaded by chicken-little patent law fear-mongering, but plenty will be annoyed and irritated. Please stop.


Sorry for hijacking the thread.
@OP-
Most Windoze users say my desktop looks like OSX, with hydroygen icons, mish-mashed window settings, emerald decorator, and AWN.
I just wish AWN had better icon effect. I like the rocket dock icon zoom, Which BTW I have installed through a bricopack on my XP machine at work. I also wish I could put AWN as top panel! Seems simple enough, why does it lack this capability?

---

### Post by zmjjmz on 2009-02-26
> **RiceMonster said:**
> People from apple are going to kick down your door, steel your computer, and track mud all over your nice clean floor.

My friend's gaming machine got steeled by Apple.
At first it looked like this:
[img]http://images.tigerdirect.com/skuimages/large/V133-8211-BlackXB-main.jpg[/img]

But after Apple steeled it because he installed Stardock, it looked like this.
[img]http://www.itechnews.net/wp-content/uploads/2007/04/apple-mac-pro.jpg[/img].

He's gone into a horrible state of depression :(

---

### Post by Mark76 on 2009-02-27
It's all moot anyway since I couldn't get globalmenubar to work and the cairo-dock plugins (you need the render one for the 3D view) aren't available for 64 bit Linux.

Still. I did manage to establish that the xfwm compositing is good enough to give me a transparent background to cairo-dock. That's something, I suppose.

---

