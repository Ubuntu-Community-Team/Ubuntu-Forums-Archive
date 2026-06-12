---
title: "I have a Huge FLAC audio collection, Can sync it to my Ipod easily time after time?"
date: 2008-02-18
forum: The Cafe
---

### Post by savantelite on 2008-02-18
If you have found a way please share,

If you havn't done it please don't tell me you "think" songbird, amarok, exail, Banshee, or Rythmbox will do it. I have tried. 

I hope there is just a simple extra step.

---

### Post by Bachstelze on 2008-02-18
Make a little shell script to transcode everything to mp3 using e.g. ffmpeg. It's very easy, but it will take a while...

---

### Post by bobbocanfly on 2008-02-18
Seeing as your music is in Flac im guessing you like your music to be good quality so using lame via a bash script with the -V 0 switch would probably get better quality results than ffmpeg, though this is just a guess.

---

### Post by fwojciec on 2008-02-18
The recent version of gtkpod (0.99.12) converts FLACs to MP3s on the fly when you "add" them to your iPod.

For an example of a script to convert FLACs to MP3s see this: [http://wiki.archlinux.org/index.php/Convert_Flac_to_Mp3]("http://wiki.archlinux.org/index.php/Convert_Flac_to_Mp3")

---

### Post by dcast on 2008-02-18
Load up Rockbox on it, this is an open source firmware for the iPod that has FLAC support. I believe it supports ipods up to 5.5 Generation, so all of them until the most recent iPod classic.

[http://www.rockbox.org/](http://www.rockbox.org/)

---

### Post by fwojciec on 2008-02-18
Here is another script for converting FLACs to MP3s (this is the one I actually use) -- I wasn't at my main computer when I posted previously:

```
#!/bin/sh
# from http://www.linuxtutorialblog.com/post/solution-converting-flac-to-mp3

OUT_DIR="./mp3"
[ ! -d ${OUT_DIR} ] && mkdir -p ${OUT_DIR}

# modify the lame options to your
# preference
lame_opts=" --vbr-new -V 2 -B 256 "

for x in "${@}"
do
FLAC=${x}
MP3=`basename "${FLAC%.flac}.mp3"`

[ -r "$FLAC" ] || { echo can not read file \"$FLAC\" >&1 ; exit 1 ; } ;

TITLE=""
TRACKNUMBER=""
GENRE=""
DATE=""
COMMENT=""
ARTIST=""
ALBUM=""
Title=""
Tracknumber=""
Genre=""
Date=""
Comment=""
Artist=""
Album=""

metaflac --export-tags-to=- "$FLAC" | sed 's/=\(.*\)/="\1"/' > tmp.tmp

. ./tmp.tmp
rm tmp.tmp

[ -z "$TITLE" ] && TITLE="$Title"
[ -z "$TRACKNUMBER" ] && TRACKNUMBER="$Tracknumber"
[ -z "$GENRE" ] && GENRE="$Genre"
[ -z "$DATE" ] && DATE="$Date"
[ -z "$COMMENT" ] && COMMENT="$Comment"
[ -z "$ARTIST" ] && ARTIST="$Artist"
[ -z "$ALBUM" ] && ALBUM="$Album"

echo "Converting ${FLAC} to MP3 format"

flac -c -d "$FLAC" | lame ${lame_opts} - ${OUT_DIR}/"$MP3"

id3v2 \
-a "$ARTIST" \
-A "$ALBUM" \
-t "$TITLE" \
-c "$COMMENT" \
-g "$GENRE" \
-y "$DATE" \
-T "$TRACKNUMBER" \
${OUT_DIR}/"$MP3"

done
```

Just paste this into your favorite editor and save it as something like "flac2mp3.sh".  After that you'll need to make it executable with "chmod +x flac2mp3.sh".  Put it in some directory that's included in PATH and then just navigate to the directory with flac files and call it like this: "flac2mp3.sh *.flac"

It requires "flac", "lame" and "id3v2" packages.

---

### Post by machoo02 on 2008-02-18
What about [mp3fs]("http://mp3fs.sourceforge.net/")?

---

### Post by nothingspecial on 2012-03-01
Old thread.

Closed.

---

