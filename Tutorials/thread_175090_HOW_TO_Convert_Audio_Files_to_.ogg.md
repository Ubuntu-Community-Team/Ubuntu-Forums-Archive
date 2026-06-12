---
title: "HOW TO: Convert Audio Files to .ogg"
date: 2006-05-12
forum: Tutorials
---

### Post by smartalecks on 2006-05-12
[SIZE="5"]Converting Audio Files (.mp3, .wav) to .ogg[/SIZE]

I don't like the .mp3 file format. It is not very well supported in Linux, and the Ogg Vorbis filetype is a very nice alternative. The .ogg file can be played in Totem, Rhythm Box, amaroK, etc.

This is a tutorial on how to convert audio files (such as .mp3, .wav) to the Ogg Vorbis (.ogg) filetype. As always when converting a file there will be loss in quality (very very little in this, however. Consider testing first, backup too.)

This script was written by Micheal Hipp (not me).
[B]
Dependent on:[/B] mp3info , mpg123 , vorbis-tools (go to Synaptic, search, and install)

1. Make a new file on your desktop named mp3-ogg.sh. Open it with a text editor and paste this code. Save it and close.

```
#/bin/sh
#
# converts mp3 to ogg


function mp3-ogg () {

if [ ! -f "$1" ]; then

  echo "File "$1" not found!"

else

  mp3info -p "title%t\nartist%a\nalbum%l\nbitrate%r\n" "$1" > tag.txt
  
  title=$(cat tag.txt | grep title | cut -c 6-50)
  artist=$(cat tag.txt | grep artist | cut -c 7-50)
  album=$(cat tag.txt | grep album | cut -c 6-50)
  bitrate=$(cat tag.txt | grep bitrate | cut -c 8-50)

  if [ "$bitrate" -ge 256 ];then
	quality=8
  elif [ "$bitrate" -ge 192 ];then
	quality=7
  elif [ "$bitrate" -ge 128 ];then
	quality=6
  else
	quality=5
  fi

  wav=`echo "$1"|sed -e 's/.[mM][pP]3/.wav/'`
  notag=`echo "$1"|sed -e 's/.[mM][pP]3/.ogg/'`
  mpg123 --wav "$wav" "$1" &&
  oggenc -q $quality -t "$title" -a "$artist" -l "$album" -o "$notag" "$wav"
  rm tag.txt
  rm -f "$wav" ||
  echo "There was a problem with the conversion process!"

fi

}



# convert all mp3 files in directory

if [ $# -eq 1 -a -d "$1" ]; then

for file in $1/*.[mM][pP]3; do
	mp3-ogg "$file"
done
exit

fi

# One or more mp3 files were given

for file in $*; do

  mp3-ogg "$file"

done

# Not enough information

if [ $# -lt 1 ]; then

  echo
  echo "Usage:	$0 myfile.mp3"
  echo "	$0 /directory/containing/mp3/files"
  echo "	$0 myfile.mp3 myfile2.mp3 myfile3.mp3"
  # You have to use quotations for the arguement below.
  # Failure to do so will result in only one file being
  # converted. Namely, the first one it comes across...
  echo '	$0 "*.mp3"'
  echo
  echo "For converting .mp3's that have spaces in the"
  echo 'name, use the directory option OR "*.mp3"'
  echo
  exit

fi

exit
```

2. Make the script executable by 

```
chmod +x /home/username/Desktop/mp3-ogg.sh
```

3. To use it, enter these commands in a terminal:

```

cd /directory/where/your/music/is
/home/username/Desktop/mp3-ogg.sh mp3file1.mp3 mp3file2.mp3 mp3file4.mp3

```

To find other ways to use it enter 

```

/home/username/Desktop/mp3-ogg.sh
```

It will usually convert on about 15-18 seconds for a 3 minute .mp3.
Hope this helps for whatever you are doing! :-D

---

### Post by stormdragon2976 on 2008-09-07
Thanks, I suddenly got the urge to convert all my music to ogg.  This is a big help.

---

### Post by niceangelbaby on 2008-09-07
just been browsing and came across  [www.watchesshopping.net](http://www.watchesshopping.net) there prices seem to be way lower that standard. All of the watches seem to be priced around $200 to $300. Are they fakes? The site seems to look quite legit.

---

### Post by RATM_Owns on 2008-09-07
Is there a way to convert music to aac/at3?

---

### Post by TenPlus1 on 2008-09-07
Pop into Add.Remove and install SoundConverter, it's a case of dragging and dropping your mp3 directories/files onto the window and pressing start :)

---

### Post by jpapas on 2012-06-24
:popcorn: 

Do you know if save metadata info then convert audio???

):P

---

### Post by LHammonds on 2012-06-26
I am guessing but I would be that this process does NOT save MP3 tags that you might have carefully tweaked over the years such as the image/jpeg thumbnail, album, track, genre, year, mood, comments, artist, album artist, composer, etc.

As always, test and see what it does with one file before trying to convert an entire collection. ;)

---

