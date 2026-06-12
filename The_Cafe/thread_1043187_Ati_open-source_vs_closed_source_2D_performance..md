---
title: "Ati open-source vs closed source: 2D performance."
date: 2009-01-18
forum: The Cafe
---

### Post by Vadi on 2009-01-18
I know some people have been claiming that ATI is way better than nVidia because of their open-source drivers. I think this benchmark by Phoronix should be interesting to them: 

**[http://www.phoronix.com/scan.php?page=article&item=amd_fglrx_radeon_2d&num=1&single=1](http://www.phoronix.com/scan.php?page=article&item=amd_fglrx_radeon_2d&num=1&single=1) [AMD Catalyst vs. X.Org Radeon Driver 2D Performance]**

Note that this is 2D only - not 3D.

End result?

> While the Catalyst Linux driver is frequently criticized as being slow when it comes to the 2D performance, the Catalyst 8.12 driver with the ATI Radeon X1800XT graphics card had actually **better performance** than the open-source xf86-video-ati driver in **17 of the 28** tests performed using the Phoronix Test Suite.

Interesting stuff ;)

---

### Post by HavocXphere on 2009-01-18
As I understand it the "superiority" claim isn't based on better performance, but rather on the openness of the open driver.

---

### Post by Vadi on 2009-01-18
Derived from that, the openness of the driver meant better performance since anyone could optimize it, fix bugs, etc. Doesn't seem to be paying off here however (except in some of the special tests where the driver indeed was significantly better).

---

### Post by jrusso2 on 2009-01-18
It does not matter much what 2d performance is its 3d that counts.

How fast do you want your email to draw?

---

### Post by HavocXphere on 2009-01-18
[QUOTE=jrusso2]How fast do you want your email to draw? [/QUOTE]
I want it to run like it stole something.:twisted:

I always assumed the opposite: ATI has the insider knowledge on driver optimizations and details on the hardware while the OpenSource crew needs to guess, beg for info and reverse engineer. Just guessing here...I've never compared them with benchmarks.

---

### Post by Grant A. on 2009-01-18
I use NVidia drivers and have experienced no problems playing games like [The Mana World]("http://www.themanaworld.org"). Infact, I have one of the fastest frame rates out of all of the contributors, and the fastest frame rate with OpenGL on.

---

### Post by Polygon on 2009-01-18
> **Vadi said:**
> Derived from that, the openness of the driver meant better performance since anyone could optimize it, fix bugs, etc. Doesn't seem to be paying off here however (except in some of the special tests where the driver indeed was significantly better).

but then, ati are the people who MADE the cards, and have much much much more experience in writing drivers then whoever helps develop the open source ones. What we need is both parties working on an open driver, and then we get the best of both worlds

---

### Post by Vadi on 2009-01-18
> (02:49:54 PM) Friend: im sad i have to go back to windows
(02:50:07 PM) Me: Yeah? :\
(02:50:18 PM) Friend: i wasnt thinking when i bough the ati ard
(02:50:22 PM) Friend: card*
(02:50:28 PM) Friend: bu i need warcraft to play well
(02:50:31 PM) Friend: and it just doesnt

Gogo ATI efforts, misleading Linux consumers with hype.

---

### Post by fissionmailed on 2009-01-18
My laptop has a Ati card.  After getting a nvidia card for my desktop, I promised myself to never get another Ati card again.  If you don't have good drivers and you don't open the specs to the community, you're going to drive away customers.

---

### Post by Trail on 2009-01-19
> **jrusso2 said:**
> It does not matter much what 2d performance is its 3d that counts.

How fast do you want your email to draw?

Instantly.

---

### Post by Archmage on 2009-01-19
> While the Catalyst Linux driver is frequently criticized as being slow when it comes to the 2D performance, **the Catalyst 8.12 driver with the ATI Radeon X1800XT graphics card had actually better performance than the open-source xf86-video-ati driver in 17 of the 28 tests performed using the Phoronix Test Suite**. **Though in some of the tests where the open-source ATI stack was faster, the Catalyst Linux driver was substantially slower (by up to five times or more in some of the tests).** There are certainly some operations where the Catalyst driver is faster and other areas where it is not being accelerated well at all. **The 2D performance of the xf86-video-ati driver should be more competitive with the introduction of X Server 1.6, which does bring some EXA improvements.** On a similar note, just recently the open-source ATI stack began supporting basic 2D acceleration on the R600/700 series.

I think if you note all the things that stand in the test, you decide who is the winner here. At least from my point of view I see no reason to use the close driver, unless you prefer to get a driver break each time x-org had been updated.

---

### Post by 3rdalbum on 2009-01-19
I originally had an ATI integrated graphics chip in my old computer. Performance was terrible but eventually the drivers stopped crashing my machine on logout. It wasn't so bad.

Now I've got an Nvidia card, and now eventually the drivers have stopped randomly crashing, but they still WILL NOT fix their broken video playback which only happens on certain common combinations of card and driver. I swear, the next card I buy will be an ATI with open-source 3D support. Probably the HD4850 or 4870; there should be open-source 3D on those cards before the middle of the year.

---

### Post by etnlIcarus on 2009-01-19
IMO, this thread smells like bait. OP posts some selective data, makes some slick rationalisation which ignores that, until recently, ATi's open-source efforts were largely backward engineered and then follows-up with this gem:
> **Vadi said:**
> Gogo ATI efforts, misleading Linux consumers with hype.
Groan.


IMO, I don't think many cards have very good driver support on *nix, when talking comprehensively. Nvidia's own closed-source efforts seem to be ahead of the pack when it comes to feature support and stability. Intel chips are apparently well supported (with Intel playing nice with source code and documentation) but since I'm assuming Intel drivers still rely on Mesa, that means missing graphic operations and tempromental fallback rendering (like open-source ATi drivers seem to suffer from).

Things have certainly improved with my Radeon card since 05 or 06, when the open drivers didn't seem to have any texture_from_pixmap support on SuSE and getting the cloced drivers to work at all was an exercise in morification but it's still the situation that I'll install a platnum-rated game in WINE, only to find out that open ATi users are still out in the cold. Or I'll install the closed drivers - until such time as they break and I can't get them to work again.

Hopefully there's still enough people out there using R300 chipsets to warrant continued work on the open drivers. The documentation is now there and the *nix graphical stack is apparently improving so if I hold onto this PC long enough, I might just be able to play Sauderbraten or Direct3D games in Wine.

---

### Post by Polygon on 2009-01-19
> **Vadi said:**
> Gogo ATI efforts, misleading Linux consumers with hype.

of course warcraft doesnt play well . ITS A WINDOWS GAME

---

### Post by blueturtl on 2009-01-19
Isn't it a little early to do a comparison like this when ATI only just recently released their specifications to the community? The closed-source driver has been in development far longer with the proper background information.

From an end-user point of view it looks like the open source ATI driver is developing at a rapid pace. Just two Ubuntu releases prior ATI wasn't really an option to consider at all. Now Compiz seems to run out-of-box on most off-the-shelf-ATI hardware. No more praying to get X to run after you tick fglrx in the restricted drivers manager!

While 2D/3D performance is still behind nVidia on similar hardware, it is only a matter of time before the full potential of the hardware becomes realized.

Come on guys, let's not diss AMD/ATI. They're moving in the right direction. For regular desktop use ATI is a viable alternative already, and it will probably be good for 3D in a year or so. Now is a good time to show support and buy an ATI card.

---

### Post by Vadi on 2009-01-19
Heh, I'd stay away from 4850 - because that's exactly what my friend has and will be installing Windows over Ubuntu soon.

Yeah, it's a windows game - but plays fine on other cards nonetheless. Unfortunarely he can't return his card, newegg doesn't do them O.O.

---

### Post by helliewm on 2009-01-19
> Heh, I'd stay away from 4850 - because that's exactly what my friend has and will be installing Windows over Ubuntu soon.

Why? I have no issues with my 4850. I bought it beacuse I had loads of 2d issues with Nvidia 8500GT. There is a huge thread on the Nvidia forums about 2d issues.

My laptop is ATI also and again no issues. I would now buy ATI everytime.

Helen

---

### Post by mips on 2009-01-19
> **helliewm said:**
> There is a huge thread on the Nvidia forums about 2d issues.



I think that issue has been sorted out with their new drivers.

---

### Post by helliewm on 2009-01-19
Thanks I was not aware Nvidia had released new drivers. I bought my 4850 when they first came out. I am very happy with ATI so will stick with them for now.

Helen

---

### Post by Vince4Amy on 2009-01-19
> **Vadi said:**
> Heh, I'd stay away from 4850 - because that's exactly what my friend has and will be installing Windows over Ubuntu soon.

Yeah, it's a windows game - but plays fine on other cards nonetheless. Unfortunarely he can't return his card, newegg doesn't do them O.O.

Works fine for me in Ubuntu, proprietary driver. OpenSUSE it works fine as well and it's not too bad with the open driver on Fedora 10.

The Open driver is not an option until 3d works properly. After the Vista nForce 3 problems which were never solved from nVidia I will always try to avoid nVidia.

---

### Post by Mazza558 on 2009-01-19
I don't believe that result - Ever since switching to EXA  in Intrepid, the FOSS drivers have been far and away better, in every way. Scrolling actually works instantly now, switching tabs doesn't take 500ms, and it's got even better since then.

---

### Post by Skripka on 2009-01-19
> **Vadi said:**
> I know some people have been claiming that ATI is way better than nVidia because of their open-source drivers. I think this benchmark by Phoronix should be interesting to them: 

**[http://www.phoronix.com/scan.php?page=article&item=amd_fglrx_radeon_2d&num=1&single=1](http://www.phoronix.com/scan.php?page=article&item=amd_fglrx_radeon_2d&num=1&single=1) [AMD Catalyst vs. X.Org Radeon Driver 2D Performance]**

Note that this is 2D only - not 3D.

End result?



Interesting stuff ;)

What I'm wondering is WTH are they doing this benchmarking with a card that is***_ 3 or 4 years old_***?????? Srsly, WTF?

I have a 1900XTX laying around here unused-as the performance in *buntu was awful with the proprietary driver (8.11 IIRC).  Whoever wrote Amdcccle should go stab themselves before they reproduce.  IMHO, IME, YMMV.

---

### Post by CarpKing on 2009-01-19
The OP also fails to note that, while in most of the tests the closed-source driver did better, the difference was never large.  On the other hand, the open-source driver did much better on a few tests, including one where it performed five times better.

---

