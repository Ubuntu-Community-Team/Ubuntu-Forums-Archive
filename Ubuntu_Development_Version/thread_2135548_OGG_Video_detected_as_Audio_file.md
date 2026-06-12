---
title: "OGG Video detected as Audio file"
date: 2013-04-14
forum: Ubuntu Development Version
---

### Post by Gavin77 on 2013-04-14
I've got some videos I recorded using Recordmydesktop.  In Quantal they work perfectly but in Raring they are detected as Audio files.  I don't get any thumbnails in dolphin and the right-click "Open with" menu doesn't give any options.

[[IMG]http://thumbnails104.imagebam.com/24888/20bc49248879635.jpg[/IMG]](http://www.imagebam.com/image/20bc49248879635)

The file association for .ogv is set to Ogg Video already.

[[IMG]http://thumbnails103.imagebam.com/24889/56703b248880233.jpg[/IMG]](http://www.imagebam.com/image/56703b248880233) 

Does anyone else have this problem and is it fixable?

---

### Post by cwsnyder on 2013-04-14
What is your video player in Kubuntu 13.04?  Do you have one installed?

Raring Ringtail Xfce plays Ogg Theora videos (.ogv) with Totem with no problems.

No, you WON'T get thumbnails or play the videos without a video player installed.

---

### Post by Gavin77 on 2013-04-14
You can see in the 2nd image above that I have both VLC and Smplayer installed.  I can manually select the files and open in vlc etc.  My problem is that dolphin (gwenview also) don't detect them as video files, I only get an audio icon.

[[IMG]http://thumbnails104.imagebam.com/24892/ddd7f2248912211.jpg[/IMG]](http://www.imagebam.com/image/ddd7f2248912211)

---

### Post by Rog131 on 2013-04-15
**Preview - KDE**

To preview with the KDE and with the KDE application you need the thumbnailer.

[IMG]http://i.imgur.com/uBrrMck.png[/IMG]

**Mime types problem - at here - Kubuntu 13.04 / KDE 4.10.2**

Downloading a sample Ogg video file (small.ogv) : [http://techslides.com/sample-webm-ogg-and-mp4-video-files-for-html5/](http://techslides.com/sample-webm-ogg-and-mp4-video-files-for-html5/)

The xdg-mime query is telling:
> $ xdg-mime query filetype small.ogv
audio/ogg

Whitch is wrong -> The KDE video thumbnailer can't make a preview (video) image from the audio file -> No preview image.

[IMG]http://i.imgur.com/g3LZcX8.png[/IMG]

The mimetype is working fine with the earlier version of the Kubuntu/KDE.

**Workaround**

(working at here)

If the files from the /usr/share/mime/ is symlinked to the ./local/share/mime/

[IMG]http://i.imgur.com/DDLj27y.png[/IMG]

then the xdg-mime query is working

> $ xdg-mime query filetype small.ogv
video/ogg

and the thumbnailing is working.

[IMG]http://i.imgur.com/IlYsAno.png[/IMG]

---

### Post by Gavin77 on 2013-04-15
I tried doing ```
ln -s /usr/share/mime/video/ /home/gavin/.local/share/mime/video

``` but it didn't help.  Do I need to do anything else.  It still thinks it's an audio file.

```
gavin@kubuntu:~/Desktop$ xdg-mime query filetype small.ogv
audio/ogg

```

---

### Post by Rog131 on 2013-04-15
**Originally - linking**

I was using the the Dolphins "Link here" - Drag&drop everything from the /usr/share/mime/ to the local mime directory.


**The minimum**

The problem seems to be the "magic" file. The xdg-mime or the KDE can't find the /usr/share/mime/magic but it can find the magick via the symlink.

[IMG]http://i.imgur.com/bO06aCl.png[/IMG]

The link
> ~/.local/share/mime$ ls -l
total 0
lrwxrwxrwx 1 rog131 rog131 21 Apr 15 21:23 magic -> /usr/share/mime/magic

is working at here - Why - beats me.

---

### Post by Gavin77 on 2013-04-15
Wow, that's done it.  I already had a magic file so I deleted it and linked to the one in /usr/share/mime and it works now.
Thanks a lot for your help :)

I hope the Kubuntu devs know about this since it might affect a lot more people in 10 days time.

---

