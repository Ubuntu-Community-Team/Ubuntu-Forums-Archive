---
title: "Conky Clementine script for Beaver"
date: 2018-05-31
forum: Ubuntu, Linux and OS Chat
---

### Post by NHerby on 2018-05-31
Hi,
I've been using for years conkyclementine described here: [https://ubuntuforums.org/showthread.php?t=1645481](https://ubuntuforums.org/showthread.php?t=1645481)
Unfortunately, the repository ppa:conky-companions/ppa is not available anymore in Beaver and I didn't find any working script doing the job under beaver/clementine1.3.1.
I managed to create a bash script to get inputs from Clementine inside my conky:
```
#!/bin/bash

# clementine info display script by NHerby

case "$1" in

# Create a copy of the cover
cover)

file=`qdbus org.mpris.MediaPlayer2.clementine /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Metadata | grep artUrl`
FILENAME=$( echo "$file" | cut -c 22- )

if [ "$FILENAME" != "" ]
then
cp "$FILENAME" ~/.conky/cover.jpg
fi
;;

# Now Playing Info

status) 

status=`qdbus org.mpris.MediaPlayer2.clementine /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.PlaybackStatus`
if [ "$status" == "Paused" ]
then status="Playing"
fi

echo $status

;;

artist) qdbus org.mpris.MediaPlayer2.clementine /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Metadata | grep artist | cut -c 15- ;;

title) qdbus org.mpris.MediaPlayer2.clementine /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Metadata | grep title | cut -c 14- ;;

album) qdbus org.mpris.MediaPlayer2.clementine /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Metadata | grep album | cut -c 14- ;;

year) qdbus org.mpris.MediaPlayer2.clementine /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Metadata | grep year | cut -c 12- ;;

genre) qdbus org.mpris.MediaPlayer2.clementine /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Metadata | grep genre | cut -c 14- ;;

progress)

curr=`qdbus org.mpris.MediaPlayer2.clementine /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Position`
tot=`qdbus org.mpris.MediaPlayer2.clementine /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Metadata | grep length`
total=$( echo "$tot" | cut -c 14- )

if [ "$total" != "" ]
then
let progress=curr*100
let progress=progress/total
fi

echo $progress

;;

esac
```Just save this in ~/.conky/clementine and make it executable.
I'm far from being a programmer so this is the first working script I managed to write. I'm pretty sure that there is a lot of room for improvement.
And here's the part of my conky.rc using this script:
```
${if_running clementine}${if_match "Playing" == "${execi 10 ~/.conky/clementine status}"}${color 4769ea}${font caviar dreams:size=10}Music
${voffset -8}${hr}
${font caviar dreams:size=8}${color b5f9ff}${voffset 2}${goto 91}${execi 10 ~/.conky/clementine artist}

${goto 91}${execi 10 ~/.conky/clementine title}

${goto 91}${execi 10 ~/.conky/clementine album}

${image ~/.conky/cover.jpg -p 1, 786 -s 75x75 -f 10}${execi 10 ~/.conky/clementine cover}
${color 4769ea}${voffset -12}${execibar 2 ~/.conky/clementine progress}
$endif$endif
```

---

### Post by QIII on 2018-05-31
Not a support request.  Moved to **Ubuntu, Linux and OS Chat.**

---

