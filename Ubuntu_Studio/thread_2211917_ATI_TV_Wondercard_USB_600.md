---
title: "ATI TV Wondercard USB 600"
date: 2014-03-18
forum: Ubuntu Studio
---

### Post by Flaggmann on 2014-03-18
Does anyone know of a decent setup process to get one of these working with ubuntu 12.04 so that any application will recognize it quickly ?

---

### Post by lukeiamyourfather on 2014-03-18
What specifically do you mean? It's a V4L device so it should already show up for applications aware of V4L devices.

---

### Post by Flaggmann on 2014-03-18
the V4L apps I have seen don't allow for control of the channels or input selection ie composite/tuner etc. once set up an editor using it as a video input will save whatever it sees but the application does not have built in controls to select digital, analog channels, cable or antenna, or just composite inputs in the win universe one just runs catalyst and it allows for selecting and configuring the card then records to a common folder; once recorded any editor can then just import the file to the editor.

---

### Post by Flaggmann on 2014-03-20
I found this script online to start the tvtime app (it started and worked both aud & vid then after closing and reopening it erroed with audio busy) :
best one so far but instructions at start aren't super clear what to do or why. The recording script halts also appears to be audio busy. any suggestions?

###########################
    #!/bin/bash
    # add following line via visudo or put "snd_mixer_oss" in rc.conf MODULES array
    # %wheel ALL=(root) NOPASSWD: /sbin/modprobe snd_mixer_oss
    sudo modprobe snd_mixer_oss
    # modify string for your language regarding aplay -l
    SEARCHSTRING="Karte"

    CARDS="$(aplay -l | grep -i "$SEARCHSTRING" | cut -d \: -f1 | cut -d \  -f2 | sort -u)"
    LASTCARD=$(echo $CARDS | rev | cut -d " " -f1)
    TVCARD=$((LASTCARD+1))
    for i in $(seq 0 $LASTCARD) ; do
        aplay -l | grep "$SEARCHSTRING ${i}:" >/dev/null
        [ $? = 1 ] && TVCARD=$i
    done
    sox -t alsa hw:$TVCARD,2 -t alsa default --no-show-progress &
    /usr/bin/tvtime "$@"
    # close sox session
    kill %%

#############
Recording script (also found online using transcode)

#!/bin/sh
killall tvtime
TODAY=$( date +%Y%m%d )
NOW=$( date +%H:%M )
sleep 4 && amixer -q set "Line" 100% unmute
sleep 1 && amixer -q set "Master" 100% unmute
#####################################################################
gnome-terminal --execute transcode -x v4l2,v4l2 \
-M 2 \
-i /dev/video0 \
-p /dev/dsp \
-w 6000 \
-y ffmpeg \
-F mpeg4 \
-g 720x420 \
-f 0,4 \
-I 1 \
-J resample,levels,smartyuv,pv \
-u 100 \
-Q 3 \
-Z 640x480,fast \
-E 48000,16,2 \
-o ~/-${TODAY}-${NOW}.avi \
#####################################################################

---

