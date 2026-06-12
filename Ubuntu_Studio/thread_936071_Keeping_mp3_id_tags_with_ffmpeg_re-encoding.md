---
title: "Keeping mp3 id tags with ffmpeg re-encoding"
date: 2008-10-02
forum: Ubuntu Studio
---

### Post by Hiperi0n on 2008-10-02
Do you know how if there is a way to ffmpeg to keep the original mp3 id tags when converting audio files? I am lowering the bitrate of some mp3 files but the id tags are not copied into the new mp3 file.

Thanks.

---

### Post by Hiperi0n on 2008-10-03
bump, someone?

I have get used to ffmpeg but I can't find anything about tags...

---

### Post by FakeOutdoorsman on 2008-10-03
I'm fairly sure that both FFmpeg and LAME don't preserve the tags / metadata.

---

### Post by Hiperi0n on 2008-10-04
Well, that is a pity. And is there any program that could copy the original id tags to the newly created file? So it would be easy to insert it in my original mp3 converting script.

Thanks.

---

### Post by Hiperi0n on 2008-10-17
Hey Hiperi0n why don't you try id3tool?

[https://lists.ubuntu.com/archives/ubuntu-users/2008-February/137635.html](https://lists.ubuntu.com/archives/ubuntu-users/2008-February/137635.html)

Ooops, I am talking to myself! :lolflag:

---

### Post by dranorter on 2011-05-20
Ha, I've replied to myself before. :) On these forums too, I think. Though I'm not right now, I'm pretty sure.

Anyway the man page for ffmpeg says it has a -map_meta_data option but I can't figure out how to get it to work, the syntax as stated doesn't seem to work. It keeps telling me the files already exist. Of course they exist, I'm trying to copy tags from them! D:

id3tool doesn't seem to have a way to outright copy id3 tags so I sure hope I can get -map_meta_data working.

---

### Post by andrew.46 on 2011-05-20
> **dranorter said:**
> Anyway the man page for ffmpeg says it has a -map_meta_data option but I can't figure out how to get it to work, the syntax as stated doesn't seem to work. It keeps telling me the files already exist. Of course they exist, I'm trying to copy tags from them!

The syntax should be:

```
ffmpeg -y -i original_file -map_meta_data 0:0 new_file
```

Depending on your version of FFmpeg the mapping might be done automagically without the -map_meta_data option, may not work at all, or will work beautifully with the suggested syntax :). Just be aware that the *-y* option will allow overwriting...

---

### Post by dranorter on 2011-05-20
Okay so if I type 

ffmpeg -ab 256k -map_meta_data 0:0 -i endofmay.ogg endofmay.mp3

I don't get any errors and the program seems to say it really is going to copy the tags (it repeats the title, artist, rating and lyrics both when overviewing the input file and the output file) but then the output file still doesn't have any of the information when I check with the file browser (that is, right clicking on it and looking at properties).

id3tool says neither the ogg nor the mp3 contains id3 tags, so that's a bit confusing and useless.

---

### Post by andrew.46 on 2011-05-20
If the original file is ogg you could try the following rather cumbersome method:

```

ffmpeg -i endofmay.ogg  \
 -metadata title="$(vorbiscomment --list endofmay.ogg | grep 'title' | cut -d '=' -f 2)" \
 -metadata artist="$(vorbiscomment --list endofmay.ogg | grep 'artist' | cut -d '=' -f 2)" \
 -metadata album="$(vorbiscomment --list endofmay.ogg | grep 'album' | cut -d '=' -f 2)" \
 -ab 256k endofmay.mp3

```

I have used this for ogg to ogg re-encoding rather than ogg to mp3 but hopefully it will work in this case as well. This only transfers title, artist and album but others could be added in easily enough...

---

### Post by sparrowhawker on 2011-07-01
Try this in a script file to batch convert all ogg files to mp3@256kbps in the directory preserving the title, artist and album tags. Just copy the code into a text file, say **conv.sh**, and then run the command(s)
**chmod +x conv.sh**
**./conv.sh**

```

#!/bin/bash
for f in *.ogg; do
  title=$(vorbiscomment -l "$f" | grep -i 'title' | cut -d '=' -f 2)
  album=$(vorbiscomment -l "$f" | grep -i 'album' | cut -d '=' -f 2)
  artist=$(vorbiscomment -l "$f" | grep -i 'artist' | cut -d '=' -f 2)
  ffmpeg -y -i "$f" -metadata title="$title" -metadata album="$album" -metadata artist="$artist" -ab 256k "${f%.ogg}.mp3"
done

```

---

### Post by 3djake on 2012-06-01
Sorry for digging up an old post but I too am having troubling keeping the id tags or "meta data"

I tried the shell script and using -map_metadata, 
I changed the settings on my my CD ripper program last week to rip to mp3 and went thru half my CD collection but it changed back to ogg on its own when I went thru the other half today and did not realize they were all ogg :(

Has any one figured out how to convert ogg to mp3 and keep all the metadata yet?

Thanks

---

### Post by CharlesA on 2012-06-01
[http://superuser.com/questions/110411/convert-music-library-to-ogg-vorbis-without-losing-tag-data](http://superuser.com/questions/110411/convert-music-library-to-ogg-vorbis-without-losing-tag-data)

Might be a good idea to create a new thread as this one is a bit old.

---

