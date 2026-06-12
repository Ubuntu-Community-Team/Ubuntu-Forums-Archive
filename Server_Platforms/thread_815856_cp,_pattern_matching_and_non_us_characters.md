---
title: "cp, pattern matching and non us characters"
date: 2008-06-02
forum: Server Platforms
---

### Post by Yulquen on 2008-06-02
ok, so I have this directory:

/media/video_01/Series/B/Brødrene Dal

containing some dvd iso`s:

Legenden om Atlantis.iso
Mysteriet om Karl XIIs gamasjer DVD 2.iso
Professor Dr?vels hemmelighet.iso

now, I want to copy those as symbolic links to, say ~/test

if I do this:
cp -s "/media/video_01/Series/B/Brødrene Dal"/* ~/test

or this:
cp -s /media/video_01/Series/B/Brødrene\ Dal/* ~/test

i get:
cp: cannot stat `/media/video_01/Series/B/Br\370drene Dal/*': No such file or directory

the above methods works with directories not containing 
non-us characters.

if I do individual files like this:

cp -s "/media/video_01/Series/B/Brødrene Dal/Professor Drøvels hemmelighet.iso" ~/test

or this: 

cp -s /media/video_01/Series/B/Brødrene\ Dal/Professor\ Drøvels\ hemmelighet.iso ~/test

they both work.

I need this functionality for a script.I know I can make my script do individual links with either cp or ln, but doing
so makes my script much slower because I need to invoke ln or
cp once for each link (I already have a script doing it like
that).

Thanks in advance for any suggestions.

---

### Post by jpkotta on 2008-06-03
Try xargs.  I haven't tested the command below.

```
ls weird_character_filenames | xargs cp -s -t destination
```

---

