---
title: "ffmpeg Script for batch convert video files into mp4 for iDevice really fast!"
date: 2012-07-05
forum: Tutorials
---

### Post by beterhans on 2012-07-05
=========== UPDATED Aug 16 2013 ===========

Hello
I'm a ubuntu user and a Mac / iDevice / iTunes user.

Because of the restriction of iTunes, you can't play divx or mkv files in iPhone / iPod / or iPad. even Xboxs / PS3

so you need to convert files. and a lots of files.
most convertor sucks. they are slow!
actually you can make it faster. 

you know: video files have 
container: like mp4 mkv avi (change container is superfast)
video: like h.264 divx, (change video format is superslow)
audio: like mp3 aac ac3 5.1 dts (change audio format is fast)

Now lots of mkvs now encoded in H.264 that means you don't need to re-encode the video part. that save a lots of time!

unlike other tools I want something can decide what to convert what to copy automaticlly.

So I start to learn shell script and here is my first shell script



How to use:
it come's with 2 files
ffbc.sh
ffbc_atv.sh

ffbc.sh is for all devices but it will convert AC3 5.1 audio into aac 2 channel.

ffbc_atv.sh is for Apple TV it won't convert AC3 5.1 audio but copy it into new file because APPLE TV can play/passthrought AC3 5.1 audio

0. make sure you have ffmpeg 2.x with libfaac and x264 installed. [COLOR="Red"]**(there are 2 ffmpegs, this script works for the ffmpeg from ffmpeg.org not the avconv)**[/COLOR]
1. put all video files into a folder ([COLOR="Red"]**File name MUST NOT have Spaces**[/COLOR])
2. make sure you have rights for write into the folder
3. cd the folder contain the scripts.
4. type the command

like:

```
sh ffbc.sh mp4 /home/username/video
```

this will start to convert all video files in /home/username/video into mp4 format which iDevices can play.

if you want to covert into mkv for further process try

```
sh ffbc.sh mkv /home/username/video
```
this will start to convert all video files in /home/username/video into mkv with H.264 video and aac audio. 

5. find new file in output folder




Script: ffbc.sh
```

#! /bin/bash

# Batch Convert Script by Beterhans based on FFMPEG
# The Purpose of this Script is to convert any video file to mp4 format
# which most hardware player like iPhone/iPod PS3 Xbox360 could play.
# you can even convert to mkv with h.264 + aac for further process
# this script only convert necessary tracks if the video is already
# in H.264 format it won't convert it save your great time! and quality.

# if you want to make multi-track audio/video/sub mp4 you should convert
# to mkv and then use a MAC OS X app called "mp4tools"
# to mix them down into m4v

# Put all video files need to be converted in a folder!
# the name of files must not have " " Space!
# Rename the File if contain space 


# Variable used
# indir
# ffversion the version if your ffmpeg
# outmode is out put for mkv or mp4
# outformat is used by ffmpeg
# vcodec acodec for ffmpeg

# working mode
outmode=$1

# Target dir
indir=$2
cd "$indir"
if mkdir -p output
	then
	 echo "\nUsing $indir/output as Output Folder"
	else
	 echo "\n\nErr: Check you have the rights to write in $indir ?"
	 exit
fi


# check output mode
if [ $outmode = "mp4" ] || [ $outmode = "mkv" ]
	then 
	echo "\nWORKING MODE $outmode"
	else
	echo "$outmode is NOT a Correct target format\nYou need to set an output format! like "ffbc mp4 xxxx" or ffbc mkv xxxx"
	exit
fi

# set format
if [ $outmode=mp4 ]
	then
	 outformat=mp4
	else
	 outformat=matroska
fi

# Check FFMPEG Installation
if ffmpeg -formats > /dev/null 2>&1 
	then
	 ffversion=`ffmpeg -version 2> /dev/null | grep ffmpeg | sed -n 's/ffmpeg\s//p'`
	 echo "Your ffmpeg verson is $ffversion"
	else
	 echo "\nERROR:\nYou need ffmpeg installed with x264 and an aac encoder"
	 exit
fi

if ffmpeg -formats 2> /dev/null | grep "E mp4" > /dev/null
	then
	 echo "Check mp4 container format ... OK"
	else
	 echo "Check mp4 container format ... NOK"
	 exit
fi

if ffmpeg -formats 2> /dev/null | grep "E matroska" > /dev/null
        then
         echo "Check mkv container format ... OK"
        else
         echo "Check mkv container format ... NOK"
         exit
fi

if ffmpeg -codecs 2> /dev/null | grep "libfaac" > /dev/null
        then
         echo "Check fAAC Audio Encoder ... OK"
        else
         echo "Check fAAC Audio Encoder ... NOK"
         exit
fi

if ffmpeg -codecs 2> /dev/null | grep "libx264" > /dev/null
        then
         echo "Check x264 the free H.264 Video Encoder ... OK"
        else
         echo "Check x264 the free H.264 Video Encoder ... NOK"
         exit
fi

echo "Your FFMpeg is OK\nEntering File Processing\n\n"

################################################################

for filelist in `ls`
do
	if ffmpeg -i $filelist 2>&1 | grep 'Invalid data found'		#check if it's video file
	   then
	   echo "\n\nERROR\nFile $filelist is NOT A VIDEO FILE can be converted!"
	   exit	   
	
	fi

	if ffmpeg -i $filelist 2>&1 | grep Video: | grep h264		#check video codec
	   then
	    vcodec=copy
	   else
	    vcodec=libx264
	fi

	if ffmpeg -i $filelist 2>&1 | grep Video: | grep "High 10"	#10 bit H.264 can't be played by Hardware.
	   then
	    vcodec=libx264
	fi

	if ffmpeg -i $filelist 2>&1 | grep Audio: | grep aac		#check audio codec
	   then
	    acodec=copy
	   else
	    acodec=libfaac
	fi

	echo "\n\nUseing video codec: $vcodec audio codec: $acodec and Container format $outformat for\nFile: $filelist\n\n\n\nStarting Converting\n" 

# using ffmpeg for real converting
	echo "ffmpeg -i $filelist -y -f $outformat -acodec $acodec -ab 128k -ac 2 -absf aac_adtstoasc -async 1 -vcodec $vcodec -vsync 0 -profile:v main -level 3.1 -qmax 22 -qmin 20 -x264opts no-cabac:ref=2 -threads 0 ./output/$filelist.$outmode\n\n"
	ffmpeg -i $filelist -y -f $outformat -acodec $acodec -ab 128k -ac 2 -absf aac_adtstoasc -async 1 -vcodec $vcodec -vsync 0 -profile:v main -level 3.1 -qmax 22 -qmin 20 -x264opts no-cabac:ref=2 -threads 0 ./output/$filelist.$outmode

	
done
	echo ALL Processed!



###################
echo "DONE"
exit


```





Script: ffbc_atv.sh
```

#! /bin/bash

# Batch Convert Script by Beterhans based on FFMPEG
# The Purpose of this Script is to convert any video file to mp4 format
# which most hardware player like iPhone/iPod PS3 Xbox360 could play.
# !Note! this script won't convert AC3 Stream. 
# becase Apple TV are capable passthrough AC3 stream
# you can even convert to mkv with h.264 + aac for further process
# this script only convert necessary tracks if the video is already
# in H.264 format it won't convert it save your great time! and quality.

# if you want to make multi-track audio/video/sub mp4 you should convert
# to mkv and then use a MAC OS X app called "mp4tools"
# to mix them down into m4v

# Put all video files need to be converted in a folder!
# the name of files must not have " " Space!
# Rename the File if contain space 


# Variable used
# indir
# ffversion the version if your ffmpeg
# outmode is out put for mkv or mp4
# outformat is used by ffmpeg
# vcodec acodec for ffmpeg

# working mode
outmode=$1

# Target dir
indir=$2
cd "$indir"
if mkdir -p output
	then
	 echo "\nUsing $indir/output as Output Folder"
	else
	 echo "\n\nErr: Check you have the rights to write in $indir ?"
	 exit
fi


# check output mode
if [ $outmode = "mp4" ] || [ $outmode = "mkv" ]
	then 
	echo "\nWORKING MODE $outmode"
	else
	echo "$outmode is NOT a Correct target format\nYou need to set an output format! like "ffbc mp4 xxxx" or ffbc mkv xxxx"
	exit
fi

# set format
if [ $outmode=mp4 ]
	then
	 outformat=mp4
	else
	 outformat=matroska
fi

# Check FFMPEG Installation
if ffmpeg -formats > /dev/null 2>&1 
	then
	 ffversion=`ffmpeg -version 2> /dev/null | grep ffmpeg | sed -n 's/ffmpeg\s//p'`
	 echo "Your ffmpeg verson is $ffversion"
	else
	 echo "\nERROR:\nYou need ffmpeg installed with x264 and an aac encoder"
	 exit
fi

if ffmpeg -formats 2> /dev/null | grep "E mp4" > /dev/null
	then
	 echo "Check mp4 container format ... OK"
	else
	 echo "Check mp4 container format ... NOK"
	 exit
fi

if ffmpeg -formats 2> /dev/null | grep "E matroska" > /dev/null
        then
         echo "Check mkv container format ... OK"
        else
         echo "Check mkv container format ... NOK"
         exit
fi

if ffmpeg -codecs 2> /dev/null | grep "libfaac" > /dev/null
        then
         echo "Check fAAC Audio Encoder ... OK"
        else
         echo "Check fAAC Audio Encoder ... NOK"
         exit
fi

if ffmpeg -codecs 2> /dev/null | grep "libx264" > /dev/null
        then
         echo "Check x264 the free H.264 Video Encoder ... OK"
        else
         echo "Check x264 the free H.264 Video Encoder ... NOK"
         exit
fi

echo "Your FFMpeg is OK\nEntering File Processing\n\n"

################################################################

for filelist in `ls`
do
	if ffmpeg -i $filelist 2>&1 | grep 'Invalid data found'		#check if it's video file
	   then
	   echo "\n\nERROR\nFile $filelist is NOT A VIDEO FILE can be converted!"
	   exit	   
	
	fi

	if ffmpeg -i $filelist 2>&1 | grep Video: | grep h264		#check video codec
	   then
	    vcodec=copy
	   else
	    vcodec=libx264
	fi

	if ffmpeg -i $filelist 2>&1 | grep Video: | grep "High 10"	#10 bit H.264 can't be played by Hardware.
	   then
	    vcodec=libx264
	fi

	if ffmpeg -i $filelist 2>&1 | grep Audio: | grep aac		#check audio codec
	   then
	    acodec=copy
	elif ffmpeg -i $filelist 2>&1 | grep Audio: | grep 5.1		#check audio codec
	   then
	    acodec=copy
	   else
	    acodec=libfaac
	fi

	echo "\n\nUseing video codec: $vcodec audio codec: $acodec and Container format $outformat for\nFile: $filelist\n\n\n\nStarting Converting\n" 

# using ffmpeg for real converting
        echo "Command:\nffmpeg -i $filelist -y -f $outformat -acodec $acodec -ab 256k -ac 2 -absf aac_adtstoasc -vcodec $vcodec -profile:v main -level 3.1 -qmax 22 -qmin 20 -x264opts no-cabac:ref=2 -threads 0 ./output/$filelist.$outmode\n\n"
        ffmpeg -i $filelist -y -f $outformat -acodec $acodec -ab 256k -ac 2 -absf aac_adtstoasc -vcodec $vcodec -profile:v main -level 3.1 -qmax 22 -qmin 20 -x264opts no-cabac:ref=2 -threads 0 ./output/$filelist.$outmode
	
done
	echo ALL Processed!



###################
echo "DONE"
exit


```

If you find the code won't work for your ffmepg
try this new one. it works with newer ffmpeg
[http://www.sendspace.com/file/9n9wwo](http://www.sendspace.com/file/9n9wwo)

---

### Post by Quackers on 2012-07-05
*Thread moved to **Tutorials & Tips**.*

---

### Post by mattoligy on 2012-07-15
Hi, this is Really really helpful :-)

Do you think you could adapt it a bit for me, as i want to use it as a post process script with iSabnzbd which is a python usenet client for ios!

I want to just enable the script per download if i am downloading an mkv movie, which most are lol, so that after it has been downloaded and extracted this script will kick in and convert it to mp4 ready to be played on the stock player! I dont think i want the audio touched though? Is there any chance of removing that part?

I was thinking maybe (And bear with me as i know Nothing lol)

1) Change the name of any mkv in downloads/subfolder to "input.mkv"
2) This script kicks in and changes container from mkv to mp4
3) input.mkv is deleted and input.mp4 is renamed to what it was, ideally from parent folder name

Would this be hard to do? Thanks So much for any help, this has been driving me crazy for days of non stop research...

Matt

---

### Post by beterhans on 2012-07-15
> **mattoligy said:**
> Hi, this is Really really helpful :-)

Do you think you could adapt it a bit for me, as i want to use it as a post process script with iSabnzbd which is a python usenet client for ios!

I want to just enable the script per download if i am downloading an mkv movie, which most are lol, so that after it has been downloaded and extracted this script will kick in and convert it to mp4 ready to be played on the stock player! I dont think i want the audio touched though? Is there any chance of removing that part?

I was thinking maybe (And bear with me as i know Nothing lol)

1) Change the name of any mkv in downloads/subfolder to "input.mkv"
2) This script kicks in and changes container from mkv to mp4
3) input.mkv is deleted and input.mp4 is renamed to what it was, ideally from parent folder name

Would this be hard to do? Thanks So much for any help, this has been driving me crazy for days of non stop research...

Matt

I don't think I'll do this
1st. Because I Don't JB my iOS devices.
2nd I Just put movies in iTunes and use home sharing stream them to iOS devices.
3rd I want subler to add movie metadata info, subtitles and cover into the mp4 and it looks nice.
4th I'm not a usenet user. The only usenet I've been used maybe free newsgroups :) I don't know how to use usenet to download files.
5th ffmpeg on Linux or Mac OS X require compile from source along with x264 and libfaac. I don't think I can do it on iOS

---

### Post by radiocom on 2012-07-23
Can anyone give an advice how can I use ffmpeg as a transcoding server that pass a transcoded stream to Wowza streaming server?

---

### Post by sudodus on 2012-07-23
> **radiocom said:**
> Can anyone give an advice how can I use ffmpeg as a transcoding server that pass a transcoded stream to Wowza streaming server?
Welcome to the Ubuntu Forums :-)

You are free to write in this thread, but I think you will get more and better feedback, if you start a new thread with a good desciptive title and write a few more lines in the first post to describe what you have and what you want.

Good luck :-)

See also 

[[COLOR="Red"]_https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide_[/COLOR]]("https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide")

[[COLOR="red"]_http://ffmpeg.org/contact.html_[/COLOR]]("http://ffmpeg.org/contact.html")

[[COLOR="red"]_http://ubuntuforums.org/showthread.php?t=786095_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=786095")

---

### Post by xmrkite on 2012-10-05
Hello, I am trying to get this to work, but get this error every time I run any of your scripts:


Your ffmpeg verson is 0.7.6-4:0.7.6-0ubuntu0.11.10.1
Check mp4 container format ... OK
Check mkv container format ... OK
Check fAAC Audio Encoder ... NOK



I have installed ffmpeg and all the codecs from medibuntu but don't know what to do now. Also, could I easily change your script to have the video done with mp3 audio? Will that still play on my android phone?

---

### Post by beterhans on 2012-10-05
> **xmrkite said:**
> Hello, I am trying to get this to work, but get this error every time I run any of your scripts:


Your ffmpeg verson is 0.7.6-4:0.7.6-0ubuntu0.11.10.1
Check mp4 container format ... OK
Check mkv container format ... OK
Check fAAC Audio Encoder ... NOK



I have installed ffmpeg and all the codecs from medibuntu but don't know what to do now. Also, could I easily change your script to have the video done with mp3 audio? Will that still play on my android phone?

You need to google how to compile ffmpeg from source code with x264 and libfaac
aac is not a free codec so it wont include in common deb.

there is still a chance that your android phone's system player cant play mp4 with mp3 audio cuz aac is the standard mp4 audio format.

---

### Post by Merrattic on 2012-10-06
Tried the script, had to add ":v" to "-profile" and remove +slice to get the main command to run (converting an mp4 to mkv, which was really just a container swap and audio badly out of sync).

Tried on an avi and the script failed to do anything other than create an empty output file

---

### Post by beterhans on 2012-10-07
> **Merrattic said:**
> Tried the script, had to add ":v" to "-profile" and remove +slice to get the main command to run (converting an mp4 to mkv, which was really just a container swap and audio badly out of sync).

Tried on an avi and the script failed to do anything other than create an empty output file

is script is for an old ffmpeg
yes newer version need to add :v

I have a script for newer version it's the zip file locate at the last line of 1st post.
avi should works fine. but yes some avi will out of sync. and I don't know why :(

---

### Post by Merrattic on 2012-10-10
Tried the script for newer ffmpeg and this works now, but still get a bad a/v sync, sound way ahead of video, when converting mp4 to mkv 

(Elephants Dream (1080p) from Blender project)
```
Duration: 00:10:53.79, start: 0.000000, bitrate: 3519 kb/s
    Stream #0:0(und): Audio: aac (mp4a / 0x6134706D), 44100 Hz, stereo, s16, 125 kb/s
    Stream #0:1(und): Video: h264 (High) (avc1 / 0x31637661), yuv420p, 1920x1080 [SAR 1:1 DAR 16:9], 3391 kb/s, 24 fps, 24 tbr, 24k tbn, 48 tbc
```

---

### Post by Lyfang on 2012-10-10
Does this shell (bash) script also work with Libav (a fork of FFmpeg)? FFmpeg is not being developed anymore.

---

### Post by FakeOutdoorsman on 2012-10-10
> **Lyfang said:**
> FFmpeg is not being developed anymore.

Totally incorrect. People think this is true due to the message they get when they try to use libav's version of "ffmpeg". Neither the message (annoyingly) nor users (understandably) make a distinction between the ffmpeg (the program) and the FFmpeg (the project). It is true that their "ffmpeg" is not being developed anymore, and it has since been dropped from libav since they basically renamed ffmpeg to avconv. It's a controversial mess and I can't imagine libav not foreseeing user confusion from their malworded message and enjoying this side-effect.

I tried to get the maintainer to re-word the message, but the process was frustrating and the result was unsatisfactory.

FFmpeg and ffmpeg are very alive.

See [Who can tell me the difference and relation between ffmpeg, libav, and avconv](http://stackoverflow.com/a/9477756/1109017) for a quick summary.

---

### Post by beterhans on 2012-10-10
> **FakeOutdoorsman said:**
> Totally incorrect. People think this is true due to the message they get when they try to use libav's version of "ffmpeg". Neither the message (annoyingly) nor users (understandably) make a distinction between the ffmpeg (the program) and the FFmpeg (the project). It is true that their "ffmpeg" is not being developed anymore, and it has since been dropped from libav since they basically renamed ffmpeg to avconv. It's a controversial mess and I can't imagine libav not foreseeing user confusion from their malworded message and enjoying this side-effect.

I tried to get the maintainer to re-word the message, but the process was frustrating and the result was unsatisfactory.

FFmpeg and ffmpeg are very alive.

See [Who can tell me the difference and relation between ffmpeg, libav, and avconv](http://stackoverflow.com/a/9477756/1109017) for a quick summary.

Thank you very much for the info
that's why the command is different.

---

### Post by kingcharles1666 on 2013-01-01
I have used the script with success to convert a bunch of files but for another bunch it does not work. The error displayed is:

[I]Input stream #0.2 frame changed from rate:48000 fmt:s16 ch:6 to rate:48000 fmt:s16 ch:2
[B][mp4 @ 0x8dc860] Application provided invalid, non monotonically increasing dts to muxer in stream 0: -2 >= -2
av_interleaved_write_frame(): Invalid argument[/B][/I]

Any ideas what the problem could be? I did a bit of googling and [found a thread on this]("http://ffmpeg.org/pipermail/ffmpeg-devel/2012-February/121184.html") error but not much else.

Something that can be fixed in the file?
Thanks

Edit: Using standard Ubuntu 12.04

---

### Post by beterhans on 2013-08-16
updated for ffmpeg 2.0

---

### Post by beterhans on 2013-08-16
try the new one with ffmpeg 2.0

---

