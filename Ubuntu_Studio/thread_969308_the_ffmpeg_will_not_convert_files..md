---
title: "the ffmpeg will not convert files."
date: 2008-11-03
forum: Ubuntu Studio
---

### Post by KanineN on 2008-11-03
Hello! I have just installed ffmpeg on my new computer because my other was broke. I used the

```
sudo apt-get install ffmpeg
```

but when I want to convert a file

```
ffmpeg -i ole.mpg -b 500k -s 320x240 ole.mp4
```

i get this message 

```
Input #0, mpeg, from 'ole.mpg':
  Duration: 00:29:48.2, start: 0.213367, bitrate: 1388 kb/s
    Stream #0.0[0x1e0]: Video: mpeg1video, yuv420p, 320x240 [PAR 1:1 DAR 4:3], 1150 kb/s, 29.97 tb(r)
    Stream #0.1[0x1c0]: Audio: mp2, 44100 Hz, stereo, 224 kb/s
Output #0, avi, to 'ole.avi':
    Stream #0.0: Video: 0x0000, yuv420p, 320x240 [PAR 1:1 DAR 4:3], q=2-31, 200 kb/s, 29.97 tb(c)
    Stream #0.1: Audio: mp2, 44100 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec for output stream #0.0
```

So can someone please give me a codec so I can convert files.

---

### Post by Cresho on 2008-11-04
use winff.  ffmpeg has been going through some changes and commands are changed as well.  You may be envoking wrong commands.

this last line tells you that you are envoking the wrong command.  you are either using outdated sources or new sources for envoking commands.

Unsupported codec for output stream #0.0

the old winff had tons of pre configured paramaters, it uses ffmpeg.  the new winff uses newer paramaters but is less and few since it needs people to create more templates for it.

---

### Post by Cresho on 2008-11-04
ohh and another thing, you are missing lots more.

ffmpeg -i ole.mpg -b 500k -s 320x240 ole.mp4

change to

xvid ipod
ffmpeg -i ole.mpg -r 29.97 -croptop 58 -cropbottom 62 -vcodec xvid -s 320x240 -aspect 2.35 -maxrate 1500k -b 500k -qmin 3 -qmax 5 -bufsize 4096 -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -g 300 -acodec aac -ar 48000 -ab 80k -ac 2 ole.mp4

you may need to configure it yourself.  or more simplified

ffmpeg -i ole.mpg -r 24 -vcodec xvid -s 320x240 -aspect 4:3 -maxrate 600k -acodec mp3 -ab 128k -ac 2 -ar 44100 ole.mp4


in your line, you are missing alot of stuff.

---

### Post by nowardev on 2008-11-04
nope cresho 

he has compiled bad ffmpeg he has not xvid enabled that's

---

### Post by KanineN on 2008-11-04
How do I install winff? I cant find the deb pack anywhere!


EDIT: Found it! :D But now when I want to convert I get a wrong message. I can unfortunately not copy the wrong message text. But it says that it doesn'y have the encoder. And that is with every format.

---

### Post by Cresho on 2008-11-04
winff uses it's built in ffmpeg.  It does not use the systems ffmpeg.  it has everything enabled.

try uninstalling the one you are using , delete your .winff directory and reinstall this one.

winff-0.42-i386.deb
[http://code.google.com/p/winff/downloads/detail?name=winff-0.42-i386.deb&can=2&q=](http://code.google.com/p/winff/downloads/detail?name=winff-0.42-i386.deb&can=2&q=)

or 64bit

winff-0.42-amd64.deb
[http://winff.googlecode.com/files/winff-0.42-amd64.deb](http://winff.googlecode.com/files/winff-0.42-amd64.deb)
this older version has tons of presets.

---

### Post by nowardev on 2008-11-05
man on windows maybe on linux winff install ffmpeg and if you have not medibuntu open or you have compiled,bad like in this case,  with your hand ffmpeg winff doesn't work...

---

### Post by Cresho on 2008-11-05
> **nowardev said:**
> man on windows maybe on linux winff install ffmpeg and if you have not medibuntu open or you have compiled,bad like in this case,  with your hand ffmpeg winff doesn't work...

OHH CRAP, YOUR RIGHT!  i just stripped the deb file and couldnt locate ffmpeg.

this guys ffmpeg needs to be uninstalled and updated from medibuntu.  I just wish I had that link to fix the issue.

in anycase, he can download the correct binary files and use the specific location and have winff use those instead of the ones on his pc.  But then it wouldnt fix the problem since other softwares use ffmpeg from the pc.

---

### Post by nowardev on 2008-11-05
and i have to say more....

on intrepid there IS NOT  ffmpeg with restricted formats enabled even if you use medibuntu :)

that's why my slideshow software crash :( and ffmpeg interface doesn't works 
luckly i have made mencoder and ffmpeg2theora gui too xD

---

### Post by KanineN on 2008-11-05
yea, but how do I fix this problem? 

when i try

```
sudo apt-get uninstall ffmpeg
```

it doesn't work at all.

---

### Post by nowardev on 2008-11-05
1 you try to compile ffmpeg
2 wait for medibutu in intrepid
or install some mencoder gui

---

### Post by Cresho on 2008-11-05
are you on intrepid?

---

### Post by KanineN on 2008-11-06
yes, I use ubuntu 8.10 intrepid.

---

### Post by mr_pouit on 2008-11-06
> **nowardev said:**
> 
2 wait for medibutu in intrepid


FFmpeg won't be added in medibuntu for intrepid, as there is already a ffmpeg variant with many codecs enabled in multiverse. You need to install the following packages:
* libavcodec-unstripped-51
* libavdevice-unstripped-52
* libavformat-unstripped-52
* libavutil-unstripped-49
* libpostproc-unstripped-51
* libswscale-unstripped-0

And you should be able to convert your file.

---

### Post by KanineN on 2008-11-06
ok, do you know the command line to install all these?

---

### Post by cesera on 2008-11-07
That would be:

```
sudo apt-get installlibavcodec-unstripped-51 libavdevice-unstripped-52 libavformat-unstripped-52 libavutil-unstripped-49 libpostproc-unstripped-51 libswscale-unstripped-0

```

---

### Post by KanineN on 2008-11-10
I have just installed the package but it still won't work.

---

### Post by alexeix on 2008-11-10
I want to install WinFF on Mythbuntu 64, but I can't find a link at the download page ([http://code.google.com/p/winff/downloads/list](http://code.google.com/p/winff/downloads/list)).

Which one do I need?

Need to convert some mpeg files to avi, so I can stream them to my Xbox.

Also, are there any 'dummies' installation guides?

Thanks.

---

### Post by alexeix on 2008-11-10
Okay, I found and tried the correct method to install (see [http://code.google.com/p/winff/wiki/UbuntuInstallation](http://code.google.com/p/winff/wiki/UbuntuInstallation)), but cannot get WinFF to install on Mythbuntu 64.

I followed all the steps, but it is not available in Package Manager.

Can anyone advise on this please?  Do I need to do something else for Winff to install correctly?

Have spent a few hours trying various things, with no success.

I installed the Windows version to get things moving with my conversions and didn't have any trouble...

Thanks in advance.

---

### Post by alexeix on 2008-11-10
Hold on...I checked the menu and there's an entry for "Video convertor (WinFF)".  There's no icon, but it does run.

I'm glad it's working, but why no icon and why doesn't it appear in the package list?

:confused:

---

### Post by alexeix on 2008-11-11
Turned on the PC today and the icon appears in the menu.

Unfortunately, WinFF can't seem to encode my files.  I'm trying to convert  mpeg to AVI (xvid) or WMV.

Can anyone help with this as it just doesn't seem to work?!

I'm on Ubuntu 8.10.

This just seems to be much more hassle than it should be.

---

### Post by FakeOutdoorsman on 2008-11-11
> **alexeix said:**
> Turned on the PC today and the icon appears in the menu.

Unfortunately, WinFF can't seem to encode my files.  I'm trying to convert  mpeg to AVI (xvid) or WMV.

Can anyone help with this as it just doesn't seem to work?!

I'm on Ubuntu 8.10.

This just seems to be much more hassle than it should be.
WinFF should have appeared immediately in the menu.  You should have supplied us with any errors WinFF/ffmpeg are giving you.  You can see them in WinFF by going to Options -> Display CMD Line.  Also show the full output of:
```
ffmpeg -formats
```

---

### Post by alexeix on 2008-11-12
Hi,

Sorry for not posting the errors; they related to the codec, e.g. "unknown codec - WMV".

I'm not at my Ubuntu box right now, but it was definitely an 'unknown codec' message and I couldn't find any file types that didn't give me such a warning.

Hope that helps.

I want to convert from .mpg to .avi or .wmv, so do I need to install something else?

Thanks.

---

### Post by alexeix on 2008-11-12
The exact error when attempting to convert from mpg to avi (MS compatible AVI), is:

warning: the bitrate parameter is set too low. It takes bits/s as argument, not kbits/s
unknown encoder 'msmpeg4v2'


If I try converting to AVI - 'XviD in AVI (16:9 Anamorphic)', the error is:

unknown encoder 'libxvid'.


See attached screenshot for an example...

---

### Post by FakeOutdoorsman on 2008-11-12
The WinFF presets you are using were designed for a newer version of ffmpeg than what you are using.  Open a terminal and paste the full output of:
```
ffmpeg -formats
```
This will help determine what to rename the WinFF preset parameters to work with your ffmpeg version.

---

### Post by alexeix on 2008-11-12
Here you go:

See attachment.

---

### Post by FakeOutdoorsman on 2008-11-12
You need to install the "unstripped" versions of some packages that provide restricted formats.

Using a terminal:
1. Uninstall ffmpeg and WinFF
```
sudo aptitude purge ffmpeg winff
```
2. Install ffmpeg with the unstripped codec libraries.
```
sudo aptitude install ffmpeg libavcodec-unstripped-51 libavdevice-unstripped-52 libavformat-unstripped-52 libavutil-unstripped-49 libpostproc-unstripped-51 libswscale-unstripped-0
```
3. Reinstall WinFF and the presets should work.

You can do the same as above in Synaptic Package Manager if you prefer.

---

### Post by alexeix on 2008-11-12
Thanks.

Converting to MS Compatible AVI still fails.


However, conversion to XviD in AVI (16:9 Anamorphic) starts processing.  I'll leave it running overnight and see what I get in the morning.

I'm not sure if that file will stream successfully to an Xbox, but we'll see.

---

### Post by alexeix on 2008-11-13
The suggestion did fix the problem with WinFF and it produced files which could be streamed to the Xbox, however, it also removed the streaming capability - which I'd originally added by following this process: 

[http://ubuntuforums.org/showthread.php?t=848144](http://ubuntuforums.org/showthread.php?t=848144)

Subsequently, I had to remove Ushare in the package manager and add it again, so I could stream the converted files, but now I'm back where I started - I can't convert any more files (not unexpectedly).

Is there a solution to this issue?

Alternatively, is there an alternative conversion application with a GUI?

I tired Avidemux, but that was unsuccessful for playback on the Xbox.

---

### Post by KanineN on 2008-11-28
is there still not any good video converters for ubuntu 8.10? :(

Sorry becuase of the delay of answering but because of sickness and studies I didn't find any time.

---

### Post by alexeix on 2008-12-05
I'm still using the workaround. :(

Another issue is that the converted files have the top and bottom of the picture cut off.  
The 'convert to' is XviD in AVI (16:9 Anamorphic), so I thought it would have filled the TV screen.

---

### Post by pt123 on 2009-01-23
anyone still able to install an unstripped version of ffmpeg?

---

### Post by StevenHarper on 2009-07-11
The winff application in the standard repository was not working with the error

```
Unknown encoder 'libxvid'
```

However after installing these 2 packages, ffmpeg could then re-encode files.

```
sudo apt-get install libxvidcore4
sudo apt-get install libavcodec-unstripped-52
```

Good Luck

---

