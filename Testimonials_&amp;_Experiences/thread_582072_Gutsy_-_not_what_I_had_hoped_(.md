---
title: "Gutsy - not what I had hoped :("
date: 2007-10-19
forum: Testimonials &amp; Experiences
---

### Post by ElEdwards on 2007-10-19
I spent about 10 years in front of my computer today ;) trying to get Gutsy to work.  I installed three different times, doing a complete fresh installation each time.... and EACH TIME, my video card came up as something else.

My card is an nVidia GeForce FX 5200 PCI, which I bought about a month ago for use with 7.04... and I loved it with 7.04....  I had no problems configuring a dual display and effects, too.

My card came up today as "Generic", "ATI Radeon", and finally, "nVidia" ...  WHAT A TEST!!

"Generic" I can see..... but "ATI Radeon"????  Aw, come on!

I finally have things running and have my dual display.... but MAN is it sluggish.  I even disabled effects in Appearance....but it is still sluggish.  For example, in this forum right now, whether I use the scroll bar at the side or the wheel on my mouse, the page scrolls about 2 seconds *after* I do the action.  The same thing happens in other apps, too; not just Firefox.

Terrible!... AND unacceptable!

Prior to this, I've tried almost every available distro based on Ubuntu 7.04 and had great success with each one...... so, like so many other others, I've been waiting with great expectation for 7.10....

and now I think I ready to go back to Mint 3.1.

**I'm so discouraged right now!**

I've been quite the evangelist at work about Ubuntu 7.04.... but I'm not saying a word about 7.10 unless/until it gets fixed! At least fixed so that there are no hoops to jump through to even get a display working.

7.04 just worked ..... 7.10 just doesn't!

<sigh> :confused:

---

### Post by rsambuca on 2007-10-19
Did you consider that either your iso or disc may contain errors?

---

### Post by ElEdwards on 2007-10-19
I guess it's worth a shot to try again :(

---

### Post by rsambuca on 2007-10-19
Check the md5sum first, burn it at a very slow rate to avoid single bit errors, and then run the cd integrity check.  Then maybe you can start complaining ;)

---

### Post by FrancoNero on 2007-10-19
i've been running gutsy as upgrade from feisty since herd 2 or so, it went downhill from there. it just... with every update it got worse. at some point, it just got slower and slower, and while suddenly, suspend seemed to work, at some point either xorg or gdm or the intel graphics driver, something crashed.

so, installed gutsy final today, fresh install. what excitement, I figured a fresh install will help.

1st boot: totally crashes, gdm doesn't really start or something, had to pull the plug on the laptop. wtf.... this is a FINAL?
2nd boot: boots up fine, some flickering, indicates graphics problems, but i get the login screen. font is way too large, but i get into Ubuntu and... .whew.. I'm there. Okay... Suspend? nope... screen stays black when I try to come back.

bottom line: I thought Microsoft was the only company to ship an operating system that just doesn't really work. Feisty was so close. so close! well woohoo, i got semitransparent windows now and a 3d cube, but I can't even USE IT!

Now I'm not a complete n00b, and I've fixed errors in the past, I've gotten to know my way around a terminal, and i've edited config files and all kinds of other stuff that an end user shouldn't ever have to be doing, but at some point, excuse me, I just need to have a working operating system. i can't have Ubuntu just to have Ubuntu and hack around with it. I'm not a beta tester, and this isn't a beta anymore... or wait. I think I got it. It should be a Beta.....

Well guys, I'm back with Redmond until this Ubuntu thing starts working. I've said it before, I'll probably say it again. Every 6 months, thousands of users around the planet just like me, will install ubuntu, see that upon close examination it just doesn't work, and will dump it again, to try again in 6 months.... an endless cycle? I don't think so. The Ubuntu community has done extraordinary stuff....


but with Gutsy, I think the gutsy as it is right now shouldn't be a public release.... I am VERY disappointed.

and now jump and kill me ;-)

---

### Post by buntunub on 2007-10-19
Run the media check at boot. You could be bitten by the new unbreakable X garbage that they put in with Gutsy too. Borked my system up like you cant imagine. Dual screens are a total nogo if you use that stupid Screens and Graphics utility they threw in without bothering to read the bug reports on it during beta, or bothering to fix them because the Devs think that dual screens are not a big deal for people. Gonna be interesting to see how people who want to use Gutsy for business are going to feel about that.

---

### Post by ElEdwards on 2007-10-19
OK, Rsambuca :)

I downloaded the iso again, checked the md5sum, ran the integrity check after booting to the cd.... all appeared fine.

Rebooted as instructed, booted up, ran "install" from the desktop, set up my partitions.... and here I am at two identical 800x600 LCD displays.  Crap!!  So (as you put it) I am back complaining.

I'm not done yet.... going after Envy now.

I'll be back. :(

---

### Post by rsambuca on 2007-10-19
Whoa, have you tried the restricted drivers manager first?  And other than the resolution, is it working better than the previous installs?  ie. sluggishness?

---

### Post by ElEdwards on 2007-10-19
I took a different direction that I did before.  I didn't go the Envy route, NOR did I go to the Restricted Drivers panel.... both of those caused me gastro-intestinal distress before. ;)

This time, I did this:
1- used Synaptic to download and install **nvidia-glx-new** from the repos
2- there's a little note in Synaptic when you select this driver for installation that reads:
**Enable this driver with "sudo nvidia-glx-config enable"**
so I opened Terminal and did that and rebooted
3- after the reboot, I received a message that "Restricted Drivers" were in use, so evidently the install from the repos takes care of this.
4- I opened Terminal and typed **sudo nvidia-settings**, which opened the nVidia Control Panel and from there, I was able to successfully configure my dual display.

It also appears that the sluggishness is gone, as well, which can probably be attributed to a bad iso or burn in my previous attempts.  So RSAMBUCA, I attribute that to your advice... and please forgive me for trying to get you caught in my garbage disposal.

I'll go sit quietly in the corner now while I make sure everything else is working correctly..

From this experience, my advice is to go directly to the Ubuntu repos for the nVidia driver and handle it there, then use the nVidia Control panel and not the "Screens and Graphics" one.

---

### Post by rsambuca on 2007-10-19
Good stuff!  Glad you have her up and running.

---

### Post by athaki on 2007-10-19
Gusty hasn't been all that nice to me either. I've had to do OEM installs because the CD wants to hang. Yes, I've checked the CD and it is supposedly good. So now, since I have an ATI Mobility Radeon X300 video card, I'm not sure if I want to get the restricted driver and lose the eye candy (which I know I can get back if I enable XGL, but I really just don't want to fool with it) or just use the SGI driver which works 'good enough' for me.

---

### Post by FrancoNero on 2007-10-20
feisty was so hassle-free. installed and it at least worked (aside from the missing suspend and hibernate, and a ton of other things that were MISSING, but it worked!)

---

