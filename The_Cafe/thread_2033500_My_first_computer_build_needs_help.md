---
title: "My first computer build needs help"
date: 2012-07-26
forum: The Cafe
---

### Post by tjeremiah on 2012-07-26
My apologies if this isnt the right forum to post this. 

Its the summer, im bored while I wait for another semester to begin. While im here, I decided that since I now have the money and always wanted to do this, I would like to finally build my own desktop computer. Forget the tablet and the netbook for now, I want a desktop. :o

I want a desktop because I assume its easily upgradable and is best suited for gaming. What I want however is to build a pc that doesnt consume a lot of power and will cost no more than $530. 

I managed to make a list of items I think is best suited for my needs but would like some opinions from here. Is this a good build and most importantly, would it work good with Linux and its future (Steam) support? 
1. [COLOR="DarkOrange"][http://www.newegg.com/Product/Product.aspx?Item=N82E16811553002](http://www.newegg.com/Product/Product.aspx?Item=N82E16811553002)[/COLOR] - I really like this tower

2. [COLOR="DarkOrange"][http://www.newegg.com/Product/Product.aspx?Item=N82E16813157315](http://www.newegg.com/Product/Product.aspx?Item=N82E16813157315)[/COLOR] - Motherboard

3. [COLOR="DarkOrange"][http://www.newegg.com/Product/Product.aspx?Item=N82E16814121633](http://www.newegg.com/Product/Product.aspx?Item=N82E16814121633)[/COLOR] - I assume this is good enough to run pretty much any game above current console gaming level. I know it wont run everything super high but it will look better than say XBOX and PS3 games. Also its at a reasonable price. 

4. [COLOR="DarkOrange"][http://www.newegg.com/Product/Product.aspx?Item=N82E16817139026](http://www.newegg.com/Product/Product.aspx?Item=N82E16817139026)[/COLOR]  - Power

5. [COLOR="DarkOrange"][http://www.newegg.com/Product/Product.aspx?Item=N82E16819116507](http://www.newegg.com/Product/Product.aspx?Item=N82E16819116507)[/COLOR] - At first I wanted to go with AMD but I see this intel chip is built on 22nm and consumes low power. Correct?

6. [COLOR="DarkOrange"][http://www.newegg.com/Product/Product.aspx?Item=N82E16820231277](http://www.newegg.com/Product/Product.aspx?Item=N82E16820231277)[/COLOR] - RAM

7. I have a 3yr 500 GB HDD that was hardly used and plan on using it for this build. 

This is what I managed to choose so far. What do you guys think.

---

### Post by forrestcupp on 2012-07-26
I'll probably have some diehard AMD fans yelling at me, but I'd much rather have an nvidia GPU in Linux.

---

### Post by Frogs Hair on 2012-07-26
Make sure you have a large enough power supply for the graphics card and other hardware. You will have poor performance if you don't .

---

### Post by Dlambert on 2012-07-26
Go with Nvidia for the GPU a 550TI is around that price range.

---

### Post by mike acker on 2012-07-26
me building one too

get _Building the Perfect PC_ from Amazon and study .  you have to select components that will work together ...

... is that HDD SATA ?

---

### Post by Grenage on 2012-07-26
Yeah, to be honest I currently stick to Intel and Nvidia.

---

### Post by mike acker on 2012-07-26
="Yeah, to be honest I currently stick to Intel and Nvidia."

no chance.  I'm doing AMD with onboard ATI Graphics.   particularly after Linus remarks regarding nvideo

---

### Post by tjeremiah on 2012-07-26
> **mike acker said:**
> me building one too

get _Building the Perfect PC_ from Amazon and study .  you have to select components that will work together ...

... is that HDD SATA ?

I believe its SATA. Im going to double check later today. 

As for everyone else, ill switch the Graphic card to Nvidia. But for those who viewed the links, is the CPU I picked good for saving power?

---

### Post by drmrgd on 2012-07-26
> **Frogs Hair said:**
> Make sure you have a large enough power supply for the graphics card and other hardware. You will have poor performance if you don't .

When I looked at your list of components, I thought the same thing.  I could be wrong, but 430 watt might be a little slim for that computer - especially if you start running a bunch of fans, a water cooling system (which it seems that case is set up for), and whatnot.  You might consider going a little larger, and it's definitely worth spending a little extra for the 80 Plus certified PSUs.  Having just worked with my first modular PSU, if you really feel like splurging a little, the modular units are really, really nice and make the inside of your case look great (especially since your case has a nice little window on it).  If the case has plenty of room on the other side to hide all the cables, then maybe it's not worth the extra cash for you, though.

---

### Post by tjeremiah on 2012-07-26
> **Dlambert said:**
> Go with Nvidia for the GPU a 550TI is around that price range.

:( From a Newegg buyer . 

**_Cons:_** If you plan on running GNU/Linux this card is a poor choice. I went with Nvidia because I have had excellent experiences with running their cards with GNU/Linux. The 550Ti is an exception. I had to scroll through pages of forums just to be able to install Ubuntu. Booting an install CD simply presents you with a black screen. It was the same with Mint. I finally got Ubuntu 12.04LTS installed. After a kernel update the video card wouldn't work. I expected this as the drivers need to be recompiled with the new kernel. I completely removed Nvidia's Linux drivers. I reinstalled the drivers from the command line. When I rebooted my computer I still had a command line only interface. I found a way to boot into my desktop from the command line using a shell script. It was a real pain. I also couldn't switch between user accounts in the GUI. One day I restarted my computer and it booted straight to the GUI. It worked fine until now. I updated again and this time it wasn't even a kernel update.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814130625](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130625)

Also, this would push my build over $530. Any other suggestions?

---

### Post by oldfred on 2012-07-26
Ever since they converted video drivers to kernel mode I have had to use nomodeset with my nVidia card. Just before that it worked without any issue.

Now if you include the check to install everything including proprietary drivers, it downloads the nVidia driver. But .40 from nVidia has had issues with certain cards. Not Ubuntu or Linux issue but nVidia. If you do not download driver, then you have to use nomodeset on first boot or until you install nVidia driver.

I think Linus complaint is about the idea of closed source video drivers and the lack of support. But I find the nVidia driver works and many seem to think it works pretty well or AMD and Intel also have video driver issues.

---

### Post by Dlambert on 2012-07-26
Go with an AMD cpu or (APU-I'll sell one to you :) 3870K-quad core-brand new ) and an Nvidia GPU.

---

### Post by forrestcupp on 2012-07-26
> **mike acker said:**
> ="Yeah, to be honest I currently stick to Intel and Nvidia."

no chance.  I'm doing AMD with onboard ATI Graphics.   particularly after Linus remarks regarding nvideo

So you're going to limit your experience just because Linus hates nvidia? If that's the only reason, that's not a very good reason. Linus hates a lot of things, and he seems to change his mind a lot about what he hates.

---

### Post by tjeremiah on 2012-07-26
> **Dlambert said:**
> Go with an AMD cpu or (APU-I'll sell one to you :) 3870K-quad core-brand new ) and an Nvidia GPU.

I was looking into APUs for months. I read a lot of complains when it came to ubuntu and APUs and how they are only good for gaming while the CPU cant really compete with Intel. Same for AMD in general. I picked the intel CPU because I think its good for its price and will be suited for increased needs in the future. Also, low power consumption.

---

### Post by tjeremiah on 2012-07-26
> **drmrgd said:**
> When I looked at your list of components, I thought the same thing.  I could be wrong, but 430 watt might be a little slim for that computer - especially if you start running a bunch of fans, a water cooling system (which it seems that case is set up for), and whatnot.  You might consider going a little larger, and it's definitely worth spending a little extra for the 80 Plus certified PSUs.  Having just worked with my first modular PSU, if you really feel like splurging a little, the modular units are really, really nice and make the inside of your case look great (especially since your case has a nice little window on it).  If the case has plenty of room on the other side to hide all the cables, then maybe it's not worth the extra cash for you, though.

thanks. ill do more hw on this later.

---

### Post by Nixarter on 2012-07-26
First off, don't get the 7750.  Get the 7770 if anything.  For about $20 more, you get 60% more performance, with similar power consumption.  It has similar power consumption, except when it passes the 7750... it can pump more power for higher output, but pretty much linearly from the 7750's output.  So the power is there if you need it, but won't hog power when you are surfin the interwebs.

It really sucks that there isn't a proper CPU that Intel makes atm.  They are all combos (with the exception of a couple, but they are way overpriced, and seem to be based off of the combo designs :( ).  Personally, I recommend the AMD FX-8120.  It will save you a solid $40 before tax, yet performs ~13% better ([source](http://www.cpubenchmark.net/overclocked_cpus.html)).  It also has more potential as more programs support their advanced instruction set.  It uses about 10-20% more power per calculation, but has the potential to calculate more, so it depends on your choice.  So it is cheaper, future-proof, and faster.  Plus, you have the piece of mind that you are buying form a company that doesn't try to screw over their customers, competition, and linux users every time you turn around.

Whatever the case, you will need a bigger power supply.  Go with at least a 500w power supply.  Personally, I recommend an 80plus certified supply.  They save a LOT more power than the name implies, and that choice will easily be the biggest savings in actual electricity consumption in your design.
[]("http://www.cpubenchmark.net/cpu.php?cpu=AMD+FX-8120+Eight-Core")

---

### Post by pqwoerituytrueiwoq on 2012-07-26
> **tjeremiah said:**
> :( From a Newegg buyer . 

**_Cons:_** If you plan on running GNU/Linux this card is a poor choice. I went with Nvidia because I have had excellent experiences with running their cards with GNU/Linux. The 550Ti is an exception. I had to scroll through pages of forums just to be able to install Ubuntu. Booting an install CD simply presents you with a black screen. It was the same with Mint. I finally got Ubuntu 12.04LTS installed. After a kernel update the video card wouldn't work. I expected this as the drivers need to be recompiled with the new kernel. I completely removed Nvidia's Linux drivers. I reinstalled the drivers from the command line. When I rebooted my computer I still had a command line only interface. I found a way to boot into my desktop from the command line using a shell script. It was a real pain. I also couldn't switch between user accounts in the GUI. One day I restarted my computer and it booted straight to the GUI. It worked fine until now. I updated again and this time it wasn't even a kernel update.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814130625](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130625)

Also, this would push my build over $530. Any other suggestions?
just add nomodeset to the kernel's boot line, not needed after you install the driver 
for the recored i am using a 550 ti right now
driver install (latest)
```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update;sudo apt-get install nvidia-current nvidia-settings
```it will be recompiled after a kernel update automatically

There are 4 gaming builds to pick from here:
[http://www.eggxpert.com/forums/permalink/837453/837454/ShowThread.aspx#837454](http://www.eggxpert.com/forums/permalink/837453/837454/ShowThread.aspx#837454)
linking you to than so so much easer than remaking it probably spent 20min on that the 1st time, lol
just drop the HDD in it and the lower end ones will be in your budget

---

### Post by Dlambert on 2012-07-27
> **tjeremiah said:**
> I was looking into APUs for months. I read a lot of complains when it came to ubuntu and APUs and how they are only good for gaming while the CPU cant really compete with Intel. Same for AMD in general. I picked the intel CPU because I think its good for its price and will be suited for increased needs in the future. Also, low power consumption.

Yeah but this APU retails at 120, and it's unlocked to overclock. The closest intel quad core is?? And just throw a cpu in the and you don't need the gpu part.

---

### Post by ojdon on 2012-07-27
From my experience Intel and Nvidia is a better combination. What Linus was speaking about was more about Optimus technology since the support is awful. It's just that news sites made the quote sound like it was every single bit of Nvidia hardware was awful under Linux. 

If you only want an out of the box experience then Intel chipsets is the best you're going to get, but awful for gaming/high end multimedia etc. With my Nvidia cards I just need to install the restricted Nvidia binary driver and they pretty much work flawlessly no extra tweaking, etc.

---

### Post by Bodsda on 2012-07-27
In case it helps anyone, here is a PC build that I used recently, works like a dream with Ubuntu. 

[http://www.ebuyer.com/lists/list/6695](http://www.ebuyer.com/lists/list/6695)

It comes in at £316.37, which at the moment is $497.62

By the way, that CPU, with that motherboard, has 6 cores, not 4 :D

-- Bodsda

---

### Post by desktorp on 2012-07-27
I don't mean to bash the hybrid CPU+GPU / APU products out there, but I think it's important to consider that it's just another form of onboard video.  Onboard video is an insult to any respectable desktop/workstation case. ;)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103873](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103873)  - 64.99  Athlon II X2 3.2GHz 65W

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813157305](http://www.newegg.com/Product/Product.aspx?Item=N82E16813157305)  - 66.99 ASRock board / no onboard video (AMD770)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16820231424](http://www.newegg.com/Product/Product.aspx?Item=N82E16820231424)  - 39.99 G.SKILL Value 2x4GB DDR3 1333

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814121639](http://www.newegg.com/Product/Product.aspx?Item=N82E16814121639)  - 79.99 ASUS GeForce GT 630 2GB 128-bit DDR3

[http://www.newegg.com/Product/Product.aspx?Item=N82E16817139028](http://www.newegg.com/Product/Product.aspx?Item=N82E16817139028)  - 64.99 Corsair CX600 600w PSU

[http://www.newegg.com/Product/Product.aspx?Item=N82E16811553002](http://www.newegg.com/Product/Product.aspx?Item=N82E16811553002)  - 89.99 COUGAR case

Basically, don't skimp on the power supply.  Skimp just a bit on the CPU.  Maybe get a  good heatsink/fan.  *Maybe* get a Phenom instead of an  Athlon, for the few games that will take advantage of L3 cache, but it's  another **nearly negligible** difference.  (and if you like Intel.. get a core i3 or i5.. or even older are still fine like Core2)

Just remember that when you're on a budget and using Linux, the Bleeding Edge of Hardware is a double edged sword.

---

### Post by Dlambert on 2012-07-27
Tell that to the people who can't afford GFX cards. I got an APU fro free from AMD and have to post my review to them and I'll ve in their reviewer program! Woow!

---

### Post by tjeremiah on 2012-07-27
thanks for all the feedback but im still debating. However, here is where I stand as of right now.

I read the feedback but it looks like im going to stick with the Intel i5 for now based on its 22nm and low power consumption while giving great performance. As for the graphic card im currently still leaning towards AMD/ATI because of the number of cards not requiring an addiontional "upage" in power use while also giving good performance. Lot of positive user reviews too. I know its a gamble but so far ATI seems to be reasonable from what im seeing. As for the power supply, im going to upgrade to a 550W platinum standard from newegg. 

I'll give my final thoughts early next week and will order the final parts later that week. In the mean time, I managaed to dig up an old HDD that was hardly used and  think its too old to work with any modern motherboard. Here it is :
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822148034](http://www.newegg.com/Product/Product.aspx?Item=N82E16822148034)

Im looking at the cable attached to it and have no idea what it is. So a new HDD will be ordered. Mainly 500GB.

---

### Post by Dlambert on 2012-07-27
ATM drivers are better with Nvidia. And none of this conversation will matter once wayland comes.

---

### Post by Nixarter on 2012-07-27
> **desktorp said:**
> I don't mean to bash the hybrid CPU+GPU / APU products out there, but I think it's important to consider that it's just another form of onboard video.  Onboard video is an insult to any respectable desktop/workstation case. ;)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103873](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103873)  - 64.99  Athlon II X2 3.2GHz 65W

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813157305](http://www.newegg.com/Product/Product.aspx?Item=N82E16813157305)  - 66.99 ASRock board / no onboard video (AMD770)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16820231424](http://www.newegg.com/Product/Product.aspx?Item=N82E16820231424)  - 39.99 G.SKILL Value 2x4GB DDR3 1333

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814121639](http://www.newegg.com/Product/Product.aspx?Item=N82E16814121639)  - 79.99 ASUS GeForce GT 630 2GB 128-bit DDR3

[http://www.newegg.com/Product/Product.aspx?Item=N82E16817139028](http://www.newegg.com/Product/Product.aspx?Item=N82E16817139028)  - 64.99 Corsair CX600 600w PSU

[http://www.newegg.com/Product/Product.aspx?Item=N82E16811553002](http://www.newegg.com/Product/Product.aspx?Item=N82E16811553002)  - 89.99 COUGAR case

Basically, don't skimp on the power supply.  Skimp just a bit on the CPU.  Maybe get a  good heatsink/fan.  *Maybe* get a Phenom instead of an  Athlon, for the few games that will take advantage of L3 cache, but it's  another **nearly negligible** difference.  (and if you like Intel.. get a core i3 or i5.. or even older are still fine like Core2)

Just remember that when you're on a budget and using Linux, the Bleeding Edge of Hardware is a double edged sword.

Core2's aren't very efficient power-wise.  I helped a friend of mine OC a 1st-gen and it heated up the dorm room by 18 degrees :o (yes, literally.  we measured it-from ~72 to ~90)  We wanted to watch some massive battles in Rome: Total War.  We did, but we were sweating... so after that we cut back on the over-clock it hahaha

I have a second-gen Core2 Duo (aka the 45 nm ones).  I love it.  I've had it for about 4 years now and it still plays ALL of the latest games (Skyrim plays very well on High, with AA and AF to boot).  It doesn't get too hot, either.  One day when doing annual cleaning (tee hee) I noticed that there was a piece of grass that was obstructing the fan.  I have no idea how long it had been there, but my guess is months.  Despite that, I had no problems, even with my 20% overclock.  I have a similar story with my GPU (8800GT).  It looked perfectly clean on the outside, so I had NEVER cleaned it, until last week.  Though clean on the outside, it was 100% stopped up on the inside.  It has probably been like that for years.  Still going strong, though.  :)

Honestly, I can't really justify upgrading the computer.  If you want to go that route, I'm sure you can find a similar setup on craigslist (or just post for an e8400 setup with 8800GT.  It is a very popular build).  You could probably get the whole tower off of someone who wants to upgrade for a couple hundred bucks.

---

### Post by Nixarter on 2012-07-27
> **tjeremiah said:**
>  I managaed to dig up an old HDD that was hardly used and  think its too old to work with any modern motherboard. Here it is :
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822148034](http://www.newegg.com/Product/Product.aspx?Item=N82E16822148034)

Im looking at the cable attached to it and have no idea what it is. So a new HDD will be ordered. Mainly 500GB.

That hard drive will work with any modern motherboard.  It is SATA version 1 (SATA I).  It uses standard connectors for power and data that standard SATA I/II/III drives use.  All SATA standards are backward-compatible with SATA I drives.

Pretty much all power supplies now have SATA power connectors, but if yours doesn't, you can use one of [these](http://www.newegg.com/Product/Product.aspx?Item=N82E16812119010) to adapt standard molex connectors to SATA.  The SATA connectors are the black ones.

The Data cables for SATA look like [this](http://www.newegg.com/Product/Product.aspx?Item=N82E16812119270).  Unless the motherboard you get is a refurbished one, it should come with a couple SATA cables.  Any SATA cables would work with that drive.

---

### Post by tjeremiah on 2012-07-27
> **Nixarter said:**
> That hard drive will work with any modern motherboard.  It is SATA version 1 (SATA I).  It uses standard connectors for power and data that standard SATA I/II/III drives use.  All SATA standards are backward-compatible with SATA I drives.

Pretty much all power supplies now have SATA power connectors, but if yours doesn't, you can use one of [these](http://www.newegg.com/Product/Product.aspx?Item=N82E16812119010) to adapt standard molex connectors to SATA.  The SATA connectors are the black ones.

The Data cables for SATA look like [this](http://www.newegg.com/Product/Product.aspx?Item=N82E16812119270).  Unless the motherboard you get is a refurbished one, it should come with a couple SATA cables.  Any SATA cables would work with that drive.
oh ok thanks :)

---

### Post by bilnovile09 on 2012-07-27
I Think 430 Watt is Not Good, Maybe you must take Up To 500 Watt for your safety

---

### Post by tjeremiah on 2012-07-31
Thank you all for the help :). After days of thinking I've finally made a final build of parts. I will do the ordering today but will put it on hold [_B]IF[/B]_ someone points a out **[COLOR="Red"]CRITICAL FLAW[/COLOR]** in the parts I selected. Quick responses are welcomed becomes most of the promos expire today. Anyway, here is my list. 

[COLOR="Red"]TOWER[/COLOR] - [http://www.newegg.com/Product/Product.aspx?Item=N82E16811147108](http://www.newegg.com/Product/Product.aspx?Item=N82E16811147108) Heres the new tower I selected. Its cheaper and with the promo code its 5% off. 

Video of TOWER : [https://www.youtube.com/watch?v=BMxaGVG6PX4&feature=player_embedded](https://www.youtube.com/watch?v=BMxaGVG6PX4&feature=player_embedded)

[COLOR="red"]POWER[/COLOR] - [http://www.newegg.com/Product/Product.aspx?Item=N82E16817104097](http://www.newegg.com/Product/Product.aspx?Item=N82E16817104097) playing it safe as suggested with 500w. 10% off with promo code

[COLOR="red"]MOTHERBOARD [/COLOR]- [http://www.newegg.com/Product/Product.aspx?Item=N82E16813157326](http://www.newegg.com/Product/Product.aspx?Item=N82E16813157326)

[COLOR="red"]CPU[/COLOR] - [http://www.newegg.com/Product/Product.aspx?Item=N82E16819116507](http://www.newegg.com/Product/Product.aspx?Item=N82E16819116507) Remains the same.

[COLOR="red"]GPU[/COLOR] - [http://www.newegg.com/Product/Product.aspx?Item=N82E16814102969http://www.newegg.com/Product/Product.aspx?Item=N82E16814102969](http://www.newegg.com/Product/Product.aspx?Item=N82E16814102969http://www.newegg.com/Product/Product.aspx?Item=N82E16814102969) $90 after rebate plus FREE Dirt Game

[COLOR="red"]RAM[/COLOR] - [http://www.newegg.com/Product/Product.aspx?Item=N82E16820144509](http://www.newegg.com/Product/Product.aspx?Item=N82E16820144509) Not all to sure this will support my motherboard. Need some help here :mad:

[COLOR="red"]HDD[/COLOR] - Some 3yr old 120GB from a computer that was hardly used. 

[COLOR="red"]Monitor/Keyboard/Mouse[/COLOR] - I already have. 

Overall this is it. Again, if someone fails to point out a "D'oh" moments based on the list ive made, I will do the ordering this afternoon. Again, thanks.

Total - $512

---

### Post by drmrgd on 2012-07-31
You can usually find out what RAM is supported by looking up the motherboard's Qualified Vendor List (QVL).  While other RAM may work, this list usually reflects what's been tested and proven to work.  

Doing a quick search for this board, I find:

[http://www.asrock.com/mb/memory.asp?Model=B75M-GL](http://www.asrock.com/mb/memory.asp?Model=B75M-GL)

I couldn't find that particular model number in the list, but based on the specs, I believe it will work.  You can always contact their customer support to be sure before you buy, though.

---

### Post by kingtiger01 on 2012-07-31
> **Frogs Hair said:**
> Make sure you have a large enough power supply for the graphics card and other hardware. You will have poor performance if you don't .

x2, was just thinking this... 400w is not enough to sustain... Remember output at 80*f/thermal Will be closer to 360w if youre lucky... its best to go about 100w above the suggested. Minimum of 500w...

Although i can say from expierence, BE CAREFUL... those style coolers dont do much... they just blow the hot air from the case onto a 150*F GPU...

Ive burned out a GPU from not paying attention and having that happen when i first started out. Rear-Venting Fans are worth the investment.

----

As far as CPU Debate, Its a real pain any way you look. Intel price range i think is outrageos anymore, and honestly Price-per-watt is not worth it... - As far as AMD, im still running a Original Phenom(x3), and have been happy for years... 

Price Wise, AMD is Superior, Performance Wise, Intel is still Superior(Core Performance). Although, if youre using Threaded Applications that wreak havoc on multi-core'd Systems. Id go for AMD's AMD FX-8 series(I have a 8150 in the Office and LOVE it), and its power-management features(with the right motherboard) are hard to beat...

---------

As far as APU's go, There Pointless. Hybrid Design's like that dont provide the Gaming Performance youre expecting. On Top of that, you Would have to use 2 Monitors to Benifit from such a Setup...

Its not like Rendering will be processed on the APU and sent to the GPU... There Independant...

So you would literally have to switch between the Ports or Monitors just to play any modern games... - Honestly in my 2 cents, not worth owning unless its shared system or a micro-server.

------

As far as GPU's Go, FGLRX and Radeon(Gallium3D) has its problems, and the fglrx team Is lazy... But Hardware Wise, i love AMD still... Hard to beat... Honestly though, For support purposes NVIDIA wins hands-down, but if you want to keep in budget, and dont mind not running on the Bleeding-Edge of Linux-Kernels/Xorg Stick with AMD.

-----

PS - i picked up a 5750 for $65 brand new on Ebay, Verified. Been using it for the last 5 months and love it. I dont really see a huge point in 65xx-/76xx- ,remember as far as versions go, its usually safe to say 57xx > 65xx > 75xx, but the performance of the 57xx cant be compared to the 65xx/75xx series, but its, its couterpart.

Only real Benifit to owning a 7xxx series is VAAPI and OPENCL for linux, there was "Slight" improvements to OpenCL... But thats not to say, that the 57xx cannot perform the same task. Not to mention alot better gaming performance than a sub-par 75xx card...
DirectX 11.1 and OpenGL 4.2 are application Dependant, and honestly mean nothing right now... Worse part is, unless youre using a 79xx+ card, youre not even getting OpenGL4.2 Hardware Support... its a 6850 and 6870 with a 7xxx label... Same core, smaller Die.

---

### Post by tjeremiah on 2012-07-31
> **kingtiger01 said:**
> 

Although i can say from expierence, BE CAREFUL... those style coolers dont do much... they just blow the hot air from the case onto a 150*F GPU...

Ive burned out a GPU from not paying attention and having that happen when i first started out. Rear-Venting Fans are worth the investment.

----

As far as CPU Debate, Its a real pain any way you look. Intel price range i think is outrageos anymore, and honestly Price-per-watt is not worth it... - As far as AMD, im still running a Original Phenom(x3), and have been happy for years... 

Price Wise, AMD is Superior, Performance Wise, Intel is still Superior(Core Performance). Although, if youre using Threaded Applications that wreak havoc on multi-core'd Systems. Id go for AMD's AMD FX-8 series(I have a 8150 in the Office and LOVE it), and its power-management features(with the right motherboard) are hard to beat...

---------

As far as APU's go, There Pointless. Hybrid Design's like that dont provide the Gaming Performance youre expecting. On Top of that, you Would have to use 2 Monitors to Benifit from such a Setup...

Its not like Rendering will be processed on the APU and sent to the GPU... There Independant...

So you would literally have to switch between the Ports or Monitors just to play any modern games... - Honestly in my 2 cents, not worth owning unless its shared system or a micro-server.

------

As far as GPU's Go, FGLRX and Radeon(Gallium3D) has its problems, and the fglrx team Is lazy... But Hardware Wise, i love AMD still... Hard to beat... Honestly though, For support purposes NVIDIA wins hands-down, but if you want to keep in budget, and dont mind not running on the Bleeding-Edge of Linux-Kernels/Xorg Stick with AMD.

-----

PS - i picked up a 5750 for $65 brand new on Ebay, Verified. Been using it for the last 5 months and love it. I dont really see a huge point in 65xx-/76xx- ,remember as far as versions go, its usually safe to say 57xx > 65xx > 75xx, but the performance of the 57xx cant be compared to the 65xx/75xx series, but its, its couterpart.

Only real Benifit to owning a 7xxx series is VAAPI and OPENCL for linux, there was "Slight" improvements to OpenCL... But thats not to say, that the 57xx cannot perform the same task. Not to mention alot better gaming performance than a sub-par 75xx card...
DirectX 11.1 and OpenGL 4.2 are application Dependant, and honestly mean nothing right now... Worse part is, unless youre using a 79xx+ card, youre not even getting OpenGL4.2 Hardware Support... its a 6850 and 6870 with a 7xxx label... Same core, smaller Die.

you just made my head hurt even more :( . Building computers is a very confusing task. I know about AMD and Intel but based on reviews, intel beats AMD. But I like AMD because they are cheaper but the intel I selected seems to be good for its price too and isnt a power sucker.

As for the tower, are you telling me it sucks? If putting fans in the rear is best maybe I can unscrew one and add to the back of the tower :(

As for the GPU, I'd love to get Nvidia but couldn't find one that didn't require an additional powerplant to run. AMD here seems reasonable performance wise and price wise. BUT as you pretty much just told me, gettings a 7000 series,the one that I selected isnt worth the price correct. If so I should just get a 6870 and call it a day?

Also would any PCI 2.0 graphic card work in a PCI 3.0 slot. This build here is my test run and also will be something im going to be using for years to come.

---

### Post by tjeremiah on 2012-07-31
ordering all parts in 2hrs.

---

### Post by tjeremiah on 2012-07-31
Alright, everything is ordered :) . Thank you all. The bulding will begin on Friday and i'll let you guys know how that went.

---

### Post by drmrgd on 2012-07-31
Cool!  Good luck with the new build! :D

---

### Post by oldfred on 2012-07-31
Now the big questions. UEFI or BIOS? gpt or MBR? Dual booting with Windows? You can only use gpt partitioning with Windows in UEFI mode. But if drive is only Ubuntu it can be either gpt or MBR.

Arch had some good technical info. Some 'light' reading while you wait for delivery of the parts.

Grub2 efi info ArchLinux - Arch but grub2 is grub2 with maybe minor differences by distribution
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)

[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

Most new motherboards are UEFI, but will also boot in BIOS mode depending on how you install.

---

### Post by tjeremiah on 2012-08-01
> **oldfred said:**
> Now the big questions. UEFI or BIOS? gpt or MBR? Dual booting with Windows? You can only use gpt partitioning with Windows in UEFI mode. But if drive is only Ubuntu it can be either gpt or MBR.

Arch had some good technical info. Some 'light' reading while you wait for delivery of the parts.

Grub2 efi info ArchLinux - Arch but grub2 is grub2 with maybe minor differences by distribution
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)

[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

Most new motherboards are UEFI, but will also boot in BIOS mode depending on how you install.
wow. Thanks for the info.

---

### Post by mips on 2012-08-01
Did you buy a AMD/ATI GPU?

Can't see from your link as the item has been deactivated.

---

### Post by tjeremiah on 2012-08-01
> **mips said:**
> Did you buy a AMD/ATI GPU?

Can't see from your link as the item has been deactivated.

AMD/ATI. I know, its a gamble but apparently the card doesnt suck up a lot of power to operate. Wont be able to run games @ 1080p (dont have a 1080p monitor anyway) but im ok with that for now. 

If I screw up ill just learn from it.

---

### Post by mips on 2012-08-01
> **tjeremiah said:**
> AMD/ATI. I know, its a gamble but apparently the card doesnt suck up a lot of power to operate. Wont be able to run games @ 1080p (dont have a 1080p monitor anyway) but im ok with that for now. 

If I screw up ill just learn from it.

Which brand/model did you end up getting.

I have heard things have improved on the AMD/ATI side when it comes to linux drivers so hopefully it works out well for you. Let us know how it performs with the new 12.6 Catalyst drivers.

If I was a windows only user I would not worry whether I buy ati or nvidia but it would be really great if amd is up there with nvidia when it comes to their linux drivers.

---

### Post by tjeremiah on 2012-08-01
> **mips said:**
> Which brand/model did you end up getting.

I have heard things have improved on the AMD/ATI side when it comes to linux drivers so hopefully it works out well for you. Let us know how it performs with the new 12.6 Catalyst drivers.

If I was a windows only user I would not worry whether I buy ati or nvidia but it would be really great if amd is up there with nvidia when it comes to their linux drivers.
SAPPHIRE Radeon HD 7750

---

### Post by tjeremiah on 2012-08-01
Just noticed a "D'oh" moment as I was looking over everything for the heck of it. 

The tower was updated from the video that is shown on the NEWEGG. Instead of one USB 3.0 with an adapter to connect it from the front to the back of the case, there is now two USB 3.0 in the front panel and it doesnt come with an adapter. Instead it needs to connect to a motherboard that has a 20pin connector. Looking at my motherboard, no 20pin connector :(. So those two usb 3.0s are going to be useless...

Damn, already a screw up and the thing hasnt arrived yet. Cant believe I missed this...

---

### Post by mips on 2012-08-02
> **tjeremiah said:**
> Just noticed a "D'oh" moment as I was looking over everything for the heck of it. 

The tower was updated from the video that is shown on the NEWEGG. Instead of one USB 3.0 with an adapter to connect it from the front to the back of the case, there is now two USB 3.0 in the front panel and it doesnt come with an adapter. Instead it needs to connect to a motherboard that has a 20pin connector. Looking at my motherboard, no 20pin connector :(. So those two usb 3.0s are going to be useless...

Damn, already a screw up and the thing hasnt arrived yet. Cant believe I missed this...

Get a USB3 PCI card.

---

### Post by tjeremiah on 2012-08-02
items have arrived! One note so far, the case is freaking huge and looks way better in person. Doesnt feel like a "cheap" $40 case either ( well, i assume as this is my very first purchase of a case).

---

### Post by TheMTtakeover on 2012-08-02
> **tjeremiah said:**
> items have arrived! One note so far, the case is freaking huge and looks way better in person. Doesnt feel like a "cheap" $40 case either ( well, i assume as this is my very first purchase of a case).

Great! Hope the build goes well. Keep us updated.

---

### Post by tjeremiah on 2012-08-02
[SIZE="3"]**[COLOR="DarkOrange"]+[/COLOR]**[/SIZE] Ok, first the positives I see so far. The case I mentioned to me feels like a steal. Though I havent been able to see if all fans can be plugged or will operate well, the case feels solid and well built. 

Another good thing is the power supply. I can't hear the fan at all when it was powered on. Even when I placed my ear near it, nothing. The stock fan is pretty silent too. 

During the test run, I powered up the motherboard, put in the CPU carefully, stock fan,  and applied a VGA to my TV and everything seems to be working. I was greeted with the new "BIOS" setting screen which allows you to navigate with a mouse. 

[SIZE="3"][COLOR="Red"]**- **[/COLOR][/SIZE]Now, what looks to be a HUGE "D'oh" moment. Remember the HDD I said I took out from an old computer that was hardly used (HDD is about 3yrs old). Well, apparently im going to have to buy one that is compatible with my pc. Below are the pictures I took at the inputs of the HDD and the cables that came with my Motherboard. The grey thick cable with blue end is from my old motherboard and was attached to the HDD when I ripped it out the old case.

Neither looks like they were meant to be together. This is a HUGE screw up on my part. 

However I do see that Sata plug from the power supply to power it up but that cant be it right, something connected from the HDD must be in the motherboard correct?

Sorry for the poor q. pictures. Using phone.

---

### Post by TheMTtakeover on 2012-08-02
> **tjeremiah said:**
> [SIZE="3"]**[COLOR="DarkOrange"]+[/COLOR]**[/SIZE] Ok, first the positives I see so far. The case I mentioned to me feels like a steal. Though I havent been able to see if all fans can be plugged or will operate well, the case feels solid and well built. 

Another good thing is the power supply. I can't hear the fan at all when it was powered on. Even when I placed my ear near it, nothing. The stock fan is pretty silent too. 

During the test run, I powered up the motherboard, put in the CPU carefully, stock fan,  and applied a VGA to my TV and everything seems to be working. I was greeted with the new "BIOS" setting screen which allows you to navigate with a mouse. 

[SIZE="3"][COLOR="Red"]**- **[/COLOR][/SIZE]Now, what looks to be a HUGE "D'oh" moment. Remember the HDD I said I took out from an old computer that was hardly used (HDD is about 3yrs old). Well, apparently im going to have to buy one that is compatible with my pc. Below are the pictures I took at the inputs of the HDD and the cables that came with my Motherboard. The grey thick cable with blue end is from my old motherboard and was attached to the HDD when I ripped it out the old case.

Neither looks like they were meant to be together. This is a HUGE screw up on my part. 

However I do see that Sata plug from the power supply to power it up but that cant be it right, something connected from the HDD must be in the motherboard correct?

Sorry for the poor q. pictures. Using phone.

Are you saying that your hard drive has a PATA connection and you are trying to use a SATA cable?

---

### Post by drmrgd on 2012-08-02
Yeah, what you have is an IDE drive, and likely the new gear is all going to be SATA.  I think you can get an adaptor.  But, to be honest, hard drives aren't all that expensive these days, and you'll be better off just getting a new one.  Plus the transfer speed will be a little quicker, which is nice.  

Also, the power connector for SATA devices and the data connector look similar.  However, the data cable is more narrow than the power cable; there is a difference from the old molex power cables.

---

### Post by tjeremiah on 2012-08-02
> **drmrgd said:**
> Yeah, what you have is an IDE drive, and likely the new gear is all going to be SATA.  I think you can get an adaptor.  But, to be honest, hard drives aren't all that expensive these days, and you'll be better off just getting a new one.  Plus the transfer speed will be a little quicker, which is nice.  

Also, the power connector for SATA devices and the data connector look similar.  However, the data cable is more narrow than the power cable; there is a difference from the old molex power cables.

huge bummer :(. I should of took a pic of the HDD to show you guys days ago . Im going to order one later or maybe go to BESTBUY tomorrow assuming I dont see a good deal on NEWEGG. Maybe go with a 500GB HDD. 

Well I guess as I wait, im going to install the motherboard into the case and power up the fans in the mean time. Again,thank you.

---

### Post by tjeremiah on 2012-08-02
> **TheMTtakeover said:**
> Are you saying that your hard drive has a PATA connection and you are trying to use a SATA cable?

just googled PATA and yeah :(. Im just going to buy a new HDD one later and call it a day. I guess this is what I get for trying to cut corners.

---

### Post by oldfred on 2012-08-02
Many new motherboards usually have one PATA connection. More for legacy PATA CD/DVDs. 

with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
[http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1](http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1)

I converted to SATA only with my 'new' build in 2006. Samsumg just came out with a SATA DVD that was only $10 extra, the week I went shopping for parts. Sony was the only one before with a SATA DVD and it 50% more that PATA.

I used to have so much trouble with PATA connections coming loose when I mucked around in case that I really wanted something better.

---

### Post by mips on 2012-08-03
> **tjeremiah said:**
> just googled PATA and yeah :(. Im just going to buy a new HDD one later and call it a day. I guess this is what I get for trying to cut corners.

Just go check out bestbuy else you have to wait again for delivery.
Just make sure you get a 7200rpm drive with 32-64MB cache. The 5400rpm drives are really slow for having your OS loaded on, for storage alone they are fine.

---

### Post by tjeremiah on 2012-08-03
> **mips said:**
> Just go check out bestbuy else you have to wait again for delivery.
Just make sure you get a 7200rpm drive with 32-64MB cache. The 5400rpm drives are really slow for having your OS loaded on, for storage alone they are fine.

i'll be heading there tomorrow. How much you think is a reasonable price for this spec and say about 250GB or 500GB?

Also I installed the motherboard. Hows my cable management? 

Theres one problem though, I dont know if this is normal but I plugged the top fan into Chassis fan on the motherboard. The problem is it doesnt fully operate. For example, I have to plug it out and then back in for it to start. Aftr it starts it shutsdown in about 2 minutes. When that happens, the "BIOS" reads : N/A. The back fan is plugged into the motherboard too but has no such problem. 

Is this normal?

---

### Post by mips on 2012-08-03
> **tjeremiah said:**
> i'll be heading there tomorrow. How much you think is a reasonable price for this spec and say about 250GB or 500GB?

Also I installed the motherboard. Hows my cable management? 

Theres one problem though, I dont know if this is normal but I plugged the top fan into Chassis fan on the motherboard. The problem is it doesnt fully operate. For example, I have to plug it out and then back in for it to start. Aftr it starts it shutsdown in about 2 minutes. When that happens, the "BIOS" reads : N/A. The back fan is plugged into the motherboard too but has no such problem. 

Is this normal?

Well get some prices of newegg tonight for comparison, if best buy is like $10-30 more then I would still buy just for the convenience but that's me.

As for cable management I recon you could invest in some small cable ties (I think you guys call them zip ties over there). It's not bad but it could be better.

---

### Post by tjeremiah on 2012-08-03
while I make up my mind im going to be running UBUNTU via LIVE USB. :guitar:

I've been doing some searching with the HDD specs I should be looking for and see some good prices. This is the one im aiming for. 

[http://www.newegg.com/Product/Product.aspx?Item=N82E16822236070](http://www.newegg.com/Product/Product.aspx?Item=N82E16822236070)

I'm going to go to BESTBUY later and see if they have it for less or at that same price.

---

### Post by mips on 2012-08-03
No, stay away from green drives for your main OS drive. They are slow and have very aggressive power management.

Rather get one of these,
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822236339](http://www.newegg.com/Product/Product.aspx?Item=N82E16822236339)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822236342](http://www.newegg.com/Product/Product.aspx?Item=N82E16822236342)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822136533](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136533)

The WD Caviar black being the best in the bunch.

---

### Post by tjeremiah on 2012-08-04
thanks. I've settled with the BLACK verison, 500GB for $50. Should be here on Monday.7200 32mb 3gbs. I read the mechanical drives dont really benefit with SATA 6gbs. I'll save that port for an SSD in the future.

EDITED!

---

### Post by tjeremiah on 2012-08-10
Final update. Installed the HDD the other day and everything is running smoothly. I've only been able to run Windows 8 so far (which was a bit crazy to use at first) so that I can test all the drivers. Ubuntu will come later. Again and again, thank you all for the help! :)

---

