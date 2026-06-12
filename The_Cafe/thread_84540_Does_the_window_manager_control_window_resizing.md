---
title: "Does the window manager control window resizing?"
date: 2005-10-31
forum: The Cafe
---

### Post by Rotarychainsaw on 2005-10-31
Is there a way in gnome to have the maximize button work like OSX where it just makes the window as big as it needs to be, not take up the whole screen.

---

### Post by Brunellus on 2005-10-31
define "as it needs to be"

---

### Post by Kvark on 2005-10-31
You can use devilspie to make the windows become as big as you need them to be when they are first opened. But after you rezise the window manually I doubt you can make metacity's maximize button return the window to the size devilspie originally gave it instead of maximizing it.

You will first have to make devilspie aware of how big you need the various windows to be. You do that by writing rules like for example "all windows with firefox in the title should be resized to 600x500" (but in xml format instead of in english) in a text file. There is a great howto on it in [this thread](http://ubuntuforums.org/showthread.php?t=75749).

There might be a window manager that maximizes in the same way as OSX's window manager and that you can replace metacity with but you will probably still have to define how big you need the windows to be by typing down rules in a text file.

The reason you don't have to choose how big you need the windows to be in OSX is that the program developers there have already decided for you how big you need the windows to be.

---

### Post by Rotarychainsaw on 2005-10-31
Oh I thought OSX looked at what was in the window and made its own decision. I'm fine as it is, but just kind of liked that feature in OSX.

---

### Post by Vidar on 2005-10-31
Don't think you can do it with out making lots of custom devilpie-rules...

Sounds like a pretty nifty feature though. :)

---

