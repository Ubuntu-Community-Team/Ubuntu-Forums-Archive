---
title: "HOWTO: convert wma to mp3"
date: 2005-05-28
forum: Tutorials
---

### Post by mtron on 2005-05-28
This small script is for former Windows useres, who want to convert their **not DRM "protected" wma's** to mp3s. 

Why? 
- some portable music players don't support it
- it's micro$oft. isn't that enough  ;-) ?

Requirements:
[mplayer](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Player_.28Mplayer.29_with_plug-in_for_Mozilla_Firefox) ,[win32 codecs](https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5) and [lame](http://wiki.ubuntu.com/RestrictedFormats) 


but remember: every de- and recoding usually results in a loss of quality, so if you have the original CD,
 rip it again, and do not recode the wma's to mp3's. 

Open a Terminal

Type:
```
cd ~/.gnome2/nautilus-scripts
```

Type:
```
gedit convert\ wma\ to\ mp3
```

# Paste the following code into the file:
```
#! /bin/sh
# wma to mp3 script by mtron
zenity --info \
        --text="this script converts all wma files in the current folder
to mp3s and puts them in the folder output 

all lame command line options can be set in the next step. 

usage:
	lame -m s: for stereo mp3 output
	lame -m s V 3-4-5: for stereo mp3 output with VBR"

# Dialog box to choose output quality
FORMAT=`zenity --list --title="Choose mp3 output quality" --radiolist --column="Check" --column="Quality (editable)" --editable "" "lame -m s" "" "lame -m s -V 3" "" "lame -m s -V 4" "" "lame -m s -V 5"`

if [ $FORMAT -eq ""]; then    
zenity --error --text="mp3 output quality not defined or no wma file found

usage:
	lame -m s: for stereo mp3 output
	lame -m s V 3-4-5: for stereo mp3 output with VBR 
 
type: lame --longhelp 
for all command line options "
exit 1
fi

mkdir -p output
cp *.wma output
cd output

# How many files to make the progress bar
PROGRESS=0
NUMBER_OF_FILES=`find -iname "*.wma"`
let "INCREMENT=100/$NUMBER_OF_FILES"

#remove spaces
(for i in *.wma; do mv "$i" `echo $i | tr ' ' '_'`; done

#remove uppercase
for i in *.[Ww][Mm][Aa]; do mv "$i" `echo $i | tr '[A-Z]' '[a-z]'`; done

#Rip with Mplayer / encode with LAME
for i in *.wma ; do 
echo "$PROGRESS";
echo "# Re-Coding $i";
mplayer -vo null -vc dummy -af resample=44100 -ao pcm:waveheader $i && $FORMAT audiodump.wav -o $i;
let "PROGRESS+=$INCREMENT"
done

#convert file names
for i in *.wma; do mv "$i" "`basename "$i" .wma`.mp3"; 
done

rm audiodump.wav
let "PROGRESS+=$INCREMENT"
) | zenity  --progress --title "$Recoding...encoding..." --percentage=0
```

Save the file, and quit gedit.
Back in the terminal type:

```
chmod +x convert\ wma\ to\ mp3
```

navigate in nautilus to the folder containing the wma's, right click, choose "scripts" and "convert wma to mp3" 
it takes ca. 3 min for one wma. This script will not delete your wma's. all mp3 will be put to the new created folder output. (check that your user has write support in the directory!)

you can set the lame encoder settings in the zenity dialog box. all lame switches are supported, like

lame -m s: for stereo mp3 output
lame -m s V 3-4-5: for stereo mp3 output with VBR"


Credits: to [c m](http://www.ubuntuforums.org/showthread.php?t=33227) 

Have fun!

---

### Post by bored2k on 2005-05-28
Cute.
What about ape to mp3 or mpc ?

---

### Post by Gouchi on 2005-05-28
Maybe some tools in here :

[http://rarewares.org/debian.html](http://rarewares.org/debian.html)

sure for mpc and mp3 but Monkey Audio ?

---

### Post by mtron on 2005-05-28
i'm sorry, i don't have one single ape file...

but when mplayer is able to play it, the script needs onlya small modification. the same for ogg, 

Perhaps i will make a version to choose the input - and output format. 
for wma, mp3 and ogg it should not be a big problem, but i need to figure out how to use the zenity radiobox input further in the script. Not only the $FOMAT variable.

when you set the 
FORMAT=... "mp3" "" "ogg" "" "ape"

you can't use it later wit the switches
if [ $FORMAT -eq "mp3"]; then
or 
if [ $FORMAT -eq "ogg"]; then 

or at least i could not. Someone an idea how to do this?

---

### Post by Lovechild on 2005-05-28
If there's support for wma in gstreamer I would like to add that the following converts wma to ogg vorbis:

gst-launch-0.8 filesrc location=path-to-file/name-of-file.wma ! spider ! vorbisenc ! filesink location=path-to-file/name-of-destination-file.ogg

for mp3 conversion replace vorbisenc with lame bitrate=128 and of course change postfix to mp3.

---

### Post by Steve Kinney on 2006-08-05
How to convert ape to mp3?  Off topic for the thread, but a searching for it landed me here, so here 'tis:  I ran into that .ape problem last night, and this brute force method worked out OK:

Go to [www.monkeysaudio.com](www.monkeysaudio.com) and download the author's Win32 binary tool for converting into and out of .ape format.  (Gratis but not free, hence the lack of a Linux package.)  Drop the installer in some convenient location, and run it with "WINE Windows emulator".  This will install the software into a hidden directory tree in your /home/[user] that spoofs a standard Windows file system.  

If your shell command options don't include WINE and Wine Windows Emulator, you may have to install these as well.  No sweat, just use Synaptic or your favorite package manager.

Once Monkey Audio is installed, fire up your favorite file navigator, set it to show hidden files, and navigate to the ".wine/drive c/program files/Monkey's Audio/" directory, where you will find "Monkey's Audio.exe"  Open  up the app and ... just do it.

I also installed soundKonverter so I could take the .wav files Monkey handed me and conveniently batch convert them to MP3.  (You will also need LAME if it is not already installed.)  It's native to KDE but works fine under Gnome, at least on my system.

---

### Post by theadventuresofanidealist on 2006-08-30
i did all you asked but it doesnt work for me.
it says converting but then the folder output is empty.
is there something relating to it i need to install?

---

### Post by exactt on 2006-09-06
the trick is to use the script INSIDE the folder. I first also tried to do things on the top folder...

but it would be a nice feature...

---

### Post by danderson3 on 2006-09-06
pacpl does all of this and more.  a new version was
just released.  see [http://viiron.googlepages.com/home](http://viiron.googlepages.com/home)

-David

 Perl  Audio  Converter  (PAC)  is a tool for converting multiple audio
        types  from  one  format to another. It supports MP2, MP3, Ogg Vorbis,
        FLAC,  Shorten,  Monkey  Audio,  FAAC  (AAC/M4A/MP4),  Musepack (MPC),
        Wavpack  (WV), OptimFrog (OFR/OFS), TTA, LPAC, Kexis (KXS), AIFF, AC3,
        Lossless Audio (LA), BONK, AU, SND, RAW, VOC, SMP, RealAudio (RA/RAM),
        WAV,  and  WMA.  It  can  also  convert audio from the following video
        formats/extensions:  RM, RV, ASF, DivX, MPG, MKV, MPEG, AVI, MOV, OGM,
        QT,  VCD, VOB, and WMV. A CD ripping function with CDDB support, batch
        and  playlist conversion, tag preservation for most supported formats,
        independent  tag  reading/writing,  and  extensions  for Konqueror and
        amaroK are also provided.

---

### Post by exactt on 2006-09-06
there is a bug in the script:

mplayer -vo null -vc dummy -af resample=44100 -ao pcm -waveheader $i && $FORMAT audiodump.wav -o $i; 

needs to get

mplayer -vo null -vc dummy -af resample=44100 -ao pcm:waveheader $i && $FORMAT audiodump.wav -o $i;

...at least on dapper with the latest updates installed. otherwise the files just get renamed.

---

### Post by aev on 2006-11-12
to encode wma to mp3 just do this:

wma to wav:
      
```
>mplayer -ao pcm:output-file-name.wav input-file-name.wma
```

and then wav to mp3:

```
>mplayer -ao pcm:output-file-name.mp3 input-file-name.wav
```


I got this from the mplayer manual. :mrgreen:

---

### Post by boast on 2006-12-05
this just creates an empty folder called output.

---

### Post by mtron on 2006-12-06
this was posted a long time ago (may 2005) and worked for hoary (or was it even for warty?)

anyway, will update it asap. but first i need to get some shitty wma files...

**_EDIT:_ Just tested it. The script works good.** Are you trying to convert a DRM'ed wma? this won't work ! You need to remove the drm first. googe for it, there are ways to do it ;) & you need to run the script in the same folder with the wma files

---

### Post by nismoskys on 2006-12-12
[http://zamzar.com/]("http://zamzar.com/") :D

---

### Post by mtron on 2006-12-13
very cool!

---

### Post by loyd86 on 2007-01-08
Is anyone else having troubles with this killing the tags on files?

---

### Post by melusyne on 2007-01-24
Hi everyone :

first, thanks for this little wonder ! just perfect to get rid of those win files...

a few observations (i hope constructive ones)

- for the newbs (and i consider myself right in this category) you could add in the how-to that : in case this is the first script added to nautilus, the script-menu won't show up until the next X-session is launched. (i couldn't find it, and started to think it didn't work when i suddenly tried the good old Ctrl+Alt+Del to update everything)

- the new MP3 files don't have any tags any more (you could just add it in the description, since i imagine it wouldn't be that simple to enlarge the script in order to save them)

- the progress bar doesn't work for me: it stays white all the way long and suddenly fills up when all the work is done. (same for multi-files usage : when all are done)

all these are just result of a first usage, but i'm looking forward to use it a fex times more :)

regards

---

### Post by Reitermaniac on 2007-02-22
WMA to MP3? Some weeks ago I purchased [Soundtaxi]("http://www.soundtaxi.info") and had great success with converting all my wma files to mp3. Those wma's were drm-protected!

---

### Post by randell6564 on 2007-05-26
> **danderson3 said:**
> pacpl does all of this and more.  a new version was
just released.  see [http://viiron.googlepages.com/home](http://viiron.googlepages.com/home)

-David

 Perl  Audio  Converter  (PAC)  is a tool for converting multiple audio
        types  from  one  format to another. It supports MP2, MP3, Ogg Vorbis,
        FLAC,  Shorten,  Monkey  Audio,  FAAC  (AAC/M4A/MP4),  Musepack (MPC),
        Wavpack  (WV), OptimFrog (OFR/OFS), TTA, LPAC, Kexis (KXS), AIFF, AC3,
        Lossless Audio (LA), BONK, AU, SND, RAW, VOC, SMP, RealAudio (RA/RAM),
        WAV,  and  WMA.  It  can  also  convert audio from the following video
        formats/extensions:  RM, RV, ASF, DivX, MPG, MKV, MPEG, AVI, MOV, OGM,
        QT,  VCD, VOB, and WMV. A CD ripping function with CDDB support, batch
        and  playlist conversion, tag preservation for most supported formats,
        independent  tag  reading/writing,  and  extensions  for Konqueror and
        amaroK are also provided.
Hey thanks!  I think this is what I'm looking for, but is it a GUI app?  In other words, can I drag a .wma file into it and get an .mp3 comin' out the other side?

---

### Post by randell6564 on 2007-05-26
Well, I installed 'pacpl' and got this error when I tryed to start it from terminal:
> bigboss@bigboss-desktop:~$ pacpl

Perl Audio Converter - v3.3.1

There was an error loading: MP4::Info.
Install the module or set USETAGS to 0 in conf file.

No such file or directory
Anyone know how to correct this?  Heres what I want to do.  I have alot of music on my Windows partition in .wma format.  Rhythmbox will not play them, xmms will not play them, so I want to convert them to a format that is playable on my Ubuntu desktop.

---

### Post by janne_oksanen on 2007-05-28
> **Reitermaniac said:**
> WMA to MP3? Some weeks ago I purchased [Soundtaxi]("http://www.soundtaxi.info") and had great success with converting all my wma files to mp3. Those wma's were drm-protected!

You're plugging a Windows app here? How nice and trolly of you.

EDIT: corrected typo

---

### Post by randell6564 on 2007-05-28
> **janne_oksanen said:**
> You're plugging a Windows app here? How nice and trolly of you.

EDIT: corrected typo
LMAO! This is exactly NOT what I was looking for!  'SoundTaxi' Humf!!  I'm running Linux!  I want to convert my .WMA files, copied over from Windoze XP into playable formats in Ubuntu Feisty.

---

### Post by kevpatts on 2007-06-02
Very useful, thanks man

Kevpatts

---

### Post by musicatplay on 2007-06-15
I'm new to using Ubuntu Linux (Feisty) but I have been reading through a bunch of message boards and forums to find a GUI tool to convert my old WMA files to MP3 with little luck.  I stumbled upon a thread on Softpedia which mentioned [SoundConverter]("http://linux.softpedia.com/get/Multimedia/Audio/Sound-Converter-3407.shtml") for the Gnome desktop.  I was going to download the package directly from the site and try my luck with installing the compressed package when I thought about searching in the Synaptic Package Manager for it and there it was!  No scripts, no compiling or tarball installations, just a nice, clean, managed installation to help all of us Newbs with our transition from M$ world!  

:: PLEASE NOTE THAT THIS WILL **NOT** CONVERT DRM-PROTECTED WMA FILES ::


Installation Instructions:

[LIST]
[*]Click System --> Administration --> Synaptic Package Manager
[*]Type in your administrative password
[*]Click the "Search" button and type "SoundConverter" in the text field
[*]Right-click on the "SoundConverter" package name in the main window and select "Mark for Installation"
[*]Click the "Apply" button to begin installation
[/LIST]

All dependent packages should install automatically by using this installation method.  If you need more info on the SoundConverter program visit their website [here]("http://soundconverter.berlios.de/").


Notes:

[LIST]
[*]Conversion process is quite slow (took about an hour to convert 263 wma files on my machine to 192Kb mp3 format)
[*]Conversion results in loss of fidelity as you are converting a "lossy" format to another "lossy" format.  Use source audio CD's / "lossless" files if possible for best results
[/LIST]

Happy transitions to computing freedom!!

---

### Post by randell6564 on 2007-06-15
Well done 'musicatplay'.  Thank You!
I use 'MuvAudio2' and 'TuneBite' when logged onto my Windoze DT.  (Had to pay for both.)  I would rather not USE Windoze at all for my music needs, so I was looking for something like this!  Thanks Again!

---

### Post by johnnyspire on 2007-06-16
This is a nice framework to get you started. I use Kubuntu (not to brag) which needed a LOT of Gnome stuff when I tried to Aptitude in zenity. I read the package description for Zenity and decided I didn't need graphical help to convert batches of wma files.

Be sure you've installed mplayer and lame. I also installed ffmpeg and I see that it's using it.

I edited the script as follows:

```
#! /bin/sh
# wma to mp3 script

mkdir -p converted_mp3
cp *.wma converted_mp3
cd converted_mp3

# How many files to make the progress bar
PROGRESS=0
NUMBER_OF_FILES=`find -iname "*.wma"`

#remove spaces
for i in *.wma; do mv "$i" `echo $i | tr ' ' '_'`; done

#remove uppercase
for i in *.[Ww][Mm][Aa]; do mv "$i" `echo $i | tr '[A-Z]' '[a-z]'`; done

#edit this if you need to change the options for lame encoding to mp3
FORMAT='lame -h -m s'

#Rip with Mplayer / encode with LAME
for i in *.wma ; do
echo "$PROGRESS";
echo "# Re-Coding $i";
mplayer -vo null -vc dummy -af resample=44100 -ao pcm:waveheader $i && $FORMAT audiodump.wav -o $i;
done

#convert file names
for i in *.wma; do mv "$i" "`basename "$i" .wma`.mp3";
done

rm audiodump.wav

exit 0

```

Now another good idea is setup a cron task to run this in a specific folder every night. That way you can drop stuff in and forget it.

---

### Post by fujikofujio on 2007-09-11
Wow!!! This worked great, I tried that perl converter and it didn't work, had the same error as the other guy complaining about MP4::info, soundconverter worked like a charm and converted all my wma's to mp3 :)


> **musicatplay said:**
> I'm new to using Ubuntu Linux (Feisty) but I have been reading through a bunch of message boards and forums to find a GUI tool to convert my old WMA files to MP3 with little luck.  I stumbled upon a thread on Softpedia which mentioned [SoundConverter]("http://linux.softpedia.com/get/Multimedia/Audio/Sound-Converter-3407.shtml") for the Gnome desktop.  I was going to download the package directly from the site and try my luck with installing the compressed package when I thought about searching in the Synaptic Package Manager for it and there it was!  No scripts, no compiling or tarball installations, just a nice, clean, managed installation to help all of us Newbs with our transition from M$ world!  

:: PLEASE NOTE THAT THIS WILL **NOT** CONVERT DRM-PROTECTED WMA FILES ::


Installation Instructions:

[LIST]
[*]Click System --> Administration --> Synaptic Package Manager
[*]Type in your administrative password
[*]Click the "Search" button and type "SoundConverter" in the text field
[*]Right-click on the "SoundConverter" package name in the main window and select "Mark for Installation"
[*]Click the "Apply" button to begin installation
[/LIST]

All dependent packages should install automatically by using this installation method.  If you need more info on the SoundConverter program visit their website [here]("http://soundconverter.berlios.de/").


Notes:

[LIST]
[*]Conversion process is quite slow (took about an hour to convert 263 wma files on my machine to 192Kb mp3 format)
[*]Conversion results in loss of fidelity as you are converting a "lossy" format to another "lossy" format.  Use source audio CD's / "lossless" files if possible for best results
[/LIST]

Happy transitions to computing freedom!!

---

### Post by petit_prince on 2007-11-05
Hi everyone,

check out this solution, it doesn't require the intermediate wave file:
[http://ubuntuforums.org/showthread.php?p=3712276#post3712276](http://ubuntuforums.org/showthread.php?p=3712276#post3712276)

All best,
Dan

---

### Post by eyemean on 2007-12-17
cheers musicatplay for soundcoverter, its done the trick for me.

---

### Post by babil on 2008-01-04
**audio-converter**
[http://linux.softpedia.com/get/Multimedia/Audio/Audio-Convert-3104.shtml](http://linux.softpedia.com/get/Multimedia/Audio/Audio-Convert-3104.shtml)

it's a bash script ... 'n works pretty good

---

### Post by rykel on 2008-01-09
> **danderson3 said:**
> pacpl does all of this and more.  a new version was
just released.  see [http://viiron.googlepages.com/home](http://viiron.googlepages.com/home)

-David



I am interested in trying out PAC... but where is the installer file for Ubuntu Gutsy? Is an autopackage available? Please advise? Thanks!

---

### Post by kris_a on 2008-01-14
Not to knock the good work you have done here, I used it to convert some files and it worked fine.
The only problem I found is that it doesn't deal with the tags for files, so I went hunting for a different solution, and it works so well I had to post it here...

It's called [PACPL]("http://viiron.googlepages.com/home"), it's not in the repositories but the debian package from the website works fine for me. It makes you answer some questions during the installation so make sure you expand the install window to show the installer text.

I haven't used the Amarok integration as I don't have KDE, but the command line one worked a treat for me, just do:

pacpl --to mp3 --bitrate 128 -r *.wma

to go recursively through all your directories converting wma's to mp3's at 128k.
It keeps your tag info as well!

Hope that helps somebody,
Kris.

---

### Post by vette95 on 2008-01-15
The easiest way I found to convert from was with "OGGConvert", although it only converts media to .OGG. It has to be done one fie at a time :roll:, but since it is much easier for new linux users like myself to use a graphical interface, I guess this should take a little load off of some of us.

I certainly hope this helps a lot of us, and I am always willing to listen to other people's ideas, I'm as much a rookie at Linux as the next newby.

---

### Post by codecaine on 2008-03-16
Heres what I did I used ffmpeg

for i in *.wma; do
ffmpeg -sameq -i "$i" "`basename "$i" .wma`.mp3"; 
done

write this in vi or any text edit
chmod +x the filename you save it as
mv filename /usr/bin
cd to the directory of yoru wma files then run the script
if you want to delete the .wma files just type 
rm *.wma

---

### Post by th_agorastos on 2008-04-08
pacpl rocks! I just installed and used it successfully.

Note you may have to install a few additional packages - nothing special.

---

### Post by lapichiflati on 2008-04-10
I tried this code above:
```
for i in *.wma; do ffmpeg -sameq -i "$i" "`basename "$i" .wma`.mp3"; done
```
But I got ```
Input #0, asf, from '01_Bach.wma':
  Duration: 00:02:49.9, start: 1.578000, bitrate: 129 kb/s
  Stream #0.0: Audio: wmav2, 44100 Hz, stereo, 128 kb/s
Output #0, mp3, to '01_Bach.mp3':
  Stream #0.0: Audio: mp3, 44100 Hz, stereo, 64 kb/s

```

Output at 64 kbs from input of 128, obviously not the desired effect.  I would like to run this as a batch but I have many wma files of different bitrates so I would rather not use the -b switch to specify the bitrate since the -sameq switch doesn't seem to want to output to the same bitrate.  Any idears?

---

### Post by brnbock on 2008-05-26
This script does not work for me:(. When the script is activated it only takes a few seconds for the conversion to complete but the files are still listed as WMA version 8. I burn it as an MP3 cd and the cd player will not play them. Any help would be appreciated. And yes lame is installed.

Thanx

---

### Post by brnbock on 2008-05-31
Duh...I am an idot [http://ubuntuforums.org/images/smilies/icon_redface.gif](http://ubuntuforums.org/images/smilies/icon_redface.gif) ! Read the forums and the answers will come! :) SoundConverter works great! LLU (LongLiveUbuntu) [http://ubuntuforums.org/images/smilies/biggrin.gif](http://ubuntuforums.org/images/smilies/biggrin.gif)

---

### Post by polytropos on 2008-08-20
I'm trying to use pacpl but am not having any luck.  I don't think I've installed it properly.  In a terminal, I tried this command:

pacpl --to mp3 --bitrate 128 -r *.wma

And I got this response:

Can't locate Ogg/Vorbis/Header.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/bin/pacpl line 29.
BEGIN failed--compilation aborted at /usr/bin/pacpl line 29.

Any help?

---

### Post by davidryder on 2008-09-17
Thanks dude, worked perfectly

---

### Post by KayMyst on 2008-10-02
amazing script bravo

---

### Post by psm22 on 2008-12-09
:guitar:
The script on the first page worked fine for me from inside the orig wma folder (I'm using Hardy 8.04).
Thanks and respect!

---

### Post by Raymond Day on 2009-03-19
It worked very good for me. Here is a copy and paste of how it looks.

```
for i in *.wma; do ffmpeg -sameq -i "$i" "`basename "$i" .wma`.mp3"; done
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
Input #0, asf, from '0312.wma':
  Duration: 01:44:31.8, start: 3.000000, bitrate: 48 kb/s
    Stream #0.0: Audio: wmav2, 44100 Hz, mono, 48 kb/s
Output #0, mp2, to '0312.mp3':
    Stream #0.0: Audio: mp2, 44100 Hz, mono, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
```

I guess 48 kb/s in .wma is about the same as 64 kb/s in .mp3

-Raymond Day

---

### Post by trystan.lea on 2009-04-28
Thanks! This worked great for me :)

---

### Post by bettlebrox on 2009-04-28
Now there's a Nautilus script that does this:

```
apt-cache show nautilus-script-audio-convert
Package: nautilus-script-audio-convert
Priority: optional
Section: universe/sound
Installed-Size: 100
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Lukas Fittl <lfittl@ubuntu.com>
Architecture: all
Source: audio-convert
Version: 0.3.1.1-0ubuntu4
Depends: file, gawk | mawk, nautilus-script-manager, zenity
Suggests: faac, faad, flac, lame, mplayer | mplayer-nogui, vorbis-tools
Filename: pool/universe/a/audio-convert/nautilus-script-audio-convert_0.3.1.1-0ubuntu4_all.deb
Size: 15612
MD5sum: e0fa7ee5eddd5755f7c7bc3565c6c6a9
SHA1: 7dd90bc2c35c8137fb98c3e0eefa92ec3c7b3fa5
SHA256: 0c4ea641b3e4b12952ddc88f55b8bda22eaa41919c93a3734406772389177bb4
Description: A nautilus audio converter script
 audio convert is a script that converts between WAV, Ogg, MP3, MPC, FLAC, APE,
 AAC, and WMA files. It has an easy-to-use interface that makes it possible to fill in the tags for a few formats, copy the tags from input files into the new files, and choose the quality of compression.
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu

```

Install it with:

```
sudo apt-get install  nautilus-script-audio-convert
```

---

### Post by drjnet on 2009-05-29
> **bettlebrox said:**
> Now there's a Nautilus script that does this:

```
apt-cache show nautilus-script-audio-convert
Package: nautilus-script-audio-convert
Priority: optional
Section: universe/sound
Installed-Size: 100
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Lukas Fittl <lfittl@ubuntu.com>
Architecture: all
Source: audio-convert
Version: 0.3.1.1-0ubuntu4
Depends: file, gawk | mawk, nautilus-script-manager, zenity
Suggests: faac, faad, flac, lame, mplayer | mplayer-nogui, vorbis-tools
Filename: pool/universe/a/audio-convert/nautilus-script-audio-convert_0.3.1.1-0ubuntu4_all.deb
Size: 15612
MD5sum: e0fa7ee5eddd5755f7c7bc3565c6c6a9
SHA1: 7dd90bc2c35c8137fb98c3e0eefa92ec3c7b3fa5
SHA256: 0c4ea641b3e4b12952ddc88f55b8bda22eaa41919c93a3734406772389177bb4
Description: A nautilus audio converter script
 audio convert is a script that converts between WAV, Ogg, MP3, MPC, FLAC, APE,
 AAC, and WMA files. It has an easy-to-use interface that makes it possible to fill in the tags for a few formats, copy the tags from input files into the new files, and choose the quality of compression.
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu

```

Install it with:

```
sudo apt-get install  nautilus-script-audio-convert
```

Thanks for this mate, i battled with the other scripts for a while to no effect but this works sweet so thanks!!

---

### Post by designzinthesun on 2010-02-06
The script on the first page worked for me converting wma to mp3 in Ubuntu 9.04. Thanks!

---

### Post by whiskey.will on 2010-03-13
New to Ubuntu from XP, and I have about oh... 45Gigs of WMA files, do you see my problem?  Well I tried the actions recommended in the beginning of the thread and got as far as the "right click" when I do right click I see the script option with "WMA to MP3".  When I select this though nothing happens, I mean an "output" folder is created and I press OK confirming is has just recoded the files but theres none in the output folder?  If you have a clue how to help me here I would truly appreciate it...

---

### Post by oldmankit on 2010-04-28
I downloaded a supported program (Perl Audio Converter) and it works fine.  Keeps tags, recurses directories, very professional.  It's got several releases and so people have clearly put a lot of time and thought into making it work well.

Because I use dialup at home I got a small download using the no-install-recommends option like this:

```
sudo apt-get install --no-install-recommends pacpl
```

---

### Post by robinlovelace on 2010-10-23
This thread is out of date! It's now super easy and even a Linux cretin like me can make it work. Just go into Applications, open the "Ubuntu Software Centre", search for "Sound Converter", download the program with this name. Then use it (also find it in Applications, guess where).

I'm amazed how well this works. Better than any proprietary alternative I've tried, super fast, loads of settings and easy (see Screenshot attachment). Now I see why it's called Linux for human beings.

Spread the Ubuntu word (see Poster attachment), Robin

---

### Post by Hilko on 2010-11-23
Thanks! The 'Sound Converter' app is just what I was looking for. It's perfect !

---

### Post by jandrioli on 2010-11-24
I’ve been struggling to find a way to do this without mplayer.
It’s been a pain the the a** to get it to a reasonably productive state, but this is how it goes:

1-run the command below to generate a script which will convert your files

2-check the script for apostrophes or single quites or double quotes in the names of your files

3-run the script

```

find -L /path/to/your/mp3/library -iname *.wma -exec echo 'vlc -v  "{}" --sout '\'#transcode{acodec=mp3}:standard\{access=file,dst=\"{}.mp3\",mux=ffmpeg\}\''' \; >> batch_wma2mp3.sh; chmod u+x batch_wma2mp3.sh;

```

**[COLOR="Red"]NB.: [/COLOR]**you must have ffmpeg installed. If you have DRM protected files, there will be no way to decrypt them with VLC neither with Mplayer. I didn't add the vlc://quit at the end of each command call coz sometimes it will mess up the playlist and just quit without converting the song, that's why you have to close VLC manually.

---

### Post by Mka on 2011-11-12
Try giving ftransc a shot, web site: [http://code.google.com/p/ftransc/](http://code.google.com/p/ftransc/)

ftransc uses ffmpeg to decode any audio/video file and pipe the wav file to either lame, faac, mppenc, oggenc to encode to MP3, WMA, MPC, OGG, AAC formats.

---

