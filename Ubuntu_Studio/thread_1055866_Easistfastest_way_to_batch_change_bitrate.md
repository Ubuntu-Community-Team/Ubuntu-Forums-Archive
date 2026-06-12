---
title: "Easist/fastest way to batch change bitrate?"
date: 2009-01-31
forum: Ubuntu Studio
---

### Post by Donalb on 2009-01-31
Hi all,
 Multimedia wouldn't be an area I dabble in much.

I have a bunch (50 or 60?) of large MP3s with a bitrate of 256kbps.

I'd like to change them to 96 or 112kbps (they're not music) to conserve storage on my iRiver. What's the easist and fastest way to do this? When I say fastest what I mean is not having to do each file seperately (rather than the speed of the actual operation).
I selected them with audacity (which I've yet to use) but it opened them all into seperate windows to do one at a time. 
Is there an easy way to do this? ( I remember in XP I had a dbPower, a freeware addon that could do this with a right-click in Explorer).

Thanks for any advice

Regards
Donal

---

### Post by raboofje on 2009-01-31
I'd probably decode them with 'mpg123', then re-encode them with 'lame', with a small shell script from the commandline:


 ```
 for i in *.mp3 
    do 
      mpg123 -w "`basename "$i" .mp3`.wav" "$i"
      lame --preset cbr 96 "`basename "$i" .mp3`.wav" "`basename "$i" .mp3`.reencoded.mp3"
      rm "`basename "$i" .mp3`.wav"
    done
```

(you can replace newlines by ';' if you want)

---

### Post by sleepingdragon on 2009-02-01
SoundKonverter will give you the bitrate options you need, and does a good job of batch processing. It's pretty quick too.

---

### Post by Donalb on 2009-02-01
Great, I'll try that, thanks!

---

### Post by TunaCanTommy on 2009-09-06
I know I'm jumping into this thread a little late, and I don't mean to hijack the thread, but I have a similar situation.

 I'd like to convert "high-bitrate" .MP3 files in stereo to an .mp3 at a lower bitrate and mono. They're audio-book files and I don't need much quality to store and play them on my MP3 player - file size is important.

I've had good success with a lame command run on each file:

```
lame -m m --preset 48 /Audiobook/file1.mp3
```

Lame knows it's an .mp3 file that you want to "transcode".

The file is transcoded to mono at 48kbps(ABR), and resampled from 44.1kHz down to about 24kHz. The resulting file is about 1/2 to 1/3 the size with very little, if any, loss in listenability. However the ID3v2 tags are lost and the another .mp3 is added to the file name . . . file_name.mp3.mp3.

If I use:

```
lame -m m --preset 48 /Audiobook/file_1.mp3 /Audiobook/file_2.mp3
```

I don't get the extra .mp3 added to the file name, but it's more typing/coding.

I fix the extra .mp3 in the file names with a nice little application called "Bulk Rename" - it's in the repos. And I use "Audio Tag Tool" to re-apply ID3v2 / ID3v1 tags.

I couldn't find a way to do a "bulk-transcode" with lame. So I started looking at a Nautilus Script to simplify the task. Here's what I came up with using my very limited knowledge some research on the web.

```
#! /bin/sh
lame -m m --preset 48 $NAUTILIUS_SCRIPT_SELECTED_URIS
```

But it doesn't work. It's in my Nautilus Scripts folder, it's executable, and it shows up on the "Scripts-Menu" when I right-click on a file. . . . any suggestions as to how this should be coded.

Can I add anything to the code to remove the extra .mp3 that's added when the file is transcoded ? ?  Also, sometimes the .mp3 files have spaces in their name - this needs to be dealt with.

Any suggestions would be appreciated.

---

