---
title: "How can I make Cinelerra recognize a video format?"
date: 2009-05-20
forum: Ubuntu Studio
---

### Post by mjpatey on 2009-05-20
Hi, all-

I've installed Cinelerra, and it's running beautifully!  But I have to convert my compressed AVIs into something else in order to use them with Cinelerra.  Is there any way to allow Cinelerra to read my video files?  The format for the files is an AVI containing XVID MPEG-4 video, 640 x 480 @ 30fps, with 44.1KHz Mono ADPCM audio.

The symptom I'm experiencing is that Cinelerra will load the files, but throws up an error for each on import:

> virtual int FileMOV::read_frame(VFrame*): quicktime_read_frame/quicktime_decode_video failed, result:When playing or editing a file like this in the editor, the audio is just looping digital noise, and the same error occurs.

Any idea how to get Cinelerra to recognize this format?  Thanks in advance!!!

-Mark

---

### Post by kayosiii on 2009-05-22
mjpeg with very little compression seems to be a practical solution. 

Uncompressed or PNG Compressed Movs work quite well (but take up looots of space).... YUV4Linux works quite well if you don't need sound -- this is a great option if you are taking sources from DVDs - you get about 2 mins and 18 seconds to a 2GB file though... Other YUV uncompressed formats may also work but could take a bit of fiddling.

(Basically Cinelerra is designed to work with uncompressed video and tends to behave best when you feed it the right things).

---

### Post by wkulecz on 2009-05-29
No matter how nice Cinelerra might be, its a showstopper for me if I have to convert input videos or it can't outptut the edits in the same format that I've chosen for "archive" (DV type 1 for now).  If you can play it back in "Movie Player" on your system, any decent video editor should accept it as input.

But Windows systems also fall down here with various corporate pissing contests about codecs -- Sony Vegas won't touch Adobe FLV files for example.  But most of what can be played back can be used for editing.

Kdenlive seems pretty good here so far, on the one system I have where it doesn't crash all the time. 

--wally.

---

