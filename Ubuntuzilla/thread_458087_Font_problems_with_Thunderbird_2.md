---
title: "Font problems with Thunderbird 2"
date: 2007-05-29
forum: Ubuntuzilla
---

### Post by max.spicer on 2007-05-29
Hi,

I've just installed Thunderbird 2 using the installnewthunderbird_3.2.0.sh script.  The install went fine, but I'm having problems with fonts in Thunderbird.  The default font that messages are displayed in is far too small, and looks very blocky.  I can increase the font size, but it's still very blocky. If I switch back to 1.5, everything is fine.  Is this because the official Thunderbird Linux release doesn't use freetype fonts?  Is there any way I can make it do so?

Thanks,

Max

---

### Post by nanotube on 2007-05-29
hi,
not sure exactly what's going on, but please see if any of the info on this page: [http://kb.mozillazine.org/Font_settings_in_Thunderbird](http://kb.mozillazine.org/Font_settings_in_Thunderbird)
helps any. 
specifically, maybe if you change your font settings under 'Edit -> Preferences -> Display -> Formatting -> Fonts...' ?

you could maybe even compare the settings you have under tb1.5 and see if they are any different under tb 2...

please try fiddling around with the settings, and see if you come up with something. :)

---

### Post by max.spicer on 2007-05-31
Unfortunately, no manner of fiddling has fixed this.  I've also had a look at a friends Thunderbird 2, which he's running on Debian, using OpenBox.  His Thunderbird 2.0 has exactly the same font problems (although he hadn't noticed).  A few years ago, when I first ran Mozilla on Linux, it always had these font problems - fonts would appear jagged and ugly.  This was solved when they first started releasing builds that were tagged as XFT (or maybe GTK2 - my memory is hazy!).  Is it possible that this feature is somehow missing in the official builds of Thunderbird 2.0, or that the Ubuntu package of 1.5 contains some hacks to get it working?

I've attached some screenshots to show the problem.  The first two show how things should be.  If you compare 'Thunderbird 1.5.png' to 'Thunderbird 2.png' you can see that the font is suddenly much smaller and the anti-aliasing has disappeared.  Comparing 'Compose 1.5.png' and 'Compose 2.png' you can see the same again, but also note the ugly down arrow to the right of the To: box.

These screenshots were taken using the Ubuntu packaged version of Thunderbird 1.5 and the official Mozilla version of Thunderbird 2, as downloaded by installnewthunderbird_3.2.0.sh.  The same profile was used for both and no preference changes were made between the two screenshots.  I also tried a completely fresh profile in Thunderbird 2 and got exactly the same behaviour.  All these problems can also be seen on my friend's Debian install.

Hope that helps,

Max

---

### Post by nanotube on 2007-05-31
> **max.spicer said:**
> Unfortunately, no manner of fiddling has fixed this.  I've also had a look at a friends Thunderbird 2, which he's running on Debian, using OpenBox.  His Thunderbird 2.0 has exactly the same font problems (although he hadn't noticed).  A few years ago, when I first ran Mozilla on Linux, it always had these font problems - fonts would appear jagged and ugly.  This was solved when they first started releasing builds that were tagged as XFT (or maybe GTK2 - my memory is hazy!).  Is it possible that this feature is somehow missing in the official builds of Thunderbird 2.0, or that the Ubuntu package of 1.5 contains some hacks to get it working?

I've attached some screenshots to show the problem.  The first two show how things should be.  If you compare 'Thunderbird 1.5.png' to 'Thunderbird 2.png' you can see that the font is suddenly much smaller and the anti-aliasing has disappeared.  Comparing 'Compose 1.5.png' and 'Compose 2.png' you can see the same again, but also note the ugly down arrow to the right of the To: box.

These screenshots were taken using the Ubuntu packaged version of Thunderbird 1.5 and the official Mozilla version of Thunderbird 2, as downloaded by installnewthunderbird_3.2.0.sh.  The same profile was used for both and no preference changes were made between the two screenshots.  I also tried a completely fresh profile in Thunderbird 2 and got exactly the same behaviour.  All these problems can also be seen on my friend's Debian install.

Hope that helps,

Max

hmm, well, i am not sure what exactly is the underlying issue. i have found a couple of threads on launchpad that may be helpful, check them out and see if they are what you are looking for:
[https://answers.launchpad.net/ubuntu/+source/mozilla-firefox/+question/1290](https://answers.launchpad.net/ubuntu/+source/mozilla-firefox/+question/1290)
[https://answers.launchpad.net/ubuntu/+question/5905](https://answers.launchpad.net/ubuntu/+question/5905)

if not, we will try something else (like maybe asking our own question on launchpad :) ).

---

### Post by max.spicer on 2007-06-01
> **nanotube said:**
> hmm, well, i am not sure what exactly is the underlying issue. i have found a couple of threads on launchpad that may be helpful, check them out and see if they are what you are looking for:
[https://answers.launchpad.net/ubuntu/+source/mozilla-firefox/+question/1290](https://answers.launchpad.net/ubuntu/+source/mozilla-firefox/+question/1290)
[https://answers.launchpad.net/ubuntu/+question/5905](https://answers.launchpad.net/ubuntu/+question/5905)

if not, we will try something else (like maybe asking our own question on launchpad :) ).

I don't think those two threads are dealing with the same issues, but thanks for digging them out.  Does your install of thunderbird look the same as my screenshots - in particular, do you get the dodgy down arrow to the right of the To box in the compose window?  Having done a bit more reading, it certainly used to be the case that the official Linux builds of Thunderbird were not built with XFT enabled.  This was done because not all platforms would have XFT support.  It's quite possible that this is still the case, but that when Ubuntu create their packages of 1.5 they do enable XFT.  This would explain my problems, but it would also mean that everyone should see the behaviour that I've described.

I've asked in the MozillaZine forums about this, but they're pretty busy these days so I'll have to wait and see if anyone replies to my post.

Thanks,

Max

---

### Post by nanotube on 2007-06-01
> **max.spicer said:**
> I don't think those two threads are dealing with the same issues, but thanks for digging them out.  Does your install of thunderbird look the same as my screenshots - in particular, do you get the dodgy down arrow to the right of the To box in the compose window?  Having done a bit more reading, it certainly used to be the case that the official Linux builds of Thunderbird were not built with XFT enabled.  This was done because not all platforms would have XFT support.  It's quite possible that this is still the case, but that when Ubuntu create their packages of 1.5 they do enable XFT.  This would explain my problems, but it would also mean that everyone should see the behaviour that I've described.

I've asked in the MozillaZine forums about this, but they're pretty busy these days so I'll have to wait and see if anyone replies to my post.

Thanks,

Max

hmm, well, i am attaching a screenshot of my tb2 compose window. it does have the same down arrow in the to box, but i didn't think it was "dodgy" :)
the fonts seem to look just fine, though...

you might have better luck asking on launchpad than mozillazine, though, since those guys would actually know if ubuntu does something special with the ubuntu thunderbird package with regard to the fonts.

edit: by the way, which version of ubuntu are you running? i'm on feisty (as are most people these days). if you are running dapper or breezy or something, maybe those versions have something different in the font config.?

---

### Post by max.spicer on 2007-06-01
> **nanotube said:**
> hmm, well, i am attaching a screenshot of my tb2 compose window. it does have the same down arrow in the to box, but i didn't think it was "dodgy" :)
the fonts seem to look just fine, though...

you might have better luck asking on launchpad than mozillazine, though, since those guys would actually know if ubuntu does something special with the ubuntu thunderbird package with regard to the fonts.

edit: by the way, which version of ubuntu are you running? i'm on feisty (as are most people these days). if you are running dapper or breezy or something, maybe those versions have something different in the font config.?

I think your down arrow is "dodgy".  Compare it to what you get with the Ubuntu Thunderbird 1.5.  Try switching to fixed-width fonts (Edit->Preferences->Display) and press ctrl-0 to get to the default size.  I suspect you'll find you've got jagged, fonts with no-antialiasing.

I'm running Feisty, by the way.

I think this is quite possibly turning into a non-issue, although it is annoying.  I think it's just how the official Thunderbird Linux builds work.  It's a shame that they don't appear to provide xft builds as well though.

Thanks,

Max

---

### Post by nanotube on 2007-06-01
> **max.spicer said:**
> I think your down arrow is "dodgy".  Compare it to what you get with the Ubuntu Thunderbird 1.5.  Try switching to fixed-width fonts (Edit->Preferences->Display) and press ctrl-0 to get to the default size.  I suspect you'll find you've got jagged, fonts with no-antialiasing.

I'm running Feisty, by the way.

I think this is quite possibly turning into a non-issue, although it is annoying.  I think it's just how the official Thunderbird Linux builds work.  It's a shame that they don't appear to provide xft builds as well though.

Thanks,

Max

Hm, well, i looked at my preferences, and it is already set to fixed width font, and is set at 0 magnification (ctl-0 didn't change anything). so what i've got is what i've got in the screenshot, and i think it doesn't look too bad. :)
the down arrow /is/ more jagged than the tb1.5 arrow, though, as you say.

you could try compiling tb from source with xft, and see if that helps? i remember seeing instructions for building tb/ff from source on the ubuntu wiki.

---

