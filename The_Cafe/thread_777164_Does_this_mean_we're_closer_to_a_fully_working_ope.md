---
title: "Does this mean we're closer to a fully working open source flash player ?"
date: 2008-05-01
forum: The Cafe
---

### Post by oedipuss on 2008-05-01
[http://www.adobe.com/openscreenproject/](http://www.adobe.com/openscreenproject/)

---

### Post by seatex on 2008-05-01
I sure hope so.  

64-bit!

---

### Post by Sef on 2008-05-01
It does not seem truly open.  Adobe still controls the final output.

If you want a truly opensource flash player, check out [GNash]("http://www.gnu.org/software/gnash/").  It is made for 64-bit.  It is in beta now.  Fully supports adobe flash 7, and some support for flashes 8.5 and 9.

---

### Post by SunnyRabbiera on 2008-05-01
Yeh but at least the protocols themselves are mostly open :D

---

### Post by geoken on 2008-05-01
What it means is that Gnash and SWFdec will be able to accelerate their development because the SWF spec will now be open. Currently, creating an SWF 'player' requires a compiled SWF to be reverse engineered.

---

### Post by SunnyRabbiera on 2008-05-01
Right and with this gnash and other free alternatives will have access to more current flash technologies...
soon in linux gnash or swfdec could take over for adobe full time if one wishes to.
either way this is good news, even if flash itself remains proprietary its implementation has gone practically open source making it on par with MP3(mp3 is almost open source too thanks to the owners of the format not minding open implementation)
so in short no matter how you say it, this is very good news indeed.

---

### Post by geoken on 2008-05-01
I think this will go beyond mp3 and be more like PDF. From the sound of this announcement reading the spec and creating a player won't require any licences to be paid.

---

### Post by SunnyRabbiera on 2008-05-01
aye, though MP3 is getting more open these days...
looks like almost everyone is looking at open source now, even if a lot of stuff remains proprietary at least the support will be there

---

### Post by eragon100 on 2008-05-01
Does it matter? Right now, the normal flash player works correctly with youtube.

Gnash doesn't, so I don't use it. If they have problems with adobe I feel sorry for them,but I simply use what is best fit for the task. If that's a open-source program, so be it. If that's a closed-source program, so be it. As long as my computer works. It are my rights that are being restrained by proprietary licences, and I don't care about being able to modify the source code of a program :guitar:

---

### Post by SunnyRabbiera on 2008-05-01
Yeh but this can make gnash much better and make it work for more people including you...
that way the choice factor becomes more appealing :D

---

### Post by FuturePilot on 2008-05-01
> **eragon100 said:**
> Does it matter? Right now, the normal flash player works correctly with youtube.



Right now the normal Flash player is constantly crashing my browser and eating my CPU and it has terrible playback performance. I'm sure a lot of others will agree with that too. Yet these problems only exist on the Linux Flash player. I've never had any of those problems with the Windows version. And Adobe will not fix them. Having openness or more openness, we may be able to fix these problems since Adobe won't.

---

### Post by SunnyRabbiera on 2008-05-01
aye, though I never had too many catastrophic issues with flash myself...
still this translates to better stability, gnash and swfdec are native to linux and this can benefit them greatly.

---

### Post by eragon100 on 2008-05-01
I dont' have any problems at all with flash, except that it doesn't support opera, which I like better than firefox.

So, if gnash supports opera, even though that's offcourse a proprietary browser, and works just as well or better as/then flash, I will use it :popcorn:

---

### Post by howlingmadhowie on 2008-05-01
gnash has other advantages. with gnash i'm able to view a lot of flash content on my ultrasparc running ubuntu and on my imac also running ubuntu. 

one of the large advantages of free software is that it frees the hands of hardware manufacturers to produce better products. there are some absolutely fascinating chip architectures out there which don't stand a chance because microsoft won't compile windows for them.

---

### Post by SunnyRabbiera on 2008-05-01
aye and with this gnash can be just as good as regular flash

---

### Post by geoken on 2008-05-01
The point is that the open implementations can now begin to compete with the flash player. Gnash and SWFdec are so far behind because they can not use the SWF spec to create their player. They must rely on decompiling an SWF file (which is a binary file) and reverse engineering.

---

### Post by eragon100 on 2008-05-01
Isn't reversre engineering illegal according to the flash EULA :confused:

Can't Adobe sue them for that :confused:

---

### Post by SunnyRabbiera on 2008-05-01
> **geoken said:**
> The point is that the open implementations can now begin to compete with the flash player. Gnash and SWFdec are so far behind because they can not use the SWF spec to create their player. They must rely on decompiling an SWF file (which is a binary file) and reverse engineering.


right, and now that wont be an issue :D

> **eragon100 said:**
> Isn't reversre engineering illegal according to the flash EULA :confused:

Can't Adobe sue them for that :confused:

well now the EULA is kind of a moot point, now they can legally fork flash :D

---

### Post by forrestcupp on 2008-05-01
> **eragon100 said:**
> Does it matter? Right now, the normal flash player works correctly with youtube.
Aside from the fact that the proprietary Linux version of Flash has a lot of bugs that aren't being fixed because the community can't be involved, there's also the fact that Adobe doesn't give a rat's behind about compiling a 64-bit version.  If an open source project has the capability of catching up because of open technology, it would be easy to compile a 64-bit version because we'd have the code.

I don't use Gnash because it's stuck back in version 7, but if Gnash catches up to Flash, I'd use it in a heart beat.

---

### Post by SunnyRabbiera on 2008-05-01
Yeh but as I said this points to now gnash can get what it needs to catch up so those with issues with adobe can be fully happy now

---

### Post by geoken on 2008-05-01
> **eragon100 said:**
> Isn't reversre engineering illegal according to the flash EULA :confused:

Can't Adobe sue them for that :confused:

No. The EULA only applies for reading the SWF file spec. If you go to Adobe's website and try to read the SWF spec you'll first need to agree to a EULA which says you won't use the spec to create an app that can read SWF files. 

This is why gnash had to resort to simply decompiling an SWF. If gnash didn't care about violating EULA's they could easily go to Adobe's website and get the spec, then violate the EULA by basing their app around the info contained in that spec.

---

### Post by eragon100 on 2008-05-01
Does gnash work with opera? Because personally, that's the only thing I care about :lolflag:

---

### Post by SunnyRabbiera on 2008-05-01
> **geoken said:**
> No. The EULA only applies for reading the SWF file spec. If you go to Adobe's website and try to read the SWF spec you'll first need to agree to a EULA which says you won't use the spec to create an app that can read SWF files. 

This is why gnash had to resort to simply decompiling an SWF. If gnash didn't care about violating EULA's they could easily go to Adobe's website and get the spec, then violate the EULA by basing their app around the info contained in that spec.

yeh but with this that is no longer an issue :D

---

### Post by swoll1980 on 2008-05-01
Yes unless silverlight takes over then were back to square 1

---

### Post by Sunflower1970 on 2008-05-01
I hope this means Flash will work better under Linux. For the most part it works fine, except when I need to upload images to my photobucket account. They have started to use a Flash interface which doesn't work at all. 

Also, some newspaper websites which has an option to upload photos with a person's classified ad uses Flash. Again, it doesn't work under Linux. (no matter how many times I told the developers they have to have a fallback, they just didn't care...GAHHH!)

---

### Post by heartburnkid on 2008-05-01
> **eragon100 said:**
> Does it matter? Right now, the normal flash player works correctly with youtube.

Gnash doesn't, so I don't use it. If they have problems with adobe I feel sorry for them,but I simply use what is best fit for the task. If that's a open-source program, so be it. If that's a closed-source program, so be it. As long as my computer works. It are my rights that are being restrained by proprietary licences, and I don't care about being able to modify the source code of a program :guitar:

It does matter.  Adobe's Linux player is notoriously slow, buggy, and resource heavy (even more so than their Windows player, though that's no bed of roses either), and is i386 only.  Opening the source would enable us to optimize it and port it like crazy-go-nuts.

---

### Post by k99goran on 2008-05-01
> **heartburnkid said:**
> It does matter.  Adobe's Linux player is notoriously slow, buggy, and resource heavy (even more so than their Windows player, though that's no bed of roses either), and is i386 only.  Opening the source would enable us to optimize it and port it like crazy-go-nuts.
How many Ubuntu users actually bother to install Adobe (PDF) Reader today?
I think Adobe Flash Player will go the same way. And I personally long for the day when we can take flash support for granted. :)

---

### Post by swoll1980 on 2008-05-01
> **k99goran said:**
> How many Ubuntu users actually bother to install Adobe (PDF) Reader today?
I think Adobe Flash Player will go the same way. And I personally long for the day when we can take flash support for granted. :)

+1

---

### Post by SunnyRabbiera on 2008-05-01
> **k99goran said:**
> How many Ubuntu users actually bother to install Adobe (PDF) Reader today?
I think Adobe Flash Player will go the same way. And I personally long for the day when we can take flash support for granted. :)

well I usually install it so I can view PDF files in my browser for quick access

---

### Post by geoken on 2008-05-01
> **SunnyRabbiera said:**
> well I usually install it so I can view PDF files in my browser for quick access

I do to. I use PDF's for accurate document interchange (sending to a printer who only want's PDF, etc.) and Evince fails at this task.  I've noticed several rendering glitches in Evince. And before anyone says maybe Adobe's doing it wrong, I checked against kpdf and it's results were consistent with Adobe.

---

### Post by forrestcupp on 2008-05-01
> **eragon100 said:**
> Does gnash work with opera? Because personally, that's the only thing I care about :lolflag:

flashplugin-nonfree works with the latest beta of Opera.  You just have to go to Opera's website and download the Ubuntu deb for it.

---

### Post by drascus on 2008-05-01
i dont think they truly intend to make good on this promise.

---

### Post by geoken on 2008-05-01
> **drascus said:**
> i dont think they truly intend to make good on this promise.

LOL.

They already have. If you go to the page that houses the SWF spec you can now use it without agreeing to any licenses (like you previously had to)

---

### Post by SunnyRabbiera on 2008-05-01
> **geoken said:**
> LOL.

They already have. If you go to the page that houses the SWF spec you can now use it without agreeing to any licenses (like you previously had to)

Yup, lookie:
[http://www.adobe.com/devnet/swf/]("http://www.adobe.com/devnet/swf/")
[http://www.adobe.com/devnet/flv/]("http://www.adobe.com/devnet/flv/")

No EULA to be seen now :D

---

### Post by zmjjmz on 2008-05-01
Next up is porting their CS to Linux.
You can do it Adobe.

---

### Post by SunnyRabbiera on 2008-05-01
> **zmjjmz said:**
> Next up is porting their CS to Linux.
You can do it Adobe.

well even if its closed source having photoshop and stuff more supported on linux is a great thing indeed.
I dont care if Photoshop stays proprietary, if its supported and at a semi decent price I would buy it :D

---

### Post by zmjjmz on 2008-05-01
I also think that this will greatly help flash creation tools for Linux.
Maybe I don't care if CS is ported (I just wanted Flash MX >.>)

---

### Post by geoken on 2008-05-01
> **zmjjmz said:**
> I also think that this will greatly help flash creation tools for Linux.
Maybe I don't care if CS is ported (I just wanted Flash MX >.>)

What will help flash creation tools is the new XFL file format. Really, a flash creation tool wouldn't be hard to build but most devs are looking at it from the wrong point of view. Rather than offering a simple interface that merely translates there actions to .as behind the scenes and uses an already available compiler they have all been trying to compile their own SWF's directly. A simple port of muSprite ([http://musprite.sourceforge.net/]("http://musprite.sourceforge.net/")) with more refined drawing tools and auto compiling (to an existing compiler) would probably be relatively easy to develop and all that anyone would want.

---

