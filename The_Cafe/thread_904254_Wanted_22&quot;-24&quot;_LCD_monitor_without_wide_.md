---
title: "Wanted: 22&quot;-24&quot; LCD monitor without wide gamut"
date: 2008-08-29
forum: The Cafe
---

### Post by jazzgossen on 2008-08-29
I recently bought a Dell 2408WFP, which is a good 24" widescreen monitor with a (very) wide colour gamut. In theory, that's a good thing, but I didn't realize until I got it that in apps that aren't color management aware (pretty much everything except Gimp, EOG and Firefox 3) the colours look way oversaturated.

So now I plan to return the monitor and get a similar one that *doesn't* have wide gamut.

What options do I have? When searching, it seems that most newer panels that aren't TN (TN is not an option) are wide gamut. 

Or, does anyone know when Gnome will be colour aware?

---

### Post by barbedsaber on 2008-08-29
I think this belongs in the marketplace.

---

### Post by jazzgossen on 2008-08-29
Maybe, but it's not a request for someone to sell me a monitor. Just wondering if anybody knows of a model that would fit my needs.

---

### Post by ssam on 2008-08-29
can you not colour manage all of X

there is some stuff over at [http://jcornuz.wordpress.com/category/tutorials/](http://jcornuz.wordpress.com/category/tutorials/) that might get you started

====
just saw this in a photo forum. looks like windows XP users suffer similarly with wide gamut monitors
[http://forums.dpreview.com/forums/readflat.asp?forum=1004&thread=25060360](http://forums.dpreview.com/forums/readflat.asp?forum=1004&thread=25060360)

---

### Post by jazzgossen on 2008-08-29
> **ssam said:**
> can you not colour manage all of X
No, I don't think so. There is [xicc]("http://burtonini.com/blog/computers/xicc"), but that only works with programs that are color management aware. One imporant program that doesn't use xicc is Nautilus, which means that all orange folder icons and other icons, as well as my desktop wallpaper, has very oversaturated colours.

So for the time being, I think that having a wide gamut monitor has more drawbacks than advantages for me.

---

### Post by ssam on 2008-08-29
have you looked at xcalib.

---

### Post by jazzgossen on 2008-08-29
Thanks. That looks promising. But the ICM profile I've been able to find for my monitor doesn't make a difference when used with xcalib. So I guess it doens't include a vcgt tag (whatever that is)? 

I'll search for a usable profile. If I could make it work without switching the monitor that would be great!

---

### Post by jespdj on 2008-08-29
I am using a ColorVision (now DataColor) [Spyder](http://spyder.datacolor.com/) with software on Windows to create an ICC profile for my Dell 2405 FPW monitor and load it with xcalib on Ubuntu - that works.

Doesn't your monitor have controls to make the colors less saturated?

---

### Post by jazzgossen on 2008-08-30
I don't have a hardware calibration tool. Would you mind posting or PM'ing me your profile?

I have played around a lot with the monitor controls but haven't found a way to get rid of the oversaturated reds and greens. I can make them better, but not quite right. There is a colour preset called "sRGB" which doesn't have hte oversaturated colours, but I think that looks too bland instead, and too warm.

---

### Post by jespdj on 2008-08-30
I could send you my monitor profile, but you don't even have the same model, so I don't think it would make much sense for you to use the profile of my monitor. Each individual monitor has its own characteristics (depending on exactly what type of LCD panel it contains, slight manufacturing differences, its age, etc...) so using the profile made for one monitor on another, especially if it's not the same model, isn't very useful. Also, the monitor controls have to be set to very specific settings that the calibration program helps you to set - it's going to be very hard to set your monitor exactly the same as mine.

---

### Post by mips on 2008-08-30
**[HOWTO] LCD Monitor Calibration! Photo, gfx & web designers.**
[http://ubuntuforums.org/showthread.php?t=880636](http://ubuntuforums.org/showthread.php?t=880636)

Sometimes monitors have special effects like colour boosters and crap enabled which can be turned off.

---

### Post by jazzgossen on 2008-09-01
Thanks for all your help. But it seems that in order to get usable colours from this monitor I'd need to buy a Spyder3 colorimeter [which I don't think works in Linux]("http://lists.freedesktop.org/archives/openicc/2007q4/001026.html") (and also is quite pricey). The cheaper Spyder2 apparently won't work with a wide gamut monitor like the Dell 2408 (according to the manufacturer's product finder).

So my original question remains: Does anybody know of a large LCD display with "normal" gamut?

---

### Post by heimo on 2008-11-26
> **jazzgossen said:**
> So my original question remains: Does anybody know of a large LCD display with "normal" gamut?

I understand this question was asked almost three months ago, but still it may be relevant to some people.

As far as I know, Eizo S2431W is a 24 inch display without wide gamut (covers about 94% of SRGB-range) and then there's Samsung 305T, which used to be "normal gamut", but is now shipped with wide gamut panel (all the 350T+ models are wide gamut, but some of the older 350T models are normal). I believe HP LP3065 is also wide gamut.

But yes, at least in 24 inch range there's a normal gamut display available. Not too cheap one, but should be quite good for at least (serious) amateur graphics work.

---

