---
title: "MPD setup that may be of interest. Have questions"
date: 2007-08-04
forum: Server Platforms
---

### Post by skinnymonkey on 2007-08-04
All right. So this is my first question on the board. Thanks in advance for any help.

I'm using MPD for my waiting room and phone on hold music. I would like to add a "zone" and separate the phone and normal music so I can play brief marketing type stuff between normal music on the phone system.

So the questions are:

Can I run multiple instances of mpd with different playlists? 

What would I need to modify to output to channels 1 and 2, then another output to channels 3 and4? Or even two different mono outputs to channel 1 and channel 2 using separate playlists. 

Got any ideas how to pllayback files in mono without changing the audio files or y-ing the outputs?

I'm sure this could be done, but not sure where to start.

---

### Post by skinnymonkey on 2007-08-08
Anyone?

---

### Post by dreadlord_chris on 2007-08-08
> **skinnymonkey said:**
> Anyone?

Yes, mpd can serve different playlists to different connecting clients...
For the rest - I think you're looking for something like [JACK]("http://jackaudio.org/")

it's in the repositories...

---

