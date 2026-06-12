---
title: "WoW graphic problem"
date: 2009-11-12
forum: Wine
---

### Post by bwisdom on 2009-11-12
First off, Im on Ubuntu 9.10, and I am running wine-1.1.31
I know this is a problem with the graphics, but I have no clue what to do. Here is what I get:

```

$ wine "c:\program files\world of warcraft\wow.exe"
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  215
  Current serial number in output stream:  215

```

and this

```

$ glxinfo | grep rendering
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16

```

Again, probably pretty standard, but I dont know how to fix it. I googled somethings, but I thought I would come on here and ask around before I screwed something up too bad.

---

### Post by beastrace91 on 2009-11-12
Try updating to the latest Wine release (1.1.32) I know this was fixing alot of 3D issues many users where having.

If this does not resolve the issue what graphics card and driver version are you running?

~Jeff

---

### Post by bwisdom on 2009-11-12
Well Im back to square one. I know I said I didn't want to mess anything up, but I did. Now Im going to reinstall the whole OS because what I did messed up the X graphics thingy and all I have is a command line. But no worries, gotta learn somehow I guess.

What I do remember the card to be was an ATI Radeon x1200 (or x2100) HD mobility card (this is on a laptop) and as far as drivers I would always look under hardware devices to see if there was a driver for it, but nothing came up so Im going to guess it was using whatever comes standard with 9.10.

I know that when I first installed WoW and I did the whole glxinfo | grep rendering thing it came back saying yes, but since Ive been doing a few things to it I wouldn't know what exactly had messed it up so that it wouldnt say yes anymore.

But when I get everything squared away I will try and install wine 1.1.32. I think I tried previously but just couldnt for some reason or another so I had just settled with the version I got

---

