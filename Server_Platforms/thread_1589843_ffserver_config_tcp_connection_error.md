---
title: "ffserver config tcp connection error"
date: 2010-10-07
forum: Server Platforms
---

### Post by phroman on 2010-10-07
Hi all, I'm unable to connect to ffserver, hope I can get a bit of help.  

I installed ffmpeg and ffserver, I can start the server and verify that it's running via the web admin. 

```
FFserver Status

Available Streams

Path	  Served  Conns	 bytes	Format	 Bit rate kbits/s    Video kbits/s   Codec    Audio kbits/s  Codec       Feed
test.flv	   0	  0	 flv	 40550	  	  	40550	      flv	     0                 feed1.ffm         
stat.html	   1	  0	 -	  -	    -		 -
	
Feed feed1.ffm

Stream	type	kbits/s	codec	Parameters
0	video	40550	flv	352x288, q=2-31, fps=14

Connection Status

Number of connections: 1 / 10
Bandwidth in use: 0k / 10000k
#	File	IP	Proto	State	Target bits/sec	Actual bits/sec	Bytes transferred
1	stat.html	127.0.0.1	HTTP/1.1	HTTP_WAIT_REQUEST	0	0	0
```

I can type: ffplay -f video4linux2 /dev/video0 and a small window will open and I see the feed from my webcam. 
I can type: ffmpeg -f oss -i /dev/dsp -f video4linux2 -i /dev/video0 /tmp/out.mpg and record a video file from my webcam.

I'm trying to start the stream and then view it via VLC.  To start the stream I'm typing:  

ffmpeg -f oss -i /dev/dsp -f video4linux2 -i /dev/video0 -r 14.2 -s 352x288 [http://localhost:8090/feed1.ffm](http://localhost:8090/feed1.ffm)

The reslult is always a TCP connection error. Complete result here: 
```
FFmpeg version SVN-r25329, Copyright (c) 2000-2010 the FFmpeg developers
  built on Oct  3 2010 21:39:11 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-x11grab --enable-libmp3lame
  libavutil     50.32. 0 / 50.32. 0
  libavcore      0. 9. 0 /  0. 9. 0
  libavcodec    52.92. 0 / 52.92. 0
  libavformat   52.79. 0 / 52.79. 0
  libavdevice   52. 2. 2 / 52. 2. 2
  libavfilter    1.48. 0 /  1.48. 0
  libswscale     0.12. 0 /  0.12. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[oss @ 0x9e45470] Estimating duration from bitrate, this may be inaccurate
Input #0, oss, from '/dev/dsp':
  Duration: N/A, start: 1286431294.749004, bitrate: N/A
    Stream #0.0: Audio: pcm_s16le, 44100 Hz, 1 channels, s16, 705 kb/s
[video4linux2 @ 0x9e48c90] Estimating duration from bitrate, this may be inaccurate
Input #1, video4linux2, from '/dev/video0':
  Duration: N/A, start: 1286431296.069869, bitrate: -2147483 kb/s
    Stream #1.0: Video: rawvideo, yuyv422, 352x288, -2147483 kb/s, 1000k tbr, 1000k tbn, 1000k tbc
TCP connection to localhost:8090 failed: Connection refused
HTTP error 503 Server too busy
http://localhost:8090/feed1.ffm: Input/output error
ioctl(VIDIOC_QBUF)
joe@blackbox:~$  repeated 20 times
```


Here is my ffserver.conf file:

```
Port 8090
BindAddress 0.0.0.0
MaxHTTPConnections 20
MaxClients 10
MaxBandwidth 100000
CustomLog -
NoDaemon

<Feed feed1.ffm>
File /tmp/feed1.ffm
FileMaxSize 5M
ACL allow localhost
</Feed>

<Stream test.flv> 
Feed feed1.ffm 
Format flv 
# this must match the ffmpeg -r argument 
VideoFrameRate 14.2 
VideoBufferSize 80000 
VideoBitRate 40550 
VideoSize 352x288 
PreRoll 0 
Noaudio 
ACL allow localhost
ACL allow 192.168.0.0 192.168.255.255
</Stream> 

#<Stream test1.flv>
#Feed feed1.ffm
#Format flv
#AudioBitRate 32
#AudioChannels 1
#AudioSampleRate 44100
#VideoBitRate 64
#VideoBufferSize 40000
#VideoFrameRate 14
#VideoSize 352x288
#</stream>


#<Stream test.asf>
#Feed feed1.ffm
#Format asf
#VideoFrameRate 15
#VideoSize 352x288
#VideoBitRate 320
#VideoBufferSize 40
#VideoGopSize 30
#AudioBitRate 64
#StartSendOnKey
#ACL allow localhost
#</Stream>


<Stream stat.html>
Format status
# Only allow local people to get the status
ACL allow localhost
ACL allow 192.168.0.0 192.168.255.255
</Stream>
```

How is the server running and I can see the status page but ffmpeg cannot connect to the server?  Very new to ffmpeg and server, stuck and not sure how to proceed.  Thanks in advance for any help on getting this running.  :)

---

