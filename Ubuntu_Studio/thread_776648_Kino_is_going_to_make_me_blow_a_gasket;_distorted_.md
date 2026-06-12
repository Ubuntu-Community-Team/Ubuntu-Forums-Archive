---
title: "Kino is going to make me blow a gasket; distorted audio in mpeg output"
date: 2008-04-30
forum: Ubuntu Studio
---

### Post by dbsoundman on 2008-04-30
Ok, so this is like the 5th time I've tried exporting this video with a failure of some sort. I exported the video to an mpeg, I think I used some deinterlacing, but otherwise standard mpeg output options in kino, burned to dvd, and discovered that the video was great and the audio sounded like crazy modulated static, kind of like TV static mixed with the sound old modems made. I think the audio encoder is the mp2enc, should I change something? I tried Cinelerra and I can never get it to install or work right, so I've basically cast that off, and there's not really anything else other than Kino. Any suggestions?

Thanks,
Dan

---

### Post by tk03759 on 2008-04-30
> **dbsoundman said:**
> Ok, so this is like the 5th time I've tried exporting this video with a failure of some sort. I exported the video to an mpeg, I think I used some deinterlacing, but otherwise standard mpeg output options in kino, burned to dvd, and discovered that the video was great and the audio sounded like crazy modulated static, kind of like TV static mixed with the sound old modems made. I think the audio encoder is the mp2enc, should I change something? I tried Cinelerra and I can never get it to install or work right, so I've basically cast that off, and there's not really anything else other than Kino. Any suggestions?

Thanks,
Dan

I've had the same problem with Kino since updating to 8.04.
At first I didn't have permission to access the firewire, but I fixed that pretty easy.

But the sound problem confuses me because I didn't have problems in the past.

Edit: I didn't see the date of this. Did you find a solution?

---

### Post by tk03759 on 2008-04-30
Okay, so I tried running kino as root with sudo after a search, since my other problem was a permissions problem, but had no luck. I tried changing a bunch of options in kino, but had no luck there eithor. 

Oddly though, when I started up firefox while kino was playing video off the camera, the sound distortion from the pc speakers evened out and fixed itself. Unfortunately, when I hit record, the resulting video file still sounded distorted.

Any ideas??

Edit:

It works with sudo now sometimes? If I restart a couple times or let it play for a while, it tends to work. Makeshift solution, but it's better than nothing.

---

### Post by Alfred_McGee on 2009-03-27
My sound problem in recent versions of Kino has been more about it being out-of-synch, but anyway, the following is the best tutorial I've found for how to make a DVD from camcorder video captured with Kino: [http://www.my-guides.net/en/content/view/75/26/](http://www.my-guides.net/en/content/view/75/26/)

It's weird how difficult it is to find recent info on this topic.

---

### Post by Ubuntiac on 2009-03-27
Move to Kdenlive. Seriously. Even Kino's developer (Dan) did, and he now helps out there instead and has dropped Kino development. It's more up to date. More flexible. More powerful and just as open source as Kino. It's also available in the repo's.

Kino was great and has now fully passed the baton firmly to Kdenlive 0.7.2.1.

---

