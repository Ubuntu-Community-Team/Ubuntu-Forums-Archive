---
title: "SoundConvert AAC support"
date: 2009-01-14
forum: Ubuntu Studio
---

### Post by adamitj on 2009-01-14
How can I install AAC encoding to convert my MP3 files with SoundConvert?

---

### Post by stderr on 2009-01-17
I don't know if SoundConverter supports encoding to AAC. If it does it probably uses libfaac0, so check you've got that first

sudo apt-get install libfaac0

You can alternatively use an encoder such as faac. Here's a little script I mocked up to convert from MP3 to AAC. You will need these packages first though:

sudo apt-get install mplayer faac

You can save the below script as e.g. convertMP3toAAC, make it executable (chmod +x convertMP3toAAC) and run it with ./convertMP3toAAC /file/to/convert.mp3

```
#!/bin/bash
mp3file=$1
wavfile=$(echo $mp3file | sed -e s/mp3$/wav/)
aacfile=$(echo $mp3file | sed -e s/mp3$/aac/)

mplayer -ao pcm:file="$wavfile" "$mp3file"
faac -o "$aacfile" "$wavfile"
rm "$wavfile"

```

---

### Post by adamitj on 2009-01-27
Thanks to Gautier Portet (maintainer of SoundConverter) I could solve this problem.

It was missing "gstreamer0.10-plugins-bad-multiverse" package. After a shot install trhough Synaptic, AAC format became available.

However there is not how to set AAC encoding properties. Maybe in a future version, but for this moment it's doing a nice job.

---

### Post by drunkmatador on 2009-06-09
Thanks for the script! This is exactly what I've been looking for.. just got a Nintendo DSi and they don't support mp3 so I've got to convert everything to AAC.

Would it be easy to modify this script to do an entire folder at once? It's taking forever to put in each file name, even using the tab button to finish filling them in.

---

### Post by Jorge Cafrune on 2010-11-30
> **adamitj said:**
> Thanks to Gautier Portet (maintainer of SoundConverter) I could solve this problem.

It was missing &quot;gstreamer0.10-plugins-bad-multiverse&quot; package. After a shot install trhough Synaptic, AAC format became available.

However there is not how to set AAC encoding properties. Maybe in a future version, but for this moment it's doing a nice job.

 Hey all,  The AAC format is now available but I have this message when trying to convert (encode from .flac to .mp3) : "Gstreamer Error Impossible to configure the support library"  The message is probably not the good one because it's a translation from french : "Gstreamer Error Impossible de configurer la bibliothèque de prise en charge"  Any idea why I have this message when trying to convert from .flac to .aac ?  Thank you !

---

