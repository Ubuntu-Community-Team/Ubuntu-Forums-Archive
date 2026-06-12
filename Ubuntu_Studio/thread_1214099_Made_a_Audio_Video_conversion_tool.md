---
title: "Made a Audio Video conversion tool"
date: 2009-07-15
forum: Ubuntu Studio
---

### Post by ~Las~ on 2009-07-15
I tried to convert mp3 to a less quality mp3 but wasnt able to find one with meta tag option ...so i thought build a gui for ffmpeg .It can be inserted in to nautilus-scripts i think for right click menu.Here im posting it so if anyone like it they can make improvements.My programming skills are not good so it may be not that much good;)

```

#!/bin/bash

notify-send "Starting {converter}"

title={converter}

FILE=`zenity --file-selection --title="$title" --multiple --title="Select a File"`
case $? in
                 
                 1)
                        exit;;
                
        esac
   FILENAME=${FILE##*/};
NOEXT=${FILENAME%\.*}
av=$(zenity --title="$title" --list --radiolist --column="" --column="Convert to Audio or Video?" -- FALSE "audio" FALSE "video" )
case $? in
                 
                 1)
                        exit;;
                
        esac
if [ "$av" = "audio" ]
        then 
                        ( ext=$(zenity --title="$title" --list --radiolist --column="" --column="Convert To" -- FALSE ".avi" FALSE ".mpg" FALSE ".mkv" FALSE ".flv" FALSE ".mp3" FALSE ".ogg" FALSE ".ogm" FALSE ".mov" FALSE ".wmv" FALSE ".vob" FALSE ".rm" FALSE ".asf" FALSE ".3gp" FALSE ".mp4" FALSE ".amr")
case $? in
                 
                 1)
                        exit;;
                
        esac

abit=$(zenity --title="$title" --list --radiolist --column="" --column="Audio Bitrate" -- FALSE "6.6k" FALSE "8.85k" FALSE "12.65k" FALSE "14.25k" FALSE "15.85k" FALSE "16k" FALSE "18.25k" FALSE "19.85k" FALSE "23.05k" FALSE "23.85k" FALSE "16k" FALSE "32k" FALSE "64k" FALSE "96k" FALSE "128k" FALSE "192k" FALSE "256k" FALSE "320k" 
)
case $? in
                 
                 1)
                        exit;;
                
        esac


afrq=$( zenity --title="$title" --list --radiolist --column="" --column="Audio Frq" -- FALSE "8000" FALSE "16000" FALSE "22050" FALSE "44100" FALSE "48000" )
case $? in
                 
                 1)
                        exit;;
                
        esac

achan=$(zenity --title="$title" --list --radiolist --column="" --column="Audio Channels" --  FALSE "1" FALSE "2" )
case $? in
                 
                 1)
                        exit;;
                
        esac

FILE1=`zenity --file-selection --directory --title="Save Location"`
case $? in
                 
                 1)
                        exit;;
                
        esac
    

{
    ffmpeg -i "$FILE" -ab $abit -ar $afrq -ac $achan -map_meta_data "$FILE":"$FILE1$NOEXT$ext" "$FILE1/$NOEXT$ext"| notify-send "Processing $NOEXT$ext" 
}

notify-send "Conversion Finished")


else 
(ext=$(zenity --title="$title" --list --radiolist --column="" --column="Convert To" -- FALSE ".avi" FALSE ".mpg" FALSE ".mkv" FALSE ".flv" FALSE ".mp3" FALSE ".ogg" FALSE ".ogm" FALSE ".mov" FALSE ".wmv" FALSE ".vob" FALSE ".rm" FALSE ".asf" FALSE ".3gp" FALSE ".mp4" FALSE ".amr")
case $? in
                 
                 1)
                        exit;;
                
        esac

abit=$(zenity --title="$title" --list --radiolist --column="" --column="Audio Bitrate" -- FALSE "6.6k" FALSE "8.85k" FALSE "12.65k" FALSE "14.25k" FALSE "15.85k" FALSE "16k" FALSE "18.25k" FALSE "19.85k" FALSE "23.05k" FALSE "23.85k" FALSE "16k" FALSE "32k" FALSE "64k" FALSE "96k" FALSE "128k" FALSE "192k" FALSE "256k" FALSE "320k" 
)
case $? in
                 
                 1)
                        exit;;
                
        esac


afrq=$( zenity --title="$title" --list --radiolist --column="" --column="Audio Frq" -- FALSE "8000" FALSE "16000" FALSE "22050" FALSE "44100" FALSE "48000" 
)
case $? in
                 
                 1)
                        exit;;
                
        esac

achan=$(zenity --title="$title" --list --radiolist --column="" --column="Audio Channels" --  FALSE "1" FALSE "2" 
)
case $? in
                 
                 1)
                        exit;;
                
        esac

vbit=$(zenity --title="$title" --list --radiolist --column="" --column="Video Bitrate" -- FALSE "50k" FALSE "100k" FALSE "200k" FALSE "300k" FALSE "400k" FALSE "500k" FALSE "600k" FALSE "700k" FALSE "800k" FALSE "900k" FALSE "1000k" FALSE "1200k" FALSE "1500k" FALSE "2000k" FALSE "2500k" FALSE "5000k" FALSE "10000k" FALSE "15000k" FALSE "20000k"
)
case $? in
                 
                 1)
                        exit;;
                
        esac
vfs=$(zenity --title="$title" --list --radiolist --column="" --column="Video FPS" -- FALSE "12" FALSE "15" FALSE "25" FALSE "30" 
)
case $? in
                 
                 1)
                        exit;;
                
        esac
vsize=$(zenity --title="$title" --list --radiolist --column="" --column="Video Size" -- FALSE "128x96" FALSE "160x120 " FALSE "176x144" FALSE "320x240" FALSE "352x288" FALSE "640x480" FALSE "704x576" FALSE "800x600" FALSE "1024x768 "FALSE "1600x1200"FALSE "1408x1152"FALSE "1408x1152" 
)
case $? in
                 
                 1)
                        exit;;
                
        esac
FILE1=`zenity --file-selection --directory --title="Save Location"`
case $? in
                 
                 1)
                        exit;;
                
        esac
        


(
    ffmpeg -i "$FILE" -ab $abit -ar $afrq -ac $achan -b $vbit -r $vfs -s $vsize- "$FILE1/$NOEXT$ext"| notify-send "Processing $NOEXT$ext"
)

notify-send "Conversion Finished")
 fi    
exit

          

```Hope some one likes it....:p
I don't know how to do batch processing with this..hope some one help me with that command....

you need zenity and ffmpeg +lame etc..depending on your conversion requirements.You can find that from ffmpeg documentation

---

