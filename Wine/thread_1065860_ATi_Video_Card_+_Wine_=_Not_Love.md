---
title: "ATi Video Card + Wine = Not Love"
date: 2009-02-10
forum: Wine
---

### Post by rocky5051 on 2009-02-10
I recently bought new hardware for my dated machine to get the most performance I could out of it. Among other parts which have nothing to do with my problem, I bought an ATI Raedon HD 2600XT IceQ Turbo graphics card. It's also an AGP model.

The problem is that any time I try playing any game through Wine, it chucks a bunch of GL INVALID ENUM errors, and if the game continues (like Halo did), it'll run for maybe ten seconds and lock up the whole system, forcing me to restart the system. I think this was with Wine-1.1.3 so I'll be retesting with the most recent version if I must.

Right now this is really the only thing keeping me from switching entirely over to Kubuntu. I have since uninstalled Kubuntu to free up space on the hard drive it was occupying for Windows, but I'm not against reinstalling it if you guys need more info.

Specs:
Kubuntu 8.04 with KDE 4.0 (for some odd reason Kubuntu 8.10 won't load X when I try to install it...)

ATI Raedon HD 2600XT IceQ Turbo, AGP, 512mb GDDR3

I don't quite remember the driver version. They were the ones provided by AMD from their site. I'll probably retest using the ones availible from the Ubuntu repositories though.

Sorry for the vagueness and thanks in advance.

---

### Post by zami on 2009-02-10
I'm sorry I don't have anything cheerier to say here... any chance you can return that ATI card?

Because I think your right, ATI+WINE=no love.  And a lot of headaches trying to figure out what's wrong.

My very recent experience with Lord of the Rings Online, ATI, and Nvidia

My setup -
Ubuntu 8.10, Wine 1.1.2, 2Gig RAM, Pentium 4 3Gig processor

And after all the in-game and registry tweaks the best I could get was...



ATI Radeon HD3850 512meg card
lowest possible game settings
960x600 resolution
latest proprietary drivers
hours and hours of troubleshooting
---------------------------
10-20 fps (aka, mud)



3 year old Nvidia 215meg card
"high" game settings
1440x900 resolution
easy to install Ubuntu drivers
zero time troubleshooting
---------------------------
50-60 fps (aka, silk)


Conveniently enough, I just traded cards with my husband, so we both felt we got an upgrade, as he's a Windows man and that ATI card runs faaaantastically in Windows.

It could just be your card is so new it's not properly supported in Linux yet.  I did notice improvements every few Catalyst releases, but that meant watching Wine games go from unplayable to barely playable - never "good".

I think you are better off dual-booting rather than giving yourself a headache wondering what's wrong with your Wine setup (because it's probably not you or Wine, it's ATI!), or returning that card if you can.

Maybe someone else will have some better input for ya.

-zami

---

### Post by rocky5051 on 2009-02-11
I wish I could say "yes," but Newegg only allows replacement for their return policy on the card, which I knew ahead of time. The reason I purchased the ATi card over nVidia was because the ATI card was about 3x more powerful than the best AGP Nvidia card I could find, and about the same price.

Can't say I haven't had my share of problems getting it to work on Windows (had to update the gart drivers, get special hotfix drivers, new power supply, etc. etc...), but I guess what I'm trying to say is I don't mind going through all the trouble since that's usually my luck anyway. :lolflag:

Anyway, I've gotten Kubuntu set up again, and I followed [this]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Install_Method") tutorial to get it working. Initially I tried the fglrx drivers that you could get from the repositories but they failed to even load the login screen. After that I tried the manual install method on that tutorial with Catalyst 9.1, but that yielded the same results...

I did however notice two things.

1) The driver was saying it didn't recognize my graphics card
2) Aside from that, it said it didn't recognize "8 bits", whatever that is...that's all the error said.
EDIT: I mean't to say it says 8 bits isn't supported. What could that mean? Pixel pipelines? I know the card only has 8 of something and I forget what. Before when the driver was detecting my card, Wine was reporting a similar error, but rather, that it was supposed to have 16 instead of 8.

EDIT 2: I have a good feeling this probably doesn't belong in the Wine section now since it seems the drivers are the culprits, more or less.

Any ideas?

---

