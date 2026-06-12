---
title: "Converting vob files"
date: 2009-12-16
forum: The Cafe
---

### Post by winjeel on 2009-12-16
Just a simple question. My wife is needing to convert vob (DVD) files to something that's playable on computer without needing a DVD player, preferably a multiplatform file type. She needs not the entire length, just a small segment to show in her class.

1. What converters are there available in Linux? I've had a look in Ubuntu's Software Centre, but there didn't seem to be anything.
2. What's the easiest to use editing software? Considering that all she needs to do is to splice out a two minute segment (for educational use), and needs to work in both Windows. Linux, and Mac (really, all three are used).

---

### Post by Irihapeti on 2009-12-16
Vobcopy (available through synaptic) will copy DVDs to hard disk. It's quite a while since I used it, but I think it will also allow you to copy only a portion of a DVD. Mpeg2dec (also through synaptic) may also be useful.

---

### Post by 3rdalbum on 2009-12-16
You need to rip the DVD first. You can't just copy the files across.

Acidrip can rip a DVD and convert it to another format. I also hear a lot of good things about Handbrake.

---

### Post by Gizenshya on 2009-12-16
> **3rdalbum said:**
> You need to rip the DVD first. You can't just copy the files across.

Acidrip can rip a DVD and convert it to another format. I also hear a lot of good things about Handbrake.

Actually, yes, you can just copy the files across.  A DVD video disc is nothing more than a collection of video files in a folder.

VOB files are actually regular mpeg video files that are just renamed to *.vob instead of *.mpg, and there is no need to transcode them, as they are already there.  If you want a smaller file size or a none-mpg format, you will have to transcode it.  So just copy-paste the video files to your computer and then change the file extension (rename it to .mpg), and you're set.

To edit the video for a simple project like that, I recommend avidemux (available in the repositories, and it also has win and mac versions, just google for them).  You should be able to open the video and intuitively edit it by selecting and deleting (with delete key) segments that you don't want.

If the DVD is encrypted, however, you would need specialized software to decrypt the files.

---

### Post by stinger30au on 2009-12-16
handbrake will convert the vob files to what ever you like

[http://handbrake.fr/](http://handbrake.fr/)

---

### Post by amsterdamharu on 2009-12-16
Avidemux can convert vob files, with vlc you can convert the dvd and choose what subs and sound to use.

The result of vlc ripped dvd can mostly only play in vlc there is something wrong with the stream that doesn't allowe other players to play it but I haven't got that much experience with it.

---

### Post by handy on 2009-12-16
Here is a quick & dirty how-to for using Handbrake:

[http://www.ostalk.org/showthread.php?tid=433](http://www.ostalk.org/showthread.php?tid=433)

It will be worth having a quick look at the Handbrake site, which is linked to in the above how-to, as the new version may have made a change or two to the command line parameters.

By the way, whenever I have a use for Handbrake, I just go to the above how-to & cut & paste the command line that is there, then modify it to suit my purpose. It saves both typing & remembering. :)

I usually rip the DVD first with DVDShrink 3.2, & then use handbrake to reprocess the file. Handbrake is pretty fast, does a great job & the recently released version now allows you to store a subtitle track that you can choose to use or not whilst the movie is playing.  In the past if you chose subtitle it was hard coded into the movie, so you could not get rid of it even if you wanted to.

DVDShrink runs fine under Wine, & is probably the easiest & most reliable (free) software for the job.

---

### Post by winjeel on 2009-12-17
Thanks all, I'll give it a go. The help is muchly appreciated.

---

### Post by pedja_portugalac on 2009-12-17
> **Gizenshya said:**
> Actually, yes, you can just copy the files across.  A DVD video disc is nothing more than a collection of video files in a folder.

VOB files are actually regular mpeg video files that are just renamed to *.vob instead of *.mpg, and there is no need to transcode them, as they are already there.  If you want a smaller file size or a none-mpg format, you will have to transcode it.  So just copy-paste the video files to your computer and then change the file extension (rename it to .mpg), and you're set.

To edit the video for a simple project like that, I recommend avidemux (available in the repositories, and it also has win and mac versions, just google for them).  You should be able to open the video and intuitively edit it by selecting and deleting (with delete key) segments that you don't want.

If the DVD is encrypted, however, you would need specialized software to decrypt the files.

Avidemux is the best choice, I agree.

---

### Post by user1397 on 2009-12-17
Hmm if avidemux doesnt work, you could try tovid, check out the link in my sig

---

