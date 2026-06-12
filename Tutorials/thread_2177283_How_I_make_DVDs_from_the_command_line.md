---
title: "How I make DVDs from the command line"
date: 2013-09-28
forum: Tutorials
---

### Post by GrouchyGaijin on 2013-09-28
I tested this on Ubuntu 12.04 with .mp4 and .avi files.
 The DVD will **[COLOR=#ff0000]not[/COLOR]** have a menu or chapters, but will play in a DVD player.
 At least it works in my player connected to my TV
 The DVD will only have the default audio track.  
 If you want to change audio tracks you need to do that before running this script.
 I use mencoder for specifying audio tracks.
 Call the script by putting it in PATH (Don't forget to make this script executable.)
 I named the script makedvd

Change: Fixed the problem of spaces in the .iso file name

```


#!/bin/bash
# by GrouchyGaijin September 28, 2013
#I tested this on Ubuntu 12.04 with .mp4 and .avi files.
# The DVD will not have a menu or chapters, but will play in a DVD player.
# At least it works in my player connected to my TV
# The DVD will only have the default audio track.  
# If you want to change audio tracks you need to do that before running this script.
# I use mencoder for specifying audio tracks.
# Call the script by putting it in PATH (Don't forget to make this script executable.)
# I named the script makedvd


## REQUIRED PROGRAMS ##
# ffmpeg
# dvdauthor
# growisofs


#Change: Fixed the problem of spaces in the new DVD name 




echo "This script is for making a DVD "
echo "Start in the folder containing the master video."
read -p "Enter the name of the master video file: " master
read -p "Enter the name for your DVD: " new_name


echo "Shall we convert the video into the correct format?
If so type yes."
read x
if [ "$x" = "yes" ]
then
# I chose PAL change this to the correct format
ffmpeg -i $master -aspect 4:3 -target pal-dvd dvd.mpg


else
echo "OK, come back when you are ready"
fi


echo "Now we make the DVD files."
dvdauthor -o dvd/ -t dvd.mpg 


echo "Here we set the region to PAL"
#Change this as needed
VIDEO_FORMAT=PAL dvdauthor -o dvd/ -T


echo "Ready to make the iso file? 
If so type yes."
read x
if [ "$x" = "yes" ]
then
mkisofs -dvd-video -o dvd.iso dvd/
else
echo "OK, come back when you are ready"
fi
mv dvd.iso "$new_name".iso


echo "Want to try to burn one?. 
If so type yes."
read x
if [ "$x" = "yes" ]
then
# I have a crappy old laptop so I burn at 2x. You can probably go faster.
growisofs -speed=2 -dvd-compat -Z /dev/dvdrw=$new_name.iso 
else
echo "OK, come back when you are ready"
fi

echo "Clean up?
If so type yes"
read x
if [ "$x" = "yes" ]
then
rm -r dvd 
rm dvd.mpg
else
echo "OK, Don't forget to do it later"
fi


echo "Finished and all according to plan more or less!"




```

---

### Post by alf31 on 2013-10-04
nica tutorial dude :D

---

