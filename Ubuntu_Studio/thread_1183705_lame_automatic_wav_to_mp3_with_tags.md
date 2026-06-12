---
title: "lame automatic wav to mp3 with tags"
date: 2009-06-10
forum: Ubuntu Studio
---

### Post by jonlemur on 2009-06-10
So, I have a bunch of .wav files in one folder that I would like to transcode to mp3.  Each of the .wav files has a name like WaitingInVain.wav, where the words in the title of the song are run together, and each word is capitalized.  I would like to write a script (that would likely use lame) to transcode each of the .wav files to an mp3 file with the same name, and a tag for the title that has the same name, except with spaces in between words.  I'd also like to add tags for the composer and for the genre.

The psuedo code that I'm thinking of would go something like this:

```
for each .wav in folder
  NAME = nameofsong (from nameofsong.wav)
  NAME_WITH_SPACES = NAME with spaces before every capital letter except the first
  TITLE_TAG = NAME_WITH_SPACES
  COMPOSER_TAG = "Bob Marley"
  GENRE_TAG = "Reggae"
  transcode nameofsong.wav to NAME.mp3 with tags
next
```

Any ideas how I could script this, or even what programs I need?

Thanks for any help.
jonlemur

---

### Post by lukeiamyourfather on 2009-06-10
This would be pretty straightforward with Python and its awesome string capabilities, but there's software out there that will create tags based on directory structure and filenames which would solve the problem. Just transcode to the same directory and same name (with different extension) and then go from there with other software to create the tags.

If you're trying to save space you might consider transcoding to FLAC instead of MP3 since FLAC is both lossless (but compressed) and open source where MP3 is both proprietary and lossy. If you need MP3 or other formats for players the FLAC can always be transcoded again to whatever you need but is smaller than the WAV. Cheers!

---

