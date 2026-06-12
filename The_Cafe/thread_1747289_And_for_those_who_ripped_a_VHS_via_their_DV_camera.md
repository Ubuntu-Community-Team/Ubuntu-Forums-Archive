---
title: "And for those who ripped a VHS via their DV camera..."
date: 2011-05-02
forum: The Cafe
---

### Post by jjpcexpert on 2011-05-02
... I have something that may help.

[Here is the filter chain]("http://jack-gopher.dyndns.org:70/Other/VHS.adxflist"). Import it into the Avidemux Filter List using the page-in-a-folder button in that list. (Link is to the HTTP proxy of my gopher site, running on the same server)

Well, it's basically an Avidemux (get that now if you don't have it) filter chain that applies deinterlacing and crops the gibberish from a VHS rip. If the first frame is not interlaced, you should not worry about it. If the first frame is interlaced, Yadif will deinterlace for you (bottom field first) and TDeint does the rest of the video right up to the very end. This is possibly a tech support issue, but it's for those that have gone through what would be valid for the support discussions anyway.

Stay sane, and be happy, and don't say anything you would not say to your mother.

---

### Post by Artemis3 on 2011-05-02
who ever "rips" vhs with a DV camera? Talk about overkill... You get a vhs machine, plug the video cable to a capture board in your pc (such as wintv), and the audio cable to the line in of your mobo/sound card; start recording with the pc and hit play in the vhs. Then edit/filter/reencode all you want.

I used to capture analog video like this with huffyuv/flac (lossless) in interlace mode both for broadcast or VCR source just fine. This video could be opened with avidemux for editing/filtering/reencoding into h264/aac for final storage.

Now compare the price of a dv camera vs a pci analog capture board (aka tvtuner)...

---

### Post by jjpcexpert on 2011-05-03
> **Artemis3 said:**
> who ever "rips" vhs with a DV camera? Talk about overkill... You get a vhs machine, plug the video cable to a capture board in your pc (such as wintv), and the audio cable to the line in of your mobo/sound card; start recording with the pc and hit play in the vhs. Then edit/filter/reencode all you want.

I used to capture analog video like this with huffyuv/flac (lossless) in interlace mode both for broadcast or VCR source just fine. This video could be opened with avidemux for editing/filtering/reencoding into h264/aac for final storage.

Now compare the price of a dv camera vs a pci analog capture board (aka tvtuner)...
Artemis3, I'm using my DV camcorder as a capture card (which it doubles as) because DV is I-frame only (so it's all Key frames) and therefore easy to edit. And it's higher quality than most Hauppauge cards that capture in H.263. And because it's the only thing I have and it does the job perfectly well.

And by rip: I mean record signals. Just like ripping a CD, you're recording signals from it. (albeit on a CD it's digital, so you can play it on a PC, on a VHS it's analogue so you need an analogue to digital converter, in my case the DV VCR/camcorder).

My miniDV camcorder (or camera and VCR all in one) can operate without a tape, where it is a computer controlled camera, a CVBS/LR digitizer to DV/48000PCM (PCM is uncompressed) or an SD card still camera and low resolution video camera.

---

