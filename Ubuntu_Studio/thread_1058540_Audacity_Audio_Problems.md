---
title: "Audacity Audio Problems"
date: 2009-02-02
forum: Ubuntu Studio
---

### Post by djrobthaman on 2009-02-02
Hi,

I have a question.

I installed audacity with the following problems:

1.  There is no playback audio (though it attempts to play and the cursor moves and it believes everything is fine and there are no errors)

2.  I can record if there is no track already inside the window.  If there is any track in the window I get an error message telling me that the audio driver cannot be opened.

I have been able to get around the first error by executing the program from inside the terminal using "pasuspender audacity" and adjusting the playback driver to ALSA: HDA ATI SB: ALC888 Digital (hw:0,0).

This turns off any other audio output though.

Is there any way to come up with a permanent fix to my problems?  I have used audacity before on earlier builds of ubuntu with my hardware and not had any of these problems.

On a bit of a tangent.  How can I:

Record from both my front mic and back mic (ie the mic jack in the back of the pc) at the same time?

Completely get rid of pulse (I've been having problems with this thing for ages. I just cannot get it to work properly.  Even when I tried some config tweaks suggested.  I live in constant fear of having an audio-less computer because pulse has crashed once again which requires killing pulse and restarting anything that outputs audio)

Also, extra info, I'm using the 64 bit version of intrepid with the default audacity build in the ubuntu repositories (1.3.5 beta I believe)

Thanks a bunch

---

