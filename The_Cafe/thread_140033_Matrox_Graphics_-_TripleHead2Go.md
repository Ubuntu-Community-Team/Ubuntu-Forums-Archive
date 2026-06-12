---
title: "Matrox Graphics - TripleHead2Go"
date: 2006-03-05
forum: The Cafe
---

### Post by FoxLogic on 2006-03-05
[http://www.matrox.com/graphics/offhome/th2go/press_release.cfm](http://www.matrox.com/graphics/offhome/th2go/press_release.cfm)



Sweet.  Will it compatible with Linux?

---

### Post by heretic9 on 2006-03-05
Nope. Or should I say very doubtful. Ars technica did a review on the dualhead2go a while back and it didn't work with any OS that doesn't come from redmond which kinda sucks cause I hate messing with twinview or xinerama. I doubt matrox have changed their stance since releasing dualhead2go.

---

### Post by briancurtin on 2006-03-05
[QUOTE=http://www.matrox.com/graphics/offhome/th2go/press_release.cfm]**System Compatibility**
TripleHead2Go includes support for Microsoft® Windows® 2000 and Windows® XP[/QUOTE]
[COLOR="White"].[/COLOR]

---

### Post by TrendyDark on 2006-03-05
Well there you go. . . Windows, who would have ever guessed?

---

### Post by Adrenal on 2006-03-06
TechSonic would of, had he been here.
Oh, wait

---

### Post by Kernel Sanders on 2006-03-06
[QUOTE=Adrenal]TechSonic would of, had he been here.
Oh, wait[/QUOTE]

:mrgreen:  How many pointless threads does that make now? :rolleyes:

---

### Post by Dark Nations on 2006-03-11
I could use one of those at the office.

---

### Post by fatespeaks on 2007-07-02
I am using a TripleHead2Go in Ubuntu right now.  3840x1024 is pretty nice.  As neat side effect, I can share the 3 monitors between multiple computers with a KVM.  Only needed to edit my xorg.conf with advice from [OpenSceneGraph.]("http://www.openscenegraph.com/index.php?page=KnowledgeBase.TripleHead2Go") The important bit is the modeline:
```
Modeline "3840x1024" 301.37  3840 3920 4224 4752 1024 1027 1030 1057
```
Though it would be much better if Matrox would release a Linux app to set this up for you.

My only problem with it now is that I haven't figured out how to implement Xinerama features like maximizing to a single display instead of the whole desktop.

---

### Post by CyberCam on 2007-10-28
SWEET so it can actually work on ubuntu !!! So... is it worth the purchase? I would love to run ET:QW on it !!!!

---

### Post by funrider on 2007-10-28
File not found

The Matrox Graphics web site was recently redesigned and restructured to serve you better. Please update your bookmarks.

If you cannot find what you're looking for, please use our sitemap or contact our Webmaster.

---

### Post by CyberCam on 2007-10-28
> **funrider said:**
> File not found

The Matrox Graphics web site was recently redesigned and restructured to serve you better. Please update your bookmarks.

If you cannot find what you're looking for, please use our sitemap or contact our Webmaster.

Here's the new link;
[http://www.matrox.com/graphics/en/gxm/products/th2go/digital/home.php](http://www.matrox.com/graphics/en/gxm/products/th2go/digital/home.php)

---

### Post by fatespeaks on 2007-10-30
> **CyberCam said:**
> SWEET so it can actually work on ubuntu !!! So... is it worth the purchase? I would love to run ET:QW on it !!!!
I can tell you that the TripleHead2Go Analog Edition works on Ubuntu with an NVidia 5200FX.  I would assume that any video card that allows 3840x1024 resolution will work.  The Matrox site has a list of compatible video cards.  Matrox only supports this device with Windows.

For my setup, it was definitely worth the purchase.  The only issue I have is that windows maximize to the entire desktop instead of a single display.  This happens because the video card sees the device as one really wide display.  Perhaps if more Ubuntu users find this thing useful, someone will devise a solution.

Cheers,
Aaron
:guitar:

---

### Post by CyberCam on 2007-10-30
Thanks for the input... looks like I'm going to purchase the analog version.

---

### Post by Mnemonics on 2008-09-08
You can actually get 3840x1200 (2x1920) however you have to configure this with windoze, because factory settings are 3840x1024.

So configure the box with a windoze machine and than hook it up to Ubuntu and its running ok.
On my Dell XPS M1730 Laptop I now do have 5760x1200 (1920x1200 on loptop and 2 x 1920x1200 on 2 24" Dell LCD's).

I say developers heaven!

---

### Post by fatespeaks on 2008-09-21
> **Mnemonics said:**
> You can actually get 3840x1200 (2x1920) however you have to configure this with windoze, because factory settings are 3840x1024.
That is pretty cool.  Are you using the analog or digital triplehead2go?

Cheers,
Aaron

---

### Post by toupeiro on 2008-09-21
Maybe I'm missing something here, but NVidia outdid this some years ago with their X2 cards, which have great linux support, but they aren't cheap..

[IMG]http://www.elsa-jp.co.jp/products/graphicsboard/quadro_fx4700x2/img/ph_quadro_fx_4700x2.jpg[/IMG]

[IMG]http://www.nvidia.com/docs/IO/53243/ultra_high_res_displays.jpg[/IMG]

---

### Post by bluebyt on 2008-09-21
It is mainly use for laptop, you cannot do that with a video card:

---

### Post by fedex1993 on 2008-09-21
hmm looks cool.

---

### Post by chmac on 2008-12-10
Mnemonics, which device are you using? The triplehead or dualhead?

How did you configure the device in Windows? Using the supplied software, or was it just a case of sending that resolution to the device?

---

### Post by gordtulloch on 2009-11-24
I love mine, works wonderfully under Ubuntu 9.04 64 bit!

---

### Post by chmac on 2009-11-25
Would you like to share any info on how you got the whole setup working?

---

### Post by baumisch on 2010-11-15
*push* I am also very interested in bying a used triplehead2go and use it on my ubuntu 10.04 box .... any news?

---

### Post by grayceworks on 2011-03-10
Also interested in how to do this. have a dualhead2go, and it sorta works as I see kubuntu booting up from the cd and it stretches across both my laptop screen, and my other 2 screens, however then it goes back to text that says authentication error right after it tries to load my ati radeon, so I'm not sure if it's my video card, or the dualhead2go, but regardless, I'd like to know how to set it all up correctly. Thanks!

---

### Post by grayceworks on 2011-03-13
Hmm. Once it gets totally into the kubuntu desktop, I can update the video settings to be 3200x1200 which works fine for that screen. However, I have to update, let it revert, then update again with the same settings, otherwise the screen is garbled. Once it's been set up it's fine. The hardware info shows it as a dualhead2go, so it's detected automatically. I just have to set the screen resolution once it's all up and running, otherwise it's just one of the screens, instead of stretched across both. (I have to do this each time, when I'm booting from a usb drive. I shouldn't have to once I actually get this installed on my main drive -- which I'm having a bit of problems with at the moment, unrelated)

---

### Post by CharlesA on 2011-03-13
I would suggest creating a new thread in the support area, as this area isn't for support and this thread is from 2006.

You can link to the original thread, of course.

---

