---
title: "Converting mkv to m2ts for playing on Playstation3"
date: 2009-01-03
forum: Ubuntu Studio
---

### Post by sundowndk on 2009-01-03
Hi,

I have been messing around with a small script for converting (remuxing) MKV files into M2TS. So you might think why m2ts?! well, simple the PS3 normally does not allow for 5.1 AC3 audio playback when its streamed across the network via DNLA, BUT for some reason it works with the m2ts container. I havent looked into why that is, I just wish that Sony would support MKV in the first place.. :-)

Now most MKV files on the net have DTS audio, so this also needs to be taken care of, the script reencodes DTS into AC3 if DTS tracks are found. 

The script uses a couple of tools to get the job done. 

tsMuxer: [http://www.videohelp.com/tools/tsMuxeR](http://www.videohelp.com/tools/tsMuxeR)
mkvtoolnix: [http://www.videohelp.com/tools/MKVtoolnix](http://www.videohelp.com/tools/MKVtoolnix)
dcadec: [http://www.videolan.org/developers/libdca.html](http://www.videolan.org/developers/libdca.html)
aften: [http://aften.sourceforge.net/](http://aften.sourceforge.net/)

I would recommend to use the win32 version of tsMuxeR for now, since the Linux version seams to mess up the audio really bad sometimes. Wine will run tsMuxeR with out any problems.

The script was not written by me originally and can be found here in its pure form :*)

[http://sticky123.blogspot.com/2008/03/remuxing-mkv-to-m2ts-on-linux.html](http://sticky123.blogspot.com/2008/03/remuxing-mkv-to-m2ts-on-linux.html)

But I did add options to use a TEMP folder, this can really speedup muxing time if the TEMP folder is located on another physical drive than the MKV that is being muxed. 

I also added a progress window using Zenity, since I mainly use this script from the desktop I thought a progress window would be nice. I do plan to make the Zenity window an option, but for now its not.  

Any ways I hope you find the script usefull, I know I do :-)

```

#!/bin/bash
#
# mkvtom2ts.sh - a simple wrapper around the tsmuxeR
# Creates a m2ts from a "standard" mkv (assuming video is MPEG4, and sound is AC3 or DTS)
#
# Original script by: http://sticky123.blogspot.com/
#
# Features from v0.4 added by: rasmus@akvaservice.dk
#
# This script needs the following tools to work:
#
# tsMuxer: http://www.videohelp.com/tools/tsMuxeR 
# mkvtoolnix: http://www.videohelp.com/tools/MKVtoolnix
# dcadec: http://www.videolan.org/developers/libdca.html
# aften: http://aften.sourceforge.net/
# zenity: http://live.gnome.org/Zenity
#
#
# v0.1 : initial version
# v0.2 : added DTS support
# v0.3 : changed to tsmuxer linux version + added multiple audio lang support
# v0.4 : added option to use tsmuxer linux or win32 version. Linux version og tsmuxer seams for now to have problems with PS3
# v0.5 : added option to use temp folder. This would speedup muxing if temp is located on another physical drive.
# v0.6 : added Zentiy progress window. 

# Usage: mkv2m2ts filename.mkv

# Options
AUDIO_LANGS="eng und swe"		
USETEMPFOLDER="yes"
USEWIN32TSMUXER="yes"
TEMPFOLDER="/tmp"

# Need a randomstring
string=$( echo "$1$$" | md5sum | md5sum )
randstring="${string:0:30}"

# Get filename and path
BASENAME=$(basename "$1" .mkv)
DIRNAME=$(dirname "$1")
DEST_FILE="$DIRNAME/$BASENAME.m2ts"

# Set tempfolder
if [ "$USETEMPFOLDER" == "no"  ]
then
	TEMPFOLDER=$DIRNAME
fi

# Some other stuff, needs cleaning
WINDOWTITLE="mkv2m2ts.sh"
VIDEOMPEG4="$TEMPFOLDER/$randstring.mpeg4"
AUDIOAC3="$TEMPFOLDER/$randstring.ac3"
AUDIODTS="$TEMPFOLDER/$randstring.dts"

MUXMETA="$TEMPFOLDER/$randstring.muxmeta"
DEMUXLOG="$TEMPFOLDER/$randstring.demuxlog"
REMUXLOG="$TEMPFOLDER/$randstring.remuxlog"
TRANSCODELOG="$TEMPFOLDER/$randstring.transcodelog"

DURATION="0"

DemuxProgress() 
{
	sleep 0.5
	while ps | grep "$pid " >/dev/null
	do
		PERCENTDONE=`tail -c 90 "$DEMUXLOG" | sed 's/.*gress://g' | sed 's/\%//'`
		if [ "$PERCENTDONE" == "100"  ]
		then
			PERCENTDONE="99"
		fi
		echo $PERCENTDONE
		echo "# $BASENAME\nDemuxing A/V..."
		sleep 1
	done
	echo 99
}

TransCodeProgress() 
{
	sleep 0.5
	PERCENTDONE="0"
	TOTALFRAMES=`echo "$DURATION * 32" | bc`
	echo "0"

	while ps | grep "$pid " >/dev/null
	do
		FRAMESCOMPLETED=`tail -c 90 "$TRANSCODELOG" | grep frame: | awk '{ print $2}'`
		PERCENTDONE=`echo "100 * $FRAMESCOMPLETED/$TOTALFRAMES" | bc`
		if [ "$PERCENTDONE" == "100" ]
		then
			PERCENTDONE="99"
		fi
		echo "$PERCENTDONE"
		echo "# $BASENAME\nTranscoding DTS to AC3..."
		sleep 1
	done
	echo 99
}

RemuxProgress() 
{
	sleep 0.5
	PERCENTDONE="0"
	echo "0"

	while ps | grep "$pid " >/dev/null
	do
		PERCENTDONE=`tail -c 20 "$REMUXLOG" | grep '% complete' | awk '{ print $1 }' | sed 's/\..*//'` 

		if [ "$PERCENTDONE" == "100" ]
		then
			PERCENTDONE="99"
		fi
		echo "$PERCENTDONE"
		echo "# $BASENAME\nRemuxing A/V"
		sleep 1
	done
	echo 99
}

CleanUp()
{
	echo 0
	echo "# $BASENAME\nCleaning up..."
	rm -f "$MUXMETA"
	echo 15
	rm -f "$VIDEOMPEG4"
	echo 30
	rm -f "$AUDIOAC3"
	echo 45
	rm -f "$AUDIODTS"
	echo 70
	rm -f "$DEMUXLOG"
	echo 90
	rm -f "$REMUXLOG"
	echo 95
	rm -f "$TRANSCODELOG"
	sleep 3
	echo "# $BASENAME\nDone"
}

# Extract MKV info
MPEG4_TRACK_NO=`mkvinfo "$1" | grep V_MPEG4/ISO/AVC -B10 | grep Track\ number\:\ | awk '{ print $5 }'`
DURATION=`mkvinfo "$1" | grep Duration | awk '{ print $4 }' | sed 's/\..*//'`

for AUDIO_LANG in $AUDIO_LANGS
do
	AC3_TRACK_NO=`mkvinfo "$1" | grep A_AC3 -B10 -C3 | grep Language\:\ $AUDIO_LANG -B13 | grep Track\ number\:\ | awk '{ print $5 }'`
	DTS_TRACK_NO=`mkvinfo "$1" | grep A_DTS -B10 -C3 | grep Language\:\ $AUDIO_LANG -B13 | grep Track\ number\:\ | awk '{ print $5 }'`

	if [ -n "$AC3_TRACK_NO" -o -n "$DTS_TRACK_NO" ]
	then
		break
	fi	
done

# Do some stuff
(
	if [[ $AC3_TRACK_NO -gt "0" ]]
	then
		# Demux A/V
		mkvextract tracks "$1" $AC3_TRACK_NO:"$AUDIOAC3" $MPEG4_TRACK_NO:"$VIDEOMPEG4" > "$DEMUXLOG" & pid=$!
		DemuxProgress
	else		
		if [[ $DTS_TRACK_NO -gt "0" ]]
		then
			# Demux A/V
			mkvextract tracks "$1" $DTS_TRACK_NO:"$AUDIODTS" $MPEG4_TRACK_NO:"$VIDEOMPEG4" > "$DEMUXLOG" & pid=$!
			DemuxProgress			

			# Transcode DTS to AC3
			dcadec -r -o wavall "$AUDIODTS" | aften -b 640 -v 2 -readtoeof 1 - "$AUDIOAC3" >"$TRANSCODELOG" 2>&1 & pid=$!
			TransCodeProgress
		else
			# If no AC3 or DTS tracks found, we fail.
			zenity 	--info \
				--title="$WINDOWTITLE" \
				--text="No AC3 or DTS audio tracks found!" \
				--width=450 --height=100 \
			exit
		fi  
	fi

	# Remux A/V
	echo "MUXOPT --no-pcr-on-video-pid --new-audio-pes --vbr" >>$MUXMETA
	echo "V_MPEG4/ISO/AVC, "$VIDEOMPEG4", level=4.1, insertSEI, contSPS, track=1, lang=eng" >>$MUXMETA
	echo "A_AC3, "$AUDIOAC3", track=1, lang=eng" >>$MUXMETA
	
		
	if [ "$USEWIN32TSMUXER" == "no"  ]
	then
		tsMuxeR "$MUXMETA" "$DEST_FILE" 2>&1 > "$REMUXLOG" & pid=$!
		
	else	
		tsMuxeR.exe "$MUXMETA" "$DEST_FILE" 2>&1 > "$REMUXLOG" & pid=$!
	fi
	RemuxProgress

	# All done, lets cleanup.	
	CleanUp
) |
zenity 	--progress \
	--title="$WINDOWTITLE" \
	--text="" \
	--width=450 --height=100 \
	--percentage=0

if [ "$?" = 1 ] 
then	
	kill $pid
	CleanUp
	exit
fi	




```

---

### Post by perarild on 2009-02-08
*

---

### Post by forgetclosure on 2010-03-08
Hello, I am currently wondering what formats the audio and video have to be in before muxing into *.m2ts. I am working with a file with an audio codec 'a52' and standard h264 video. Obviously since the audio is not DTS or AC3, this script does not work for me, so manual demuxing, converting, remuxing into m2ts is my only option. I'm sure a few others are having this problem too, although I'm also sure this isn't the biggest deal in the world. Maybe an addition to this script to also include converting a52 audio to AC3 would be a good idea, but I'm not sure how prevalent it is. Thanks for the script by the way! Aside from this, it's worked on a couple of my other movies :)

---

