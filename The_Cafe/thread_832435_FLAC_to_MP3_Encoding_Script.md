---
title: "FLAC to MP3 Encoding Script"
date: 2008-06-17
forum: The Cafe
---

### Post by Tom Mann on 2008-06-17
Hi Guys

I decided to start to learn the BASH shell today, and looked at my most common problem on my PC to start: Converting FLAC to MP3. I have used various interfaces but do not really like them much, plus I am planning to have this run as a cron job on my server.

This is the first draft of a script that will find all the .flac files in one folder and create .mp3 files in another folder - keeping the folder structure from the initial folder it searches on and also keeping the tags intact (apart from genre which I took out as I was having errors)

I intend to post another version of this at some point which will add the following:

1. Store a MD5 fingerprint of each .flac file that the script comes across, and re-encode only files that haven't yet been done, or .flac files that have been replaced (this is due to me having some damaged CDs that I plan on cleaning up/replacing and re-encoding)

2. Sort out the genre problem (if there is no genre I'll add a placeholder of some description)

3. Logging of files that may have gone wrong for some reason.

I have seen no bugs with this code at the time I've put it here, but if anyone needs a solution like this please try this code thanks :)

Enjoy! Indeed.

Tom


To use. Download the file and in a terminal, navigate to the folder containing the file and type

```
chmod +x ./flactomp3.sh
```

to make it executable. You will then need to edit two values in the script:

```
flacdir=/media/old_storage/Music/FLAC
mp3dir=/media/old_storage/Music/MP3
```

change these to the location of your .flac files, and where you would like the MP3s to go - the MP3 folder is created by the program if it doesn't already exist - as will all folders you may have down from $flacdir.

You may also want to alter the lame command to use a lower bitrate (I like 210-280) :)

Then just type:

```
./flactomp3
```

and walk away while it churns. It's created 5GB in 3 hours (approx 6-12 seconds a song) on my AMD X2 6400+ with Ubuntu 64 bit.

---

### Post by Tom Mann on 2008-06-17
Just to add, here's the code:

```
#!/bin/bash
#!/bin/sh

# flactomp3.sh v0.01
# converts all flac files recursively found at $flacdir
# and creates MP3s of them at mp3dir, following any
# existing directory structure.
#
# Requirements
# lame, flac.
 
flacdir=/media/old_storage/Music/FLAC
mp3dir=/media/old_storage/Music/MP3

# test to see if the mp3 directory exists: if not create it
if [ ! -d "$mp3dir" ]
then
  mkdir -p "$mp3dir"
fi

# main loop - we go into directories, make sure the mp3
# equivalent directory exists, create it if not, then
# convert each file across.

export IFS=$'\n'
for flac in $(find $flacdir -type f)
do

  # check we're dealing with a .flac
  if [ "${flac##/*.}" == "flac" ]
  then
  
  # replace flac directory structure with mp3 directory structure
    mp3="$mp3dir${flac#$flacdir}"
  # replace .flac extension with .mp3 extension
    mp3="${mp3%.flac}.mp3"
  
    #echo $flac \>\> $mp3
  # retrieve tags

    metaflac --export-tags-to=- "$flac" | sed 's/=\(.*\)/="\1"/' > /tmp/flacmeta.tmp
    . /tmp/flacmeta.tmp
    rm /tmp/flacmeta.tmp

  # check target directory exists, creating it if necessary
    targetdir="${mp3%/*.mp3}"
    if [ ! -d "$targetdir" ]
    then
      mkdir -p "$targetdir"
    fi
  
  # convert flac to mp3, preserving tags
    flac -dc "$flac" | lame -V 1 -q 0 --vbr-new -h \
      --tt "$TITLE"\
      --tl "$ALBUM"\
      --tn "$TRACKNUMBER"\
      --ty "$DATE"\
      --ta "$ARTIST"\
      --ty "${DATE%%-*}"\
      --id3v2-only\
      --replaygain-accurate\
      - "$mp3"
  fi
  
done
export IFS=" "
```

---

### Post by billgoldberg on 2008-06-17
I appreciate your work on this, but is their any reason you can't use ffmpeg (with winff gui)?

---

### Post by Tom Mann on 2008-06-17
Hi Bill,

My plan for this (on top of being an exercise in learning some bash scripting) is to put it onto my file server and have it run at specific intervals, where I can do the basic ripping and copying, and pick my mp3s up when I'm wondering what to put onto my Zen. It's laziness for the sake of laziness :)

---

### Post by billgoldberg on 2008-06-17
> **Tom Mann said:**
> Hi Bill,

My plan for this (on top of being an exercise in learning some bash scripting) is to put it onto my file server and have it run at specific intervals, where I can do the basic ripping and copying, and pick my mp3s up when I'm wondering what to put onto my Zen. It's laziness for the sake of laziness :)

Ok, I was just wondering, because it's easier for the desktop.

I really have start learning how to make a script soon.

I know the cli pretty good but besides that I'm only good at html and css.

I'll start learning this weekend.

---

### Post by Tom Mann on 2008-06-18
OK - this version has been cleaned up somewhat (I have implemented functions), and also implemented the flac md5 database which only fills up if a mp3 encoding exits successfully. This takes care of update 1.

The above also re-encodes a file if it finds it to be different (if you have a scratched cd that you've replaced, this should update any damaged flac files to mp3)

The genre problem seems to be associated with lame, so I have added a --ignore-tag-errors linx to lame for the time being - with a view on fixing this fully in the future.

Finally, logging isn't added yet for failed files, but with the md5 database skipping failed encodings this shouldn't be a problem.

Next todo:

Create an ogg-vorbis version: should be easy, just change the encoding function to use ogg vorbis instead - maybe change some variable names to reflect the use of .ogg instead.

```
#!/bin/bash
#!/bin/sh

# flactomp3.sh v0.01
# converts all flac files recursively found at $flacdir
# and creates MP3s of them at mp3dir, following any
# existing directory structure.
#
# Requirements
# lame, flac.
 
flacdir="/media/old_storage/Music/FLAC"
mp3dir="/media/old_storage/Music/MP3"
dbfilename="$HOME/.FlacMP3"

function createmp3 {
      flac -dc "$1" | lame --preset fast extreme -h \
      --tt "$TITLE"\
      --tl "$ALBUM"\
      --tn "$TRACKNUMBER"\
      --ty "$DATE"\
      --ta "$ARTIST"\
      --ty "${DATE%%-*}"\
      --id3v2-only\
      --replaygain-accurate\
      --ignore-tag-errors\
      - "$2"
}

function getmd5 {
  md5=`md5sum $1`
  flacmd5=${md5%% $1}
  flacmd5="${flacmd5/[/}"
  flacmd5="${flacmd5/]/}"
}

function readmd5 {
  md5=`cat "$dbfilename" | grep $1`
  storedmd5="${md5%% $1}"
  storedmd5="${storedmd5/[/}"
  storedmd5="${storedmd5/]/}"
}

function storemd5 {
  md5=`md5sum $1`

  if [ ! "x$storedmd5" == "x" ] # x added as "" is not a valid input for a test
  then
    sed -i 's|'"$storedmd5*$flac"'||g' "$dbfilename"
    cat "$dbfilename" | awk '$0!~/^$/ {print $0}' "$dbfilename" > "$dbfilename".tmp
    mv "$dbfilename.tmp" "$dbfilename" # remove blank lines
    # TODO: the sed statement above can break if there is more than one of the same entry!
  fi
  echo $md5 >> "$dbfilename"
}

function makedir {
  if [ ! -d "$1" ]
  then
    mkdir -p "$1"
  fi
}

# test to see if the flac md5 database exists: if not create it
if [ ! -f "$dbfilename" ]
then
  touch "$dbfilename"
fi

# test to see if the mp3 directory exists: if not create it
makedir "$mp3dir"

# main loop - we go into directories, make sure the mp3
# equivalent directory exists, create it if not, then
# convert each file across.

export IFS=$'\n'
for flac in $(find "$flacdir" -type f)
do

  # check we're dealing with a .flac
  if [ "${flac##/*.}" == "flac" ]
  then

  # check that the file does not have a matching entry in our md5 database
  getmd5 "$flac"
  readmd5 "$flac"

  if [ ! "$storedmd5" == "$flacmd5" ]
  then

      # replace flac directory structure with mp3 directory structure
      mp3="$mp3dir${flac#$flacdir}"
      # replace .flac extension with .mp3 extension
      mp3="${mp3%.flac}.mp3"
  
      # retrieve tags
      metaflac --export-tags-to=- "$flac" | sed 's/=\(.*\)/="\1"/' > /tmp/flacmeta.tmp
      . /tmp/flacmeta.tmp
      rm /tmp/flacmeta.tmp
  
      # check target directory exists, creating it if necessary
      targetdir="${mp3%/*.mp3}"
      makedir "$targetdir"
    
      # convert flac to mp3, preserving tags
      createmp3 "$flac" "$mp3"

      # finally store the md5 in our database as we have
      # created the mp3 successfully.
      if [ $? == 0 ]
      then
	storemd5 "$flac"
      fi
    fi
  fi
done
export IFS=" "
```

---

### Post by roaldz on 2008-06-18
Sorry, I have to ask.. Wouldn´t it be much cooler to convert things to ogg? Cuz mp3=lame. And yes, I know your mp3 player doesn´t play ogg:)

---

### Post by Tom Mann on 2008-06-18
Roaldz - the next phase of this script is to convert files to ogg instead, as I'm patiently waiting for Rockbox to find it's way onto the Zen... :KS

---

### Post by roaldz on 2008-06-18
> **Tom Mann said:**
> Roaldz - the next phase of this script is to convert files to ogg instead, as I'm patiently waiting for Rockbox to find it's way onto the Zen... :KS

Yeah, that´s the spirit!

---

### Post by Tom Mann on 2008-06-18
And here is the FLAC to OGG script!

```
#!/bin/bash
#!/bin/sh

# flactoogg.sh v0.05
# converts all flac files recursively found at $flacdir
# and creates OGGs of them at oggdir, following any
# existing directory structure.
#
# Requirements
# lame, flac.
 
flacdir="/media/old_storage/Music/FLAC"
oggdir="/media/old_storage/Music/OGG"
dbfilename="$HOME/.FlacOGG"

function createogg {
      oggenc -q7 \
      --date "$DATE"\
      --tracknum "$TRACKNUMBER"\
      --title "$TITLE"\
      --album "$ALBUM"\
      --artist "$ARTIST"\
      --genre "$GENRE"\
      --output="$2" "$1"
}

function getmd5 {
  md5=`md5sum $1`
  flacmd5=${md5%% $1}
  flacmd5="${flacmd5/[/}"
  flacmd5="${flacmd5/]/}"
}

function readmd5 {
  md5=`cat "$dbfilename" | grep $1`
  storedmd5="${md5%% $1}"
  storedmd5="${storedmd5/[/}"
  storedmd5="${storedmd5/]/}"
}

function storemd5 {
  md5=`md5sum $1`

  if [ ! "x$storedmd5" == "x" ] # x added as "" is not a valid input for a test
  then
    sed -i 's|'"$storedmd5*$flac"'||g' "$dbfilename"
    cat "$dbfilename" | awk '$0!~/^$/ {print $0}' "$dbfilename" > "$dbfilename".tmp
    mv "$dbfilename.tmp" "$dbfilename" # remove blank lines
    # TODO: the sed statement above can break if there is more than one of the same entry!
  fi
  echo $md5 >> "$dbfilename"
}

function makedir {
  if [ ! -d "$1" ]
  then
    mkdir -p "$1"
  fi
}

# test to see if the flac md5 database exists: if not create it
if [ ! -f "$dbfilename" ]
then
  touch "$dbfilename"
fi

# test to see if the ogg directory exists: if not create it
makedir "$oggdir"

# main loop - we go into directories, make sure the ogg
# equivalent directory exists, create it if not, then
# convert each file across.

export IFS=$'\n'
for flac in $(find "$flacdir" -type f)
do

  # check we're dealing with a .flac
  if [ "${flac##/*.}" == "flac" ]
  then

  # check that the file does not have a matching entry in our md5 database
  getmd5 "$flac"
  readmd5 "$flac"

  if [ ! "$storedmd5" == "$flacmd5" ]
  then

      # replace flac directory structure with ogg directory structure
      ogg="$oggdir${flac#$flacdir}"
      # replace .flac extension with .ogg extension
      ogg="${ogg%.flac}.ogg"
  
      # retrieve tags
      metaflac --export-tags-to=- "$flac" | sed 's/=\(.*\)/="\1"/' > /tmp/flacmeta.tmp
      . /tmp/flacmeta.tmp
      rm /tmp/flacmeta.tmp
  
      # check target directory exists, creating it if necessary
      targetdir="${ogg%/*.ogg}"
      makedir "$targetdir"
    
      # convert flac to ogg, preserving tags
      createogg "$flac" "$ogg"

      # finally store the md5 in our database as we have
      # created the ogg successfully.
      if [ $? == 0 ]
      then
	storemd5 "$flac"
      fi
    fi
  fi
done
export IFS=" "
```

---

### Post by Sniffer on 2008-08-02
Thanks

Great Work indeed.

---

### Post by Lostincyberspace on 2008-08-04
Is there any way you could set it up so i can select the song in nautilus and have it convert it right there. I know it is possible but I don't know enough about bash scripting to be able to make it work.

---

### Post by Fynn on 2008-08-10
I must be doing something wrong with the flac to mp3 (new version) as it's giving me the error '19: Syntax error: "}" unexpected' after Lame does it's thing.

UPDATE:

Came downstairs this morning and it appears to have worked!  

[http://ubuntuforums.org/showthread.php?t=499045](http://ubuntuforums.org/showthread.php?t=499045) 
explains what I was seeing...

Many thanks.

UPDATE 2:

... but Nitin Sawhney appears to have inherited Anthrax's summary data.

---

### Post by eti.que on 2009-06-01
Hello all,

Reviving this thread a bit. I updated the script from Tom Mann to include a kind of "MP3 folder cleanup".

Basically anything that is recorded in the database and not present anymore in the flacdir will be removed.

```
#!/bin/bash
#!/bin/sh

# flactomp3.sh v0.01
# converts all flac files recursively found at $flacdir
# and creates MP3s of them at mp3dir, following any
# existing directory structure.
#
# Requirements
# lame, flac.

flacdir="/media/Musique/Librairie/"
mp3dir="/media/Musique/Baladeur/"
dbfilename="$mp3dir.convert_db"
logfile="$mp3dir.log"

function createmp3 {
      flac -dc "$1" | lame -V 5 -h \
      --tt "$TITLE"\
      --tl "$ALBUM"\
      --tn "$TRACKNUMBER"\
      --ty "$DATE"\
      --ta "$ARTIST"\
      --ty "${DATE%%-*}"\
      --id3v2-only\
      --replaygain-accurate\
      --ignore-tag-errors\
      - "$2"
	  chmod 775 "$2"
	  chgrp users "$2"
}

function getmd5 {
  md5=`md5sum $1`
  flacmd5="${md5%% $1}"
  flacmd5="${flacmd5/[/}"
  flacmd5="${flacmd5/]/}"
}

function readmd5 {
  md5=`cat "$dbfilename" | grep $1`
  storedmd5="${md5%% $1}"
  storedmd5="${storedmd5/[/}"
  storedmd5="${storedmd5/]/}"
}

function storemd5 {
  if [ ! "x$storedmd5" == "x" ] # x added as "" is not a valid input for a test
  then
    sed -i 's|'"$storedmd5  $barefile"'||g' "$dbfilename"
    cat "$dbfilename" | awk '$0!~/^$/ {print $0}' "$dbfilename" > "$dbfilename".tmp
    mv "$dbfilename.tmp" "$dbfilename" # remove blank lines
    # TODO: the sed statement above can break if there is more than one of the same entry!
  fi
  echo "$flacmd5 $1" >> "$dbfilename"
}

function makedir {
  if [ ! -d "$1" ]
  then
    mkdir -p "$1"
echo "Folder $1 created." >> "$logfile"
	fi
}

# test to see if the flac md5 database exists: if not create it
if [ ! -f "$dbfilename" ]
then
  touch "$dbfilename"
fi

if [ ! -f "$logfile" ]
then
	touch "$dbfilename"
else
	rm "$logfile"
	touch "$logfile"
fi

# test to see if the mp3 directory exists: if not create it
makedir "$mp3dir"

# main loop - we go into directories, make sure the mp3
# equivalent directory exists, create it if not, then
# convert each file across.

export IFS=$'\n'

#MP3 Database cleanup
for dir in $(find "$mp3dir" -type d)
do
	if [ ! "$dir" == "$mp3dir" ]
	then

		#Remove any empty folder
		rmdir --ignore-fail-on-non-empty "$dir"
		
		#Get the artist & artist/album pattern
		dir="${dir#$mp3dir}"


		#Select only the tracks matching the above pattern
		for track in $(cat "$dbfilename" | grep "$dir/")
		do
			#Retrieve track from the database
			track="${track#*  }"
			
			#Check if the folder still exists in $flacdir
			if [ ! -d "$flacdir$dir" ]
			then
				
				#Remove the entry if not
				sed -i 's|'".*$track"'||g' "$dbfilename"
				cat "$dbfilename" | awk '$0!~/^$/ {print $0}' "$dbfilename" > "$dbfilename".tmp
				mv "$dbfilename.tmp" "$dbfilename" # remove blank lines

				#Remove the folder if not removed before
				if [ -d "$mp3dir$dir" ]
				then
echo "$dir has been removed from \$mp3dir" >> "$logfile"
					rm -r "$mp3dir$dir"
				fi
			
			#Folder still exists
			else
				#Check if file still exists
				if [ ! -f "$flacdir$track.flac" ]
				then
					#Remove the entry if not
					sed -i 's|'".*$track"'||g' "$dbfilename"
					cat "$dbfilename" | awk '$0!~/^$/ {print $0}' "$dbfilename" > "$dbfilename".tmp
					mv "$dbfilename.tmp" "$dbfilename" # remove blank lines
					
					#Remove the file if it still exists
					if [ -f "$mp3dir$track.mp3" ]
					then
echo "$track has been removed from \$mp3dir" >> "$logfile"
						rm "$mp3dir$track.mp3"
					fi
				fi
			fi
		done
	fi
done

for flac in $(find "$flacdir" -type f)
do
	# check we're dealing with a .flac
	if [ "${flac##/*.}" == "flac" ]
	then
		track="${flac#$flacdir}"
		track="${track%.flac}"
		
		# check that the file does not have a matching entry in our md5 database
		getmd5 "$flac"
		readmd5 "$track"
		if [ ! "$storedmd5" == "$flacmd5" ]
		then

			# replace flac directory structure with mp3 directory structure
			mp3="$mp3dir$track.mp3"

			# retrieve tags
			metaflac --export-tags-to=- "$flac" | sed 's/=\(.*\)/="\1"/' > /tmp/flacmeta.tmp
			. /tmp/flacmeta.tmp
			rm /tmp/flacmeta.tmp
echo "Tag values: $ARTIST/($DATE) $ALBUM/$TRACKNUMBER. $TITLE" >> "$logfile"
			# check target directory exists, creating it if necessary
			targetdir="${mp3%/*.mp3}"
			makedir "$targetdir"

			# convert flac to mp3, preserving tags
			createmp3 "$flac" "$mp3"


			# finally store the md5 in our database as we have
			# created the mp3 successfully.
			if [ $? == 0 ]
			then
echo "$flac correctly encoded to $mp3" >> "$logfile"
				storemd5 "$track"
			fi
		fi
	fi
done
export IFS=" "
```

So far it works well. If it can be of any use to somebody... ;)

Ah, one thing, if anyone knows how to benefit from a multicore/hyperthreaded CPU, it would be nice ! (I have an Atom 330, 2 cores with HT)

I was thinking of creating a separate script for the encoding and launching 2 or 3 cronjobs in the same time, but that's a bit, errhhh, wild, and I wonder how to handle possible conflicts.

Well, we'll see !
Cheers

---

### Post by monsterstack on 2009-06-01
Useful stuff. I'll see if I can be bothered to add in some getopts so people can set the "in" and "out" directories from the commandline, a bit like "mp3Demflacs -i /home/user/flacs/ -o /home/user/mp3s".

---

### Post by DarkWan on 2010-08-20
> **monsterstack said:**
> Useful stuff. I'll see if I can be bothered to add in some getopts so people can set the "in" and "out" directories from the commandline, a bit like "mp3Demflacs -i /home/user/flacs/ -o /home/user/mp3s".

try something like this

```

#!/bin/bash
#!/bin/sh

# flactomp3.sh v0.01
# converts all flac files recursively found at $flacdir
# and creates MP3s of them at mp3dir, following any
# existing directory structure.
#
# Requirements
# lame, flac.

flacdir="/media/Musique/Librairie/"
mp3dir="/media/Musique/Baladeur/"

while [ ! -z "$1" ]; do
    case $1 in
        -i | --input_file )
            shift
            flacdir=$1
            ;;
        -o | --output_file )
            shift
            mp3dir=$1
            ;;
    esac
    shift
done

dbfilename="$mp3dir.convert_db"
logfile="$mp3dir.log"

[...]


```

---

