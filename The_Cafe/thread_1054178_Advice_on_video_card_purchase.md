---
title: "Advice on video card purchase"
date: 2009-01-29
forum: The Cafe
---

### Post by 4th guy on 2009-01-29
Since upgrading my system, I have been left without a video card (my old video card was AGP and the new slot is PCI-E). Now I'm looking to add one of these things ;)
The motherboard that I have is a P5GC-MX/1333 (micro board)
I want the video card to be able to handle some of the recent games, but it doesn't have to handle Crysis with everything set to max.
But I have a couple of questions.

Will a PCI-E 2.0 card work on a PCI-E bus? Is it wasted money?
There are 2 different 8400GS and 3 different 9500GT. What is the difference between those (seemingly similar) video cards? [Gefore 8400GS]("http://klikk.com.mt/#scatid=2:catid=16:filters=190_1708_") [Geforce 9500GT]("http://klikk.com.mt/#scatid=2:catid=16:filters=190_5198_")
Has ATI support in Ubuntu since the 7.10 days, or is NVIDIA still better?
That's all for now, I will ask additional questions when these are answered.

---

### Post by mips on 2009-01-29
> **4th guy said:**
> 
I want the video card to be able to handle some of the recent games, but it doesn't have to handle Crysis with everything set to max.
But I have a couple of questions.

Will a PCI-E 2.0 card work on a PCI-E bus? Is it wasted money?
There are 2 different 8400GS and 3 different 9500GT. What is the difference between those (seemingly similar) video cards? [Gefore 8400GS]("http://klikk.com.mt/#scatid=2:catid=16:filters=190_1708_") [Geforce 9500GT]("http://klikk.com.mt/#scatid=2:catid=16:filters=190_5198_")
Has ATI support in Ubuntu since the 7.10 days, or is NVIDIA still better?
That's all for now, I will ask additional questions when these are answered.

The XFX 9600GT is a great card. 9x00 series also use less power and run cooler.
The PCI-E 2.0 is backward compatible with PCI-E
nVidia drivers are still better than ATI although some people that own ATI will tell you otherwise. The nVidia 180.xx drivers are great!

See my thread here about buying a video card, [http://ubuntuforums.org/showthread.php?t=908091&highlight=XFX](http://ubuntuforums.org/showthread.php?t=908091&highlight=XFX)

Had some excellent input from people on differences between the different model numbers and what it all means.

Great site to compare GPU specs side by side and links to reviews, [URL="http://www.gpureview.com/show_cards.php"]http://www.gpureview.com/show_cards.php
[/URL]

---

### Post by Skripka on 2009-01-29
+1 mips.

Make sure your PSU has the cajones to drive current nuclear-reactor-powered cards if you're getting a 9XXX series or above Nvidia card, you'll be wanting something along the lines of a 500W power supply...you'll need a PSU with at least ONE 6pin PCIE power connector on it....possible 2.

---

### Post by 4th guy on 2009-01-29
> **Skripka said:**
> +1 mips.

Make sure your PSU has the cajones to drive current nuclear-reactor-powered cards if you're getting a 9XXX series or above Nvidia card, you'll be wanting something along the lines of a 500W power supply...you'll need a PSU with at least ONE 6pin PCIE power connector on it....possible 2.

I was going to buy another power supply anyway since I managed to avoid buying one for the "upgrade".
I think I will buy one of [these]("http://klikk.com.mt/#scatid=2:catid=0:filters=190_5147_") (the ones marked 60 Euros, but I'm kind of confused. What is the difference between XFX, Sparkle and Palit?
Also, do you think it's worth the 60 euros, or is there something cheaper which performs at a similar rate?

---

### Post by jimi_hendrix on 2009-01-29
> **4th guy said:**
> Has ATI support in Ubuntu since the 7.10 days, or is NVIDIA still better?
That's all for now, I will ask additional questions when these are answered.

in 8.04 ATI is great but i have a bug posted on launchpad for.10

---

### Post by 4th guy on 2009-01-30
Will someone please answer my question? :-\"
> I think I will buy one of these (the ones marked 60 Euros, but I'm kind of confused. What is the difference between XFX, Sparkle and Palit?
Also, do you think it's worth the 60 euros, or is there something cheaper which performs at a similar rate? 

---

### Post by Skripka on 2009-01-30
> **4th guy said:**
> Will someone please answer my question? :-\"

Your web linky isn't working on my end, or I would ;)

---

### Post by 4th guy on 2009-01-30
Oh, sorry. [http://klikk.com.mt/html.php?catid=16&filters=190](http://klikk.com.mt/html.php?catid=16&filters=190)
I also have another question: what are the benefits of the exact same card that has more ram on it? Will it just allow better textures or would it improve FPS?

---

### Post by jespdj on 2009-01-30
An nVidia 8400 is not a really powerful graphics card. Why not get at least a 8600, or a 9600? Those are more powerful and don't cost a lot more. If I'd want to play games, I'd get something more powerful than a 8400.

The same graphics card with more memory doesn't make a major difference in FPS. It indeed means that there's more memory for textures, which could make a minor difference, but the GPU itself is the main thing that determines how fast graphics can be rendered.

As far as I know, nVidia is still the safest bet when you want to have 3D graphics working well on Linux. (Although that could change this year; ATI recently published the specs for some of their GPUs, which means that open source developers finally have the documentation they need to build a fully open source driver themselves).

---

### Post by mips on 2009-01-30
You can forget trying games like crysis on a 8400,8500,8600 series card, they are really not powerfull. You will have to look at 9600GT, 8800GT & higher models.

---

### Post by 4th guy on 2009-01-30
Who said anything about me getting an 8400? :P
I got an 9500 because even with all the benefits 9600 offered, it was too expensive (double in cost).

---

### Post by mips on 2009-01-30
> **4th guy said:**
> Who said anything about me getting an 8400? :P

I got an 9500 because even with all the benefits 9600 offered, it was too expensive (double in cost).

I just assumed you were looking at it as I saw mention of it in that link you provided ;)

The 9600 is more expensive but on paper it provides more than twice the performance.

Enjoy your card and let us know how it goes. Use the latest 180.22 or 180.25 drivers, see [http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)
I think you can install via synaptic.

---

### Post by Zero Prime on 2009-01-30
As one user stated, an ATI user will disagree.  I've used Nvidia and ATI.  When I first started with Linux (3 years ago) Nvidia was the only player in the game.  The newest drivers for ATI have changed this.  There is now multi-monitor support, crossfire support, and hybrid crossfire support.  This is with the proprietary drivers though.  If you want to use the open source drivers I would then suggest Nvidia, if you don't mind the easy task of downloading and installing proprietary drivers I would suggest ATI.

---

### Post by 4th guy on 2009-02-01
> **mips said:**
> I just assumed you were looking at it as I saw mention of it in that link you provided ;)

The 9600 is more expensive but on paper it provides more than twice the performance.

Enjoy your card and let us know how it goes. Use the latest 180.22 or 180.25 drivers, see [http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)
I think you can install via synaptic.
Thank you, I am well aware of your points. However, I could not justify the cost I am not an obsessive gamer that has to play all the latest games with all bells and whistles turned on.
Is there a way to upgrade drivers using Ubuntu's prompts?

---

### Post by aaaantoine on 2009-02-01
You might find some usefulness in this page:

[http://www.tomshardware.com/reviews/best-graphics-card,2118.html](http://www.tomshardware.com/reviews/best-graphics-card,2118.html)

Tom's Hardware updates their Best Graphics Card for the Money guide monthly.  They have more in-depth reviews elsewhere on the site, but at the end of this article they have a table indicating different tiers of performance.

---

