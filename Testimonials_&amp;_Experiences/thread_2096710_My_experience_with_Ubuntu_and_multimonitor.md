---
title: "My experience with Ubuntu and multimonitor"
date: 2012-12-20
forum: Testimonials &amp; Experiences
---

### Post by yenic on 2012-12-20
I gave Ubuntu 12.04LTS another shot because Valve is bringing Steam to the platform. I wanted to share my experience and gather any recommendations from the community on it.

Everything went without a hitch besides the video driver. I have a Radeon 5870. I tried the latest official release (12.10) from AMD's website, following the instructions in their documentation and it never did work right. It didn't seem to integrate properly with Ubuntu. I uninstalled those and tried the open source driver again, that seemed to crash randomly (screen would flicker then end up garbled and unusable until a reboot). 

What ultimately worked is the fglrx driver in 'additional drivers' after doing an uninstall of the AMD 12.10 fglrx drivers. The post-release version did not install at all. Resulting with an error and then causing the original set (if installed first) to no longer show as being installed.

After installing the base proprietary driver from additional drivers, and running aticonfig --initial, I was able to get my dual monitor setup to work properly by enabling the Xinerama feature that supposedly allows you to drag windows to other desktop environments. This also disables the display properties built into Ubuntu.

This got my dual monitor setup to work, kind of. 

Issues that remained: The task bar was miscolored and I had a strange invisible line in the middle of the desktop that would stop the cursor for a moment as if it was the dividing line between two screens.
Also anytime I plugged in my HDMI HDTV with my dual DVIs and restarted the computer it made the HDMI the primary display. Even if disabled before a restart. So I'd have to turn on the TV, and use my Logitech DiNovo Mini to change it back to my primary display.
I also never found a way to setup multimonitor profiles as in the Windows CCC. In Win7 I have two profiles, one for my dualmonitor setup and another that disables both and activates the HDTV/HDMI.

I'd like to switch over completely to Ubuntu, but need one of two things  at minimum: 
-my multimonitor setup to work, -or all of my games to work.
With neither working (or working easily.. I spent over a day on this, and I'm not a fool, I'm  a hobbyist Python developer and a sysadmin for a day job) I can't take the dive yet . 

For a single monitor user, the experience would be pretty much flawless. Although I don't know if Linux users chase down the latest goodies as I do on Windows (chipset infs, Intel RSTs, ssd toolkits, video drivers, Renesas/NEC USB3.0 controller drivers ect), or if that doesn't really apply.

I've removed my Ubuntu partition for now, and am back to just  Windows. 
I do run Ubuntu in a VM just for development reasons. I've been trying to make the move off of Windows, as I already use FOSS tools for everything I do.

If I were to buy a Nvidia card will the experience be the same? I would do so if it works properly with my multimonitor profile requirements. The games part I can work around with a small Win7 partition solely for games that won't run well under WINE.

Just my experience with a day of tinkering with Ubuntu 12.04LTS.
Thanks for reading.

---

### Post by overdrank on 2012-12-20
Moved to Ubuntu Testimonials & Experiences

---

### Post by yenic on 2012-12-20
It is a testimonial but I'd like feedback on what I did wrong or if I need to buy a Geforce..

---

### Post by QIII on 2012-12-20
Hold on to your money.  One of my machines is a dual monitor setup with a 5870 and it works fine.

On my cell phone now and not at home, but I can give you a couple of hints.

Don't turn Xinerama on.  There are settings in CCC to extend your workspace across two monitors.  Xinerama is useful for four monitors on two cards, for instance.

The pause or delay as your cursor moves from monitor to monitor is something you can adjust in Ubuntu itself.  I believe it is called "sticky edges".

---

### Post by yenic on 2012-12-20
> **QIII said:**
> Hold on to your money.  One of my machines is a dual monitor setup with a 5870 and it works fine.

On my cell phone now and not at home, but I can give you a couple of hints.

Don't turn Xinerama on.  There are settings in CCC to extend your workspace across two monitors.  Xinerama is useful for four monitors on two cards, for instance.

The pause or delay as your cursor moves from monitor to monitor is something you can adjust in Ubuntu itself.  I believe it is called "sticky edges".

I assumed sticky edges could be turned off, I got a sticky edge in the middle of my center monitor though (horizontally).  The sticky edges otherwise were welcome additions. 

Even if I got dual monitors to work well, the lack of monitor profiles (from dual to a single HDTV) would be a showstopper. 

I can let go of most of my games, or spend time tinkering with them, or just keep a small Win7 partition for them.. but the overall video driver situation was a headache. I wouldn't expect anyone else to get it going without a few days of investment with trial and error.

---

### Post by mastablasta on 2012-12-21
> **yenic said:**
>  
I can let go of most of my games, or spend time tinkering with them, or just keep a small Win7 partition for them.. but the overall video driver situation was a headache. I wouldn't expect anyone else to get it going without a few days of investment with trial and error.
 
well because overall you are doing it wrong. 
 
- first in ubuntu you don't have to download drivers from manufacturers website. instead you use built in tools to install them (for 12.04 the tool i called jockey).
- second you can't just slap 12.10 drivers to 12.04 ubuntu. well at least not without extra work.
- third - linux drivers are mostly part of kernel so you received them along with other updates.
- fourth - windows games are best run on windwos because they are windows porgrammes. eventhough they ported steam to linux, games that are sold there are not all ported to linux. in short dont' expect windows games to work on linux though some of them do quite nicely = it's a miracle.
 fifth - you might try another desktop environment. i am not sure unity was really made with dual monitors in mind. though some people use it. but perhaps you migth get more comfortable with someting like KDE (kubuntu).
 
for ATI/AMD experience on linux the entity responsible is not Ubuntu as they can't do much about it but AMD. the community did it's best to reverse engineer the drivers (called opensource). AMD and nvidia keep their drivers locked. i guess they give them competitive advantage over the other. Intel on the other hand has opensource drivers so their chips work well on linux. but the problem is their chips aren't as strong.

---

### Post by orb9220 on 2012-12-21
> "Intel on the other hand has opensource drivers so their chips work well on linux. but the problem is their chips aren't as strong."

How could they Do That don't they know they are losing "The Competitive Edge" :-P

And agree for games have a separate windows partition. Linux still not ready for the masses even with Steam. And many spend god awful time trying to make it work when they could be playing a game and have more game choices to boot.
.

---

### Post by Tamlynmac on 2012-12-21
>    	orb9220
And many spend god awful time trying to make it work when they could be playing a game and have more game choices to boot.

Perhaps, some of those users enjoyed the learning experience and found learning to be more productive. There's always time for games, but learning is something that can benefit one in life. I've taken every opportunity in my life to learn and it's paid off many times.

I realize that some users truly enjoy gaming, but IMHO games don't hold a candle to learning something new that may enhance my life by improving my knowledge base. While games are entertaining, learning is that which not only enhances the individual, but often improves the quality of their life.

Just my $0.02

---

### Post by orb9220 on 2012-12-21
> **Tamlynmac said:**
> Perhaps, some of those users enjoyed the learning experience and found learning to be more productive. There's always time for games, but learning is something that can benefit one in life. I've taken every opportunity in my life to learn and it's paid off many times.

I realize that some users truly enjoy gaming, but IMHO games don't hold a candle to learning something new that may enhance my life by improving my knowledge base. While games are entertaining, learning is that which not only enhances the individual, but often improves the quality of their life.

Just my $0.02

True enough I also rarely game. And find learning new things in subjects I am passionate about. 
Photography and Learning Linux more at the moment.

But some are just as passionate about games. And I leave them at that with their passions which maybe different than mine.
.

---

### Post by yenic on 2012-12-22
I grew up on games (Commodore/Atari2600/MSDOS/NES/Genesis) and if you find the right games they are awesome. For years I stopped gaming, and lately only enjoy very few games. I'm picky as can be in my old age, and being selfish with my time. But, if you haven't experienced a DOTA game like League of Legends.. it's pretty addictive, and enough fun I don't classify it as a waste of time. It's genuinely as enjoyable as a book or movie, possibly more so due to the competition. And more addictive once you become great at the game. My habit is far less expensive than some who go out and drink every weekend, give money to the pope or gamble..

> **mastablasta said:**
> well because overall you are doing it wrong. 
 
- first in ubuntu you don't have to download drivers from manufacturers  website. instead you use built in tools to install them (for 12.04 the  tool i called jockey).
- second you can't just slap 12.10 drivers to 12.04 ubuntu. well at least not without extra work.
- third - linux drivers are mostly part of kernel so you received them along with other updates.
- fourth - windows games are best run on windwos because they are  windows porgrammes. eventhough they ported steam to linux, games that  are sold there are not all ported to linux. in short dont' expect  windows games to work on linux though some of them do quite nicely =  it's a miracle.
 fifth - you might try another desktop environment. i am not sure unity  was really made with dual monitors in mind. though some people use it.  but perhaps you migth get more comfortable with someting like KDE  (kubuntu).
 
for ATI/AMD experience on linux the entity responsible is not Ubuntu as  they can't do much about it but AMD. the community did it's best to  reverse engineer the drivers (called opensource). AMD and nvidia keep  their drivers locked. i guess they give them competitive advantage over  the other. Intel on the other hand has opensource drivers so their chips  work well on linux. but the problem is their chips aren't as  strong.

Thanks for this. I really don't know how the Linux world works. I  installed RedHat about 15 years ago, didn't have much use for it and  went back to Windows.

I'll look at Kubuntu, as overall I've never  been impressed with Windows. Not 3.0, not 95, not XP, 2K , Vista or 7  (or anything before or inbetween). 

I always found the UI to be  exactly what I would not design and overall pretty clunky and  unintuitive. Ubuntu works for me because of Unity, it's closer to what a  rational person would design IMO. 

People don't like change, so  the Windows style is preferred. But I never liked the Windows UI, and it  got worse going from XP to 7. 
A good example would be the alt-tab behavior.. they had this right in XP, where you knew exactly what had a new notification by the color-change behind the icon.

That said, I do run Ubuntu with dual monitors. Just in a VM on a Windows desktop. I don't mind how Ubuntu functions with a dual monitor setup (I have a 1920x1200 and a 1050x1680 display). It gives me the native environment I need for my dabbling in C coding and my preferred environment for Python. It's just sluggish in comparison and it's hard to really get lost in the experience which is why I wanted to try a native install again.

---

### Post by yenic on 2012-12-22
> **Tamlynmac said:**
> Perhaps, some of those users enjoyed the learning experience and found learning to be more productive. There's always time for games, but learning is something that can benefit one in life. I've taken every opportunity in my life to learn and it's paid off many times.

I realize that some users truly enjoy gaming, but IMHO games don't hold a candle to learning something new that may enhance my life by improving my knowledge base. While games are entertaining, learning is that which not only enhances the individual, but often improves the quality of their life.

Just my $0.02

I agree with this. Oddly enough though, I learned a lot about computers just trying to get games to run. :P I program in Python in my spare time, it's always good to be productive. I followed this ideal too much in the past though, I've come to appreciate the value of being entertained. 

As long as you're not the average American (I'm from the US so this is my best point of reference), and just watching tv, and you're productive at least some of the time learning something new. 

Reading a book is IMO one of the strongest things you can do for your mind and overall betterment of yourself. It's underrated, and I mean a real book that's been edited, the internet in most cases doesn't utilize the same level of literature/vocabulary.

Games are good for you too, but not to the same degree. They are better than television which is a 1 way activity. Even if it's twitch brain reaction, it's better than no brain reaction. :P I should note I no longer play, nor really ever enjoyed games that pit man vs man. I prefer a scifi setting or something with a united mankind. It's even worse when its USA vs China or something insanely propagandized like that like the Battlefield series. I think we have enough war and internal strife on earth that is going to contribute to our extinction, and if something as simple as not encouraging such a game plays a small role in that, I support that.

---

### Post by Tamlynmac on 2012-12-23
> yenic
Reading a book is IMO one of the strongest things you can do for your  mind and overall betterment of yourself. It's underrated, and I mean a  real book that's been edited, the internet in most cases doesn't utilize  the same level of literature/vocabulary.

Something about  holding a bound book in your hand. I know it's old school, but the  smell and feel of a book can't be beat. I agree with you 100% with  respect to reading, it's both my wife's and my fav past time. Except  for enjoying the rocky mountains (our back yard).  :grin:

*  The OP suggested that users could be playing games instead of making Ubuntu/Linux work. I was simply suggesting that "some" of those users  might truly enjoy  stepping outside their comfort zone to make it work. I didn't wish to  insinuate that games are bad, only that moderation and diversity are  IMHO just as important. The learning experience can be extremely  rewarding and by investing in that experience, we improve our knowledge  base. Hopefully, no one thought I was demeaning games -  as that was not my intent.

---

### Post by yenic on 2012-12-23
We have a Nook Simple Touch, and find a lot of books online in public domain. Some great stuff there. I have a few printed books but try to not collect them. I don't have a library card, but I would use it if I did.. here (in Chicago) you have to be a landowner and pay property tax to get a library card (without another fee).

---

### Post by lykwydchykyn on 2012-12-23
For the record, I've had almost no trouble doing dual monitors with an Nvidia card with the proprietary drivers.  Actually, since maybe 12.04, the open-source nouveau drivers seem to work fine too (at least for desktop use).

As for games, I don't have anything against them, but I personally don't want my working environment dictated to me by what game companies want to support.

If you try out Kubuntu, take one piece of advice: don't immediately dismiss it because the default layout looks like windows 7.  It's a very flexible environment that can look and behave like just about anything you want, if you take a little time to explore it.

---

### Post by Tamlynmac on 2012-12-23
> yenic
find a lot of books online in public domain. Some great  stuff there. I have a few printed books but try to not collect them.  

Yes, there's quite a few free public domain sites. I found these two sites have some nice offerings.
[http://www.smashwords.com/books/category/1213/newest/0/free/epic](http://www.smashwords.com/books/category/1213/newest/0/free/epic)
[http://www.free-online-novels.com/index.html](http://www.free-online-novels.com/index.html)

This site contains new writers that freely share their work.
[http://www.fictionpress.com/fiction/Sci-Fi/10/13/1/1/100/0/0/0/0/1/](http://www.fictionpress.com/fiction/Sci-Fi/10/13/1/1/100/0/0/0/0/1/)  

You  can download in pdf (using document reader) or I often use FBreader  which is available in the software center to read directly off my mini.  FBreader reads numerous formats including prc & mobi. I still prefer  the real thing, but our local library is rather small and has a limited  number of books available. Plus, our home will need an addition if we  purchase any more books. :wink:  Enjoy.

* I won't post in this thread again, as not to hijack or risk it's closure.

---

### Post by sffvba[e0rt on 2012-12-23
> **Ubuntu Testimonials & Experiences** Here is your opportunity to tell other forum members about your experience of Ubuntu. Please do not use this section for support questions, bug reports, or debate.

This thread has strayed from the intended purpose of this section.

***Closed.***



404

---

