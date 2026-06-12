---
title: "How do I send video to OS-X?"
date: 2008-05-03
forum: Ubuntu Studio
---

### Post by adair on 2008-05-03
I need to send a video clip to a relative who has a bog standard OS-X setup. They are not confident about tweaking software, etc. so loading a plugin to Quicktime Player (or installing VLC), is not really an option.

Does anyone know what format/codecs I should use that will play on the default 'Quicktime-player'? The clip is an AVI file containing jpeg video and pcm (from memory), audio.

I can convert it using Avidemux and/or ffmpeg (or other if required), but I don't know what specification to use.

Thanks in advance, Adair.

---

### Post by kaiataris on 2008-05-06
Try creating an .mp4, It's a format that quicktime can play, and a format you can convert to using ffmpeg or mencoder. 

You might what to search for a guide that will give you the right switches to make  the .mp4 quicktime compatible.

-Kai

---

### Post by adair on 2008-05-06
Thanks for that, but what I thought was a fairly basic question is turning out to be non-trivial!

My latest attempt (using the mp4 container) was with the MPEG-4 AVC (x264) video codec and AAC (FAAC) audio. Audio works fine at their end, but no video. Turns out the h.264 codec used by Avidemux isn't compatible with Quicktime (though it ought to be!).

Apparently ffmpeg can successfully code for Quicktime compatible video, but looking at the guidelines for achieving it---well, I've got a life to live and there aren't that many free hours in my day!

So, if anyone has a reasonably straightforward recipe for creating, in Linux, a video package that is compatible with vanilla Quicktime (v. 7 I should think), in OS-X I would still really like to know about it!


Regards, Adair.

---

### Post by wkulecz on 2008-05-06
When I want to be sure a random system can play a video without needing to download I fall back to mpeg1 encoding.  Not the best compression but encoding quality is better than most everything on you tube and if the system can't play mpeg1 its hopeless to try anything newer.

I found Kino makes nice VCD format (352x240) encodings pretty painlessly.

--wally.

---

### Post by adair on 2008-05-08
Thanks for the Kino and mpeg-1 suggestion. Not great quality but it does actually work---unlike everything else I've tried! Mpeg-2 with VCD seems to lock up, when they play it, within a few seconds of starting; never mind.

It is mildly disturbing to realise that with all the effort put into video on the net and PCs over the last ten years there still aren't any standard generic AND up-to-date cross-platform codecs that are obviously and easily available, i.e. to video what .txt or .rtf, or even .pdf are to text! They don't have to be all singing all dancing, just adequate, recognised, and SUPPORTED!

But then what would be the fun in that?

Cheers.

---

### Post by adair on 2008-05-09
Okay, after more research and experiment here is a solution that seems to be straightforward and offering good quality with up to date codecs:

Import original to Kino
(if necessary Kino converts the file into the 'standard' dv format that it uses)
(edit if required)
'Export' from 'Other' menu as: 'mp4' with h.264 video (dual pass), 'Profile' set at 'Medium quality'.

Job done; small file size (12Mb from 180Mb), and reasonable quality.

Thanks everyone.

---

