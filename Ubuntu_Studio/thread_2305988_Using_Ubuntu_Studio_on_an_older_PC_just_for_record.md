---
title: "Using Ubuntu Studio on an older PC just for recording &amp; streaming"
date: 2015-12-11
forum: Ubuntu Studio
---

### Post by waxer2 on 2015-12-11
Morning all, currently I have an OS X based studio setup running Logic as a DAW, Nicecast for streaming a radio show & Traktor for mixing (using encoded vinyl).  I like to use traktor to do the radio show with, then divert the audio into Nicecast to stream to a shoutcast server.

It's a bit sticky though and sometimes I get problems so I'm looking for a completely separate solution just to record & stream.

So, I have a Behringer UFO202 USB soundcard that I would like to use with Ubuntu Studio just to take an output from my mixing desk which would be routed into a shoutcast streaming app to stream to a shoutcast server.

Also when I make tracks, I do a lot of scratching, so I make the track in Logic then bounce it down, then I try to add the scratches on top (bear in mind I'm using Traktor), so if I was using something like Cool Edit, or a DAW within Ubuntu Studio, I wouldn't have to worry about internally rerouting audio all the time (which can cause some delay).

So, the question is, can Ubuntu Studio support my soundcard & do what I want above?

Many thanks!

---

### Post by gdesilva on 2015-12-21
@waxer2, Ignore my comment if you have tried this already but I would first try to see whether the UFO202 USB card is recognized on Ubuntu Studio in the first place. I would think that it should get recognized and be useable. Run 'lsusb' command to see whether the card is recognized and then see whether you can set it as your default sound device using the sound applet.

---

