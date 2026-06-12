---
title: "Songbird or Exaile? (Sound quality)"
date: 2007-08-10
forum: The Cafe
---

### Post by Lucifiel on 2007-08-10
In terms of sound quality, which would you choose? Songbird or Exaile and why?

(Posting from Linux-xfce livecd. Whoa livecds rock!!!!!!!!! :D )

---

### Post by igknighted on 2007-08-10
Neither.  Both use the same framework underneath to handle sound (gstreamer), which does an OK job.  The problem is that both of those apps are pretty buggy.  Especially songbird, which is in a pre-alpha state.  Honestly, you probably wont notice anything wrong with the sound, but if you do, look for something built off of the jack platform (armour is the first that comes to mind, but remember that most apps built on jack are music creation tools, not really intended for playback)

EDIT: Regarding what app I recommend, I would suggest rhythmbox.  Its not flashy, but its the most stable music player.

EDIT2: Exaile is supposed to be a GTK clone of Amarok... so why not use xine?  Xine is so much nicer than gstreamer...

---

### Post by forrestcupp on 2007-08-10
Well, jack is necessary for audio creation, especially music, because with the right kernel, etc., you can do real-time or low-latency.  That's necessary for multi-track recording.

But in your case, for playback only, you don't need to worry about jack, and you don't need ardour.  igknighted is right that it's the underlying audio framework that matters, not the front end.  So as far as Songbird or Exaile goes, it's just which user interface you like better.

I guess the better question for quality would be gstreamer or xine?

---

### Post by fuscia on 2007-08-10
[ah]audacious[/choo!1]

---

### Post by strabes on 2007-08-10
amarok

---

### Post by Lucifiel on 2007-08-11
Oooh... trying Amarok now. It's awesome 'cos it's much closer to Winamp in terms of sound quality. (Edit : What? It blows away Winamp in terms of sound quality!!!)

Ooh... will try Audacious afterwards. :) 

Note: I've tried Songbird, Exaile and Xmms players so far.
Thank you for all your suggestions. :)

---

### Post by Frak on 2007-08-11
I would say neither, they both use gstreamer.

---

