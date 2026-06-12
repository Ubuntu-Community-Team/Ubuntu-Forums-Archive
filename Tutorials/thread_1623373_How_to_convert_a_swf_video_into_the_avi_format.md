---
title: "How to convert a swf video into the avi format"
date: 2010-11-16
forum: Tutorials
---

### Post by WitchCraft on 2010-11-16
Recently I watched this video.
[http://nat.org/demos/gtksharp.html](http://nat.org/demos/gtksharp.html)

The problem was I couldn't move the movie forward or backward...
Very annoying.

So I had to convert the swf into a avi/flv video.

I downloaded the video
```

wget http://nat.org/demos/gtksharp.swf

```

Searched for edit.py in the package pyvnc2swf
```

apt-get install pyvnc2swf
apt-file search edit.py
pyvnc2swf: /usr/share/pyvnc2swf/edit.py

```

With which I could easily convert the .swf file into a .flv file
```

/usr/share/pyvnc2swf/edit.py -o output.flv gtksharp.swf 

```


From that point on, one can use ffmpeg to convert the flv movie into any popular video format, e.g. avi
```

ffmpeg -i output.flv output.avi

```

---

### Post by tkoco on 2010-11-20
Great tip. Thanks!;)

---

### Post by olemathgeek on 2011-01-19
When I try to use this and run the call /usr/share/pyvnc2swf/edit.py -o RandomB.flv RandomB.swf

I get this:

Using pygame 1.9.1release
Input movie: version=8, size=430x450, framerate=10fps, frames=633, duration=63.3s.
Output movie size: 430x450
Scanning source swf file: RandomB.swf...
Traceback (most recent call last):
  File "/usr/share/pyvnc2swf/edit.py", line 248, in <module>
    if __name__ == "__main__": sys.exit(main(sys.argv))
  File "/usr/share/pyvnc2swf/edit.py", line 243, in main
    debug=debug)
  File "/usr/share/pyvnc2swf/edit.py", line 77, in reorganize
    movie.parse_vnc2swf(fname, True, debug=debug)
  File "/usr/share/pyvnc2swf/movie.py", line 169, in parse_vnc2swf
    parser.open(fname)
  File "/usr/share/pyvnc2swf/swf.py", line 165, in open
    getattr(self, name)(tag, length)
  File "/usr/share/pyvnc2swf/movie.py", line 413, in scan_tag19
    self.movie.info.reg_mp3blocks(self.fp, length-4, nsamples, seeksamples)
  File "/usr/share/pyvnc2swf/movie.py", line 124, in reg_mp3blocks
    MP3Reader(self.mp3).read_mp3file(fp, length, nsamples, seeksamples)
  File "/usr/share/pyvnc2swf/mp3.py", line 232, in read_mp3file
    assert totalsamples == totalsamples0
AssertionError


What should I do to fix this problem?

---

### Post by WitchCraft on 2011-01-23
> **olemathgeek said:**
> When I try to use this and run the call /usr/share/pyvnc2swf/edit.py -o RandomB.flv RandomB.swf

I get this:

Using pygame 1.9.1release
Input movie: version=8, size=430x450, framerate=10fps, frames=633, duration=63.3s.
Output movie size: 430x450
Scanning source swf file: RandomB.swf...
Traceback (most recent call last):
  File "/usr/share/pyvnc2swf/edit.py", line 248, in <module>
    if __name__ == "__main__": sys.exit(main(sys.argv))
  File "/usr/share/pyvnc2swf/edit.py", line 243, in main
    debug=debug)
  File "/usr/share/pyvnc2swf/edit.py", line 77, in reorganize
    movie.parse_vnc2swf(fname, True, debug=debug)
  File "/usr/share/pyvnc2swf/movie.py", line 169, in parse_vnc2swf
    parser.open(fname)
  File "/usr/share/pyvnc2swf/swf.py", line 165, in open
    getattr(self, name)(tag, length)
  File "/usr/share/pyvnc2swf/movie.py", line 413, in scan_tag19
    self.movie.info.reg_mp3blocks(self.fp, length-4, nsamples, seeksamples)
  File "/usr/share/pyvnc2swf/movie.py", line 124, in reg_mp3blocks
    MP3Reader(self.mp3).read_mp3file(fp, length, nsamples, seeksamples)
  File "/usr/share/pyvnc2swf/mp3.py", line 232, in read_mp3file
    assert totalsamples == totalsamples0
AssertionError


What should I do to fix this problem?

I'd say file a bug-report for pyvnc2swf.

---

### Post by skarosg3 on 2011-05-10
Hi,
I am trying to convert some swf files to flv in order to be able to edit them using avidemux,since i can open flv files but not swf.
the problem is that the output is a black screen.
do you know what might be the problem?

---

### Post by geazzy on 2011-05-10
great tips :)

---

### Post by Masru on 2011-05-13
How to convert flv to avi ?? How can I joint avi videos?? Is there any software to download streaming videos ilke IDM in windows????

---

### Post by skarosg3 on 2011-05-14
> **Masru said:**
> How to convert flv to avi AviDemux

> **Masru said:**
> How can I joint avi videos?? AviDemux

> **Masru said:**
> Is there any software to download streaming videos ilke IDM in windows????
dont know, but this is an ubuntu forum, think you are in the wrong place:)

---

### Post by rbarra on 2012-01-21
Hi,

I am trying to convert a swf file into a flv video. I followed the steps provided by you, and I get a really short (1 or 2 seconds) black video. The original file is like 20 or 30 seconds long.

I wrote this in the terminal:

```
/usr/share/pyvnc2swf/edit.py -o my_video.flv my_file.swf
```

What did I do wrong? Thanks!

---

### Post by skarosg3 on 2012-01-23
@rbarra
The way i am doing it is using a windows app called  [iwisoft]("http://www.flash-swf-converter.com") using Virtual box under ubuntu.
I havent tried to install it under wine.

hope this helps

---

### Post by nikolatesla411 on 2012-03-09
> **skarosg3 said:**
> @rbarra
The way i am doing it is using a windows app called  [iwisoft]("http://www.flash-swf-converter.com") using Virtual box under ubuntu.
I havent tried to install it under wine.

hope this helps

It does work under wine very well, but it has the same problem ALL windows converters have.

They claim to be free, but then put a watermark in the output file that's too big to ignore.

So, I did some googling, and found a patch for the .exe launcher. You can download it here-----> [http://keygens.nl/crack/133815/](http://keygens.nl/crack/133815/)

Open the patch, and direct it to the .exe launcher in the installation folder. 

VOILA! No more watermark and you have clean, high quality output files!

Enjoy!

---

### Post by chickenPie4breakfast on 2012-03-11
I just used to use WinAvi under windows but cant get it to work under Wine and cant find an alternative for linux. I dont like the idea of converting from swf to flv and then to avi. The more you convert the worse the quality gets.

I did try the python prog. but like 2 of the other posters said. All I get is a black video.

using this worked for me
ffmpeg -i my.swf my.flv

---

### Post by gaosanyong on 2013-03-06
Thank you for the tip. 

The python script can surely capture the image. But the sound in a swf file is not captured in a flv file. Is there any solution to that?

Cheers, 
Ye

---

