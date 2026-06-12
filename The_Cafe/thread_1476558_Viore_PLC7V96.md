---
title: "Viore PLC7V96"
date: 2010-05-07
forum: The Cafe
---

### Post by lank23 on 2010-05-07
Great little tv, connected to digital catv "no cable box" has a really nice clear picture.  Using the antenna does not work unless I am close to the station.  Reads JPG's and MP3's and AVI movies off my USB and SD cards just fine.  One thing is that the videos need to be in XVID format with an AVI container.  H264, DVIX, and other MPEG4 formats don't seem to work. Battery life is about 1hr 30mins watching tv.

This is the ffmpeg I used which gave me a ~90mb file from ~30mins of SD video that was captured using Mythtv and PVR-150.

```

ffmpeg -i "FILENAME.mpg" -vcodec mpeg4 -vtag xvid -b 300k -s vga -acodec libmp3lame -ab 128k -metadata title="FILENAME" -f avi "NEW-FILENAME.avi"

```

or you can use this modified script from [here]("http://www.mythtv.org/wiki/Transcoding_into_a_3gp_Video") as a job in mythtv

```

#!/bin/sh
VIDEOIN=$1
FILENAME=$2
OUTDIR=$3
# Sanity checking, to make sure everything is in order.
if [ -z "$VIDEOIN" -o -z "$FILENAME.avi" ]; then
        echo "Usage: $0 <PathToVideoFileName> <OutFile> <OutDirectory>"
        exit 5
fi
if [ ! -f "$VIDEOIN" ]; then
        echo "File does not exist: $VIDEOIN"
        exit 6
fi
# The meat of the script. Flag commercials, copy the flagged commercials to
# the cutlist, and transcode the video to remove the commercials from the file.
# Creating cutlist
mythcommflag --gencutlist -f $VIDEOIN
ERROR=$?
if [ $ERROR -ne 0 ]; then
        echo "Copying cutlist failed for ${FILENAME} with error $ERROR"
        exit $ERROR
fi
# Exporting video minus the data in the cutlist
CUTLIST=$(mythcommflag --getcutlist -f $VIDEOIN | tail -n 1 | awk '{print $2}' | sed 's/,/ /g')
ERROR=$?
if [ $ERROR -ne 0 ]; then
        echo "Copying cutlist failed for ${FILENAME} ($VIDEOIN) with error $ERROR"
        exit $ERROR
fi
mythtranscode -m -i $VIDEOIN --honorcutlist "$CUTLIST" --showprogress -o "$OUTDIR/$FILENAME.tmp"
ERROR=$?
if [ $ERROR -ne 0 ]; then
        echo "Transcoding failed for ${FILENAME} ($VIDEOIN) with error $ERROR"
        exit $ERROR
fi
# Removing the cutlist from recording (but leaving commercial flags)
mythcommflag --clearcutlist -f $VIDEOIN
ERROR=$?
if [ $ERROR -ne 0 ]; then
        echo "Could not clear cutlist. Aborted with error $ERROR"
        exit $ERROR
fi
# Now we'll convert the new temp file to xvid avi using ffmpeg

/usr/bin/ffmpeg -i "$OUTDIR/$FILENAME.tmp" -vcodec mpeg4 -vtag xvid -b 300k -s vga -acodec libmp3lame -ab 128k -metadata title="$FILENAME" -f avi "$OUTDIR/$FILENAME.avi"

ERROR=$?
if [ $ERROR -ne 0 ]; then
        echo "Could not covert file to xvid avi. Aborted with error $ERROR"
fi
# Now, regardless of an ffmpeg error we'll remove the temp file
rm -f "$OUTDIR/$FILENAME.tmp"
rm -f "$OUTDIR/$FILENAME.tmp.map"

``` 

lank23

---

