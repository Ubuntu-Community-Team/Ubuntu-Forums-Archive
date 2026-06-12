---
title: "Does anyone else found that if you run GTK and Qt apps together sound can break? ._."
date: 2009-10-23
forum: The Cafe
---

### Post by hoppipolla on 2009-10-23
They like, nick each other's sound on my KDE desktop so sometimes Amarok can play and sometimes Chrome plays sound on Youtube clips... anyone know how to fix this one?

It's a shame as quite a few people mix apps depending on which desktop has the best app for a certain thing. Does the sound also get confused like this in Gnome? It might be a PulseAudio problem ._.


EDIT -- and sorry for the sloppy thread title lol

---

### Post by Tibuda on 2009-10-23
Don't know, I use VLC and Skype (Qt apps) in Gnome/Openbox/Compiz and never seen my sound breaking.

---

### Post by hoppipolla on 2009-10-23
Yeah it keeps coming up with a little message saying something about my Sound Blaster Audigy has broken in Phonon (the KDE sound management thingy). And yes before people jump on KDE - 4 is still new cut it some slack! It's not perfect but it's still AWESOME! lol :)

---

### Post by RiceMonster on 2009-10-23
What phonon backend are you using? I had some apps that wouldn't play sound (TuxGuitar mainly) when I was using gstreamer but switching to xine solved that problem (as well as sound problems that emerged with Amarok)

---

### Post by hoppipolla on 2009-10-23
> **RiceMonster said:**
> What phonon backend are you using? I had some apps that wouldn't play sound (TuxGuitar mainly) when I was using gstreamer but switching to xine solved that problem (as well as sound problems that emerged with Amarok)

I shall try that! :)

EDIT -- Owh it's already using Xine ._.  I wonder what the problem is... maybe it's something to do with my soundcard setup.

---

### Post by lovinglinux on 2009-10-23
I use mixed apps and don't have problems. In Jaunty I removed pulseaudio completely and installed esound, but in KDE Karmic the only sound setup that is working for me is with Pulseaudio. In fact it is working pretty well, without extra CPU load like in Jaunty.

You could try to go to "System Settings >>  Computer Administration >> Multimedia" and moving Pulseaudio to the top of the list for every option available there (including the top ones in the tree). This stopped the warnings and fixed any audio issue I had.

---

### Post by AlphaLexman on 2009-10-23
I have had some sound issues here: [http://ubuntuforums.org/showthread.php?t=1269030](http://ubuntuforums.org/showthread.php?t=1269030) as I have all (k/x)ubuntu on my machine.

I still have that problem, I just had to resort to using media player.

---

### Post by hoppipolla on 2009-10-23
That's a good thought I like that, as actually I may have fiddled with that before I can't remember, and PulseAudio was actually at the BOTTOM for everything, which may have been the problem.

Let's see if this is any smoother, thanks both of you :)

---

### Post by lovinglinux on 2009-10-23
> **hoppipolla said:**
> That's a good thought I like that, as actually I may have fiddled with that before I can't remember, and PulseAudio was actually at the BOTTOM for everything, which may have been the problem.

Let's see if this is any smoother, thanks both of you :)

Just keep in mind that I'm still learning the KDE stuff, so a lot of tweaks I do (including this one) is trial and error. I have HDA intel card and it was constantly failing and falling back to "Playback/recording through the Pulseaudio server" so I thought it could solve the problem by moving Pulseaudio to the top of the list. It worked, but I guess there is probably a better way of setting the sound system.

---

### Post by hoppipolla on 2009-10-23
> **lovinglinux said:**
> Just keep in mind that I'm still learning the KDE stuff, so a lot of tweaks I do (including this one) is trial and error. I have HDA intel card and it was constantly failing and falling back to "Playback/recording through the Pulseaudio server" so I thought it could solve the problem by moving Pulseaudio to the top of the list. It worked, but I guess there is probably a better way of setting the sound system.

meh, whatever.. if it works it works! :)

---

### Post by lovinglinux on 2009-10-23
> **hoppipolla said:**
> meh, whatever.. if it works it works! :)

That's true :)

---

### Post by xuCGC002 on 2009-10-23
This seems to be a problem either with only the apps you're running or the hardware you're using. Running Gtk+ and Qt apps together works perfectly for me (Firefox playing Youtube video + Amarok playing music).

---

### Post by hoppipolla on 2009-10-23
> **xuCGC002 said:**
> This seems to be a problem either with only the apps you're running or the hardware you're using.

It's probably down to settings, not apps or hardware. My hardware is standard and so are my apps lol

---

