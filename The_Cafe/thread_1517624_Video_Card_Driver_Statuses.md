---
title: "Video Card Driver Statuses"
date: 2010-06-25
forum: The Cafe
---

### Post by konqueror7 on 2010-06-25
i'm planning on buying a new laptop, and since my last laptop and current pc both uses nvidia, i had no problems regarding driver installation.

from the last time i heard, there seems to be still existing driver problems regarding ati and intel cards, but that was back then. and, i would gladly welcome opinions or experiences regarding their respective statues currently on linux in general, because i don't want my laptop selection to be limited based on these.

thanks!

---

### Post by Frogs Hair on 2010-06-25
I installed 256.35 Nvidia driver for my 8 series card yesterday and it is running great . The previous driver wasn't bad , but I do notice improvement . The transition from login to desktop is much smother.

---

### Post by spoons on 2010-06-25
Here's my ATi experience:

Video playback has problems. No VSync so tearing etc. 3D is fine apart from WINE which has some bugs in 3D which Nvidia don't have.

Desktop effects can get a little sluggish and they don't work properly with 3D stuff.

There are bugs which are annoying and I wouldn't recommend an ATi card for Linux use.

---

### Post by konqueror7 on 2010-06-25
> **spoons said:**
> Here's my ATi experience:

Video playback has problems. No VSync so tearing etc. 3D is fine apart from WINE which has some bugs in 3D which Nvidia don't have.

Desktop effects can get a little sluggish and they don't work properly with 3D stuff.

There are bugs which are annoying and I wouldn't recommend an ATi card for Linux use.

i see, its seems these issues haven't still been resolved. what driver were you using? repo or proprietary?

---

### Post by konqueror7 on 2010-06-25
> **Frogs Hair said:**
> I installed 256.35 Nvidia driver for my 8 series card yesterday and it is running great . The previous driver wasn't bad , but I do notice improvement . The transition from login to desktop is much smother.

i still got 195 here. this just get me more on leaning towards nvidia...i'll just wait for a few more opinions.:p

---

### Post by spoons on 2010-06-25
> **konqueror7 said:**
> i see, its seems these issues haven't still been resolved. what driver were you using? repo or proprietary?

The propietary driver in Ubuntu 10.04 from the repos. I'll see if the latest one from AMD solves these later for you.

---

### Post by konqueror7 on 2010-06-26
> **spoons said:**
> The propietary driver in Ubuntu 10.04 from the repos. I'll see if the latest one from AMD solves these later for you.

that would be great! i appreciate that...

---

### Post by konqueror7 on 2010-06-27
i've seen on searches and reviews that intel GPUs works also pretty well, with addition of a few tweaks and configs...seems i could put intel 2nd on the list...

---

### Post by doorknob60 on 2010-06-27
Nvidia = Still perfect or close to it
ATI = Much better than before, most things work fine (Wine can sometimes cause problems though, for example)
Intel = The drivers themselves work fine, but Intel graphics cards still suck for gaming and all that stuff though (on any OS)

---

### Post by NightwishFan on 2010-06-27
I agree, I am using the 2.12 git intel drivers here, and they work great except for some games in Wine. Though the card itself as said above will not get far. I can watch 1080p without a hitch though.

---

### Post by Spr0k3t on 2010-06-27
I have worked with all three types of chipsets.  If you have any intention of even attempting to play games that require a good amount of 3D... don't think, just go with nVidia.

Intel graphics for your standard graphics needs does very well.  I might add, it's better than your low end external graphics card for some of the newer intel chipsets.  The Intel GMA 500 chipset is solid on the desktop.  There's no tearing or ripping in video playback even on h264 1080p streams.  The desktop handles 2D and 3D quite well.  When it comes to 3D gaming (even native source), it falls flat on its face and chugs away.  Most of the heavier games won't even start in WINE.

When it comes down to ATI, the graphics drivers are MUCH improved than they were just a year ago.  However, the drivers are not where they need to be to even compete with the closed binary drivers of nVidia.  2D and 3D desktop effects work quite well with the latest cards/drivers.  Wine gaming has so many work arounds needed for many popular games.  Keep in mind though, just last release in 9.10 the drivers were not nearly as good.  I believe this has to do with the R6/700 chipset driver changes.  Desktop operation (2D or 3D) feels about the same when comparing to the nVidia binary.  Some tearing can be seen when streaming video, but I had to look for it to find it.

One of the nVidia laptops a client has is using an 8200M-G processor.  The drivers are nvidia-current and the guy plays quite a few games on it.  The system is solid.  Outside of lower than desktop framerates on 3D... the system handles 3D like it was a bigbox computer.

Hardware wise... I prefer ATI over nVidia, but I like to use what works well so I go with nVidia most of the time.  If I have a client that I know will not be gaming at all on the system being built, I will generally recommend Intel over either.

---

### Post by konqueror7 on 2010-06-27
thanks for all the inputs! gaming is not really an issue for me, also i try as much as possible in using wine...the notebook would be for dev't puropose, and some media work...maybe i'll try to choose the card that atleast could play MMORPGs...based on performance on linux in general, which is better, ati or intel! thanks for the input again!

---

### Post by 3rdalbum on 2010-06-27
> **konqueror7 said:**
> thanks for all the inputs! gaming is not really an issue for me, also i try as much as possible in using wine...the notebook would be for dev't puropose, and some media work...maybe i'll try to choose the card that atleast could play MMORPGs...based on performance on linux in general, which is better, ati or intel! thanks for the input again!

ATI's graphics cards are an order of magnitude faster than Intel's. Intel doesn't compete on performance, only on cost. Intel graphics is very cheap 3D with open-source drivers.

Even with terrible drivers, ATI's graphics are better.

However, I don't recommend ATI at all on Linux. Either buy an Nvidia card and get good 3D and good video decoding, or stick with a stock-basic Intel graphics solution that will just allow you Compiz and Google Earth. It's not a case of "Should I buy ATI or Intel", it's a case of "If you want any graphics performance at all, buy Nvidia; and if your computer will only be used for web surfing then stick with Intel graphics".

You play MMORPGs? Those are games. Nvidia for you. Easy answer :-)

---

### Post by konqueror7 on 2010-06-28
> **3rdalbum said:**
> ATI's graphics cards are an order of magnitude faster than Intel's. Intel doesn't compete on performance, only on cost. Intel graphics is very cheap 3D with open-source drivers.

Even with terrible drivers, ATI's graphics are better.

However, I don't recommend ATI at all on Linux. Either buy an Nvidia card and get good 3D and good video decoding, or stick with a stock-basic Intel graphics solution that will just allow you Compiz and Google Earth. It's not a case of "Should I buy ATI or Intel", it's a case of "If you want any graphics performance at all, buy Nvidia; and if your computer will only be used for web surfing then stick with Intel graphics".

You play MMORPGs? Those are games. Nvidia for you. Easy answer :-)

thanks for the input! i intend to play them on windows, so having a 'so-so' performance of cards in linux would just be fine for me...

if i prioritze my linux desktop, then it seems i should choose intel over ati then...

---

### Post by rabbotz on 2010-06-28
> **konqueror7 said:**
> thanks for the input! i intend to play them on windows, so having a 'so-so' performance of cards in linux would just be fine for me...

if i prioritze my linux desktop, then it seems i should choose intel over ati then...

intel is ok for basic stuff, 3d is garbage though.

---

### Post by konqueror7 on 2010-06-28
okay, last question. how sluggish is the 3d compiz in ati? can it be tolerated? or it makes you want to smash your head against the wall? i don't really use heavy effects. i just use minimize, expo, and sliding desktop effects.

---

### Post by 5dolla on 2010-06-28
dude Nvidia for linux period ........!

---

### Post by konqueror7 on 2010-06-29
i think i'll go with nvidia again. it may cost a little bit more, but then less headaches and regrets.

thanks for all who shared their opinions and experiences!:p

---

### Post by rajeev1204 on 2010-06-29
> **konqueror7 said:**
> okay, last question. how sluggish is the 3d compiz in ati? can it be tolerated? or it makes you want to smash your head against the wall? i don't really use heavy effects. i just use minimize, expo, and sliding desktop effects.


The performance with the new catalyst 10.6 driver for ATI is significant.

There was one major problem with ATI fglrx drivers and that was the windows maximise/minimise performance and it has been fixed.Whether or not you use compiz, this was a major issue with the drivers but its gone now .

Gaming was never an issue and i regularly use my linux system to game.If you play games natively, you wont go wrong with either nvidia or ATI .

Wine is not a supported platform for gaming for a windows game ,and it sucks for both cards. If it works for you , you are lucky, but dont expect Nvidia or ATI to fix your issues with wine, if they do then consider yourself fortunate.

I would request members who are commenting on graphics driver performance to stay a little current since drivers are updated once a month for either nvidia or ATI. 

I have used both cards and i heavily recommend 10.6 drivers to those who have a recent ATI card .I have a Radeon 4850 and iam very satisfied with its performance .Frankly the 10.6  driver for windows is actually having issues with some recent games like bad company 2 .

I have been making frequent posts about the 10.6 performance which might appear to some as fanboyish, but my goal is to let new users know the current status of the ATI drivers from a real user perspective and not just forum hearsay.

---

### Post by konqueror7 on 2010-06-29
> **rajeev1204 said:**
> The performance with the new catalyst 10.6 driver for ATI is significant.

There was one major problem with ATI fglrx drivers and that was the windows maximise/minimise performance and it has been fixed.Whether or not you use compiz, this was a major issue with the drivers but its gone now .

Gaming was never an issue and i regularly use my linux system to game.If you play games natively, you wont go wrong with either nvidia or ATI .

Wine is not a supported platform for gaming for a windows game ,and it sucks for both cards. If it works for you , you are lucky, but dont expect Nvidia or ATI to fix your issues with wine, if they do then consider yourself fortunate.

I would request members who are commenting on graphics driver performance to stay a little current since drivers are updated once a month for either nvidia or ATI. 

I have used both cards and i heavily recommend 10.6 drivers to those who have a recent ATI card .I have a Radeon 4850 and iam very satisfied with its performance .Frankly the 10.6  driver for windows is actually having issues with some recent games like bad company 2 .

I have been making frequent posts about the 10.6 performance which might appear to some as fanboyish, but my goal is to let new users know the current status of the ATI drivers from a real user perspective and not just forum hearsay.

thanks for the input!

i don't do wine or native gaming. i'll boot to windows if i have to play.

does the driver just apply to recent models? as i was doing my research on laptops, i've came across a lot of them, coming with ati, and cheaper than those with nvidia cards, so it would be great if i get the same performance for lesser money.

---

### Post by rajeev1204 on 2010-06-29
> **konqueror7 said:**
> thanks for the input!

i don't do wine or native gaming. i'll boot to windows if i have to play.

does the driver just apply to recent models? as i was doing my research on laptops, i've came across a lot of them, coming with ati, and cheaper than those with nvidia cards, so it would be great if i get the same performance for lesser money.

Minimum card it supports is the Radeon HD 2400 , please check the site here [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)  for release notes.

So a 2400 HD should be fine.But that might be dropped later on i dont know.

---

### Post by konqueror7 on 2010-06-30
thanks!

this ati card, ATI Radeon HD 5470, i really like, if it does work well against NVIDIA GeForce GT240M. the price difference is about 40 € between the 2 notebooks. but i'm still leaning towards the nvidia one, trying to search more about the two...


[ATI Notebook]("http://expert.de/expert/productstart.action?id=18864&locationId=2954")

[NVIDIA Notebook]("http://expert.de/expert/productstart.action?id=18821&locationId=2953")

---

### Post by konqueror7 on 2010-06-30
after a little research on both cards, NVIDIA had the better FPS rate and performance overall, so investing extra 40€ would be okay...

maybe i'll try ATI next time on a desktop rather than on a notebook...:p

---

### Post by AllRadioisDead on 2010-06-30
Don't go ATI, whatever you do.
If you're going to use Linux, go Nvidia.

---

### Post by antenna on 2010-06-30
ATI is very good these days.

---

### Post by AllRadioisDead on 2010-06-30
> **antenna said:**
> ATI is very good these days.

ATI fanboys have been saying that for years.

---

### Post by antenna on 2010-06-30
Probably, regardless.. 10.6 is very good.  And ATI hardware is typically better right now so it's worth looking at current drivers and support rather than relying on old sentiment.

---

### Post by sandy8925 on 2010-06-30
Intel drivers have been opensource for a long time so they'll work out of the box no problems. 

Nvidia is pretty good there's no doubt. and the noveau driver is being developed. 

Regarding ati......... i just recently got a laptop with inbuilt ati graphics. installed kubuntu 10.04 graphics worked out of the box thanks to the opensource radeon drivers. compiz and desktop effects worked well too no sluggishness. can play 720p smoothly. 1080p video lags but no tearing. am able to play flash videos well too. gaming does sort of dissapoint though. osmos demo works smoothly in low detail but is slow in higher detail. lugaru hd demo was jerky in low detail. battle for middle earth 2 in wine at lowest details worked smoothly. haven't tested at higher details bcos characters aren't drawn.

ps - i've compiled and installed the 2.6.34 kernel.

---

### Post by spoons on 2010-06-30
Sorry, I haven't checked for you yet due to exams, I'll see if have time to install the drivers tonight and will post when I do.

---

### Post by rajeev1204 on 2010-06-30
> **ihermit said:**
> Don't go ATI, whatever you do.
If you're going to use Linux, go Nvidia.

Please dont spread FUD on the forums.

---

### Post by rajeev1204 on 2010-06-30
> **konqueror7 said:**
> after a little research on both cards, NVIDIA had the better FPS rate and performance overall, so investing extra 40&#8364; would be okay...

maybe i'll try ATI next time on a desktop rather than on a notebook...:p

I see that the ATI card system  has a core i3 , thats much more efficient than a  core 2 duo as far as i know with shared l3 cache etc and a 32 nm manufacturing process.

On top of that , its cheaper than the Nvidia.Why would you go for the more expensive one ? Game performance is better for some games on nvidia and favours ATI for some.But i think you have to look more into other features too since its a laptop.Also the ATI one has a smaller HDD so you decide. :)


For graphics card recommendations , i follow this chart [http://www.tomshardware.com/reviews/graphics-card-geforce-radeon,2646.html](http://www.tomshardware.com/reviews/graphics-card-geforce-radeon,2646.html) 

Its a very good series and i have always used it to buy my cards,Some 4 years ago i got an nvidia 7600 GT, and after recent reading i got an ATI 4850.

But today, it doesnt make much sense to buy Nvidia since ATI offer similar performance at a lower price.

Those charts are for desktops but you will have a rough idea from them, also in the end there is a huge list of comparable cards which includes mobile chipsets  also.
Also final thoughts, since this is a laptop ,i would recommend getting a nice big screen and some good inbuilt speakers.

---

### Post by konqueror7 on 2010-07-01
> **rajeev1204 said:**
> I see that the ATI card system  has a core i3 , thats much more efficient than a  core 2 duo as far as i know with shared l3 cache etc and a 32 nm manufacturing process.

On top of that , its cheaper than the Nvidia.Why would you go for the more expensive one ? Game performance is better for some games on nvidia and favours ATI for some.But i think you have to look more into other features too since its a laptop.Also the ATI one has a smaller HDD so you decide. :)


For graphics card recommendations , i follow this chart [http://www.tomshardware.com/reviews/graphics-card-geforce-radeon,2646.html](http://www.tomshardware.com/reviews/graphics-card-geforce-radeon,2646.html) 

Its a very good series and i have always used it to buy my cards,Some 4 years ago i got an nvidia 7600 GT, and after recent reading i got an ATI 4850.

But today, it doesnt make much sense to buy Nvidia since ATI offer similar performance at a lower price.

Those charts are for desktops but you will have a rough idea from them, also in the end there is a huge list of comparable cards which includes mobile chipsets  also.
Also final thoughts, since this is a laptop ,i would recommend getting a nice big screen and some good inbuilt speakers.

yeah, its cheaper. i just seem to be inclining to the nvidia one, because i have a copy of crysis and f.e.a.r. and would really like to play them too.

i did a little more research, and found a really good ati card, better than the nvidia one, ATI Radeon Mobility HF 4650, which, only that the laptop is cheaper. 

[HP Pavillion dv6-2115eg ]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01967141&cc=ca&lc=en&dlc=en&product=4115976")

the good thing is, it's upgradable up to 8gb...:P

nah, i don't like big screens. also i already have a laptop backback, so it would be a waste if it doesn't fit, maximum is 16"...

thanks for guiding me through.

---

