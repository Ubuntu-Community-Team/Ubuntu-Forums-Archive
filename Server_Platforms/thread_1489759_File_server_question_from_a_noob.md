---
title: "File server question from a noob"
date: 2010-05-21
forum: Server Platforms
---

### Post by banff2010 on 2010-05-21
I am hoping to set up a file server. I have an imac, laptop(XP) and Sony computer which has ubuntu desktop. My router is an apple Time capsule (500Gigs). I want to put ubuntu server on the Sony computer and attach two USB drives to it (one WD 2TB and other home built 1.5TB). I will download movies (of course not pirated ones)  using JDownloader on the Sony computer and play using ps3mediaserver on imac. Would this work? Should I just give up and set up JDownloader on imac and throw out the Sony computer? Should I go with samba file server, since USB drives are already formatted in NTFS, or just reformat for imac/ubuntu?

---

### Post by CharlesA on 2010-05-21
Samba would probably work, since you have a Windows machine in the mix.

It wouldn't matter what file system the USB drives are using, since they would only need to be able to be read by the machine serving the files, not by the machine that is reading the files off the network.

---

### Post by jbrown96 on 2010-05-21
ps3mediaserver also runs on Linux. I don't know how much transcoding you will need to do and how fast the Sony machine is, but you may be able to eliminate the iMac from the file server setup. 
If you stay with the iMac serving files to the PS3, then I would recommend setting up NFS. Transfer rates are much faster and won't stress your LAN as much. You probably have a router that connects all your machines; the content has to go Ubuntu-->iMac-->PS3 but will all use the same router, so you are creating twice as much traffic. Your LAN might not be able to handle it. Samba is not particularly bandwidth-efficient. Running Ps3mediaserver from the Ubuntu box would be even better.

If you plan to expand your storage in the future, then it would be far better to format the hard drives and put an LVM below the file system. This makes it far easier to increase your storage in the future.

---

### Post by arrrghhh on 2010-05-21
+1.  Get that iMac outta the mix.  Let your server serve all!

---

### Post by banff2010 on 2010-05-21
Thanks for all suggestions. Ps3mediaserver on my Sony (xp) computer couldn't handle 1080p movies,wonder how it work on ubuntu; thats why I went with imac. But imac is from work, so I don't want to have lots of unnecessary stuff on it for a year or so. I will read on LVM. Eventually, when I get some (more?) money I will have MythTV too.

---

### Post by arrrghhh on 2010-05-21
I have issues transcoding 1080p.  If the file is in a native format the PS3 can understand, 1080p is no problem whatsoever - however, if you have a 1080p file that's an MKV for example, then you have to transcode the file on-the-fly - you need a pretty beefy server to do this.  Doesn't matter if it's XP, Mac, or Ubuntu, I hear that you need at a minimum a quad-core PC.  Keep that in mind.

My server is a lowly dual-core with 3gb of RAM - I think I'm fine on the RAM, but for transcoding HD that's where processor power comes in.

---

### Post by banff2010 on 2010-05-21
Thanks arrghhh:

OK so this mean I should find a fast method to convert .mkv (1080p) files to ps3 compatible format which does not degrade the quality, to use with ps3mediaserver on sony (ubuntu)

Thanks

---

### Post by arrrghhh on 2010-05-21
Essentially, yes.  If you want little load on your streaming server, try to get all the files in a native format for the PS3 (DivX or the like...)

---

### Post by banff2010 on 2010-05-27
So, after trying mkvtoolnix unsuccessfully to convert .mkv files to a native ps3 format, I came across [this]("http://www.smlabs.net/tsmuxer_en.html"). I  installed it and it took only about 15 minutes to convert 7.5GB .mkv file into m2ts or bluray format. But in the conversion it kept saying they changed the FPS rate; so did that mean it degraded the video quality? Also, am I correct to assume m2ts or bluray format do not need "on the fly trans coding"?

Also, if I delete all the programs other than what I need to use, it would not cause any problems?

I am just getting into these thing. Many moons ago I was quite happy with BSD-unix; it was just command lines.I am  sorry if these don't make any sense.

---

### Post by arrrghhh on 2010-05-27
No worries.  I'm not sure how to answer your question, I don't know what you mean by "bluray format"... like an H.264 MP4 or something?!?

The m2ts format is essentially what PS3MediaServer is converting to on-the-fly.  It should work, and hopefully with little degredation... however, the files will be HUGE.

If the software changed the framerate, it may have degraded the quality.  The only way you can prevent from quality loss is if you're going to a different container and you're keeping the codec.  For example if the video is H.264 and you have it in an MKV file, you can convert that file to MP4 or AVI without losing any video quality - you must be careful however, not all applications are created equal in this sense.

I have yet to find a single piece of software that will convert all MKV files to a PS3-compliant format.  The problem is, MKV is just a container and you can pretty much throw anything into it, format-wise.  So it's very difficult to make a one-size-fits-all for converting MKV files...

---

