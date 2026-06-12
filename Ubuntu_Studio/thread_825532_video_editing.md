---
title: "video editing"
date: 2008-06-11
forum: Ubuntu Studio
---

### Post by jaappolling on 2008-06-11
I installed Ubuntu 8.04. Everything seems to work fine. I also installed Kino in able to edit my video clips and movies. 
My video camera saves its files in .avi format. My Olympus camera in .mov fromat. 
Kino only seems to understand .dv and refuses to import .avi or .mov. 
Is there a way to convert these film formats so that I can edit them?

Thanks in advance
Jaap Polling

---

### Post by yodermk on 2008-06-11
mencoder could probably do it. That thing is complex though; you can try to figure it out with "man mencoder", but hopefully a guru has the command on the top of his or her head. :)

Cinelerra can edit those files directly. You might consider trying that.

---

### Post by shakabra on 2008-06-11
Look into Tovid.  I have found it very useful for avi, but I have'nt tried .mov yet.  It uses a GUI and I find that very useful.

---

### Post by Creative2 on 2008-06-11
look at fuoco tools 
it converts every formats 

but blender 2.46 can handle mov files (yes is a movie editor too :D)

---

### Post by jaappolling on 2008-06-11
> **Creative2 said:**
> look at fuoco tools 
it converts every formats 

but blender 2.46 can handle mov files (yes is a movie editor too :D)
Thanks, I downloaded fuocotools. I&#314;l see what it does. 
With blender I must have made some mistake: the blender command doesn't do anything.

---

### Post by jaappolling on 2008-06-11
> **yodermk said:**
> mencoder could probably do it. That thing is complex though; you can try to figure it out with "man mencoder", but hopefully a guru has the command on the top of his or her head. :)

Cinelerra can edit those files directly. You might consider trying that.
I installed Cinelerra (under SUSE) it takes my .avi files but only the audio tracks. I don't see any image.
So I´ll try again.
Thanks anyway

---

### Post by jaappolling on 2008-06-11
> **shakabra said:**
> Look into Tovid.  I have found it very useful for avi, but I have'nt tried .mov yet.  It uses a GUI and I find that very useful.
Thank you. I understand Tovid is in Ubuntu. So I'll try it.

---

### Post by elgalloloco on 2008-06-11
For .avi files you could also try avidemux, its in the repos.

Works very well for me!

---

### Post by Unterseeboot_234 on 2008-06-11
Because you are coming from a video camera, that .avi is almost like dvRAW format ... uncompressed, full data. Just about anything made on a Windows box that has the .avi extension will have some compression. Be aware of that. I use ffmpeg...

for ntsc, in a Terminal

```
ffmpeg -i video.avi -target ntsc-dv video.dv
```

for pal

```
ffmpeg -i video.avi -target pal-dv video.dv
```

A nice GUI is Kdenlive, based on ffmpeg with a lot of presets.

---

### Post by JEDIDIAH on 2008-06-11
> **Unterseeboot_234 said:**
> Because you are coming from a video camera, that .avi is almost like dvRAW format ... uncompressed, full data. Just about anything made on a Windows box that has the .avi extension will have some compression. Be aware of that. I use ffmpeg...

for ntsc, in a Terminal

```
ffmpeg -i video.avi -target ntsc-dv video.dv
```

for pal

```
ffmpeg -i video.avi -target pal-dv video.dv
```

A nice GUI is Kdenlive, based on ffmpeg with a lot of presets.

Yes, before you do anything to the output of your DV camera you should find a tool to tell you what is exactly in those QT files. "mplayer -identify -v" should be of some help in this respect.

Dunno if there is a good "avi-info" tool for the GUI though. It would be a handy thing to have.

---

### Post by Vivaldi Gloria on 2008-06-11
> **elgalloloco said:**
> For .avi files you could also try avidemux, its in the repos.

Works very well for me!

+1 for avidemux. It is the easiest editor I have ever tried.

It can also handle some of the mov files.

---

### Post by roberto.eiberle on 2008-06-12
it's not a problem with kino, kino will open just about any video as long as you have the necessary codecs, get all ffmpeg codecs, bad, uggly etc. and then when you tell kino to open the file it will ask if it should import instead o.k. this and it will transcode and load in dv format which you can edit and export to dvd, mpeg, divx and any format you imagine.

---

### Post by eye208 on 2008-06-13
> **jaappolling said:**
> With blender I must have made some mistake: the blender command doesn't do anything.
You have to install it first.

sudo apt-get install blender

---

