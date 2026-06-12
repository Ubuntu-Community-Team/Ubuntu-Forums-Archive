---
title: "Has it always done that?"
date: 2009-01-14
forum: The Cafe
---

### Post by razerbug on 2009-01-14
I dual boot Vista and Ubuntu Studio on my laptop (seperate HD's) and in Vista  recently I updated my Synaptic touchpad drivers. Everything went swimmingly and I got some new functions out of it, such as the double-tap-and-hold function to mimic the click and drag/highlight of the left mouse... useful as my left click physical button is pretty cream-crackered. 

so having got used to moveing icons and highlighting text with just the trackpad in windows I found myself instictivly doing it under linux... at first I didn't notice it was working but it clearly is behaving exactly the same under linux as the updated windows version...

presumably the updated driver in Vista didn't update Ubuntu, so: has Ubuntu always had this double-tap-and-drag feature?

---

### Post by Mr. Picklesworth on 2009-01-14
Indeed. There's also (probably) two finger scrolling, two finger / three finger clicks, and circular scrolling. If you have SHMConfig enabled for the touchpad driver in xorg.conf, play with synclient in the terminal. synclient -l will get you started.
There's a program called gsynaptics for configuring many common options for the touchpad. (At least, the ones that always work regardless of which touchpad you have).

If you play with two finger tap (which is an awesome thing), keep in mind that 3 is for right click. I believe Ubuntu has a three finger tap set to right click by default, which is a bit odd. To right click with a two finger tap, use synclient TapButton2=3. You may also want to adjust EmulateTwoFingerMinZ depending on your touchpad and your fingers. For example, the default is 280 but I have it set to 100 resulting in very smooth interaction for me.

---

### Post by razerbug on 2009-01-15
That is all amazing advice - and I'll endevour to try all of it. 

I'll also give Linux a great big +1 in my blog comparing the big 3 OS's 

but at the same time you've highlighted why Ubuntu still won't ever top Win/OSx

what sort of options are those?! in windows I run one exe - I get a nice GUI with well explain features and test functions (to do all of the above btw) 

[s]in Linux I have to be launching cmd line's with flags.

It's probably not an issue for me, but for you daily computer user... it's serious hassel...[/s]

Wait im being an idiot - a simple synaptic download and there we have a controle panel for the touch pad. I'd give it another +1 but that should probably come installed by default... 

but thanks for the reply dude! I'll definitly be having a play with that!

---

### Post by razerbug on 2009-01-15
hmm loaded the gsynaptic program - dosn't give me any multitouch scrolling options... the comandline way brings up the usualy values that mean nothing to a human being... Is there a way to enable the extra touch options in a way a someone who dosn't think in C+ can understand :P

---

