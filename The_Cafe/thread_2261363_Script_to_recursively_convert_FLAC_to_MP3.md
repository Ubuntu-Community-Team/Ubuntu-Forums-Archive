---
title: "Script to recursively convert FLAC to MP3"
date: 2015-01-18
forum: The Cafe
---

### Post by knucklehead101 on 2015-01-18
I didn't want to spend a few bucks on a GUI tool and I have plenty of Linux VMs running at home so I decided to try to make a script and failed but I stumbled across [http://ubuntuforums.org/showthread.php?t=832435&highlight=flac+to+mp3](http://ubuntuforums.org/showthread.php?t=832435&highlight=flac+to+mp3) via Google and decided I would give it a try.  It was converting my FLAC to MP3 however it was stripping all metadata and ID3 tags from the files.  I tweaked the script to use avconv instead of flac and lame since I guess they are notorious for stripping the data that I wanted to preserve.  Again this is a script that I have just tweaked and I am not taking credit for the real work that went into it.

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
 
flacdir="/home/nanderson/fileshare/Music"
mp3dir="/home/nanderson/fileshare/converted/"
dbfilename="$HOME/.FlacMP3"


function createmp3 {
    avconv -i "$1" -ab 320k -map_metadata 0 "$2"
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

### Post by TheFu on 2015-01-18
Definitely remove the 
#!/bin/sh
line. The script appears to be using bash-specific stuff.

---

### Post by knucklehead101 on 2015-01-26
Will do.  Thanks for the tip... I am new to Bash scripting so I am sure I would overlook many mistakes :D.

---

### Post by SeijiSensei on 2015-01-26
deleted

---

### Post by mamamia88 on 2015-01-26
Just a heads up no reason to spend any money on a tool like that.  Use gnome soundconverter package [http://packages.ubuntu.com/search?keywords=soundconverter](http://packages.ubuntu.com/search?keywords=soundconverter) It does everything easily and maintains metadata

---

### Post by jim_osborn on 2015-02-16
Hi, mamamia88, et. al.  I'm writing a script of my own to convert audio files to mp3 to share some playlists with a relative who can only use that format, and tried to use soundconverter in batch mode to do the job.  The deal breaker for me is that I can find no way to tell soundconverter where to put the output, and I really don't want to have the script dig the new files out of my library for placement where I want them.  The output location that can be selected in soundconverter's gui mode isn't persistent, afaik.  I don't see a .soundconverterrc (or similar) file, where I'd expect such preferences to live.

Before I move on to another converter (I need flac, ogg, and wav in) to mp3, does anyone know how to get soundconverter to place its output preferentially in batch mode?  And yes, I realize ogg-->mp3 can be problematic. :)

TIA,

Jim

---

### Post by HermanAB on 2015-02-16
Well, it is a one liner actually, using find exec sox.  Sometimes it is a good idea to read a man page instead of writing a 100 line script.

---

### Post by TheFu on 2015-02-16
> **HermanAB said:**
> Well, it is a one liner actually, using find exec sox.  Sometimes it is a good idea to read a man page instead of writing a 100 line script.

Nice.

Sometimes a 1 liner is perfect.
Other times we forget and create a tiny loop when a one-liner would do too.

It is good to have both in our toolkit.

---

### Post by Erik1984 on 2015-02-17
> **HermanAB said:**
> Well, it is a one liner actually, using find exec sox.  Sometimes it is a good idea to read a man page instead of writing a 100 line script.

But the 100 liner can be educational to write if you are not familiar with bash.

---

