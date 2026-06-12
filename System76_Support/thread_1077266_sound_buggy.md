---
title: "sound buggy"
date: 2009-02-22
forum: System76 Support
---

### Post by Lee_Machine on 2009-02-22
So upon installing a new batch of updates my sound stopped working, kind of...I didnt notice it at first and I dont know what updates, because for videos I used VLC, and it works, but when I watched a .wmv video it's configured to open with mplayer. The video plays just fine, but the sound doesnt work, and I get a dialog box that says unable to find audio device.

I thought it might be just for that file type, but it turned out to be everything. In mplayer that is, VLC plays everything just fine.

Another thing I noticed is that my music does not work. I open up Songbird and audio does not work, same with Banshee. They both crash when trying to play a song.

So I then went into sound preferances and chaged everything to OSS, and configured mplayer, and VLC to use OSS. 

Everything works now. What gets me is that these were supported updates, I have unsupported unchecked. 

Anyone else get this? AlSA stop working that is?

Later Im just going to purge ALSA and reinstall it. Im sure that will get rid of what ever config file got dicked up.

Hardware is Pangolin Panp4n, ubuntu 8.10 kernel 2.6.27-12

---

### Post by thomasaaron on 2009-02-23
I'm updating a PanP4 now to test.

---

### Post by betrunkenaffe on 2009-02-23
Don't know if it shipped out with it but I traced the problems on my lappy to Pulseaudio, I uninstalled it.

---

### Post by thomasaaron on 2009-02-23
OK, I'm not getting that problem.

I agree that purging and re-installing ALSA would be the most efficient way to start.

---

### Post by Lee_Machine on 2009-02-26
I purged and reinstalled ALSA and it fixed the sound issue with mplayer, but not with any music player. Them being Banshee, Songbird, and Rythmbox. 

Everything works with OSS, I just only can use one sound program at a time. 

It could be something is dicked up because I compiled the newest ALSA to get sound over HDMI and the update installed an update for the older one causing some conflict. 


But it's cool I dont really use two programs that use sound that much. In the past with OSS even programs like Deluge, and firefox counted as sound program, but not anymore. 

I'll see if I can figure it out, and if not a fresh install will fix it :lolflag:

On a last note, Im turning off all updates except security ones. Latley they have been breaking things. It's just with my laptop. All my desktops get the same updates with no issues. 

Eh, Jaunty will be here before we know it. 

Thanks again thomasarron

---

### Post by Lee_Machine on 2009-03-06
So I never did fix that sound problem. I decided to keep updates on just encase a fix came down. Sure enough today with the -13 kernel update it was fixed. I dunno if it was that or the backport modules that came with it. Either way it works now.

---

