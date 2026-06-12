---
title: "bash script batch ffmpeg convert"
date: 2010-03-11
forum: Server Platforms
---

### Post by prodsacnetworking on 2010-03-11
HI, 

I try to convert .flv files by batch, but I can't seem to be making it work any ideas? here the script:

> #!/bin/bash
##########
# Variables
FICHIERS='ls *.flv'
#FFMPEG='/usr/local/ffmpeg/bin/ffmpeg'
FLVDIR='/data/ftp/MA2/archives_camz/FLV/'
FLVDIRDONE='/data/ftp/MA2/archives_camz/FLV_DONE/'
PROCESSINGDIR='/data/ftp/MA2/archives_camz/processing/'
MPEGDIR='/data/ftp/MA2/archives_camz/MPEG/'
##########
##########

#cd $FLVDIR
#mv *.flv $PROCESSINGDIR
cd $PROCESSINGDIR
for i in 'ls *.flv' ;
do /usr/local/ffmpeg/bin/ffmpeg -i $1 -acodec ac3 -ab 96k -ac 2 -r 25 -vcodec libx264 -vpre slow -crf 22 -threads 0 $MPEGDIR/$1 ;
mv $1 $FLVDIRDONE ;
done

cd $MPEGDIR
for f in *.flv;
do mv "$f" "`basename "$f" .flv`.mpeg";
done


and the error:

> FFmpeg version SVN-r22468, Copyright (c) 2000-2010 the FFmpeg developers
  built on Mar 11 2010 14:25:01 with gcc 4.3.3
  configuration: --prefix=/usr/local/ffmpeg --enable-shared --enable-gpl --enable-nonfree --enable-pthreads --enable-libx264 --enable-decoder=mpeg1video --enable-decoder=mpeg2video --enable-decoder=flv --enable-decoder=mpeg4 --enable-decoder=tiff --enable-decoder=cinepak --enable-decoder=ac3 --enable-decoder=mp3 --enable-decoder=mjpeg --enable-decoder=wmv1 --enable-decoder=wmv2 --enable-decoder=wmv3 --enable-decoder=mpegvideo --enable-libfaac --enable-libmp3lame --enable-libxvid
  libavutil     50.11. 0 / 50.11. 0
  libavcodec    52.58. 0 / 52.58. 0
  libavformat   52.55. 0 / 52.55. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0.10. 0 /  0.10. 0
-acodec: no such file or directory
mv: missing destination file operand after `/data/ftp/MA2/archives_camz/FLV_DONE/'
Try `mv --help' for more information.
mv: cannot stat `*.flv': No such file or directory


From what I see, he seems to interpret the -acodec option in ffmpeg as an output file or something...

any ideas? 

thanks

---

### Post by Samatva on 2010-03-11
I'm a bit of a bash neophyte, but shouldn't the "$1" be a "$i" instead??

I'm also not sure of your objective, but VLC *might* be an alternative for converting - I think is uses ffmpeg, but the command lines might be shorter.

---

