---
title: "Help creating a DVD using .VOB, .IFO, and .BUP files."
date: 2009-06-15
forum: Ubuntu Studio
---

### Post by cainttouchthis6 on 2009-06-15
I recently downloaded a torrent for a DVD containing .VOB, .IFO, and .BUP files and I would like to burn these to create a playable DVD, but I am not sure how to do so.  I tried using Brasero to create a DVD with these files, however Brasero does not allow me to add the .IFO and .BUP files because they are not "a suitable file type for video projects."  Is there anything I can do to create a playable DVD?

---

### Post by lukeiamyourfather on 2009-06-15
> **cainttouchthis6 said:**
> Is there anything I can do to create a playable DVD?

Buy the DVD instead of pirating it? The only thing that matters is the VOB (MPEG 2 stream which is the actual video), the other files are the menus.

---

### Post by cainttouchthis6 on 2009-06-15
> **lukeiamyourfather said:**
> Buy the DVD instead of pirating it? The only thing that matters is the VOB (MPEG 2 stream which is the actual video), the other files are the menus.

I understand, but I would like the menus on the DVD so I can choose the different options that are available.

---

### Post by lukeiamyourfather on 2009-06-16
> **cainttouchthis6 said:**
> I understand, but I would like the menus on the DVD so I can choose the different options that are available.

Have you tried burning the files to a DVD (as a data project) with something like K3b or another burner? I haven't tried it myself but its possible that would work. Cheers!

---

### Post by cainttouchthis6 on 2009-06-17
> **lukeiamyourfather said:**
> Have you tried burning the files to a DVD (as a data project) with something like K3b or another burner? I haven't tried it myself but its possible that would work. Cheers!

I was going to try that, however according to K3B, if i was to burn a data project, it would only be able to play on a computer and not a DVD player.  I may just end up doing that anyways though, because i cannot seem to find any solutions.  Thanks for the advice though!

---

### Post by wadubois on 2009-06-17
Try this: Open a fresh video DVD project (I think that's what it's called.  I'm not in front of my home computer right now) in k3b which will create a file structure with two directories in it.  Drag your .VOB, .IFO's etc into the 'VIDEO_TS' directory and burn your disk.

Voila! You'll have your DVD.

A safer way is to let k3b create a .iso file first, and then use vlc or mplayer to preview the DVD.  (I currently use vlc for this, but mplayer or xine will also work.  ymmv)

Once you're satisfied with your disk you can use k3b (or any other .iso-burning program) to make your DVD.

Good luck.

---

### Post by cainttouchthis6 on 2009-06-18
> **wadubois said:**
> Try this: Open a fresh video DVD project (I think that's what it's called.  I'm not in front of my home computer right now) in k3b which will create a file structure with two directories in it.  Drag your .VOB, .IFO's etc into the 'VIDEO_TS' directory and burn your disk.

Voila! You'll have your DVD.

A safer way is to let k3b create a .iso file first, and then use vlc or mplayer to preview the DVD.  (I currently use vlc for this, but mplayer or xine will also work.  ymmv)

Once you're satisfied with your disk you can use k3b (or any other .iso-burning program) to make your DVD.

Good luck.

Alright, I really appreciate the advice but heres the deal...

I tried both of your ideas and I am still having problems.  When burning the first way, an error message appeared before any progress was actually made with the burn, the error message saying "Media is not formatted or unsupported"  and "Write Error".

When I attempted to create the .iso first, the .iso was successfully created but when it tried to burn it to the disk i got the same error message as before.  When i clicked "Show debugging Output" i noticed in the text it said, ":-( Write Failed: Wrong Medium Type"

Does this mean I have a problem with the disc I am using?  I was trying to use a Memorex 4.6 GB DVD-R.  The files only make up 4.2 GB, so the size isnt the problem, but it is possible that K3B cannot write onto certain types of DVD-Rs?

---

### Post by ttyeur4 on 2009-10-05
Hey i know how to burn a dvd. 1. make sure the .ifo and .bup and .vob files are all in a VIDEO_TS folder. 2. create a folder next to VIDEO_TS and name it AUDIO_TS and don't put anything in it. 3.download and install "IMG burn" then click on the icon that has a folder and magnify glass on it. 4. select the folder that has both the VIDEO_TS and AUDIO_TS folders in it. 5. burn (it is best to check the box while burning that's says "verify" that makes sure everything's on the disc after it is created.)

---

### Post by chrisbryan on 2011-02-11
use Nero linux version that will burn vob, ifo  & bup files.

---

### Post by lemik on 2012-04-24
Here is the answer:

[http://ubuntuforums.org/showpost.php?p=9557968&postcount=10]("http://ubuntuforums.org/showpost.php?p=9557968&postcount=10")

---

