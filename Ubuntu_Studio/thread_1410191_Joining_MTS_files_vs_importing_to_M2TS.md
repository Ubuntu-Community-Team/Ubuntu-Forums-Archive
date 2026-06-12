---
title: "Joining MTS files vs importing to M2TS?"
date: 2010-02-18
forum: Ubuntu Studio
---

### Post by DPic on 2010-02-18
So, i have a AVCHD digital camcorder. Video files are stored on the camera as MTS files of no longer than 2GB (approximately 16 minutes). The software that comes with the camera is proprietary, and does not run on Ubuntu. When using it to import the video from my camera onto the computer, the software converts it into an M2TS file. On Ubuntu, i can easily [join files using the cat command]("http://www.ffmpeg.org/faq.html#SEC29") and it seems to play fine but i'm wondering what the difference is. 

When importing and converting to M2TS, does the file get re-encoded (and lose quality)? 

Is joining the MTS files the best solution for Linux desktops? 

When joining MTS files, does that mess anything up? What would be the difference between an M2TS file created from importing the files "properly", and a file created by just joining the MTS files together?

---

### Post by jsmnuk on 2010-02-18
I'd be interested in what kind of responses you get. I've got a Blu-Ray camcorder, and if I could play, edit and burn my own Blu-Ray movies on Ubuntu, I think that I could slam the door in Windows' ugly face.

The drumbeat for full Linux support for Blu-Ray is getting LOUDER AND LOUDER....(anybody listening out there?).

---

### Post by DPic on 2010-03-11
I asked on Reddit but haven't had much luck: 

[http://www.reddit.com/r/linux/comments/b3p7y/joining_mts_files_vs_importing_to_m2ts/](http://www.reddit.com/r/linux/comments/b3p7y/joining_mts_files_vs_importing_to_m2ts/)

---

### Post by Wizzu on 2010-03-20
The Reddit info looks good... I managed to get rid of the "Too many video packets in the buffer" error by adding *-demuxer lavf* to the mencoder command line. However the resulting joined MTS file didn't work too well.

@jsmnuk: The OpenShot video editor looks somewhat promising for Blu-Ray, at least you can select Blu-Ray as an export option. Don't know if it works since I've not tried it, and at least with DVD formats the results with OpenShot were not that great. :( Still, maybe it will get better, since it's under active development.

---

### Post by DPic on 2010-04-20
Hm, there needs to be some tool for importing AVCHD files from a camcorder without losing all the metadata.

---

### Post by DPic on 2010-05-05
> **jimmy8765 said:**
> [COLOR=black][/COLOR]
[COLOR=black][/COLOR] 
[COLOR=black]The M2TS container format is a standard used on Blu-ray Video discs. Blu-ray Disc Video titles authored with menu support are in the BDMV (Blu-ray Disc Movie) format and contain audio, video, and other streams in BDAV container (.m2ts), which is based on the MPEG transport stream format. [/COLOR]
 
[COLOR=black]What you want to do ?  Edit MTS files or burn MTS files to DVD/Blu  ray disc.
 
[/COLOR][COLOR=black] [/COLOR]
[COLOR=black][/COLOR]

Extract them from a camcorder while retaining metadata
[https://bugs.edge.launchpad.net/ubuntu/+bug/574870](https://bugs.edge.launchpad.net/ubuntu/+bug/574870)
and edit them
[https://bugs.edge.launchpad.net/gstreamer/+bug/327872](https://bugs.edge.launchpad.net/gstreamer/+bug/327872)

---

