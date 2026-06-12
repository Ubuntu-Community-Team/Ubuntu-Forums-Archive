---
title: "Photo management similar to Aperture? Gnome based"
date: 2009-09-27
forum: Ubuntu Studio
---

### Post by ormandj on 2009-09-27
Hi,

I've seen Digikam, which seems fairly neat, but I'm looking for a GTK based solution. Are there any out there? I'll be processing 1500-2000 RAW images every 2 months, roughly, so I need something to help manage the mess. I'm currently using an older first generation Intel-based Apple, but I do NOT like it.

I need two things - good RAW conversion and the ability to manage a large collection of photos. I can fire up Gimp if necessary (it's getting better, still no PS, but good enough for most needs) for the basics (such as noise reduction/tone adjustment/etc), but I absolutely need something to help me manage all of the photographs without losing my mind. :)

Any suggestions? I'm not a fan of f-spot. I don't mind RAW conversion being done on the CLI if that's necessary, but it would be nice if the application was RAW aware and could handle it internally. My camera will be profiled, so I will need some type of RAW conversion/application that allows this to be utilized.

Thanks!
David

---

### Post by ormandj on 2009-09-28
I found solang, which looks promising, but very young. Bibble was especially promising, but it appears they do not make a true 64-bit version, only a 32bit version that runs using the 32 bit libraries. With the amount of photos I deal with, the extra RAM that 64-bit allows for would be nice. I'll have to contact the makers. Also, it's closed source, which is disappointing, but not necessarily a show-stopper.

RawTherapee looked interesting, it sounds like the next iteration is going to be fairly awesome.

---

### Post by blur xc on 2009-09-28
I've been playing w/ a demo version of bibble.  Version 5 is looking to be pretty sweet, I hope it comes out soon.  And it's noise reduction (noise ninja) is pretty amazing.  The bibble workflow is different, and I still have a lot to learn, but it is very fast.

BM

---

### Post by Neobuntu on 2009-09-30
ufraw plug-in for Gimp might help you.

---

### Post by UbuWu on 2009-10-04
For raw conversion/processing Rawstudio is pretty good.

---

### Post by Neobuntu on 2009-10-19
ufraw (separate; before tweaked NR in digikam)seems to be about the best (in open software Raw processing) at this time. I'm a huge fan of Kubuntu; and these Raw development options are not yet, as good as, Lightroom (on closed systems). This will likely improve; if we take it seriously.

Addendum: Noiseware and Topaz Denoise may be the best(XP). Noiseware being fastest (retaining detail and eliminating most of the noise) and Denoise (a plug in for Photoshop)eliminate most (as in about ALL) noise and miraculasly retaining detain. Catch: It will not let you export, without signing up. I think we need an open competitor. Yet, you can try (see results at 100% mag) Topaz Denoise; for free.

At this point, while Digikam does a good job of editing JPEGS (and can do Raw), if you are (copying to tiff and) editing your JPEGs then you should be shooting Raw (when you can). Not "Raw+JPEG(standard)" but Raw and/or Fine-Jpeg. Raw files include an embedded standard JPEG anyway. Yet, you still need to improve it. That, is what you see; BEFORE a Raw file is developed (and if it's purple then it, is not correctly handling your Raw format. Seek a Raw update, for your developer). 

Reference camera: FZ28 with Raw (.rw2)
Adobe Lightroom (Lr): V2.5 with Adobe Camera Raw (ACR) combined; updated.

Specifically, the NR is not quite as good, as in Lr, for tweaked, end-results (on a noisy, dim lighting, no-flash, DMC-FZ28, control picture). More artifacts are also present. FZ28 specific camera adjustments (CA, Barrel etc...) are not auto applied. More work; per raw picture, is required (not a good thing).

Mainly, the overall feel of the program and it's flow, are not nearly as mature, capable and smooth. Yet, Rawstudio can get you by; but it is arguably not worth it when compared to JPEG(Camera dependent). Especially for someone who rarely chooses to do Raw. Meaning those who DO NOT post process their fine-JPEGs; but rather may tweak the camera to achieve similar effects (like I-Exposure/D-Lighting, the Picture Settings and/or I-ISO) and also allow things like faster multi shots per second ("Drive mode"; when it is not available with Raw). You want JPEG; for time savings.

Yet, you WILL want Raw for contrast-y(DR) and low light(NR) scenes. The maximum range and color(WB) can be shown to a greater extent (basically ALL the sensor saw); when needed. Yet, Raw processing is such a time consuming, and per photo endeavor, you will want a program that does Raw (and your entire work-flow) the fastest, and the best! This is the critical point; of any Raw development module.

Batch Raw processing is only for multiple shots; of (basically) the same thing. Even then, a batch process may not bring the best individual improvements(when changes creep in). For me, Raw processing is a picture, by picture tweaking process, by in large. That editing process (with total IQ paramount) has to be FAST and with superior(IQ)! Else, there is no point in it.

Note: Never change your original photograph. Work on a copy or use a system like Lightroom that stores changes in it's "library". Then you export the final product in the form required. Such as web, 4x6, 8x10 etc... If it's worth keeping, it's worth keeping (and backing up) the original. JPEG or Raw. Yes, you will need a bigger hard drive. Copy Fine-JPEGs to TIFF, if you plan to pass it through many different editors(they all have their pluses). Yet, in that case, you might as well, do Raw(when you can).

Note: You will not notice better NR (Noise reduction in low light) with Raw (Compared to well done JPEGs; with there instant NR), *unless* you use the better noise reduction programs. 

Keep in mind, in this case, the resolution and sharpness of the quality (Lecia) lens, allows you to achieve better (moderately dim light; depending) results than most cameras, even after your NR smoothing/softening is applied (using ACR; in Lightroom for example. Not so much, in others). Thus covering most real world situations; with a more flexible lens (and lower total costs, more portable and not A NOT as often banned, camera system). Time for processing, is the catch with Raw.

Note: There are other nasties besides noise. All these are but one small part; of total IQ. Total IQ (if it's passable) is but one small part of a great, and heart-moving photograph.

Note: If this report does not make it to the developers, then Ubuntu and/or Rawstudio is being mismanaged(like it or not).

I do not think Lightroom works well, in WINE. Virtual box, maybe.

Mac users can choose Lr or Aperture(OS-X only). Aperture may only be slightly better; in usage. However, It is not reported to create better resultant IQ. Thus, I have not tested it. Yet, you can see extensive demos for Lightroom and Aperture, on-line.

Lightroom is very expensive, Sometimes. Perhaps you can obtain a free trial, or something. Make sure your computer meets the required hardware specs.

---

### Post by Neobuntu on 2009-10-29
All that to say, we can get very (VERY) close to the best NR available in Windows now. The difference is almost ALL noise gone (if it wasn't ridicules to start with; it depends. Obviously, I used the same noisy test subject) while retaining all the detail. Compared to the best in open software, only slightly more noise showing with same the detail level.

I already said, this was with the FZ28 (and VERY dim light no-flash and far away) and it's fairly tough noise, in the shadows (nit picking at 100% and for enlargement prints 8x10 or more). A larger sensor camera would likely get better reduction results (given similar lens characteristics and the same scene); but at a much more exclusive price tag.

More people looking for noise reduction from the open software system, may then have a similar noise profile, as my camera. Again, mine was a tough (noisy) and real world control picture.

This is certainly where we can improve. Just know that all NR programs produce widely differing results, and we want to beat, the best.

1. I don't know why you get better NR; if you import with ufraw first and then do NR with DigiKam. As opposed to just doing it all in DigiKam.

2. DigiKam is almost there, as being the world best, one stop shop, for total photo manipulation. Lightroom being the competition there.

All this proves Raw can be better (low light or high contrast scenes). It highly depends on the Raw development programs used (and your Raw tweaking skills). That doesn't mean there are not other advantages; to just shooting JPEG. We need both.

---

### Post by JuanC on 2010-01-06
Have you tried [Shotwell]("http://www.yorba.org/shotwell")?

---

### Post by Neobuntu on 2010-01-29
No, I haven't. 

Thank you for the heads up!

---

### Post by Neobuntu on 2010-05-13
I'm currently peeved at DigiKam. For all it's comprehensive goodness, it's still crashing on me; only after I've done a bunch of processes on a photo. All was lost. NOT COOL! I had this problem last year and the year before; but I thought it was just passing growing pains. It has a wonderful restoration process (and NR); but it's also too darn slow!

DigiKam needs HELP; Fast! Yes, I reported it. 

Also, I hear rumor; that Lr works for some, with Crossover.

---

