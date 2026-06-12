---
title: "FFmpeg - Removing Commercial Breaks from mpeg TV Recordings"
date: 2009-05-19
forum: Ubuntu Studio
---

### Post by Chris_Smith on 2009-05-19
Hi Guys,

I have been experimenting with FFmpeg, and was hoping that by using the "-ss" and "-t" options with multiple inputs, that it would be possible to directly encode the content from an mpeg-ts TV recording without including the commercial breaks.

I have two input files "input01.mpg", and "input02.mpg" that contain six sections of "unwanted" content as shown below:

xxx = unwanted material

input01.mpg - total time 00:19:27

--------------------
|  00:12:57 |xxx|
--------------------
|0

input02.mpg - total time 01:33:11

-----------------------------------------------------------------------------------
|xxx| 00:21:43 |xxx| 00:16:57 |xxx| 00:18:34 |xxx|00:20:18 |xxx|
-----------------------------------------------------------------------------------
|0--|-00:04:57------|-00:27:21------|-00:48:56------|01:12:08

In the past I have used the "-ss" and "-t" options to separately encode sections of the above files using for example the following options:

ffmpeg -i input02.mpg -ar 22050 -acodec libmp3lame -ab 32k -r 25 -s 320x240 -vcodec flv -ss 00:27:21 -t 00:16:57 output.flv

and then concatenated the five flv files using the pipe method described in the FFmpeg help files. However, this takes a long time on my system, and I was hoping that the same result could be achieved using something like the following to directly encode the five sections:

ffmpeg -t 00:12:57 -i input01.mpg -ss 00:04:57 -t 00:21:43 -i input02.mpg ........................... output.flv

Any help would be greatly appreciated.
-----------
Chris_Smith

---

