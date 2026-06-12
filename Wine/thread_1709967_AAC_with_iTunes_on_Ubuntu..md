---
title: "AAC with iTunes on Ubuntu."
date: 2011-03-19
forum: Wine
---

### Post by e-San on 2011-03-19
Today i am doing some small reserch on 'how to' create best audio quality on AAC.

I own small iPod Shuffle (2GB). Glad to know it supports m4a.
Everyone knows best encoder for aac is in iTunes.
(I won't do any tests, thy are made: [http://listening-tests.freetzi.com/Roberto/index.htm](http://listening-tests.freetzi.com/Roberto/index.htm) )

We all are linux freaks, so, yeah, meybe it would be easier to do it on windows but i prefer linux enywhere i can use it.

So, since there is no option to use encoder without installing iTunes, lets start.

I downloaded iTunes from apple's page and installed it.
Here [ on Wine's page]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=21302") are some usefull informations about how to install it. Most of those are out-of-date. 

Maybe usefull tips:
- do not turn on autorun
- while installing screen turnes black. simply hit alt+tab.
- for me, i do not have to swich wine to Windows 7 at any time
- did not have to install any of vcrun

So, iTunes is installed. Turn it on - it takes a while but should run at last. You may need to try to 'killall distnoted.exe AppleMobileDeviceHelper.exe'.
Configuration turnes on long while and it is quite useless...

To automate process i tried to use two 'helpers'.
[itunescoder]("http://www.shchuka.com/software/itunescoder/index.html#download"), but it failed. It starts quite well but iTunes won't end process since we kill it. iTunes ends encoding and mp4 is complete but it is useless since we want to automate process.

old [itunesencode46]("http://www.hydrogenaudio.org/forums/index.php?showtopic=35242"), which works fine. it starts and ends just fine. it does show even progress.

everything looks great but i have fev problems.
- it is not a big problem, but none of those wont output mp4's where i asked it for. there is no problem since they are put somewhere i.e. */home/san/.wine/drive_c/users/san/Moja muzyka/iTunes/iTunes Media/Music/Beck/Moulin Rouge!*.

- second and _real_ problem is i can not change any option about codecs. as i mentioned before changing options is useless. i tried to change bitrate to 192 without vbr (only place i found to do so is 'cd import') but iTunes seems to ignore it and does mp4 with bitrate 256 with vbr.

please, do not start off topics about 'i think that mp3@128 is good enought for me', ok? it does not matter.

I share this with you, beacose i think it is quite easy to do and meybe someone can help me to improve this process. maybe someone tried [iTunes COM for Windows SDK]("http://www.paraesthesia.com/archive/2009/05/20/itunes-com-for-windows-sdk-now-in-adc.aspx") or something like it.
Maybe someone knows where bitrate settings are saved in windows and we could import it to linux. 
Or, meybe, any other great ideas?

Best regards!
San

---

### Post by e-San on 2011-03-19
yeah, but what next?

i made very dirty script:

```
san@eeepc:~/Publiczny/sd/Ext01$ cat du
find -L -mindepth 3 -maxdepth 3 -type d  | while read i; do 
echo wchodz&#281; do "$i"
cd /home/san/Publiczny/sd/Ext01/"$i"

ls -1 | grep -i flac | while read flac; do
echo encoding "$flac"

flac "$flac" -o - | sox - -twav -o /dev/shm/"$flac".wav

wine /home/san/Pobrane/iTunesEncode46/iTunesEncode.exe -i /dev/shm/"$flac".wav

rm /dev/shm/"$flac".wav

done #album

cd /home/san/Publiczny/sd/Ext01

done[/quote]

short explanation:
first line is to enter every album. i have directory tree like A/Artist/Album

flac and sox combination is becose:
1. iTunes does not support flac (which is quite weird)
2. flac does not export to .wav.

now, i have to add something to support tags

fond this on [here]("http://ubuntuforums.org/showthread.php?t=1609760"):
[code]#!/bin/bash
for f in *.flac
do
OUTF=`echo "$f" | sed s/\.flac$/.m4a/g`

ARTIST=`metaflac "$f" --show-tag=ARTIST | sed s/.*=//g`
TITLE=`metaflac "$f" --show-tag=TITLE | sed s/.*=//g`
ALBUM=`metaflac "$f" --show-tag=ALBUM | sed s/.*=//g`
GENRE=`metaflac "$f" --show-tag=GENRE | sed s/.*=//g`
TRACKTOTAL=`metaflac "$f" --show-tag=TRACKTOTAL | sed s/.*=//g`
DATE=`metaflac "$f" --show-tag=DATE | sed s/.*=//g`
TRACKNUMBER=`metaflac "$f" --show-tag=TRACKNUMBER | sed s/.*=//g`

flac -c -d "$f" - | neroAacEnc -if -  -cbr 320000 -of  "$OUTF"
neroAacTag "$OUTF"  -meta:artist="$ARTIST" -meta:title="$TITLE" -meta:album="$ALBUM" -meta:genre="$GENRE" -meta:year="$DATE" -meta:track="$TRACKNUMBER" -meta:totaltracks="$TRACKTOTAL"
done
mkdir "$ALBUM" && mv *.m4a "$ALBUM"
```

---

