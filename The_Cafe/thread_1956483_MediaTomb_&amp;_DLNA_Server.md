---
title: "MediaTomb &amp; DLNA Server?"
date: 2012-04-11
forum: The Cafe
---

### Post by terrykiwi83 on 2012-04-11
[SIZE=2][FONT=Georgia]So I have a BluRay player that can connect to a DLNA server, so I installed MediaTomb (Which isn't a 'proper' DLNA server apparently) and find that its adequate, but very basic.

What are everyone else's experiences with DLNA servers, can you recommend different software? and what do you use?


[/FONT][/SIZE]

---

### Post by sdowney717 on 2012-04-11
miniDLNA
[http://sourceforge.net/projects/minidlna/](http://sourceforge.net/projects/minidlna/)

When I was trying dlna servers, this one was easiest and best to use for me.

---

### Post by Shaun_Yute on 2012-04-11
If you have a PS3 or a newer Sony surround sound system you can use PS3mediaserver. It works pretty well.

---

### Post by terrykiwi83 on 2012-04-11
Thanks for the replies, since I haven't got a PS3 just a Panasonic LCD I will give miniDLNA a try. :)

---

### Post by sdowney717 on 2012-04-11
miniDLNA has a configuration file which you can adjust for various things such as source of files.
[https://help.ubuntu.com/community/MiniDLNA](https://help.ubuntu.com/community/MiniDLNA)
also shows a deb download at page bottom

---

### Post by cariboo on 2012-04-11
I use miniDLNA for both my Samsung Blu-Ray players. It's pretty basic, but what it does do is work well. I have the version from Sourceforge on my server, and the version from the repositories on my Precise installation.

---

### Post by terrykiwi83 on 2012-04-11
> **cariboo907 said:**
> I use miniDLNA for both my Samsung Blu-Ray players. It's pretty basic, but what it does do is work well. I have the version from Sourceforge on my server, and the version from the repositories on my Precise installation.

I have installed miniDLNA on my Precise install, which went pretty well.

Only problem with it is when I access it via my TV, and click on an avi file to play it just sits on loading file then says cannot open file?

whereas mediatomb works well? any ideas? have I missed something in the configuration?

```

port=8200
media_dir=V,/home/terry/Downloads
friendly_name=Ubuntu DLNA Server
db_dir=/var/cache/minidlna
log file
log_dir=/var/log
album_art_names=Cover.jpg/cover.jpg/AlbumArtSmall.jpg/albumartsmall.jpg/AlbumArt.jpg/albumart.jpg/Album.jpg/album.jpg/Folder.jpg/folder.jpg/Thumb.jpg/thumb.jpg
inotify=yes
enable_tivo=no
strict_dlna=no
notify_interval=900
serial=12345678
model_number=1

```

---

### Post by sdowney717 on 2012-04-11
mediatomb maybe locking the directory?
turn off mediatomb and try it.

---

### Post by terrykiwi83 on 2012-04-11
It turns out that it may be a bug. Bug Report generated so will see what happens

[https://bugs.launchpad.net/ubuntu/+source/minidlna/+bug/979505](https://bugs.launchpad.net/ubuntu/+source/minidlna/+bug/979505)

---

### Post by alex2e1gzy on 2012-04-12
I currently use MediaTomb with my Samsung TV. As in my experience, if it does'nt work, it can be fixed as it is customizable!

---

