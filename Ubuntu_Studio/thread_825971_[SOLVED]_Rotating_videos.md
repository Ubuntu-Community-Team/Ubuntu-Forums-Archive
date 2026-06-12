---
title: "[SOLVED] Rotating videos"
date: 2008-06-11
forum: Ubuntu Studio
---

### Post by natirips on 2008-06-11
Is there any program I can use to **rotate an mp4 video by 90 degrees**. (It has been recorded using a mobile phone tilted by 90 degrees, but turning my display by 90 degrees ain't that practical).

I've already tried with Kdenlive (it simply won't export files, when I tell it to save a file it does nothing, also didn't seem to do anything with the effects I told it to apply), Blender (coudn't load an mp4), Avidemux (GTK+ and Qt) (I couldn't figure out how to acctually APPLY the effect, only preview it), Kino (doesn't have the feature), Open Movie Editor (doesn't have the feature) and Pitivi Video Editor (doesn't have the feature).

Any help appriciated.

---

### Post by Vivaldi Gloria on 2008-06-11
I just tried it with avidemux. I use xvid and also I don't use the english version of avidemux so I may not describe it perfectly but you'll get it.

1. start avidemux and load your video.

2. choose avi from the button at the (almost) bottom left.

3. choose the line containing Xvid4 on the top video button at the left.

4. Press the filters button which is the third button on the left.

5. Find rotate filter, double click it, choose angle and click ok.

6. Now close filters windows.

7. Press the Save button and enter a new name name.avi.

That's it.

---

### Post by natirips on 2008-06-11
Thank you so very much. Worked like a charm. Thanks again.

---

### Post by Vivaldi Gloria on 2008-06-11
You're welcome.

---

### Post by ivainsencher on 2009-12-31
live would be easier if all tips in the forum were that crystal clear:-)

---

### Post by Jimmy9pints on 2010-05-29
Thanks!!!!!!

Still useful years later. 

It's a shame PiTiVi can't do this.

---

### Post by ravi84m on 2010-07-12
I have a problem with the audio when doing this. Does anyone have a solution to this?

---

### Post by Jimmy9pints on 2010-07-13
I don't have a solution, but just to confirm I have some sound problems too doing this. Sound becomes either very compressed (high pitch), or streched out (lower pitch).

If you find a solution, please let us know!

---

### Post by mjones41 on 2010-10-28
Really good explanation, thanks.

And yes it is a shame that Pitivi is the Ubuntu standard movie maker, but it is sadly lacking.  Please guys look at how easy Windows Movie Maker is.

---

### Post by gotamangoflavouredrat on 2011-05-21
apologies for reviving a very old thread. The instructions work. 

[LIST=1]
[*]I dont have any sound anymore
[*]The resulting video cannot be imported in to PiTiHiVi
[/LIST]
Guess will have to do edit the video on a windows machine tommrow

---

### Post by matbonucci on 2011-09-12
> **Vivaldi Gloria said:**
> I just tried it with avidemux. I use xvid and also I don't use the english version of avidemux so I may not describe it perfectly but you'll get it.

1. start avidemux and load your video.

2. choose avi from the button at the (almost) bottom left.

3. choose the line containing Xvid4 on the top video button at the left.

4. Press the filters button which is the third button on the left.

5. Find rotate filter, double click it, choose angle and click ok.

6. Now close filters windows.

7. Press the Save button and enter a new name name.avi.

That's it.
 thank you, it worked

---

### Post by 98cwitr on 2011-11-12
FYI, PiTiVi has rotate effects now :)

---

### Post by rvec on 2012-01-05
Thanks heaps. Worked a treat.

---

### Post by bcarlowise on 2012-01-10
I've used mencoder up to now to accomplish video rotation but after trying both avidemux and Pitivi it's nice to finally have a gui tool to rotate my videos. Avidemux worked perfectly but Pitivi crashes when saving/exporting the video.

---

### Post by Botruckle on 2012-04-06
For those having audio issues, be sure to click the Audio button on the left and specify a codec, such as "MP3 (lame)". This is all it took to get audio to go along with my video (which had no audio until I did it).

---

### Post by leona on 2012-05-12
> **Botruckle said:**
> For those having audio issues, be sure to click the Audio button on the left and specify a codec, such as "MP3 (lame)". This is all it took to get audio to go along with my video (which had no audio until I did it).

I had the audio problem, solved by going to Audio (on the top menu) and selecting 'Rebuild VBR Time Map', seemed to cure it.

---

### Post by daddyfix on 2012-08-20
Thanks!

---

### Post by smartboyhw on 2012-08-21
This thread is real old.... Maybe someone should close it or something. Anyway, rotating videos shouldn't be difficult...
 
Regards,
Howard Chan
Ubuntu Studio Team Member at [https://wiki.ubuntu.com/UbuntuStudio/TeamStructure](https://wiki.ubuntu.com/UbuntuStudio/TeamStructure)

---

