---
title: "N00b Question Re: layering Two Audio Files."
date: 2009-11-03
forum: Ubuntu Studio
---

### Post by Hutchie81 on 2009-11-03
Hi, I hope this is the right place to post this. I'm an amateur musician (and a very amateur linux user running Ubuntu 9.4 on a Dell Inspiron). I have an MP3 file with a guitar track and an MP4 file with vocals. I simply want to layer one track on top of the other to make a new, complete track (and be able to trim them to fit), but I've been struggling for about 6 hours with no luck.

   First I tried audacity and avidemux but neither would recognize the MP4 file, so then I spent ages trying to convert the MP4 into MP3. No joy - I just hit a lot of jargon and for some reason I can only download software from the 'add/remove' menu - anyway, I then tried some more advanced music production software (Ardour, rosegarden) but I was totally out of my depth and didn't have a clue where to start. Finally, in desperation, I tried to use recordmydesktop to layer the tracks by manually starting and stopping them while capturing video (sketchy huh?), but although the video recorded, there was no audio on playback! (same when I tried this technique with audacity - no audio records even though I can hear it playing through the speakers)
   
   I'm so frustrated because it seems every problem I've hit has contained 5 more, which have each contained 5 more etc., and I feel like I'm farther from achieving this SIMPLE goal than I was 6 hours ago. I'd appreciate anyone taking time out to give me some pointers, in layman's terms if possible! Thanks.
Rob H

---

### Post by skullmunky on 2009-11-13
Stop me if you've heard this jargon already ... :) 

First, using the Synaptic package manager, install "ffmpeg" (you can just enter it in the search box and it should come up).

Or, in the terminal, you can install it like this:

```

sudo apt-get install ffmpeg

```

To convert the MP4 to an MP3 this ought to work:

```

ffmpeg -i vocals.mp4 vocals.mp3

```

I also like "Handbrake", which is a nice easy to use conversion program that uses ffmpeg without having to use the command line:

[http://www.handbrake.fr]("http://www.handbrake.fr")

---

### Post by dawiba on 2009-11-13
You might find that the mp4 is protected (.m4p extension) which means, in my experience in linux so far, you won't be able to play it. So you can save yourself a bit of time and trouble there.

I might be wrong and I hope so and that someone knows how to play these files, because I have a few of my own that I'd like to import, but haven't managed to do so as yet.

---

### Post by ryanisablond on 2009-11-14
Hi Hutchie81,

I hope that skullmunky's solution works for you, and that your .mp4 files are not protected (as dawiba) suggests. 

If you absolutely need a hack to get these files together, you could try the time-tested ghetto hack of hooking up a stereo 1/8" (mini) cable from your headphone-output jack to your mic-input jack. Audio quality would decrease, but sometimes you gotta do what you gotta do.

Sounds like you already have Audacity installed, which (normally) works great for mixing and editing, so you could record your vocal track straight into there. Oh, but make sure to "mute" the mic-input so that it's input isn't being sent to the headphone output which is sent to the mic input... which would result in fabulous feedback.

Hope this helps. Let us know!

---

