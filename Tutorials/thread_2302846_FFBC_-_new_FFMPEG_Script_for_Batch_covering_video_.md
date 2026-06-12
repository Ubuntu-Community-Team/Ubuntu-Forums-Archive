---
title: "FFBC - new FFMPEG Script for Batch covering video files like TV shows for iTunes iOS"
date: 2015-11-14
forum: Tutorials
---

### Post by beterhans on 2015-11-14
This script can run under any OS with bash
Ubuntu Fedora Mac ... etc..

I used to have an [older one]("http://ubuntuforums.org/showthread.php?t=2017284") but outdated

It need ffmpeg 2.x (tested on 2.6) to run
it need the encoder libfdk_aac to run

the purpose of this script is
I have a tv show in mkv format
lots of them. 
I need to use handbrake to convert them (or you can't play it on iTunes and can't sync it in iDevice)
I have to use tag edit to edit them.  (or you got nameless video file in home video section. it won't show in TV show or Moive section)
after that I got nice edited video file you can drop into your iTunes them sync into your iOS device.

and this script 
auto check you video or audio is needed to be re-encodeed or not.if it don't need to be re-encoded. it won't do it. so your audio and video quailty won't suffer.
it auto add video tag and video type for you

!!!Waring! if your input video is VFR (frame rate is variable) and it's in h.264 8 bit format. you will run into audio video sync problem.!!!  cause the script won't re-encode it.!!!

===== HOW to use ======
create a folder like tv_show_123 (without space or "-" or [] ())
put all your video files in that folder.(without space or "-" or [] ()) and your video file must in order.
run the script like
bash ffbc.sh tv_show_123

it will ask a few question and start.

Download
[https://www.sendspace.com/file/15ybnb](https://www.sendspace.com/file/15ybnb)

---

### Post by mc4man on 2015-11-14
It's a small file, just stick in a folder, compress & attach to post. Better than some wonky site.

---

### Post by beterhans on 2015-11-14
Thanks I forgot it since most forums don't allow upload attachments.

---

