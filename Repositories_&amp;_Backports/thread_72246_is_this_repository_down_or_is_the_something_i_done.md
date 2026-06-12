---
title: "is this repository down or is the something i done wrong??"
date: 2005-10-05
forum: Repositories &amp; Backports
---

### Post by tomski on 2005-10-05
when ever i load up synaptic or try apt-get update i get these messages  ;

[ftp://ftp2.caliu.info/backports/dists/hoary-backports/main/binary-i386/Packages.gz:](ftp://ftp2.caliu.info/backports/dists/hoary-backports/main/binary-i386/Packages.gz:) Unable to fetch file, server said ‘Failed to open file.  ’
[ftp://ftp2.caliu.info/backports/dists/hoary-backports/universe/binary-i386/Packages.gz:](ftp://ftp2.caliu.info/backports/dists/hoary-backports/universe/binary-i386/Packages.gz:) Unable to fetch file, server said ‘Failed to open file.  ’
[ftp://ftp2.caliu.info/backports/dists/hoary-backports/multiverse/binary-i386/Packages.gz:](ftp://ftp2.caliu.info/backports/dists/hoary-backports/multiverse/binary-i386/Packages.gz:) Unable to fetch file, server said ‘Failed to open file.  ’
[ftp://ftp2.caliu.info/backports/dists/hoary-backports/restricted/binary-i386/Packages.gz:](ftp://ftp2.caliu.info/backports/dists/hoary-backports/restricted/binary-i386/Packages.gz:) Unable to fetch file, server said ‘Failed to open file.  ’


and  ;

W: Couldn't stat source package list [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-backports/main Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-backports/universe Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)


have i entered them in correctly or are they down


here is my current sources.lst

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse universe main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted


#Hoary-Extras
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main universe multiverse restricted




deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted 
# [http://acm.cs.umn.edu/ubp/](http://acm.cs.umn.edu/ubp/)
#deb [http://mirror.brianpuccio.net/ubuntu...ts-repository/](http://mirror.brianpuccio.net/ubuntu...ts-repository/) hoary-backports main universe multiverse restricted
#deb [http://mirror.brianpuccio.net/ubuntu...ts-repository/](http://mirror.brianpuccio.net/ubuntu...ts-repository/) hoary-extras main universe multiverse restricted

---

### Post by Mustard on 2005-10-05
I'm wondering whether the ftp2.caliu links are mirrors of the old unofficial backports which has been shut down.

---

### Post by tomski on 2005-10-06
thats what i thought.

i also cant get transcode or sun java so alot of the apps i want are out of reach.

i wish there was a list that was daily updated with all current working repositoiers instead of having to go through the forum digging for hours

---

### Post by commodore on 2005-10-06
I'm having the same problem.

---

### Post by commodore on 2005-10-06
Please help. I'm a linux n00b.

---

### Post by spectre013 on 2005-10-06
We have Verio for an ISP and I am unable to get to ubunto.com or the repositories as well. 

Is there any mirrors out there for repositories?

Cause as it stands right now I can get any updates or packages.

---

### Post by tomski on 2005-10-06
i wish i could help but i cant find anything thats why im posting here
with a bit of luck we should get some help

---

### Post by Mustard on 2005-10-06
I would comment out or even remove those entries completely and find an alternative location to source whatever application it is you are after.

This list here has an example of a current source.list for Hoary Hedgehog.

[http://paste.ubuntulinux.nl/969](http://paste.ubuntulinux.nl/969)

I would consider the last entry (shown below) in the above example as redundant.

## hoary-extras - the most widely used source for packages not includded in Ubuntu
## no guarantees on working - not enabled by default
#deb [http://public.planetmirror.com/pub/ubuntu-backports/](http://public.planetmirror.com/pub/ubuntu-backports/) hoary-extras main universe multiverse restricted

P.S.

I would add that if you fire up XChat and hop on the Ubuntu IRC channels, help is available there as well.

---

### Post by jdong on 2005-10-06
The warning on official (Archive.ubuntu.com) hoary-backports is very harsh -- we do great amounts of QA on all our packages, and the Backports packages are as great in quality as any Ubuntu package. In fact, it *IS* an official Ubuntu package -- ALWAYS.

---

### Post by malacoda on 2005-10-06
I too am having the same problem.  All was fine with Hoary.  I upgraded to Breezy about 2 weeks ago; everything still fine for first week.  Then, after not having booted into linux for about a week I booted up - into both gnome and kde desktop - and tried updating yesterday in each but received the same 'failed' errors. 

I too am a bit of a noob so don't know if it's an issue on my end, or a problem on a server side...

Anyone figure out what might be the cause and how it can be fixed?

Also, I installed all necessary kde apps necessary to switch from gnome environment to kde env. (as a noob I want to taste each an see which I prefer) - e.g. made the switch to Kubuntu within Breezy.  When I was running a kde desktop on gnome AND now in the pure kubuntu environment my desktop background crashes and corrupts my display as I cycle through any open panels.  Any thoughts anyone?

Learning but confused,
Malac

---

### Post by jdong on 2005-10-06
Open up /etc/apt/sources.list with a text editor under sudo, then seach for all instances of "backports" and "extras", remove the lines.

---

### Post by spectre013 on 2005-10-07
I am not sure if this is the problem or not but I cant get to the archives from work but I can from home. The only difference is the path to the archives goes the level3's network from home and Cogent at work. These 2 networks are currently not letting each others traffic travel across each others networks.

Here is an article from CNet [Internet Blackout]("http://news.com.com/Blackout+shows+Nets+fragility/2100-1038_3-5890424.html?tag=nefd.lede")

---

### Post by John.Michael.Kane on 2005-10-07
well im inthe same boat with the repo's error's out the door on that.. i hope it will be corrected..

---

### Post by commodore on 2005-10-08
I can't do so many things right now. Ubuntu is almost useless in the moment for me.

---

### Post by aysiu on 2005-10-08
Until we get out of the weird transitional period before Breezy gets released, I put together some instructions for enabling extra repositories for both Breezy and Hoary:

[http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)

jdong, please let me know if you notice any errors in the repositories I list.

---

### Post by jdong on 2005-10-08
[QUOTE=aysiu]Until we get out of the weird transitional period before Breezy gets released, I put together some instructions for enabling extra repositories for both Breezy and Hoary:

[http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)

jdong, please let me know if you notice any errors in the repositories I list.[/QUOTE]

For your 5.04 list, 

```

deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted 
```
Is still valid.

For 5.10, the following repository is available but empty as of now:
```

[code]
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main universe multiverse restricted 
```
[/code]

breezy-backports on archive.ubuntu.com is still under development.

---

### Post by Efwis on 2005-10-08
I'm glad I found this topic, I was looking everywhere to fix this issue. The original announcement thread I read earlier didnt' work for me. after going to Aysiu's webpage there, it is working great.

Now on to getting ready to install breezy next week. Great work gang keep it up :)

---

### Post by larry_steiner on 2005-10-08
Thanks for the script.  I know I jumped the gun and installed B.B.  pre release.  But the Unofficial How to under System >Help  did not work correctly when adding repository.  Most got 404 not found.  Ubuntu is not much use if you can't install all the apps like multi media.

But hay.  It's free, it's software and digging around is part of the fun.

Thanks again.
Larry

---

### Post by tomski on 2005-10-10
i have tried various others but to no avail ie:
mirrormax, marliet, and someone's own repo
but non work all i want is transcode and the sun java and a few other apps but just cant get them other than that its a great os i even used the first issue not much content but very stable i prefer ubuntu to kanotix,
as soon as i get the software i need for my normal use i will ditch Mikewrong Shafted&#169; Windblows&#169; altogether

---

### Post by tomski on 2005-10-10
thing seem to be getting confusing as im reading alot on this thread about breezy;
the last thing i want to do is think about dist upgrades i cant get hoary to function how i want it too unless i can use the repo's for breezy i think those posts are slightly off topic!!!


no offence but im trying to fix a problem not create a whole bunch of different ones

---

### Post by glug101 on 2005-10-10
[QUOTE=tomski]thing seem to be getting confusing as im reading alot on this thread about breezy;
the last thing i want to do is think about dist upgrades i cant get hoary to function how i want it too unless i can use the repo's for breezy i think those posts are slightly off topic!!!


no offence but im trying to fix a problem not create a whole bunch of different ones[/QUOTE]

Yeah, things like that will creep in sometimes in a thread.  I'd ignore the chatter as best as possible if I were you.  My experience on this thread is that most of the people here just want to help and some (like myself) find it oddly relaxing. (yeah, sounds weird even to me) ;)

In answer to your problems with transcode, I was having similar problems and just solved them last night.... although you might not like my solution if you are unfamiliar with compilling.  I compiled transcode from source.  Not for everybody, but not as hard as it sounds.  I found the key to it while I was searching other forums and found out a bizaar quirk to Ubuntu.

Before compiling transcode, compile ffmpeg first.  Turns out that transcode requires a shared version of libavencode and Ubuntu only provides a non-shared version of it.

Basically, if you would like better instructions for compiling transcode on Ubuntu Hoary, pop me up here and I'll provide them after I'm home and in front of my Ubuntu box.

Transcode may also be fixed on Breezy.  If compiling transcode sounds scarey, then I would consider the dist upgrade approach.  It looks pretty easy, though I have not tried it yet. (I'll be trying it either tomorrow or on thursday ;) )

Hope this helps!

---

### Post by Efwis on 2005-10-10
[QUOTE=tomski]i have tried various others but to no avail ie:
mirrormax, marliet, and someone's own repo
but non work all i want is transcode and the sun java and a few other apps but just cant get them other than that its a great os i even used the first issue not much content but very stable i prefer ubuntu to kanotix,
as soon as i get the software i need for my normal use i will ditch Mikewrong Shafted© Windblows© altogether[/QUOTE]
you won't find Sun Java on the repos, some legal thing, to get Sun Java you have to go to [Sun's download page](http://www.java.com/en/download/manual.jsp) and manually download and install it. Make sure you get the  Linux (self extracting file) not the RPM. Last I knew Ubuntu doesn't like the rpm format without having to do alien to install it.

---

### Post by tomski on 2005-10-10
thats bizarre because i got the .deb for it when i was running kanotix but ubuntu does not like it so it tells me its broken and complains when i update.   ok cheers efwis i'll do that

as for the post by glug 101 you diamond i've wondered for ages why transcode complains during compile, how can i contact you ...via personal message or other means   :KS


thanks for all help provided so far

---

### Post by markthecarp on 2005-10-10
Tomski,

I believe you can find Sun Java in the backports repository.

```
mark@smokey:~$ apt-cache show sun-j2re1.5
Package: sun-j2re1.5
Status: install ok installed
Priority: optional
Section: non-free/devel
Installed-Size: 86996
Maintainer: Ubuntu Backports Project <ubuntu-bp-devel@googlegroups.com>
Architecture: i386
Version: 1.5.0+update04
Replaces: sun-j2re1.5debian
Provides: java-common, java-virtual-machine, java-runtime, java2-runtime, java-browser-plugin, j2re1.5
Depends: libasound2 (>> 1.0.8), libc6 (>= 2.3.2.ds1-4), libx11-6 | xlibs (>> 4.1.0), libxext6 | xlibs (>> 4.1.0), libxi6 | xlibs (>> 4.1.0), libxp6 | xlibs (>> 4.1.0), libxt6 | xlibs (>> 4.1.0), libxtst6 | xlibs (>> 4.1.0)
Recommends: netbase, libx11-6 | xlibs, libasound2, libgtk1.2
Description: Java(TM) 2 RE, Standard Edition, Sun Microsystems(TM)
 The Java(TM) 2 Runtime Environment contains the Java virtual machine,
 runtime class libraries, and Java application launcher that are
 necessary to run programs written in the Java progamming language
 (this includes the Java 2 Plug-In for Netscape and Mozilla
 browsers). It is not a development environment and doesn't contain
 development tools such as compilers or debuggers. For development
 tools, see the Java 2 SDK, Standard Edition.
 .
 This package has been automatically created with java-package (0.23).


```

Note the "Maintainer:" line. I have dist-upgraded to Breezy but this package was originally installed on my system while running Hoary. Here's the lines for backports from my Hoary /etc/apt/sources.list.

```
# Backports
deb http://archive.ubuntu.com/ubuntu hoary-backports main restricted universe multiverse
# Extra
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```

Hope that helps. 

-mark

---

### Post by online14230 on 2005-10-10
I cant do JACK!
Ive been looking for the addon CD for about 4 hours now, but cant seem to find it. Any takers? I REALLY need to fing it. I cant go online using my Ububox and theres like NO functionality in barebones 5.04. Please help!!! I REALLY need this baby!!!
Brendan

---

### Post by Efwis on 2005-10-10
[QUOTE=markthecarp]Tomski,

I

Note the "Maintainer:" line. I have dist-upgraded to Breezy but this package was originally installed on my system while running Hoary. Here's the lines for backports from my Hoary /etc/apt/sources.list.

```
# Backports
deb http://archive.ubuntu.com/ubuntu hoary-backports main restricted universe multiverse
# Extra
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```

Hope that helps. 

-mark[/QUOTE]

The mirrormax backports are no longer available as they have been shut down as part of the transition to Breezy. this is how your sources.list file should look now for 5.04 Hoary.

```

## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

deb http://archive.ubuntu.com/ubuntu hoary-backports main restricted universe multiverse 
```

---

### Post by glug101 on 2005-10-10
[QUOTE=tomski]thats bizarre because i got the .deb for it when i was running kanotix but ubuntu does not like it so it tells me its broken and complains when i update.   ok cheers efwis i'll do that

as for the post by glug 101 you diamond i've wondered for ages why transcode complains during compile, how can i contact you ...via personal message or other means   :KS


thanks for all help provided so far[/QUOTE]

Thank you, you are most kind:)

I thought that I would post the instructions publicly here, incase somebody else will find them useful.  Several of the configure options are not necessary, but most are very useful.  As state earlier, they may need -dev dependencies installed through synaptec.
```
Steps: 1. Remove ffmpeg and libavcodec through Synaptec

2. Download the source for the latest ffmpeg and transcode from their respective sites

ffmpeg:
http://ffmpeg.sourceforge.net/index.php

transcode:
http://www.transcoding.org/cgi-bin/transcode

3. Unpack the source someplace convenient

tar -zxvf ffmpeg-insert-version-here.tar.gz
tar -zxvf transcode-insert-version.tar.gz

4. Configure and compile ffmpeg

./configure --enable-mp3lame --enable-vorbis --enable-a52 --enable-gpl --enable-shared
make
sudo make install

5. Configure and compile transcode

./configure --enable-v4l --enable-lame --enable-ogg --enable-vorbis --enable-theora --enable-libquicktime --enable-a52 --enable-gtk --enable-mjpegtools
make
sudo make install

6. If there are any dependency problems with this method, the best way to handle it that I know of is to go into Synaptec an
install 'dependency-dev' package from there.  Or, you can crawl all over the internet finding the source packages and installing them.  (your choice ;) )

7. Enjoy transcode:)

```

Disclaimer: Again, your mileage may vary :)

---

### Post by tomski on 2005-10-11
thanks for that Glug101 i'll give it a whirl after work;
one question you mention to remove libavcodec but donot mention to reinstall it is there a reason we dont need this or is it part of one of these progs???!!

thanks

---

### Post by glug101 on 2005-10-11
libavcodec is part of ffmpeg.  I don't know why it is packaged as seperate in Ubuntu, but that appears to be what they did.  If you do not remove it you will still run into problems with compiling transcode.

---

### Post by glug101 on 2005-10-11
errr... another oddity...

you might need to add */usr/local/lib* to the file */etc/ld.so.cache* and then run *sudo ldconfig* in order to get ffmpeg to work after you follow my mini-guide.  The libavformat.so and libavcodec.so files live there but Hoary doesn't look unless you tell it. :)

---

### Post by tomski on 2005-10-12
ok looks like i have all the weapons now to dive in and try this 

thanks
i've had a couple of hardware issues latley so i been concentrating on sorting those but i'll dive in this compile tonight and get back with the results


thanks again glug101 

this forum is becoming a haven of helpful people

congrats to all involved

---

### Post by tomski on 2005-10-12
i ran into some problems during the ffmpeg configure
partial output follows:

gcc -g -O3 -Wall -DHAVE_AV_CONFIG_H -I.. -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOU RCE -D_GNU_SOURCE -c -o mp3lameaudio.o mp3lameaudio.c
mp3lameaudio.c:27:23: lame/lame.h: No such file or directory
mp3lameaudio.c:30: error: syntax error before "lame_global_flags"
mp3lameaudio.c:30: warning: no semicolon at end of struct or union
mp3lameaudio.c:32: error: syntax error before '}' token
mp3lameaudio.c:32: warning: type defaults to `int' in declaration of `Mp3AudioCo ntext'
mp3lameaudio.c:32: warning: data definition has no type or storage class
mp3lameaudio.c: In function `MP3lame_encode_init':
mp3lameaudio.c:37: error: `s' undeclared (first use in this function)
mp3lameaudio.c:37: error: (Each undeclared identifier is reported only once
mp3lameaudio.c:37: error: for each function it appears in.)
mp3lameaudio.c:44: warning: implicit declaration of function `lame_init'
mp3lameaudio.c:46: warning: implicit declaration of function `lame_set_in_sample rate'
mp3lameaudio.c:47: warning: implicit declaration of function `lame_set_out_sampl erate'
mp3lameaudio.c:48: warning: implicit declaration of function `lame_set_num_chann els'
mp3lameaudio.c:50: warning: implicit declaration of function `lame_set_quality'
mp3lameaudio.c:52: warning: implicit declaration of function `lame_set_mode'
mp3lameaudio.c:52: error: `JOINT_STEREO' undeclared (first use in this function)
mp3lameaudio.c:53: warning: implicit declaration of function `lame_set_brate'
mp3lameaudio.c:54: warning: implicit declaration of function `lame_init_params'
mp3lameaudio.c:65: warning: implicit declaration of function `lame_close'
mp3lameaudio.c: In function `MP3lame_encode_frame':
mp3lameaudio.c:73: error: `s' undeclared (first use in this function)
mp3lameaudio.c:78: warning: implicit declaration of function `lame_encode_buffer _interleaved'
mp3lameaudio.c:81: warning: implicit declaration of function `lame_encode_buffer '
mp3lameaudio.c: In function `MP3lame_encode_close':
mp3lameaudio.c:90: error: `s' undeclared (first use in this function)
make[1]: *** [mp3lameaudio.o] Error 1
make[1]: Leaving directory `/home/tom/apps/Transcode/ffmpeg-0.4.8/libavcodec'
make: *** [lib] Error 2

i installed lame with synaptic 
it is in usr/bin/lame

should uninstall and try to compile that too??

please help

---

### Post by jdong on 2005-10-12
you need the -dev package for lame.... should be named similar to lame-dev or liblame-dev or you-probably-will-never-ever-guess-this-package-for-lame-dev -- use Synaptic to search for it.

---

### Post by tomski on 2005-10-12
well i tried to compile lame that went well;

now when i try to compile ffmpeg ut complains about oggvorbis ???

so i think its looking like i'll have to uninstall and re compile all the dependencies for this -  which to be honest i dont have the time or the skill let alone the patience to do so.
So im gonna think hard on this.... 
but this is a problem that i always seem to have with linux in general where the app i want is there but to get it i have to change so much to get the thing to work and i always thought that you would only need to compile from source if you wanted cpu specific performance for a given app???
perhaps i was miss informed or just got the wrong idea..
so for now my video editing lays with a north,western breeze called mikewrong shafted windblows

that is untill i get enough knowledge of compiling apps from source to get what i want

then again i could always start from scratch and go with breezy but then who knows what other problems may lie ahead 

oh well isnt linux good

---

### Post by tomski on 2005-10-12
ok im at step 5 and now after getting ffmpeg to compile i now get this:

ERROR: requirement failed: cannot link against libavcodec
libavcodec can be found in the following packages:
  FFMpeg  [http://www.ffmpeg.org/](http://www.ffmpeg.org/)

ERROR: requirement failed: cannot compile mpeg2dec/mpeg2.h
mpeg2dec/mpeg2.h can be found in the following packages:
  mpeg2dec  [http://libmpeg2.sourceforge.net/](http://libmpeg2.sourceforge.net/)

ERROR: requirement failed: cannot link against libmpeg2
libmpeg2 can be found in the following packages:
  mpeg2dec  [http://libmpeg2.sourceforge.net/](http://libmpeg2.sourceforge.net/)

ERROR: option '--enable-libquicktime' failed: cannot link against libquicktime
libquicktime can be found in the following packages:
  libquicktime  [http://libquicktime.sourceforge.net/](http://libquicktime.sourceforge.net/)

ERROR: option '--enable-gtk' failed: cannot compile gtk/gtk.h
gtk/gtk.h can be found in the following packages:
  gtk+  [http://www.gtk.org/](http://www.gtk.org/)

ERROR: option '--enable-gtk' failed: cannot link against libgtk
libgtk can be found in the following packages:
  gtk+  [http://www.gtk.org/](http://www.gtk.org/)

ERROR: option '--enable-libjpeg' failed: cannot compile jpeglib.h
jpeglib.h can be found in the following packages:
  jpeg  [ftp://ftp.uu.net/graphics/jpeg/](ftp://ftp.uu.net/graphics/jpeg/)

ERROR: option '--enable-libjpeg' failed: cannot link against libjpeg
libjpeg can be found in the following packages:
  jpeg  [ftp://ftp.uu.net/graphics/jpeg/](ftp://ftp.uu.net/graphics/jpeg/)


Please see the INSTALL file in the top directory of the
transcode sources for more information about building
transcode with this configure script.


all these are installed along with the dev packages too (thanks for the pointer from jdong 

you need the -dev package for lame

i think this is because i need to enter /usr/local/lib to the file /etc/ld.so.cache and then run sudo ldconfig  but how the file is all garble do i use vi or what???
my *nix skills are now shining through arent they

---

### Post by tomski on 2005-10-12
do you know if so post a quik reply this is bugging me and i dont know enough about comliling apps to resolve this so any help will be well recieved

cheers

---

### Post by tomski on 2005-10-13
i am really considering an update to breezy but i dont want to run into errors
with other software

any advice

---

### Post by glug101 on 2005-10-14
[QUOTE=tomski]i am really considering an update to breezy but i dont want to run into errors
with other software

any advice[/QUOTE]
Sorry, I've been out for awhile.  My breezy update blew up on me. :(  I'm not the only one too, several people are describing kernel panics on the latest kernel update.  Since my /home directory is on a seperate partition, I can blow away the old install and put a fresh Hoary install on in about an hour (with a weeks worth of occasional tweaking to get it back to where I had it :( )  In short, I would be wary of any kernel upgrades for a few days till the capable folks in development can get this sorted out. :)

As far as the dependency problems you are seeing...

I didn't compile any of the dependencies.  I was able to pull all of the -dev files up in Synaptic and compile ffmpeg successfully.  My suggestion is to install as much as possible from the dev's in Synaptic.

I went crazy under Mandrake (excuse me, Mandriva!) trying to compile all the dependencies for stuff.  For compiling everything from scratch, nothing beats Gentoo, cause it's designed that way to automatically take care of the dependencies.  What I love about Ubuntu is that I have the binaries for 'good enough', and I usually only have to compile 1 or 2 packages to get a source compiled version for whatever isn't in Synaptic.

---

### Post by adamb10 on 2005-10-14
Am I the only one that the upgrade did work for?  My ugrade for Hoary was seemless and painless.

---

### Post by jdong on 2005-10-14
Kernel panics during upgrades have nothing to do with the Backports repository. Backports/Extras are designed to migrate cleanly to the next distribution regardless of whether or not Backports/Extras repositories are available for these new versions. I've tested the upgrade path numerous times in my virtual machines, and it's perfectly flawless.

Before upgrading to a new version, I highly recommend testing out the LiveCD to make sure everything (hardware-wise) still works fine, and there's no real surprising changes to the environment that you wouldn't particularly enjoy...

---

### Post by glug101 on 2005-10-14
[QUOTE=jdong]Kernel panics during upgrades have nothing to do with the Backports repository. Backports/Extras are designed to migrate cleanly to the next distribution regardless of whether or not Backports/Extras repositories are available for these new versions. I've tested the upgrade path numerous times in my virtual machines, and it's perfectly flawless.

Before upgrading to a new version, I highly recommend testing out the LiveCD to make sure everything (hardware-wise) still works fine, and there's no real surprising changes to the environment that you wouldn't particularly enjoy...[/QUOTE]
I will give the livecd a try, but 3 out of 3 kernel panics after upgrade to breezy (including a blow away fresh install) makes me think that there is something with the new setup that doesn't sit well with my computer.  (And it works fine under Hoary)

---

### Post by tidoyle1 on 2005-10-14
Somethings wrong cuz I've got the same problem too..

---

### Post by celticmonkey on 2005-10-15
I've been reading throught the posts on the backports and the respository support forums. One thought occurs to me:

**WHY wasn't it better known that the unofficial backports would be disappearing?**

As a newbie, I just did a clean install of breezy to upgrade from hoary thinking that I would be able to reinstall all those great unofficial packages using the instructions we all know from the Unofficial Ubuntu Starter Guide. But I can't.

I think I understand the (legal?) reasons for the unofficial backports disappearing. I don't disagree with it. I just wish I'd known. I suspect that the average user, like myself, doesn't often read the backport and respository forums because once you set those up you never have to think about them again. Most users just go to the unofficial guide or the HowTo forum here. We all missed the announcement. And frankly, it's big big news. It totally changes the way I administer my machine.

A lot of users are still stumbling around expecting the unofficial backports to work again and for win32 codecs and that sort of thing to reappear. They're not going to and we need to get the word out somehow. Someone in-the-know who knows what the souces.list will look like when the offical backports are up needs to put something in the HowTo forum amd sticky it where it will actually get read.

---

### Post by tomski on 2005-10-17
i was thinking if i go ahead and update to breezy will this give me access to the apps i mentioned in this thread 
and 
does anyone know weather the extras are available and what has happend to the repos for hoary and breezy (latest news)

i ask as i just spend to long going through the forum to find what i deem quite important issuses

any links or quotes
would be good

---

### Post by tomski on 2005-10-18
i was wondering seeing as ubuntu is based on sid would i be able to use this repo:

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sid main

this contains transcode and other such app
we all want?????

any ideas
as i was mooching about i discoverd this little cookie:

[http://www.apt-get.org/main/](http://www.apt-get.org/main/)

its a list of repos for deb

---

### Post by glug101 on 2005-10-18
[QUOTE=tomski]i was wondering seeing as ubuntu is based on sid would i be able to use this repo:

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sid main

this contains transcode and other such app
we all want?????

any ideas
as i was mooching about i discoverd this little cookie:

[http://www.apt-get.org/main/](http://www.apt-get.org/main/)

its a list of repos for deb[/QUOTE]
I understand your logic here.  Ubuntu is based on Debian, and they both use deb's, why not use the deb for Debian?  I'm not an expert on this, but I do know that not all deb's are created equal.  I think that there are compatibility issues involved between the two.

That being said, I'm rather certain that those debs will install, and I think it might be worth a try to get one or two pet programs working that are not in the Ubuntu reps.  However I wouldn't load too much from them.  Basically, enable the repo, install the one program you want, and then disable it.

A better approach is to install Breezy.  Assuming, of course, it doesn't blow up on you like it did for me.  Transcode is available for Breezy.  Personally, I have a bet going with my wife, so I'll either have Breezy working by the end of the week, or I'll have a new DVD burner :)  (Yeah, sounds win-win to me too :) )

Cheers!

---

### Post by tomski on 2005-10-19
i tried the live breezy last night and it dont like my g/card (ati 9200radeon)
which is strange coz im using the latest drivers for it in hoary??

so i wont make that move yet!

im making a backup of what i have at the moment then ill experiment with those repos ill kepp ya posted on the results

---

### Post by Andrew G on 2005-10-19
I'm also having the same problem - I've tried playing around with my repositories file (sources.list) in all different ways and have had absolutely no luck. apt-get and Synaptic Package Manager keep returning 404 errors on the Sources.gz (or whatever they're called) files although they exist.

If something is not done about this problem, the amount of Ubuntu users will most likely decrease a lot since apt-get/Synaptic are some of the best things about the distro.

Anyway, I presume nobody knows how to fix this major problem?

Here is my sources.list file:
[INDENT]deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe[/INDENT]

---

### Post by Andrew G on 2005-10-19
Oh, this is my APT-GET output if that helps:

[INDENT]Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
  404 Not Found
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz)  404 Not Found
Reading package lists... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.[/INDENT]

---

### Post by tomski on 2005-10-19
i know that the hoary repo's are down due to the release of breezy these im told will be back up soon (hope so),
 but as for breezy (read my earlier post) sorry no advice for these repo's as i tried breezy and it seems a bit buggy for my hardware so rather than trying to fix a whole bunch more problems i choose to stay with what works.

Did you try any of the debian/sid repo's in the previous post of mine they might help but if you do use them remember to DISABLE them BEFORE any  update,
i normally do this with any repo i add that is not official anyway but you guys may not, its your choice

Did you check the threads in the breezy section (subscribe and set notify by email) to a couple that seem to be about the same problem and see how things progress as there is so many different cominations of hard/software that there is always someone in the same boat or at least in the crows nest!!!

you are right though if they don't sort out these issue's then i would imagine the less experienced may leave but those of us who have been around a bit may well stick it out. 

This is the 3rd time i've used ubuntu and i must say that compared to the first release of warty things have just moved on so much from what was a good but empty distro to a distro that seems to offer the same choice as the big boys but with out the problems(haha) and its bleeding edge thanks to the super fast dev team working on a 6mth turnaround =D> 

if you got the cash and are reading this then donate to ubuntu and debian now or at least but some clothes

---

### Post by jdong on 2005-10-19
Andrew G, you have a **really weird** internet connection, because over here, the links that APT claims it can't download (404 not found) I can open fine with an ordinary web browser :).

---

### Post by tomski on 2005-10-19
i know its really pissing me off, personaly i think its bt as most of the people in this forum that are oversea's (ie non uk) seem to have no problems accessing them.
i am currently compiling a list of problematic repo's to see if there is anyone else having problems with these also.
and im trying to find out if there are any other repo's that are not official and putting them into a list as well  
(fed up with revisiting threads and sites for the same info)
 hopefully they will become sticky??

---

### Post by glug101 on 2005-10-19
[QUOTE=tomski]i know its really pissing me off, personaly i think its bt as most of the people in this forum that are oversea's (ie non uk) seem to have no problems accessing them.
i am currently compiling a list of problematic repo's to see if there is anyone else having problems with these also.
and im trying to find out if there are any other repo's that are not official and putting them into a list as well  
(fed up with revisiting threads and sites for the same info)
 hopefully they will become sticky??[/QUOTE]
Here, here, brother, you're preaching to the choir!  The state of repo's are a muddled mess to my eyes, and I've been using Linux for years (though this is my first debian based dist).  I can't imagine what they look like to newbies.  I appreciate the fine work that the developers and hosts of those repo's are doing on them, but I can't help but feel like there is something basic missing....

---

### Post by tomski on 2005-10-19
[QUOTE=glug101] I can't help but feel like there is something basic missing....[/QUOTE]


thats it in a nutshell glug

i think the thing missing here may be drive or rack space!!!

---

### Post by Emerzen on 2005-10-19
I haven't read this entire thread, but I know some of us are looking for alternatives to some of the packages that have been removed from the repo's for legal reasons.  Here's a link to a new repository for Ubuntu in France where it is legal.

[http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)

There's apt lines on the page.

---

### Post by tomski on 2005-10-20
if you want transcode try using these repo's: deb [ftp://ftp.mowgli.ch/pub/debian](ftp://ftp.mowgli.ch/pub/debian) sid unofficial
deb-src [ftp://ftp.mowgli.ch/pub/debian](ftp://ftp.mowgli.ch/pub/debian) sid unofficial 

i did last night and managed to suck it in but wether any other apps work is a guess..

many others are listed here :

[http://www.apt-get.org/main/](http://www.apt-get.org/main/) 

 im currently going through that and other repo's people have posted in this forum to compile 2 list's one for working and one for non-working 
these would only be tested in hoary so they may work in breezy but im having probs with the live cd crashing before login(x probs i think)
but most repo's cater for both just normaly need to change hoary -> breezy

---

### Post by jeffreyvergara.NET on 2005-10-21
i think the repos are down again. i changed http with ftp, and it worked but now it wont

---

### Post by Andrew G on 2005-10-21
Well my problem has gone, the repositories are working fine now. When they weren't working I was able to access them through my web browser, just not through Synaptic Pkg. Man.
I'm just wondering how long it will be until we can get the final release version of OpenOffice 2.0.0 for Ubuntu :S

---

