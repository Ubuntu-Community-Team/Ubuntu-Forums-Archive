---
title: "How to convert movies to 3gp (mobile phones)"
date: 2006-07-14
forum: Tutorials
---

### Post by Zhukov on 2006-07-14
Hi there!

I've managed to develop a small app in Mono to convert movies from flv, avi and mpeg to 3gp.

[CENTER][IMG]http://ubuntuforums.org/attachment.php?attachmentid=12740&stc=1&d=1152928765[/IMG][/CENTER]

It has a script for Ubuntu (install-ubuntu) and another one just to compile the program (make).

Be advised that after running install-ubuntu you must sudo dpkg -i <ffmpeg.deb name> 

Feel free to post your comment and request features!

Enjoy!

Download:
[3gp Creator 2]("http://www.box.net/public/ubkgxi61ym")

[FFmpeg deb]("http://www.box.net/public/mjnbyec3om")

---

### Post by hellmet on 2006-07-15
well..gr8 one man!!
but can we have a .deb package??
that wud be much more confortable!!
I still have not installed it..
I need to install more packages to 'make' it..
thnkx

---

### Post by buildid on 2006-07-15
thanks i have installed and convert a file ill get this output :

Got filename /home/buildid/converting/omzetten/bbbb3.avi
Arguments are  -i /home/buildid/converting/omzetten/bbbb3.avi -ab 56 -ar 2205 0 -b 500  -s 320x240 /home/buildid/converting/omzetten/bbbb3.mpg
FFmpeg version SVN-r5754, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-amr_nb --enable-amr_wb
  libavutil version: 49.0.0
  libavcodec version: 51.10.0
  libavformat version: 50.5.0
  built on Jul 15 2006 20:51:57, gcc: 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
Input #0, avi, from '/home/buildid/converting/omzetten/bbbb3.avi':
  Duration: 02:05:02.7, start: 0.000000, bitrate: 782 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 576x320, 23.98 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 32 kb/s
Output #0, mpeg, to '/home/buildid/converting/omzetten/bbbb3.mpg':
  Stream #0.0: Video: mpeg1video, yuv420p, 320x240, q=2-31, 500 kb/s, 23.98 fps( c)
  Stream #0.1: Audio: mp2, 22050 Hz, stereo, 56 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
[mpeg1video @ 0x83f7a44]warning, clipping 1 dct coefficients to -255..255
frame=179886 q=1.6 Lsize=  514214kB time=7502.7 bitrate= 561.5kbits/s
video:457847kB audio:51288kB global headers:0kB muxing overhead 0.997465%
FFmpeg version SVN-r5754, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-amr_nb --enable-amr_wb
  libavutil version: 49.0.0
  libavcodec version: 51.10.0
  libavformat version: 50.5.0
  built on Jul 15 2006 20:51:57, gcc: 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
bbbb3.mpg: I/O error occured
Usually that means that input file is truncated and/or corrupted.
Error
/bin/rm: kan `bbbb3.mpg' niet verwijderen: Onbekend bestand of map



The file is converted to mpg and does excist , quality is pretty good , still i see an error message i dont understand .....

---

### Post by loell on 2006-07-15
same here..

---

### Post by buildid on 2006-07-15
so i did it again second time , this time i succeed...

a file name with a space into the name is not what ffmpg like 
if it fails , drag the file again into the gui without closing it ..

---

### Post by Zhukov on 2006-07-16
Well, i cant do much about the space issue.
I'll add a notification of sucess or failure.

I'll also look in the deb issue as soon as i can.

Glad someone found it usefull :D

Regards!

---

### Post by buildid on 2006-07-17
how about encoding to mp4 a new option included into the gui ?
would be nice

mobile phone playing ,mp4 not 3gp :-(

---

### Post by Zhukov on 2006-07-17
Ok, i'll try to fix all the issues tomorow morning, including the mp4 one.

Regards!

---

### Post by buildid on 2006-07-18
thanks great

---

### Post by Zhukov on 2006-07-18
Ok, i managed it! :D FFmpeg was a pain in the ***
I made the debs, it is only missing the 3gp converter deb but im too tired now. Ill post them tomorrow (if i can) or Thursday after lunch (i have an exam), just wanted to say something to you guys!

Anyway, iPod user out there, i believe there is a better tool with a lot of options:

[http://ubuntuforums.org/showthread.php?t=114946](http://ubuntuforums.org/showthread.php?t=114946)

---

### Post by Zhukov on 2006-07-21
Updated!

---

### Post by dvarsam on 2006-08-01
Very good idea!

But I would like to be able to do the _opposite_ too!

Example:
I have a Nokia phone.
I have taken some .3gp videos with it.
I would like to convert them from .3gp to other format, so that I can watch them in my PC (Windows or Linux).

Can you upgrade your program to do the opposite too?

Thanks.

P.S.> By the way: to use programs that do this in the Windows world, you have to pay $20! It would be great if somebody could do this in Linux for free!

---

### Post by Zhukov on 2006-08-03
It is possible, but you'll have to wait a bit because right now I am in Slovakia and my network acess is limited. They promissed me a decent one. I will shout a little bit more with them. :D

---

### Post by fago on 2006-09-20
great work, thanks.

I would also be interested in playing 3gps with sound, which have been produced by nokia mobile phones.

How can I get mplayer or totem to use this ffmpeg deb? Do I have to compile then again?

---

### Post by Zhukov on 2006-09-20
Thanks!
I dont have it installed now (had to format) but i believe i've managed to play sound, somehow. Ill install it again tomorrow and ill give it a try.

Cheers!

---

### Post by lorddaddy84 on 2006-11-08
Could someone please tell me how to use this, thanks.

---

### Post by Zhukov on 2006-11-10
I really have to get my hands back on this :D
Anyway, what exactly do you want to know?

If you just want to convert media try this in the meanwhile:

[http://media-convert.com/convert/index.php](http://media-convert.com/convert/index.php)

Anyway, if you want some extras features just request them :)

---

### Post by A-Dream on 2006-11-23
Hm I tried to download it but i can't download the deb files... they are no longer available. What is the problem?

---

### Post by Zhukov on 2006-11-23
Yes, I know. I was stupid enough to delete some folders by accident.
Not so bad as the day I erased 30Gb of data.

I'll fix it as soon as possible.

---

### Post by A-Dream on 2006-11-23
Please post it here as soon it's back online :)

---

### Post by sabitha on 2006-11-25
then how to remove ??

---

### Post by Zhukov on 2006-11-27
Sorry? How to remove? Just search in Synaptic for the packages you installed and replace them with the version in the repos.

---

### Post by A-Dream on 2006-11-28
How long will it take before the deb files are online again?

---

### Post by Zhukov on 2006-11-29
[http://student.dei.uc.pt/~jpoa/Packages_3gp/ffmpeg_3.cvs20060718-1_i386.deb](http://student.dei.uc.pt/~jpoa/Packages_3gp/ffmpeg_3.cvs20060718-1_i386.deb)

[http://student.dei.uc.pt/~jpoa/Packages_3gp/ffmpeg_3.cvs20060718-1_i386.deb](http://student.dei.uc.pt/~jpoa/Packages_3gp/ffmpeg_3.cvs20060718-1_i386.deb)

Be advised, this is for DAPPER only.

I have to make new packages.

Sorry for the late reply!

---

### Post by jeegiz on 2006-12-03
i get 403 Forbidden, if i try to download your ffmpeg :-k

---

### Post by Zhukov on 2006-12-03
I'm sorry, it was a permission problem, solved!
Thanks for pointing it out!

---

### Post by svitj on 2006-12-19
Thanks!

It works perfectly! :)

---

### Post by cbudden on 2006-12-19
When I click the link you provided in the first post, I get this error :
No shared files/folders found.
Please email [email]support@box.net[/email] for support

Does anyone have a mirror?

edit.  Noticed the attachment in the first post :P

---

### Post by Zhukov on 2006-12-21
:S I'm really sorry for the lack of updates here but I've been somewhat busy.
I'm hoping to format my computer before Christmas and continue developing this as soon as possible.

Regards.

---

### Post by gmatt on 2006-12-29
> **dvarsam said:**
> Very good idea!

But I would like to be able to do the _opposite_ too!

Example:
I have a Nokia phone.
I have taken some .3gp videos with it.
I would like to convert them from .3gp to other format, so that I can watch them in my PC (Windows or Linux).

Can you upgrade your program to do the opposite too?

Thanks.

P.S.> By the way: to use programs that do this in the Windows world, you have to pay $20! It would be great if somebody could do this in Linux for free!

The GUI that was written here is nothing more than a wrapper around the ffmpeg program. To do the reverse is actually just as easy if not easier, that is to convert 3gp->mpg or avi or whatever is. ffmpeg is actually an extremely powerful video stream editing program, but it is all command line, so it's somewhat hard to grasp. 

Here is sample code to convert 3gp->avi with ffmpeg:
```
ffmpeg -i input.3gp -f avi -vcodec xvid -acodec mp3 output.avi
```
actually you can do much more cooler things if you actually take time to learn a little about how mplayer/ffmpeg actually works, though I don't blame you if you don't, its all very complicated.

---

### Post by amoore on 2007-01-08
Please make an edgy packages!!!! Please, please, please....

---

### Post by dvarsam on 2007-01-20
Hello!

And thanks for the good work!

[QUOTE=Zhukov][http://student.dei.uc.pt/~jpoa/Packages_3gp/ffmpeg_3.cvs20060718-1_i386.deb](http://student.dei.uc.pt/~jpoa/Packages_3gp/ffmpeg_3.cvs20060718-1_i386.deb)
[http://student.dei.uc.pt/~jpoa/Packages_3gp/ffmpeg_3.cvs20060718-1_i386.deb](http://student.dei.uc.pt/~jpoa/Packages_3gp/ffmpeg_3.cvs20060718-1_i386.deb)

Be advised, this is for DAPPER only.
I have to make new packages.[/QUOTE]

I downloaded the package provided on your above 1rst link.
When I tried to install it (on my Ubuntu Edgy), I got a message saying "something" similar to this:

[quote=dvarsam]A newer package than "**ffmpeg_3.cvs20060718-1_i386.deb**" exists in the Repos.[/quote]
So, I searched in Synaptic & found this:

**ffmpeg_3%3a0.cvs20060823-3.1ubuntu1_i386.deb**

So, by comparing those 2 dates, I realized that the later is a newer version & decided to install that one...
Then I realized the following:

1. No shortcut/link was created/added in my Ubuntu's menus!
2. You can only run the program from the Terminal (i.e. there is _no_ GUI launching/appearing like the pretty picture you attached on your starting post in this thread... :confused:

I then tried to use the Terminal to achieve what I wanted - e.g. _convert_ **.3gp->.ogg** by using the following command:

[quote=dvarsam]ffmpeg -i Video000.3gp -f ogg -vcodec xvid -acodec mp3 Video001.ogg[/quote]

And got the following results:

[quote=dvarsam]dimitris@dimitris-desktop:~/Desktop$ ffmpeg -i Video000.3gp -f ogg -vcodec xvid -acodec mp3 Video001.ogg
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Sep 20 2006 00:26:15, gcc: 4.1.2 20060906 (prerelease) (Ubuntu 4.1.1-13ubuntu2)

Seems that stream 0 comes from film source: 15750.00 (15750/1) -> 15.50 (31/2)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'Video000.3gp':
  Duration: 00:00:06.0, start: 0.000000, bitrate: 1975 kb/s
  Stream #0.0(eng): Video: mpeg4, yuv420p, 640x480, 15.50 fps(r)
  Stream #0.1(eng): Audio: samr / 0x726D6173, 8000 Hz, mono
**Unknown codec 'xvid'**[/quote]

What is wrong?
Why does the last line state **unknown codec 'xvid'**?
What do I do to fix it?

Thanks.

P.S.> Sorry, but I just used an example that was given in Page 3 of this Thread, changed it a bit & then applied it...

---

### Post by claypole on 2007-02-12
I haven't tried this yet but it should help... [http://blogger.rukker.org/2007/01/29/enable-mp3-and-amr-support-in-ffmpeg-ubuntu-edgy-eft/](http://blogger.rukker.org/2007/01/29/enable-mp3-and-amr-support-in-ffmpeg-ubuntu-edgy-eft/)
:)

---

### Post by benmau5 on 2007-10-16
can you re upload the links for the software it says there old.....and im trying to convert the file to 3gp for ringtones.....is this the right page?

---

### Post by Zhukov on 2007-10-17
:S Been so busy lately that I completely forgot this...

I have no idea on the status of the ffmpeg in the repos now, but I belive that now it only matters to create a package for gutsy, right?

Sorry for the delay guys!

---

### Post by mbhavaraju on 2008-08-21
Please Help.. What am I doing wrong? I am using Hardy.



~/Desktop$ ffmpeg -i SSPX0012.3g2 -f mp4 -vcodec mpeg4 -acodec mp3 SSPX0012.MP3
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:21:25, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'SSPX0012.3g2':
  Duration: 00:02:00.7, start: 0.000000, bitrate: 393 kb/s
  Stream #0.0(eng): Video: mpeg4, yuv420p, 320x240, 30.00 fps(r)
  Stream #0.1(eng): Audio: mp4a / 0x6134706D, 8000 Hz, stereo
File 'SSPX0012.MP3' already exists. Overwrite ? [y/N] y
Output #0, mp4, to 'SSPX0012.MP3':
  Stream #0.0: Video: mpeg4, yuv420p, 320x240, q=2-31, 200 kb/s, 30.00 fps(c)
  Stream #0.1: Audio: mp3, 8000 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
**Unsupported codec (id=86043) for input stream #0.1**

Thanks in Advance...

---

### Post by HungryMan on 2008-08-26
> **mbhavaraju said:**
> Please Help.. What am I doing wrong? I am using Hardy.



~/Desktop$ ffmpeg -i SSPX0012.3g2 -f mp4 -vcodec mpeg4 -acodec mp3 SSPX0012.MP3
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:21:25, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'SSPX0012.3g2':
  Duration: 00:02:00.7, start: 0.000000, bitrate: 393 kb/s
  Stream #0.0(eng): Video: mpeg4, yuv420p, 320x240, 30.00 fps(r)
  Stream #0.1(eng): Audio: mp4a / 0x6134706D, 8000 Hz, stereo
File 'SSPX0012.MP3' already exists. Overwrite ? [y/N] y
Output #0, mp4, to 'SSPX0012.MP3':
  Stream #0.0: Video: mpeg4, yuv420p, 320x240, q=2-31, 200 kb/s, 30.00 fps(c)
  Stream #0.1: Audio: mp3, 8000 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
**Unsupported codec (id=86043) for input stream #0.1**

Thanks in Advance...

not sure if this is the right place to say this,but i'm getting this too, im using medibuntu's ffmpeg... it converts flv to mpg, but not anything to 3gp OR mp4.

---

### Post by sneeks on 2008-12-08
you could always try winff..

---

### Post by Zhukov on 2009-02-25
I'm really tempted to get my hands back on this project if there are interested users...

Feedback?

Best regards!

---

### Post by rtom on 2009-04-08
Since I'm not familiar with ffmpeg in command line, I'd like to have some easy to use converter (especially into 3gp), with gui - so go on please!;)

---

### Post by imnotjack on 2011-03-10
Interested in making a maverick distro?. I'm getting pretty mad at everything else I'm trying... Please post here when its ready... I get 404 not found on the ones you already have.

Thanks,
John

---

### Post by morean51 on 2011-03-11
thank you for the application info

---

### Post by rejimbbs on 2011-04-10
I could not install the 3gp convertor properly. when I run        ./installer_ubuntu.sh
after extracting the files following error message appears at the end
"Package mono is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source"

Is there any solution?
 
Thanks in advance

---

### Post by TossTheTV on 2011-04-10
Yes, download Arista Transcoder. In Software Manager I think or get-deb.net. It's amazing! Better than Handbrake or Transmageddon! 
And supports Ipod, phone, netbook presets, etc:popcorn:

[http://www.transcoder.org/presets/](http://www.transcoder.org/presets/)

---

### Post by fredypost on 2011-12-24
for Ubuntu 10.4 with simple GUI works:  [http://www.miksoft.net/mobileMediaConverterUbuntu.htm](http://www.miksoft.net/mobileMediaConverterUbuntu.htm)

---

