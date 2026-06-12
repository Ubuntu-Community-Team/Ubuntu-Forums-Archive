---
title: "Display and Compiz"
date: 2010-01-13
forum: System76 Support
---

### Post by Paul Dietrich on 2010-01-13
Order #9511

I just got my panp6 and love it.  Quick question:

When I go to System > Preferences > Display, I get a message that reads:

"It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?"

Naturally, I click "Yes"

Then I see a window entitled "NVIDIA X Server Settings", which I am unfamiliar with.  Is this normal, or is there anything I should do?

The reason I ask, is I was looking for Compiz and wound up looking at System > Preferences > Display.  I see that Compiz appears in my list Ubuntu Software Center as installed.  I thought I would find it under System > Preferences > ccsm, but do not see it.  Compiz, however, is clearly enabled, because I get wobbly windows when I move them, etc., which is great, but wanted to fine-tune my Compiz settings.  Where is it?  Thanks, and my next computer will definitely be a System76.  Cheers.

---

### Post by howefield on 2010-01-13
As compiz appears to be installed and functioning, and you want to play about with extra features, try installing compizconfig-settings-manager in Synaptic.

You'll then find it in the System > Preferences menu.

Or you can use simple-ccsm which has fewer features/settings.

---

### Post by Paul Dietrich on 2010-01-13
Many thanks.

---

### Post by thomasaaron on 2010-01-14
> Then I see a window entitled "NVIDIA X Server Settings", which I am unfamiliar with. Is this normal, or is there anything I should do?

Yes, that is normal. NVIDIA X Server Settings is the preferred way of configuring the display on an nVidia machine. System > Preferences > Display doesn't have the capability.

Compiz comes with any Ubuntu installation nowadays. It's not something you 'go to,' per se. It's a graphics engine that runs beneath the surface.

You can disable it by going to System > Prefs > Appearance > Visual Effects > None. This comes in handy every once in a while, as there are still occasional conflicts between compiz and some software.

Howefield's answer is right on the money for providing a tool that allows you to customize compiz's settings.

---

