---
title: "batch convert mp3 files to wav"
date: 2008-09-15
forum: Ubuntu Studio
---

### Post by jonabyte on 2008-09-15
As the title says, anyone know of a good program to do this.
I got a few thousand I need to convert.

Thanks!

---

### Post by prismatic7 on 2008-09-15
try soundconverter, in the repos.

---

### Post by prshah on 2008-09-15
> **jonabyte said:**
> As the title says, anyone know of a good program to do this.
I got a few thousand I need to convert.


You can do it from the terminal (Application-Accessories-Terminal)with the following commands```

#first, install lame
sudo apt-get install lame
cd ~/wavdirectory
for filname in * ; do lame -V2 $filname $filename.mp3 ; done
``` this will produce a bunch of *.wav.mp3 files.

Check the mp3 _before_ deleting the corresponding WAVs! I use this to convert my (recorded) phone conversations to MP3, and apparently something called "endianness" (sp?) can cause the MP3's to be nothing but static! Post back if you run into this problem.

---

### Post by Superslobberface on 2008-11-13
I found this nice article with details:
[https://encodable.com/tech/blog/2006/05/08/Find_Forloops_and_Spaces_in_BASH]("https://encodable.com/tech/blog/2006/05/08/Find_Forloops_and_Spaces_in_BASH")

Basically, you can open the command prompt and cd to the directory of the wav files you want to convert.

One Liner:
```
export IFS=$'\n';for song in $(find -type f -iname '*.wav' |sed 's!\.wav$!!');do lame -h "$song.wav" "$song.mp3";done
```

This will produce .mp3 files in addition to the .wav files you already have.

You could put this in a bash shell script:
```

#! /bin/bash
# convert.sh
# Convert all .wav files in this and all sub directories to .mp3
# Optional: Delete .wav files after conversion

export IFS=$'\n';
time for song in $(find -type f -iname '*.wav' |sed 's!\.wav$!!');
do
  echo -n "$song.mp3"
  lame -h -S "$song.wav" "$song.mp3";
  # uncomment the next line to delete .wav after conversion.
  #rm "$song.wav";  
  echo -n " ";
done

```

Make the shell script executable and copy it to your bin directory:
```

chmod +x convert.sh
sudo cp convert.sh /usr/bin/

```

Change to the wav directory and run the script:
```

cd /home/username/Music/wavfiles
convert.sh

```

Always be careful when deleting files with find!

---

### Post by alwayshere on 2008-11-13
sudo apt-get install soundKonverter

---

