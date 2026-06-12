---
title: "Ubuntu idea: Profiles"
date: 2008-11-18
forum: Ubuntu Brainstorm
---

### Post by gardara on 2008-11-18
Not sure if I'm posting this in the right place, so let me know if I should post this somewhere else... 
I got a idea that I would really like to see on my laptop.
Not sure if ubuntu team can do it, if it's a job for gnome or kde maby... or if such thing exists already somewhere.

I carry my laptop around with me everywhere I go (school, work, home, friends houses). Everywhere I go I connect to different wireless networks and use different things, at some places I use proxy, other place I use a ssh tunnel and some places I don't (just direct connection).
I am wondering if something like profiles could be done, so when I am at school I can just click one button and all the settings apply (proxy settings for my applications... firefox, xchat, pidgin proxy and status message (even nick), brightness and volume change, even wallpaper and theme changes.)
This could also be automatic, for laptops with gps or just when I connect to a different wireless network.... Or maby even timed.
The possibilities for this kind of "profiles" are endless, and It's something I really would like to see for my laptop...

What do you guys think?

---

### Post by Bölvaður on 2008-11-18
System &#8594; Administration &#8594; Users And Groups

Add new user (profile), set up different theme... click the switch user button... :popcorn:

---

### Post by gardara on 2008-11-18
> **Bölvaður said:**
> System &#8594; Administration &#8594; Users And Groups

Add new user (profile), set up different theme... click the switch user button... :popcorn:

haha yeah... Well not exactly what I had in mind... A good point though...



Btw, gaman að sjá fleiri íslendinga hér \\:D/

---

### Post by Swarms on 2008-11-18
I think its an great idea, but shouldn't it rather be like it remembered each connection you have made?
Like I cycle between two connections normally, home and school. The connection at school is secured by proxy but I have to go into each individual program I want to use and de- or activate proxy settings if I want to have online access.

For the boys from Iceland:
Ked af med jeres kommende statsbankerot, I er velkommen til at komme under vores flag igen. :P

---

### Post by gardara on 2008-11-18
> **Swarms said:**
> I think its an great idea, but shouldn't it rather be like it remembered each connection you have made?
Like I cycle between two connections normally, home and school. The connection at school is secured by proxy but I have to go into each individual program I want to use and de- or activate proxy settings if I want to have online access.

Yeah I think there are many ways to implement this... I got this idea originally because I hate having to activate and de-activate proxy in all my applications xchat, firefox, and all my pidgin accounts (msn, gtalk, facedbook, myspace, icq, aol)... I have been thinking about this for some time now and I can always see more and more things that would be nice to include in this "profile" support....

> **Swarms said:**
> 
For the boys from Iceland:
Ked af med jeres kommende statsbankerot, I er velkommen til at komme under vores flag igen. :P

hahaha

---

### Post by johnkzin on 2008-11-18
> **Bölvaður said:**
> System &#8594; Administration &#8594; Users And Groups

Add new user (profile), set up different theme... click the switch user button... :popcorn:

In which case they all have different UID's and home directories, so while the things that should be separate are separate, the things that should be the same are not.

You could do some hacking to make it seem more appropriate (give them all the same UID, symlink the heck out of their home directories so that everything other than config files are shared, etc.).  But it's still going to be a fragile, high-maintenance, hack ... instead of a "solution".

Real profiles would be nicer.

---

