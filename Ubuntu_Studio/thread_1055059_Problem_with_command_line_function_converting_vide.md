---
title: "Problem with command line function converting video for sansa player"
date: 2009-01-30
forum: Ubuntu Studio
---

### Post by Ulysses on 2009-01-30
Hello,

I posted a reply to this [http://ubuntuforums.org/showthread.php?t=892971&page=2]("http://ubuntuforums.org/showthread.php?t=892971&page=2") and realized (while I was at work, no less) that I should not have posted to a [SOLVED] thread, so here goes.

I did as instructed
Edited .bashrc to include the following lines:
```
# Command line function to convert video for sansa player
sansavideo() {
frame_per_second="23.98"
video_bit_rate="578k"

ffmpeg -i "$1" -r 29.97 -vcodec mpeg4 -b $video_bit_rate -ar 44100 -g 300 -s 320x240 -aspect 4:3 -ac 2 -f mp4 -y "$2"

}
```

I have the correct version of ffmpeg
I did this
```
ffmpeg -formats |grep aac
```
And received the proper result
```
D aac ADTS AAC
DEA aac
D A mpeg4aac
```

But when I put the command line in like this
```
sansavideo inputfilename.ext outputfilename.mp4
```

I get this error message
```
INPUT.avi: I/O error occured
Usually that means that input file is truncated and/or corrupted.
```

Though, I wonder now and am fain to admit that I did not think this before (I am as new as new can be at this and I really try, I really do), if when I executed the command line I did not use the terminal commands to navigate to the folder where the INPUTFILENAME.ext was located - and that the error message I received was a generic one that simply related to not being able to find the file

Please, any help would be appreciated. Sorry for posting in the wrong thread to begin with

---

### Post by FakeOutdoorsman on 2009-01-30
You will first need to navigate to the directory where the input file is located or you can probably include it in your command such as:
```
sansavideo videos/originals/inputfilename.ext videos/outputs/outputfilename.mp4
```
Also, paste the output of:
```
ffmpeg -version
```

---

### Post by Ulysses on 2009-01-30
Woo hoo!!!!

Thanks for responding to me

This was the first chance I had to test it and it worked so well I think I might cry.

So that means I can now play video on my SansaView player.

Now, the fun lies in a couple more things
Write it up, mebbe, for someone else who wants to be able to make the most use out of this cool little player (got it as a factory refurbished for 70.00 CDN - 8GB with a slot for MicroSD that I can expand to)
And, what would be even better, is if mebbe someone could give me some tips on how to turn the command line into a little shell script that anyone could use and enjoy.

Thanks, again

RAR

---

