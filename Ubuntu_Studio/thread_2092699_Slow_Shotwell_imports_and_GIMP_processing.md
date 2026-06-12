---
title: "Slow Shotwell imports and GIMP processing"
date: 2012-12-08
forum: Ubuntu Studio
---

### Post by Eklod on 2012-12-08
Hello:

I run 64bit Studio 12.04 on the following hardware:
Gygabyte mb 970A-D3
AMD FX8 cpu
sapphire hd7770 iGig overclocked 
8 gig Kingston hyperX RAM

When I import pictures from my camera using Shotwell, response seems slooow, considering the available hardware resources. Also GIMP's response is great opening/manipulating files, but applying filers is really slow (not faster than my 5 year old laptop which only has half a gig of RAM).  Meanwhile, in both cases, lots and lots of CPU (utilised at 10%-20%) and RAM are available (30% used on average).  Under GIMP, tile size is set to 4Gig (half of amount of RAM). 

Any suggestions to speed things up?

Thank you

---

### Post by SeijiSensei on 2012-12-08
My guess is that the camera itself is the bottleneck.

---

### Post by Eklod on 2012-12-09
> **SeijiSensei said:**
> My guess is that the camera itself is the bottleneck.

Hello:

I get this behavior just editing photos, no other apps open, no camera connected.  Frustrating to wait when you simultaneously see 8 processors trotting at 22%..
My last downloand -1Gig of raw images took about 15 minutes to download from Nikon d40x to Shotwell (which uses RawTherapy to convert to .jpg).

I am thinking that perhaps increasing the priority of related processes?

---

### Post by SeijiSensei on 2012-12-09
Apparently the stable version of GIMP doesn't yet support multithreading, but in [this discussion](http://www.gimpusers.com/forums/gimp-user/15004-multi-threaded-gimp), it is mentioned that you can alter the number of processors for GIMP to use in Edit > Preferences > Environment.  Mine is set to four; perhaps you should try increasing it to eight.

---

### Post by Eklod on 2012-12-09
I have 8 processors already configured in GIMP.  Will explore multithreading as it makes sense - I also find that OpenShot is slow packaging videos from photos and does not use available processor/memory resources - perhaps for the same reasons. 
Thanks

---

### Post by eric-yorba on 2012-12-11
> **Eklod said:**
> Hello:

I get this behavior just editing photos, no other apps open, no camera connected.  Frustrating to wait when you simultaneously see 8 processors trotting at 22%..
My last downloand -1Gig of raw images took about 15 minutes to download from Nikon d40x to Shotwell (which uses RawTherapy to convert to .jpg).

I am thinking that perhaps increasing the priority of related processes?

For camera imports in Shotwell, have you tried using a memory card reader instead of your camera?  That's typically quite a bit faster.

FYI, Shotwell uses libraw to develop RAW files.  In the prefs you can set the default developer to "Camera" and it will use either embedded JPEGs inside the RAW file, or the JPEG component of a RAW+JPEG pair.  This can speed RAW import considerably.

---

