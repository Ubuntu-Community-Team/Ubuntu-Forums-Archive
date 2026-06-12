---
title: "HOW-TO Salvage Songs from a Corrupted iPod"
date: 2011-10-30
forum: Tutorials
---

### Post by sarloth on 2011-10-30
A friend of mine recently brought a 120 GB iPod to me complaining that iTunes was telling her it was corrupted. She explained that it worked fine and it was the only place she had all of those songs because she had received several from other peoples' computers.

I had initially thought "iTunes does this crap all the time, I'll just hook it up to my Ubuntu system and pull the files off." I was wrong. iTunes, for once, was actually reporting the problem correctly. The FAT file system was corrupted in several sectors and was unmountable.

I proceeded treating the device as any other corrupted hard drive. It was located on my machine as sdb and had one partition sdb1 which was 120GB.

I cleared out a 200 GB partition on my large main-drive: /dev/sda1

I used an Ubuntu wiki page to help me out:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Downloaded gddrescue and ran:

```
sudo ddrescue --no-split --force /dev/sdb1 /dev/sda1 hername.log
```

This took several hours (I fell asleep) to complete. Once it was complete I ran the other two commands in the wiki file to no gain. I had already told her that because the drive was actually corrupt she may loose songs, so I was okay with this.

I made a directory and mounted the partition to remove the songs:

```
mkdir pod
sudo mount /dev/sda1 pod
```

In order to rapidly extract all of the mp3 files (I was not concerned with album art or other things) I wrote a quick one-line for loop:

```
for d in pod/iPod_Control/Music/*; do cp *.mp3 Music; done
```

Once all of the songs were in Music, I found a script posted by "boontu" in the forums to help me rename the files with id3 tags. However, I did have to make one modification to bring the script to a working state. I changed "ls $1" to "find $1 -name "*.mp3"" in order to include relative paths.

```
#!/bin/bash
# This script will bulk rename music files with ID3 tags to format:
# '[song title]-[artist name].extension'
# The script will take one argument which is the directory in which to rename.
# WARNING: All files in directory with spaces will be renamed, substituting
# the spaces for the '_' character.
if [ "$1" = "" ];then
echo "Error: Please enter a directory."
echo "Format is 'namemp3s [directory]'."
sleep 1
exit
fi
rename 's/ /_/g' *
find $1 -name "*.mp3" > /tmp/lsout
while read LINE; do
if [ -d $LINE ];then
echo "$LINE is a directory. It will not be renamed."
elif [ "`id3tool $LINE | grep "No ID3 Tag"`" != "" ]; then
echo "$LINE has no ID3 Tag. It will not be renamed."
else
EXT=`echo "$LINE" | cut -d\. -f2`
TITLE=`id3tool $LINE | grep Title | cut -d\: -f2 | sed 's/^[ \t]*//;s/[ \t]*$//'`
ARTIST=`id3tool $LINE | grep Artist | cut -d\: -f2 | sed 's/^[ \t]*//;s/[ \t]*$//'`
NEWNAME="$TITLE-$ARTIST.$EXT"
NEWNAME=`echo "$NEWNAME" | sed 's/ /_/g'`
mv "$LINE" "$NEWNAME"
echo "$LINE ---> $NEWNAME"
fi
done < /tmp/lsout
rm /tmp/lsout
```

Many of the files did not have mp3 tags. But my level of effort for this has been exceeded :P I will hope that when she loads these into iTunes it will recognize the song names for her and make her life easy, though I suspect she will have to listen and name them each. She deserves it for not backing things up!

---

