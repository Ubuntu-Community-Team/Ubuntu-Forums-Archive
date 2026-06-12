---
title: "VLC crash in 12.04.2 - vlc crashed with SIGSEGV in x264_encoder_delayed_frames()"
date: 2014-05-28
forum: Ubuntu Studio
---

### Post by Lehthanis on 2014-05-28
Hello everyone!

I'm having a problem with VLC...whenever I try to convert/save or stream to a compressed stream from my capture device

If I set Sout Stream->Transcode settings and just hit record, I can capture the open capture device, but the bitrate doesn't seem to want to go low enough to make the file size manageable...(8 gb for a 40 minute low def vid) but if I go to Media->Stream->Capture Device and set up a stream to H.264+MP3 (MP4) with a file destination, it just crashes.

That's the method I feel will get me a better filesize.  Because on my windows machine I can convert/save the 8gb file using those settings and get a filesize of about 200Mb but if I try to do that same operation on this UbuntuStudio machine, it crashes just like the Stream option does...

Anyone have any ideas?
The crash report states:  vlc crashed with SIGSEGV in x264_encoder_delayed_frames()

---

### Post by mörgæs on 2014-05-29
When old software is buggy I recommend erasing and installing the latest version (14.04) as a first step.

A) The bug might be fixed already.
B) If you need to get in touch with the developers they are paying more attention to recent software.

---

### Post by Lehthanis on 2014-07-02
Sorry it's taken me a long time to reply. We had a baby.

I'm not really pleased with this answer. Especially not considering the version I'm running is a LTS version that's still in service.  How come I can't get the latest VLC updates for this build?

---

### Post by mörgæs on 2014-07-03
If you by default had the latest release of all applications in 12.04 it would essentially be another 14.04. 

You might be able to get a new VLC through a PPA but in general I don't recommend PPA's when there's an easier and safer way.

---

