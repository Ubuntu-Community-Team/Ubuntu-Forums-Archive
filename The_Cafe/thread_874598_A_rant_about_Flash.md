---
title: "A rant about Flash"
date: 2008-07-30
forum: The Cafe
---

### Post by th3james on 2008-07-30
I am so sick of flash! It is probably single handedly the biggest annoyance in my day to day computing. In Hardy, it crashes ALL the time, and when it doesn't crash, it fails to initialise (which might admittedly be due to my insistence on flash-block, mostly in the interests of maintaining my sanity). It hardly provides the best advert for ubuntu either when friends come over and it crashes all the time, leaving my friends with the perception that linux is unstable (trying to explain it as the problem with closed source software just makes me come across as a zealot...)
Plus, everywhere on the web seems to use it now, it's truly a sad thing that so much of our internet is tied up in a closed source standard, especially so one with no viable open decoder.
Add to this, the full screen video decoding performance is dreadful, on an nvidia 8600 and an intel core 2 2.6GHz, which is completely unacceptable, i dread to think what it's like on lesser machines.
I imagine most of the blame lies with Adobe and their neglect of the linux community, but its behavior with sound is appalling. I understand though, some of the problems may be due to pulse-audio, but it's not like this is a new thing.

All I can say is roll on a better swfdec, we need you!

/rant

Sorry, needed to get that out of my system, it's been bugging me a lot recently!!:(

---

### Post by thisllub on 2008-07-30
Yeah.
32 bit works for a while but 64 bit Flash is a tragedy.

I run any flash I need on a Windows VM.

---

### Post by adewale on 2008-07-30
Well i don't use flash. Why because some animations just simply distracts me. I've used flash on dapper,  edgy , fiesty and they never gave problems. Except once in a while, it would use as much as 80% of my processing power. 
But really adobe should have fixed this problem. Its really childish not to. Simply because the internet is tied to their format. At least opening pdf on linux isn't a problem. Even adobe reader works flawlessly on linux so why shouldn't flash work also ?

---

### Post by Exershio on 2008-07-30
Am I the only person who's never had a problem with flash, and not once had it crash?

32bit btw, that might be why. Don't know how bad 64bit flash is

---

### Post by CastilleV on 2008-07-30
The only thing I have against flash, is that there are various type of flash. And some sites only use ones (gaiaonline) that win users use.

---

### Post by gn2 on 2008-07-30
In 32-bit 8.04 removing the Pulse Audio packages and the libflashsupport package fixed it for me.

Now libflashplugin-nonfree works fine and *never* crashes FF3.

---

### Post by Tom--d on 2008-07-30
> **gn2 said:**
> In 32-bit 8.04 removing the Pulse Audio packages and the libflashsupport package fixed it for me.

Now libflashplugin-nonfree works fine and *never* crashes FF3.


Same,
I have also got Flash Player 10 beta 2 and its never crashed on me once.
Flash Player 9 always crashed around 2 or 3 videos of youtube. Now I can watch unlimited. :D without crashing :)

---

### Post by billgoldberg on 2008-07-30
I'm using ALSA and flash 10 beta 2 on Ubuntu Hardy and it doesn't crash anymore.

The performance still sucks.

On my less powerfull intel machine fullscreen plays pretty good. 

On my way more powerfull desktop, fullscreen lags and the cpu's are getting hit hard.

I'm using flash-block, to keep my internet experience good and fast.

---

### Post by Arthur Archnix on 2008-07-30
I feel your pain. Flash support on Linux sucks. Heck, it's not all that great on Windows either. But until an opensource alternative is available we're going to be stuck begging adobe to give us better support. And I'm not talking about gnash or swfdec, I mean an alternative for developers to do the kind of things they're doing, but with an open source tool. I don't see that even on the horizen.. flash is the new mp3. Maybe in 5 years we'll have an 'ogg' like replacement, but getting websites to switch over will be ... about as successful as having them move away from mp3.

---

### Post by Vorian Grey on 2008-07-30
> **Exershio said:**
> Am I the only person who's never had a problem with flash, and not once had it crash?


I've never had any problems with it. I loathe it, though. I think it works right just to annoy me.

---

### Post by init1 on 2008-07-30
> **Exershio said:**
> Am I the only person who's never had a problem with flash, and not once had it crash?

32bit btw, that might be why. Don't know how bad 64bit flash is
I use 32 bit, but it crashes a lot for me. It only happens when I'm leaving a page, and the restore session doesn't remember that I've closed it, so it goes like this:
```
Youtube video in a tab
Attempt to close tab
Firefox crashes
Restore the session
Youtube tab is still there
Attempt to close it again
Firefox crashes again 
Process repeats 

```
Sometimes Firefox doesn't crash, sometimes it crashes over and over again.

---

### Post by qazwsx on 2008-07-30
I have created shortcut to kill flash. :lolflag:
It is easy in Konqueror maybe impossible in Firefox.
It is not unstable for me. CPU hungriness is the reason. 
Usually I just kill flash because of adds.

I have tweaked adblock filters in Konqueror. Never truly satisfactory result.

---

### Post by original_jamingrit on 2008-07-30
I have the 32-bit adobe plugin installed on Slackware 12.1, with FF3.

I use it on Newgrounds, Youtube (and many other youtube clones), and the pizza pizza online service (which requires it for the menu sidebar, of all things).  It lags somewhat once in a while, but otherwise runs perfectly.  It has only crashed on Kongregate, which tends to have 6 or 7 useless instances of flash serving ads.

@qazwsx: try out NoScript, which prevents flash from starting untill you grant it permission.  Before it starts, it just shows as a gray box, waiting for you to click on it.  I'm not sure if this is the default behaviour, but this is how I've set it up.

---

### Post by billgoldberg on 2008-07-30
> **init1 said:**
> I use 32 bit, but it crashes a lot for me. It only happens when I'm leaving a page, and the restore session doesn't remember that I've closed it, so it goes like this:
```
Youtube video in a tab
Attempt to close tab
Firefox crashes
Restore the session
Youtube tab is still there
Attempt to close it again
Firefox crashes again 
Process repeats 

```
Sometimes Firefox doesn't crash, sometimes it crashes over and over again.

[http://flashblock.mozdev.org/](http://flashblock.mozdev.org/)

That way the flash video won't be loaded by default. You'll have to click the button before it starts to load. So it can't crash.

---

### Post by bruce89 on 2008-07-30
> **billgoldberg said:**
> [http://flashblock.mozdev.org/](http://flashblock.mozdev.org/)

That way the flash video won't be loaded by default. You'll have to click the button before it starts to load. So it can't crash.

The OP already has that.

---

### Post by init1 on 2008-07-30
> **billgoldberg said:**
> [http://flashblock.mozdev.org/](http://flashblock.mozdev.org/)

That way the flash video won't be loaded by default. You'll have to click the button before it starts to load. So it can't crash.
I used to do that, but I haven't gotten around to installing on this installation of Debian yet. It does prevent flash that I don't want to see from crashing it, but it can't prevent flash that I do want to see from crashing it. Still, it is an option. Of course, I haven't had much problems with crashing yet. It usually takes a few months in Debian before it becomes an issue.

---

### Post by tuxxy on 2008-07-30
Mine runs fine also on 64bit Hardy, lags when changing videos occasionally but apart from that and the odd non load it runs fine.

---

### Post by DeadSuperHero on 2008-07-30
I find it strange that Flash on OpenSolaris is waaay better than Flash on Linux.

Could it possibly have something to do with Solaris having only one standardized system, and Linux having many?

---

### Post by geoken on 2008-07-30
> **Arthur Archnix said:**
>  And I'm not talking about gnash or swfdec, I mean an alternative for developers to do the kind of things they're doing, but with an open source tool. I don't see that even on the horizen..

Huh?

The Flex Compiler has been open sourced. Barring that, HAXE compiles SWF's. There are various methods to build Flash using open source tools. Any text editor and one of the free, open source compilers will allow you to build Flash.

Here's me working on Flash in Ubuntu;
[IMG]http://i5.photobucket.com/albums/y169/geoken/flex.jpg[/IMG]

---

### Post by geoken on 2008-07-30
> **Mr. Psychopath said:**
> 

Could it possibly have something to do with Solaris having only one standardized system, and Linux having many?

Of course not. I mean, even though pretty much everyone who has uninstalled PulseAudio has fixed all flash issues, I'm sure PulseAudio has nothing to do with it since it's Open Source and by definition good and Flash is closed source and by definition bad. I'm sure the removal of PulseAudio and Flash working perfectly are completely unrelated.

Apparently, the only time we're allowed to blame PulseAudio for causing problems is when it's affecting another open source app (like Audacity).

---

### Post by Arthur Archnix on 2008-07-30
geoken, I would have believed you without the massive screenshot. So what's the problem with flash then if it's already open. Or are you saying there are flash developer tools that are open, but the compiler is closed... or what.

I'm trying to understand why gnash doesn't work with almost anything I try on youtube and why adobe's plugin sucks so hard.

---

### Post by geoken on 2008-07-30
> **Arthur Archnix said:**
> geoken, I would have believed you without the massive screenshot. So what's the problem with flash then if it's already open. Or are you saying there are flash developer tools that are open, but the compiler is closed... or what.

I'm trying to understand why gnash doesn't work with almost anything I try on youtube and why adobe's plugin sucks so hard.

No, they're both open. The compiler is open (under the Mozilla Public License) which allows you to use any tool you want. All you need to is write some valid actionscript in any text editor, save it with a ".as" file extension, then run the compiler and tell it what .as file to compile. In the pic I'm using the official Eclipse based IDE from Adobe, but I also use Scite w/AS3 extensions.

Gnash doesn't work because they don't fully support the SWF spec and Adobe suck's hard because of Pulse Audio.

---

### Post by DeadSuperHero on 2008-07-30
> **geoken said:**
> Of course not. I mean, even though pretty much everyone who has uninstalled PulseAudio has fixed all flash issues

I meant actual system libraries. Linux has the disadvantage of having many distributions with different library versions, different kernel versions, different DE's and sound stacks (PulseAudio, ALSA, ESD, OSS, Phonon) as well as different media frameworks (Phonon, Gstreamer, Xine).

With a proprietary app like Flash that calls from specific libraries with specific versions, it could possibly be a cause as to why Flash acts up so much in Linux.

Yet, Nvidia drivers work completely fine. So, the argument can go both ways.

---

### Post by geoken on 2008-07-30
> **Mr. Psychopath said:**
> 

Yet, Nvidia drivers work completely fine. So, the argument can go both ways.

They do? Last I checked the official release notes for KDE 4 specifically mention incompatibility with nvidia due to their lack of support for XRender.

BTW, my post was meant to be sarcastic. I was in fact blaming it on the sound stack (flash works great with ALSA, and fails with PulseAudio)

---

### Post by th3james on 2008-07-30
Like I said in my original post, pulse has to take it's share of the blame (one has to wonder if it was ready for an LTS?) but the fact remains that we still have a massive portion of the web tied up in a proprietary standard, viewing of which is currently controlled by Adobe and weather they choose to bless your OS with a decent decoder (even disregarding the sound, video playbacks speed is also unacceptable, and has been a bug for ages)
Alas I fear with Silverlight on the horison it's only going to get worse (that said, they are working with novell to get it a decent linux version, so who knows...)

---

### Post by cardinals_fan on 2008-07-30
I have no problems on Arch i686 with Vimperator/Swiftfox.

---

### Post by dspari1 on 2008-07-30
Flash works, but many sites don't display them properly. That's my beef with it.

---

### Post by Keyper7 on 2008-07-30
I was glad to see that Flash 10 beta solved the z-index issue that hid javascript menus behind flash ads. It's going slowly, step by painful step, but at least it *is* somehow improving.

I do expect a major boost in Gnash with Adobe opening up swf/flv specs, though.

Then again, currently flash is not what forces me to use a 32-bit browser... (Sun, I'm looking at you)

---

### Post by AliG on 2008-07-30
my current setup with Win XP pro used to run any/all youtube videos perfectly never had any jitter/lag.

since I upgraded to Ubuntu, almost all flash video content is unwatchable. 

my guess is my Hardware is not up to it as the processor gets used 100% when viewing flash content, but if it worked perfectly well in Win XP, if anything it should work better using lesser resources then windows when running linux. very disappointed. :confused:

---

### Post by DrumScum on 2008-07-30
> **billgoldberg said:**
> 
I'm using flash-block, to keep my internet experience good and fast.

Same here, especially to get rid of those annoying Flash ads eating away my bandwidth. I recommend this add-on to anyone.

---

### Post by waapwoop1 on 2008-07-30
Quick question guys. I have flash 10 on my 32 bit laptop.

Can i put flash 10 on my 64bit ubuntu at home. I must admit, flash 9 isn't going so well on my 64 bit pc. its ok, i can watch youtube... but will flash 10 beta work in 64, anyone tried this?

---

### Post by ScrewdriverClock on 2008-07-30
Well ever since mid 2006 I've been developing applications and animations with Flash (I know thats not long, but I started at 14). Before jumping to linux, when building webpages rather than using gifs or pngs for buttons on a nav bar, I preferred to use flash navigation bars. While they do have their benefits, when I jumped to Linux and installed Flash Player 9 I noticed that the transparency features didn't work. So fastforward in time a bit, to when Flash Player 10 Beta 2 just came out. About 2-3 days ago I reinstalled Ubuntu onto this box and started playing around with it. Unfortunately the new beta ran outrageously slow for me, and watching youtube videos drastically reduced the video quality. I then went to my site to test it and see how it fared, and it wasn't much better when it came to the nav bar.

So Long story short: 

While I LOVE Flash, and I love its functionality as a Web 2.0 Application, I don't see it being viable for use in all out web development until the new Flash Player is coming out. Reason? Many sites opt for transparent swfs which do lag significantly in Linux distributions, and it seems that Linux is unable to load multiple Flash documents at once. Needless to say I see it becoming viable in the next few months once the betas are finalized and finally released, and now all thats left for me is to figure out how to optimize my flash work to work for all platforms equally.

---

### Post by Alldan on 2008-07-31
Yes! Firefox crashes... system freeze ... Flash performs very poorly for me

---

### Post by Alldan on 2008-08-18
in my case situation improved only after pulseaudio removal

---

