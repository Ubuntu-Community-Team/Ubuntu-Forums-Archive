---
title: "Set the full screen display without black area for fluxbox and gdm login"
date: 2008-08-07
forum: The Cafe
---

### Post by leehanliang on 2008-08-07
Here is the way to match GDM and Fluxbox and to set both to the full screen display without black area.

Open  etc/X11/xorg.conf  with any editor as a root user.
Inside the file you may find the script about screen section as below.

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "1024x768@85 +0+0; 1024x768@43 +0+0; 1152x864@75 +0+0; 1024x768@60 +0+0; 1280x1024@75 +0+0; 1024x768@70 +0+0; 1280x960@60 +0+0; 1024x768@75 +0+0; 1280x960@85 +0+0; 1280x1024@85 +0+0; 832x624@75 +0+0; 1280x1024@60 +0+0; 800x600@60 +0+0; 1280x960@75 +0+0; 800x600@85 +0+0; 1400x1050@60 +0+0; 800x600@75 +0+0; 1400x1050@75 +0+0; 800x600@72 +0+0; 1600x1200@65 +0+0; 800x600@56 +0+0; 1600x1200@60 +0+0; 640x480@85 +0+0; 640x480@75 +0+0; 1600x1200@70 +0+0; 640x480@72 +0+0; 1792x1344@60 +0+0; 640x480@60 +0+0; 1856x1392@60 +0+0; 1920x1440@60 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


Then, in "Option " and "Modes" simply delete all the Resolution Options that is higher than your favorite resolution.

Example: 
Here I prefer only 1024x768@85 +0+0 in the "Option" and "1024x768" in the "Modes".
So, simply I delete "1600x1200" and "1280x1024" and whichever are HIGHER than my preference, with those lower ones remained for just in case.
Then, save the file and done.

P.S. since those higher options as been remove, at the time of starting up, both GDM and Fluxbox have no better resolutions to select and have to match your preference.
I am a absolute newbie and I know it's not a nice trick. But it works for me.
Hope it works for you, too.
Any opinions are more than welcome.

Tony Lee

---

### Post by billgoldberg on 2008-08-07
Real fluxbox users don't use the gdm.

:p:p

Nice write up.

---

### Post by leehanliang on 2008-08-07
Hi, billgoldberg
Thanks for having a look at my post!
You are quite right! I also admire those folks who can play with barebone fluxbox. But I still have a long way to go that far. Still struggling in trivial "problems", I hope the above can help other newbie-fellows like me. =)

---

