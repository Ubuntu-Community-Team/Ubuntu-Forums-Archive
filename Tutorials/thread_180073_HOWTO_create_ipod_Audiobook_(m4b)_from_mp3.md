---
title: "HOWTO create ipod Audiobook (m4b) from mp3"
date: 2006-05-21
forum: Tutorials
---

### Post by Sir_Yaro on 2006-05-21
[SIZE="7"]THIS SCRIPT IS IN BETA STAGE AND IS NOT SUPPORTED ANY MORE[/SIZE]

Some of us have audiobooks splited to many files. Ex.:
chapter01.mp3, chapter02.mp3, chapter03.mp3[...]chapter61.mp3
This script will split them into a few batches, then join every batch into one big file and finally will create m4b files.

To do it just run script in directory with files. Make sure that files are properly named and only sound files are located in working directory...

Please try to remove all non-latin (including spaces) characters from file names.
I suggest names as simple as possible **with subsequent number include**
For example like that:
chapter01.mp3, chapter02.mp3 [...] chapter71.mp3
**but NEVER, EVER like that:**
chapter01.mp3, chapter02.mp3 [...] chapter71.mp3 [...] chapter131.mp3

If there is more than 99 files you **MUST** use 3 (or more) figures in a number otherwise script will join them in a wrong order!


## Changes:
## 1.0.2
## + Files split function added
##
## 1.0.3
## e mpg123 was changed to madplay due some errors
##
## 1.0.4
## + other types support
## r wavmerge required
## r mplayer required
## + automatic batches execution
## + output files are numbered
## + input files type detection
##
## 1.0.5
## + remove merged files
## + sort files
## f decode no-mp3 files
##
## 1.0.6
## + encode to mp3
## d lame
## d normalize-audio
## d imagemagick
## + waves normalization
## f minor bug fixes
## + apt-get deps instalation
## + cover arts generation for an iPod and [roxbox](http://www.rockbox.org/)
## + hints
##
## 1.0.7
## minor changes
##

```

Code was removed because it was too long
Check attachment

```
Just d/l archive and execute:
```
unzip encode-mp3-m4b-1.x.x.zip
chmod a+x encode
cp encode ~/bin

```

---

### Post by adamkane on 2006-05-21
Why choose m4b over mp3 or ogg?

Nice conversion script though.

---

### Post by Sir_Yaro on 2006-05-21
[QUOTE=adamkane]Why choose m4b over mp3 or ogg?
[/QUOTE]
Because m4b is ipod audiobook format? :D
> 
Nice conversion script though.
thx

---

### Post by adamkane on 2006-05-21
Does the ipod automatically put m4b files into the Audiobook directory?

---

### Post by Sir_Yaro on 2006-05-21
yes, it does.
and you can use speed settings with them

---

### Post by adamkane on 2006-05-21
Firefox -> Bookmarks -> Bookmark This Page...

---

### Post by sinaen on 2006-05-22
Yeah Baby Yeah man ive searched for this shit :) thanks man

but how must the files be named so that it can convert them?

sinaen@Neko:/media/space/audiobooks/Terry Pratchett$ ./kodowanie-mp3-m4b DW09\ -\ Eric/
bash: ./kodowanie-mp3-m4b: /bin/bash: bad interpreter: Permission denied
sinaen@Neko:/media/space/audiobooks/Terry Pratchett$ sudo ./kodowanie-mp3-m4b DW09\ -\ Eric/
Password:
sudo: unable to execute ./kodowanie-mp3-m4b: Permission denied

ive tried to execute the script in the folder too

Later:
Ive tried a little more now. and it seems i must write /bin/bash <scriptname>
and then i get a error-message that i am missing faac. but i have the latest libfaac-codec installed 1.24 cleanubuntu :) is that correct?

---

### Post by Sir_Yaro on 2006-05-22
To run any script you must chmod it.
chmod +x file_name
or run:
bash file_name

> 
but how must the files be named so that it can convert them?

Please try to remove all non-latin (including spaces) characters from file names.
I suggest name as simple as possible **with subsequent number included**
For example like that:
chapter01.mp3, chapter02.mp3 [...] chapter71.mp3
**but NEVER like that**
chapter01.mp3, chapter02.mp3 [...] chapter71.mp3 [...] chapter131.mp3

If there is more than 99 files you **MUST** use 3 (or more) figures in a number because otherwise script will join them in a wrong order!

faac might be found in faac*.deb package (faac_1.24clean-0ubuntu3_i386.deb)
[http://packages.ubuntu.com/breezy/sound/faac](http://packages.ubuntu.com/breezy/sound/faac)

I've updated script to most recent version

---

### Post by sinaen on 2006-05-25
[QUOTE=Sir_Yaro]To run any script you must chmod it.
chmod +x file_name
or run:
bash file_name
[/QUOTE]
yup its chmodded :D
[QUOTE=Sir_Yaro]

Please try to remove all non-latin (including spaces) characters from file names.
I suggest name as simple as possible **with subsequent number included**
For example like that:
chapter01.mp3, chapter02.mp3 [...] chapter71.mp3
**but NEVER like that**
chapter01.mp3, chapter02.mp3 [...] chapter71.mp3 [...] chapter131.mp3

If there is more than 99 files you **MUST** use 3 (or more) figures in a number because otherwise script will join them in a wrong order!
[/QUOTE]
then i got a lot to do. it is not fun. cause its multiple files for every cd. and not named chapters :(

[quote=Sir_Yaro]
faac might be found in faac*.deb package (faac_1.24clean-0ubuntu3_i386.deb)
[http://packages.ubuntu.com/breezy/sound/faac](http://packages.ubuntu.com/breezy/sound/faac)
[/quote]
well now i have faac but not 

* wavmerge is missing....
Check on [http://huli.org/wavbreaker/](http://huli.org/wavbreaker/)

Missing dependencies...
Can't continue.

going to check on huli.org/wavbreaker

Edit: now the script works as it should :D i am testing it how it does as i write this :)
Edit: ok another program thats missing :( madplay. but after i installed that. i dont know how to correct the error that the scrip made :/

as i can se it when i ls the dir its made the mp3s merge into 4 great mp3 in batch 1 2 3 4 5 folders
should i just move the files out to the original folder and try the script again?
Did so now it works, i really love that you made this script :D :D

---

### Post by Sir_Yaro on 2006-05-29
[QUOTE=sinaen]
then i got a lot to do. it is not fun. cause its multiple files for every cd. and not named chapters :(
[/QUOTE]
i was only an example
i just know from an experience that simple names are usually better. It should work fine fine with almost any file file name but i can't guarantee that...

mostly is all about good files numbering ex:
if you have files:
1.mp3, 2.mp3, 10.mp3
look what ls returns:
```
[yaro][~/tmp/1]$ ls
razem 0
-rw-r--r--  1 yaro yaro 0 2006-05-29 20:25 10.mp3
-rw-r--r--  1 yaro yaro 0 2006-05-29 20:25 1.mp3
-rw-r--r--  1 yaro yaro 0 2006-05-29 20:25 2.mp3
[yaro][~/tmp/1]$
```
"10" is before "1". Story with files merge will be the same. Chapter "10" will be in a wrong place. thats why I draw attention on this.

btw I'm posting new version right now.

---

### Post by Sir_Yaro on 2006-05-29
[QUOTE=adamkane]Why choose m4b over mp3 or ogg?
[/QUOTE]
i've mentioned speed settings but there is another thing much more important - bookmarks. ipod remember place where you stop listen your AAC file (audiobook). So next time when you push play, a-book will starts from this very place not from the begining...

---

### Post by Sir_Yaro on 2006-06-17
New version available
[http://www.ubuntuforums.org/showpost.php?p=1038201&postcount=1](http://www.ubuntuforums.org/showpost.php?p=1038201&postcount=1)

---

### Post by hopstah on 2006-07-17
it's cool that you have this working, but are you aware of any way to get amarok to recognize m4b files to have in my library as well as to put onto my ipod?  i've been struggling with this ever since i switched to ubuntu.

thanks!

---

### Post by Sir_Yaro on 2006-07-20
try this:
[http://www.yaro.at/deb/amarok.1.4.acc/](http://www.yaro.at/deb/amarok.1.4.acc/)
this is amarok with acc support compiled
I found this on some ubuntu forum (maybe even this forum)
(server doesn't work from time to time)

---

### Post by hopstah on 2006-07-23
amarok works with m4a right now, but doesn't recognize m4b.  i'll give this a try and see where it leads me.

and the server is down right now :(

---

### Post by Sir_Yaro on 2006-07-23
i've made mirror for you
[http://yaro.gdi.pl/deb/amarok.1.4.acc/](http://yaro.gdi.pl/deb/amarok.1.4.acc/)

First server works between ~17.00 and 24.00 usualy and is most up to date...

btw its very strange because m4b and m4a are exactly the same audio format....

---

### Post by hopstah on 2006-07-23
thanks for the mirror.  and i know, i'm very confused and frustrated by this as well.  amarok doesn't even try to play the m4b files, and just complains about it being unreadable.  but change it to m4a, and we're good to go.  hopefully this will make it onto somebody's radar soon enough who knows how to take care of it.

---

### Post by sinaen on 2006-08-30
hmm. cant you associate your m4b files in the file-manager. to get them to play with amarok?

i have this problem to. but i did not have it before. must be the package thats been uninstalled..

i still humbly thank you for this conversion script. i really like it. sometimes my books chapter comes in the wrong order. but its easily sorted out with mp3wrap and unwrap :)

maybe soon well get a graphical interface for the script :D

really thanks mate a lot of times over and over again.

---

### Post by sinaen on 2006-08-30
> **Sir_Yaro said:**
> try this:
[http://www.yaro.at/deb/amarok.1.4.acc/](http://www.yaro.at/deb/amarok.1.4.acc/)
this is amarok with acc support compiled
I found this on some ubuntu forum (maybe even this forum)
(server doesn't work from time to time)

How can i install this the simplest way?
EDIT: Must i manually download the packages and install?

---

### Post by sinaen on 2006-09-24
> **sinaen said:**
> How can i install this the simplest way?
EDIT: Must i manually download the packages and install?

still doesnt get it. i got the new sourche of the latest amarok. and voila. i got the album cover art working for the ipod. but the ipod doesnt recognize acc m4a or m4b files. nor does amarok play the m4b files.

---

### Post by fisherking on 2006-09-30
Hey, just what I was looking for! The only problem is that I cant find wavmerge anywhere! Please help me find it!

---

### Post by xtacocorex on 2006-10-01
> **fisherking said:**
> Hey, just what I was looking for! The only problem is that I cant find wavmerge anywhere! Please help me find it!

It's supposed to download from Sir_Yaro's server, but the server is flaky. I sent him a pm to get the .deb he made and I'll probably put it on my googlepage site for people to get.

wavmerge is found here: [http://huli.org/wavbreaker](http://huli.org/wavbreaker)

You might have to download the source and compile it yourself:
```
./compile && make && sudo make install
``` in the source directory after you extract the archive.

I tried compiling it, but I'm running Edgy Knot 3 in a VM on OS X and I couldn't get dependencies, but Sir_Yaro did this on Dapper, so there should be no problems if you're running that.

---

### Post by fisherking on 2006-10-01
> **xtacocorex said:**
> It's supposed to download from Sir_Yaro's server, but the server is flaky. I sent him a pm to get the .deb he made and I'll probably put it on my googlepage site for people to get.

wavmerge is found here: [http://huli.org/wavbreaker](http://huli.org/wavbreaker)

You might have to download the source and compile it yourself:
```
./compile && make && sudo make install
``` in the source directory after you extract the archive.

I tried compiling it, but I'm running Edgy Knot 3 in a VM on OS X and I couldn't get dependencies, but Sir_Yaro did this on Dapper, so there should be no problems if you're running that.

hmmm, ok tried to compile it (is that even recommended under Ubuntu? - I previously used gentoo, and it was really as death sin to comile software outside portage ;) ) - but when I run ./configure it complains that I dont have gtk+2, gthread or libxml2 installed - which I have. At least gtk+2 and libxml2, gthread I couldn't find anywhere. 


error message: 
```

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking for gawk... (cached) mawk
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... none
checking dependency style of gcc... none
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for cos in -lm... yes
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking for unistd.h... (cached) yes
checking for an ANSI C-conforming const... yes
checking whether gcc needs -traditional... no
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for working memcmp... yes
checking whether lstat dereferences a symlink specified with a trailing slash... yes
checking whether stat accepts an empty string... no
checking for strchr... yes
checking for strdup... yes
checking for strrchr... yes
checking for strstr... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for UNUSED... checking if GTK+ is version 2.6.0 or newer... no
checking for UNUSED... checking if GTK+ is version 2.3.0 or newer... no
TDR:
checking for snd_pcm_open in -lasound... no
checking sys/soundcard.h usability... yes
checking sys/soundcard.h presence... yes
checking for sys/soundcard.h... yes
checking machine/soundcard.h usability... no
checking machine/soundcard.h presence... no
checking for machine/soundcard.h... no
checking for WAVBREAKER... configure: error: Package requirements (gtk+-2.0 gthread-2.0 libxml-2.0) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the WAVBREAKER_CFLAGS and WAVBREAKER_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.


```

---

### Post by xtacocorex on 2006-10-01
That's the same error message I got. I just booted up my old Dell laptop with Dapper on it and will see if I can get it to compile.

EDIT:
Figured out the compile stuff.
If you do the following before the configure:
```
pkg-config --cflags --libs gtk+-2.0 gthread-2.0 libxml-2.0
```
it will work.
Also, if you install the package **checkinstall **it will create .deb packages and install them.
The compile process should be:
```

pkg-config --cflags --libs gtk+-2.0 gthread-2.0 libxml-2.0
./configure
make
sudo checkinstall

```

---

### Post by fisherking on 2006-10-01
thanks xtacocorex,

I also hadn't installed the dev-packages :-\" 

Now the script works great ... so far !

---

### Post by sinaen on 2006-10-02
what programs do you use to get the files to your ipod? im looking for an alternative to amarok as i cannot get that to work :(

---

### Post by xtacocorex on 2006-10-02
> **sinaen said:**
> what programs do you use to get the files to your ipod? im looking for an alternative to amarok as i cannot get that to work :(

I actually bought a MacBook, so I don't run Ubuntu predominately anymore (I have Edgy in a Virtual Machine), but I needed this go convert some poorly imported Audiobooks my wife and I have into iTunes.

I know people use GTKPod for their iPods.  It's surprising that amaroK won't work.  I gave my wife the iPod since I bought an iRiver a while back and most of my music is in .ogg files; I wanted a player that supported that.

---

### Post by sinaen on 2006-10-03
O yeah. its working with mp3/audio files. but not m4b files :/ and how do you convert the audiobook-cds to m4b in itunes?

some audio files does not transfer completely or some won't transfer :(
its real strange...

---

### Post by xtacocorex on 2006-10-03
> **sinaen said:**
> O yeah. its working with mp3/audio files. but not m4b files :/ and how do you convert the audiobook-cds to m4b in itunes?

some audio files does not transfer completely or some won't transfer :(
its real strange...

I don't think you can convert an audiobook cd to .m4b into iTunes, unless you rip it at .m4a and maybe change the extension to .m4b.  I haven't tried it, but I thought about trying it on my wife's computer.

I think the script is only able to make .m4b files and won't use them as input.

---

### Post by sinaen on 2006-10-04
i convert my files with Sir-Yaro's script here and they work lovely. but i have lost the function to 
get the files on the ipod with amarok as i use as my main-player and ipod-program :(

i think i had it in one of the former versions of amarok. but now thats lost. and i dont now how to get it back :( im going to try with gtkpod... :P 
F**k..

---

### Post by xtacocorex on 2006-10-04
> **sinaen said:**
> i convert my files with Sir-Yaro's script here and they work lovely. but i have lost the function to 
get the files on the ipod with amarok as i use as my main-player and ipod-program :(

i think i had it in one of the former versions of amarok. but now thats lost. and i dont now how to get it back :( im going to try with gtkpod... :P 
F**k..
Do you still have a Windows machine that you hook your iPod up to? I think the new iPod update might have made them incompatable with the code in amaroK.  Just a theory though that I can't prove.

---

### Post by sinaen on 2006-10-05
yup i have a windows computer to hook it up in. not my own thoug. 

but i havent updated the software. do itunes do that automatically?

i have formated it and reset it to the standards? does it not work? should i reset the factory defaults. (totally reset)

But i have full functionallity in amarok for ipod. and audio files. the thing that doesnt work is that amarok doesnt play m4b files or  :/

---

### Post by xtacocorex on 2006-10-05
Don't really know how much help I can be anymore since I don't actually use an iPod.  The iTunes in Windows should have asked to update itself.

---

### Post by Sir_Yaro on 2006-10-08
sorry that i didn't answer.
please check here:
[http://yaro.gdi.pl/deb/dapper/](http://yaro.gdi.pl/deb/dapper/)
or here:
[http://www.yaro.at/deb/dapper/](http://www.yaro.at/deb/dapper/)

second one might be disabled quite often but usually content is more recent...

---

### Post by Sir_Yaro on 2006-10-08
btw i found limitation in ipod (or ipod software). it can't play veeery long mp3's.
I got lord of the ring, third part last over 25 hours and stupid ipod see only first 45 minutes. Maybe it's a one time only issue but who know...

---

### Post by airtonix on 2006-10-09
[rockbox]("http://www.rockbox.org/") is way better than the piffy limited ipod-apple os.....nuff said.

---

### Post by Sir_Yaro on 2006-10-10
> **airtonix said:**
> [rockbox]("http://www.rockbox.org/") is way better than the piffy limited ipod-apple os.....nuff said.

agree... rockbox rule, but there is one exception - quality of decoders. They are much worse the apple's. battery last for much shorter period - what is unacceptable for me. Anything below 13h is unacceptable for me and only apple software can do that... :( :(

---

### Post by sinaen on 2006-10-21
> **Sir_Yaro said:**
> agree... rockbox rule, but there is one exception - quality of decoders. They are much worse the apple's. battery last for much shorter period - what is unacceptable for me. Anything below 13h is unacceptable for me and only apple software can do that... :( :(

Yup rockbox and ipodlinux seems all niftytifty. but when you look about how much the battery-time is shortend its dissapointing. and if you research you know that ogg/flac takes much more cpu-power to decode again when youre listening. so there's a real "why" to use mp3/aac. encoding.

Havent got the amarok part to work yet. but now i have support on the gtkpod for aac/m4a/m4b, and another problem has risen to my attention. theres no practical program/way to edit m4b tag-files so im really dissapointed on the programs (i dont know about amarok as its not able to open m4b, dunno about the m4a files)

---

### Post by Sir_Yaro on 2006-10-21
as far i remember my script can tag m4b files...

try to call:
faac --help

---

### Post by sinaen on 2006-10-22
> **Sir_Yaro said:**
> btw i found limitation in ipod (or ipod software). it can't play veeery long mp3's.
I got lord of the ring, third part last over 25 hours and stupid ipod see only first 45 minutes. Maybe it's a one time only issue but who know...

is it the same with m4b?

faac --help gave me some hint. but i think linux/ubuntu still needs a good program that can open m4b and rename/edit tags....

---

### Post by Sir_Yaro on 2006-10-22
> **sinaen said:**
> is it the same with m4b?

i don't think so... u may try... :P

---

### Post by sinaen on 2006-10-23
> **Sir_Yaro said:**
> i don't think so... u may try... :P

The script does say that it's a limitation on the wav-file so it may not be possible if you do it in any case... :)

---

### Post by netztier on 2006-10-26
I installed encode-mp3-m4b-1.0.6 yesterday. After figuring out what packages I had to add (id3v2, normalize etc), all dependencies were met. For wavebreaker, I found an .rpm archive, converted it with [FONT="Courier New"]**alien**[/FONT] to .deb and installed it easily with [FONT="Courier New"]**dpkg -i <package name>**[/FONT].

I want to transcode 12 files of 25-30MBytes each. 

When I tell the script to work in batches, nothing happens - it says it will do 3 batches, creates subdirectories, seems to wrap the 12 files into groups of 4 and then... stops and claims "all done". However, the "Audiobook" directory is empty, so are the "batch_1", "batch_2" "batch_..." directories.

If I tell the scrip *not* to do batches, it wraps all the files into the single large mp3 of ca 320Mbytes and then starts to transcode. It estimates some ~1'048'000 frames to decode/encode, and on my 1.8Ghz Athlon 64 (Venice 3000) with 1 GByte RAM, it estimates to be done after ~3000 seconds. 

[COLOR="Red"]However, exactly after 38150 frames (some 3-4% of the total), the counters stop increasing, and faac eats 100% CPU until i kill it.[/COLOR] I tried it more than once, it's always at the same point where the effect occurs.

What strikes me as odd is this: xmms says the large mp3 file is 5h50' long, totem (gstreamer) only sees 28'35" - if i recall correctly, that is about the length of the first mp3. Nonetheless, both players play the file to it's very end without error.

Is faac stumbling over some incorrect length value in the .mp3 haeder or something like that?

regards

Marc

---

### Post by Sir_Yaro on 2006-10-27
Could u show me this files (output of *ls -l*) ??
This was happening from time to time in old versions but i thought i fixed this for good...

and about faac - that's true. I think it can't manage with mp3's contains some "bugs" inside. I'm pretty sure mp3wrap creates mp3s according to some very simple algorithm, _something_ like:
cat *mp3>>new.mp3
That's why (i think) all this players show wrong, different time.

To be honest right now i don't have a clue how to get round this issue....

---

### Post by sinaen on 2006-11-01
i have some similar problem with one file. and it solved when i dled another version of that file. and tried again. but its not funny..
EDIT: I tried to transfer/download the files again to my computer and then the script worked. it might be that its no-good mp3's you tryed to convert, so trie to dlad again, i have hade this error on 2 convertion-projects  so far.

i have experienced when i listen to my audiobooks on my ipod. that it (on one occassion this night) was playing one book and suddenly stopped. i thougt i was out of battery but it was the file that stopped and the ipod defaulted out to the original menu...

have you had any of this? it might be faulty transfer to ipod or?
i have no clue whatsoever anyway

can it be that it loses sync and the wav-file is limited to it's size. cant you convert it in mp3 or another format? raw?? :D just an idea...
But the loss of syncing does not seem to be an issue of the wav file-size. lets hope Sir_Yaro has the expertice in this question. im to lousy on script-programming..

EDit:
Here are some of the errors i get when i get them:

Freeware Advanced Audio Coder
FAAC 1.24

error: frame 0: lost synchronization
Quantization quality: 80
Bandwidth: 11025 Hz
Object type: Low Complexity(MPEG-4) + TNS + M/S
File format: MPEG-4 File Format (MP4)
Encoding - to The Fifth Elephant.cz..m4b
   frame          | bitrate | elapsed/estim | play/CPU | ETA
  150/-2097150 (  0%)|  -38.8  |    0.3/-3691.2 |   26.38x | -3691.5 error: frame 342: lost synchronization
38700/-2097150 ( -1%)|  -37.9  |   88.5/-4797.0 |   20.30x | -4885.5 error: frame 68903: lost synchronization
77450/-2097150 ( -3%)|  -38.0  |  182.7/-4946.4 |   19.69x | -5129.1 error: frame 137810: lost synchronization
116200/-2097150 ( -5%)|  -37.9  |  283.8/-5121.4 |   19.02x | -5405.2 error: frame 206716: lost synchronization
155000/-2097150 ( -7%)|  -37.8  |  383.7/-5191.4 |   18.76x | -5575.0 error: frame 275622: lost synchronization
193750/-2097150 ( -9%)|  -37.8  |  471.0/-5098.1 |   19.10x | -5569.1 error: frame 344529: Huffman data overrun
232500/-2097150 (-11%)|  -37.7  |  568.5/-5127.9 |   18.99x | -5696.4 error: frame 413435: lost synchronization
271250/-2097150 (-12%)|  -37.7  |  668.4/-5167.4 |   18.85x | -5835.8 error: frame 482341: lost synchronization
310000/-2097150 (-14%)|  -37.8  |  769.4/-5205.0 |   18.71x | -5974.5 error: frame 551247: lost synchronization
348750/-2097150 (-16%)|  -37.8  |  869.1/-5226.2 |   18.64x | -6095.3 error: frame 620154: lost synchronization
387500/-2097150 (-18%)|  -37.9  |  968.0/-5238.9 |   18.59x | -6206.9 error: frame 689060: lost synchronization
411000/-2097150 (-19%)|  -37.9  | 1027.7/-5243.8 |   18.57x | -6271.5 error: frame 730825: lost synchronization
426300/-2097150 (-20%)|  -37.9  | 1067.0/-5249.2 |   18.55x | -6316.2 error: frame 757966: lost synchronization
465050/-2097150 (-22%)|  -37.8  | 1165.9/-5257.7 |   18.52x | -6423.6 error: frame 826872: Huffman data overrun
503800/-2097150 (-24%)|  -37.8  | 1265.3/-5266.9 |   18.49x | -6532.2 error: frame 895779: lost synchronization
542550/-2097150 (-25%)|  -37.8  | 1366.2/-5280.9 |   18.44x | -6647.1 error: frame 964685: Huffman data overrun
581300/-2097150 (-27%)|  -37.8  | 1465.4/-5286.6 |   18.42x | -6752.0 error: frame 1033586: lost synchronization
620050/-2097150 (-29%)|  -37.8  | 1564.1/-5290.1 |   18.41x | -6854.2 error: frame 1102492: lost synchronization
658850/-2097150 (-31%)|  -37.9  | 1663.6/-5295.4 |   18.39x | -6959.0 error: frame 1171399: lost synchronization
697600/-2097150 (-33%)|  -37.9  | 1763.2/-5300.6 |   18.37x | -7063.8 error: frame 1240305: lost synchronization
736350/-2097150 (-35%)|  -37.9  | 1862.5/-5304.5 |   18.36x | -7167.0 error: frame 1309211: lost synchronization
775100/-2097150 (-36%)|  -37.9  | 1962.7/-5310.3 |   18.34x | -7272.9 error: frame 1378117: lost synchronization
813850/-2097150 (-38%)|  -37.9  | 2062.4/-5314.4 |   18.33x | -7376.7 error: frame 1447024: Huffman data overrun
834200/-2097150 (-39%)|  -37.9  | 2114.9/-5316.7 |   18.32x | -7431.6 error: frame 1483162: lost synchronization
834255/-2097150 (-39%)|  -37.9  | 2115.0/-5316.7 |   18.32x | -7431.7

Batch  done

---

### Post by ChrisQ on 2007-06-01
Hi, 
This is a really great script! 

Here are a couple ideas that could make it even better.

1. Check to see if both tracks in the stereo mp3 are the same, if so default to merge them to mono and save some ipod space.
2. Make the encode rate configureable. This could take the form of a select option to choose low quality, med quality, regular quality, high quality, crazy quality, etc.

3. Allow for the splitting to be done based on length of time. I only peripherally care how big the resulting m4b file is, but i care a great deal how long it is. Ipods tend to lose my place every once in a while and it is a great deal easier to fast forward through a two hour segment to my position than a ten hour segment.

Thanks,

Keep up the good work!

---

### Post by joachim.j on 2007-06-07
Wow! This is exactly the thing I've been looking for. Being a Mac convert I still prefer m4b as my audiobook format. I'm still doing my first conversion from mp3 to m4b but so far everything looks fine.

Great work.

---

### Post by skrimpy on 2007-06-15
I am trying to get this working because it would be perfect for me.  I've installed the script in the directory with my audio files and run it.  It was able to get everything it needed except wavbreaker.  I tried to get wavbreaker from its site but it's telling me I'm missing dependencies.  When I try and install those dependencies I'm told one of them conflicts with something already on my system (I'm running feisty).  Any ideas on how I can get wavbreaker installed so I can run this script?

---

### Post by Sir_Yaro on 2007-06-16
Go to the line 168 and 169. And there change:
> http://yaro.gdi.pl/deb/wavbreaker_0.7-1_i386.deb
into:
> http://yaro.gdi.pl/deb/dapper/wavbreaker_0.7-1_i386.deb
and run script again. 
Or do it manually:
```

[yaro]@d[/tmp]$ wget http://yaro.gdi.pl/deb/dapper/wavbreaker_0.7-1_i386.deb
--13:46:42--  http://yaro.gdi.pl/deb/dapper/wavbreaker_0.7-1_i386.deb
           => `wavbreaker_0.7-1_i386.deb'
Translacja yaro.gdi.pl... 80.55.48.77
&#321;&#261;czenie si&#281; z yaro.gdi.pl|80.55.48.77|:80... po&#322;&#261;czono.
&#379;&#261;danie HTTP wys&#322;ano, oczekiwanie na odpowied&#378;... 200 OK
D&#322;ugo&#347;&#263;: 38,494 (38K) [text/plain]

100%[=====================================================================================================================>] 38,494        22.12K/s

13:46:45 (22.09 KB/s) - `wavbreaker_0.7-1_i386.deb' saved [38494/38494]

[yaro]@d[/tmp]$
[yaro]@d[/tmp]$ sudo dpkg -i wavbreaker_0.7-1_i386.deb
Password:
Zaznaczenie poprzednio niezaznaczonego pakietu wavbreaker.
(Odczytywanie bazy danych ... 168092 plików i katalogów obecnie zainstalowanych.)
Rozpakowanie wavbreaker (z wavbreaker_0.7-1_i386.deb) ...
Konfigurowanie wavbreaker (0.7-1) ...
[yaro]@d[/tmp]$ wav
wavbreaker  wavinfo     wavmerge
[yaro]@d[/tmp]$ wavmerge
Must pass filenames of wave files to merge.
Usage: wavmerge [-o outfile] mergefiles...
[yaro]@d[/tmp]$   

```


If u have some problems show them to us instead of just telling u have some... :P

---

### Post by Sir_Yaro on 2007-06-16
> **ChrisQ said:**
> Hi, 
This is a really great script! 

Here are a couple ideas that could make it even better.

1. Check to see if both tracks in the stereo mp3 are the same, if so default to merge them to mono and save some ipod space.
2. Make the encode rate configureable. This could take the form of a select option to choose low quality, med quality, regular quality, high quality, crazy quality, etc.

3. Allow for the splitting to be done based on length of time. I only peripherally care how big the resulting m4b file is, but i care a great deal how long it is. Ipods tend to lose my place every once in a while and it is a great deal easier to fast forward through a two hour segment to my position than a ten hour segment.

Thanks,

Keep up the good work!

I do not maintain this script any more. I found huge mp3 and audiobooks (m4b) not very useful for me atm. Beside that this script require complete rewrite cause now its like McGyver work - improvised arrangement. It works but it can be much better. :D
I'll take a look and maybe I'll do some improvements but I can't promise you that.

---

### Post by Sir_Yaro on 2007-06-16
> **sinaen said:**
> i have some similar problem with one file. and it solved when i dled another version of that file. and tried again. but its not funny..
EDIT: I tried to transfer/download the files again to my computer and then the script worked. it might be that its no-good mp3's you tryed to convert, so trie to dlad again, i have hade this error on 2 convertion-projects  so far.

i have experienced when i listen to my audiobooks on my ipod. that it (on one occassion this night) was playing one book and suddenly stopped. i thougt i was out of battery but it was the file that stopped and the ipod defaulted out to the original menu...

have you had any of this? it might be faulty transfer to ipod or?
i have no clue whatsoever anyway

I'd say merge process if far from perfection. I think it just merge files without any (i think) processing. But this has nothing to do with my script and I can;t fix this.
> 
can it be that it loses sync and the wav-file is limited to it's size. cant you convert it in mp3 or another format? raw?? :D just an idea...
But the loss of syncing does not seem to be an issue of the wav file-size. lets hope Sir_Yaro has the expertice in this question. im to lousy on script-programming..

I tried to use raw files but as far I remember I had some major problem with piping data from one program to another... :(
> 
EDit:
Here are some of the errors i get when i get them:

Freeware Advanced Audio Coder
FAAC 1.24

error: frame 0: lost synchronization
Quantization quality: 80
Bandwidth: 11025 Hz
Object type: Low Complexity(MPEG-4) + TNS + M/S
File format: MPEG-4 File Format (MP4)
Encoding - to The Fifth Elephant.cz..m4b
   frame          | bitrate | elapsed/estim | play/CPU | ETA
  150/-2097150 (  0%)|  -38.8  |    0.3/-3691.2 |   26.38x | -3691.5 error: frame 342: lost synchronization
38700/-2097150 ( -1%)|  -37.9  |   88.5/-4797.0 |   20.30x | -4885.5 error: frame 68903: lost synchronization
77450/-2097150 ( -3%)|  -38.0  |  182.7/-4946.4 |   19.69x | -5129.1 error: frame 137810: lost synchronization
116200/-2097150 ( -5%)|  -37.9  |  283.8/-5121.4 |   19.02x | -5405.2 error: frame 206716: lost synchronization
155000/-2097150 ( -7%)|  -37.8  |  383.7/-5191.4 |   18.76x | -5575.0 error: frame 275622: lost synchronization
193750/-2097150 ( -9%)|  -37.8  |  471.0/-5098.1 |   19.10x | -5569.1 error: frame 344529: Huffman data overrun
232500/-2097150 (-11%)|  -37.7  |  568.5/-5127.9 |   18.99x | -5696.4 error: frame 413435: lost synchronization
271250/-2097150 (-12%)|  -37.7  |  668.4/-5167.4 |   18.85x | -5835.8 error: frame 482341: lost synchronization
310000/-2097150 (-14%)|  -37.8  |  769.4/-5205.0 |   18.71x | -5974.5 error: frame 551247: lost synchronization
348750/-2097150 (-16%)|  -37.8  |  869.1/-5226.2 |   18.64x | -6095.3 error: frame 620154: lost synchronization
387500/-2097150 (-18%)|  -37.9  |  968.0/-5238.9 |   18.59x | -6206.9 error: frame 689060: lost synchronization
411000/-2097150 (-19%)|  -37.9  | 1027.7/-5243.8 |   18.57x | -6271.5 error: frame 730825: lost synchronization
426300/-2097150 (-20%)|  -37.9  | 1067.0/-5249.2 |   18.55x | -6316.2 error: frame 757966: lost synchronization
465050/-2097150 (-22%)|  -37.8  | 1165.9/-5257.7 |   18.52x | -6423.6 error: frame 826872: Huffman data overrun
503800/-2097150 (-24%)|  -37.8  | 1265.3/-5266.9 |   18.49x | -6532.2 error: frame 895779: lost synchronization
542550/-2097150 (-25%)|  -37.8  | 1366.2/-5280.9 |   18.44x | -6647.1 error: frame 964685: Huffman data overrun
581300/-2097150 (-27%)|  -37.8  | 1465.4/-5286.6 |   18.42x | -6752.0 error: frame 1033586: lost synchronization
620050/-2097150 (-29%)|  -37.8  | 1564.1/-5290.1 |   18.41x | -6854.2 error: frame 1102492: lost synchronization
658850/-2097150 (-31%)|  -37.9  | 1663.6/-5295.4 |   18.39x | -6959.0 error: frame 1171399: lost synchronization
697600/-2097150 (-33%)|  -37.9  | 1763.2/-5300.6 |   18.37x | -7063.8 error: frame 1240305: lost synchronization
736350/-2097150 (-35%)|  -37.9  | 1862.5/-5304.5 |   18.36x | -7167.0 error: frame 1309211: lost synchronization
775100/-2097150 (-36%)|  -37.9  | 1962.7/-5310.3 |   18.34x | -7272.9 error: frame 1378117: lost synchronization
813850/-2097150 (-38%)|  -37.9  | 2062.4/-5314.4 |   18.33x | -7376.7 error: frame 1447024: Huffman data overrun
834200/-2097150 (-39%)|  -37.9  | 2114.9/-5316.7 |   18.32x | -7431.6 error: frame 1483162: lost synchronization
834255/-2097150 (-39%)|  -37.9  | 2115.0/-5316.7 |   18.32x | -7431.7

Batch  done

did u try to convert then by hand ?

---

### Post by skrimpy on 2007-06-18
> **Sir_Yaro said:**
> Go to the line 168 and 169. And there change:

into:

and run script again. 
Or do it manually:
```

[yaro]@d[/tmp]$ wget http://yaro.gdi.pl/deb/dapper/wavbreaker_0.7-1_i386.deb
--13:46:42--  http://yaro.gdi.pl/deb/dapper/wavbreaker_0.7-1_i386.deb
           => `wavbreaker_0.7-1_i386.deb'
Translacja yaro.gdi.pl... 80.55.48.77
&#321;&#261;czenie si&#281; z yaro.gdi.pl|80.55.48.77|:80... po&#322;&#261;czono.
&#379;&#261;danie HTTP wys&#322;ano, oczekiwanie na odpowied&#378;... 200 OK
D&#322;ugo&#347;&#263;: 38,494 (38K) [text/plain]

100%[=====================================================================================================================>] 38,494        22.12K/s

13:46:45 (22.09 KB/s) - `wavbreaker_0.7-1_i386.deb' saved [38494/38494]

[yaro]@d[/tmp]$
[yaro]@d[/tmp]$ sudo dpkg -i wavbreaker_0.7-1_i386.deb
Password:
Zaznaczenie poprzednio niezaznaczonego pakietu wavbreaker.
(Odczytywanie bazy danych ... 168092 plików i katalogów obecnie zainstalowanych.)
Rozpakowanie wavbreaker (z wavbreaker_0.7-1_i386.deb) ...
Konfigurowanie wavbreaker (0.7-1) ...
[yaro]@d[/tmp]$ wav
wavbreaker  wavinfo     wavmerge
[yaro]@d[/tmp]$ wavmerge
Must pass filenames of wave files to merge.
Usage: wavmerge [-o outfile] mergefiles...
[yaro]@d[/tmp]$   

```


If u have some problems show them to us instead of just telling u have some... :P

This worked for me, and the script seems to have successfully worked on the first harry potter book.  I'm playing it through now to be sure.  Thanks for this script!

---

### Post by skrimpy on 2007-06-29
:(  Well I had no problems with the first book but now I can't get any of the others to convert successfully.  I have tried over and over, using fresh transfers of the files, splitting into batches, etc.  The script always freezes, sometimes at 0% sometimes higher.  Here is what I'm frozen on attempting the fourth book:

```
size is 1211951232


Freeware Advanced Audio Coder
FAAC 1.24

error: frame 0: lost synchronization
Quantization quality: 80
Bandwidth: 13600 Hz
Object type: Low Complexity(MPEG-4) + TNS + M/S
File format: MPEG-4 File Format (MP4)
Encoding - to Harry Potter and the Goblet of Fire.cz..m4b
   frame          | bitrate | elapsed/estim | play/CPU | ETA
598700/1048577 ( 57%)|   50.4  | 1172.4/2053.4 |   11.86x | 881.0  

```

It's wrapping the files fine but not rewriting them.  Any suggestions?  Anything else to do this?  I really want to get my audiobooks into audiobook format for itunes :(

---

### Post by chronusdark on 2007-07-10
i dont know what is wrong but it seems the script is looking for a file called _MP3WRAP.mp3 but the only one is .mp3_MP3WRAP.mp3?
is this an error or am i stupid

---

### Post by sinaen on 2007-07-11
> **Sir_Yaro said:**
> I'd say merge process if far from perfection. I think it just merge files without any (i think) processing. But this has nothing to do with my script and I can;t fix this.

I tried to use raw files but as far I remember I had some major problem with piping data from one program to another... :(


did u try to convert then by hand ?

No i havent done that. im only trying your script. 

i have some other problems that is that your scripts suddelny just stops or is skipping, the stopping part i dont get but the skipping could be that the mp3-files is badly synced before i convert them ....

i have had some success in converting the files that crashes/stops the script in itunes on a windows computer (its my gf's computer) :)

---

### Post by ephman on 2007-10-19
hi,

i've installed everything followed the instructions, all is good on that end, no errors or issues.  made very simple chapter names 1.mp3, 2.mp3, etc... now when i run the script all seems fine until it gets to 5% of the first chapter and then it hangs.  i've tried running it twice and twice it has happened.  funny thing however, faac is still rocking my cpu at full crank.  i've played the mp3 seems to be alright from an ear perspective.  any thoughts???

thanks for your bandwidth,

ephman

---

### Post by ChrisQ on 2007-10-19
no idea, I stopped using this stuff some time ago. The transkode script that comes with amarok is much easier.

---

### Post by Sheryl22 on 2008-02-19
Nice information. Thank you.
________________________________
Download your favorite audio books from Harry Potter to Stephen King Here [http://www.im-listening-audio-books.com/](http://www.im-listening-audio-books.com/)...

---

### Post by MaX on 2008-05-10
I have multiple m4b files I want merged or joined together into one single file. How do I do that?

---

### Post by ChrisQ on 2008-05-10
no idea how to join m4b files. I used mp3wrap for mp3 files though

---

### Post by gobo38 on 2008-06-07
@MaX

Try a ```
cat 01.m4b, 02.m4b...xx.m4b > complete m4b
```
This works perfect with mp3 files (and no additional tags are written as with mp3merge)

greetz
gobo38

---

### Post by giusorgente on 2008-08-03
I'm not able to download it :-(....


> **Sir_Yaro said:**
> [SIZE="7"]THIS SCRIPT IS IN BETA STAGE AND IS NOT SUPPORTED ANY MORE[/SIZE]

Some of us have audiobooks splited to many files. Ex.:
chapter01.mp3, chapter02.mp3, chapter03.mp3[...]chapter61.mp3
This script will split them into a few batches, then join every batch into one big file and finally will create m4b files.

To do it just run script in directory with files. Make sure that files are properly named and only sound files are located in working directory...

Please try to remove all non-latin (including spaces) characters from file names.
I suggest names as simple as possible **with subsequent number include**
For example like that:
chapter01.mp3, chapter02.mp3 [...] chapter71.mp3
**but NEVER, EVER like that:**
chapter01.mp3, chapter02.mp3 [...] chapter71.mp3 [...] chapter131.mp3

If there is more than 99 files you **MUST** use 3 (or more) figures in a number otherwise script will join them in a wrong order!


## Changes:
## 1.0.2
## + Files split function added
##
## 1.0.3
## e mpg123 was changed to madplay due some errors
##
## 1.0.4
## + other types support
## r wavmerge required
## r mplayer required
## + automatic batches execution
## + output files are numbered
## + input files type detection
##
## 1.0.5
## + remove merged files
## + sort files
## f decode no-mp3 files
##
## 1.0.6
## + encode to mp3
## d lame
## d normalize-audio
## d imagemagick
## + waves normalization
## f minor bug fixes
## + apt-get deps instalation
## + cover arts generation for an iPod and [roxbox](http://www.rockbox.org/)
## + hints

```

Code was removed because it was too long
Check attachment

```
Just d/l archive and execute:
```
unzip encode-mp3-m4b-1.x.x.zip
chmod a+x encode
cp encode ~/bin

```

---

### Post by Sir_Yaro on 2008-08-06
> **giusorgente said:**
> I'm not able to download it :-(....
Why? How? When? What? Who ? :confused:  :D :D
Files are attachted to my post and i got them without any problems.

---

### Post by chronusdark on 2008-10-02
There is a broken link, when this script tries to download wavebreaker.

Also there are a couple sentences that I cannot understand:

```
Mp3 files detected.
You may force to encode files as none mp3
by adding "o" as a parameter of the script


Split files to batches? (y/n) [y]
If you're going to encode from mp3 to mp3
(merge only) choose "n"
```

I think the wording is a little weird.

Otherwise the script is great so far!  I will give a full report when the current job is completed.

---

### Post by jdforsythe on 2008-10-14
The script seems to be working great for me in Intrepid Ibex Beta.

It installs all the missing dependencies thru apt-get EXCEPT wavbreaker.

This is simple enough to change, though. Two options:

If you just want to get it working, before running the script, run in a terminal:

sudo apt-get install wavbreaker

If, as me, you are going to save this script and use it on your next install, you'll want to change the script to add wavbreaker package to the apt-get command so when you use it on a fresh install it will correctly add the wavbreaker package. This is simple enough.

Open it in gedit or nano, whichever you prefer
gedit encode
or
nano encode

Look for the line that echos the apt-get command. You can change that if you wish, but it doesn't have any effect. The next line is where the apt-get command is actually run (looks very similar but doesn't start with ECHO and doesn't have any " double quotes in the command). Simply add " wavbreaker" to the end (without quotes). Then remove the whole next section from if to fi that deals with wavbreaker. Save it and exit.

Now you can continue to copy it to /bin but that's not necessary. I like to keep my addons that I will want on fresh installs (or for setting up other people's computers) in a separate folder. Mine is ~/Software (Software folder under my home folder) so just use Nautilus to move the encode file there, or, for instance:
mv encode ~/Software

I also renamed it to have more meaning, since encode could be anything. Mine is called "mp3-to-m4b". So when I want to convert an audio book, I open a terminal and cd to the audio book directory:
cd ~/Audiobooks/BOOKFOLDER

(Make sure the files are named correctly according to the instructions in the original post. To simplify it, I just name everything 01.mp3, 02.mp3, etc)

Then run the script from its remote directory, like so:
~/Software/mp3-to-m4b

The script automatically detects the directory you are in, not where the script resides, so if you have cd'd to the folder the audio book is in, it will work just like that.

Note: IT TAKES A VERY LONG TIME! Fair warning. Large books take forever.

I will attempt to attach a zip of my modified script, if it doesn't work though, just PM me or email [email]jdforsythe@gmail.com[/email] and I'll send it to you.

---

### Post by sinaen on 2008-10-15
Have you seen this script SirYaro?

[http://www.usalug.org/phpBB2/viewtopic.php?printertopic=1&t=13478&start=0&postdays=0&postorder=asc&vote=viewresult&sid=73b303bf78e6375bd34b432e5339c7b1](http://www.usalug.org/phpBB2/viewtopic.php?printertopic=1&t=13478&start=0&postdays=0&postorder=asc&vote=viewresult&sid=73b303bf78e6375bd34b432e5339c7b1)

---

### Post by SirThom on 2009-02-14
OK so after much mucking about I have my audiobook converted to m4b format.  How to I upload it as an audiobook?  When I just upload it it treats it as a song.  I don't have any kind of Audiobook directory on this thing.  It was initialised originally with gtkpod.

---

### Post by SirThom on 2009-02-15
Never mind, I figured out an easier way.  I was having some troubles with those scripts.
Just use mp3wrap from the command line to combine the mp3s.  Navigate to the folder with them and type 'mp3wrap *.mp3'.  As for the order, just make sure that if you list the mp3's alphabetically, that they are in the correct order.  Your wrapped mp3 will have the name of the first mp3 in the collection appended with '_MP3WRAP'.
Then upload the wrapped mp3 with gtkpod.  From gtkpog, right click on the uploaded file and select 'Edit Track Details.'  Edit anything you want with album name, artist, etc.  Then, from the 'Media Type' drop-down menu select 'Audiobook.'  Also tick the boxes for 'Remember Playback Position' and 'Skip when Shuffling.'  Click 'Apply' and then 'OK'
Also, by left clicking on the title field you can change the name of the file to your book title.
Now click 'Save Changes' before quitting gtkpod and ejecting the ipod.  It works like a charm.

This worked on a 4g iPod nano.

---

### Post by darkkith on 2009-02-16
this is all great, but the primary issue i end up with is no bookmarks, or chapters in the resulting m4b.  for a short audiobook this isn't much of a problem, but a standard audiobook, say 5hrs+ long, it becomes extraordinarily difficult to navigate without some chapter stops...

---

### Post by pathos_84 on 2009-11-11
> **darkkith said:**
> this is all great, but the primary issue i end up with is no bookmarks, or chapters in the resulting m4b.  for a short audiobook this isn't much of a problem, but a standard audiobook, say 5hrs+ long, it becomes extraordinarily difficult to navigate without some chapter stops...

I've encountered the same problem and posted this thread:
[http://ubuntuforums.org/showthread.php?p=8291719](http://ubuntuforums.org/showthread.php?p=8291719)

I include a much simpler way of performing the same operations outlined here, and link to a Windows (icky) tool which bookmarks the resulting m4a's. Cheers!

---

### Post by ztrange on 2009-12-01
Ok, maybe I'll be attacked by all the windows haters but here I found a possible solution. I havent tested it yet; it is currently downloading. It may be for windows but it is open source; the source con be found in the download section

[http://www.freeipodsoftware.com/download.php]("http://www.freeipodsoftware.com/download.php")

Edit: Tested it with wine and it works. However, opened the resulting file with vlc and cannot see the chapters divisions. I'll try it with an ipod.
Edit2 (or 3...): Another Windows utility "Chapter Master" does the trick with chpater markers. However it requires Quicktime and .NET Framework 2 to work. I found it on warez-bb forums and is in my download list so maybe I'll use it in my audiobooks on my Vbox XP.

Anyway, I could not find any other way to add chapter permanent bookmarks to m4b files. Hope this may help someone.

---

### Post by jfroebe on 2009-12-25
I recently figured out how to create iTunes/iPod compatible audiobooks (m4b) with chapters only using free software (MP4Box and mp4v2).  :)  

[How to create an iTunes/iPod compatible audiobook (MPEG4 m4b) on Linux using MP4Box and mp4v2 v1.9.1]("http://froebe.net/blog/2009/12/24/how-to-create-an-itunesipod-compatible-audiobook-mpeg4-m4b-on-linux-using-mp4box-and-mp4v2-v1-9-1-it-can-be-done/")

I haven't figured out how to add individual images per chapter ... yet.

jason

---

### Post by crabman on 2010-03-16
Ive recently written a Howto that makes use of a GUI, so might be easier for some users. Check it out:

[http://ubuntuforums.org/showthread.php?t=1431384](http://ubuntuforums.org/showthread.php?t=1431384)

---

### Post by boros1124 on 2010-11-25
Whether you have a very good inexpensive way to purchase audio books. Here it is, for example:
[http://konyv-konyvek.hu/a_magyar_lelek](http://konyv-konyvek.hu/a_magyar_lelek)
Hungary has 48 songs on it. Also a nice Christmas gift.;)

Akár már olcsón vásárolhattok nagyon jó hangoskönyveket. Itt van például ez:
48 magyar dal van rajta. Karácsonyra is szép ajándék lehet.

---

### Post by Sir_Yaro on 2011-05-28
new version available at first post

---

### Post by igrowingbaby on 2011-12-27
Just google search **Step by Step Guide on How to Convert M4B to MP3 as well as Split M4B with the Powerful M4B to MP3 Converter**
 you will find a simple solution

---

