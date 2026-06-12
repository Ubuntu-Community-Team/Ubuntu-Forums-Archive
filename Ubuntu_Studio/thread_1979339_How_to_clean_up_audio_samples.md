---
title: "How to clean up audio samples"
date: 2012-05-13
forum: Ubuntu Studio
---

### Post by Sylos on 2012-05-13
Hello all.

I have recorded some samples using ardour that have come from a TV show. The samples are of people talking but also have a variety of background noise and background music. Obviously I would like to get rid of these annoyances. 

I have tried using a gate but that does not do much good - once the level gets above the threshold it goes through. If I set the threshold higher I loose the audio I want as well.

I though about using a shelving eq run through a compressor to first highlight the nasty audio frequencies and then compress them into the audio to make them less audible. But then I would need to run a second track with the raw audio through another EQ - completely remove the frequencies in question and then mix the two tracks together. Seems like excessive work and difficulty.

Does anyone have any tips for doing this sort of processing?

Cheers

---

### Post by JC Cheloven on 2012-05-13
Hi,

Isolating (filtering) the range of frequencies of the human voice is rather inefficient if ramdom noise/sound is around. You have found that already :)

> I though about using a shelving eq run through a compressor to first highlight the nasty audio frequencies and then compress them into the audio to make them less audible. But then I would need to run a second track with the raw audio through another EQ - completely remove the frequencies in question and then mix the two tracks together. Seems like excessive work and difficulty.
 Emmm... it's an "interesting" problem (to say the least) that of yours. It's not like a hiss tape noise which can be greatly improved with noise reduction algorithms based on sampling. I imagine every kind of ringtones music, etc along the voices in your TV shows. I don't think any frequency approach will help much in that case, but if it at all does, I'd see it as a lucky event, despite the method being a bit involved ;)

Something I'm thinking of: A karaoke approach. 
It is based on the fact that the voice of the singer is usually placed "just in the middle" of the panoramic range. Basically, the karaoke effect removes the voice by "substracting" left channel from right, or vice-versa (that is, adding one to the other inverted). You obtain a mono file, or a stereo file which has the same wave in both channels. If your recordings follow that pattern, you may obtain something from that.

Although there are some karaoke plugins for different players (banshee, xmms2...), and a karaoke effect in the swh-lv2 set of plugins (Steve Harrys' plugins), you can do it in a simpler way using sox. Please install sox if you don't have it, and satisfy yourself in the manpages as for what the "remix 1,2i" and the "oops" effects can do for you.

If the voice removal has succes, your particular task would need an additional step: conceptually, substracting the original wave minus the music-only wave. This can be tricky, or maybe I'm really thick today, but I can't think right now of a method of certain success for that. So I'll give you a tentative answer, in the hope you may elaborate a better one based on these thoughts:

1) Assuming an original stereo audio called source.wav, create two mono files called sum.wav, and minus.wav as follows
```

sox source.wav sum.wav remix 1,2
sox source.wav minus.wav remix 1,2i
```
minus.wav should have no or little voice.

2) Put the two waves in two tracks in a multitrack editor (ardour, or so), timed with sample accuracy. Play them at the same time, and see if some of the noise is cancelled. Try adjusting slightly the volumes of the tracks. 

Hope this to be of any help at all.

JC

---

