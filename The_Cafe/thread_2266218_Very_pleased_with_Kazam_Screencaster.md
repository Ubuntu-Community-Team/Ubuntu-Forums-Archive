---
title: "Very pleased with Kazam Screencaster"
date: 2015-02-21
forum: The Cafe
---

### Post by michael-piziak on 2015-02-21
I've been looking for a desktop recorder off and on for a few months.

Finally, one that works!    The others I tried wouldn't record the audio.

Kazam works perfect.

---

### Post by sammiev on 2015-02-21
> **michael-piziak said:**
> I've been looking for a desktop recorder off and on for a few months.

Finally, one that works!    The others I tried wouldn't record the audio.

Kazam works perfect.

Make sure you mark this thread as "solved" so when other people are looking for the same they know it works. :p

---

### Post by deadflowr on 2015-02-21
Cafe has no solved option.
But you can manually edit the thread title...

---

### Post by michael-piziak on 2015-02-21
The reason it was hard to find in the Software Center in the past is because Kazam doesn't come up if you search "desktop recorder" or "screen recorder."
I just happened to find it in the comments section of other recorders.

Kazam comes up if you search "Screencaster" which not many people would think to type in.

---

### Post by jacobpratt909 on 2015-02-22
Many people reject Kazam because it leaves you with a raw data file that is unusable, this is because you need to wait for it to process the file into a .mp4. I pointed this out in the software centre also.

---

### Post by michael-piziak on 2015-02-22
You can upload the file that it makes to youtube, which is mostly what I want to do with the files I create.  I just made this video:  [http://youtu.be/A-kiMGLaMUY](http://youtu.be/A-kiMGLaMUY)

I did not find another screen recorder that would record the audio.   Kazam is great for me.

Update:  I see that Winff will convert the Kazam files to mpg files.

Update 2:  I just recorded a 10 minute video with Kazam, choosing mp4, and it saved the file instantly with no wait.  Perhaps this is a newer version of Kazam that doens't take time to process the files into mp4.

---

### Post by jacobpratt909 on 2015-02-23
Neat :)

---

### Post by monkeybrain20122 on 2015-02-25
> **michael-piziak said:**
> 

Update 2:  I just recorded a 10 minute video with Kazam, choosing mp4, and it saved the file instantly with no wait.  Perhaps this is a newer version of Kazam that doens't take time to process the files into mp4.


Same here. I never have to wait for processing the file like jacobpratt909 said. Either because he uses an old version of Kazam from the Software centre (I installed from ppa) or because he has weak hardware so the conversion takes longer.

---

### Post by sffvba[e0rt on 2015-02-27
I have found [simplescreenrecorder]("http://www.maartenbaert.be/simplescreenrecorder/") to work very very well (even the stream video to sites like [www.twitch.tv](www.twitch.tv))...

---

### Post by michael-piziak on 2015-02-28
Well I installed an Nvidia card, then I took the card out.

Now my Kazam Screencaster won't record the audio.

If anyone knows some ways to trouble shoot this, please do tell.

---

### Post by michael-piziak on 2015-03-01
> **not found said:**
> I have found [simplescreenrecorder]("http://www.maartenbaert.be/simplescreenrecorder/") to work very very well (even the stream video to sites like [www.twitch.tv]("http://www.twitch.tv"))...

Since Kazam quit working for me (after my graphics card experience), I think I'll try simplescreenrecorder.   Using 12.04 LTS here.

Is this what I type into terminal, as from your webpage link, to install it:

sudo add-apt-repository ppa:maarten-baert/simplescreenrecorder
sudo apt-get update
sudo apt-get install simplescreenrecorder
# if you want to record 32-bit OpenGL applications on a 64-bit system:
sudo apt-get install simplescreenrecorder-lib:i386

p.s. what's that 32-bit option?  I'm running 64 bit Ubuntu now.

---

### Post by jacobpratt909 on 2015-03-01
get the ```
 sudo apt-get install simplescreenrecorder-lib:i386 
``` option.

---

### Post by michael-piziak on 2015-03-01
Solved problem with a program called PulseAudio Volume Control in the Ubuntu Software Center.

Source of solution:  [https://www.youtube.com/watch?v=jeATRDE7LzI](https://www.youtube.com/watch?v=jeATRDE7LzI)

---

### Post by RangerK on 2015-04-24
> **michael-piziak said:**
> Solved problem with a program called PulseAudio Volume Control in the Ubuntu Software Center.

Source of solution:  [https://www.youtube.com/watch?v=jeATRDE7LzI](https://www.youtube.com/watch?v=jeATRDE7LzI)

I tried exactly this solution, but I still can record sound.  :-(

---

