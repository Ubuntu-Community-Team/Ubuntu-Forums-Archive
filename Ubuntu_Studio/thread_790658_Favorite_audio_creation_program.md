---
title: "Favorite audio creation program?"
date: 2008-05-11
forum: Ubuntu Studio
---

### Post by eleifsp on 2008-05-11
I enjoy editing and creating audio (usually stuff my friends play that I mix), and while playing around with ALSA the other day my microphone started working all of a sudden (I really am not sure what I did to make it work, but I'm happy all the same).  

I usually use Audacity to edit songs/sounds because it seems like the best one out there (and I have a bit of experience with it and Adobe Premier, which has a similar feel to Audacity).  For some reason, however, Audacity won't let me record.  Sound recorder will, but not Audacity.

Anyway, I was wondering what other audio programs everyone uses with Linux and why.  

Also, if anyone has used Adobe Soundbooth, is there any program on Linux that works vaguely like it?  (It's really one feature I was looking for that Soundbooth has:  it can render an audio clip into an odd-looking map that shows different frequencies, and lets you use tools to patch the sound visually.  It's a really cool feature, but I don't have money right now to buy soundbooth.  Or the patience to boot Windows to use it.)

---

### Post by Stochastic on 2008-05-11
Well in Linux there are a ton of tools that each do one part of audio creation very well.  If you're serious about mixing, Ardour is the best app, but it can be hard to learn if you're a noivce.  As far as the neat little graph of frequencies you're talking about in Soundbooth, is it this (screenshot from Adobe.com): [IMG]http://wwwimages.adobe.com/www.adobe.com/products/soundbooth/images/sb_heal_285x200.jpg[/IMG]
If so, that's called a spectrogram and many apps in linux can display those (even some players).  Check out FreqTweak if you want fine grained control over frequencies with a spectrogram for feedback.  Audacity (and most editors for that matter) has the ability to display the waveform as a spectrogram - just select the dropdown menu where the track name is (the little black arrow down) and select 'spectrum'.

But if you want to get into creating music, not just mixing other people's, you'll need synth apps and some midi sequencing (check out ZynAddSubFX, Rosegarden, Qsynth, and Muse).

Audacity should work if sound recorder works, try checking in Edit->Preferences->Audio I/O as to which devices are selected.

---

### Post by eleifsp on 2008-05-11
Thanks!  That is the program I was talking about.  I'm reinstalling audacity right now, so maybe there was a setting I messed with (which I think is the problem).

As for creating music... Not so much.  I'm not really musically talented, but I'm good at mixing and editing.  I'll stick with what I know (for now).

Plus, I have a bit of an aversion to Midi files... They just sound too unrealistic to me.  If I want to compose music, I'll use the electronic keyboard I have in my closet.

EDIT:

I reinstalled and I still can't get it to record.  I attached a screenshot of the error it gives me, maybe that can help.  I messed around with both the device to record from and the sample rate, but no dice.

Also, I found the spectrum thingy.  I got excited, grabbed the pencil tool, and it gave me the error that pencil tool only works on linear views and everything froze.  Except my cursor.  It's times like this that I just love linux for the simple control alt backspace command.

I'm trying out FreqTweak like you suggested.  That looks interesting.

EDIT2:

I tried out FreqTweak.  Not exactly what I need.  Is there a program that I can edit an existing file using the spectrum (like what can be done in Soundbooth, you can like it shows in the picture circle areas of the file and patch it to reduce sound in certain frequencies.  That's what I really am looking for, a powerful editing tool.)

---

