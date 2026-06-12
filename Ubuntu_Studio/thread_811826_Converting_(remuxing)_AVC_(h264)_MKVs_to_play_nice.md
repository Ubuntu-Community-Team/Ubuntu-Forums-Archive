---
title: "Converting (remuxing) AVC (h264) MKVs to play nicely on a Playstation3"
date: 2008-05-29
forum: Ubuntu Studio
---

### Post by truant on 2008-05-29
Over the past few months, I've tried many, many different people's scripts/instructions to remux HD video in Matroska containers (.mkv) into a form that the PS3 can play.  Most of them work, but none of them are quite easy/friendly enough for me to want to give to my linux-newbie friends.

So, I've knocked up a reasonably friendly script to remux Matroska/AVC video into an mp4 file.  It works with just about every source I've tried it with.  It attempts to find the real values for things like stream location, frame rate and audio type, but there are dialogs displayed for each so the user can make sure or change if they know better.  Just accepting the default values is usually pretty safe.

Because this script remuxes the video rather than re-encodes it, it's very quick, even on slower machines.  Bear in mind audio is mixed down to stereo 'cos I don't have an HD sound setup, but if you do, just remove '-ac 2' from the ffmpeg command towards the bottom.  You'll probably want to increase the audio bitrate (-ab 256k) at the same time - my TV speakers can't outperform 256Kb audio.  :)

You will need roughly twice the source file's size of disk space free, half of it temporarily.

**In addition to standard packages like python, you will require: mkvtoolnix, ffmpeg, mplayer, gpac**

You will probably need to compile your own ffmpeg, making sure you include AAC/AC3 audio support.  Fortunately, there are plenty of howtos for that out there.  All other packages are stock hardy versions.

Also, if anyone wants to make this script better, it's GPL so help yourself.  It's not exactly error-friendly, for example. :)


Copy the below into a new file, make that file executable*, then either run the file or use Nautilus Actions to set it up as a shell extension.  Remember to use '%M' as a parameter in Nautilus Actions so the script knows which file you're running it on.

* Right-click the file, Properties, Permissions, then tick "Allow executing file as program" and press 'Close'

```
#!/bin/bash

## remuxerator to remux AVC video into PS3-friendly form
# requires: mkvtoolnix (mkvmerge, mkvextract), ffmpeg, mplayer, gpac (MP4Box), zenity

#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.

#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU General Public License for more details.

#   You should have received a copy of the GNU General Public License
#   along with this program.  If not, see <http://www.gnu.org/licenses/>.


# let's have some progress meters.  there's no kill like overkill.
DisplayProgress () {
	inputlength=`mplayer -identify -frames 0 -vc null -vo null -ao null \
               "$INPUT_F" 2>/dev/null | grep ^ID_LENGTH | sed -e 's/^.*=//' -e 's/[.].*//'`
    (
      while ps | grep "$pid " >/dev/null
      do
        secondsCompleted=`tail -c 90 "/tmp/ffmpegalog.log" | awk -F"time=" {'print $2'} | cut -d"." -f 1`
        [ -n "$secondsCompleted" ] || secondsCompleted=0
        percentage=$((100*$secondsCompleted/$inputlength))
        echo "$percentage"
        sleep 1
      done
      echo 100
    ) | zenity --progress --title="Re-encoding audio - ${inputlength}s" \
               --text="" --auto-close --auto-kill --width=500
}

DemuxProgress () {
    (
      while ps | grep "$pid " >/dev/null
      do
	perCentCompleted=`tail -c 90 "/tmp/mkvx.log" | sed 's/.*gress://g' | sed 's/\%//'`
	echo $perCentCompleted
        sleep 0.1
      done
      echo 100
    )  | zenity --progress --title="Demuxing A/V streams" --text="" --auto-close --auto-kill --width=500

}

# filezpls
args=("$@")
if [ -z ${args[0]} ]; then
	INPUT_F=`zenity --file-selection --title="Choose some AVC video to remux"`
else
	INPUT_F=${args[0]}
fi
OUTPUT_F="${INPUT_F}.remuxed.mp4"

# fps pls - this has to be bang-on perfect otherwise a/v will desync.
FPS=`mplayer -identify -frames 0 -vc null -vo null -ao null \
               "$INPUT_F" 2>/dev/null | grep ^ID_VIDEO_FPS | sed -e 's/^.*=//'`
FRAME_RATE=`zenity --entry --text="Choose a frame rate in fps" --entry-text="${FPS}" --title="eff pee ess"`


## remux chain
# and, for a million extra points, add PROPER subtitle support.

# identify A/V streams
STRM_INFO=`mkvmerge -i "$INPUT_F"`
STREAMS=`echo $STRM_INFO | sed 's/File.*ska//' | sed 's/Track ID //g'  | sed 's/(V.*AVC)//'`
V_STREAM=`echo $STREAMS| sed 's/.: audio (.*)//' | sed 's/: video//' | sed 's/^[ \t]*//;s/[ \t]*$//'`
A_INFO=`echo $STREAMS| sed 's/.: video //' | sed 's/: audio//' | sed 's/^[ \t]*//;s/[ \t]*$//'`
A_STREAM=`echo $A_INFO | sed 's/.(.*//' | sed 's/^[ \t]*//;s/[ \t]*$//'`
A_TYPE=`echo $A_INFO | sed 's/^..(A_//' | sed 's/).*//' | awk '{print tolower($1)}' | sed 's/^[ \t]*//;s/[ \t]*$//'`


# show STRM_INFO in a zenity box? "Please select video stream" 
# worth keeping to make sure the above sedwork works
V_STREAM=`zenity --entry --text="${STRM_INFO} 

Please enter which stream number is video" --entry-text="${V_STREAM}" --title="V_STREAM"`

A_STREAM=`zenity --entry --text="${STRM_INFO} 

Please enter which stream number is audio" --entry-text="${A_STREAM}" --title="A_STREAM"`

A_EXT=`zenity --entry --text="${STRM_INFO} 

Please enter audio type file extension (ac3/aac)" --entry-text="${A_TYPE}" --title="A_TYPE"`

zenity --question --text="Press OK to start remuxing, or cancel to stop now." --title="Ready to go"
if [ $? != 0 ]; then
	exit
fi

# extract A/V streams
mkvextract tracks "${INPUT_F}" "${V_STREAM}:${INPUT_F}.tmp.video.h264" "${A_STREAM}:${INPUT_F}.tmp.audio.${A_EXT}" > /tmp/mkvx.log &
pid=$!
DemuxProgress

# convert audio to AAC, downmix to stereo (src usually 5.1)
ffmpeg -i "${INPUT_F}.tmp.audio.${A_EXT}" -acodec libfaac -ac 2 -ab 256k -threads 4 "${INPUT_F}.tmp.audio_final.aac" 2>> /tmp/ffmpegalog.log &
pid=$!
DisplayProgress
zenity --info --text="Audio conversion complete - preparing to mux" &

# change apparent h264 level to 4.1
# replace first "64 00 xx" with "64 00 29" in video file, to fool the PS3.
# mmmm, DIRRTY.
PYPROG="import re; bf = file('${INPUT_F}.tmp.video.h264', \"r+\"); nh = re.sub(\"\x64\x00[\x00-\x99]\", \"\x64\x00\x29\", bf.read(1024)); bf.seek(0); bf.write(nh);"
python -c "${PYPROG}"

# remux into MP4
MP4Box -add "${INPUT_F}.tmp.video.h264" -add "${INPUT_F}.tmp.audio_final.aac" -fps $FPS "$OUTPUT_F"

# tidy up
rm "${INPUT_F}.tmp.video.h264"
rm "${INPUT_F}.tmp.audio.${A_EXT}"
rm "${INPUT_F}.tmp.audio_final.aac"
rm /tmp/ffmpegalog.log
rm /tmp/mkvx.log

# let the user know
zenity --info --text="Remuxing complete"
```

---

### Post by fuzzmo on 2008-06-01
Hi,

many thanks for this except it doesn't seem to work for me - the remuxed file isn't completed and I get these following messages:

Import results: 62870 samples - Slices: 650 I 43115 P 19105 B - 1 SEI - 637 IDR
	Stream uses B-slice references - max frame delay 2
Opening file /home/farvesh/downloads/complete/Battlestar Galactica (2003) - 4x08 - Sine Qua Non/battlestar.galactica.s04e08.720p.hdtv.x264-bia.mkv.tmp.audio_final.aac failed
Error importing /home/farvesh/downloads/complete/Battlestar Galactica (2003) - 4x08 - Sine Qua Non/battlestar.galactica.s04e08.720p.hdtv.x264-bia.mkv.tmp.audio_final.aac: Requested URL is not valid or cannot be found
rm: cannot remove `/home/farvesh/downloads/complete/Battlestar Galactica (2003) - 4x08 - Sine Qua Non/battlestar.galactica.s04e08.720p.hdtv.x264-bia.mkv.tmp.audio_final.aac': No such file or directory

I can see the Temp files being created but for some reason it doesn't create the .mp4 file.  Any suggestions?

---

### Post by truant on 2008-06-02
Hmmm.  Not sure.  told you it wasn't very error-friendly..  :)

does the audio_final file actually exist?

I successfully used this script on the same bsg episode (eg, BiA's rip) as you did, just last week.

---

### Post by fuzzmo on 2008-06-05
Ah right I think I know what the problem is - it creates the *.tmp.ac3 file but doesn't transcode it into *.tmp.audio_final.aac hence where it is failing - I take it I need a compiled version of FFMPEG.... I got my codecs from medibuntu....

---

### Post by truant on 2008-06-05
that sounds about right.

I'm afraid I can't tell you whether the mediabuntu version of ffmpeg has aac support or not (although if you do "ffmpeg -formats|grep aac", you should be able to tell).  Libfaac is what you're looking for.

I compiled my own ffmpeg, always have done.  I need stuff like libamr and 100% up-to-date mp4 support (not related to this, more for Flash video).  Have a go, there's loads of ffmpeg-compiling-howtos out there.

Here's my ./configure command for ffmpeg, in case it's useful:

```
./configure --enable-shared --enable-gpl --enable-libvorbis --enable-liba52 --enable-libgsm --disable-debug --enable-libmp3lame --enable-libfaad --enable-libfaac --enable-pthreads --enable-libx264 --enable-libamr-wb --enable-libamr-nb --enable-libxvid --enable-libtheora --enable-nonfree --enable-postproc
```

---

### Post by fuzzmo on 2008-06-05
Ahhh finally sorted it out - uninstalled the medibuntu ffmpeg and installed ffmpeg from this tutorial: [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

Works like a charm now - worked fine on my ps3 - many thanks Truant!

---

### Post by truant on 2008-06-05
woop!  I made a thing that was useful to someone!

that's made my day, that has.  may even warrant a stupid smiley: :guitar:

---

### Post by fuzzmo on 2008-06-05
Lol!  Go ahead dude - you deserve it!  :)

---

### Post by kingcharles1666 on 2008-06-26
Many thanks for the script, works perfect!

---

### Post by oisuxx on 2008-07-27
thanks for this script! only problem is now i cant find the file it spits out :\

where is the remuxed file at?
it should be in .h264 correct?

---

### Post by oisuxx on 2008-07-28
so i got a mp4 file but my ps3 wont recognize it when i stream or burn it to a disk.....can anyone help please?

---

### Post by kingcharles1666 on 2008-07-28
the file format is .mp4 not .h264

---

### Post by oisuxx on 2008-07-29
this thing spit out an mp4 file. it wont stream at all.

---

### Post by truant on 2008-09-08
Stream with what?  Works fine for me, I'm using mediatomb, straight out of  Hardy, no special setup (apart from uncommenting the line in config.xml that makes it work with the PS3)

---

### Post by comradburk on 2008-09-15
Script works great on my computer, but I was wondering what all would be required to make it CLI capable.  I'm kinda new at shell scripting and I'm not sure what all I'd have to take out to get rid of the dialog boxes and just make it use the default values.  Thanks!

---

### Post by truant on 2008-09-15
Shouldn't be too hard.  I didn't know how to do much bash at all when I started doing this, and I did it all as CLI (complete with menu options etc) at first.  If you pass it a path when you run it, it'll use that file.  It's just the whole selecting which stream is which bit that needs the gui bits.

If I'd been less lazy, I wouldn't have just used zenity everywhere, I'd have made it a bit more portable so it could work in other graphical environments like KDE, and on the command line too.  But I'm lazy, sorry. :)

Here's a non-gui version, it doesn't take any input other than a path to the mkv file.  It doesn't ask you to confirm which stream is which or anything like that, so it may fail (and not tell you about it) if it gets it wrong.  I've seen it get the streams mixed up when you have multiple audio tracks, or lots of subtitles or something.  It'd be a nice little learning project, scripting that user input.

The variables you want to check are $V_STREAM, $A_STREAM and $A_EXT (which is at some points, for some reason I can't remember but I'm sure was sensible at the time, called $A_TYPE).  The information about the MKV file is in $STRM_INFO.

usage:

remuxerator /path/to/file.mkv

You could use xargs to pass it a whole stack of files to do batch processing, if you wanted.

Note: I haven't tested this version, at all.  But there's no reason it shouldn't work as it is.. Hope it helps.

```
#!/bin/bash

## remuxerator to remux AVC video into PS3-friendly form (CLI version, no human checking on stream-info, may be unreliable)
# requires: mkvtoolnix (mkvmerge, mkvextract), ffmpeg, mplayer, gpac (MP4Box)

#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.

#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU General Public License for more details.

#   You should have received a copy of the GNU General Public License
#   along with this program.  If not, see <http://www.gnu.org/licenses/>.

## filezpls
args=("$@")
if [ -z ${args[0]} ]; then
	echo "File not found, exiting...\n"
	exit;
else
	INPUT_F=${args[0]}
fi
OUTPUT_F="${INPUT_F}.remuxed.mp4"

# fps pls - this has to be bang-on perfect otherwise a/v will desync.
FPS=`mplayer -identify -frames 0 -vc null -vo null -ao null \
               "$INPUT_F" 2>/dev/null | grep ^ID_VIDEO_FPS | sed -e 's/^.*=//'`

## remux chain

# identify A/V streams
STRM_INFO=`mkvmerge -i "$INPUT_F"`
STREAMS=`echo $STRM_INFO | sed 's/File.*ska//' | sed 's/Track ID //g'  | sed 's/(V.*AVC)//'`
V_STREAM=`echo $STREAMS| sed 's/.: audio (.*)//' | sed 's/: video//' | sed 's/^[ \t]*//;s/[ \t]*$//'`
A_INFO=`echo $STREAMS| sed 's/.: video //' | sed 's/: audio//' | sed 's/^[ \t]*//;s/[ \t]*$//'`
A_STREAM=`echo $A_INFO | sed 's/.(.*//' | sed 's/^[ \t]*//;s/[ \t]*$//'`
A_TYPE=`echo $A_INFO | sed 's/^..(A_//' | sed 's/).*//' | awk '{print tolower($1)}' | sed 's/^[ \t]*//;s/[ \t]*$//'`
A_EXT=$A_TYPE

# extract A/V streams
mkvextract tracks "${INPUT_F}" "${V_STREAM}:${INPUT_F}.tmp.video.h264" "${A_STREAM}:${INPUT_F}.tmp.audio.${A_EXT}" > /tmp/mkvx.log &

# convert audio to AAC, downmix to stereo (src usually 5.1)
ffmpeg -i "${INPUT_F}.tmp.audio.${A_EXT}" -acodec libfaac -ac 2 -ab 256k -threads 4 "${INPUT_F}.tmp.audio_final.aac" 2>> /tmp/ffmpegalog.log &

# change apparent h264 level to 4.1
# replace first "64 00 xx" with "64 00 29" in video file, to fool the PS3.
# mmmm, DIRRTY.
PYPROG="import re; bf = file('${INPUT_F}.tmp.video.h264', \"r+\"); nh = re.sub(\"\x64\x00[\x00-\x99]\", \"\x64\x00\x29\", bf.read(1024)); bf.seek(0); bf.write(nh);"
python -c "${PYPROG}"

# remux into MP4
MP4Box -add "${INPUT_F}.tmp.video.h264" -add "${INPUT_F}.tmp.audio_final.aac" -fps $FPS "$OUTPUT_F"

# tidy up
rm "${INPUT_F}.tmp.video.h264"
rm "${INPUT_F}.tmp.audio.${A_EXT}"
rm "${INPUT_F}.tmp.audio_final.aac"
rm /tmp/ffmpegalog.log
rm /tmp/mkvx.log

echo "\nDONE\n";
```

---

### Post by comradburk on 2008-09-15
Awesome, thanks! I'll fool around with this script some, and if it gives me any problems I'll try and get the CLI input working!  Thanks again!

---

### Post by BurningFury on 2008-09-28
This is great stuff.
However, can you add options to mux subtitles?
Most of the MKVs I have are Animes encoded in HD, and they contain
a_s_s subs. So I wonder if there could be an option to mux those into the
video, hard-coded that is.

It would be nice if we could choose the output folder.
I don't know where the files go after they are remuxed.

So far so good. Thanks for the script.

---

### Post by truant on 2008-09-29
As it goes, the MP4 container does have soft subtitle capability, like Matroska et al, but the PS3 don't like 'em (well, I've never managed to get anything I've made to work).  Plus you'll have to convert from ***[1] to TTXT or SRT to use with MP4Box, and that ain't too much fun.  I doubt it would be as automatable as this script - as far as I know, there's nothing on Linux that can convert ***/SSA subs at all, let alone on the command line.

Hard subs - in theory they're easy enough, just takes ages to do 'cos the video stream will need transcoding not remuxing.  Use a recent build of AVIDemux to re-encode the video with hardsubs and you should be fine.  Subtitles are a video filter in AVIDemux, iirc.  This is far from an ideal solution, I'm well aware.  If Sony would only give us a Matroska demuxer in the PS3 itself, this problem wouldn't exist!  Damn you Sony, damn you...

Something that might be useful if you have a lot of DivXs with soft subtitle files (srt, sub, etc) is AVIAddXSub (google it).  Little, free, windows app that runs happily under WINE to add soft-subs to DivX files in mere minutes.  You can then turn them on using 'Subtitle options' during playback on the PS3.

The output file goes into the input folder, with ".remuxed.mp4" added on to the end of the original file name.  Feel free to add a file-output-chooser onto the script, if you want one - shouldn't be too hard.  :)



[1] this forum's word filter won't let me type the correct file extension for an Advanced SubStation Alpha Subtitle file.  A.S.S.

---

### Post by fuzzmo on 2008-11-26
This was working for me in Hardy but now in intrepid there seems to be an issue - when trying to remux the video and audio together mp4bpx seems to crash:

AVC-H264 import - frame size 1280 x 720 at 23.976 FPS
Import results: 57545 samples - Slices: 608 I 36726 P 20211 B - 1 SEI - 589 IDR
	Stream uses B-slice references - max frame delay 2
AAC import - sample rate 48000 - MPEG-4 audio - 2 channels
*** buffer overflow detected ***: MP4Box terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7c06558]
/lib/tls/i686/cmov/libc.so.6[0xb7c04680]
/lib/tls/i686/cmov/libc.so.6(__strcpy_chk+0x44)[0xb7c03944]
MP4Box[0x804f58d]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7b22685]
MP4Box[0x804cea1]
======= Memory map: ========
08048000-0806f000 r-xp 00000000 08:02 927966     /usr/bin/MP4Box
0806f000-08071000 r--p 00026000 08:02 927966     /usr/bin/MP4Box
08071000-08072000 rw-p 00028000 08:02 927966     /usr/bin/MP4Box
09891000-0a236000 rw-p 09891000 00:00 0          [heap]
b7936000-b7937000 rw-p b7936000 00:00 0 
b7937000-b7939000 r-xp 00000000 08:02 1445345    /lib/tls/i686/cmov/libdl-2.8.90.so
b7939000-b793a000 r--p 00001000 08:02 1445345    /lib/tls/i686/cmov/libdl-2.8.90.so
b793a000-b793b000 rw-p 00002000 08:02 1445345    /lib/tls/i686/cmov/libdl-2.8.90.so
b793b000-b793c000 rw-p b793b000 00:00 0 
b793c000-b7951000 r-xp 00000000 08:02 1445365    /lib/tls/i686/cmov/libpthread-2.8.90.so
b7951000-b7952000 r--p 00014000 08:02 1445365    /lib/tls/i686/cmov/libpthread-2.8.90.so
b7952000-b7953000 rw-p 00015000 08:02 1445365    /lib/tls/i686/cmov/libpthread-2.8.90.so
b7953000-b7955000 rw-p b7953000 00:00 0 
b7955000-b7a87000 r-xp 00000000 08:02 997131     /usr/lib/i686/cmov/libcrypto.so.0.9.8
b7a87000-b7a8f000 r--p 00132000 08:02 997131     /usr/lib/i686/cmov/libcrypto.so.0.9.8
b7a8f000-b7a9c000 rw-p 0013a000 08:02 997131     /usr/lib/i686/cmov/libcrypto.so.0.9.8
b7a9c000-b7aa0000 rw-p b7a9c000 00:00 0 
b7aa0000-b7ae2000 r-xp 00000000 08:02 997134     /usr/lib/i686/cmov/libssl.so.0.9.8
b7ae2000-b7ae3000 r--p 00041000 08:02 997134     /usr/lib/i686/cmov/libssl.so.0.9.8
b7ae3000-b7ae6000 rw-p 00042000 08:02 997134     /usr/lib/i686/cmov/libssl.so.0.9.8
b7ae6000-b7b0a000 r-xp 00000000 08:02 1445347    /lib/tls/i686/cmov/libm-2.8.90.so
b7b0a000-b7b0b000 r--p 00023000 08:02 1445347    /lib/tls/i686/cmov/libm-2.8.90.so
b7b0b000-b7b0c000 rw-p 00024000 08:02 1445347    /lib/tls/i686/cmov/libm-2.8.90.so
b7b0c000-b7c64000 r-xp 00000000 08:02 1445339    /lib/tls/i686/cmov/libc-2.8.90.so
b7c64000-b7c66000 r--p 00158000 08:02 1445339    /lib/tls/i686/cmov/libc-2.8.90.so
b7c66000-b7c67000 rw-p 0015a000 08:02 1445339    /lib/tls/i686/cmov/libc-2.8.90.so
b7c67000-b7c6b000 rw-p b7c67000 00:00 0 
b7c6b000-b7c7f000 r-xp 00000000 08:02 927508     /usr/lib/libz.so.1.2.3.3
b7c7f000-b7c81000 rw-p 00013000 08:02 927508     /usr/lib/libz.so.1.2.3.3
b7c81000-b7efb000 r-xp 00000000 08:02 927965     /usr/lib/libgpac-0.4.4.so
b7efb000-b7efc000 r--p 0027a000 08:02 927965     /usr/lib/libgpac-0.4.4.so
b7efc000-b7f00000 rw-p 0027b000 08:02 927965     /usr/lib/libgpac-0.4.4.so
b7f00000-b7f02000 rw-p b7f00000 00:00 0 
b7f0b000-b7f18000 r-xp 00000000 08:02 1428064    /lib/libgcc_s.so.1
b7f18000-b7f19000 r--p 0000c000 08:02 1428064    /lib/libgcc_s.so.1
b7f19000-b7f1a000 rw-p 0000d000 08:02 1428064    /lib/libgcc_s.so.1
b7f1a000-b7f1b000 rw-p b7f1a000 00:00 0 
b7f1c000-b7f1f000 rw-p b7f1c000 00:00 0 
b7f1f000-b7f39000 r-xp 00000000 08:02 1428019    /lib/ld-2.8.90.so
b7f39000-b7f3a000 r-xp b7f39000 00:00 0          [vdso]
b7f3a000-b7f3b000 r--p 0001a000 08:02 1428019    /lib/ld-2.8.90.so
b7f3b000-b7f3c000 rw-p 0001b000 08:02 1428019    /lib/ld-2.8.90.so
bfb04000-bfb3c000 rw-p bffc8000 00:00 0          [stack]
./ps32mkv: line 115: 28677 Aborted                 MP4Box -add "${INPUT_F}.tmp.video.h264" -add "${INPUT_F}.tmp.audio_final.aac" -fps $FPS "$OUTPUT_F"


Any ideas anybody as to why this might be happening?

---

### Post by fuzzmo on 2008-11-26
Ahh OK it appears the gpac in intrepid breaks mp4box.  

More info here: [https://bugs.launchpad.net/ubuntu/+source/gpac/+bug/273075](https://bugs.launchpad.net/ubuntu/+source/gpac/+bug/273075)

I am using mp4creator for now (install mpeg4ip-server package from synaptic).  Here is the slightly modified script to cater for mp4creator - seems to work ok....

#!/bin/bash

## remuxerator to remux AVC video into PS3-friendly form
# requires: mkvtoolnix (mkvmerge, mkvextract), ffmpeg, mplayer, gpac (MP4Box), zenity

#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.

#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU General Public License for more details.

#   You should have received a copy of the GNU General Public License
#   along with this program.  If not, see <http://www.gnu.org/licenses/>.


# let's have some progress meters.  there's no kill like overkill.
DisplayProgress () {
	inputlength=`mplayer -identify -frames 0 -vc null -vo null -ao null \
               "$INPUT_F" 2>/dev/null | grep ^ID_LENGTH | sed -e 's/^.*=//' -e 's/[.].*//'`
    (
      while ps | grep "$pid " >/dev/null
      do
        secondsCompleted=`tail -c 90 "/tmp/ffmpegalog.log" | awk -F"time=" {'print $2'} | cut -d"." -f 1`
        [ -n "$secondsCompleted" ] || secondsCompleted=0
        percentage=$((100*$secondsCompleted/$inputlength))
        echo "$percentage"
        sleep 1
      done
      echo 100
    ) | zenity --progress --title="Re-encoding audio - ${inputlength}s" \
               --text="" --auto-close --auto-kill --width=500
}

DemuxProgress () {
    (
      while ps | grep "$pid " >/dev/null
      do
	perCentCompleted=`tail -c 90 "/tmp/mkvx.log" | sed 's/.*gress://g' | sed 's/\%//'`
	echo $perCentCompleted
        sleep 0.1
      done
      echo 100
    )  | zenity --progress --title="Demuxing A/V streams" --text="" --auto-close --auto-kill --width=500

}

# filezpls
args=("$@")
if [ -z ${args[0]} ]; then
	INPUT_F=`zenity --file-selection --title="Choose some AVC video to remux"`
else
	INPUT_F=${args[0]}
fi
OUTPUT_F="${INPUT_F}.remuxed.mp4"

# fps pls - this has to be bang-on perfect otherwise a/v will desync.
FPS=`mplayer -identify -frames 0 -vc null -vo null -ao null \
               "$INPUT_F" 2>/dev/null | grep ^ID_VIDEO_FPS | sed -e 's/^.*=//'`
FRAME_RATE=`zenity --entry --text="Choose a frame rate in fps" --entry-text="${FPS}" --title="eff pee ess"`


## remux chain
# and, for a million extra points, add PROPER subtitle support.

# identify A/V streams
STRM_INFO=`mkvmerge -i "$INPUT_F"`
STREAMS=`echo $STRM_INFO | sed 's/File.*ska//' | sed 's/Track ID //g'  | sed 's/(V.*AVC)//'`
V_STREAM=`echo $STREAMS| sed 's/.: audio (.*)//' | sed 's/: video//' | sed 's/^[ \t]*//;s/[ \t]*$//'`
A_INFO=`echo $STREAMS| sed 's/.: video //' | sed 's/: audio//' | sed 's/^[ \t]*//;s/[ \t]*$//'`
A_STREAM=`echo $A_INFO | sed 's/.(.*//' | sed 's/^[ \t]*//;s/[ \t]*$//'`
A_TYPE=`echo $A_INFO | sed 's/^..(A_//' | sed 's/).*//' | awk '{print tolower($1)}' | sed 's/^[ \t]*//;s/[ \t]*$//'`


# show STRM_INFO in a zenity box? "Please select video stream" 
# worth keeping to make sure the above sedwork works
V_STREAM=`zenity --entry --text="${STRM_INFO} 

Please enter which stream number is video" --entry-text="${V_STREAM}" --title="V_STREAM"`

A_STREAM=`zenity --entry --text="${STRM_INFO} 

Please enter which stream number is audio" --entry-text="${A_STREAM}" --title="A_STREAM"`

A_EXT=`zenity --entry --text="${STRM_INFO} 

Please enter audio type file extension (ac3/aac)" --entry-text="${A_TYPE}" --title="A_TYPE"`

zenity --question --text="Press OK to start remuxing, or cancel to stop now." --title="Ready to go"
if [ $? != 0 ]; then
	exit
fi

# extract A/V streams
mkvextract tracks "${INPUT_F}" "${V_STREAM}:${INPUT_F}.tmp.video.h264" "${A_STREAM}:${INPUT_F}.tmp.audio.${A_EXT}" > /tmp/mkvx.log &
pid=$!
DemuxProgress

# convert audio to AAC, downmix to stereo (src usually 5.1)
ffmpeg -i "${INPUT_F}.tmp.audio.${A_EXT}" -acodec libfaac -ac 2 -ab 256k -threads 4 "${INPUT_F}.tmp.audio_final.aac" 2>> /tmp/ffmpegalog.log &
pid=$!
DisplayProgress
zenity --info --text="Audio conversion complete - preparing to mux" &

# change apparent h264 level to 4.1
# replace first "64 00 xx" with "64 00 29" in video file, to fool the PS3.
# mmmm, DIRRTY.
PYPROG="import re; bf = file('${INPUT_F}.tmp.video.h264', \"r+\"); nh = re.sub(\"\x64\x00[\x00-\x99]\", \"\x64\x00\x29\", bf.read(1024)); bf.seek(0); bf.write(nh);"
python -c "${PYPROG}"

# remux into MP4
mp4creator --create="${INPUT_F}.tmp.video.h264" -r $FPS "${INPUT_F}.mp4"
mp4creator --create="${INPUT_F}.tmp.audio_final.aac" "${INPUT_F}.mp4"

# tidy up
rm "${INPUT_F}.tmp.video.h264"
rm "${INPUT_F}.tmp.audio.${A_EXT}"
rm "${INPUT_F}.tmp.audio_final.aac"
rm /tmp/ffmpegalog.log
rm /tmp/mkvx.log

# let the user know
zenity --info --text="Remuxing complete"

---

### Post by fuzzmo on 2008-11-26
Further to this the original script will work on intrepid if you use the Hardy version of gpac and the associated libgpac....

---

### Post by truant on 2008-11-27
Oh, nice timing.  The "thread updated" email was the first one I read after upgrading to Intrepid, today.  :)

Weirdly, gpac still works for me, but I've been meaning to do some work on this script recently anyway, so I might rework it a bit with mp4creator anyway - the launchpad page suggest it's a bit quicker to run, and I never liked gpac all that much to start with (who uses capital letters in their binary names anyway!)

---

### Post by truant on 2008-11-27
oh-ho-ho-ho.

mp4creator looks well nice.  it has a -mpeg4-video-profile option, which might mean not having to use that dirty python hack to change the level.  although that hack has worked for a long time, which suggests it does at least work.  working code is always nice.

I'm going to have a bit of a tinker about with this, will post up new stuff as and when I have something nice for y'all.

---

### Post by truant on 2008-11-30
OK, here's an updated version that uses mp4creator.  I've also streamlined it a bit, so you can just click one button to attempt to remux without checking to make sure it's got all the stream id's correct.

However, there does appear to be a small bug in zenity now (that's the app that draws the dialog boxes), where it's creating them behind all the other windows.  Apply the patch here: [https://bugs.launchpad.net/ubuntu/+source/zenity/+bug/272083](https://bugs.launchpad.net/ubuntu/+source/zenity/+bug/272083) for a fix for that.

```
#!/bin/bash

## remuxerator to remux AVC video into PS3-friendly form
# requires: mkvmerge, mkvextract (in package mkvtoolnix), ffmpeg (with h264/aac support compiled in), 
#           mplayer, mp4creator (in package mpeg4ip-server), zenity

#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.

#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU General Public License for more details.

#   You should have received a copy of the GNU General Public License
#   along with this program.  If not, see <http://www.gnu.org/licenses/>.


# let's have some progress meters.  there's no kill like overkill.
AudioProgress () {
	inputlength=`mplayer -identify -frames 0 -vc null -vo null -ao null \
 "$INPUT_F" 2>/dev/null | grep ^ID_LENGTH | sed -e 's/^.*=//' -e 's/[.].*//'`
    (
      while ps | grep "$pid " >/dev/null
      do
        secondsCompleted=`tail -c 90 "/tmp/ffmpegalog.log" | awk -F"time=" {'print $2'} | cut -d"." -f 1`
        [ -n "$secondsCompleted" ] || secondsCompleted=0
        percentage=$((100*$secondsCompleted/$inputlength))
        echo "$percentage"
        sleep 1
      done
      echo 100
    ) | zenity --progress --title="Re-encoding audio - ${inputlength}s" --text="" --auto-close --auto-kill --width=500
}

DemuxProgress () {
    (
      while ps | grep "$pid " >/dev/null
      do
	perCentCompleted=`tail -c 90 "/tmp/mkvx.log" | sed 's/.*gress://g' | sed 's/\%//'`
	echo $perCentCompleted
        sleep 0.1
      done
      echo 100
    )  | zenity --progress --title="Demuxing A/V streams" --text="" --auto-close --auto-kill --width=500

}

# filezpls
args=("$@")
if [ -z ${args[0]} ]; then
	INPUT_F=`zenity --file-selection --title="Please choose some AVC video to remux."`
else
	INPUT_F=${args[0]}
fi
OUTPUT_F="${INPUT_F}.rmxd.mp4"


# fps - this has to be perfect otherwise a/v will desync.
FPS=`mplayer -identify -frames 0 -vc null -vo null -ao null "$INPUT_F" 2>/dev/null | grep ^ID_VIDEO_FPS | sed -e 's/^.*=//'`

## remux chain
# and, for a million extra points, add PROPER subtitle support.

# identify A/V streams
STRM_INFO=`mkvmerge -i "$INPUT_F"`
STREAMS=`echo $STRM_INFO | sed 's/File.*ska//' | sed 's/Track ID //g'  | sed 's/(V.*AVC)//'`
V_STREAM=`echo $STREAMS| sed 's/.: audio (.*)//' | sed 's/: video//' | sed 's/^[ \t]*//;s/[ \t]*$//'`
A_INFO=`echo $STREAMS| sed 's/.: video //' | sed 's/: audio//' | sed 's/^[ \t]*//;s/[ \t]*$//'`
A_STREAM=`echo $A_INFO | sed 's/.(.*//' | sed 's/^[ \t]*//;s/[ \t]*$//'`
A_TYPE=`echo $A_INFO | sed 's/^..(A_//' | sed 's/).*//' | awk '{print tolower($1)}' | sed 's/^[ \t]*//;s/[ \t]*$//'`
A_EXT=`echo $A_TYPE`

# allow fast version
zenity --question --text="Press OK to remux now using automatic settings, or cancel to verify manually." --title="Feeling lucky?"
if [ $? != 0 ]; then

	# manually check that sed has done it's magic right.
	V_STREAM=`zenity --entry --text="${STRM_INFO} 

	Please enter which stream number is video" --entry-text="${V_STREAM}" --title="V_STREAM"`

	A_STREAM=`zenity --entry --text="${STRM_INFO} 

	Please enter which stream number is audio" --entry-text="${A_STREAM}" --title="A_STREAM"`

	A_EXT=`zenity --entry --text="${STRM_INFO} 

	Please enter audio type file extension (ac3/aac/dts)" --entry-text="${A_TYPE}" --title="A_TYPE"`

	zenity --question --text="Press OK to start remuxing, or cancel to stop now." --title="Ready to go"
	if [ $? != 0 ]; then
		exit
	fi
fi

# extract A/V streams
mkvextract tracks "${INPUT_F}" "${V_STREAM}:${INPUT_F}.tmp.video.h264" "${A_STREAM}:${INPUT_F}.tmp.audio.${A_EXT}" > /tmp/mkvx.log &
pid=$!
DemuxProgress

# convert audio to AAC, downmix to stereo (src usually 5.1)
ffmpeg -i "${INPUT_F}.tmp.audio.${A_EXT}" -acodec libfaac -ac 2 -ab 256k "${INPUT_F}.tmp.audio_final.aac" 2>> /tmp/ffmpegalog.log &
pid=$!
AudioProgress

# change apparent h264 level to 4.1
# replace first "64 00 xx" with "64 00 29" in video file, to fool the PS3.
# mmmm, DIRRTY.
# it's possible that this can be removed and replace with "-mpeg4-video-profile=4.1" in the mp4creator lines below.
PYPROG="import re; bf = file('${INPUT_F}.tmp.video.h264', \"r+\"); nh = re.sub(\"\x64\x00[\x00-\x99]\", \"\x64\x00\x29\", bf.read(1024)); bf.seek(0); bf.write(nh);"
python -c "${PYPROG}"

# remux into MP4
mp4creator "${INPUT_F}.tmp.audio_final.aac" "${OUTPUT_F}"
mp4creator "${INPUT_F}.tmp.video.h264" -rate=$FPS "${OUTPUT_F}"

# tidy up
rm "${INPUT_F}.tmp.video.h264"
rm "${INPUT_F}.tmp.audio.${A_EXT}"
rm "${INPUT_F}.tmp.audio_final.aac"
rm /tmp/ffmpegalog.log
rm /tmp/mkvx.log

# let the user know
zenity --info --text="Remuxing complete"
```

---

### Post by fuzzmo on 2009-01-05
Dude you da man!  I'll try this one out with the next batch of hi def rips I get.  BTW your script came to my rescue when mkv2vob barfed on one file on my brothers new PC (Windows with loads of hi def rips downloaded on to it hence easier just to go with a windows app).  I loaded the file up in Ubuntu and then ran your script - voila! All done.  Nice work dude :)

---

### Post by joeelmex on 2009-07-05
hey guys I followed the instructions and when the file is done, I hear no audio.  I see the audio as AAC3, and the 3 options I can pick are AAC, DTS and one more.  What you think I can try to get the audio? THANKS!

I can see this error in the terminal..

```
mp4creator: can't open file /home/joeelmex/Downloads/Pink_Panther_2_Video_Preview.mkv.tmp.audio_final.aac: No such file or directory
rm: cannot remove `/home/joeelmex/Downloads/Pink_Panther_2_Video_Preview.mkv.tmp.audio_final.aac': No such file or directory

```

---

### Post by samuiyo on 2009-12-27
ante todo gracias!! truant

i was looking for a function to add progress bar to zenity and i found yours so i hope to get your permission to use it. it was funny cos i'm coding a script to do something similar. just i have not limitation of PS3 cos i'm using a hd media player. i want to choose which track to remux into an avi or mp4 container from a mkv. i'm new programing so i didn't take any care of showing any error. also i got problems about guess how many number of tracks could it have so i limit mkv tracks to 5... :(

anyhow i type this
```

#!/bin/bash

DemuxProgress () {
    (
        while ps | grep "$pid " >/dev/null
        do
        perCentCompleted=`tail -c 90 "/tmp/mkvx.log" | sed -n 's/.*: \([0-9]*\).*/\1/p'`
        echo $perCentCompleted
        sleep 0.1
        done
        echo 100
    ) | zenity --title="Demuxing A/V streams" --window-icon=mkv.png --progress --text "" --auto-close --auto-kill --width=500
}
RemuxProgress () {
    (
        while ps | grep "$pid " >/dev/null
        do
        perCentCompleted=`tail -c 90 "/tmp/mp4x.log" | sed -n 's/.*(\([0-9]*\).*/\1/p'`
        echo $perCentCompleted
        sleep 0.1
        done
        echo 100
    ) | zenity --title="Remuxing A/V streams" --window-icon=mkv.png --progress --text "" --auto-close --auto-kill --width=500
}

MKV_FILENAME=${1}
MKV_VALIDATA=`file "${MKV_FILENAME}" | grep Matroska`
if [ -z "${MKV_VALIDATA}" ]
    then
    zenity --title "MKV Converter" --window-icon=mkv.png --info --text "¡ERROR!\n`file "${MKV_FILENAME}"`\nNo es un archivo Matroska."
    exit
fi        
MKV_FILE_NAME=`echo "${MKV_FILENAME}" | sed 's/ /_/g'`
mv "${1}" "${MKV_FILE_NAME}"

# concatena todas las salidas en una linea -> sed -e :a -e '$!N;s/\n/ /;ta' -e 'P;D'`
TRACKS_NUM=`mkvmerge -i "${MKV_FILE_NAME}" | sed -n -e '/Track ID /p' | sed -n '$='`

MKV_INFO=`mktemp`
mkvinfo "${MKV_FILE_NAME}" > ${MKV_INFO}

VIDEO_WIDTH=`grep 'Pixel width' ${MKV_INFO} | sed -n -e 's/.*Pixel width: //p'`
VIDEO_HEIGHT=`grep 'Pixel height:' ${MKV_INFO} | sed -n -e 's/.*Pixel height: //p'`

for (( TRACK_CON=1; "${TRACK_CON}" <= "${TRACKS_NUM}"; TRACK_CON++ ))
do
    case ${TRACK_CON} in
    1)
    TRACK1_CHK="FALSE"
    TRACK1_ID=`grep 'Track number:' ${MKV_INFO} | sed -n -e '1 s/.*Track number: //p'`
    TRACK1_TYPE=`grep 'Track type:' ${MKV_INFO} | sed -n -e '1 s/.*Track type: //p'`
    TRACK1_CODEC=`grep 'Codec ID:' ${MKV_INFO} | sed -n -e '1 s/.*Codec ID: [VAS]_//p'`
    TRACK1_LANG=`grep 'Language:' ${MKV_INFO} | sed -n -e '1 s/.*Language: //p'`
    ;;
    2)
    TRACK2_CHK="FALSE"
    TRACK2_ID=`grep 'Track number:' ${MKV_INFO} | sed -n -e '2 s/.*Track number: //p'`
    TRACK2_TYPE=`grep 'Track type:' ${MKV_INFO} | sed -n -e '2 s/.*Track type: //p'`
    TRACK2_CODEC=`grep 'Codec ID:' ${MKV_INFO} | sed -n -e '2 s/.*Codec ID: [VAS]_//p'`
    TRACK2_LANG=`grep 'Language:' ${MKV_INFO} | sed -n -e '2 s/.*Language: //p'`
    ;;
    3)
    TRACK3_CHK="FALSE"
    TRACK3_ID=`grep 'Track number:' ${MKV_INFO} | sed -n -e '3 s/.*Track number: //p'`
    TRACK3_TYPE=`grep 'Track type:' ${MKV_INFO} | sed -n -e '3 s/.*Track type: //p'`
    TRACK3_CODEC=`grep 'Codec ID:' ${MKV_INFO} | sed -n -e '3 s/.*Codec ID: [VAS]_//p'`
    TRACK3_LANG=`grep 'Language:' ${MKV_INFO} | sed -n -e '3 s/.*Language: //p'`
    ;;
    4)
    TRACK4_CHK="FALSE"
    TRACK4_ID=`grep 'Track number:' ${MKV_INFO} | sed -n -e '4 s/.*Track number: //p'`
    TRACK4_TYPE=`grep 'Track type:' ${MKV_INFO} | sed -n -e '4 s/.*Track type: //p'`
    TRACK4_CODEC=`grep 'Codec ID:' ${MKV_INFO} | sed -n -e '4 s/.*Codec ID: [VAS]_//p'`
    TRACK4_LANG=`grep 'Language:' ${MKV_INFO} | sed -n -e '4 s/.*Language: //p'`
    ;;
    5)
    TRACK5_CHK="FALSE"
    TRACK5_ID=`grep 'Track number:' ${MKV_INFO} | sed -n -e '5 s/.*Track number: //p'`
    TRACK5_TYPE=`grep 'Track type:' ${MKV_INFO} | sed -n -e '5 s/.*Track type: //p'`
    TRACK5_CODEC=`grep 'Codec ID:' ${MKV_INFO} | sed -n -e '5 s/.*Codec ID: [VAS]_//p'`
    TRACK5_LANG=`grep 'Language:' ${MKV_INFO} | sed -n -e '5 s/.*Language: //p'`
    ;;
    *)
    msg1="¿Cuantas Pistas tiene este MKV!!!? - $TRACKS_NUM Pistas"
    ;;
    esac
done
TRACKS_CHK=`mktemp`
zenity --title "MKV Converter" --window-icon=mkv.png --list  --text "Elija las Pistas para ${MKV_FILENAME%.*}\n\n$msg1" --checklist  --column "" --column "#" --column tipo --column codec --column idioma $TRACK1_CHK $TRACK1_ID $TRACK1_TYPE $TRACK1_CODEC $TRACK1_LANG $TRACK2_CHK $TRACK2_ID $TRACK2_TYPE $TRACK2_CODEC $TRACK2_LANG $TRACK3_CHK $TRACK3_ID $TRACK3_TYPE $TRACK3_CODEC $TRACK3_LANG $TRACK4_CHK $TRACK4_ID $TRACK4_TYPE $TRACK4_CODEC $TRACK4_LANG $TRACK5_CHK $TRACK5_ID $TRACK5_TYPE $TRACK5_CODEC $TRACK5_LANG --separator "
" --width 320 --height 240 > ${TRACKS_CHK}

for (( TRACK_CON=1; `sed -n -e "$TRACK_CON"p <"${TRACKS_CHK}"`; TRACK_CON++ ))
do
    TRACK_N=`sed -n -e "$TRACK_CON"p <"${TRACKS_CHK}"`
    FPS_CON=1
    RATE_CON=1
    case ${TRACK_N} in
    1)
    if [ ${TRACK1_TYPE} = "video" ]
        then
        TRACK1_FPS=`grep 'Default duration:' ${MKV_INFO} | sed -n -e "${FPS_CON} s/.*(\([0-9]*.[0-9]*\).*/\1/p"`
        case ${TRACK1_CODEC} in
        MPEG4/ISO/AVC)
        T1_EXT="${TRACK1_ID}:${MKV_FILE_NAME%.*}.tmp.264"
        T1_MP4="-add ${MKV_FILE_NAME%.*}.tmp.264"
        ;;
        MS/VFW/FOURCC)
        T1_EXT="${TRACK1_ID}:${MKV_FILE_NAME%.*}.tmp.avi"
        T1_MP4="-add ${MKV_FILE_NAME%.*}.tmp.avi"
        ;;
        *)
        zenity --title "MKV Converter" --window-icon=mkv.png --info --text="1: ${TRACK1_CODEC} :Formato de video no soportado"
        exit
        ;;
        esac
    elif [ ${TRACK1_TYPE} = "audio" ]
        then
        TRACK1_RATE=`grep 'Sampling frequency:'  ${MKV_INFO} | sed -n -e "${RATE_CON} s/.*Sampling frequency: //p"`
        TRACK1_CHAN=`grep 'Channels:'  ${MKV_INFO} | sed -n -e "${RATE_CON} s/.*Channels: //p"`
        FPS_CON=$[${FPS_CON}+1]
        RATE_CON=$[${RATE_CON}+1]
        case ${TRACK1_CODEC} in
        DTS)
        T1_EXT="${TRACK1_ID}:${MKV_FILE_NAME%.*}.tmp.${TRACK1_LANG}.dts"
        T1_MP4="-add ${MKV_FILE_NAME%.*}.tmp.${TRACK1_LANG}.dts"
        ;;
        AAC)
        T1_EXT="${TRACK1_ID}:${MKV_FILE_NAME%.*}.tmp.${TRACK1_LANG}.aac"
        T1_MP4="-add ${MKV_FILE_NAME%.*}.tmp.${TRACK1_LANG}.aac"
        ;;
        AC3)
        T1_EXT="${TRACK1_ID}:${MKV_FILE_NAME%.*}.tmp.${TRACK1_LANG}.ac3"
        T1_MP4="-add ${MKV_FILE_NAME%.*}.tmp.${TRACK1_LANG}.ac3"
        ;;
        MPEG/L3)
        T1_EXT="${TRACK1_ID}:${MKV_FILE_NAME%.*}.tmp.${TRACK1_LANG}.mp3"
        T1_MP4="-add ${MKV_FILE_NAME%.*}.tmp.${TRACK1_LANG}.mp3"
        ;;
        VORBIS)
        T1_EXT="${TRACK1_ID}:${MKV_FILE_NAME%.*}.tmp.${TRACK1_LANG}.ogg"
        T1_MP4="-add ${MKV_FILE_NAME%.*}.tmp.${TRACK1_LANG}.ogg"
        ;;
        *)
        zenity --title "MKV Converter" --window-icon=mkv.png --info --text="1: ${TRACK1_CODEC} :Formato de audio no soportado"
        exit
        ;;
        esac
    else
        case ${TRACK1_CODEC} in
        TEXT/***)
        T1_EXT="${TRACK1_ID}:${MKV_FILE_NAME%.*}.${TRACK1_LANG}.***"
        ;;
        TEXT/UTF8)
        T1_EXT="${TRACK1_ID}:${MKV_FILE_NAME%.*}.${TRACK1_LANG}.srt"
        ;;
        *)
        T1_EXT="${TRACK1_ID}:${MKV_FILE_NAME%.*}.${TRACK1_LANG}.txt"
        ;;
        esac
    fi
    ;;
    2)
    if [ ${TRACK2_TYPE} = "video" ]
        then
        TRACK2_FPS=`grep 'Default duration:' ${MKV_INFO} | sed -n -e "${FPS_CON} s/.*(\([0-9]*.[0-9]*\).*/\1/p"`
        case ${TRACK2_CODEC} in
        MPEG4/ISO/AVC)
        T2_EXT="${TRACK2_ID}:${MKV_FILE_NAME%.*}.tmp.264"
        T2_MP4="-add ${MKV_FILE_NAME%.*}.tmp.264"
        ;;
        MS/VFW/FOURCC)
        T2_EXT="${TRACK2_ID}:${MKV_FILE_NAME%.*}.tmp.avi"
        T2_MP4="-add ${MKV_FILE_NAME%.*}.tmp.avi"
        ;;
        *)
        zenity --title "MKV Converter" --window-icon=mkv.png --info --text="2: ${TRACK2_CODEC} :Formato de video no soportado"
        exit
        ;;
        esac
    elif [ ${TRACK2_TYPE} = "audio" ]
        then
        TRACK2_RATE=`grep 'Sampling frequency:'  ${MKV_INFO} | sed -n -e "${RATE_CON} s/.*Sampling frequency: //p"`
        TRACK2_CHAN=`grep 'Channels:'  ${MKV_INFO} | sed -n -e "${RATE_CON} s/.*Channels: //p"`
        FPS_CON=$[${FPS_CON}+1]
        RATE_CON=$[${RATE_CON}+1]
        case ${TRACK2_CODEC} in
        DTS)
        T2_EXT="${TRACK2_ID}:${MKV_FILE_NAME%.*}.tmp.${TRACK2_LANG}.dts"
        T2_MP4="-add ${MKV_FILE_NAME%.*}.tmp.${TRACK2_LANG}.dts"
        ;;
        AAC)
        T2_EXT="${TRACK2_ID}:${MKV_FILE_NAME%.*}.tmp.${TRACK2_LANG}.aac"
        T2_MP4="-add ${MKV_FILE_NAME%.*}.tmp.${TRACK2_LANG}.aac"
        ;;
        AC3)
        T2_EXT="${TRACK2_ID}:${MKV_FILE_NAME%.*}.tmp.${TRACK2_LANG}.ac3"
        T2_MP4="-add ${MKV_FILE_NAME%.*}.tmp.${TRACK2_LANG}.ac3"
        ;;
        MPEG/L3)
        T2_EXT="${TRACK2_ID}:${MKV_FILE_NAME%.*}.tmp.${TRACK2_LANG}.mp3"
        T2_MP4="-add ${MKV_FILE_NAME%.*}.tmp.${TRACK2_LANG}.mp3"
        ;;
        VORBIS)
        T2_EXT="${TRACK2_ID}:${MKV_FILE_NAME%.*}.tmp.${TRACK2_LANG}.ogg"
        T2_MP4="-add ${MKV_FILE_NAME%.*}.tmp.${TRACK2_LANG}.ogg"
        ;;
        *)
        zenity --title "MKV Converter" --window-icon=mkv.png --info --text="2: ${TRACK2_CODEC} :Formato de audio no soportado"
        exit
        ;;
        esac
    else
        case ${TRACK2_CODEC} in
        TEXT/***)
        T2_EXT="${TRACK2_ID}:${MKV_FILE_NAME%.*}.${TRACK2_LANG}.***"
        ;;
        TEXT/UTF8)
        T2_EXT="${TRACK2_ID}:${MKV_FILE_NAME%.*}.${TRACK2_LANG}.srt"
        ;;
        *)
        T2_EXT="${TRACK2_ID}:${MKV_FILE_NAME%.*}.${TRACK2_LANG}.txt"
        ;;
        esac
    fi
    ;;
    3)
    if [ ${TRACK3_TYPE} = "video" ]
        then
        TRACK3_FPS=`grep 'Default duration:' ${MKV_INFO} | sed -n -e "${FPS_CON} s/.*(\([0-9]*.[0-9]*\).*/\1/p"`
        case ${TRACK3_CODEC} in
        MPEG4/ISO/AVC)
        T3_EXT="${TRACK3_ID}:${MKV_FILE_NAME%.*}.tmp.264"
        T3_MP4="-add ${MKV_FILE_NAME%.*}.tmp.264"
        ;;
        MS/VFW/FOURCC)
        T3_EXT="${TRACK3_ID}:${MKV_FILE_NAME%.*}.tmp.avi"
        T3_MP4="-add ${MKV_FILE_NAME%.*}.tmp.avi"
        ;;
        *)
        zenity --title "MKV Converter" --window-icon=mkv.png --info --text="3: ${TRACK3_CODEC} :Formato de video no soportado"
        exit
        ;;
        esac
    elif [ ${TRACK3_TYPE} = "audio" ]
        then
        TRACK3_RATE=`grep 'Sampling frequency:'  ${MKV_INFO} | sed -n -e "${RATE_CON} s/.*Sampling frequency: //p"`
        TRACK3_CHAN=`grep 'Channels:'  ${MKV_INFO} | sed -n -e "${RATE_CON} s/.*Channels: //p"`
        FPS_CON=$[${FPS_CON}+1]
        RATE_CON=$[${RATE_CON}+1]
        case ${TRACK3_CODEC} in
        DTS)
        T3_EXT="${TRACK3_ID}:${MKV_FILE_NAME%.*}.tmp.${TRACK3_LANG}.dts"
        T3_MP4="-add ${MKV_FILE_NAME%.*}.tmp.${TRACK3_LANG}.dts"
        ;;
        AAC)
        T3_EXT="${TRACK3_ID}:${MKV_FILE_NAME%.*}.tmp.${TRACK3_LANG}.aac"
        T3_MP4="-add ${MKV_FILE_NAME%.*}.tmp.${TRACK3_LANG}.aac"
        ;;
        AC3)
        T3_EXT="${TRACK3_ID}:${MKV_FILE_NAME%.*}.tmp.${TRACK3_LANG}.ac3"
        T3_MP4="-add ${MKV_FILE_NAME%.*}.tmp.${TRACK3_LANG}.ac3"
        ;;
        MPEG/L3)
        T3_EXT="${TRACK3_ID}:${MKV_FILE_NAME%.*}.tmp.${TRACK3_LANG}.mp3"
        T3_MP4="-add ${MKV_FILE_NAME%.*}.tmp.${TRACK3_LANG}.mp3"
        ;;
        VORBIS)
        T3_EXT="${TRACK3_ID}:${MKV_FILE_NAME%.*}.tmp.${TRACK3_LANG}.ogg"
        T3_MP4="-add ${MKV_FILE_NAME%.*}.tmp.${TRACK3_LANG}.ogg"
        ;;
        *)
        zenity --title "MKV Converter" --window-icon=mkv.png --info --text="3: ${TRACK3_CODEC} :Formato de audio no soportado"
        exit
        ;;
        esac
    else
        case ${TRACK3_CODEC} in
        TEXT/***)
        T3_EXT="${TRACK3_ID}:${MKV_FILE_NAME%.*}.${TRACK3_LANG}.***"
        ;;
        TEXT/UTF8)
        T3_EXT="${TRACK3_ID}:${MKV_FILE_NAME%.*}.${TRACK3_LANG}.srt"
        ;;
        *)
        T3_EXT="${TRACK3_ID}:${MKV_FILE_NAME%.*}.${TRACK3_LANG}.txt"
        ;;
        esac
    fi
    ;;
    4)
    if [ ${TRACK4_TYPE} = "video" ]
        then
        TRACK4_FPS=`grep 'Default duration:' ${MKV_INFO} | sed -n -e "${FPS_CON} s/.*(\([0-9]*.[0-9]*\).*/\1/p"`
        case ${TRACK4_CODEC} in
        MPEG4/ISO/AVC)
        T4_EXT="${TRACK4_ID}:${MKV_FILE_NAME%.*}.tmp.264"
        T4_MP4="-add ${MKV_FILE_NAME%.*}.tmp.264"
        ;;
        MS/VFW/FOURCC)
        T4_EXT="${TRACK4_ID}:${MKV_FILE_NAME%.*}.tmp.avi"
        T4_MP4="-add ${MKV_FILE_NAME%.*}.tmp.avi"
        ;;
        *)
        zenity --title "MKV Converter" --window-icon=mkv.png --info --text="4: ${TRACK4_CODEC} :Formato de video no soportado"
        exit
        ;;
        esac
    elif [ ${TRACK4_TYPE} = "audio" ]
        then
        TRACK4_RATE=`grep 'Sampling frequency:'  ${MKV_INFO} | sed -n -e "${RATE_CON} s/.*Sampling frequency: //p"`
        TRACK4_CHAN=`grep 'Channels:'  ${MKV_INFO} | sed -n -e "${RATE_CON} s/.*Channels: //p"`
        FPS_CON=$[${FPS_CON}+1]
        RATE_CON=$[${RATE_CON}+1]
        case ${TRACK4_CODEC} in
        DTS)
        T4_EXT="${TRACK4_ID}:${MKV_FILE_NAME%.*}.tmp.${TRACK4_LANG}.dts"
        T4_MP4="-add ${MKV_FILE_NAME%.*}.tmp.${TRACK_LANG}.dts"
        ;;
        AAC)
        T4_EXT="${TRACK4_ID}:${MKV_FILE_NAME%.*}.tmp.${TRACK4_LANG}.aac"
        T4_MP4="-add ${MKV_FILE_NAME%.*}.tmp.${TRACK4_LANG}.aac"
        ;;
        AC3)
        T4_EXT="${TRACK4_ID}:${MKV_FILE_NAME%.*}.tmp.${TRACK4_LANG}.ac3"
        T4_MP4="-add ${MKV_FILE_NAME%.*}.tmp.${TRACK4_LANG}.ac3"
        ;;
        MPEG/L3)
        T4_EXT="${TRACK4_ID}:${MKV_FILE_NAME%.*}.tmp.${TRACK4_LANG}.mp3"
        T4_MP4="-add ${MKV_FILE_NAME%.*}.tmp.${TRACK4_LANG}.mp3"
        ;;
        VORBIS)
        T4_EXT="${TRACK4_ID}:${MKV_FILE_NAME%.*}.tmp.${TRACK4_LANG}.ogg"
        T4_MP4="-add ${MKV_FILE_NAME%.*}.tmp.${TRACK4_LANG}.ogg"
        ;;
        *)
        zenity --title "MKV Converter" --window-icon=mkv.png --info --text="4: ${TRACK4_CODEC} :Formato de audio no soportado"
        exit
        ;;
        esac
    else
        case ${TRACK4_CODEC} in
        TEXT/***)
        T4_EXT="${TRACK4_ID}:${MKV_FILE_NAME%.*}.${TRACK4_LANG}.***"
        ;;
        TEXT/UTF8)
        T4_EXT="${TRACK4_ID}:${MKV_FILE_NAME%.*}.${TRACK4_LANG}.srt"
        ;;
        *)
        T4_EXT="${TRACK4_ID}:${MKV_FILE_NAME%.*}.${TRACK4_LANG}.txt"
        ;;
        esac
    fi
    ;;
    5)
    if [ ${TRACK5_TYPE} = "video" ]
        then
        TRACK5_FPS=`grep 'Default duration:' ${MKV_INFO} | sed -n -e "${FPS_CON} s/.*(\([0-9]*.[0-9]*\).*/\1/p"`
        case ${TRACK5_CODEC} in
        MPEG4/ISO/AVC)
        T5_EXT="${TRACK5_ID}:${MKV_FILE_NAME%.*}.tmp.264"
        T5_MP4="-add ${MKV_FILE_NAME%.*}.tmp.264"
        ;;
        MS/VFW/FOURCC)
        T5_EXT="${TRACK5_ID}:${MKV_FILE_NAME%.*}.tmp.avi"
        T5_MP4="-add ${MKV_FILE_NAME%.*}.tmp.avi"
        ;;
        *)
        zenity --title "MKV Converter" --window-icon=mkv.png --info --text="5: ${TRACK5_CODEC} :Formato de video no soportado"
        exit
        ;;
        esac
    elif [ ${TRACK5_TYPE} = "audio" ]
        then
        TRACK5_RATE=`grep 'Sampling frequency:'  ${MKV_INFO} | sed -n -e "${RATE_CON} s/.*Sampling frequency: //p"`
        TRACK5_CHAN=`grep 'Channels:'  ${MKV_INFO} | sed -n -e "${RATE_CON} s/.*Channels: //p"`
        FPS_CON=$[${FPS_CON}+1]
        RATE_CON=$[${RATE_CON}+1]
        case ${TRACK5_CODEC} in
        DTS)
        T5_EXT="${TRACK5_ID}:${MKV_FILE_NAME%.*}.tmp.${TRACK5_LANG}.dts"
        T5_MP4="-add ${MKV_FILE_NAME%.*}.tmp.${TRACK5_LANG}.dts"
        ;;
        AAC)
        T5_EXT="${TRACK5_ID}:${MKV_FILE_NAME%.*}.tmp.${TRACK5_LANG}.aac"
        T5_MP4="-add ${MKV_FILE_NAME%.*}.tmp.${TRACK5_LANG}.aac"
        ;;
        AC3)
        T5_EXT="${TRACK5_ID}:${MKV_FILE_NAME%.*}.tmp.${TRACK5_LANG}.ac3"
        T5_MP4="-add ${MKV_FILE_NAME%.*}.tmp.${TRACK5_LANG}.ac3"
        ;;
        MPEG/L3)
        T5_EXT="${TRACK5_ID}:${MKV_FILE_NAME%.*}.tmp.${TRACK5_LANG}.mp3"
        T5_MP4="-add ${MKV_FILE_NAME%.*}.tmp.${TRACK5_LANG}.mp3"
        ;;
        VORBIS)
        T5_EXT="${TRACK5_ID}:${MKV_FILE_NAME%.*}.tmp.${TRACK5_LANG}.ogg"
        T5_MP4="-add ${MKV_FILE_NAME%.*}.tmp.${TRACK5_LANG}.ogg"
        ;;
        *)
        zenity --title "MKV Converter" --window-icon=mkv.png --info --text="5: ${TRACK5_CODEC} :Formato de audio no soportado"
        exit
        ;;
        esac
    else
        case ${TRACK5_CODEC} in
        TEXT/***)
        T5_EXT="${TRACK5_ID}:${MKV_FILE_NAME%.*}.${TRACK5_LANG}.***"
        ;;
        TEXT/UTF8)
        T5_EXT="${TRACK5_ID}:${MKV_FILE_NAME%.*}.${TRACK5_LANG}.srt"
        ;;
        *)
        T5_EXT="${TRACK5_ID}:${MKV_FILE_NAME%.*}.${TRACK5_LANG}.txt"
        ;;
        esac
    fi
    ;;
    *)
    msg2="¿Cuantas Pistas tiene este MKV!!!? - $TRACKS_NUM Pistas"
    ;;
    esac
done
TRKS2EXT="${T1_EXT} ${T2_EXT} ${T3_EXT} ${T4_EXT} ${T5_EXT}"
TRKS2EXT=`echo ${TRKS2EXT} | sed 's/  //p'`
TRKS2MP4="${T1_MP4} ${T2_MP4} ${T3_MP4} ${T4_MP4} ${T5_MP4}"
TRKS2MP4=`echo ${TRKS2MP4} | sed 's/  //p'`

mkvextract tracks "${MKV_FILE_NAME}" ${TRKS2EXT} > /tmp/mkvx.log &
pid=$!
DemuxProgress

if [[ ${TRACK1_CODEC} = "MS/VFW/FOURCC" || ${TRACK2_CODEC} = "MS/VFW/FOURCC" || ${TRACK3_CODEC} = "MS/VFW/FOURCC" || ${TRACK4_CODEC} = "MS/VFW/FOURCC" || ${TRACK5_CODEC} = "MS/VFW/FOURCC" ]]
then
    MP4Box ${TRKS2MP4} "${MKV_FILENAME%.*}.avi" > /tmp/mp4x.log &
    pid=$!
    RemuxProgress
else
    MP4Box ${TRKS2MP4} "${MKV_FILENAME%.*}.mp4" > /tmp/mp4x.log &
    pid=$!
    RemuxProgress
fi

zenity --title "MKV Converter" --window-icon=mkv.png --info --text="Remuxing completado"

mv "${MKV_FILE_NAME}" "${MKV_FILENAME}"

rm "${MKV_FILE_NAME%.*}".tmp.*
rm ${MKV_INFO} 2>/dev/null
rm ${TRACKS_CHK} 2>/dev/null
rm /tmp/mkvx.log
rm /tmp/mp4x.log

```PS: TAKE CARE, CODING IS EDITED COS OF FORUM RULES!!! *** MEANS A-S-S

---

### Post by Deanodirector on 2010-06-21
Hi,

The first scripts gave me the unable to open file ....mkv.video.h264 dows not exist error

The very last script worked but the audio was completely out of sync in the mp4 it created. any ideas?

---

### Post by troipoison on 2010-08-12
Thanks for the script.
After I followed the ffmpeg compile tutorial properly it worked like a charm!!
Oh I should mention it worked like a charm for my Xbox360, should add that to the header -  Converting (remuxing) AVC (h264) MKVs to play nicely on a Playstation3/Xbox 360

To the post above ^^^ (Deanodirector), for the '....mkv.video.h264 does not exist error' I had the same problem with '....mkv.audio.aac does not exist error'
resolution, uninstall ffmpeg, and follow the compile tutorial to the letter (copy/paste is your friend). ('-enable h264' might not have been included in your ffmpeg make build)

As for OOS issues, I would guess the same. A new install of ffmpeg
good luck.:)

---

