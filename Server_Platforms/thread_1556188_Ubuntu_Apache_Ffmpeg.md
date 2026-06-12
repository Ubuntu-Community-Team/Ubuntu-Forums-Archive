---
title: "Ubuntu Apache Ffmpeg"
date: 2010-08-19
forum: Server Platforms
---

### Post by rgibbs421 on 2010-08-19
I am having problems making a you Tube clone site. 
Set Ubuntu up as the base platform. Installed apache2, php5, mysql, webmin within a virtual machine on VMWare esxi. Took a few days to get everything up an running but after about a week I was able to get joomla + you tube clone component working minus the uploading and encoding of videos. Thinking that it might be joomlas component I downloaded and installed clip-bucket a cms dedicated to this task. Both joomlas component and clip-bucket are looking in the /usr/bin or /usr/share section of the os for ffmpeg. I installed it using the package manager first then reverted to a walk through to compile it myself. But it gets compiled in a different directory and no matter what configurations I choose for the sites the encode part of the site seems to error out in one way or another. 

I found that most of the support for ffmpeg is for red hat so I setup another vm with fedora core and repeated the steps installing the server and all the extensions to it. But after another week of working on trying to just get fedora to make a samba share so I can work with the site from my windows machine im back in ubuntu. Im lost now. Im two weeks in I got everything working on the ubuntu but the encoding.

I have ffmpeg compiled for the system and using the terminal I can encode videos just fine. The sites are working fine as long as I have the encoding turned off on them. And, by that I mean the the videos get uploaded, the entries are placed in the database, and every thing works as long as the encoding is off. Clip-bucket has a script that goes and checks the servers ability to do this but im getting mixed signals from it. I will get a check mark saying it is operational but then on the same line I will get a yield sign indicating a problem. 

Didn’t know where I should post this move it if there is a better place in the forms. Figured I would post on this form first since it is more often then not the best place I have seen with reliable solutions on a normal bases.

---

### Post by gobbledigook on 2010-08-19
not sure if this is in the right direction but... maybe you need to check the [**_library path_**](http://tovid.wikia.com/wiki/Installing_svn_ffmpeg_on_a_Debian_based_distro#check_the_library_path)?

also did you compile from source for a specific reason? maybe if you just cleaned out ffmpeg and started over it may work ?

and have you considered symbolic links from /usr/bin/ ?

---

### Post by rgibbs421 on 2010-08-19
I will have to post the details of the information this afternoon when I get home, but half the lib are loading right and about 5 are not as far as clipbucket is reporting. 

The reason I compiled it from source was just trying to do something else since the easy way didn&#8217;t work. 

I have tried the linking but I am not sure I&#8217;m doing that right. I have gone to the extent of copying everything to those directories. But when compiled it creates a lot of files and directories. When I get to the house I will post the details of the status report from clipbucket and the location of the compiled ffmpeg.

---

### Post by rgibbs421 on 2010-08-19
Okay here are the stats im getting off clip bucket...
[IMG]http://1d10t.com/images/stat.jpg[/IMG]
and this is a search on the hd for ffmpeg
[IMG]http://1d10t.com/images/a.jpg[/IMG]

---

### Post by gobbledigook on 2010-08-20
ok it lookslike you are almost there!

the codecs that are showing as required can be installed manually, some fromn the universe repository. the next thing i notice is that ffmpeg revision is "r0" not a good sign! and the directories are a little messy... 

i have no idea how to fix it... all i can suggest is to remove ffmpeg (apt-get remove ffmpeg apt-get purge ffmpeg apt-get autoremove) and the source files and directories you have created compiling from source... and tehn start over! if you really need the development release of ffmpeg then follow the guide in the previous link to install from svn.

---

### Post by rgibbs421 on 2010-08-20
Oh I really screwed it up yesterday lol after doing that search and there being crap all over the place i decided to manually remove everything. wow that was a mistake now apt get install don't work... LOL what a noob. Okay screw it now that I got some one looking at what im doing im just going to make a new vm so everything is fresh I I think I screwed something up installing and removing ffmpeg 20 times. Give me a day or two to get it up. I think the symbolic link would really be the best answer but like you said I couldn't get that r0 to change no matter what i did but I have broke the repository stuff now too.

---

### Post by rgibbs421 on 2010-08-21
Okay fresh ubuntu install apache php mysql webmin phpadmin and ffmpeg with an installed clipbucket

[IMG]http://1d10t.com/images/1.jpg[/IMG]

[IMG]http://1d10t.com/images/2.jpg[/IMG]


its really funny that the first line in server stats on the clip bucket was uable to find the ffmpeg path before i installed ffmpeg. but after i installed ffmpeg it was able to find the path although the ubuntu search is just picking up gstream. i also took the first req lib libxvid searched in the synaptics package manager and installed the three files that it found. but this did not change the output of the server stats page. its clean install less then 48 hours old

---

### Post by rgibbs421 on 2010-08-22
Oh Oh here is another question... installed ffmpeg using synaptics package manager and looking for the version of it... heres a screen shot.

[IMG]http://1d10t.com/images/3.jpg[/IMG]

---

### Post by FakeOutdoorsman on 2010-08-22
Your FFmpeg version is SVN-r0.5.1-4:0.5.1-1ubuntu1. Clipbucket is probably expecting a more standard FFmpeg version, so it displays r0 by mistake.  I have no experience with Clipbucket, but if you want the encoders in red (libxvid, libx264, etc) to be enabled in FFmpeg, then see:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by rgibbs421 on 2010-08-22
Well i got ffmpeg upgraded with that post thank you

FFmpeg version SVN-r24870, Copyright (c) 2000-2010 the FFmpeg developers

but clip bucket still reporting that r0 lol okay im about tiered of clip buck im going to see what other you-tube clone cms are out there.

---

