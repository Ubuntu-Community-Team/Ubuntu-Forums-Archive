---
title: "Going Open-Source to Solve My Flash Woes"
date: 2008-08-17
forum: The Cafe
---

### Post by mrgnash on 2008-08-17
[IMG]http://i36.tinypic.com/23i8hfc.jpg[/IMG]

Like a number of Ubuntu users (especially those of us on 64bit systems), I have had my fair amount of 'issues' with the Flash plugin as released by Adobe. If it wasn't the crashing, then it was the tearing or weird artifacts, or not being picked up by the browser at all and so on.

Whenever Adobe releases a new version of the player for Linux, I must confess that I'm always a little excited, because I hold out the hope that 'could this be it? could this finally be the release that runs half decently on my system?' Inevitably though, I find that each release tends to alleviate some problems, while compounding or introducing others. When the latest one (the release candidate) simply would not install, I finally said 'enough', and went ahead and installed the latest unstable build of swfdec (0.7.4).

Immediately, I noticed how much better video rendering was (no tearing or noise), and was pleasantly surprised that there was none of this nonsense where transitioning back and forth between full-screen and regular playback would leave the regular version frozen at the moment you first activated full-screen mode. 

The only drawback was that performance in said mode was rather choppy, and I figured that this had something to do with xrender not being properly configured/supported by my current (binary Nvidia) driver. After mentioning this in the official swfdec irc channel, I was told that the Nouveau Nvidia drivers delivered much better performance in this area, thanks to their featuring a proper implementation of EXA/Xrender. Lo and behold, after I ditched the binary driver and installed the Nouveau driver, performance became silky smooth, even when playing videos in full-screen mode.

Not only that, but 2D performance across the board seemed to improve significantly. Window content now renders much quicker for me than it did previously, and although I doubt Compiz Fusion would work, I'm not missing out on much at all thanks to Gnome's own xrender-based compositor (I never went in for a lot of the more outlandish effects in Compiz Fusion) :)

I just thought I'd share this little story, not because I think that this is the path everyone should take -- both are still somewhat experimental projects, after all -- but rather because I am just amazed at the level of quality that these dedicated open source developers are able to achieve. As I understand it, both projects have received support/cooperation from Nvidia and Adobe respectively, but I still think that credit is due for, in some ways at least, out-performing the efforts of the big-league players ;)

---

### Post by mips on 2008-08-17
Have you tried gnash 0.8.3-3 yet?

I use it on Arch64 without any hassles so far. I also have not experienced any choppiness like you mentioned. Also have not experienced any cpu spikes like with flash where it just about freezes the pc. With 10 tabs open in firefox looking at youtube videos the highest my cpu spikes to is about 17% and after that it drops to below 10% userload. Average load over 1 minute is 2.35

---

### Post by mrgnash on 2008-08-17
> **mips said:**
> Have you tried gnash 0.8.3-3 yet?

I use it on Arch64 without any hassles so far. I also have not experienced any choppiness like you mentioned. Also have not experienced any cpu spikes like with flash where it just about freezes the pc. With 10 tabs open in firefox looking at youtube videos the highest my cpu spikes to is about 17% and after that it drops to below 10% userload. Average load over 1 minute is 2.35

No, I have not. I've never had much luck with Gnash in the past (and no, we're not related :P ), and so I haven't followed its development quite as closely as I have with swfdec. I fully support what each project is aiming to achieve though, of course.

And one thing that forget to mention in my original post above, was that I got massive CPU spikes as well -- often necessitating a reboot because performance would become so atrocious. After looking at htop, I concluded that either ndiswrapper, Flash, or Firefox was the culprit. The spikes have disappeared now, though, so I can at least rule out Firefox :P

---

### Post by keiichidono on 2008-08-17
Sweet I was just thinking about this, how do you guys find Gnash and swfdec to work with Youtube and Pandora Radio? What about youtube videos embedded in other websites? Can you provide some screenshots please? I'm interested in this but I need to know if it works with what I use. I'm tempted to go install it right now.

---

### Post by id1337x on 2008-08-17
I think all you really need is Gnash. Now a days people just use AJAX for a lot of the things Flash was used for previously. Flash is most popular for video and HTML5 will probably be the way people display video in the future.

---

### Post by billgoldberg on 2008-08-17
I must say that all my problems I had with flash are gone with the new flash player 10 release candidate.

The second beta was still a bit choppy in fullscreen, but the new RC handles it perfectly.

No choppyness, no more cpu hogging, ... 

I'm happy.

---

### Post by billgoldberg on 2008-08-17
> **id1337x said:**
> I think all you really need is Gnash. Now a days people just use AJAX for a lot of the things Flash was used for previously. Flash is most popular for video and HTML5 will probably be the way people display video in the future.

I doubt it (the thing about html 5).

---

### Post by mips on 2008-08-17
> **CalvinB said:**
> Sweet I was just thinking about this, how do you guys find Gnash and swfdec to work with Youtube and Pandora Radio? What about youtube videos embedded in other websites? .

Gnash works 100% on youtube and sites with youtube embedded videos. I cannot test Pandora as it is restricted to some countries.

---

### Post by keiichidono on 2008-08-17
I'm kind of excited now so I'll go check it out right now, I hope I don't mess anything up.

---

### Post by mrgnash on 2008-08-17
> **CalvinB said:**
> Sweet I was just thinking about this, how do you guys find Gnash and swfdec to work with Youtube and Pandora Radio? What about youtube videos embedded in other websites? Can you provide some screenshots please? I'm interested in this but I need to know if it works with what I use. I'm tempted to go install it right now.

Youtube videos work fine (see the screenshot I posted) -- both on Youtube.com itself, and with videos embedded on other sites.

---

### Post by init1 on 2008-08-17
Although Gnash claims it works with Youtube, I couldn't get a single video to play. As for swfdec, it was very choppy, far too choppy to be practical.

---

### Post by mips on 2008-08-18
> **init1 said:**
> Although Gnash claims it works with Youtube, I couldn't get a single video to play. As for swfdec, it was very choppy, far too choppy to be practical.

What version of Gnash did you try? Try 0.8.3-3. swfdec as far as I know still shows a bit of choppiness.

---

### Post by mrgnash on 2008-08-18
> **mips said:**
> What version of Gnash did you try? Try 0.8.3-3. swfdec as far as I know still shows a bit of choppiness.

As I illustrated in my original post, the choppiness in swfdec is due to xrender not being configured/supported properly. It's really a matter of video drivers needing to catch up (as Nouveau has done), rather than there it being a fault of swfdec.

---

### Post by tomrshl on 2008-08-18
Ok, gnash works better than swfdec for a couple of bits and pieces I've come across, but no youtube at all.
swfdec (and mozilla plugin) with youtube - Firefox asks me to search for a codec and tells me to download gstreamer.

Am I supposed to install gstreamer to get youtube working?

Thanks

---

### Post by mrgnash on 2008-08-18
> **tomrshl said:**
> Ok, gnash works better than swfdec for a couple of bits and pieces I've come across, but no youtube at all.
swfdec (and mozilla plugin) with youtube - Firefox asks me to search for a codec and tells me to download gstreamer.

Am I supposed to install gstreamer to get youtube working?

Thanks

Yes.

---

### Post by keiichidono on 2008-08-19
How did you install swfdec latest unstable? I tried installing the latest from the repo's but it didn't work out too well, the sound didn't work at all either. Gnash didn't work at all period.

---

### Post by aaaantoine on 2008-08-19
I'll have to try swfdec when 8.10 comes out.  With every new distribution update, I test Adobe Flash against Gnash and swfdec.  They have to pass two tests before I decide to use them: the YouTube test, and the [Homestar Runner](http://www.homestarrunner.com) test.

With 8.04, Gnash failed the HSR test with inaccurate rendering.  Swfdec failed with garbled sound playback.  So I decided to stick with Flash via nspluginwrapper for another 6 months.

Off-topic: MrGnash, can you tell me about your theme?  You can just point me to a link where you've already listed the specifics (theme, window border, font, copy of panel background), but I'd like to try some of that for myself, maybe in a different color.

---

### Post by geoken on 2008-08-19
Out of curiosity, did you try the combination of Adobe's plugin (v.10) and the neaveau(sp?) driver?

---

### Post by mrgnash on 2008-08-20
> **aaaantoine said:**
> I'll have to try swfdec when 8.10 comes out.  With every new distribution update, I test Adobe Flash against Gnash and swfdec.  They have to pass two tests before I decide to use them: the YouTube test, and the [Homestar Runner](http://www.homestarrunner.com) test.

With 8.04, Gnash failed the HSR test with inaccurate rendering.  Swfdec failed with garbled sound playback.  So I decided to stick with Flash via nspluginwrapper for another 6 months.

Off-topic: MrGnash, can you tell me about your theme?  You can just point me to a link where you've already listed the specifics (theme, window border, font, copy of panel background), but I'd like to try some of that for myself, maybe in a different color.

[You can find my theme right here](http://ubuntuforums.org/showpost.php?p=5447813&postcount=70).

I don't believe that I specified the fonts either in that post, or in the package itself but at the time they were from the Latin Modern family (LMRoman, LMRSans, LMSans-Serif). I'm using all Droid fonts now though. Also, I'm not using Compiz anymore, so my window-decoration is no longer Emerald, but Metacity instead; the name of the Metacity theme is Perezoso and is available on Gnome-look.

> How did you install swfdec latest unstable? I tried installing the latest from the repo's but it didn't work out too well, the sound didn't work at all either. Gnash didn't work at all period.

I installed the packages from [Stéphane Marguet](https://launchpad.net/~stemp/+archive)'s PPA.

As for the sound, I ran into the same problem; installing the libasound2-plugins fixed it.

> Out of curiosity, did you try the combination of Adobe's plugin (v.10) and the neaveau(sp?) driver? 

No.

---

### Post by keiichidono on 2008-08-20
I don't have Intrepid so I can't use those repo's. I also already have those plugins installed. I guess I'll just give up on this.

---

