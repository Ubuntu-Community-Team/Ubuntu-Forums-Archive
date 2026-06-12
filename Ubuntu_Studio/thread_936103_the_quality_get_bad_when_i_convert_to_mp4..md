---
title: "the quality get bad when i convert to mp4."
date: 2008-10-02
forum: Ubuntu Studio
---

### Post by KanineN on 2008-10-02
Hello!

When I am converting .flv files to .mp4 with ffmpeg the quality get bad. I use the code 

```
ffmpeg -i name_of_file.flv name_of_file.mp4
```

But how can I make the quality better? If a .flv file is maybe 120 but when it's .mp4 the file is around 92mb.

Can someone please help me with my problem.

---

### Post by 3rdalbum on 2008-10-03
If you want to know something about ffmpeg, the absolute quickest way is to look at the manual page:

```
man ffmpeg
```

The setting you want is "video bitrate". The man page says that the bitrate is 200kbps by default. For video, this is a low bitrate. You might want to try the following:

```
ffmpeg -i name_of_file.flv -b 500k name_of_file.mp4
```

(you must specify "k" at the end of the bitrate in order to tell ffmpeg that you want kilobits per second, not bits or megabits).

A good tip is to find about 10 seconds of footage, and encode this using the new settings to check that it works properly. There's nothing worse than waiting an hour for some long footage to finish encoding, and then finding that you got the settings wrong.

---

### Post by KanineN on 2008-10-04
ok, then I will try to convert on 500k to 1000k. Thanks!

---

### Post by KanineN on 2008-10-07
[http://img241.imageshack.us/my.php?image=namnlstu1.jpg](http://img241.imageshack.us/my.php?image=namnlstu1.jpg)

[http://img142.imageshack.us/my.php?image=namnlsfo8.jpg](http://img142.imageshack.us/my.php?image=namnlsfo8.jpg)

You see those white dots? They appear even when the video is good... And then the sound is kinda laggy. If somone say she it will go

sh sh she.. It Hard to explain but I hope you will understand.

---

### Post by KanineN on 2008-10-12
Anyone know what the problem is?

---

### Post by kg87 on 2008-10-12
sorry this may be classed as spam..

But im pretty sure that aint a disney film ;)

you should check online for FLV Converters, most od them support a large number of formats.

**Edit**,

you may want to try some of the freeware converters available for Windows/Wine..

[http://www.dvdvideosoft.com/guides/dvd/convert-YouTube-FLV-video-to-iPod-MP4-video.htm]("http://www.dvdvideosoft.com/guides/dvd/convert-YouTube-FLV-video-to-iPod-MP4-video.htm")

Is just a quick example

---

### Post by KanineN on 2008-10-17
of course it's a Disney movie. What should it else be? 	;-)

And the program you posted to was a window$ program.

---

