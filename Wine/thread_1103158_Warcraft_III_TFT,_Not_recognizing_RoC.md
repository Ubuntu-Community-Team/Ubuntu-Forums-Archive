---
title: "Warcraft III: TFT, Not recognizing RoC"
date: 2009-03-22
forum: Wine
---

### Post by Mandraix on 2009-03-22
Misplaced post.

---

### Post by Mandraix on 2009-03-22
I've installed RoC (via CD), and I have the .iso for TFT; but when I mount and run the TFT iso the installer tells me that I must install Warcraft III: Reign of Chaos first. As previously stated, WC3 is installed (I've ran and played it to make sure); so my question is this: Why isn't the FT installer detecting my already-installed RoC?

I'm running Wine 1.1.17, I've heard that there have been issues with the 1.23a patch but that isn't the issue I'm presently concerned with; I'm assuming that I don't have the original WC3: RoC file in the appropriate place. Any ideas?

---

### Post by Mandraix on 2009-03-22
Double-post?

---

### Post by hikaricore on 2009-03-22
Stop making duplicate threads...

---

### Post by Mandraix on 2009-03-22
I didn't, I made one-saw it was in the wrong section, and I didn't see a delete function. So I just edited out my question and made a thread here, apparently someone moved the old thread. Not sure whats up with the 2-3 repeat posts, merged the old and new threads?

---

### Post by hikaricore on 2009-03-22
You posted it 3 times, I merged them.

---

### Post by Mandraix on 2009-03-22
I only remember making two..I must've messed something up when I was backpeddling through my history.

Anyone have some thoughts regarding my problem?

---

### Post by Hairy_Palms on 2009-03-23
if ya look at your .wine folder and navigate down to drive_c/Program Files/ can u verify all the RoC files are properly installed? if so, u might try explicitly declaring the WINEPREFIX, with
```
env WINEPREFIX="/home/yourusename/.wine" wine /put/location/of/TFT/installer/here
```

and replacing it with the correct locations.

---

### Post by Mandraix on 2009-03-23
Thanks for the reply, I can run RoC through the Applications -> Wine -> Programs -> RoC. But I can't find in my .wine folder where it was actually installed.

Sorry if anything I say seems moronic, I'm new to Linux/Ubuntu.

Edit: Even in the 'Uninstall Wine Software' area, Warcraft III isn't listed. But Warcraft III would have to be installed and running through Wine or it wouldn't work, or am I wrong?

---

### Post by Hairy_Palms on 2009-03-23
if its not in your .wine folder it sounds like youve somehow managed to install it into a different prefix, so id suggest installing RoC again by forcing the prefix using the command i listed above with your own pathnames to make sure it installs to .wine

---

### Post by Mandraix on 2009-03-23
Another stupid question, could you explain what you mean by the wine prefix?

Or possibly have a link to some literature further explaining it?

Edit: I'm currently trying to install it again directed at what I'd like to believe is the correct filepath, I feel that this process would be easier if I'd had my Frozen Throne disc (I have my RoC disc, but I got Frozen Throne through a torrent as an .mfd file, and converted it to a .iso). This leads me to believe I may have done something stupid while mounting it.

Edit #2: Upon installing it again, I can now find it in my .wine folder and the other places I couldn't before. Trying Frozen Throne installer....

Edit #3: I no longer receive the error stating that RoC cannot be found, I'm sure I'll be back in some other part of the forums with a bug issue sooner or later. >_<

Thanks for all your help, Hairy_Palms.

---

