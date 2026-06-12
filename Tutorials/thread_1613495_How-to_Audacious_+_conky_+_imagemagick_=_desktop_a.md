---
title: "How-to: Audacious + conky + imagemagick = desktop audio info + album art"
date: 2010-11-04
forum: Tutorials
---

### Post by a.sarkar on 2010-11-04
This how-to explains how to get audio info with conky on your desktop along with album art when playing music via audacious. Check screenshot before you begin any further.
Even though the shell script is for audacious, the script can be modified for other audio players like rhythmbox and amarok etc...

The script assumes that each of your music album folder has a file folder.jpg in them.
[COLOR=Blue]The script's biggest feature is that the conky window along with background will only appear when audacious is playing music. Otherwise it will stay invisible.[/COLOR] 
**Disclaimer:**
1) I originally found a shell script by user [EMAIL="eirc.eirc@gmail.com"]eric[/EMAIL] written for amarok. However I have extended the code extensively, so that calling it via conky becomes easier.

2) The imagemagick (IM) codes are  taken from imagemagick [website]("http://www.imagemagick.org/Usage/thumbnails/#rounded"). The IM code mainly draws the semi-transparent window with rounded corners. A more generic way of making semi-transparent window with rounded corners can be done with the great lua script written by user londonali1010  which can be found [here]("http://conky-pitstop.wikidot.com/londonali1010"). [COLOR=Blue]However if I use this script then the conky window doesn't disappear when audacious is not playing.[/COLOR] This is what started me in writing this shell script.

**Requirements:**
Conky (version 1.7.1+), imagemagick, audacious

```
sudo apt-get install imagemagick conky-all audacious
```**Installation:**
_STEP - 1:_
Save the script below as audacious-info.sh
```

#!/bin/bash

## TODO:
## *) Get album art (from web) at each album change (not song change).
## *) Draw background at each song change (not every 3secs).
## *) Create headphones.jpg or something equivalent via imagemagick 
##      on-the-fly

## Author: Anjishnu Sarkar
## Version: 1.0
## Acknowledgement(s):
## *) The imagemagick code to create round background is from the website
##      http://www.imagemagick.org/Usage/thumbnails/#rounded

## Feature(s):
## *) The conky window disappears when audacious is not playing.

## Info:
## *) The script assumes you have an image "folder.jpg" in each of your 
##      music albums.

## Installation:
## *********************
## chmod +x audacious-info.sh
## mkdir -p ~/.conky/shell-scripts/
## mkdir -p ~/.conky/pix/
## cp audacious-info.sh ~/.conky/shell-scripts/

## Next create a music.conkyrc. Copy the following relevant conky parts 
## in ~/.conky/music.conkyrc
## ***************************
## minimum_size 325 120
## text_buffer_size 2048
## imlib_cache_size 0
## border_outer_margin 10
## TEXT
## ${if_running audacious}${execpi 3 ~/.conky/shell-scripts/audacious-info.sh}${endif}
## *********************

Corners=10
Opacity=0.75
BGColor='grey'  ## '#bebebe'
# BGColor='#0000ff'
AlbumArt="folder.jpg"
BackUpArt="headphones.jpg"

## Do not change anything after this
CharLength=7
StaticWidth=127
MinWidth=335
Height=118
WordCount=0

ListPosition=$(audtool playlist-position)
Status=$(audtool playback-status)
EchoStatus="Audacious is $Status"

Title=$(audtool playlist-tuple-data title "$ListPosition")
if [ -z "$Title" ];then
    Title=$(basename "$(audtool playlist-song-filename \
            "$ListPosition")" .mp3 | sed 's/%20/ /g')
fi
TitleCount=$(echo "Title: "$Title"" | wc -m)

Album=$(audtool playlist-tuple-data album "$ListPosition")
AlbumCount=$(echo "Album: "$Album"" | wc -m)

Artist=$(audtool playlist-tuple-data artist "$ListPosition")
ArtistCount=$(echo "Artist: "$Artist"" | wc -m)

for varcount in $TitleCount $AlbumCount $ArtistCount 
do
    if [ $varcount -gt $WordCount ];then
        WordCount=$varcount
    fi
done

VarWidth=$(echo "${WordCount}*${CharLength}" | bc)
Width=$(echo ""$StaticWidth"+"$VarWidth"" | bc)

if [ $Width -le $MinWidth ];then
    Width=$MinWidth
fi

mkdir -p ~/.conky/pix/

DrawBG(){
    convert -size ${Width}x${Height} xc:${BGColor} \
        png:- | convert - \
         \( +clone  -threshold -1 \
            -draw "fill black polygon 0,0 0,"$Corners" "$Corners",0 \
            fill white circle "$Corners","$Corners" "$Corners",0" \
            \( +clone -flip \) -compose Multiply -composite \
            \( +clone -flop \) -compose Multiply -composite \
         \) +matte -compose CopyOpacity -composite  \
        -alpha on -channel RGBA -evaluate multiply ${Opacity} \
         ~/.conky/pix/audbg.png
}

GetArt(){
    FilePath=$(audtool playlist-tuple-data file-path \
                "$ListPosition" | sed 's/file:\/\///') 
    if [ -f "$FilePath"/"$AlbumArt" ];then
        cp "$FilePath"/"$AlbumArt" ~/.conky/pix/
    else
        cp ~/.conky/pix/"$BackUpArt" ~/.conky/pix/"$AlbumArt"
    fi
}

GetProgress(){
    CurrLen=$(audtool current-song-output-length-seconds)
    TotLen=$(audtool current-song-length-seconds)
    if (( $TotLen )); then
        ProgLen=$(expr $CurrLen \* 100  / $TotLen)
    fi
}

AudaciousInfo(){
    case "$1" in
        bg)         DrawBG ;;
        art)        GetArt ;;
        status)     echo "$EchoStatus" ;;
        title)      echo "$Title" ;;
        artist)     echo "$Artist" ;;
        album)      echo "$Album" ;;
        progress)   GetProgress ;;
    esac
}

# if 
    AudaciousInfo bg
    AudaciousInfo art
    echo -n "\${image ~/.conky/pix/audbg.png -p 0,0}"
    echo -n "\${image ~/.conky/pix/"$AlbumArt" -p 9,9 -s 100x100}"
    echo ""
    echo -n "                 "
    echo "\${color}$EchoStatus"
    echo ""
    echo -n "                 "
    echo -n "\${color}Title: "
    echo -n "\${color0}"
    AudaciousInfo title
    echo -n "                 "
    echo -n "\${color}Artist: "
    echo -n "\${color0}"
    AudaciousInfo artist
    echo -n "                 "
    echo -n "\${color}Album: "
    echo -n "\${color0}"
    AudaciousInfo album
    AudaciousInfo progress
    echo -n "                 "
    echo "\${execbar echo "$ProgLen"}"
    echo ""
# fi

```Make the script executable and save it in ~/.conky/shell-scripts
```

chmod +x audacious-info.sh
mkdir -p ~/.conky/shell-scripts/
cp audacious-info.sh ~/.conky/shell-scripts/

```_STEP - 2:_
Create a music.conkyrc with the following lines
```

# Conky sample configuration
#
background no
use_xft yes
xftfont Bitstream Vera Sans Mono:size=9
xftalpha 0.8
mail_spool $MAIL
update_interval 3.0
total_run_times 0
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
[COLOR=Blue]minimum_size 325 120[/COLOR]
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
stippled_borders 8
border_width 1

default_color yellow
color0 white
color1 green
color2 red
default_shade_color grey
default_outline_color yellow

alignment top_left
gap_x 140
gap_y 130

no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 2
override_utf8_locale no
use_spacer none
[COLOR=Blue]text_buffer_size 2048
imlib_cache_size 0[/COLOR]

# border_inner_margin 0
[COLOR=Blue]border_outer_margin 10[/COLOR]
TEXT
[COLOR=Blue]${if_running audacious}${execpi 3 ~/.conky/shell-scripts/audacious-info.sh}${endif}
[/COLOR]
```[COLOR=Blue][COLOR=Black]
I have marked the relevant part of the conkyrc in blue. Save it in the folder ~/.conky/ 

[U]STEP - 3:
[/U]Download and save the headphones.jpg in ~/.conky/pix folder. This image is an backup in case you don't have a folder.jpg in your music folders.
Installation complete.

[B]Run the script.
[/B]```

conky -c ~/.conky/music.conkyrc

```[COLOR=Blue]You won't see anything happening after you run the above command.[/COLOR]That's because you haven't played anything with audacious yet. Now start playing some music with audacious. A window will appear on your desktop, like shown in the screenshot, which shows your audio info along with you album art. Isn't that cool.
:guitar:

Hopefully you will find the script useful. 

[/COLOR][/COLOR]

---

### Post by statmonkey on 2011-05-24
Just stumbled across this.  Thanks for posting it.  Simple and elegant.  Most of the time people get too carried away with the candy and conky (a rabbit hole I have fallen into way too often) it's so fun to play with.

---

### Post by a.sarkar on 2011-05-24
Dear @statmonkey, 
Thanks for liking it :smile:.
I  had updated the script sometime back. Haven't posted it. The updated  script should work with any player that supports mpris-remote. This  includes amarok, audacious, qmmp, decibel-audio-player etc...

I will post the updated script and installation in a couple of days.

You are right - its fun to play with conky. :razz:

---

### Post by leodelacruz on 2011-06-24
Thanks man, good work! ;)

---

### Post by geazzy on 2011-06-24
great threads :)

---

### Post by RiccITA on 2011-12-29
Can I put this in my conky.rc or this is an independant conky?

---

### Post by a.sarkar on 2011-12-29
@ RiccITA: This is an independent conkyrc [URL="http://ubuntuforums.org/member.php?u=1518417"]
[/URL]

---

### Post by DobsonM on 2012-03-09
I can get the song description to display, but not the artwork :(

---

### Post by a.sarkar on 2012-03-10
@DobsonM

First covering couple of basic things:

1. You should have imagemagick installed.
2. There should be a file called folder.jpg in each of your music folder.

Now assumming you already had those, run the command
```
conky -c /path/to/your/music.conkyrc 
```in a terminal and then play any song in audacious. What is the output in the terminal?

---

### Post by Pazit on 2012-05-07
I need your advice on how to correct the issue i have in using your conky.
you can see the scrot below.
Thanks.

---

### Post by a.sarkar on 2012-05-07
@Pazit,

Thanks for reporting the bug. I recently upgraded from 10.04 to 12.04 and have the same issue. I haven't got around to fixing it - bit rushed at present. However I will get time this week and try to fix it then. 

I have upgraded the script not just to audacious, but to any MPRIS complaint player. Will post it once I am able to fix the above issue.

---

### Post by Pazit on 2012-05-08
> **a.sarkar said:**
> @Pazit,

Thanks for reporting the bug. I recently upgraded from 10.04 to 12.04 and have the same issue. I haven't got around to fixing it - bit rushed at present. However I will get time this week and try to fix it then. 

I have upgraded the script not just to audacious, but to any MPRIS complaint player. Will post it once I am able to fix the above issue.
Thank you so much for your quick reply. I will look forward for your update.
the good thing in it is that at least I know now that It's not something that I did wrong :-)

---

