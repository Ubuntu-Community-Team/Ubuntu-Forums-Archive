---
title: "LADSPA effects"
date: 2009-03-10
forum: Ubuntu Studio
---

### Post by Abu_Dayya on 2009-03-10
Hi all
I was looking for some effects that I can use on vocal or guitar tracks in Ardour, I have tried some effects like reverb and amplifiers. But thats it. Can anyone please answer these questions?

- Is there an LADSPA plugin that will give me the effect of a megaphone when used on a vocals track?

- What are the common most used effects for vocals?

- What the heck does a compressor do?? I tried applying it on a track, but the sound doesn't change. I playback the track and click/unclick the bypass button, yet I can't hear the difference. I don't understand it at all.

---

### Post by Stochastic on 2009-03-10
This might help you with the last of the three questions: [http://greyrockstudio.blogspot.com/2008/05/compression-for-beginners.html](http://greyrockstudio.blogspot.com/2008/05/compression-for-beginners.html)

The second question is very subjective, as different projects all have different vocal treatments.  EQ, compression, and possibly a light reverb are pretty common.

The first question is probably answered by creating a chain of LADSPA plugins - band-limit the EQ (chop off the lows and the highs), add some distortion (possibly through hard compression), gate any noise, crank the volume.  You'll still be missing the friendly megaphone squelch though, I'm sure if you dig you could find a squelch effect around somewhere.

---

### Post by Abu_Dayya on 2009-03-10
Thanks
I'll take a look at the link when I get home infront of my computer

---

### Post by alanj on 2009-03-10
Have you checked out [http://linuxdsp.co.uk]("http://linuxdsp.co.uk") they have a pretty impressive compressor plugin. EQ/Reverb too for that matter.

---

### Post by Stochastic on 2009-03-10
> **alanj said:**
> Have you checked out [http://linuxdsp.co.uk]("http://linuxdsp.co.uk") they have a pretty impressive compressor plugin. EQ/Reverb too for that matter.
I'm always weary of downloading precompiled binaries.  I have no way of knowing what malicious code might be executing on my computer.  The screenshots and marketing look pretty though.

I also find it humorous that in order to read the license you have to download the file, and the license claims "* By downloading the software package you agree to the terms of our license agreement."

---

### Post by rayj on 2009-03-16
Compression+/&distortion (or overloading your input)>bandpass filter>reverb should get you close. Gated noise/radio static triggered by a sidechain will simulate your squelch...

Compression is the art of dealing with limiting the volume differences between the loudest and the quietest elements of your signal. There are many ways it can be used, but it is often used to limit the volume (amplitude) of a track so that it fits within a mix nicely. For example, if you go from whispering into a mic to yelling, or you stress some lyrics over others, the amplitude skyrockets from too quiet (well under the mix) to overbearing (louder than the mix). Compression can fix this, although some tweaking is required to avoid artifacts. It will also help EQ (hopefully), as it limits the amplitude of low frequencies (lots of dynamic energy) in relation to higher frequencies.

---

