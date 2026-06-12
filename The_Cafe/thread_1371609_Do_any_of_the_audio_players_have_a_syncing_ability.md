---
title: "Do any of the audio players have a syncing ability like that of iTunes?"
date: 2010-01-03
forum: The Cafe
---

### Post by user1397 on 2010-01-03
I'm talking about banshee, listen, rhythmbox, exaile, amarok, etc.

Can any of these sync libraries with one click like iTunes?

---

### Post by Paqman on 2010-01-03
I know Banshee can do it with less than one click. If you set it up that way it'll sync whatever type of content you want whenever you plug your device in.

---

### Post by gnomeuser on 2010-01-03
> **Paqman said:**
> I know Banshee can do it with less than one click. If you set it up that way it'll sync whatever type of content you want whenever you plug your device in.

And the upcoming 1.6 release will also be able to sync devices automatically based on smart playlists. Very useful for situations where size of collection > capacity of device.

---

### Post by user1397 on 2010-01-03
Ok cool, I'll give banshee a try and I'll report how it goes.

---

### Post by Xbehave on 2010-01-03
use rsync? unless your stuck with an ipod, rsync can sync directories irrespective of mediaplayer.

---

### Post by user1397 on 2010-01-03
> **Xbehave said:**
> use rsync? unless your stuck with an ipod, rsync can sync directories irrespective of mediaplayer.Yup, I am stuck with an ipod unfortunately.  Probably not buying anything apple ever again.

---

### Post by Xbehave on 2010-01-04
> **ubuntuman001 said:**
> Yup, I am stuck with an ipod unfortunately.  Probably not buying anything apple ever again.
you might be able to mount it as a virtual partition. I think most linux mediaplayers can add/remove music but I can't find a sync option in amarok 2.

---

### Post by user1397 on 2010-01-04
> **Paqman said:**
> I know Banshee can do it with less than one click. If you set it up that way it'll sync whatever type of content you want whenever you plug your device in.So my ipod isn't showing up automatically on the left window pane in banshee after I plug it in (even after the autostart program asks me what to open my ipod with, and I select banshee).  It's an ipod classic. It shows up automatically in rhythmbox, any ideas on how to achieve this with banshee?

---

### Post by gnomeuser on 2010-01-05
> **ubuntuman001 said:**
> So my ipod isn't showing up automatically on the left window pane in banshee after I plug it in (even after the autostart program asks me what to open my ipod with, and I select banshee).  It's an ipod classic. It shows up automatically in rhythmbox, any ideas on how to achieve this with banshee?

This is because Ubuntu moved away from HAL, and this broke the special iPod handling application called podsleuth. I believe you can install banshee from the ppa (can't remember if it's the banshee, banshee-unstable or banshee-daily one that has the required code). That way you will get the required ipod-sharp, posleuth and banshee to support the new "devicekit" world.

---

### Post by user1397 on 2010-01-06
> **gnomeuser said:**
> This is because Ubuntu moved away from HAL, and this broke the special iPod handling application called podsleuth. I believe you can install banshee from the ppa (can't remember if it's the banshee, banshee-unstable or banshee-daily one that has the required code). That way you will get the required ipod-sharp, posleuth and banshee to support the new "devicekit" world.Ah, so how does rhythmbox do it then?

Out of all the media players I've tried it's the only one so far that seems to just automatically detect and show my ipod when I connect it, sans configuration

---

### Post by Xbehave on 2010-01-06
> **ubuntuman001 said:**
> Ah, so how does rhythmbox do it then?

Out of all the media players I've tried it's the only one so far that seems to just automatically detect and show my ipod when I connect it, sans configuration
Amarok will too, it just lacks proper synciness AFAIK. i'd guess it's because rythembox and kde both use the new API, but new enough versions of any media player should (in theory) support it.

---

