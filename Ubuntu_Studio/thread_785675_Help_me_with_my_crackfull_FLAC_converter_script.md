---
title: "Help me with my crackfull FLAC converter script"
date: 2008-05-07
forum: Ubuntu Studio
---

### Post by MetalMusicAddict on 2008-05-07
Ok. So I got this bash script I use to take FLAC to other formats then .tar it up at the end. I'm tossing it out there to see if anyone wants it.

I'm pretty sure some of it is redundant. Shape it up if you can. :)

I call the script "gimmie" and it assumes your source is FLAC.

So usage is like: gimmie <format>
[LIST]
[*]vorbis
[*]mp3
[*]flac (just archives everything up)
[*]musepack
[*]wavpack
[*]faac
[/LIST]

```
[SIZE="1"]#!/bin/bash
#This script depends on the: id3v2, lame, flac, faac, wavpack, mppenc and vorbis-tools packages.
#echo Enter the root directory of the music you want:
#read pathToDir
#cd $pathToDir
format=$1
if [ "$format" = "vorbis" ]; then
   for a in *.flac
      do
         OUTF=`echo "$a" | sed s/"\.flac$"/"\.oga"/g`

         ARTIST=`metaflac "$a" --show-tag=ARTIST | sed s/.*=//g`
         TITLE=`metaflac "$a" --show-tag=TITLE | sed s/.*=//g`
         ALBUM=`metaflac "$a" --show-tag=ALBUM | sed s/.*=//g`
         GENRE=`metaflac "$a" --show-tag=GENRE | sed s/.*=//g`
         TRACKNUMBER=`metaflac "$a" --show-tag=TRACKNUMBER | sed s/.*=//g`
         DATE=`metaflac "$a" --show-tag=DATE | sed s/.*=//g`

         flac -c -d "$a" | oggenc -q 6 --artist "$ARTIST" --album "$ALBUM" --tracknum "$TRACKNUMBER" --genre "$GENRE" --title "$TITLE" --date "$DATE" -o "$OUTF" -
      done

   mkdir -p "$ARTIST"/"$ALBUM"
   mv *.oga "$ARTIST"/"$ALBUM"/.
   cp *.png "$ARTIST"/"$ALBUM"/.
   tar -cvf "$ARTIST - $ALBUM"-OGA.tar "$ARTIST"/"$ALBUM"/*.oga "$ARTIST"/"$ALBUM"/cover.png
   rm -fr "$ARTIST"
   mv *.tar /media/Multimedia/Audio

fi

if [ "$format" = "mp3" ]; then
   for a in *.flac
      do
         OUTF=`echo "$a" | sed s/"\.flac$"/"\.mp3"/g`

         ARTIST=`metaflac "$a" --show-tag=ARTIST | sed s/.*=//g`
         TITLE=`metaflac "$a" --show-tag=TITLE | sed s/.*=//g`
         ALBUM=`metaflac "$a" --show-tag=ALBUM | sed s/.*=//g`
         GENRE=`metaflac "$a" --show-tag=GENRE | sed s/.*=//g`
         TRACKNUMBER=`metaflac "$a" --show-tag=TRACKNUMBER | sed s/.*=//g`
         DATE=`metaflac "$a" --show-tag=DATE | sed s/.*=//g`

         flac -c -d "$a" | lame -V 3 --vbr-new - "$OUTF"
         id3v2 -t "$TITLE" -T "$TRACKNUMBER" -a "$ARTIST" -A "$ALBUM" -g "$GENRE" -y "$DATE" "$OUTF"
      done

   mkdir -p "$ARTIST"/"$ALBUM"
   mv *.mp3 "$ARTIST"/"$ALBUM"/.
   cp *.png "$ARTIST"/"$ALBUM"/.
   tar -cvf "$ARTIST - $ALBUM"-MP3.tar "$ARTIST"/"$ALBUM"/*.mp3 "$ARTIST"/"$ALBUM"/cover.png
   rm -fr "$ARTIST"
   mv *.tar /media/Multimedia/Audio
fi

if [ "$format" = "cd" ]; then
   for a in *.flac
      do

         ARTIST=`metaflac "$a" --show-tag=ARTIST | sed s/.*=//g`
         TITLE=`metaflac "$a" --show-tag=TITLE | sed s/.*=//g`
         ALBUM=`metaflac "$a" --show-tag=ALBUM | sed s/.*=//g`
         GENRE=`metaflac "$a" --show-tag=GENRE | sed s/.*=//g`
         TRACKNUMBER=`metaflac "$a" --show-tag=TRACKNUMBER | sed s/.*=//g`
         DATE=`metaflac "$a" --show-tag=DATE | sed s/.*=//g`

         flac -c -d "$a" | lame -V 4 --vbr-new - "$TRACKNUMBER"\ -\ "$TITLE".mp3
         id3v2 -t "$TITLE" -T "$TRACKNUMBER" -a "$ARTIST" -A "$ALBUM" -g "$GENRE" -y "$DATE" "$TRACKNUMBER"\ -\ "$TITLE".mp3
      done

   mkdir -p /media/Storage/Burn_To_CD/"$ARTIST"/"$ALBUM"
   mv *.mp3 /media/Storage/Burn_To_CD/"$ARTIST"/"$ALBUM"/
fi


if [ "$format" = "flac" ]; then
for a in *.flac
   do
      OUTF=`echo "$a" | sed s/"\.flac$"/"\.flac"/g`

      ARTIST=`metaflac "$a" --show-tag=ARTIST | sed s/.*=//g`
      TITLE=`metaflac "$a" --show-tag=TITLE | sed s/.*=//g`
      ALBUM=`metaflac "$a" --show-tag=ALBUM | sed s/.*=//g`
      GENRE=`metaflac "$a" --show-tag=GENRE | sed s/.*=//g`
      TRACKNUMBER=`metaflac "$a" --show-tag=TRACKNUMBER | sed s/.*=//g`
      DATE=`metaflac "$a" --show-tag=DATE | sed s/.*=//g`
   done

   mkdir -p "$ARTIST"/"$ALBUM"
   cp *.flac *.png "$ARTIST"/"$ALBUM"/.
   tar -cvf "$ARTIST - $ALBUM"-FLAC.tar "$ARTIST"/"$ALBUM"/*.flac "$ARTIST"/"$ALBUM"/cover.png
   rm -fr "$ARTIST"
   mv *.tar /media/Multimedia/Audio
fi

if [ "$format" = "wavpack" ]; then
   for a in *.flac
      do
         OUTF=`echo "$a" | sed s/"\.flac$"/"\.wv"/g`

         ARTIST=`metaflac "$a" --show-tag=ARTIST | sed s/.*=//g`
         TITLE=`metaflac "$a" --show-tag=TITLE | sed s/.*=//g`
         ALBUM=`metaflac "$a" --show-tag=ALBUM | sed s/.*=//g`
         GENRE=`metaflac "$a" --show-tag=GENRE | sed s/.*=//g`
         TRACKNUMBER=`metaflac "$a" --show-tag=TRACKNUMBER | sed s/.*=//g`
         DATE=`metaflac "$a" --show-tag=DATE | sed s/.*=//g`

         flac -c -d "$a" | wavpack -w "Artist=$ARTIST" -w "Title=$TITLE" -w "Album=$ALBUM" -w "Year=$DATE" -w "Track=$TRACK$" -w "Genre=$GENRE" -o "$OUTF" -
      done

   mkdir -p "$ARTIST"/"$ALBUM"
   mv *.wv "$ARTIST"/"$ALBUM"/.
   cp *.png "$ARTIST"/"$ALBUM"/.
   tar -cvf "$ARTIST - $ALBUM"-WV.tar "$ARTIST"/"$ALBUM"/*.wv "$ARTIST"/"$ALBUM"/cover.png
   rm -fr "$ARTIST"
   mv *.tar /media/Multimedia/Audio
fi

if [ "$format" = "musepack" ]; then
   for a in *.flac
      do
         OUTF=`echo "$a" | sed s/"\.flac$"/"\.mpc"/g`

         ARTIST=`metaflac "$a" --show-tag=ARTIST | sed s/.*=//g`
         TITLE=`metaflac "$a" --show-tag=TITLE | sed s/.*=//g`
         ALBUM=`metaflac "$a" --show-tag=ALBUM | sed s/.*=//g`
         GENRE=`metaflac "$a" --show-tag=GENRE | sed s/.*=//g`
         TRACKNUMBER=`metaflac "$a" --show-tag=TRACKNUMBER | sed s/.*=//g`
         DATE=`metaflac "$a" --show-tag=DATE | sed s/.*=//g`

         flac -c -d "$a" | mppenc --standard --ape2 --artist "$ARTIST" --title "$TITLE" --album "$ALBUM" --year "$DATE" --track "$TRACKNUMBER" --genre "$GENRE" - "$OUTF"
      done

   mkdir -p "$ARTIST"/"$ALBUM"
   mv *.mpc "$ARTIST"/"$ALBUM"/.
   cp *.png "$ARTIST"/"$ALBUM"/.
   tar -cvf "$ARTIST - $ALBUM"-MPC.tar "$ARTIST"/"$ALBUM"/*.mpc "$ARTIST"/"$ALBUM"/cover.png
   rm -fr "$ARTIST"
   mv *.tar /media/Multimedia/Audio
fi

if [ "$format" = "faac" ]; then
   for a in *.flac
      do
         OUTF=`echo "$a" | sed s/"\.flac$"/"\.m4a"/g`

         ARTIST=`metaflac "$a" --show-tag=ARTIST | sed s/.*=//g`
         TITLE=`metaflac "$a" --show-tag=TITLE | sed s/.*=//g`
         ALBUM=`metaflac "$a" --show-tag=ALBUM | sed s/.*=//g`
         GENRE=`metaflac "$a" --show-tag=GENRE | sed s/.*=//g`
         TRACKNUMBER=`metaflac "$a" --show-tag=TRACKNUMBER | sed s/.*=//g`
         DATE=`metaflac "$a" --show-tag=DATE | sed s/.*=//g`

         flac -c -d "$a" | faac -w -q 192 --artist "$ARTIST" --track "$TRACKNUMBER" --title "$TITLE" --album "$ALBUM" --year "$DATE" -o "$OUTF" -
      done

   mkdir -p "$ARTIST"/"$ALBUM"
   mv *.m4a "$ARTIST"/"$ALBUM"/.
   cp *.png "$ARTIST"/"$ALBUM"/.
   tar -cvf "$ARTIST - $ALBUM"-FAAC.tar "$ARTIST"/"$ALBUM"/*.m4a "$ARTIST"/"$ALBUM"/cover.png
   rm -fr "$ARTIST"
   mv *.tar /media/Multimedia/Audio
fi
[/SIZE]
```

---

