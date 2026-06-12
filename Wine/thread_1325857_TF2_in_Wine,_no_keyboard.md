---
title: "TF2 in Wine, no keyboard?"
date: 2009-11-13
forum: Wine
---

### Post by Sticky_Bit on 2009-11-13
So I have steam installed, I have HL2 and CSS working great. I installed Team Fortress 2 and ran into some performance issues, graphics wise, but it runs smooth now after some research and some tweaks. Now when I get into a game my keyboard does not work. I can look around and shoot with the mouse but cant move anywhere or even use esc to get out of the game or disconnect from a server. It's the weirdest thing, trying to get this game working has been such a pain, first with graphics and performance and now this. I'm really frustrated right now. :mad:

Anyone seen this before? Any suggestions? I am using Wine 1.1.32, running the game at mostly medium settings, with dx 8.1. Thanks! Oh, and I have a Logitech usb keyboard that works fine with everything else.

---

### Post by Sticky_Bit on 2009-11-13
OK I found that my keyboard wasn't working in Wine apps at all. I ticked the box on Allow the window manager to control the windows. I must have unchecked when mucking around with my performance issues. DUH... Well if anyone finds their keyboard not working in Wine apps, it's probably this.

---

### Post by meorbu on 2009-11-13
My Winamp equalizer and counter not function. Anybody have idea?

---

### Post by Sticky_Bit on 2009-11-14
I haven't tried winamp but maybe you should start a separate thread on that subject.

---

### Post by aoanla on 2009-11-15
> **feedusafetus said:**
> 
Anyone seen this before? Any suggestions? I am using Wine 1.1.32, running the game at mostly medium settings, with dx 8.1. Thanks! Oh, and I have a Logitech usb keyboard that works fine with everything else.

I have yet to find a version of Wine that gets keyboard focus right for Source-engine games launched from Steam. I fix it by alt-tabbing out of the application, then clicking on the minimised window icon (in the bottom-left of the desktop) to explicitly change focus back to it.
And then keyboard focus is where I expect it to be.

Apparently, if I remember the last time I mentioned this to someone, this is caused by something weird Source does with anonymous windows, which makes it hard for Wine to work out where focus should be automatically.

---

### Post by xeinsteinx on 2012-12-02
> **Sticky_Bit said:**
> OK I found that my keyboard wasn't working in Wine apps at all. I ticked the box on Allow the window manager to control the windows. I must have unchecked when mucking around with my performance issues. DUH... Well if anyone finds their keyboard not working in Wine apps, it's probably this.


where is this box which lets it control windows? i can't seem to find it, but i have the same issue as you

---

