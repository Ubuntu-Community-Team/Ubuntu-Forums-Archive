---
title: "Improve touchpad support..."
date: 2007-10-21
forum: Ubuntu Brainstorm
---

### Post by smartboyathome on 2007-10-21
Gutsy made a step in the right direction by including a couple of options for touchpad in the mouse configurations, but I think hardy should go the whole way and give the user the option to choose what they want their touchpad to do (ie, i have seen users asking how to use two fingers to scroll and a two finger tap to right click, just like an Apple). This can be done by editing the Xorg.conf, but who seriously wants to do that? Anyway, if the options could be added, many users would be happy. :)

---

### Post by Onesimus on 2007-10-21
Useful improvements in the touchpad support would be to: 
[INDENT]a) disable the touchpad if the laptop detects that a USB mouse has been connected.
b) disable the touchpad for a no. of seconds after key presses are detected.  This would
                prevent the cursor being inadvertently moved if a document is being typed.[/INDENT]

Both of these features could probably be used if the user modifies an obscure file in the system, but who would want to do that if the feature was included in the basic system setup.

---

### Post by teasum on 2007-10-23
I second this wholeheartedly.

I have tried gsyanptics, configuring xorg.conf, etc., in previous releases, but nothing has gotten the touchpad to work as well as it does in XP.  Gsynaptics never worked for me (it loaded correctly, and it would let me idsable or enable the touchpad and/or tapping, but any other settings did not affect the operation of the touchpad).  So, I have tapping turned off and I use the buttons, because I can't get tapping to work properly (it's either WAY too sensitive, or the opposite).

I nominate touchpad bugfixing as a high-priority for Hardy Heron.

---

### Post by clubsoda on 2007-10-23
Thirded!

I envision a couple of major steps.  Firstly, the settings for **evtouch** could be made dynamically adjustable.  I have heard that the whole of xorg.conf may be handled dynamically in the future, so evtouch itself may not need any work.  Some kind of GUI to aid in configuring evtouch could be what we're after.

Secondly, allowing closer integration between a touchpad and particular applications.  I'm thinking especially of front-ends to SCIM which do character recognition, like **kanjipad**.

The icing on the cake would be mode selection.  Typical modes would be:
* desktop mode as a substitute mouse, with gestures for button actions
* drawing mode within Gimp, photo editors etc.
* character recognition mode, replacing the keyboard.

---

### Post by martinw89 on 2007-10-23
I also definitely agree, it's a core and relatively simple part of using a laptop.

For me, qsynaptics (thats not G but Q synaptics) works very very well.  It offers every option imaginable.  The only negatives are having to use "qsynaptics -r" to restore settings and having to modify xorg.conf to use the program.

---

### Post by smartboyathome on 2007-10-23
> **martinw89 said:**
> I also definitely agree, it's a core and relatively simple part of using a laptop.

For me, qsynaptics (thats not G but Q synaptics) works very very well.  It offers every option imaginable.  The only negatives are having to use "qsynaptics -r" to restore settings and having to modify xorg.conf to use the program.

If we were to use a program, we would probably want it to edit as little of xorg.conf as possible.

---

### Post by Paul.Spectre on 2007-12-12
I would vote for all of the above, but in my case (and for many others with similar misery across the forums) improved detection of touchpads. If your pad is not detected, forget fancy settings in xorg.conf...

---

### Post by derrick81787 on 2008-01-16
I know this is really simple, but I think it would be a huge help if SHMConfig was set to True in xorg.conf by default. This is needed for gsynaptics (and I think all touchpad configuration programs) to be able to function, and as far as I can tell, there are no negative consequences.  It's not that adding that one line is hard for a user to do, it's just that they shouldn't have to.  Does anyone else agree with me on this?

I also think that in Gutsy, the touchpad preferences in Mouse Settings is only shown if SHMConfig is set to True in your xorg.conf.  Otherwise, I don't believe it's there.  However, I'm running Xubuntu right now, so I can't verify that right this second.

---

