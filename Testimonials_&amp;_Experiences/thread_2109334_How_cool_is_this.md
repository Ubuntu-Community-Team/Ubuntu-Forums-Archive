---
title: "How cool is this"
date: 2013-01-27
forum: Testimonials &amp; Experiences
---

### Post by GrouchyGaijin on 2013-01-27
I've been using Ubuntu since 10.04.  I'm on 12.04 now and have to say I am amazed at just how much I can do without spending any money.  THANK YOU FOSS Community!

I just learned out how to go from raw video footage to DVD that plays in a home DVD player all without leaving the command line.

Firstly thank you to FakeOutdoorsman for telling me how to set up the dev version of ffmpeg to run locally so that I can still use programs that require a different version of ffmpeg (i.e. kdenlive)

OK so if anyone wants to know, this worked for me.
I am _sure_ that there are better ways to do this, but since I am basically a hack pretending to be a geek, I'm happy that I got this to work.

1. Convert videos to proper mpeg format

```
./ffmpeg -i video.avi -aspect 4:3 -target pal-dvd dvd.mpg 
```

2. Add the mpeg to the DVD project using dvdauthor - add multiple files after each file name

```
dvdauthor -o dvd/ -t dvd.mpg
```


3. Make .iso file

```
mkisofs -dvd-video -o dvd.iso dvd/
```

4. Burn ISO

```
growisofs -speed=2 -dvd-compat -Z /dev/dvdrw=dvd.iso 
``` Note: I'm burning at a slow speed because I have an old computer and I know it won't crash using this command, you can probably go faster.

---

### Post by coldraven on 2013-01-27
Nice, well done! :)
It amazes me that people will still download and use some totally untrusted Windows software and wonder why they get pwned.

---

### Post by GrouchyGaijin on 2013-01-27
> **coldraven said:**
> 
It amazes me that people will still download and use some totally untrusted Windows software and wonder why they get pwned.

I had the same thought.  If I added up how much I might spend on software to do this on Windows, I would be out some serious money.
As it is, I have an investment for this this project of 250 SEK or about 40 US dollars for a spindle of blank DVDs.

---

### Post by FakeOutdoorsman on 2013-01-27
> **GrouchyGaijin said:**
> Firstly thank you to FakeOutdoorsman for telling me how to set up the dev version of ffmpeg to run locally so that I can still use programs that require a different version of ffmpeg (i.e. kdenlive)

Glad you got it to work.

> **GrouchyGaijin said:**
> ```
VIDEO_FORMAT=PAL dvdauthor -o dvd/ -T
```

I've never seen "VIDEO_FORMAT=PAL" being used, only "--video=pal" as shown in the man page (man dvdauthor) and by andrew.46 at the [Need ISO converter](http://ubuntuforums.org/showthread.php?p=12351726#post12351726) thread.

---

### Post by mastablasta on 2013-01-28
> **GrouchyGaijin said:**
> If I added up how much I might spend on software to do this on Windows, I would be out some serious money.

 
not really. you could just use opensource that are both free as in freedom and as in freebeer.
 
due to opensource nature of linux software. most linux programmes have a windows version while only a few windows programmes have a linux version.

---

### Post by Tamlynmac on 2013-01-28
> mastablasta
due to opensource nature of linux software. most linux programmes have a  windows version while only a few windows programmes have a linux  version. 	

I think your correct, there are many Linux apps that have a windows version.

However, I might argue with your belief that it's simply based on the "open source nature of Linux software". I think it all just comes down to a monetary issue.   ;)

Just my $0.02

---

### Post by lancest on 2013-01-28
Blender, Inkscape, Gimp perform better on Linux in my experience.
If you want performance go Linux.

---

