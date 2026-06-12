---
title: "Good slide show software"
date: 2008-08-21
forum: Ubuntu Studio
---

### Post by paltwo on 2008-08-21
Hi all,

first post here for me.

I want to make a nice presentation of photos with the possibility of having some background music etc. A more advanced slide show to show for instance vacation photos etc. Hopefully with capabilities like in Open.office presentation or PowerPoint to change photos/images in different ways (blending, sliding in, fading in, fading out etc).

Something in between PowerPoint and Movie Maker and I DON'T want something that makes photos go down in quality.

I have looked at Kino, OpenMovieEditor, Avidemux already. It seems they can't do this. I also tried Cinelerra but I only got some confusing memory error and it was very unstable.

Someone have an idea? If there are all these kinds of movieeditors out there, surely there is something to make nice slide shows aswell. Please tell me so. :)

Peter P.

---

### Post by pytheas22 on 2008-08-21
I had a similar project a few months ago and, like you, tried a whole bunch of different programs.  Cinelerra can do it but I had issues getting it to render into the correct video format.  I also tried Google's Picasa, which in principle allows you to export slide shows as video, but the video wouldn't render correctly for me, either in Ubuntu or XP.  You might have better luck, though.

My solution ended up being simply to play a slideshow with Picasa and turn it into a video with screen capture software.  I used recordmydesktop; there's also Istanbul and XVidCap, and they all work pretty well.  There are obvious limitations to this approach, but it did what I needed and I was happy.  You can play sound at the same time and capture it with the screencasting application, or you can capture just a video of the slides and use avidemux, Kino or Cinelerra to add audio later.

---

### Post by paulmerchant on 2008-08-21
There's a fairly new Linux application called SMILE Slideshow. It's supposed to be great, but I'm not sure how easy it is to install on Ubuntu and I doubt that it's packaged yet. Try googling for it.

---

### Post by Creative2 on 2008-08-22
you could use** kdenlive** or** mandvd **


use Mandvd .... (father of SMILE)

**-**enable medibuntu repository ------> search "medibuntu" in google -------> repository how to 

**-**download and install this:

[http://ftp.akl.lt/Linux/Baltix/Ubuntu/getdeb/ma/mandvd_2.4-1getdeb1_i386.deb](http://ftp.akl.lt/Linux/Baltix/Ubuntu/getdeb/ma/mandvd_2.4-1getdeb1_i386.deb)

[B]
-[/B]remember to fix dvd-slideshow 

with this :

```
sudo apt-get install sox libsox-fmt-all ffmpeg  && sudo sed -i 's/-ab 192/-ab 192k/g' /usr/bin/dvd-slideshow
```

then you will be able to create a nice video from your photo


for** kdenlive** if you have some trouble see here

[http://ubuntuforums.org/showthread.php?t=791355](http://ubuntuforums.org/showthread.php?t=791355)

---

